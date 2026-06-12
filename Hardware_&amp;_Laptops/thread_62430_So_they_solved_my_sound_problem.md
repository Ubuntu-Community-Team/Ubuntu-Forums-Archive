---
title: "So they solved my sound problem"
date: 2005-09-04
forum: Hardware &amp; Laptops
---

### Post by JensenDK on 2005-09-04
Hello,

Like so many other users I got a problem getting sound working. I've spent a couple of hours looking around for a solution and finally saw that they managed to fix this bug: 

[https://bugzilla.ubuntu.com/show_bug.cgi?id=9734](https://bugzilla.ubuntu.com/show_bug.cgi?id=9734)

Thats all jolly good and very very fine - but as a "human being"  - I have no idea whatsoever I should do with that patch? Should I print it and read it aloud to my computer? -- or is there some other way to apply such a patch?

Thanks in advance for any instructions/help any of you can supply.

Regards

/Martin

---

### Post by felipe on 2005-09-04
you could:

1) get a new kernel (if you know what you're doing)
2) just wait for the next ubuntu version, codename breezy, to come out (very soon), then upgrade via synaptic

---

### Post by JensenDK on 2005-09-05
Hey,

Thanks for the suggestions, but I think you missed my point entirely: when i write that I have no idea what I should do with the patch - I mean that I have no idea what I should do with the patch.

I can compile a new kernel following the instructions here: [http://www.ubuntuforums.org/showthread.php?t=56835&highlight=compile+kernel](http://www.ubuntuforums.org/showthread.php?t=56835&highlight=compile+kernel)

But is the patch included in the .11 version? what should I do to make sure the changes are included?

Regarding using breezy - that is still a bit too experimental for my taste. I need a working desktop system for - nothing more, nothing less  :grin:

---

### Post by felipe on 2005-09-05
ok ok :)

for the patch being included in .11 you should read the kernel.org changelogs to make sure, in any case i wouldn't go and patch a kernel with some code taken who-knows-where. YMMV of course

anyway type `man patch` to know more about how to do that. normally something like `cat file.patch | patch -p1` in the dir containing the files you want to patch... should be enough

hope this is what you were expecting to read, my tips in comment #2 stay valid though, a human being shouldn't care about kernel compilations and patches. :)

---

### Post by hashimoto on 2005-09-05
[QUOTE=JensenDK]Hey,

Thanks for the suggestions, but I think you missed my point entirely: when i write that I have no idea what I should do with the patch - I mean that I have no idea what I should do with the patch.
[/QUOTE]

As I have understood it, a patch is used for a source code. Thus, you need to use the patch tool and file to correct the source code and then compile. Me never done it...

Was the bug & patch for Hoary? If yes, then I guess they will release an updated/patched kernel and you can just sit and wait.

---

### Post by mlomker on 2005-09-05
Image 2.6.11-1 is available through Synaptic and it would be the easiest thing to try.  I don't have your particular sound card but I'm running a custom 2.6.13 kernel.  Have you tried just compiling the latest kernel and seeing if things work?  I used the ck patch set and my box is running great.

---

### Post by JensenDK on 2005-09-05
Hi everyone,

Thanks for your answers/suggestions.

I've checked the .11 kernel and the fix is not present there from what I can see. I've tried updating it anyway with no positive result. I'll try to see if I'm able to patch it myself (this is going to take alot of prayers and strong coffee).

Anyone got an idea how long it usually takes from the time a patch is "uploaded" till it ends up like a regular update?

Regarding a custom 2.6.13 kernel -- where could I find the files needed to compile that kernel? (or more specific the changelog to check if the patch is included in that).

Thanks again

/Martin

---

### Post by JensenDK on 2005-09-05
FYI: after fumbling around for a few additional hours I managed to get my soundcard working following the instructions in several of the other threads ;) 

/me so happy

Thanks for the help everyone!

/Martin

---

### Post by Kushou on 2005-09-05
hi, i got the same problem, could you kindly point out the link to solution? 

thanks in advance.

---

### Post by JensenDK on 2005-09-07
I followed the solution at this post:

[http://www.ubuntuforums.org/showthread.php?p=133272](http://www.ubuntuforums.org/showthread.php?p=133272)

However - I did a couple of things different, and got some stuff from other links etc. and that seemed to work: I've outlined below what I did: I have no idea what 50% of it means, but it worked anyway :)

1: Install a lot of different stuff

```

sudo apt-get install linux-tree
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install kernel-package
sudo apt-get install gcc
sudo apt-get install libncurses5
sudo apt-get install libncurses5-dev
sudo apt-get install libqt3-mt-dev

```

I have no idea if these are nessesary, but I needed some build tools and the kernel howto recommened getting these. Since I'm pretty clueless it seemed like the thing to do. 

2: I then downloaded the headers for the kernel: 

```

apt-get install linux-headers-2.6.10-5-686 

```

Again I was not sure if I needed these, but they seemed awefully nice to have. 

3: I then downloaded the alsa drivers (alsa is apparently some kinda sound system in ubuntu) from [http://www.alsa-project.org/download.php](http://www.alsa-project.org/download.php). You can grap the package directly using this command:

```

wget ftp://gd.tuwien.ac.at/opsys/linux/alsa/driver/alsa-driver-1.0.9rc4a.tar.bz2

```


4: I then unpacked the alsa driver stuff under /usr/src:

```

sudo mv alsa-driver-1.0.9rc4a.tar.bz2 /usr/src/
cd /usr/src
sudo tar -xvjf alsa-driver-1.0.9rc4a.tar.bz2
cd alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712

```

4: Now... the problem for me was apparently that a pointer in the file vt1720_mobo.h is incorrect. We need some kinda identification number or something: I did a: 

```

sudo lspci -d 1412:1724 -nvx

```

This gave an output along the lines of: 

```

0000:05:06.0 0401: 1412:1724 (rev 01)
Subsystem: 1297:5036
Flags: bus master, medium devsel, latency 32, IRQ 18
I/O ports at a000 [size=32]
I/O ports at a400 [size=128]
Capabilities: [80] Power Management version 1
00: 12 14 24 17 05 00 10 02 01 00 01 04 00 20 00 00
10: 01 a0 00 00 01 a4 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 97 12 36 50
30: 00 00 00 00 80 00 00 00 00 00 00 00 0c 01 00 00

```

You then need to write down the 8 numbers at the end of the 2nd last line: in the example above "97 12 36 50". This was different for me and will probably also be for you. Anyway: just type them down!

5: I then opened the file sound/pci/ice1712/vt1720_mobo.h. 

Find the line with the following value:

```

#define VT1720_SUBDEVICE_ZNF3_150 0x0f2745f6

```

And replace it with this line: 

```

#define VT1720_SUBDEVICE_ZNF3_150 0x97123650

```

Where you of course replace "97123650" with the numbers you wrote down. 

6: Then you simple do a: 

```

cd ../../..
sudo ./configure --with-cards=ice1724 --with-sequencer=yes
sudo make
sudo make install

```

This should build you a new version of something with the new corrected value. 

7: Reboot your machine and voila you should have sound if you are as lucky as I am ;)

Hope that helps! (if it does not, please do not blame me)


Regards

/Martin

---

