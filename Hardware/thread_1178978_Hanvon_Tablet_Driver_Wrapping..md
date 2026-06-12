---
title: "Hanvon Tablet Driver Wrapping."
date: 2009-06-05
forum: Hardware
---

### Post by Clowdstride on 2009-06-05
Currently running Ubuntu 9.04, and would like to use my Hanvon Paint Master tablet.
I hear that there are many people who have emailed the company and they don't have linux support.
A while ago I heard that it's possible to 'wrap' a windows driver to make it compatible in linux. Is this possible to do with the Hanvon Paint Master tablets?

Sorry for short post, but there's not much more to say.

~Wyth~

---

### Post by Clowdstride on 2009-07-07
I have emailed the Hanvon Services email this message.

To whom it may concern:

    My Hanvon PaintMaster 0806 has served me quite well over the years, but
only in Windows. Recently my version of Windows has taken a turn for the
worse and I no longer have a re-install disc. So, like 29 million
others, I installed a Linux operating system.

    I am very sad to report that I have gotten EVERY piece of hardware I
own to work with Linux except for my Hanvon tablet. I understand that
many people also are having a problem with owning a Hanvon and running
Linux and not having any way to use it.I also understand that many have
mailed you and asked for you to either support the Linux system or to
release source codes for coders to make Hanvon tablets work with Linux
for you. 

    I am not really here to request either of those; I'm just here to let
you know what while Linux is becoming much more popular around the
world, you are causing yourself to lose many many sales due to the fact
that Wacom supports Linux and not Hanvon. Just the number of users that
would begin using a Hanvon tablet with Linux should be enough to spread
the word about Hanvon and gain you very hefty increase in sales. And all
of that just for releasing a Linux driver. I honestly do not understand
why you would want to miss this chance.

    Either way you chose to approach this problem, I will continue to own
my Hanvon and await a day that it may work with Linux. Though what I
cannot promise is that I will only limit myself to a non working Hanvon
tablet nor that I will promote the products that your company
manufactures. When it comes time for me to upgrade to a higher quality
tablet, also do not expect me to purchase a tablet that I will not be
able to use. 

    I hope very much that you will think of what I have said, and honestly
consider your own gain from it. If you help me, you will also be helping
yourself, and for which I will do my best to help you.


   With regards, 
        Xxxxxxxxxx Xxxxxxxxxx

---

### Post by Favux on 2009-07-13
Hi Clowdstride,

Is it possible that the Hanvon Paint Master tablet is in fact a rebranded tablet from another manufacturer?  This appears to be a relatively common practice.  If so, despite what they say, it may be supported in linux.  For some examples of what I'm talking about see:

practic's post #11 here:  [http://ubuntuforums.org/showthread.php?t=1151464&page=2](http://ubuntuforums.org/showthread.php?t=1151464&page=2)
He lists some useful commands to identify your device, if it has been rebranded.

the WizardPen wiki:  [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

I hope this is useful.

---

### Post by ondrah on 2011-03-14
Hi all,

i've developed a driver for am 0806 which seems to work.

[http://linux.fjfi.cvut.cz/~taxman/hw/hanvon/](http://linux.fjfi.cvut.cz/~taxman/hw/hanvon/)

Cheers, oh

---

### Post by andyart on 2011-07-07
Hi, I couldn't use the driver with ubuntu 11.04. Has anyone accomplished it or knows how to ?

---

### Post by JDacapo on 2011-09-11
> **ondrah said:**
> Hi all,

i've developed a driver for am 0806 which seems to work.

[http://linux.fjfi.cvut.cz/~taxman/hw/hanvon/]("http://linux.fjfi.cvut.cz/%7Etaxman/hw/hanvon/")

Cheers, oh

I'm still new to Linux and I don't know how to install this driver. Even after reading the instructions, I'm still having problems. Can you make some more detailed instructions?

---

### Post by Favux on 2011-09-12
Hi JDacapo,

Welcome to Ubuntu forums!

Sure, the README isn't very detailed is it?

Actually compiling the kernel module is straight forward.  In a terminal change directory into the unpacked hanvon folder, i.e. *cd hanvon*.  Path depending on where you downloaded it of course. Then in that folder issue the:
```
make
or
make all
```
command.

You'll notice you went from just 3 files README, Makefile, and hanvon.c to several new ones the one you're interested in is hanvon.ko.  That's the kernel module/driver you need.  What's happened is hanvon.c has been run through the gcc compiler.

Now the part that was left out is what to do with your new kernel driver.  You could do a *insmod* and load it right away to test it:
```
sudo insmod ./hanvon.ko
```
If it works then to make it available through a restart you need to copy it into the appropriate modules directory.  So next issue this command:
```
sudo cp hanvon.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet

```
Then you want to rebuild all of the module dependenies:
```
sudo depmod -a
```
Now when you reboot the driver should automatically be loaded.

---

### Post by JDacapo on 2011-09-12
I've tried the make command but it would give me this:

make -C /lib/modules/2.6.38-11-generic/build M=/home/gina/Downloads/hanvon modules
make[1]: Entering directory `/lib/modules/2.6.38-11-generic/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.38-11-generic/build'
make: *** [all] Error 2


Would 'make all' give me the desired results? Or do I need to install some other stuff? This is a bit confusing. I still love Linux though because it's running on this rickety old Toshiba while the Windows on the other side of the partition is ancient and takes forever to even do the simplest thing!

---

### Post by Favux on 2011-09-12
Sure try *make all*.  It could be you are missing some build dependencies.  Have you installed the gcc compiler for example?  To install the basic build stuff enter:
```
sudo apt-get install build-essential
```

---

### Post by JDacapo on 2011-09-12
I already have all those packages. Just tried installing them but it said I already have all the essential packages. And I've tried 'make all' but it still gives me the same message. It wouldn't even make those folders at first... I had to make the folder for 'generic/build' for example. Is there any other thing that could be wrong with my system? I also have the gcc compiler. Is there anything else that I might need?

---

### Post by Favux on 2011-09-12
Hmmm.  What is the directory path to the hanvon folder?  If there is an illegal character that could be the problem.  For example the Desktop will let you put a space in the name or another illegal character but the shell commands won't allow that.

What did you do with this for example?
```
generic/build
```

Ahhh, maybe you need the kernel headers:
```
sudo apt-get install linux-headers-generic
```
Try that.

---

### Post by JDacapo on 2011-09-12
I installed the headers. Tried both 'make' and 'make all' commands but still I get the same errors. The directory path for the folder is: /home/gina/Downloads/hanvon

Are there any other programs that I need? Or do I need to reboot?

---

### Post by Favux on 2011-09-12
Sure try a reboot to shake things out.  I don't know what the problem is because the error message doesn't seem real informative.  What I would do is before recompiling when in the hanvon folder is issue a:
```
make clean
```
before redoing *make*.  The Makefile allows it and there might be something hanging around from a compile pre-needed dependency blocking a new compile I suppose.

I went ahead and compiled it and here is my compile output for comparison:
```
~$ cd Desktop
~/Desktop$ cd hanvon
~/Desktop/hanvon$ ls
hanvon.c  Makefile  README
~/Desktop/hanvon$ make
make -C /lib/modules/2.6.35-30-generic/build M=/home/favux/Desktop/hanvon modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-30-generic'
  CC [M]  /home/favux/Desktop/hanvon/hanvon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/favux/Desktop/hanvon/hanvon.mod.o
  LD [M]  /home/favux/Desktop/hanvon/hanvon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-30-generic'

```
So why is it entering the /usr/src/ directory on my system and /lib/modules/ on yours?  The only difference I can see is I downloaded it on the Desktop and compiled it there.

I have a bunch of extra libraries installed to compile other things, mainly the Wacom kernel module wacom.ko.  I suppose it's possible it's one of those libraries that is needed.


Edit:  Oops, the obvious finally jumps out at me.  You are compiling in Natty and I am doing it in Maverick.  He says he compiled on 2.6.38 but I should boot into Natty and check.

---

### Post by Favux on 2011-09-12
Nope, no problem in Natty either.

In /usr/src do you have linux-headers-2.6.35-30-generic or whatever your current kernel number is?

---

### Post by JDacapo on 2011-09-12
> **Favux said:**
> Nope, no problem in Natty either.

In /usr/src do you have linux-headers-2.6.35-30-generic or whatever your current kernel number is?

Here are the folders in my /usr/src folder:

alsa
linux-headers-2.6.38-8
linux-headers-2.6.38-8-generic
linux-headers-2.6.38-11
linux-headers-2.6.38-11-generic
nvidia-current-270.41.06
virtualbox-ose-4.0.4

Would there be any conflicts with the different headers?

---

### Post by Favux on 2011-09-12
No that shouldn't be a problem.  Well other than having the proprietary fglrx for nvidia and not having alsa or virtualbox they seem the same.

I don't know why it won't build and the error message is probably telling us but I don't understand it.  Not clear enough for me.

These are the libraries I install for building wacom.ko:
```
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev autoconf libtool
```
I'm thinking maybe you need xserver-xorg-dev and some of the X11 ones.  You probably don't need others like libxrandr-dev but what the heck.  Just install all of them and try to compile it again.  Trying to figure out which ones you need, if that's the problem, would take too long.  Worst case is you have some unneeded libraries.

---

### Post by JDacapo on 2011-09-12
I installed all the listed dependencies, but it still is giving me that same error. What else could be wrong?

---

### Post by Favux on 2011-09-12
In the Makefile:
```
all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
```
it's pointing to the build file that has symbolic links.  I think there is an include file that in there that is suppose to point to your kernel headers.  Check and see if you have a file /lib/modules/`uname -r`/build with an include in it.

---

### Post by JDacapo on 2011-09-12
I can't find 'modules' in the lib folder. This is weird.

---

### Post by Favux on 2011-09-12
Aright, then that's likely the problem.

Since I don't know why it isn't there let's try going nuclear on the thing.  There's no longer a kernel-devel package but you can pull in everything with:
```
sudo apt-get build-dep linux
```
Then reboot I suppose.

This is the BFMI (brute force and massive ignorance) approach.  My favorite.  Fingers crossed.

---

### Post by JDacapo on 2011-09-12
> **Favux said:**
> Aright, then that's likely the problem.

Since I don't know why it isn't there let's try going nuclear on the thing.  There's no longer a kernel-devel package but you can pull in everything with:
```
sudo apt-get build-dep linux
```Then reboot I suppose.

This is the BFMI (brute force and massive ignorance) approach.  My favorite.  Fingers crossed.

I tried that... it didn't install anything. Then I rebooted and it still won't work. Anyway, what's the exact path that's supposed to be created? I just want to be able to compile a simple program :(

---

### Post by Favux on 2011-09-13
Shoot, I hear you.  It shouldn't be this hard.

I just compiled it on my laptops Natty install unfortunately.  I was hoping I could duplicate the problem.  But no...

I'm stumped.  I pretty sure the obvious is staring me in the face and I'm just missing it.

---

### Post by JDacapo on 2011-09-13
Hope someone can help us both shed some light on this.

EDIT: I had created those folders that it was complaining about not having the 'rules' for. I wonder if this is what is causing the problems. There anyone else here who can help us both?

---

### Post by aeriph on 2012-06-20
I'm having the same issue, kernel 3.2.0-23-generic

Tried installing that driver, doesn't give any errors but it doesn't work either.

Does anyone have any new developments in getting this working?

---

