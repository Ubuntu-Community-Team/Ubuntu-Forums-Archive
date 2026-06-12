---
title: "[SOLVED] Turbo C++ in Ubuntu"
date: 2008-11-27
forum: General Help
---

### Post by iampriteshdesai on 2008-11-27
I wan to install Turbe C++ in Ubuntu. I have the installer firle but with Wine the installer gets stuck with "finding BIN.zip"
How can I run turbo c++? I need it for school, G++ wont do, anyways it doesn't have a gui,
I tried using Dosbox but it didnt work!

---

### Post by ashmew2 on 2008-11-28
Why do i have a feeling that you too are in india..hehe..

Well i got Turbo C++ to work with dosbox. Are you using Ubuntu 64 Bit or 32 Bit ? If you dont know , you are probably using 32 bit. Btw , What problems did you have when running dosbox ? I have coded lots of stuff with Turbo C++ inside dosbox.

---

### Post by iampriteshdesai on 2008-11-28
Hi!
I tried Dosbox but dont know how to use it, it doesnt have a gui.
How to setup stuff with it?
Can you plz help, I have 32 bit system.
I need TC for school. I have TC version 5 or 6 installed and TC ver 2.0 installer file.

---

### Post by justborn on 2008-11-28
why won't g++ work?

---

### Post by iampriteshdesai on 2008-11-28
G++ doesnt have a gui and I am almost a noob. TC is very easy to use, Dev C++ is an idiot which always gives an error saying that Source not compiled even after compiling it 10 times. Also my college uses TC

---

### Post by Bibek on 2008-11-28
write your code in gedit. save it as name.cpp
in the terminal compile using "gcc name.cpp"

---

### Post by iampriteshdesai on 2008-11-28
I'd rather wait for GUI

---

### Post by ashmew2 on 2008-11-28
Instructions : 

Keep the installation files inside a folder of your home directory named "setup".
Open up dosbox.
Type in :
```

mount c ~

cd setup
install.exe

```

This will start the setup of Turbo C.

After setup is finished , do :
```

c:
cd TC\bin
tc.exe

```

---

### Post by iampriteshdesai on 2008-11-28
Sure thanks!

---

### Post by ashmew2 on 2008-11-28
Pritesh , If you wanna be a programmer or something better with C++ than school level nonsense..I'd suggest you use a better and newer compiler like Code:Blocks.
I too have the Turbo C++ at school thingy, but Code blocks is far sleek and sexier than Borland's Turbo C!

---

### Post by iampriteshdesai on 2008-11-28
Hi, thanks!
I tried it and it worked!
When Dosbox is on my window doesnt insteract with anything else still it is far better than not having TC. thanks!
Can I use your tutorial for my blog?
Or rather would you like to write that post yourself?

You are a student too?

---

### Post by ashmew2 on 2008-11-28
Yes , dosbox captures the cursor..You can make it leave the cursor by pressing Ctrl as far as i remember , Fullscreen is Alt-Enter ;)

You are free to write the tutorial on the blog! Yes im in school as well , Class XI..

---

### Post by iampriteshdesai on 2008-12-20
Hi!
here is the link to the blog: [http://helpforlinux.blogspot.com/2008/12/install-borland-turbo-c-in-ubuntu.html](http://helpforlinux.blogspot.com/2008/12/install-borland-turbo-c-in-ubuntu.html)

---

### Post by ashishchandra on 2011-09-17
Hey, I am using Anjuta compiler....it works well for both c and c++.
Worth a try...

---

