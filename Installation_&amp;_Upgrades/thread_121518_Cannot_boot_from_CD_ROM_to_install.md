---
title: "Cannot boot from CD ROM to install"
date: 2006-01-25
forum: Installation &amp; Upgrades
---

### Post by akniss on 2006-01-25
OK... i'm at a loss.  If anyone has any suggestions, i'm all ears.

I have a Dell Precision Workstation 410 at work that I would like to use as a data entry machine.  I thought I would put a minimal install of Ubuntu with gnumeric on it.  I put the Install CD (from shipit) in the drive and rebooted: up came WinXP.

I went into the bios, and selected boot from CDROM first and rebooted: up came winXP.

I played around in the bios to change the order of boot, and could not select cdrom as one of the selections, but the bios tells me that CDROM First is an option.  I went to the Dell site and downloaded the Bios update (A14 from the original A07 on the machine).  I created a DOS boot disk, copied the file and intsalled the updated bios.  I set it to CDROM first, rebooted: up came WinXP!

So I then searched the forums and google, and found smart bootmanager.  I put that on a bootable floppy and rebooted.  It boots into smart bootmanager, but doesn't give me the cdrom as a boot option.  SO... after spending an entire day on what I thought would be a 30 minute project, I'm still looking at a Windows XP login screen.  (I think its taunting me...)  Does anyone know of a way to make my machine boot from the install CD???  I've tried four separate Shipit CD's (2 live CDs and 2 Install CDs), so I'm pretty sure that isn't the problem.

---

### Post by RavenOfOdin on 2006-01-25
Maybe your CD drive is on its way out?? :confused:

---

### Post by akniss on 2006-01-25
[QUOTE=RavenOfOdin]Maybe your CD drive is on its way out?? :confused:[/QUOTE]

Possibly... but it spins when the computer boots.  I can hear it, and the yellow light blinks, then here comes windows.  Maybe I'll see if I can scavenge one from somewhere...  Any other suggestions in the meantime?

---

### Post by akniss on 2006-01-30
I finally got Ubuntu to install from the CD after much gnashing of teeth!!!  Here's how I did it:

First I went to the site [http://bootcd.narod.ru/index_e.htm](http://bootcd.narod.ru/index_e.htm) and downloaded Bootable CD Loader v1.50Z.  This is a bootable floppy disk image that will allow you any bootable CD to boot.   I downloaded RawWrite from here [http://uranus.it.swin.edu.au/~jn/linux/rawwrite.htm](http://uranus.it.swin.edu.au/~jn/linux/rawwrite.htm)  This program allowed me to put the Bootable CD Loader disk image onto a floppy.  I inserted the floppy into the computer and rebooted.  The first time, it told me that there was no CD-ROM available.  I opened up my box again, and put the CD-ROM drive as a slave on the same ATAPI cable that my hard drive was on.  After I did this, I rebooted, the Floppy booted, recognized my CD Drive, and my Ubuntu installation was on its way!!

---

### Post by xXx 0wn3d xXx on 2006-01-30
ok, put the cd in the computer and reboot with it in there. It works with me and I don't have the option under my bios. Also make sure that you saved your settings under the bios.

---

### Post by akniss on 2006-01-30
If you had read the thread, you'd know that I already tried to change the bios, and rebooted numerous times with the cd in the drive.  I've installed OSs before, I know that it works most of the time.  but it did not this time.  that is why I posted my fix, so that others who have similar problems may find help if the same thing happens to them.  I'm so happy it "works for you" though...

---

### Post by goatflyer on 2006-01-30
[QUOTE=akniss]I finally got Ubuntu to install from the CD after much gnashing of teeth!!!  Here's how I did it:

First I went to the site [http://bootcd.narod.ru/index_e.htm](http://bootcd.narod.ru/index_e.htm) and downloaded Bootable CD Loader v1.50Z.  This is a bootable floppy disk image that will allow you any bootable CD to boot.   I downloaded RawWrite from here [http://uranus.it.swin.edu.au/~jn/linux/rawwrite.htm](http://uranus.it.swin.edu.au/~jn/linux/rawwrite.htm)  This program allowed me to put the Bootable CD Loader disk image onto a floppy.  I inserted the floppy into the computer and rebooted.  The first time, it told me that there was no CD-ROM available.  I opened up my box again, and put the CD-ROM drive as a slave on the same ATAPI cable that my hard drive was on.  After I did this, I rebooted, the Floppy booted, recognized my CD Drive, and my Ubuntu installation was on its way!![/QUOTE]

Way to go!!

I too ran into the same problem as yours.  I wanted to install Ubuntu on an old Win98SE machine that has no problem reading the CDs (Live or Install), has the BIOS boot option to boot first from CD selected, but nonetheless keeps coming up with the Windows screen everytime. 

I shall try your suggestion on it tomorrow, and report back

---

### Post by akniss on 2006-01-30
[QUOTE=goatflyer]Way to go!!

I too ran into the same problem as yours.  I wanted to install Ubuntu on an old Win98SE machine that has no problem reading the CDs (Live or Install), has the BIOS boot option to boot first from CD selected, but nonetheless keeps coming up with the Windows screen everytime. 

I shall try your suggestion on it tomorrow, and report back[/QUOTE]

Let me know how it goes.  If it works for you, maybe we can put together a HOWTO on this.  I've seen many similar posts, but none of their solutions seemed to work for me.

---

### Post by goatflyer on 2006-01-31
akniss:

Okay, first I tried the bootcd.narod.ru website you mentionned and got a 404 in russian.  But your main idea inspired me to look further...

...to make a long story short, it seems we had a solution practically under our noses from the beginning.

On both the Breezy Live and Install CDs there is an **install** directory.  Inside that you will find a file called **sbm.bin**   This is a complete floppy image of sbm, the 'Smart Boot Manager', an OS-independant boot floppy that presents you with a choice to boot from all the devices it can see.  If your Windows machine can see the Ubuntu CD (when running Windows), chances are very good that this program can see it too.

There was just one last hitch I ran into.  The machine had an AwardBIOS which had an option to protect against and detect boot sector viruses. (Trend ChipAwayVirus).  If I selected to boot from the hard drive (Win98SE) it seemed to get confused thinking the boot floppy was a virus.


Combining what we now know from both our experiences, a mini-HOWTO would read something like this:

HOWTO boot a Live or Install CD on machines that insist on booting from hard disk even when you select 'boot from CD' option in the BIOS.

 1.) Create a boot floppy with the sbm.bin image on it.  Here are two possible ways. 

1a) If you have access to another Linux machine, this is easy: (I assume the cd is mounted on /media/cdrom1 and the floppy drive is /dev/fd0 and is **not mounted**

        Insert the Live or Install CD, and a formatted 1.44M floppy into the drive.  then
 ```

# cd /media/cdrom1/install
# dd if=sbm.bin of=/dev/fd0 bs=512

```


OR

1b) If you have to do this from a Windows machine, download rawrite.exe from

[http://uranus.it.swin.edu.au/~jn/linux/rawwrite.htm](http://uranus.it.swin.edu.au/~jn/linux/rawwrite.htm)

  or

[http://www.fdos.org/ripcord/rawrite/](http://www.fdos.org/ripcord/rawrite/)

Insert a formatted floppy into the drive (assume A:), and insert the Linux CD, which should be readable from Windows (assume D:). Open a command prompt and type

```

rawrite -f d:\install\sbm.bin -d a

```


Now that we have a boot floppy, the rest is easy:

1.) Get into the BIOS of the target machine.  Change boot order to make sure that floppy is attempted before hard disk.  Also disable any BIOS setting for virus protection/monitoring.  We won't be writing anything with a LiveCD anyway...

2) Meanwhile, insert the sbm.bin floppy and the Live or Install CD.

3) Save BIOS settings, exit and reboot.  After a few moments. you should come up in the Smart Boot Manager menu.

4) Use cursor keys to select CD-ROM and press enter.

You are now booting from CD!

EDIT: disabled unwanted smilies in text

---

### Post by akniss on 2006-02-01
[http://www.wolfgang-brinkmann.de/bcdw/index_e.htm](http://www.wolfgang-brinkmann.de/bcdw/index_e.htm)
[http://www.bcdwb.de/bcdw/index_e.htm](http://www.bcdwb.de/bcdw/index_e.htm)
[http://bootcd.narod.ru/index_e.htm](http://bootcd.narod.ru/index_e.htm)

All three of these links are *currently* up and running.  From there, you can download the Bootable CD Loader (v1.50Z: bcdl150z.zip) floppy disk image.  I had tried the smart boot manager earlier, but it did not seem to work with my setup, for whatever reason.  I would propose that we add this as an option to get a bootable floppy section, something like this:

1.) Create a boot floppy with the sbm.bin image on it. Here are three possible ways.

1a) If you have access to another Linux machine, this is easy: (I assume the cd is mounted on /media/cdrom1 and the floppy drive is /dev/fd0 and is not mounted

Insert the Live or Install CD, and a formatted 1.44M floppy into the drive. then
```

# cd /media/cdrom1/install 
# dd if=sbm.bin of=/dev/fd0 bs=512

```


OR

1b) If you have to do this from a Windows machine, download rawrite.exe from

[http://uranus.it.swin.edu.au/~jn/linux/rawwrite.htm](http://uranus.it.swin.edu.au/~jn/linux/rawwrite.htm)

or

[http://www.fdos.org/ripcord/rawrite/](http://www.fdos.org/ripcord/rawrite/)

Insert a formatted floppy into the drive (assume A:), and insert the Linux CD, which should be readable from Windows (assume D:). Open a command prompt and type

```

rawrite -f d:\install\sbm.bin -d a

```


OR

1c)  If for some reason Smart Boot Manager does not recognize your CD-ROM, try downloading Bootable CD Loader from one of the following sites:

[http://www.wolfgang-brinkmann.de/bcdw/index_e.htm](http://www.wolfgang-brinkmann.de/bcdw/index_e.htm)
[http://www.bcdwb.de/bcdw/index_e.htm](http://www.bcdwb.de/bcdw/index_e.htm)
[http://bootcd.narod.ru/index_e.htm](http://bootcd.narod.ru/index_e.htm)

Extract the .zip file and use rawrite from a windows machine to put the bootable floppy image onto a blank floppy.

NOTE: goatflyer, I'm not at my windows box right now, to my instructions are not as specific as they could be.  I will clarify when I get some time with XP.  I also used a GUI in rawwrite to copy the image to the floppy.  I will try to repeat everything and write it down tomorrow.  Also, is there a linux package that will copy floppy images to disk?  I'm still pretty new to the linux world.

---

### Post by goatflyer on 2006-02-01
It will be a good idea to mention those multiple source urls for bootable cd loader.  I always seem to have bad luck when reading old helpfiles that send me off to a places that either died several years back, or else just happens to be switched off for the time being...  404 doesn't distinguish.

> Also, is there a linux package that will copy floppy images to disk? I'm still pretty new to the linux world.

You don't need a package at all.  Since everything in *nix is a file (including the unmounted device /dev/fd0) you can just use dd to do a raw copy:

```

dd if=/dev/fd0 of=~/MyFloppyImage.bin bs=512

```

This is just the reverse of the dd line that I used to copy the sbm.bin image to the floppy from my home machine. I don't know if you really need the blocksize 512 argument, but I put it in because I know that sector size of a floppy is 512.  The command relies on getting 'eof' from the device when we try to read the sector past the end (which doesn't exist). Mine stopped after 1474560 bytes.

What's cool about dd, is you can use it to grab boot sectors by limitting it to just the first sector.  2 examples:

```

dd if=/dev/fd0 of=~/FloppyBootSector.bin bs=512 count=1
dd if=/dev/hda of=~/MyMBR.bin bs=512 count=1

```

It's good to have that last one copied somewhere for safekeeping in case you ever trash it by mistake.  Note: you must be root or use sudo to get it.

This thread's subjectline is a more concise title for the HOWTO than the one I wrote.

Your turn.

---

### Post by maddog39 on 2006-03-08
What if we dont have a floppy drive. Then what do we do? Because I am having the same problem. Heres my topic.

[http://www.ubuntuforums.org/showthread.php?t=141705](http://www.ubuntuforums.org/showthread.php?t=141705)

---

### Post by akniss on 2006-03-09
[QUOTE=maddog39]What if we dont have a floppy drive. Then what do we do? Because I am having the same problem. Heres my topic.

[http://www.ubuntuforums.org/showthread.php?t=141705](http://www.ubuntuforums.org/showthread.php?t=141705)[/QUOTE]


Well... that presents an interesting problem that goatflyer and I didn't encounter.  Do you have access to an external floppy or cd perhaps?

---

