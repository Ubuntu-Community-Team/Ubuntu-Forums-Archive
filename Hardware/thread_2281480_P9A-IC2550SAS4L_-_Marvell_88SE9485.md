---
title: "P9A-I/C2550/SAS/4L - Marvell 88SE9485"
date: 2015-06-07
forum: Hardware
---

### Post by C4PPY on 2015-06-07
During the last week I have been trying Openmediavault, Ubuntu, 
Debian, Xpenology, CentOS and with same result with lspci the marvell controller is 
present but the driver doesn't detect/bind to it.

  Help please!

---

### Post by Bela_Spahn on 2015-06-21
> **C4PPY said:**
> During the last week I have been trying Openmediavault, Ubuntu, 
Debian, Xpenology, CentOS and with same result with lspci the marvell controller is 
present but the driver doesn't detect/bind to it.

  Help please!

C4ppy,

Have a look at the following two links. The first one is a patch for the mvsas driver that adds support for the Marvell 88se9485 on the P9A-I/C2550 motherboard. The second link is an instruction on how to compile the driver. It's well described and I can safely say it worked. I have the same board and I chose to run Ubuntu 15.x, but I'm sure it will work on 14.02 as well. It took about 10mins and a restart. All drives are now recognised on the SAS connections. The second link also shows you how to get the mvsas source code which you can then modify by hand using nano (or vim). Or use the unix patch command. You will only need to change the mv_init.c file by inserting lines from the patch. Critical were of course the device and subdevice numbers to let the driver bind properly.

I hope this can get you started.

[B][SIZE=5][FONT=verdana][SIZE=2]mvsas patch[/SIZE]
[/FONT][/SIZE][/B][SIZE=5][FONT=verdana][[SIZE=2]http://permalink.gmane.org/gmane.linux.scsi/99330[/SIZE]]("http://permalink.gmane.org/gmane.linux.scsi/99330")[/FONT][/SIZE]

[FONT=verdana]**ubuntu kernel module compilation**
[/FONT][[FONT=verdana][SIZE=2]http://askubuntu.com/questions/515407/how-recipe-to-build-only-one-kernel-module[/SIZE][/FONT]]("http://askubuntu.com/questions/515407/how-recipe-to-build-only-one-kernel-module")[SIZE=2][FONT=verdana][SIZE=2][COLOR=#000000]
[/COLOR][/SIZE][/FONT][/SIZE]

---

### Post by C4PPY on 2015-06-22
Hi, 

Thanks for the super answer i'll try following it. One thing how do i use the patch(sorry, pretty new to linux)?

---

### Post by Bela_Spahn on 2015-06-22
C4ppy,

for all commands unix the 'man' (for manual) can help you. Type 'man patch' and you get the instructions on how to use it. If you're interested follow the [ten minute guide to diff and patch]("http://jungels.net/articles/diff-patch-ten-minutes.html"). I didn't even bother with the patch function and just copy-pasted the important lines.

I have no idea how versed you are with the terminal, so I'll just assume you prefer more detailed explanations.

I've attached the modified mv_init.c as a zipped file for your convenience. Have a scroll through it with a plain text editor (one that respects and keeps unix line endings). My changes start on line 729.

Now begin by downloading your choice of linux source. Yes, the whole thing, why not. You can find your release number by typing '[FONT=courier new]uname -r[/FONT]'. Pick the first three numbers separated by dots. In my case that was '3.19.0'. Download (copy-paste all commands without the '$'-sign in front)...

```
[SIZE=2][FONT=courier new][COLOR=#111111]$ cd ~
[/COLOR][COLOR=#111111]$ apt-get source linux-source-3.19.0[/COLOR][/FONT][/SIZE]
```

cd ~ takes you to your home directory. That's where everything ends up loading to.

Once downloaded open the linux source folder, going straight to the mvsas source code directory and rename the existing mv_init.c file with

```
[FONT=courier new]$ [/FONT][FONT=courier new]cd [/FONT][FONT=courier new]linux-3.19.0/drivers/scsi/mvsas
[/FONT][FONT=courier new][SIZE=2]$ mv mv_init.c mv_init.c.orig[/SIZE][/FONT]
```

then copy over the patched one provided below, unzipped of course. If you have the patched file in your home folder the following will copy and unzip in one go:

```
[FONT=courier new]$ [/FONT][SIZE=2][FONT=courier new]unzip ~/mv_init.c.zip -d ./[/FONT][/SIZE]
```

Now you can proceed to compiling the driver as per the [excellent instructions]("http://askubuntu.com/questions/515407/how-recipe-to-build-only-one-kernel-module") (always using your release version number of linux as before):

```
[SIZE=2][FONT=courier new][COLOR=#111111]$ cd ~/linux-3.19.0
[/COLOR]$ make oldconfig
$ make prepare
[COLOR=#111111]$ make scripts[/COLOR][/FONT][/SIZE]
```

etc.

Oh and skip the two lines further down, you don't need these:

```
[SIZE=2][FONT=courier new][COLOR=#111111]$ nano mv_sas.h
[/COLOR][COLOR=#111111]$ nano mv_sas.c[/COLOR][/FONT][/SIZE]
```

...because you're providing an already modified mv_init.c file and mv_sas.h and mv_sas.c in our case didn't need changing.

For the fun of it you might want to 'diff' my mv_init.c with the original version to see the changes or to try out making your own patch file.

I hope this works for you now.

Enjoy!

[ATTACH]262789[/ATTACH]

---

### Post by C4PPY on 2015-06-27
Hi Bela,

Thanks for the super guide, but the attachment cant be downloaded. Could you post it again or give me a link to it otherwise?

---

### Post by dino99 on 2015-06-27
the related chipset bug report (select the patch found when scrolling, not the first proposed)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1270844](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1270844)

but that issue should not be met as per  [http://cateee.net/lkddb/web-lkddb/SCSI_MVSAS.html](http://cateee.net/lkddb/web-lkddb/SCSI_MVSAS.html) as that chipset is included into actual kernels

more details  [https://bugzilla.redhat.com/show_bug.cgi?id=807871](https://bugzilla.redhat.com/show_bug.cgi?id=807871)

---

### Post by Yellow Pasque on 2015-06-27
Have you tried manually loading the module?
```
sudo modprobe -v mvsas
dmesg | tail -n 20
```

---

### Post by C4PPY on 2015-06-27
The problem is that the driver doesnt attach it self to the SAS controller due to controllers identifier isnt in the mvsas.  Bela had attached a modified mvsas file for me, but it cant download it. 

Does anyone els where to get the mvsas file with the info fore this motherboard?

---

