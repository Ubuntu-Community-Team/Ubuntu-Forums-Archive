---
title: "Boot from Floppy TO USB"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by pioa on 2008-12-31
Debian has one... [http://wiki.debian.org/BootingFromFloppyToUsb](http://wiki.debian.org/BootingFromFloppyToUsb)

It's in case your BIOS can not boot from USB.

You will boot floppy first and the floppy will hand over the rest of the boot process to the USB driver. Where can I get such a BootromFloppyToUSB floppy image for Ubuntu?

---

### Post by sovietdoughnut on 2008-12-31
thank you for posting this, i have needed something like this before =)

---

### Post by Herman on 2008-12-31
It's easy to make your own GRUB boot floppy disk, here, check out the how-to in this link, [How to make your own personalized GRUB Floppy Disk]("http://users.bigpond.net.au/hermanzone/p15.htm#grub_floppy_howto_make").

Since you're wanting to boot a USB, I recommend that you should use the newest and most advanced stage2 file in your GRUB floppy disk. Intrepid Ibex's GRUB contains the most advanced stage2 file.
Intrepid Ibex's GRUB can search for your device by the file system UUID number, so you'll have reliable booting regardless of what the hard disk numbering scheme is in different computers you might want to use it in. 

I uploaded one for someone else a few days ago, but they didn't need it, it's here in case you want it though, [http://ubuntuforums.org/showpost.php?p=6455487&postcount=5](http://ubuntuforums.org/showpost.php?p=6455487&postcount=5)

EDIT: how to edit your GRUB menu for Intrepid's GRUB's uuid booting, link:  [uuid]("http://users.bigpond.net.au/hermanzone/p15.htm#root")

Regards, Herman :)

---

### Post by pioa on 2008-12-31
Thanks! :)

> **Herman said:**
> It's easy to make your own GRUB boot floppy disk, here, check out the how-to in this link, [How to make your own personalized GRUB Floppy Disk]("http://users.bigpond.net.au/hermanzone/p15.htm#grub_floppy_howto_make").
I am using grub4dos as bootmnager, it's great. It doesn't have stages. It's just the bootcode inside MBR plus an small file called grldr.

Doesn't I need the correct initrd and kernel switch?

> Intrepid Ibex's GRUB contains the most advanced stage2 file.
Sorry, what is 'Intrepid Ibex's GRUB'? Is it a fork of GNU GRUB?

Will the stage2 from Hardy also work?

I currently prefer 8.0 over 8.1 because in 8.1 the mouse driver inside VMware is broken (I either boot on bare metal or in VMware).

> Intrepid Ibex's GRUB can search for your device by the file system UUID number, so you'll have reliable booting regardless of what the hard disk numbering scheme is in different computers you might want to use it in.
Independent on what which harddisk numer, great thing...

Do you mean this would be also kernel update independent?

If I understand right... If I boot grub from floppy and use the stages from 8.1 I am perfect for USB booting for all time?

---

### Post by Herman on 2008-12-31
> Sorry, what is 'Intrepid Ibex's GRUB'? Is it a fork of GNU GRUB? Not really, at least I don't think so, it's still GNU GRUB 0.97, but it has a patch to give it the ability to boot by the file system uuid numbers instead of the 'root' command, as well as in the kernel line too.

> Will the stage2 from Hardy also work?Yes, it will work fine as long as you use it in the same computer or in other computers that have the same hard disk numbers. It may not be quite as reliable at finding the right device  in just any computer you might want to use or if you add or remove a hard disk. If you aren't planning on going anywhere and you only own one computer, that probably will never be a problem for you, please just disregard that part of my advice.

---

### Post by pioa on 2009-01-01
Can you provide please a premade floppy image with GRUB and this UUID feature and upload it? I guess this could actually help more then the stage2 file alone.

---

### Post by Herman on 2009-01-01
Alright, here it is.
```
dd if=/home/username/grub_uuid.img of=/dev/fd0 conv=notrunc
```
You should be able to use a command something like the one above to make your floppy disc. Good luck.

Regards, Herman :D

---

### Post by Herman on 2009-01-02
After you dd that image to the floppy disk, you'll need to edit the menu.lst file in it before it will boot anything.

You should delete all the numbers after the word kernel and after the word initrd.img and change to your own UUID numbers.

---

### Post by pioa on 2009-01-02
Thanks, that's pretty nice in any case. Also cool because you have additionally the option to from CD-ROM and to emulate a floppy image.

Only one thing is still questionable.... After telling the BIOS to boot the floppy, it will start grub. But how could grub boot the USB? Grub has still no USB drivers inside?

Do I need to copy the initrd and kernel to the floppy? The original purpose of the floppy was "Boot from Floppy TO USB", like the floppy image debian is providing...

---

### Post by Herman on 2009-01-02
:D I said you'll need to edit your menu.lst file yourself, but I can help you with that if I know the necessary details about your Ubuntu installation in the USB, mainly, the file system's UUID number. 
You can easily get that by booting the floppy disk and pressing your 'c' key to change from menu mode into [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") and typing the uuid command.
That will list all of the partitions in your computer, along with the names of the file systems and thier uuid numbers. Your Ubuntu will probably be the only one that has the ext3 file system.
If you're not sure, (if you have more than one ext3 file system or a reiserfs, you can test which is the right partition by taking a look at the /etc/lsb-release file. Just type 'cat (hd0,4)/etc/lsb-release and GRUB will show you that file, which will tell you what version of Ubuntu you're looking at. 
Then type 'uuid' again and take a careful note of the exact uuid number to edit your new menu.lst file with later.
You should easily be able to edit the menu.lst file from a live cd or from your operating system if you can get it to boot. 

As far as I know, the BIOS in your computer must support booting USB booting to be able to boot a USB drive. Your theory sounds correct though, if you could fit a Linux kernel and initrd.img on a floppy disc you should be able to boot those and mount the file system in the USB. According to [Rute User's Tutorial and Exposition]("http://rute.2038bug.com/index.html.gz") - byPaul Sheer, we should be able to do that and how to do so is explained in this page, 31.  [COLOR=#0000ff]lilo[/COLOR],  [COLOR=#0000ff]initrd[/COLOR], and Booting. I tried that myself quite some time back, we should be able to use GRUB or LiLo, but the problem I ran into was our modern Linux kernel seems to have grown much too large to fit in a floppy disc. You might be able to do it with a smaller or stripped down kernel. There are how-tos about how to re-compile your Ubuntu kernel and you might be able to do that and fit one on a floppy disc. That would be worth looking into. Try all the ideas you have and see what you can do, you never know until you try, and you're never beaten until you give up.

I thought you only wanted the boot floppy with GRUB in it so you'll be able to boot in computers that do support USB booting so that you won't need to go around changing each computer's BIOS settings everywhere you go, (if you're travelling for example).

What exactly is in the Debian floppy disc? ( [http://wiki.debian.org/BootingFromFloppyToUsb](http://wiki.debian.org/BootingFromFloppyToUsb)),? Have you downloaded the image from there and made it into a floppy and taken a look at it?

Regards, Herman :)

EDIT: I was just taking another look, it was a long time ago when I tried it, maybe I'm wrong.
A floppy disk is 1.44 MB, x 1,048,576 bytes each comes to 15099494.4 bytes.

   floppy disc    15099494.4 bytes
       GRUB is                   4096                 (according to the output from 'ls -lS /boot')
Ubuntu kernel    1905688
     initrd.img     - 8401688 
===========================
                                     4788022.4         - room left over - if my maths is correct - ?

---

### Post by pioa on 2009-01-02
> **Herman said:**
> As far as I know, the BIOS in your computer must support booting USB booting to be able to boot a USB drive.
Yes, but using the floppy as kicker is a nice workarround and should work on any BIOS.

> our theory sounds correct though, if you could fit a Linux kernel and initrd.img on a floppy disc you should be able to boot those and mount the file system in the USB.

> I thought you only wanted the boot floppy with GRUB in it so you'll be able to boot in computers that do support USB booting so that you won't need to go around changing each computer's BIOS settings everywhere you go, (if you're travelling for example).
No. Boot from Floppy to USB on computers which do not support USB booting or where the BIOS has bugs.

> What exactly is in the Debian floppy disc
As far I understand it helps booting USB even if the BIOS does not support USB booting.

Other Distros like DSL have similar floppies, see
[http://damnsmalllinux.org/wiki/index.php/Boot_Floppies](http://damnsmalllinux.org/wiki/index.php/Boot_Floppies)

I just haven't found such a help floppy image for Ubuntu.

Doesn't Ubuntu inherit this great feature from Debian?

---

### Post by Herman on 2009-01-02
The Debain floppy disc will probably boot Ubuntu just as well as Debian, why not give it a try! :D

---

### Post by pioa on 2009-01-02
I've done that and it didn't work.

---

### Post by Herman on 2009-01-02
:D What's in it? A kernel?

I tried to copy a kernel to the floppy disk but it didn't work, said there's not enough space on the destination. The initrd.img file is a lot larger than the kernel is too, so there must be some tricks I don't know. 

I'm having a lot of trouble with floppy discs and floppy disc drives, the ones I have are terribly unreliable. Maybe I'm buying the wrong brand or something. I threw away about ten floppies before I had two good ones made yesterday, and this morning only one of those will work. I'm finding it very frustrating trying to work with floppy discs, no wonder not too many people use floppy discs anymore these days. :(

---

### Post by pioa on 2009-01-02
If it takes to long to create them use a virtual floppy and a virtual environment for testing. I use them finally on physical medium after I am done.

Yes, some "tricks" or "hacks" are needed in order to create such a floppy. It seams this is a very advanced topic. If it would have been easy I wouldn't ask.

Before I thought such a boot floppy already exists and I am simply to stupid to find it. Unfortunately such a floppy image doesn't exist.

---

### Post by Herman on 2009-01-02
:D

[Marco&#8217;s blog Archive for the &#8216;GRUB 2&#8217; Category, ATA bug fixes]("http://mgerards.net/blog/?cat=4"), Thursday, August 14th, 2008

[USB Support for GRUB 2]("http://grub.enbug.org/USBSupport%20GrubWiki:%20USBSupport") (last edited 2008-09-01 20:49:55 by VesaJääskeläinen

What do you think of those links?

I think that GRUB2 is not finished enough yet for most people, but maybe if you're not in a hurry and you are a little bit lazy, you could simply wait a while. 
I don't think anyone knows how long before GRUB2 will really be ready though.

Here's one more link, about how to make a floppy disk from GRUB2, [how to build a grub2 floppy with fs adventure]("http://www.mail-archive.com/grub-devel@gnu.org/msg02926.html").

---

### Post by pioa on 2009-01-02
To wait for GRUB2 can turn into waiting like for HURD. GNU developement is like evolution on planet earth, it works great =D> but in your lifetime you don't see anything to finish. Therefore waiting is not really what I want, I need it now and not in some years.

This is just like PLoP Bootmanager. Generally a great thing, works generic for any kernel and even for any operating system, but it will take ages until it's no longer experimental.

While such a Boot From Floppy To USB floppy image works in any case and it can be considered as stable. I just would like to see this Debian floppy disk ported to Ubuntu.

---

### Post by GerryB on 2009-01-02
Puppy Linux has a feature in its menu whereby you can create a boot floppy to get older computers to boot from a pen drive. Works like a charm. I have no idea how it works but it's the simplest thing I've seen. Maybe someone with this kind of expertise could create a similar feature for Ubuntu..Just a thought.

---

