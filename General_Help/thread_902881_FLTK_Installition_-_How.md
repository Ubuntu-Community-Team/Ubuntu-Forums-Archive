---
title: "FLTK Installition - How?"
date: 2008-08-27
forum: General Help
---

### Post by Xarver on 2008-08-27
I think FLTK looks interesting to learn,
and I want to install it but have no idea how...
I downloaded the tar.gz file and extracted it to the folder I want it in,
and I typed make in the terminal like it said in the readme
while the folder was open, and it didn't work... :confused:
```
'make: *** No targets specified and no makefile found.  Stop.

```

I'm trying to install it on Ubuntu 8.04
I'm trying to install it for g++.
My editor is SciTE [Not like that's important, anyway...]

Any help appreciated!

P.S. I started a topic in Absolute Beginner and my topic got pushed onto the 2nd almost 3rd page with no results, So I decided to post a topic here.

---

### Post by LateNiteTV on 2008-08-27
try running
```
./configure
```
first

---

### Post by Xarver on 2008-08-27
```
bash: ./configure: No such file or directory
```

I tried... And I'm browsing the folder! Hmm...
That's weird...

Any possible solution?

---

### Post by vambo on 2008-08-27
You don't need to bother with all of that, it's in the repos.
What you need to get going is:

```
sudo aptitude install fltk1.1-doc libfltk-dev libfltk1.1 libfltk1.1-dbg libfltk1.1-dev fluid
```

Or, maybe better still, search Synaptic for fltk - give all you need

---

### Post by Xarver on 2008-08-27
Thanks but, when I copied a FLTK program to SciTE and compiled it, 
it threw errors at me...
The Code:
```

#include <FL/Fl.H>
#include <FL/Fl_Window.H>
#include <FL/Fl_Box.H>

int main(int argc, char **argv) {
	Fl_Window *window = new Fl_Window(300,180);
	Fl_Box *box = new Fl_Box(20,40,260,100,"Hello, World!");
	box->box(FL_UP_BOX);
	box->labelsize(36);
	box->labelfont(FL_BOLD+FL_ITALIC);
	box->labeltype(FL_SHADOW_LABEL);
	window->end();
	window->show(argc, argv);
	return Fl::run();
}

```
The Errors:
```

/tmp/cccCKVf4.o: In function `main':
fltk_test.cpp:(.text+0x43): undefined reference to `Fl_Window::Fl_Window(int, int, char const*)'
fltk_test.cpp:(.text+0xf0): undefined reference to `fl_define_FL_SHADOW_LABEL()'
fltk_test.cpp:(.text+0x10a): undefined reference to `Fl_Group::end()'
fltk_test.cpp:(.text+0x128): undefined reference to `Fl_Window::show(int, char**)'
fltk_test.cpp:(.text+0x12d): undefined reference to `Fl::run()'
/tmp/cccCKVf4.o: In function `Fl_Box::Fl_Box(int, int, int, int, char const*)':
fltk_test.cpp:(.text._ZN6Fl_BoxC1EiiiiPKc[Fl_Box::Fl_Box(int, int, int, int, char const*)]+0x30): undefined reference to `Fl_Widget::Fl_Widget(int, int, int, int, char const*)'
fltk_test.cpp:(.text._ZN6Fl_BoxC1EiiiiPKc[Fl_Box::Fl_Box(int, int, int, int, char const*)]+0x35): undefined reference to `vtable for Fl_Box'
collect2: ld returned 1 exit status

```

Is it me, the code, or is it set up wrong???
Help...

Edit: 
Synaptic had FLTK 1.1 Not the newest stable one [1.3]

---

### Post by vambo on 2008-08-27
Looks as if the fltk headers aren't in your include path.
Find where they are and use the -I option with gcc or g++

---

### Post by Xarver on 2008-08-27
I try -i, -I, g++ -i, and g++ -I 
but none work.

What's the specific command? :?

---

### Post by vambo on 2008-08-27
> **Xarver said:**
> I try -i, -I, g++ -i, and g++ -I 
but none work.

What's the specific command? :?

```
g++ -I /include_path
```

The default is /usr/include. Under there you should have the fltk headers in directory FL ie /usr/include/FL. If they're not there, put them there, then you won't need the -I flag.

---

### Post by Xarver on 2008-08-27
Well, it's all there.
I see all the files in usr/include/FL

Here's the new set of errors:
```

/tmp/ccEywTYb.o: In function `main':
fltk_test.cpp:(.text+0x43): undefined reference to `Fl_Window::Fl_Window(int, int, char const*)'
fltk_test.cpp:(.text+0xf0): undefined reference to `fl_define_FL_SHADOW_LABEL()'
fltk_test.cpp:(.text+0x10a): undefined reference to `Fl_Group::end()'
fltk_test.cpp:(.text+0x128): undefined reference to `Fl_Window::show(int, char**)'
fltk_test.cpp:(.text+0x12d): undefined reference to `Fl::run()'
/tmp/ccEywTYb.o: In function `Fl_Box::Fl_Box(int, int, int, int, char const*)':
fltk_test.cpp:(.text._ZN6Fl_BoxC1EiiiiPKc[Fl_Box::Fl_Box(int, int, int, int, char const*)]+0x30): undefined reference to `Fl_Widget::Fl_Widget(int, int, int, int, char const*)'
fltk_test.cpp:(.text._ZN6Fl_BoxC1EiiiiPKc[Fl_Box::Fl_Box(int, int, int, int, char const*)]+0x35): undefined reference to `vtable for Fl_Box'
collect2: ld returned 1 exit status

```
What could be the problem?!?!

---

### Post by vambo on 2008-08-27
> **Xarver said:**
> Well, it's all there.
I see all the files in usr/include/FL

Here's the new set of errors:
```

/tmp/ccEywTYb.o: In function `main':
fltk_test.cpp:(.text+0x43): undefined reference to `Fl_Window::Fl_Window(int, int, char const*)'
fltk_test.cpp:(.text+0xf0): undefined reference to `fl_define_FL_SHADOW_LABEL()'
fltk_test.cpp:(.text+0x10a): undefined reference to `Fl_Group::end()'
fltk_test.cpp:(.text+0x128): undefined reference to `Fl_Window::show(int, char**)'
fltk_test.cpp:(.text+0x12d): undefined reference to `Fl::run()'
/tmp/ccEywTYb.o: In function `Fl_Box::Fl_Box(int, int, int, int, char const*)':
fltk_test.cpp:(.text._ZN6Fl_BoxC1EiiiiPKc[Fl_Box::Fl_Box(int, int, int, int, char const*)]+0x30): undefined reference to `Fl_Widget::Fl_Widget(int, int, int, int, char const*)'
fltk_test.cpp:(.text._ZN6Fl_BoxC1EiiiiPKc[Fl_Box::Fl_Box(int, int, int, int, char const*)]+0x35): undefined reference to `vtable for Fl_Box'
collect2: ld returned 1 exit status

```
What could be the problem?!?!

From the fltk documentation:

> Compiling Programs with Standard Compilers

Under UNIX (and under Microsoft Windows when using the GNU development tools) you will probably need to tell the compiler where to find the header files. This is usually done using the -I option:

      CC -I/usr/local/include ...
      gcc -I/usr/local/include ...

The fltk-config script included with FLTK can be used to get the options that are required by your compiler:

      CC `fltk-config --cxxflags` ...

Similarly, when linking your application you will need to tell the compiler to use the FLTK library:

      CC ... -L/usr/local/lib -lfltk -lXext -lX11 -lm
      gcc ... -L/usr/local/lib -lfltk -lXext -lX11 -lm




Might be worth a read.

---

### Post by Xarver on 2008-08-27
I try -I/usr/include/FL
and g++ -I/usr/include/FL
AND g++ fltk_test.cpp -o FLTK -I/usr/include/FL

But they don't work!!!
AH!

---

### Post by Xarver on 2008-08-28
I haven't gotten an answer yet and would be happy if someone can solve this problem.

:)

---

### Post by granadajose on 2009-10-25
Hi,

I don't know if you will still be interested in this, but I run into exactly the same problem as you. This is how I fix it:

I installed TLFK using:

sudo aptitude install fltk1.1-doc libfltk-dev libfltk1.1 libfltk1.1-dbg libfltk1.1-dev fluid

(This is from your post!)

Then I wrote the following program in C++ and saved it as Hello.cpp:
#include <FL/Fl.H>
#include <FL/Fl_Window.H>
#include <FL/Fl_Box.H>

int main(int argc, char **argv) {
Fl_Window *window = new Fl_Window(300,180);
Fl_Box *box = new Fl_Box(20,40,260,100,"Hola mundo");
box->box(FL_UP_BOX);
box->labelsize(36);
box->labelfont(FL_BOLD+FL_ITALIC);
box->labeltype(FL_SHADOW_LABEL);
window->end();
window->show(argc, argv);
return Fl::run();
}

Then, I compilled it using:
g++ -Wall -o Hello.cpp Hello  -L/usr/include/FL -lfltk -lX11 -lm

And, that's all! It simply works!

Hope this helps!

Jose

---

