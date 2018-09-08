# 2D-to-SBS-3D-Image-Converter
This project was an attempt to convert a normal 2D image to a 3D image, i.e. as a 3D image represented in a side-by-side(SBS) format consists of two very similar left and right halves, we could in principle train a neural network to take the left half of this image as the input and output the right half as the output.

For achieving this result, we used the concept of a variational auto encoder(VAE), that is used for image compression. Usually, the VAE takes the same image as the input and output, and tries to learn a compressed intermediate representation. However, if we replace the inputs and outputs of the VAE by the left and right parts of the 3D image, we would be able to create a network that compresses our left side image and decompresses it to produce a right side image.

This compressed representation would contain the essence of the depth information of the objects present in the scene.

For training the network we took a clip of a 3D movie in SBS format, and used its frames as data. Each frame was compressed to get 2 small 32x64 sized images corresponding to the left and right halves of the frames. The network was trained on these pairs of images.
