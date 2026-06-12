---
title: "TV tuner card not working saa7134 chipset"
date: 2004-10-10
forum: Hardware &amp; Laptops
---

### Post by bikeham on 2004-10-10
I have been unable to get my Compro Videomate Gold card working under any distro so far, Ubuntu has been the most promising.

I'm trying Zapping as the gnome interface.  Anyone using this combo successfully?

Am very impressed with Ubuntu otherwise.

Cheers,

Steve

---

### Post by WattoDaToydarian on 2005-03-14
Hey bikeham I'm usin this combo tryin to get a homemade PVR setup with it and i'v been havin trouble also. It wasn't working at all with the warty realse so I upgraded to hoary and it's workin ok with mythtv and tvtime exept for some reason it's only giving me the left audio channel output no right! I'v tried everythin I can think of but I know it can work cus it works in windows :???: . Do you have this problem also?

---

### Post by vr9k on 2005-04-05
to get it to work you need to patch your kernel  the patches can be found at [http://linux.bytesex.org/v4l2/](http://linux.bytesex.org/v4l2/)

---

### Post by WattoDaToydarian on 2005-04-06
Hey vr9k, I take it you have gotten the stereo sound to work on it using these patches? I'v never done a kernel patch before and I dont know which one to use, could you help me out some more? I got the 2.6.11 kernel on there runnin the Knoppmyth distro.

Thanks

---

### Post by vr9k on 2005-04-06
Actual I running a mono system, I have a mono tv. I need to patch my kernel to get my remote to work; I remember reading that the patch will fix it.

I do not know anything about Knoppmyth. I have never used it. You need to find some documentation about compiling a Knoppmyth kernel from the source.

When you are just about ready to compile in the directory that the source is in, mostly the directory will be /usr/src/ download [http://dl.bytesex.org/patches/2.6.11-2/saa7134-update](http://dl.bytesex.org/patches/2.6.11-2/saa7134-update) and run 
"patch -p0 < saa7134-update" replace saa7134-update to the path to the file that you downloaded.

Then follow the directions to recompile the kernel for Knoppmyth.

---

### Post by WattoDaToydarian on 2005-04-07
Well, I downloaded the saa7134-update file by saving it to disk instead of opening it in my browser. I have already compiled the 2.6.11 kernel for the machine so I know that it works but I dont know what i'm doing with the patch. Heres where i'm unshure about:
```
root@PVR:/usr/src/linux# patch -p0 < saa7134-update
can't find file to patch at input line 33
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|Subject: [patch] saa7134 update
|
|Major saa7134 driver update.  Changes:
| * add a bunch of new cards.
| * add dvb card support.
| * update empress encoder card support,
|   use the new v4l2 mpeg API for the settings.
|
|Signed-off-by: Gerd Knorr <kraxel@bytesex.org>
|---
| drivers/media/video/Kconfig                   |    4
| drivers/media/video/saa7134/Makefile          |    1
| drivers/media/video/saa7134/saa6752hs.c       |  314 ++++++++++----
| drivers/media/video/saa7134/saa7134-cards.c   |  400 ++++++++++++++++--
| drivers/media/video/saa7134/saa7134-core.c    |   43 +
| drivers/media/video/saa7134/saa7134-dvb.c     |  191 ++++++++
| drivers/media/video/saa7134/saa7134-empress.c |   60 ++
| drivers/media/video/saa7134/saa7134-i2c.c     |   37 -
| drivers/media/video/saa7134/saa7134-input.c   |   60 ++
| drivers/media/video/saa7134/saa7134-oss.c     |    6
| drivers/media/video/saa7134/saa7134-ts.c      |    7
| drivers/media/video/saa7134/saa7134-tvaudio.c |   63 +-
| drivers/media/video/saa7134/saa7134-vbi.c     |    3
| drivers/media/video/saa7134/saa7134-video.c   |   59 +-
| drivers/media/video/saa7134/saa7134.h         |   21
| include/media/saa6752hs.h                     |   29 +
| 16 files changed, 1061 insertions(+), 237 deletions(-)
|
|Index: linux-2.6.11/drivers/media/video/saa7134/saa7134.h
|===================================================================
|--- linux-2.6.11.orig/drivers/media/video/saa7134/saa7134.h    2005-03-07 10:14 :47.000000000 +0100
|+++ linux-2.6.11/drivers/media/video/saa7134/saa7134.h 2005-03-07 16:28:06.0000 00000 +0100
--------------------------
File to patch:
``` 
It's asking me what file to patch cus it cant find out. Is this how you did it?

---

### Post by vr9k on 2005-04-07
You need to be /usr/src or do -p/usr/src for the p option and also the kernel needs to be in linux-2.6.11 directory. 
The patch comman just replaces some source code in the file given by the patch. The output you got there saying it cannot find the file, in your case it was looking for linux-2.6.11/drivers/media/video/saa7134/saa7134.h which it cannot find.

---

### Post by WattoDaToydarian on 2005-04-07
Ok, I did this:
```
root@PVR:/usr/src# ln -s linux-2.6.11.4 linux-2.6.11
root@PVR:/usr/src# patch -p0 < saa7134-update
patching file linux-2.6.11/drivers/media/video/saa7134/saa7134.h
patching file linux-2.6.11/drivers/media/video/saa7134/saa7134-core.c
patching file linux-2.6.11/drivers/media/video/saa7134/saa7134-cards.c
patching file linux-2.6.11/drivers/media/video/saa7134/saa7134-tvaudio.c
patching file linux-2.6.11/drivers/media/video/saa7134/saa7134-video.c
patching file linux-2.6.11/drivers/media/video/saa7134/saa7134-input.c
patching file linux-2.6.11/drivers/media/video/saa7134/saa7134-empress.c
patching file linux-2.6.11/include/media/saa6752hs.h
patching file linux-2.6.11/drivers/media/video/saa7134/saa6752hs.c
patching file linux-2.6.11/drivers/media/video/saa7134/saa7134-oss.c
patching file linux-2.6.11/drivers/media/video/saa7134/saa7134-dvb.c
patching file linux-2.6.11/drivers/media/video/saa7134/saa7134-i2c.c
patching file linux-2.6.11/drivers/media/video/saa7134/saa7134-ts.c
patching file linux-2.6.11/drivers/media/video/saa7134/saa7134-vbi.c
patching file linux-2.6.11/drivers/media/video/Kconfig
patching file linux-2.6.11/drivers/media/video/saa7134/Makefile
root@PVR:/usr/src#
``` 
Then I did a "make menuconfig" to check out the V4L section and see if everything is ok then I did "make" and this is what's at the end of the errors:
```
drivers/media/video/saa7134/saa7134-cards.c:1542: error: (near initialization for `saa7134_boards[55].inputs[2]')
drivers/media/video/saa7134/saa7134-cards.c:1547: error: initializer element is not constant
drivers/media/video/saa7134/saa7134-cards.c:1547: error: (near initialization for `saa7134_boards[55].inputs[3]')
drivers/media/video/saa7134/saa7134-cards.c:1547: error: initializer element is not constant
drivers/media/video/saa7134/saa7134-cards.c:1547: error: (near initialization for `saa7134_boards[55].inputs')
drivers/media/video/saa7134/saa7134-cards.c:1548: error: initializer element is not constant
drivers/media/video/saa7134/saa7134-cards.c:1548: error: (near initialization for `saa7134_boards[55]')
make[4]: *** [drivers/media/video/saa7134/saa7134-cards.o] Error 1
make[3]: *** [drivers/media/video/saa7134] Error 2
make[2]: *** [drivers/media/video] Error 2
make[1]: *** [drivers/media] Error 2
make: *** [drivers] Error 2
root@PVR:/usr/src/linux#
```
They preety much look the same all the way to the top of the terminal window but I cant see where it started cus it doesn't show that far up. Should I download the 2.6.11.7 kernel and redo everything or did I just do it wrong?

---

### Post by vr9k on 2005-04-07
It seems like the patch is not working. The same thing is happening to me I hoped it was just my kernel source, what I am doing is just patching the parts of the kernel that fixes the area you are looking at.  In order to get the patches to work you may need to patch everything, when I tried to load all of the patches it failed to me. 

To get the sound working go into the patch file, [http://dl.bytesex.org/patches/2.6.11-2/saa7134-update](http://dl.bytesex.org/patches/2.6.11-2/saa7134-update) and find every line that says LINE2_LEFT and manually changes thoses line.

the lines with the - sign you take away with the + sign you add. 

that is the easiest way that i am seeign and hopefully that will work.

There should be lines in saa7134-cards.c, saa7134-tvaudio.c and saa7134-oss.c, hoepfully.

the patch command is how some will patch code the patch does not seems to work

---

### Post by WattoDaToydarian on 2005-04-07
Uhh, I cant relly understand what you want me to do. You want me to find the lines with "LINE2_LEFT" in them and do what? Do you also want me to remove all the lines with a - at the begining of them and leave the ones with a + or nothing? Will this make the patch work right and make the stereo sound work?

---

### Post by vr9k on 2005-04-08
The patch file is just instructiosn to chaneg the source code. In this case the patch does not work. So to just get the feature you want to work, you need to patch part of the code that is wrong.

To do it manually take out the lines in the patch file with a '-' and replace it with the following line that has a '+'.

In this case you need to patch all the lines with the word LINE2_LEFT in it, and to know what file to patch there will be two lines like theses.

+++ linux-2.6.11/drivers/media/video/saa7134/saa7134-dvb.c	2005-03-07 16:28:06.000000000 +0100

This means you need to chaneg the lines in drivers/media/video/saa7134/saa7134-dvb.c of the kernel.

---

### Post by WattoDaToydarian on 2005-04-08
Ok, I looked in the patch file and found all the lines with "LINE2_LEFT" and added thoes lines to the files stated before the lines at the places that matched the lines around the "LINE2_LEFT" lines to the 2.6.11.7 kernel source. Then I compiled it and there was no change to the tuner sound, it's still only the left channel... ](*,)

---

### Post by vr9k on 2005-04-18
Inorder to get it to work all of the v4l patches need to be applied. To do that copy everything from [http://dl.bytesex.org/patches/2.6.11-2/All-2.6.11.diff.gz](http://dl.bytesex.org/patches/2.6.11-2/All-2.6.11.diff.gz) to a text file and then run "patch -p0 <nameOfFile" where the nameOfFile is the path to the text file and recompile the kernel and boot into it. and everything should work, or it did for me.

---

### Post by WattoDaToydarian on 2005-04-18
Thanks but I just switched to the Haupauge WinTV PVR 150 so everything is fine now. ;-)

---

