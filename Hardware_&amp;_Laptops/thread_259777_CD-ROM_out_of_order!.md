---
title: "CD-ROM out of order!"
date: 2006-09-17
forum: Hardware &amp; Laptops
---

### Post by xyz on 2006-09-17
[b]After some good old cleaning up, CD-ROM works now.
Please read latest posts. Thanks.
*Smart Boot Manager Problem*[/b]

Hi everyone,
I'm planning on trying to install Ubuntu in an old Dell Latitude Windows 98 SE (HD...about 4G-about 2.5 free space) using the netboot approach because my CD-ROM's dead! Once the installer downloaded, I can surely delete lots of Windows stuff to make more room.
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

I know I should have a bigger HD and more RAM but let's say I want to try it anyway.

Do you think I should give it a try or just forget it?
Is there another lighter distro that can be installed via Internet?
I'm not sure how to go about this and I thank you for your help.

---

### Post by Indras on 2006-09-17
There's still plenty of Linux distributions that can be installed via network.  Debian, for instance, can be installed with just three floppy disks and a network connection.  Many things feel very similar to Ubuntu, as well, since Ubuntu is based on Debian.

However, judging from the specs you've listed, I would be wary of installing the normal desktop package (which installs both Gnome and KDE) in the Debian installer.  If you want a nice fast system, download and write the three floppies (four if you have a PCMCIA card), then boot up, repartition, and install just the base packages.  Once your system restarts to your new base system, which will be all text mode, log in as root and do "aptitude install x-window-manager xfce4" which will install the xfce desktop, similar to xubuntu.  After it is done installing, type startx to run it.

I'd be very wary of this method, however, as Debian is definitely not a beginner's operating system.  Do you have a CD-ROM drive you can put in your system temporarily just to do a base install of (X)Ubuntu?

---

### Post by xyz on 2006-09-17
Thanks **Indras!**
Unfortunately I've got nothing in working order: no CD-ROM, not even a temporary one; floppy's out,too.
Is there, despite this, any Linux I could install on that box? It doesn't have to be Ubuntu, Debian,just something very light.
A friend wanted to throw this laptop away and I said I'd try and do something with it. Sure wish there was a chance I could.

---

### Post by xyz on 2006-09-18
I think I did things right but apparently not!
Following instructions here:
[https://help.ubuntu.com/community/In...on/FromWindows](https://help.ubuntu.com/community/In...on/FromWindows)

  

> I proceeded to create a directory called boot in the root directory of the first primary partition of your hard drive (usually drive c:\, which it will be referred to as from now on).
    

and then downloaded linux and initrd.gz from [WWW] [http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/](http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/) and save them to boot.

The I went to Windows 95/98/ME (using Loadlin) since I have Windows 98 SE installed and downloaded loadlin.exe.gz .
I then rebooted in MS-DOS mode and typed, like the howTo said:
```
cd c:\boot
loadlin linux initrd=initrd.gz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
```

At this point, it says:
> Now you should have a network installation going :)

Note: On some computers the installer has problems with the video card and you may get a "melting screen". I replaced vga=normal with vga=771 and it worked on my laptop Stjepan Stamenkovic 
And I don't!
However, I get this message ,which I don't understand, after I type the above command line:
> Enter the name of kernel image file followed by optional command line parameters for Linux (e.g. root=XXXX) or @file (file= param file)

If anyone can give me a hand here, I'd greatly appreciate it.

---

### Post by xyz on 2006-09-18
Further searching indicates I must download _"the kernel file that matches my system???"_
Also looking into lighter stuff:
[http://www.vectorlinux.com/](http://www.vectorlinux.com/)

---

### Post by xyz on 2006-09-18
Well I guess this is good news!
I got down to basics, grabbed a dust rag and a blowdryer and proceeded to clean to clean my CD-ROM!
Guess what? The CD-ROM recognizes what's in it now!!

The bad news is this old BIOS won't boot from CD-ROM.
Could something be done to force-change boot order on this Dell Latitude Pentium-233 - 64MB RAM Video Memory 2MB Level Cache 2: 512MB??

I can no problem kick Windows 98 SE off this computer so, please, tell me if I'm right:

-once Windows is gone (use Partition Magic, it's in the box?), there would be no reason this computer wouldn't go to 2nd boot level: CD-ROM?
And then maybe install a lighter distro more adapted to 64 RAM - 4,1G HD?

I'm not sure how to best proceed here. Thank you for reading.

---

### Post by xyz on 2006-09-18
I've been "playing" with Puppy Linux -quite impressive,fast- I didn't recognize my old Dell Latitude CD!
Unzipping the file with free 7 Zip (.exe.gz OK)) straight into C:\, a few easy clicks laters, you're booting in DOS and it asks you if you want L or W!
What a world we're so lucky to live in?

Also I'm downloading Xubuntu and will try to install after I cleaned the Windows partition....

---

### Post by george_apan on 2006-09-18
With that PC (especially the 64MB RAM) I wouldn't even try any of the big distros (including K/X/Ubuntu) with a graphical environment. They would just crawl if they could even boot. A server install (no gui) would work though. A distribution like Puppy or Damn Small Linux would fit nicely on the other hand. Another one that I saw lately in distrowatch and been meaning to try is [Deli linux]("http://www.delilinux.de/").

---

### Post by xyz on 2006-09-18
Thanks goerge_apan,
The more I'm reading about it, the more I understand what you mean!! Will follow your advice.

However, I've also been reading it's IMPOSSIBLE to remove Windows 98 SE. I just can't believe it. I just want this little box to run nicely only on Linux...and the distros you suggest will do just fine.
What would be the best way to go?

---

### Post by george_apan on 2006-09-18
There's no way that you are forced to use windows. If I remember well, Puppy includes gparted. It's a tool to repartition your hard drive (that will destroy your existing data, so be careful). You can remove all fat32 partitions from there and create one (or maybe two, one for the / directory and one for your /home directory) nice ext3 partition that you can use for any distribution.

---

### Post by xyz on 2006-09-18
From Deli's site:
>  If you have a brand-new hard disk or you wish to re-partition your drive type cfdisk, an example follows

    *
      cfdisk is an easy menu-driven partition program create new partitions with New
    *
      Create two primary partitions, a big one for the the file system and a small one for the swap partition
    *
      The size for swap depends on your amount of RAM. I suggest at least 64 MB
    *
      select the swap partition an select Type, then enter 82 (should be the default)


This little computer's too old to change boot order! I'll have to go into Windows and,for instance, use Partition Magic which happens to be installed to delete the partition,right?
Then I guess I'll just pop in Deli's Install CD and proceed!

---

### Post by george_apan on 2006-09-18
If Deli has cfdisk you can use that to repartition your hard drive and wipe windows too. Using cfdisk is really easy, but I haven't installed Deli to give you some instructions on the overall installation procedure. If you want to keep you existing partitions, cfdisk won't do, but gparted as I mentioned earler will work. You should not need any windows CDs any way you try it though.

---

### Post by xyz on 2006-09-18
Yes you're right; that's how it SHOULD've happened but I just had to blow it somehow! :frown: 
I worked all day, evening and  night (it's nearly 5 AM my time now!) on this and I think I "lost it" at some point.
I removed Windows 98 SE with Partition Magic knowing perfectly well that this 'ole Dell would not boot from CD-ROM nor would it boot from CD-ROM if Diskette and/or HDD boots 'failed'.

There is simply NO WAY to boot from CD-ROM in BIOS...and I knew that and went ahead anyways. So now all I've got is a nice and totally empty 4.1 G HD and I suppose I'll have to ask a friend to create some kind of Diskette Boot since it seems to be the only possible thing to boot from...  according to unchangable BIOS settings.

So I should have just popped Doli into the CD-ROM and re-partitioned from Windows since the only good thing this darn CD-ROM does is to recognize what's in it once Windows is (was) on!
I'm up shit creeck now..so live and learn!
Thanks for your help and support, though!  :grin: Much appreciated it!

---

### Post by george_apan on 2006-09-19
Well if you can boot your laptop from a floppy you can use a [Smart Boot Manager]("http://btmgr.webframe.org/") floppy disk to divert the boot process to the CD-Rom even if the bios doesn't support it.

---

### Post by xyz on 2006-09-19
> **george_apan said:**
> Well if you can boot your laptop from a floppy you can use a [Smart Boot Manager]("http://btmgr.webframe.org/") floppy disk to divert the boot process to the CD-Rom even if the bios doesn't support it.

Thanks george! I'll do that.
I'm not 100% sure the floppy "drawer" type thing works as I have not had the opportunity to test it. I just got this box; a friend wanted to throw it away.
Everybody being just soooo busy these days, I hope I can get someone to download SMB and put it on a floppy ...before the end of the year!!

Anyways, I'll let you know how it all ends up turning out...sooner or later.
Good day to you.

PS: one last thing! How did you manage to link me up to Smart Boot Manager without typing the whole http...adddress in your post.
I tried <a href... <li>>a href..to no avail. Just a detail I'd like to know how to do.Thx.

---

### Post by george_apan on 2006-09-19
> **xyz said:**
> PS: one last thing! How did you manage to link me up to Smart Boot Manager without typing the whole http...adddress in your post.
I tried <a href... <li>>a href..to no avail. Just a detail I'd like to know how to do.Thx.
Oh that! You can do it by typing
[HTML][link text]("http://www.example.com")[/HTML]

Or you can use the "Insert link" button on the toolbar so you can give the address and the text will be created. You will have to manually edit the link text in this case.

---

### Post by xyz on 2006-09-19
Oh that's all there is to it then! I was getting too complicated with HTML codes. Thx.

---

### Post by xyz on 2006-09-19
Well, Goerge your links to Smart Boot Manager in your previous post seems dead whether on my Ubuntu box or on my friend's Windows XP. In fact, no matter what link I highlight on the SBM site, the page stays put!  :-?  Tried the link over a couple of days, still the same story! The following was done on my friend's win box!

So I went here: (French Ubuntu found in Google):
[http://doc.ubuntu-fr.org/installation/smart_boot_manager](http://doc.ubuntu-fr.org/installation/smart_boot_manager)
Downloaded SBM (sbootmgr.dsk) there and found English explanations here:
[http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)

Then, still on the French Ubuntu site, I downloaded what I needed to tar, unzip, call it whatever you want the sbootmgr.dsk where it says: rawwritewin and the floppy was successfully created/written with it.

Floppy booted fine but I couldn't change the Dell's boot order despite the fact I was going by the rule using SBM. Why the hell didn't it work then?

> 5. _Insérer la disquette d"amorçage et le cd Ubuntu dans le lecteur,_ et vérifier que la machine démarre bien de la disquette.
6. Quand apparaît le menu Smart Boot Manager, sélectionner l"option avec cd-rom et valider par Entrée.

I'm assuming you guys don't understand French, sorry if I'm wrong.
[i]5 says pop in floppy **AND** Ubuntu CD (any other would do!)and make sure your box boots from floppy.
6 says that _when SBM menu shows, select the CD-ROM option and press Enter._[/i]

No need for me to alter boot order here since it boots from floppy anyway BUT here is the damn problem "pop in floppy ** AND** CD". And that's not possible; that is simultaniously, on this box.

I don't know how you'd call them floppy and/or CD-ROM (look like drawers to me). There's one single spot for both of them so I can only use one at a time; for instance, I take floppy out and insert the CD-ROM drawer but I sure can't _when SBM menu shows, select the CD-ROM option and press Enter._ since it implies that BOTH floppy and CD-ROM are operational at the same time!!
**Dead end - check mate! Shit!**

Shall I start a new thread since this one's title doens't reflect the real situation here?

PS:Just a thought much later in the night: I don't know much about floppies but is there a-ny-thing I could install from a floppy into this box and that would then give me "some kind of OS" to work with?

---

### Post by george_apan on 2006-09-20
Oh, I'm sorry I didn't realise that you had to swap the floppy and the CD in your laptop. No smart boot manager will not do in this case then.

So what can you do about it? Well, there is debian, which can be installed using floppies through the internet. A minimal debian installation should work fine. You will have to have the laptop connected to the internet for that.

You could also try installing puppy from dos. Take a look [here]("http://puppylinux.org/wikka/InstallingPuppyInMsdos") for more info.

I guess you could also take out the hard drive, put it in a PC that has a working CD, do the installation and then move the hard drive back to the laptop...

---

### Post by george_apan on 2006-09-20
Wait! There might be a chance you don't have to go through all this.

I just saw that smart boot manager has an install option! Press Tab to go to the menu, go to "System settings", press Enter, go to "Install Smart BootManager" and press Enter again. I haven't tried this but it should work. You should have Smart boot manager installed to the hard drive now, so you can turn the laptop off, swap the floppy for the CD drive and then when you boot you should get smart boot manager so you can select to boot from the CD.

Does it work?

---

### Post by xyz on 2006-09-20
> **george_apan said:**
> Wait! There might be a chance you don't have to go through all this.

I just saw that smart boot manager has an install option! Press Tab to go to the menu, go to "System settings", press Enter, go to "Install Smart BootManager" and press Enter again. I haven't tried this but it should work. You should have Smart boot manager installed to the hard drive now, so you can turn the laptop off, swap the floppy for the CD drive and then when you boot you should get smart boot manager so you can select to boot from the CD.

Does it work?

Holy Smokes...I just saw your post! Will jump on it and try it right now!
In the meantime, I'm posting my little research on alternative solutions!
Thanks George!!!fingers crossed  :-$

---

### Post by xyz on 2006-09-20
I'm posting this up hoping people, in similar and/or non-similar situations as mine, may find a way out of a tricky situation.

**_1. TestDisk_**
[TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")
> TestDisk is a powerful free data recovery software! It was primarily designed to help recover lost partitions and/or make non-booting disks bootable again when these symptoms are caused by faulty software, certain types of viruses or human error (such as accidentally deleting your Partition Table). Partition table recovery using TestDisk is really easy.


*Also* see **2. TestDisk && Live rescue cd**

_TestDisk is included on:_

> Knoppix  
PLD RescueCD  
Recovery Is Possible  Linux rescue system 
Ultimate Boot CD  
GParted LiveCD 
Note, TestDisk is also avaible on the following distributions 
ALT Linux  backports 
Debian  contrib 
Fedora Extras  
FreeBSD  ports 
Gentoo  
Gentoo Portage 
Mandriva  contrib (ex-Mandrake) 
PLD Linux  distribution 
Source Mage GNU/Linux 
Ubuntu


**_3. Active @ Partition Recovery Demo_**

[Active @]("http://www.partition-recovery.com/")
_Also:_ [Active UNERASER]("http://active-uneraser-data-recovery-software.download-553-4743.datapicks.com/")

> *Can be placed to and run from bootable floppy*  
  
  - Displays complete physical and logical drive information
  
  - Supports IDE / ATA / SCSI drives 
  
  - Supports large (more than 128GB) size drives 
  
  - Supports FAT12, FAT16, FAT32, NTFS, NTFS5 file systems
  
    *Supports MS-DOS, Windows 95/98/ME/NT/2000/XP/XP       Professional x64/XP Home x64/2003/2003 Server x64 partitions* 
  
  - Detects deleted primary/extended partitions and drives 
  
  - Scans partitions damaged by virus or with damaged MBR 
  
  - Ability to preview partition data before recovery
  
  - Displays long file names 
  
   -Ability to create Disk Image as set of 1GB files 
  
  - Creates backup for MBR, Partition Table, Boot Sectors
  
  - Restores MBR, Partition Table and Boot Sectors from backup
 
  - Saves detected partition information back to HDD  
  
  - Creates a Raw Disk Image   new!
  
   -Restores Raw Disk Image back to HDD   new!


**_4.  - Linux Recovery and Boot Disk Creation_**
[YoLinux]("http://yolinux.com/TUTORIALS/LinuxTutorialRecoveryAndBootDisk.html")
*This covers the creation and usage of boot floppies for system recovery.*

- Creation / useage of a floppy with GRUB boot loader.
- Creation / useage of a floppy with LILO.
- Creation / useage of a recovery floppy


**_5. Linux CDs and floppies_**

[http://www.linuxmigration.com/quickref/install/media.html](http://www.linuxmigration.com/quickref/install/media.html)
***Includes:***

- Places to obtain Red Hat Linux
- Creating Red Hat Linux CDs
- Creating a Red Hat Linux boot floppy
- Make a boot floppy on a MS-Windows machine
- Make a boot floppy on a Linux machine
- Installing Linux from the Internet


**_6. Partition Recover Linux_**
[ Software Listing]("http://www.sharewareconnection.com/titles/partition-recover-linux.htm")

***Feel more than free to add to this! :D ***

---

### Post by xyz on 2006-09-21
OK  SmartBootmanager did install and that's when I began to hope.
I stuck the CD-ROM in with Deli Linux CD (and others as well) but nothing happened so far.

---

### Post by xyz on 2006-09-21
I found an article by **Brad Fuller** here:
[Resurrecting old PC]("http://digitalmedia.oreilly.com/2005/03/23/linuxmusic.html")
especially the part about SmartBootManager!

I took the liberty of sending him this email. Hopefully he'll have a minute to reply:

> Hi M. Fuller,

First of all I'm sorry to bother as you are probably a very busy man but I've really been trying to solve my problem. I keep bumping against one problem or another as you may want to check this out [http://www.ubuntuforums.org/showthread.php?t=259777](http://www.ubuntuforums.org/showthread.php?t=259777)  (my pseudo is xyz) if you can spare a little time, I'd be most grateful.
 
I have been reading your very interesting article here:
Resurrect Your Old PC for Music—with Linux
[http://digitalmedia.oreilly.com/2005/03/23/linuxmusic.html](http://digitalmedia.oreilly.com/2005/03/23/linuxmusic.html)

and more particularly the part about Smart Boot Manager:

"With the floppy and the CD in their respective drives, I restarted the computer. Smart Boot Manager displayed a screen with a number of boot-device choices. I selected "CD-ROM," but..."

To make a long story short, I've got this old Dell Latitude CP and I accidently wiped off Windows 98 SE aiming to install a small Linux distro on it as this laptop has 64 RAM/4.1 G HD.

My problem with SBM is this: the laptop has drawer-like Floppy and CD-ROM meaning that I can't, as you say "With the floppy and the CD in their respective drives"...because I have to take one out so as to insert the other.

A nice member of the Ubuntu community by the name of George told me to try to install SBM on the drive thus I can pull out the Floppy "drawer" and insert the CD-ROM "drawer" so as to be able to proceed with the installation of a small Linux distro.

I could install SBM but somehow could not proceed with installation using a CD in the CD-ROM.
Is there a way to do it? What did I miss?

Again thanks for any help you could bring me even if it's to say "No way, there's no way to do it because you can't have your floppy and your CD working simultaniously."

Hope to hear from you soon.

We'll see...

---

### Post by george_apan on 2006-09-21
Sometimes you have to wait for a while until the CD gets read by the CD drive. I can't understand what else you might be doing wrong. You select the CD-ROM with the arrow keys when SBM boots and press enter right? Do you get an error message then? Why doesn't it boot?

Is the CD-ROM drive OK to begin with? Did it read CDs before?

---

### Post by xyz on 2006-09-22
"Did it read CDs before?" - At first no and that was the initial reason for this thread which I labelled 'CD-ROM out of order'...then I grabbed a blowdryer and a dust rag and somehow that did it: it read CDs. So I'm assuming it is in working order now like it was before I deleted the Windows partition.

The 1st time I succeeded in installing SBM, I got an error message when the little window came up asking: press Y if you want to install. Which I did and got an error reply.
After a while I remembered that my keyboard layout is configured for Swiss_French for the simple reason that I can type in different languages that way. English or American layouts don't work well for my use of it.

For some reason, when I boot on some Live CDs, the layout switches to American. And so id did as well when I installed SBM. I just had to remember that in that particulat keyboard configuration I had to hit Z when I want Y.

"You select the CD-ROM with the arrow keys when SBM boots and press enter right?"  Yes I did. And I was able to remove the floppy drawer and SBM was still on.

I'll try again in a little bit. Thanks.

---

### Post by xyz on 2006-09-22
OK SMB is installed and I turn off the computer. Take floppy out; insert CD-ROM with Deli's in it.
This is what I have on the screen:
> Boot Menu
NONE Quit to BIOS
NONE Power off
NONE Reboot
NONE Harddisk

And nothing happens. I tried pressing ENTER on NONE Harddisk > Black screen > Reboot > CD is spinning in there > and nothing > sometimes it doesn't sppin!!
I don't know what I'm doing wrong.

---

### Post by xyz on 2006-09-24
1. I read this and wrote to M. Fuller:
[Resurrect Your Old PC for Music]("http://digitalmedia.oreilly.com/2005/03/23/linuxmusic.html")
about recovering deleted partition.
His reply:
> You could also try slackware. It's small and might fit on floppies.

Good luck.

How could that be, I mean floppies can't handle that much MB, can they?

2. I wrote to Dell asking why I can't change boot order despite the fact that, in BIOS, it says all I have to do is to use left/right arrows to do so.

3. I wrote to M. Ben Gross about the possibility of installing a small Linux distro using a floppy:

> Hello Ben,
I don't mean to take too much of your time but if you have a minute to spare, I'd be immensely grateful. I read this:
[http://bengross.com/smallunix.html](http://bengross.com/smallunix.html)
This is what I need to figure out:
- I accidentely deleted Windows 98 SE from an old Dell Latitude CP - 64 RAM - 4.1G HD. So I've got a nice and totally empty drive.
- It boots from floppy and I can't change the boot order. It has "drawer-like" Floppy and CD-ROM which cannot be used simultaniously.
- what GNU/Linux distros could I download/write to a floppy and then proceed to install? Or any other OS which could allow me "to enter" this computer again?

Thanks for your help.

4. His reply:
> Several of the distributions on the page allow your to boot from a floppy and then run a CD installer. Just search for floppy on the page. You could also boot from one of the CD distributions that will run in memory. Many devices will boot from a CD after it fails to boot from a floppy. Lots of distributions have a boot floppy to help you install. Just look around on the docs of various distributions. I have not tried this particular method of installation so I don't have a distribution to recommend.

Good luck,
Ben

Which one should I try to write to a floppy?

Thanks fot your time.

---

### Post by george_apan on 2006-09-27
Unfortunately it looks like your laptop does not detect your CD-ROM at all. Maybe it's a connector thing, so try pushing the CD-ROM in as far as you can. 

If it doesn't work all you are left is to get a distribution that boots from a floppy and installs through the network like debian. The laptop has a network interface (ethernet port) right?

If you do have a network interface I guess you could also boot through the network using a floppy like [etherboot]("http://www.etherboot.org/wiki/index.php"). In this case you should have another PC in the network to work as a boot server. I'm sorry but I don't have any more information about this since I never used it. Also have a look [here]("http://tldp.org/HOWTO/Network-boot-HOWTO/").

If you don't have a network interface things are more difficult. Your only choice is probably to get the hard drive out of the laptop, install a distribution like puppy on a different PC and then put it back in the laptop.

---

### Post by xyz on 2006-09-28
Thanks!
This is for sure my best bet and I've been looking into it:
> If you don't have a network interface things are more difficult. Your only choice is probably to get the hard drive out of the laptop, install a distribution like puppy on a different PC and then put it back in the laptop.
Reply With Quote

I sure wish we could take out ANY HD and stick it back into ANY laptop...
as far as compatibility is concerned! I'll keep at it awhile.

---

