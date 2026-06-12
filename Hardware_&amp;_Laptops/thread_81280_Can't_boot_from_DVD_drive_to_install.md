---
title: "Can't boot from DVD drive to install"
date: 2005-10-24
forum: Hardware &amp; Laptops
---

### Post by dhigger on 2005-10-24
I have a 10 year old laptop. In spite of setting the boot order option in the BIOS, it will not boot from the DVD/CD drive.

I have tried:
[LIST]
[*]Setting all boot options to CDROM in the BIOS - doesn't work
[*]Smart Boot Manager - doesn't find my CDROM even when I set the IDE I/O ports manually to 1F0,3F6 (and "Rescan all Drives").
[*]Updating the BIOS (no update available)
[/LIST]

I currently have Windows98 and Mandrake10 on the machine - dual boot. I want to wipe the lot and use Ubuntu, but I can't try the Live CD to check for hardware compatibility. When I installed Mandrake, I browsed the install CD and found a floppy boot image which successfully allowed me to boot from the floppy drive to the CDROM drive and installation would start. This boot floppy which finds the CDROM only works for Mandrake (and only for that version of Mandrake, too).

I was hoping that Ubuntu would have something similar. :confused: 

Any ideas?

---

### Post by dhigger on 2005-10-27
I note that there are a number of unanswered posts similar to mine in this forum.  Well I have a solution which worked for me: there is a floppy disk which simply did what I was looking for - boot from the floppy, straight to the CD.

It's the Bootable CD Loader v1.50Z. You can get it at these places:

[http://www.bcdwb.de/bcdw/index_e.htm](http://www.bcdwb.de/bcdw/index_e.htm)
[http://www.wolfgang-brinkmann.de/bcdw/index_e.htm](http://www.wolfgang-brinkmann.de/bcdw/index_e.htm)
[http://bootcd.narod.ru/index_e.htm](http://bootcd.narod.ru/index_e.htm)

You can't just copy the bcdl150z.ima file to a floppy because it's a floppy image (not a picture, that means it's a replica of a whole disk). You need to use rawrite.exe, rawrite2.exe or fdimage.exe to write the file to a blank floppy disk. Search for these files on Google or someplace. They're very common. I used fdimage.

It worked fine for me. Turned my laptop on, floppy boots, then the CD starts spinning and I'm booting from the CD.

Dave

---

### Post by TheD on 2005-11-29
Why there is no simple EXE file able to load installer from any Win16/32?
I am too in a similar situation as previous posters, I just spent 3 hrs trying to install ubuntu on my notebook which can boot from floppy only, and cd-rom is a pcmcia add-on;
i am able to boot it to DOS only wth the CD-ROM support from its own boot floppy only; then i insert windows startup floppy to run fdisk and format hdd as well, and then i'm stuck.
loadlin ask me some stupid questions which I dont understand ("where is my linux" lol, and it asks actually really good question - where the f*** is this linux installer exe on my installation disc? i would love to yell at it and say "its here, on the cd somewhere, u moron" ;)
grub _for dos_ is packed as **tar.gz** - like WTF?! is it for DOS or is it for another *nix os, since it is packed in tarball?!
Yeah i know, for some of u im the stupid one, but let me tell you guys:
if this linux, any linux, is supposed to draw current windows users to linux, then at least it should have a courtesy of freaking booting from a single "SETUP.EXE" file, something which every windows user would understand.
I cannot believe some smart guys can write entire OS, yet they cant write simple installation routine for it!
I'm really cursing here so much that even my dog ran out of my room already >:/
OK, my rant is over.

Anyway - is someone willing to explain how to install this (or any) distribution on a notebook/laptop from floppy, when there is no OS on hdd, and when it must be booted with DOS 5 boot disk first to install the pc card cd-rom drivers or nothing else will see the cd-rom at all?
Or is there some REAL grub for dos working straight from DOS without freaking tar compression (yeah i know, there is probably some DOS version of tar decompression somewhere, but again - wtf!) which will be able to start installing it?

EDIT: yes, none of the mentioned here nor found on the web supposedly-boootable cd loaders works, **NONE**. It must be done from DOS loaded at boot and running the pc card driver to see my attached cd-rom, so what i probably need is some DOS-based ubuntu installer (loader?) which i can put on a floppy and by running it it will start installation from the cd with some command string? Or if Im wrong please correct me and explain?

...and up until today i thought installing windows nt on it was a troublesome process, lol! :D

---

### Post by blastus on 2005-12-02
[quote=TheD]Why there is no simple EXE file able to load installer from any Win16/32?...[/quote]

Because Linux is not a Windows application. The EXE file format is used in Windows only. Linux has its own executable file format--I believe it's called ELF (executable and linkable format.) And as far as I know, there is not a single Linux distribution anywhere that supports installing from MS-DOS. Even Windows 2000 and XP can't be installed from MS-DOS because SETUP.EXE is a Windows application.

There are two ways a system can boot from a CD; through DOS-based drivers or the system BIOS. The DOS-based method uses Microsoft proprietary SCSI or ATAPI drivers to boot from a CD and is only designed to work with MS-DOS based operating systems like Windows 95 and Windows 98. The system BIOS method can boot to a variety of operating systems and uses BIOS technology to access the CD.

If you can't boot from the Ubuntu CD (or any Linux distribution CD) then your BIOS does not support booting from CD media. That said, I don't know if a PCMCIA CD-ROM device can even be booted from the BIOS.

---

### Post by René Kabis on 2005-12-31
[QUOTE=dhigger]I note that there are a number of unanswered posts similar to mine in this forum.  Well I have a solution which worked for me: there is a floppy disk which simply did what I was looking for - boot from the floppy, straight to the CD.

It's the Bootable CD Loader v1.50Z. You can get it at these places:

[http://www.bcdwb.de/bcdw/index_e.htm](http://www.bcdwb.de/bcdw/index_e.htm)
[http://www.wolfgang-brinkmann.de/bcdw/index_e.htm](http://www.wolfgang-brinkmann.de/bcdw/index_e.htm)
[http://bootcd.narod.ru/index_e.htm](http://bootcd.narod.ru/index_e.htm)

You can't just copy the bcdl150z.ima file to a floppy because it's a floppy image (not a picture, that means it's a replica of a whole disk). You need to use rawrite.exe, rawrite2.exe or fdimage.exe to write the file to a blank floppy disk. Search for these files on Google or someplace. They're very common. I used fdimage.

It worked fine for me. Turned my laptop on, floppy boots, then the CD starts spinning and I'm booting from the CD.

Dave[/QUOTE]

FYI, this worked for me as well. I had a Compaq Presario 1200 Laptop that suddenly wouldn't boot from the CD-Rom drive anymore. It wouldn&#8217;t even accept a Windows XP CD anymore, whereas I had done a piror install using an XP CD on it before.

I used the Bootable CD Loader (the last of the three programs on the sites above, which is a Diskette image that needs to be extracted onto a diskette; I used WinImage v.8.0), and suddenly it saw Ubuntu on the CD. Prior to that, I could have sworn that the CD drive itself was damaged (ie, not spinning up enough to read the CD).

Prior to this, I had gone nuts trying to load an external USB CD-drive (didn&#8217;t work) as well as a parallel-port CD-drive (*did* work, it was a Bantam Backpack) from a MS-Dos boot diskette, and then trying to launch the Ubuntu installer using linld.com. Suffice it to say, this didn&#8217;t work, as I couldn&#8217;t figure out where the install image for Ubuntu was on the CD!!

Oh, well. Everything is fine now. But I'm keeping the diskettes just in case... =)

Thanks Dave!

---

### Post by dcon on 2006-01-05
No dice for me.  I loaded the file as directed above and set the boot order to floppy, cd, hard drive.  It definitely boots to the floppy however the system then just displays an "X".  If i hit a key, the floppy drive churns for a few seconds and another "X" appears beside the first.  Again, the external CD drive is totally unresponsive.  If I take out the floppy and hit a key, the system starts booting into windows and the external CD comes back to life.

HELP!  - How the heck can I get Ubantu on this puppy?

---

### Post by Bytebull on 2006-01-05
you gave your solution in your first sentence

update your BIOS for that system...

if it's that old then you need to firmware your bios and i bet you can change the boot sequence....

just a thought...

---

### Post by Bytebull on 2006-01-05
and to reply to your previous posts... your system bios that sets your boot sequence has nothing to do with your OS... its on your motherboard... so find out what motherboard you have and update the BIOS... EVEN if you have to burn it.... do it if its 10 years old.. you have nothing to lose but a boat anchor motherboard...

trust me...

---

### Post by dcon on 2006-01-06
I wiped out the old windows 98 installation altogether.  When rebooted, the CD responds (ie...there is some spinning)  however all I get is the standard 
"Invalid System Disk".  I'm using a Live CD for 386 machines (PC (Intel x86) live CD) which runs great on my Toshiba.  Here are the specs for the VAIO

Sony VAIO PCG-505TR
    * Mobile Pentium MMX 233 Mhz
    * 10.4 inch TFT XGA LCD screen (1024 x 768)
    * 6 GB Harddrive
    * 128 MB RAM

Am I using the right version of Ubantu or is the Install version the answer?

---

### Post by mathan on 2006-08-26
I have the same problem :) but with a twist...anyone care to help out??

I have a ASUS A6K laptop. A lovely little mashine with a 64-bit AMD Turion CPU inside.

I wanted to try out Opensuse 10.1 and downloaded DVD and burned and tried to boot on it...no luck!

Ok, Lets try this Ubuntu distro (6.06) I thought then...so I downloaded the DVD and tried to boot on it...no luck either.

I inserted a Windows Vista beta DVD and tried to boot on it. No problem at all.

Tried all three DVD:s on my other computer. No problem with any of them.

My conclusion is. Linux bootloader on the DVD:s does something else than the Vista bootloader. Therefore all of them work on one computer and only the Vista DVD on the other computer.

I would use the floppy-sollution IF my computer would have a floppy reader, but it doesn't!!!

So, what to do now??
How can I try out and install Ubuntu-Linux on my ASUS-computer???

---

### Post by matthewboh on 2007-02-10
Wow - I'm glad I like learning new things!

Anyway, I have a VERY old Pentium PC - so old the BIOS doesn't support booting from the CDROM.  So I followed the directions on how to get a Boot CD Loader, and got that up and running.  It boots, goes to the CD and spins it up, starts looking for an NTFS partition on my hard drive - can't find one.

So I suppose all I need to do is create an NTFS partition?  How do I do that with Windows 95 running?  Can I do it off a floppy?  I really just want to get rid of Windows 95 - so I would be happy just wiping everything off the two HHD's I have.

Thanks!

---

### Post by Snargledorf on 2007-04-21
Just found this thread linked from another...THANK YOU!!! Exactly what I was looking for worked like a charm.

Knew it was out there just couldn't find it anywhere.

---

### Post by orangeslide on 2008-02-21
I THINK I GOT IT
ok so what i did is i booted up to Windows and right clicked the Ubuntu icon the clicked open. I then clicked the yellow icon and it started than said you will need to restart to finish. I then restarted and didn't CLICK ANYTHING and it came to OS choices and said Windows XP or Linux Ubuntu i clicked that and im all good.
hope this helps!

---

### Post by tommys5 on 2008-04-18
I'm in the same boat here as the person with the PCMCIA Bantam Backpack CD ROM.

I have an older Dell Latitude that I want to install Ubuntu onto. But I can't get the floppy boot to see the CD ROM.

I tried the BCDL boot but it doesn't load drivers for the CD ROM.  

Any other ideas,???? PLS?

---

### Post by oldsoundguy on 2008-04-18
you could try going to bootdisk.com and download a floppy boot disk for WinDOZE that has cdrom support.  That MAY work .. but you will have to be able to format the drive also .. so make sure that your Ubuntu install CD has the gparted format utility  Also noted above that someone had an old windows system and when the install went to look for an NTFS format, did not find it in order to re-write it  ..  ahhh ereeeerr .. NTFS  =  NT File System.  98 did not have same.

---

