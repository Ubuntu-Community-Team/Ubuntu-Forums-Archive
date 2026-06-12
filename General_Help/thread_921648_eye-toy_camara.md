---
title: "eye-toy camara?"
date: 2008-09-16
forum: General Help
---

### Post by Monotoko on 2008-09-16
Hiya people, im trying to switch completly from windows, as vista annoys me and i no longer have XP, so i thought id try a linux distribution.

Only thing is, in Windows Live Messenger (i use aMSN on ubuntu) it allowed me to connect my eye-toy with a little bit of hacking the driver files, im wondering if thats possible here?

If so, an i have some instructions, as i am a complete newb with linux
thanks :)

---

### Post by ronnielsen1 on 2008-09-16
sudo apt-get install kopete

should do it

---

### Post by Monotoko on 2008-09-16
okay, i done that, it did a lot of random non-understandable stuff in the terminal.

I tried to plug my eye-toy in afterwards, but its still not working

---

### Post by Monotoko on 2008-09-16
ahh i see, its another client, i shall try it

EDIT: Okay, its loaded up, i logged in, but how do i get it to know that the eye-toy is there?? like, i have to install the drivers using the add new hardware wizard in windows, what must i do in linux?

---

### Post by Toxicity999 on 2008-09-16
there's a lot of information around about getting it to work. I used to use it myself. Just doing some searches for "eye toy, linux" should turn up enougn information for you to come back abnd ask some specific questions.

---

### Post by Monotoko on 2008-09-16
i found this: [http://alpha.dyndns.org/ov511/download.html#1.xx](http://alpha.dyndns.org/ov511/download.html#1.xx)

but it only supports up to kernal 2.5, i have 2.6.....

---

### Post by Toxicity999 on 2008-09-16
I'm not sure if it's still in hardy, but try this

sudo apt-get update
sudo apt-get install ov51x-jpeg-source module-assistant
sudo module-assistant -t a-i ov51x-jpeg

Also, I should explain what this is doing, for you. All this does, is fetch the source code of a "module" which can talk to your hardware properly. A module, in this case, essentially being a liason between the real drivers, and the kernel, teaching the kernel how to interact with your webcam. *Usually* you won't have to go through this crap, most things are just supported out of the box. but due to CD size restriction, we trim a lot of the fat out, in the form of these fringe hardware drivers not too many need (as far as I know, anyway).

---

### Post by Monotoko on 2008-09-17
Thank you very much, i ran that, and it worked very well, right up until the last few lines, on which i got:

# Build the module
/usr/bin/make KERNEL_DIR=/usr/src/linux KVERS=2.6.24-19-generic
make[2]: Entering directory `/usr/src/modules/ov51x-jpeg'
/usr/bin/make -C /lib/modules/2.6.24-19-generic/build M=/usr/src/modules/ov51x-jpeg modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.o
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:6611: error: unknown field ‘hardware’ specified in initialiser
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:6611: error: ‘VID_HARDWARE_OV511’ undeclared here (not in a function)
make[4]: *** [/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.o] Error 1
make[3]: *** [_module_/usr/src/modules/ov51x-jpeg] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/src/modules/ov51x-jpeg'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/ov51x-jpeg'
make: *** [kdist_build] Error 2
BUILD FAILED!
See /var/cache/modass/ov51x-jpeg-source.buildlog.2.6.24-19-generic.1221647527 for details.
Build failed. Press Return to continue...

Why did it fail? Sorry, i feel rather stupid asking all these questions, but im sure il get used to ubuntu...its better than windows, just differant (which iv been using since my first computer)

---

### Post by Toxicity999 on 2008-09-17
Alright, try this:

```
sudo apt-get install build-essential linux-headers-`uname -r`
cd
wget http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.8.tar.gz
tar -xvf ov51x-jpeg-1.5.8.tar.gz
cd ov51x-jpeg-1.5.8
sudo make install 
sudo modprobe videodev 
sudo modprobe i2c_core
```Then open cheese, and test it.

If that works, add videodev and 12c_core, on their own lines, to /etc/modules (edit as root, gksu gedit /etc/modules for example)

And if THAT doesn't work... try 1.5.3 (replace all instances of 1.5.8 with 1.5.3 in that code snippet)

---

### Post by Monotoko on 2008-09-17
that didnt work...and 1.5.3 gives me a 404 message

---

### Post by Toxicity999 on 2008-09-17
Weird, same error? that should compile on the latest kernel. I haven't had to hack the eyetoy in to submission for years, so my help is limited right now.

---

### Post by Monotoko on 2008-09-18
thats alright, il keep using windows for it until i can figure it out.

If anyone knows anything that can help, it would be greatly appriechiated

---

