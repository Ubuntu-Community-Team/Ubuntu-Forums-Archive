---
title: "How to start creating applications"
date: 2008-08-07
forum: General Help
---

### Post by z.s.tar.gz on 2008-08-07
Before you read this post, let me get a few things straight.
1. I know C++ but can learn other languages.
2. I have never used Visual Studio.
3. I want to know how to make graphical applications for ubuntu/gnome.
4. I know how to compile, debug, etc.

So, what I want to know is: Where should I start to create graphical programs in ubuntu? Can anyone point me to some tutorials?

---

### Post by Archimedes0212 on 2008-08-07
I guess you can use C/C++.  I've never done graphical applications with either although I have with C# in microsoft VS.

Currently I am writing some graphical apps in Python with its built in graphical components, Tkinter.

I've heard that QT works well for graphical design, although I personally have never used it.


Compiling depends on the language.
C:  gcc filename.c
C++: g++ filename.cpp
python: python filename.py
perl: perl filename.pl

(i know the last two are interpreted languages)

those are the command line tools for compiling(/interpreting).  There are some IDEs that you can compile and run from (none come to me right now).

Oh, before I forget (sorry about the hopping back and forth) you can develop in Java.  It works on all platforms and is very easy to make interfaces with.

for debugging, in linux I use gdb (again, command line)

Hope this is a good start.  Happy coding!

---

### Post by dexter.deepak on 2008-08-07
in linux world, i think you should not restrict yourself to developing "applications for ubuntu".
if you have interest in gui development for linux you can try :
1. Qt - uses C++ , and will mostly work for KDE
2. GTK+ - uses C , will work mostly on GNOME
3. learn java, and go got java-gnome,its new

---

### Post by z.s.tar.gz on 2008-08-07
ill look for a gtk+ tutorial.

If you have a recommendation, that would be helpful.

---

### Post by ibuclaw on 2008-08-07
How will you be creating your apps?

Which text editor/IDE do you have?

There are quite a few around, each with their uses and advantages.
From **Vim** to **Gedit** to **Geany** to **Code::Blocks**.

What sort are you looking for?

Regards
Iain

---

### Post by Taxman415a on 2008-08-07
You probably want to start at [http://developer.gnome.org/](http://developer.gnome.org/) then follow the links to documentation and developer tools. Also have a look at [http://library.gnome.org/devel/hig-book/stable/](http://library.gnome.org/devel/hig-book/stable/) the usability guidelines. Here's more:
[http://library.gnome.org/devel/](http://library.gnome.org/devel/) including specifically the guides listed on that page have a few tutorials and this one from the references link there:
[http://library.gnome.org/devel/gtk/stable/](http://library.gnome.org/devel/gtk/stable/)

I don't know anything about Glade, that seems to be what they recommend. So in short Gnome's website should give you enough info to get going on gtk+ and I'm sure you could find comparable material on qt if you wanted.

---

### Post by babylon2233 on 2008-08-07
You can use whatever language you want to program a Linux GUI application. What you need is interface designer and a text editor along side with other programming tools such as compiler. One example of interface designer is Glade.

---

### Post by doas777 on 2008-08-07
on linux I use netbeans and eclipse to make java guis. 
BTW. I use Visual studio on my windows apps (work stuff) and while i hate M$, it is by far the best IDE i've ever used. 

I'll prolly get kicked outta here for admiting that, but there it is.

---

### Post by cszikszoy on 2008-08-07
You might want to look into Monodevelop.  It has an IDE similar to visual studio.  Mono is basically the open source version of c#.  Mono has great GTK bindings as well.

---

### Post by Taxman415a on 2008-08-07
> **doas777 said:**
> BTW. I use Visual studio on my windows apps (work stuff) and while i hate M$, it is by far the best IDE i've ever used. 

I'll prolly get kicked outta here for admiting that, but there it is.

Well, they didn't maintain their market dominance without some tools and products that were worthwhile, it's just the dirty tricks and forced lock in that make them so easy to dislike. But either way, no one will kill you for calling it like you see it.

---

