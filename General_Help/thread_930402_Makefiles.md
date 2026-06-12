---
title: "Makefiles"
date: 2008-09-26
forum: General Help
---

### Post by Xonara on 2008-09-26
I'm a bit confused about compiling things on linux. What exactly are makefiles for and how should I use them? How are they any better than just compiling the source to an exe? Thanks :popcorn:

---

### Post by ad_267 on 2008-09-26
If you're making a huge project then the whole autotools suite allows anyone to compile your code on a Unix like system.

I use makefiles for just basic projects because it means everytime I want to compile I only have to type make. With a big enough project the compiling command can be pretty huge. It also only compiles the code that it needs to based on which files have been updated. It's also pretty easy to change which flags you use, what compiler and where libraries are located using variables.

Also compiling on Linux is a bit different to Windows because a lot of people don't use an IDE like Visual Studio, Borland or Eclipse etc. I do my programming in gedit or vim and want to be able to compile from the command line rather than having to use an IDE to compile my code. 

Do a search for makefile tutorials and have a go and see if you like them, it takes a little while to get the hang of. If it's not your thing you can use an IDE to sort that stuff out for you, but a lot of these in Linux use the GNU build system under the hood.

This is a good tutorial that just explains the basics and will get you on your feet with makefiles: [http://mrbook.org/tutorials/make/](http://mrbook.org/tutorials/make/)

---

### Post by Xonara on 2008-09-26
Yeah, I'm not exactly doing any big projects right now... "Crap, I forgot the semicolon." Heh. Anyways, it's been bugging me for a while and that tutorial is very helpful. Thanks :P

---

### Post by Xonara on 2008-09-27
How does make decide if a file is new or not? Is there a file cache or does it log save dates?

---

### Post by ad_267 on 2008-09-27
It looks at the timestamp on the file and compares that to the timestamp of the file it is building. If the file has been modified more recently than the file was last built then it needs to be rebuilt. You can see when the file was last edited in the Date Modified column in the file browser or if you use "ls -l" in the command line.

---

