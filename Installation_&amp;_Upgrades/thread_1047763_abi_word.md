---
title: "abi word"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by nneedrelief on 2009-01-22
if this isn't the right place for me please let me know where i should post this thread

hello.

I'm using an eeepc 900 20gb with array.org's kernel and I noticed abi word has a 2.6.6 out.

i've been to the abi source downloads here: [http://abisource.com/wiki/Install_on_Ubuntu](http://abisource.com/wiki/Install_on_Ubuntu)
i followed the instructions but its not showing any updates. Abi word is one of the only things i use on my computer so it would be nice if i could get a better version

is the array kernel not allowing the repository or am i just confused?

anything would help, thanks

---

### Post by hansdown on 2009-01-22
Hi       nneedrelief.   

It's in a tar gz here.

[http://www.icewalkers.com/Linux/Software/55720/AbiWord.html](http://www.icewalkers.com/Linux/Software/55720/AbiWord.html)

---

### Post by x33a on 2009-01-22
here's a link to the repositories.

[https://launchpad.net/~abiword-stable/+archive](https://launchpad.net/~abiword-stable/+archive)

---

### Post by nneedrelief on 2009-01-22
how do you install tar gz files?

---

### Post by x33a on 2009-01-22
you have to compile them. 

if you don't want to compile, you can use the repositories i posted.

---

### Post by nneedrelief on 2009-01-22
thats exactly the problem

when i did what you said it didn't work. That's what i did originally. It doesn't work

That's why i started this thread

unless you can suggest something that i may have done wrong, something blocking it from working, or anything else

but i have copied pasted the lines exactly so that's not the problem

so how do i use tar gz's?

---

### Post by x33a on 2009-01-23
to add repositories:

1. go to system -> administration -> software sources.
2. click on third party software.
3. click on add and copy-paste this line:
deb [http://ppa.launchpad.net/abiword-stable/ubuntu](http://ppa.launchpad.net/abiword-stable/ubuntu) intrepid main
4. reload the sources list when it asks to.
5. after reloading, you'll have updates available if you have an older version of the software. install them.

to compile from source:

first type: sudo apt-get install build-essential, then

1. download the tar.gz file on your desktop.
2. open a terminal, and cd into the desktop directory.
3. type tar xvzf filename.gz, this will extract the contents of the compressed file.
4. cd into the newly created directory.
5. read the install.txt or readme.txt file for installation instructions.
6. usually you have to type these commands:
    a) ./configure
    b) make
    c) sudo make install

---

### Post by nneedrelief on 2009-01-23
thanks for understanding, your instructions worked perfectly and for my next repos i'll remember your first set of instructions

thanks again

Yaser Eid

---

