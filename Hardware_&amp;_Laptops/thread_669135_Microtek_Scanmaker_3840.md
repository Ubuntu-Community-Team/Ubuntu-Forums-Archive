---
title: "Microtek Scanmaker 3840"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by Malinthe on 2008-01-16
I moved from Windows to Ubuntu few days ago. I've tried Ubuntu 7.04 and I have installed Ubuntu 7.10 64-bit version on my 64-bit AMD machine. Currently, I am unable to get my scanner to work with Gutsy. It worked fine with the previous version of ubuntu and I've searched many forums and didn't find a solution.

The scanner is a Microtek Scanmaker 3840. When I load xsane it detects the scanner. After I select it I get this error message:

Failed to open device 'sm3840:libusb:002:004': Access to resource has been denied.

I tried many things but they didn't work. Including running xsane as root. None of them worked. Glad if anyone can fix this problem.

I installed Virtualbox and ran XP, the scannerworks with it fine. So what can be the problem?

---

### Post by fireedo on 2008-03-16
it has relation with libsane 0.19 or newer so you have to use libsane-sm3840 at least x.18 version just do this as root : 
cd /usr/lib/sane
rm libsane-sm3840.so.1
ln -s libsane-sm3840.so.1.0.18 libsane-sm3840.so.1
ok you're done
just run this as a user (as long as your're in the scanner group) :
scanimage -T
I hope it works
below I attached file libsane-sm3840.so.1.0.18

---

### Post by SumnerBoy on 2008-04-27
Hi - I am having a similar problem with a Canon MP530 multi-function scanner. I tried installing the v18 of the libsane you attached to your post but it didn't seem to make a difference.

Any other ideas or hints? I can run scanimage -T and SaneTwain (on my Windoze laptop) as long as it as root, but as soon as I try using saned:scanner it gives me the access denied message.

---

### Post by shinkaide on 2008-04-27
> **fireedo said:**
> it has relation with libsane 0.19 or newer so you have to use libsane-sm3840 at least x.18 version just do this as root : 
cd /usr/lib/sane
rm libsane-sm3840.so.1
ln -s libsane-sm3840.so.1.0.18 libsane-sm3840.so.1
ok you're done
just run this as a user (as long as your're in the scanner group) :
scanimage -T
I hope it works
below I attached file libsane-sm3840.so.1.0.18

Man, a BIG THANK YOU for that information! I've been stuck with a dead piece of hardware ever since I upgraded to 7.10 ... and now I was worried I'd still be stuck with it since 8.04 still had the same error message out of the box. Once again, thanks! 

I'm still buggered as to why this issue wasn't fixed with the new release... I just wonder... :confused:

---

### Post by kaladann on 2008-05-01
> **fireedo said:**
> it has relation with libsane 0.19 or newer so you have to use libsane-sm3840 at least x.18 version just do this as root : 
cd /usr/lib/sane
rm libsane-sm3840.so.1
ln -s libsane-sm3840.so.1.0.18 libsane-sm3840.so.1
ok you're done
just run this as a user (as long as your're in the scanner group) :
scanimage -T
I hope it works
below I attached file libsane-sm3840.so.1.0.18

i did it but now even scanimage -L cant see my scaner.. :(
previous in this point was ok. 

so i removed and installed again sane and xsane but ..no effect..xsane and kooka still cant see my microtek  :(((((

(i use hardy heron on kubuntu 64 bit ) 

ps sorry for my english .r

---

### Post by SPrevatt on 2008-05-15
> **fireedo said:**
> it has relation with libsane 0.19 or newer so you have to use libsane-sm3840 at least x.18 version just do this as root : 
cd /usr/lib/sane
rm libsane-sm3840.so.1
ln -s libsane-sm3840.so.1.0.18 libsane-sm3840.so.1
ok you're done
just run this as a user (as long as your're in the scanner group) :
scanimage -T
I hope it works
below I attached file libsane-sm3840.so.1.0.18

I'm a newbie to ubuntu and have had trouble executing these commands.  When I type the line:

rm libsane-sm3840.so.1

I get:

rm: cannot remove `libsane-sm3840.so.1': Permission denied

What do I need to do?  I only have one user set up.

---

### Post by SPrevatt on 2008-05-16
Okay, I figured out the sudo command to execute the necessary commands from root.  However, when I type 

[INDENT]scanimage -T[/INDENT]

the message I get is

[INDENT]scanimage: no SANE devices found[/INDENT]

:(

Suggestions?  Please?

---

### Post by shirokurokun on 2008-05-23
> **fireedo said:**
> it has relation with libsane 0.19 or newer so you have to use libsane-sm3840 at least x.18 version just do this as root : 
cd /usr/lib/sane
rm libsane-sm3840.so.1
ln -s libsane-sm3840.so.1.0.18 libsane-sm3840.so.1
ok you're done
just run this as a user (as long as your're in the scanner group) :
scanimage -T
I hope it works
below I attached file libsane-sm3840.so.1.0.18

Thank You! That woiks for me

---

### Post by w.olle on 2008-06-03
Same problem with ubuntu 8.04 (64bit) it doesn't work.
With X.18 the scanner is no longer found. With X.19 the scanner is found but permission is denied.
May it has to be a different libsane-sm3840.so.1.0.X for Ubuntu 64bit ??
Or something to compile for the 64bit ? :confused:

My scanner: SM4800 (same as SM3840).

---

### Post by w.olle on 2008-06-03
I finally got it solved with ubuntu 64bit. It's as I thought. You have to compile a 64bit version of the libsane-sm3840.so...
All needed files are available at [http://www.ziplabel.com/sm3840/](http://www.ziplabel.com/sm3840/) You have to download the following files: 
   - sane-backends-1.0.15.tar.gz
   - sm3840_patch2
   - sm3840_source5.tar.gz
extract "sane-backends-1.0.15.tar.gz" to any folder e.g. ../sm4800 (it will create a sub folder /sane-backends-1.0.15). 
copy "sm3840_patch2" & "sm3840_source5.tar.gz" to the same directory.

code:
sudo patch -p1 < sm3840_patch2
sudo tar zvxf sm3840_source5.tar.gz
sudo ./configure
sudo make clean
sudo make
sudo make install

This procedure will install the sane backends to /usr/local/lib
"scanimage -F" & "scanimage -T" should already work.
As Xsane is looking into /usr/lib please check that all files (sane-sm3840...) are the same as on /usr/local/lib 
libsane-sm3840.so.1 schould point to libsane-sm3840.so.1.0.15

Please find attached ready compiled files for ubuntu 64bit.

---

### Post by Arabia on 2008-06-08
kuck you all

---

