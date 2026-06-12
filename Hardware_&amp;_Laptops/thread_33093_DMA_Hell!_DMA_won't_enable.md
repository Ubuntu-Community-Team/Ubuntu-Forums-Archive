---
title: "DMA Hell! DMA won't enable"
date: 2005-05-09
forum: Hardware &amp; Laptops
---

### Post by DutchLau on 2005-05-09
I've been having MAJOR problems with DMA. Here is the output of hdparm -d /dev/hdc (My DVD location):

> 
root@Discom:/home/discom # hdparm -d /dev/hdc 

/dev/hdc:
using_dma = 0 (off)


So I tried doing this:

> 
root@Discom:/home/discom # hdparm -d1 /dev/hdc

/dev/hdc:
setting using_dma to 1 (on)
HDIO_SET_DMA failed: Operation not permitted
using_dma = 0 (off) 


What must I do to enable DMA? The output of hdparm -i /dev/hdc is as follows:

> 
root@Discom:/home/discom # hdparm -i /dev/hdc

/dev/hdc:

Model=HL-DT-ST DVDRAM GSA-4163B, FwRev=A102, SerialNo=K7351SB5729
Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
BuffType=unknown, BuffSize=0kB, MaxMultSect=0
(maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
PIO modes: pio0 pio3 pio4
DMA modes: mdma0 mdma1 mdma2
UDMA modes: udma0 udma1 *udma2
AdvancedPM=no
Drive conforms to: device does not report version:

* signifies the current active mode 


Any suggestions? Please

DutchLau

---

### Post by Professor X on 2005-05-09
Looks like you need to compile a custom kernel:

[DVD PLayback HOWTO](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/DVD-Playback-HOWTO.html#dmatrouble)

Don't worry, compiling a kernel is a lot of fun.

Good luck.

---

### Post by DutchLau on 2005-05-09
Oh no, I've been dreading this since the moment I stepped into the Linux world.

Wish me luck  :razz:

---

### Post by Professor X on 2005-05-09
Here's a guide for building a kernel on ubuntu:
[http://www.ubuntulinux.org/wiki/KernelHowto](http://www.ubuntulinux.org/wiki/KernelHowto)

You should find out if the newest kernel version supports your chipset, although I don't know where to obtain this info.

---

### Post by DutchLau on 2005-05-09
Does anyone else know where to obtain this info? Please?  :-| 

DutchLau

---

### Post by DutchLau on 2005-05-09
Okay, I've made a horrible mess of my "custom kernel" so I want to delete it from GRUB (I don't care if it's still on my HDD, I have space to spare). How do I do this?

Thanks already,

DutchLau

---

### Post by DutchLau on 2005-05-09
Okay, never mind, I fixed my problem already.

I edited the GRUB file like with this command:

sudo gedit /boot/grub/menu.lst

And then I just deleted my hopelessely n00bishly compiled kernel that wouldn't even start X.  :razz:  Maybe I'll give it a shot some other time!

DutchLau

---

### Post by marks_linux on 2005-05-10
You don't need to re-compile kernel to get dma on.

I have a similar setup as yours (SATA hard drives etc) and had the same problems. you need to add some modules to load.

Heres my /etc/modules file

piix
via82cxxx
ide-core
ide-cd
ide-disk
ide-generic
#ide-cd
#ide-disk
#ide-generic
lp
mousedev
psmouse
sbp2
sr_mod

I believe you may need to double check the line beginning via82 as this depends on your chipset.

After this dma can (and is on my machine) enabled using hdparm

Mark

---

### Post by jeremy on 2005-05-10
[QUOTE=marks_linux]You don't need to re-compile kernel to get dma on.

I have a similar setup as yours (SATA hard drives etc) and had the same problems. you need to add some modules to load.

Heres my /etc/modules file

piix
via82cxxx
ide-core
ide-cd
ide-disk
ide-generic
#ide-cd
#ide-disk
#ide-generic
lp
mousedev
psmouse
sbp2
sr_mod

I believe you may need to double check the line beginning via82 as this depends on your chipset.

After this dma can (and is on my machine) enabled using hdparm

Mark[/QUOTE]
 [http://ubuntuforums.org/showpost.php?p=93238&postcount=5](http://ubuntuforums.org/showpost.php?p=93238&postcount=5)

This post has all the info you need.

---

### Post by DutchLau on 2005-05-10
Wow thanks!  :razz: 

This actually worked! Now the question is: how can I get this to load at system startup? I have added the command to turn DMA on in the /etc/hdparm.conf file, but that starts up *before* the modules load up, so it never actually turns DMA on.

Any suggestions?

DutchLau

EDIT: Now my DVD drive doesn't automatically mount and put an icon on the desktop. The output of my /etc/modules file is as follows:

> piix
ide-core
via82cxxx
ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
sbp2
sr_mod
nvidia 

What should I do?

---

### Post by kosmic on 2005-05-10
To make a persistent save in your drives so they all start with DMA on, just use the 
-k parameter (-k0 dont save) -k1 save

---

### Post by NightwishFreak on 2005-05-10
hey thanks kosmic! i didnt know about the -k option :D

---

