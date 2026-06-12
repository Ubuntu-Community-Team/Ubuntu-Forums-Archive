---
title: "How to obtain linux-headers .c file"
date: 2008-10-29
forum: General Help
---

### Post by belbo on 2008-10-29
I'm a noob. I'm trying to apply a diff file in order to compile a driver module to enable analogue tuning for my hybrid/ analogue tv tuner. 

The diff file starts off with the following lines -

|diff -Naur /usr/src/linux-headers-2.6.24-19/drivers/media/video/cx88/cx88-cards.c /usr/src/linux-headers-2.6.24-19/drivers/media/video/cx88-patched/cx88-cards.c


I have installed the linux-headers-2.6.24-19 and do have the directory /usr/src/linux-headers-2.6.24-19/drivers/media/video/cx88. However, that directory does not include the file cx88-cards.c. It contains only the files Makefile and Kconfig. (I am actually on 2.6.24-21, but the linux-headers for that also don't contain the .c file).

My question is how do I obtain the .c file ?


Any help would be appreciated. 

For what its worth I tried the following (the diff file being called dtv2000h-analogue )-

ben@htpc:/usr/src$ patch -p0 < dtv2000h-analogue


and got the following result (not surprisingly) -

can't find file to patch at input line 4

Perhaps you used the wrong -p or --strip option?

The text leading up to this was:

--------------------------

|diff -Naur /usr/src/linux-headers-2.6.24-19/drivers/media/video/cx88/cx88-cards.c /usr/src/linux-headers-2.6.24-19/drivers/media/video/cx88-patched/cx88-cards.c

|--- /usr/src/linux-headers-2.6.24-19/drivers/media/video/cx88/cx88-cards.c	2007-10-09 22:31:38.000000000 +0200

|+++ /usr/src/linux-headers-2.6.24-19/drivers/media/video/cx88-patched/cx88-cards.c	2008-01-10 19:24:06.000000000 +0100

--------------------------

File to patch: 



Also, for what its worth (and if people are happy to correct me/ elaborate to help my understanding), my understanding/ surmising about how this all works is as follows -

Presumably the diff file requires the following file against which to apply the patches -

/usr/src/linux-headers-2.6.24-19/drivers/media/video/cx88/cx88-cards.c

and the resulting patched file is then output as -

/usr/src/linux-headers-2.6.24-19/drivers/media/video/cx88-patched/cx88-cards.c

Presumably the .c indicates a file written in C and the patched .c file is then compiled into a module (.o or .ko extension ?) which is then loaded via modprobe at boot time, providing the required driver capability.

---

### Post by thomas228 on 2008-10-29
Did you install the packages:

linux-libc-dev and libc6-dev?

They helped e compile my wifi drivers

Just a guess
Tom

---

### Post by belbo on 2008-10-29
Thanks for helping. I do have both of those installed. I got the following messages when 'apt-get install'ing them -

libc6-dev is already the newest version.
libc6-dev set to manually installed.

linux-libc-dev is already the newest version.
linux-libc-dev set to manually installed.

I wonder if the 'set to manually installed' has anything to do with the missing .c files ?

Any ideas anybody ?

BTW - How do I register the 'thanks' I have made to people ?

Regards

---

### Post by lourp on 2009-02-20
Was this resolved? I've got the same problem - can't find the source code to modify.

But also, I don't know how to actually APPLY these mods into the kernel permanently.

I want to workaround this bug as per [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/211652]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/211652")

Can anyone help?

---

