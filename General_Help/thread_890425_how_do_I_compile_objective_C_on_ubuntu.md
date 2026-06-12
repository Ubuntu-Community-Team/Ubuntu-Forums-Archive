---
title: "how do I compile objective C on ubuntu"
date: 2008-08-15
forum: General Help
---

### Post by bobdobbs on 2008-08-15
Hi.

I'd like to set up an environment for learning objective C on my laptop.
I'm using Hardy on a 32-bit system.

I found this page:
[http://blog.lyxite.com/2008/01/compile-objective-c-programs-using-gcc.html](http://blog.lyxite.com/2008/01/compile-objective-c-programs-using-gcc.html)

But the installation instructions were brief and insufficient.

I install these packages via apt-get:
gnustep gnustep-base-runtime gnustep-base-libgnustep-base-dev libgnustep-base1.14 libgnustep-gui-dev libgnustep-gui0.12 common 

Compiling his example, I get:



hello.m:2:34: error: Foundation/Foundation.h: No such file or directory
hello.m:5: error: cannot find interface declaration for ‘NSObject’, superclass of ‘HelloWorld’
hello.m: In function ‘-[HelloWorld hello]’:
hello.m:10: error: cannot find interface declaration for ‘NXConstantString’
hello.m: In function ‘main’:
hello.m:15: warning: ‘HelloWorld’ may not respond to ‘+alloc’
hello.m:15: warning: (Messages without a matching method signature
hello.m:15: warning: will be assumed to return ‘id’ and accept
hello.m:15: warning: ‘...’ as arguments.)
hello.m:15: warning: no ‘-init’ method found
hello.m:17: warning: ‘HelloWorld’ may not respond to ‘-release’



I figure the first line means that I'm missing an essential set of header files. I'm also guessing that this should be fixed after I apt-get the right package.


Which further package or packages do I need?

Thanks

---

### Post by ilrudie on 2008-08-15
Most likely you are just not searching in the right place on your pc for the headers.  Put the full path to the header in your include statement or better yet use the -I option on gcc to include a path to search for header files.

If you don't know where the headers are (and I don't know where objective-c headers would be either) use 
```
find / -name *header_file_name.h *-print
```If that doesn't work you will then need to find which package include the required header file.  Search for it in synaptic.

---

### Post by jgfoot on 2009-01-04
I struggled with this for a while myself, but I think I've got it working.

To compile PURE Objective-C -- that is, NO GNUSTEP -- you can just do a command like this from the command line (where foo.m is your source code):

$ gcc -lobjc foo.m -o foo_run

Basically, the same as for compiling any other code with gcc, except you include "-lobjc" to link the Objective-C library.

But, there isn't much point in writing Objective-C without GNUStep.  To use GNUStep, I had to do the following:


1.  Make sure the gnustep-common package is installed.  (Of course, you also need build-essentials and gobjc, and perhaps others...)

2.  You have to use a makefile.  In the directory with your file, save this as "GNUmakefile:"

[INDENT]include ${GNUSTEP_MAKEFILES}/common.make

TOOL_NAME = MyApp
LogTest_OBJC_FILES = code.m

include ${GNUSTEP_MAKEFILES}/tool.make[/INDENT]

3.  Now, you need code to compile.  Try this from the GNUStep tutorial:

[INDENT]#import <Foundation/Foundation.h>

int main (void)
{ 
  NSLog (@"Executing");
  return 0;
}[/INDENT]


4.  Next step--and this is a bear--is to run a shell script that assigns values to variables like GNUSTEP_MAKEFILES.  Why the package doesn't do this for you, I don't know.

$ cd /usr/share/GNUstep/Makefiles/
$ sudo chmod +x GNUstep.sh
$ . ./GNUstep.sh

5.  Now, cd back to your directory with the makefile and the source, and type "make."  It should compile and put the executable in a new directory named "obj."

---

### Post by jgfoot on 2009-01-05
I found a way to do it from the command line, for simple GNUstep stuff:

[INDENT]gcc -lgnustep-base -lpthread -lobjc -lm -I/usr/local/include/GNUstep -I/usr/include/GNUstep source.m -o source_run[/INDENT]

The packages you need to have installed are: build-essentials, gobjc, gnustep-common, gnustep-devel, and libgnustep-base-dev.  (Plus more, if you want GUI stuff and other things).

---

