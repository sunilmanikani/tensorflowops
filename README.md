# tensorflowops
# Create a custom [user-defined] tensorflow Op in C++ which is consumable by python tensorflow


<b>How to compile</b>

TF_INC=$(python -c 'import tensorflow as tf; print(tf.sysconfig.get_include())')

g++ -std=c++11 -shared zero_out.cc -o zero_out.so -fPIC -I $TF_INC -O2

<b>Usage</b>
import tensorflow as tf
zero_out_module = tf.load_op_library('./zero_out.so')
with tf.Session(''):
    zero_out_module.zero_out([[1, 2], [3, 4]]).eval()