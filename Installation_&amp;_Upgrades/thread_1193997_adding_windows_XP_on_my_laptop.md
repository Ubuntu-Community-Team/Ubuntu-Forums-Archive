---
title: "adding windows XP on my laptop"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by penshockke29 on 2009-06-22
hello guys, im just a totally newbie when it comes to ubuntu, im currently using ubuntu 8.04 and i really wanted to add windows XP on my laptop, BTW, i bought this laptop dell vostro a840 with ubuntu 8.04 in it.

can you please help me in installing another OS in my computer? (windows XP)

tnx a lot..

---

### Post by presence1960 on 2009-06-22
Boot off the Ubuntu Live Cd or gparted Live CD and resize your Ubuntu partition to create space for Windows. Then boot your Windows install disk and install to that free space or partition if you took the extra step and created a NTFS partition from The Live CD. When complete you will have to restore GRUB as windows bootloader will overwrite GRUB. Follow this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

At #6 use setup (hd0) to put GRUB on MBR.

P.S. Should have told you when you boot off Ubuntu Live Cd choose "Try Ubuntu without any changes to your computer". When the desktop loads go System > Administration > Partition Editor. Right click on your Ubuntu partition and choose resize. A window will appear. Choose how much you want to give for Windows. When completed click the green check mark labeled Apply in the toolbar at the top.

---

### Post by swerdna on 2009-06-22
@presence1960: has this ever worked before, with XP being installed with its boot files (boot.ini, ntldr etc) on a partition higher than sda1? I've not ever heard of it, but I'm willing to look and learn?

---

### Post by ddrichardson on 2009-06-22
> **swerdna said:**
> @presence1960: has this ever worked before, with XP being installed with its boot files (boot.ini, ntldr etc) on a partition higher than sda1? I've not ever heard of it, but I'm willing to look and learn?
It's not the partition but the 1024th cylinder limitation in LILO (the 8Gb point).  AFAIK this is not an issue with GRUB.

---

### Post by swerdna on 2009-06-22
> **ddrichardson said:**
> It's not the partition but the 1024th cylinder limitation in LILO (the 8Gb point).  AFAIK this is not an issue with GRUB.
I'm not talking about a Grub limitation. I'm talking about a pure microsoft-imposed restriction:

It is my understanding that you can install on a high partition provided the first partition is windows writeable, but not otherwise. I believe that the xp installer will say something like "invalid partition selection" and abort if the first partition is not in either ntfs of fat format.

But I am prepared to be wrong (often am actually).

---

### Post by penshockke29 on 2009-06-22
tnx a lot, im going to try it..

---

### Post by ddrichardson on 2009-06-22
> **swerdna said:**
> I'm not talking about a Grub limitation. I'm talking about a pure microsoft-imposed restriction:

It is my understanding that you can install on a high partition provided the first partition is windows writeable, but not otherwise. I believe that the xp installer will say something like "invalid partition selection" and abort if the first partition is not in either ntfs of fat format.

But I am prepared to be wrong (often am actually).
Never heard of that, however I've always put Windows on first if dual booting.

---

### Post by presence1960 on 2009-06-22
[http://ubuntuforums.org/showthread.php?p=7500905#post7500905](http://ubuntuforums.org/showthread.php?p=7500905#post7500905)

no special first partition is needed,just proven in this thread. In my experience I had initially installed Ubuntu to my entire hard disk by accident because I didn't read up on what I was doing when I started to install. I then resized Ubuntu's partition and installed XP on that (sda2) Of course the windows bootloader overwrote GRUB and all I had to do was restore GRUB. Windows can be installed on any primary partition not just the first (sda1). It doesn't work well if at all on an extended partition. Linux can work on primary & extended partitions.

People should really search our forum and use Google before spreading info to which there is plenty of documentation which refutes that info.

---

### Post by presence1960 on 2009-06-22
> It is my understanding that you can install on a high partition provided the first partition is windows writeable, but not otherwise. I believe that the xp installer will say something like "invalid partition selection" and abort if the first partition is not in either ntfs of fat format.


Not true, windows installs it's bootloader to MBR. Now on the other hand Windows 7 makes a 100MB partition for boot by default. I had XP installed on sda2. sda1 was ext 3 and it installed and worked fine.

Windows can be on any primary partition. it doesn't like extended or logical partitions.

---

### Post by swerdna on 2009-06-22
> People should really search our forum and use Google before spreading info to which there is plenty of documentation which refutes that info.It's a wide spread belief that a windows-compatible partition is required first up if installing 9x, 2000 or xp (not for vista). It seems that is not a universal requirement. Of course, I wouldn't spread incorrect info. But I would and do seek advice and clarification like I did here, politely. I suppose the reason I use terms like > I've not ever heard of it, but I'm willing to look and learnand> But I am prepared to be wrong (often am actually)is that I like to be polite when I feel my way in uncharted waters, particularly if I think my information might be wrong. And I do really appreciate the advice that I get, particularly if it's like my queries, i.e. politely given advice. The community spirit and friendly, helpful interaction on this forum is very appealing.

---

### Post by presence1960 on 2009-06-22
> **swerdna said:**
> It's a wide spread belief that a windows-compatible partition is required first up if installing 9x, 2000 or xp (not for vista). It seems that is not a universal requirement. Of course, I wouldn't spread incorrect info. But I would and do seek advice and clarification like I did here, politely. I suppose the reason I use terms like andis that I like to be polite when I feel my way in uncharted waters, particularly if I think my information might be wrong. And I do really appreciate the advice that I get, particularly if it's like my queries, i.e. politely given advice. The community spirit and friendly, helpful interaction on this forum is very appealing.

I wasn't referring to you personally. if it came out the wrong way accept my apology.

---

### Post by presence1960 on 2009-06-22
[http://www.dslreports.com/forum/r18694528-Windows-on-first-partition-rule](http://www.dslreports.com/forum/r18694528-Windows-on-first-partition-rule)

read this thread from another forum.

here's a post from the thread:> 

said by Justakiwi See Profile :

Every dual booting article/tutorial I've ever read (and I've read a few) has always stated that Windows should be installed on the first partition. The articles have implied that it is possible to install to a different partition but that it's likely to cause major problems.
Well, those tutorials seem to be glossing over one vital difference to start with: the difference between 'Windows' and its boot loader (which is exactly the same as the difference between Linux and, say, grub).

There is absolutely positively definitely no requirement to have Windows on any particular partition (though life is probably easier if it's accessible via the INT 13 service in the BIOS, i.e., it's on some adapter known to the BIOS). The Windows installation gives you the choice of where to install Windows itself; you maybe have to choose 'custom' to get asked this question, I dunno, I always choose custom for everything.

I suppose it may be actually necessary to install the loader on the first active partition in the system, or maybe even the first partition. But I don't think that, technically, it is. The problem may well be that the standard installation doesn't ask where it should put the loader - it just slaps it down on the first active partition.

So I'd guess that installing Windows might mess up your MBR, if you do it second. But as long as you can recover from that, maybe it can be made to work. I assume that if the first active partition is not writeable by Windows Setup that nothing too bad will happen to it.

However, in my dual-boot systems, I did in fact install Windows first, and then use the Windows loader to load Linux.

(I speak here only of proper Windows, aka NT/2000/XP/2003/Vista, not that silly DOS-oriented stuff).

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)  scroll down to the section "MBRs and disk partitioning" and note : > The MBR is not located in a partition, it is located at a Main Boot Record area in front of the first partition. Windows is installed onto a partition and it's bootloader (which isn't Windows itself) is placed on the MBR. The windows bootloader is to windows what the GRUB is to Linux.  GRUB is not Linux as NTLDR is not Windows. NTLDR is not installed to a partition but rather to MBR.

---

### Post by swerdna on 2009-06-24
Following all of this I have just now been able to install windows xp on primary partition 3 (sda3), following my Ubuntu 9.04 on sda1 (root) and sda2 (swap).

During the win install the installer advised that there was another O/S and that the active flag would be shifted to accommodate windows.

Install was straightforward. 

After the install I booted Ubuntu live CD and dropped to grub prompt and issue these commands:
```
root (hd0,0)
setup (hd0)
```

Rebooted and the machine went to Ubuntu.

I added a chainloader to sda3 into the menu.lst.
Rebooted and access granted to both O/ses


So I now believe there is absolutely no requirement for xp (and probably the same for 2000) other than installing in a primary partition. Good to have that laid to rest after all these years :popcorn:


Thank you very much for your perseverance and assistance. 

And do have one on me: [IMG]http://www.swerdna.net.au/forumpics/smiley/beer.gif[/IMG]

---

### Post by presence1960 on 2009-06-24
> **swerdna said:**
> Following all of this I have just now been able to install windows xp on primary partition 3 (sda3), following my Ubuntu 9.04 on sda1 (root) and sda2 (swap).

During the win install the installer advised that there was another O/S and that the active flag would be shifted to accommodate windows.

Install was straightforward. 

After the install I booted Ubuntu live CD and dropped to grub prompt and issue these commands:
```
root (hd0,0)
setup (hd0)
```

Rebooted and the machine went to Ubuntu.

I added a chainloader to sda3 into the menu.lst.
Rebooted and access granted to both O/ses


So I now believe there is absolutely no requirement for xp (and probably the same for 2000) other than installing in a primary partition. Good to have that laid to rest after all these years :popcorn:


Thank you very much for your perseverance and assistance. 

And do have one on me: [IMG]http://www.swerdna.net.au/forumpics/smiley/beer.gif[/IMG]
Glad you got it installed without having to remove Ubuntu as some would have done. Now you know the truth, share your knowledge so it helps others.

---

### Post by ddrichardson on 2009-06-24
> **presence1960 said:**
> Glad you got it installed without having to remove Ubuntu as some would have done. Now you know the truth, share your knowledge so it helps others.
You know, I didn't *say* to remove Ubuntu first I said *I had* always installed Windows first.  Seeing as I've no machine which came with Ubuntu installed and several which had Windows pre-installed this is quite a common situation.

---

### Post by presence1960 on 2009-06-24
> **ddrichardson said:**
> You know, I didn't *say* to remove Ubuntu first I said *I had* always installed Windows first.  Seeing as I've no machine which came with Ubuntu installed and several which had Windows pre-installed this is quite a common situation.

ddrichrdson, wasn't referring specifically to you. There was also another thread going on, see here : [http://ubuntuforums.org/showthread.php?p=7501410#post7501410](http://ubuntuforums.org/showthread.php?p=7501410#post7501410)

---

