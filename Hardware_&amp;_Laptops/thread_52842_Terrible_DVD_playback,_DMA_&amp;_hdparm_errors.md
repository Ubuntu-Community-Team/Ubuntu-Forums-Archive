---
title: "Terrible DVD playback, DMA &amp; hdparm errors"
date: 2005-07-29
forum: Hardware &amp; Laptops
---

### Post by cosmolee on 2005-07-29
I've got xine, llibxine & libdvdcss2 intalled on a Pentium 4 3.2 GHz, but I'm getting shaky playback on movies.   [http://xinehq.de/index.php/faq#SPEEDUP](http://xinehq.de/index.php/faq#SPEEDUP) suggests turning DMA on for the DVD drive with `hdparm`:

# hdparm -d1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)
#

Any idea why I can't turn DMA on??

Thanks.

---

### Post by tseliot on 2005-07-29
Which kernel are you using?

Type this in the Terminal or Konsole

uname -r

---

### Post by heimo on 2005-07-29
Probably because your motherboards chipset spesific / or rather: ide controllers kernel module ("driver") is not loaded. That's a very common problem here and to fix it, you need to know which motherboard or chipset you're using (output of lspci helps a lot), then edit /etc/modules (add the name of the correct module) and hdparm.conf and restart. At least for me it didn't load correctly if it wasn't in /etc/modules

See for example:
[http://ubuntuforums.org/showthread.php?t=47394&highlight=dma+module]("http://ubuntuforums.org/showthread.php?t=47394&highlight=dma+module")
[http://ubuntuforums.org/showthread.php?t=30949](http://ubuntuforums.org/showthread.php?t=30949)

---

### Post by cosmolee on 2005-07-29
I'm using 2.6.10-5-386.  

I recently tried 2.6.10-5-686, but the kernel has a problem with my motherboard, it causes the system to run VERY slow.  I've got an Intel D915GEV mobo.  I've had the same problems with newer kernels w/ Fedora and other distros as well.  I've had problems running newer kernels with this board with 1GB memory.  512kb, ok, 1GB, no good.

Cosmo

---

### Post by tseliot on 2005-07-29
It's likely that kernel 2.6.11 solves your problem it's in the universe or multiverse repositories (I don't remember exactly). 

Do you use nvidia drivers? This is important because the new kernel could screw them up and you would have to reinstall the drivers.

---

### Post by cosmolee on 2005-07-29
Here's the fix:

[http://www.ubuntuforums.org/showthread.php?p=93238#post93238](http://www.ubuntuforums.org/showthread.php?p=93238#post93238)



>Do you have amd or intel hardware? If you have intel try the following:

>I just got this to work by putting

>piix
>ide-core

>ABOVE

>ide-cd
>ide-disk
>ide-generic

>in /etc/modules



But I must say that the amount of work required to find this fix just shows how far Linux is from being Desktop-ready for non-geeky users.... 

Windows users would have never gotten this far to get their DVD playback going. They would have quit when they were told they had to get libdvdcss, edit their sources.list file to download it, and search & read a bunch of FAQs.  And that's why they'll continue to pay the Microsoft tax.

---

### Post by sjmorgan on 2005-07-31
[QUOTE=cosmolee]I've got xine, llibxine & libdvdcss2 intalled on a Pentium 4 3.2 GHz, but I'm getting shaky playback on movies.   [http://xinehq.de/index.php/faq#SPEEDUP](http://xinehq.de/index.php/faq#SPEEDUP) suggests turning DMA on for the DVD drive with `hdparm`:

# hdparm -d1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)
#

Any idea why I can't turn DMA on??

Thanks.[/QUOTE]Linux DMA support is flaky to say the least. It could just be that Linux doesn't like your particular hardware setup. I have the relevant IDE modules loaded and it works OK with my hard drives (spits out the odd error now and again) but, even though I can enable it, spits out a ton of errors and gets disabled with my DVD drive.

---

### Post by FNM on 2005-08-05
Thanks for all the input guys, I was having the same problem and "hdparm -d1 /dev/hda" fixed it.  :-P Just FYI, I'm running a Pioneer DVD-R on an Intel P4.

---

### Post by ronald.craig on 2005-08-05
[QUOTE=cosmolee]I've got xine, llibxine & libdvdcss2 intalled on a Pentium 4 3.2 GHz, but I'm getting shaky playback on movies.   [http://xinehq.de/index.php/faq#SPEEDUP](http://xinehq.de/index.php/faq#SPEEDUP) suggests turning DMA on for the DVD drive with `hdparm`:

# hdparm -d1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)
#

Any idea why I can't turn DMA on??

Thanks.[/QUOTE]
 Isn't hda your hard-drive? If your DVD is connected as the master on the secondary then I think it should be hdc... not hda.

---

### Post by FNM on 2005-08-05
Just a quick question. When I reboot my computer, DMA is turned off. How can I save it, so I don't have to type it in every time I want to watch a DVD?

---

### Post by TheOtherShoe on 2005-08-05
[QUOTE=FNM]Just a quick question. When I reboot my computer, DMA is turned off. How can I save it, so I don't have to type it in every time I want to watch a DVD?[/QUOTE]
Add the following to /etc/hdparm.conf
```
/dev/hda {
       dma = on
}
```
That should do the trick. Make sure to replace /dev/hda with the device for your dvd drive. As ronald.craig said, this is usually /dev/hdc.

---

### Post by Copter on 2005-08-13
hi!

i can hardly believe that DMA is such a big problem here. i found lots of threads about it here. most of them points to other threads that points to another threads. i took me a hour to check all of those _ideas_ and tips. still DMA not working...

i have new DVD-RAM drive, one year old Asus Pundit-R computer (chipset ATI RS300 / IXP200), socket 478 Celeron CPU and 2.6.10-5-686 kernel.

ive done this:

-- added /etc/modules "piix;ide-core" before "ide-cd ..." lines
-- added /etc/hdparm.conf "/dev/dvd {dma = on}" lines
-- sudo mv S07hdparm S99hdparm

and gues what?
```

copter@xidge:~$ hdparm /dev/dvd

/dev/dvd:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
``````

copter@xidge:~$ hdparm -i /dev/dvd

/dev/dvd:

 Model=HL-DT-ST DVDRAM GSA-4163B, FwRev=A101, SerialNo=K564BDG0841
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no
 Drive conforms to: device does not report version:

 * signifies the current active mode
``````

copter@xidge:~$ sudo hdparm -d1 /dev/dvd
Password:

/dev/dvd:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)
```cd / dvd to hdd transfer rate : <2mb/s. cant believe my eyes... going crazy atm

copter :]

---

### Post by tseliot on 2005-08-13
Perhaps installing kernel 2.6.11 might do the trick for you (it is in Universe repositories, read the Unofficial Ubuntu Starter guide if you don't have them in you /etc/apt/sources.list)

Otherwise, if it didn't work you might compile a new kernel and disable the function "Enable DMA only for disks" (use this as your last resort).

Tell me if it works for you

---

### Post by Copter on 2005-08-13
[QUOTE=tseliot]Perhaps installing kernel 2.6.11 might do the trick for you (it is in Universe repositories, read the Unofficial Ubuntu Starter guide if you don't have them in you /etc/apt/sources.list)

Otherwise, if it didn't work you might compile a new kernel and disable the function "Enable DMA only for disks" (use this as your last resort).

Tell me if it works for you[/QUOTE]
thanks for fast reply. i cant believe that theres probably no other way. installing or compiling new kernel is serious thing. im no expert here, dont want to mess up my system. though if noone finds any other method i will be forced to do it.

copter :]

---

### Post by tseliot on 2005-08-13
Maybe compiling a new kernel can be for more experienced (well, at least not for newbies) but installing a new kernel is terribly easy.

You would have only to install it (linux kernel image 2.6.11-i386 or something like this.) by using Synaptic (or Kynaptic) (just like the installation of an application) and you DON'T have to remove your current kernel (something you could only do intentionally if you wanted). Then just restart your computer. Believe me, it's very easy.

If anthing went wrong (I don't know a reason for which it would) you could switch back to your kernel: while booting your computer and press "ESC" repeatedly until GRUB menu appears and you can choose kernel 2.6.10 again (using your keyboard arrows). Once you enter Ubuntu open Synaptic and remove the undesired kernel in the same way you installed it (it's a matter of mouse clicks). And reboot.

IMPORTANT NOTE BEFORE you try what's written above:
If you have an Nvidia graphic card with Nvidia drivers installed I can tell you a way to use the drivers with the new kernel.

---

### Post by Copter on 2005-08-13
hmm... i will give a try using kynaptic. im downloading linux-image-2.6.11-1-686 right now. ive heard some time ago about even or odd kernel numbers that states that it is stable or not stable build (or something like that). what about this one? anyway its worth trying if i can _undo_ it in case of serious system crash.

about my graphic card - my computer have Ati Radeon 9100 onboard integrated (no _external_ agp port).

thanks again tseliot. you helped me alot here. i hope also i will have DMA support for my dvd drive. i couldnt believe how slow it was under linux.

copter :]

---

### Post by tseliot on 2005-08-13
686 kernel should work for you (otherwise you can use 386 kernel).

However if after restarting your computer you don't have DMA enabled yet (type "sudo hdparm -d /dev/dvd" in order to check it) , do this (with your new kernel):

Open Terminal or Konsole
type:

sudo cp /etc/hdparm.conf /etc/hdparm.conf_backup (so as to make a backup of your hdparm)

Then:
(if you are using GNOME)
sudo gedit  /etc/hdparm.conf

or (if you are using KDE)
sudo kate  /etc/hdparm.conf

and add the following lines at the end of the file:

/dev/hda {
       dma = on
}

/dev/cdrom {
       dma = on
}

Save the file and exit.

Restart your computer and check if DMA works now.

If not try to substitute:
/dev/cdrom {
       dma = on
}

with

/dev/[COLOR=Red]dvd[/COLOR] {
       dma = on
}

And restart your computer again.

---

### Post by Copter on 2005-08-13
as i wrote before i already changed hdparm.conf file.

situation looks like this: i have new kernel (2.6.11-1-686). after first reboot with it i got at the end of system shutdown messages something like this printed 100 times
```

Scheduling while atomic: gam_server/0xffffffb6/6638
```and after this
```

Kernel panic - not synching : Aiee, killing interrupt handler
```i switched my computer off and on. i booted again using the same new kernel. everything looks nice except this
```

HDIO set DMA failed : operation not permitted
```or something similar. ive lost any hope. did exacly as people wrote here. it supposed to work for God's sake.

copter  ](*,)

---

### Post by tseliot on 2005-08-13
Ok, now calm down. There's another way to make it work: the so "feared" kernel compilation. I know you're a newbie but I've come to think it's time for me to write a HOWTO for total newbies. It will be very easy and you will just have to follow the instructions. Nothing will prevent you from having DMA enabled because you will enable it directly in the kernel.

I'll be working tonight on this ambitious (actually not that ambitious) HOWTO.

FOR NOW Just DELETE the lines I told you to add in hdparm.conf and save the file.

Don't fear, you'll get DMA to work after my easy HOWTO.

I'll make you know when it's ready (maybe tonight or tomorrow, it depends on my brain  ;-) )

Alberto

---

### Post by Copter on 2005-08-13
i would be very thankful for this kind of information :). the greatest power of linux is in its creative community. i would not be able to do anything without people on this forum. i would stick with windos for sure.

i surely will not die if i still had dma off for some time. but im looking forward to switch it on :)

thanks again!

copter :]

---

### Post by Dolphin on 2005-08-13
Hey guys.

I got DMA to work, and it definately improved my video situation.
I still get problems if I run xine in full screen though.  It'll still start dropping frames and I can't even exit the program. I end up resetting.  Any ideas?

---

### Post by tseliot on 2005-08-14
Here is the HOWTO I promised to write:

[http://ubuntuforums.org/showthread.php?p=301048#post301048](http://ubuntuforums.org/showthread.php?p=301048#post301048)

---

