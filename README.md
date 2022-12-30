The Gap Buffer is a Data Structure that is a dynamic array which allows efficient insertion and deletion operations clustered near the same location in
in O(1) time. The Gap Buffer is used to represent the text buffer in EMACS, a popular and widely used text-editor.
While trying to understand this, place yourself in the shoe of someone typing and the start position of the gap buffer is where the cursor on your
laptop is.

An empty Gap Buffer with the gap start position at index 0 and end position at index 2:

Images from geeksforgeeks

inserting into the buffer and resizing it 
![image](https://user-images.githubusercontent.com/87020608/210035214-87bf4457-4054-487a-bcd4-b839fe91c78c.png)

How moving withing the buffer works
![image](https://user-images.githubusercontent.com/87020608/210035173-198d2081-4d54-4b1e-ae68-c6c3bfa9d961.png)



Two ways to integrate this into your project
1. The Simple way: there are only two files that must be integrated, gapBuffer.cpp and gapBuffer.h. Integrate these files into your project,
and use any C++ build systems of your choice
2. If you want to run the Unit Tests in tests/gapBuffer/gbufferTests, created using googletest, a C++ unit testing framework,  
install cmake if it not installed already, and run this command cmake [<options>] <path-to-source | path-to-existing-build> in a build folder you create. 
This will create a build system with cmake using the existing CMakeLists.txt files in the project. 
For example, I am at the root directory of this repo
  a. create a build folder
  b. cd into build folder
  c. run cmake ../
 cmake ../
 
The ../ portion of our command points back to our root directory because at the moment we are inside the build folder. So the source of our build 
will be our root directory, which has access to the src and tests folder where the code is!

Now we move onto how to use this Gap buffer Implementation (more will be added to the api):
1. #include "gapBuffer.h" into your file
2. Instantiate a GapBuffer Object
  a. Default constructor GapBuffer :: GapBuffer() will have a buffer size of 20 with a gap size of 8 
  b. GapBuffer :: GapBuffer(int bufferSize, int gapSize)
3. As of now there are four main functions insert(char x), remove(), moveLeft(), moveRight()
  insert will insert a char value at the current position of the gap. When a char is inserted, the gap is reduced,ready for another insertion.
  remove will remove a char: for example we have, ABCD_FF, remove will result in ABC__FF.
  moveLeft will move the gap left, for example we have, ABCD_FF, moveLeft() will result in ABC_DFF. The gap moves, adjusting the letters around it.
  moveRight will mvoe the gap right, for example we have, ABCD_FF, remove will result in ABCDF_F. The gap moves, adjusting the letters around it.
The buffer is resized automatically behind the scenes, resized will the gap is filled and when the buffer is full.

In the coming days, I will be adding more to this api, at the moment it needs a lot of works. The main functions are done, but now I need to build on top
of this. I created this with the intention of programming a text-editor just for fun!


