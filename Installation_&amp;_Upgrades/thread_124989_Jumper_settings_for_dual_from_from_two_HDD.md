---
title: "Jumper settings for dual from from two HDD"
date: 2006-02-02
forum: Installation &amp; Upgrades
---

### Post by crhooker on 2006-02-02
I installed Ubuntu on an 80Gb disk, it owns the whole disk. I have decided that I need XP for some things so I went and got a 300Gb drive ($90 at Circuit City - what a deal!). I disconnected the Ubuntu drive, plugged in the new one, installed XP to a 50Gb partition and will format the remainder for data. I had hoped to use a boot manager program I found at sourceforge but no luck so...

I am thinking my config would be the XP disk as master and the Ubuntu as slave. I am not interested in resetting my BIOS everytime I want to boot XP.

It seems to me based on what I have read here and in other threads the quick fix might be to reinstall Ubuntu on the 80Gb drive (jumper as slave) and let GRUB write the MBR on the 300Gb disk? Of course if I can edit the GRUB file, put the Ubuntu disk as master and the XP disk as slave that would be fine too. I realize this is probably possible given the posts I have read. I have also seen posts about editing the boot.ini on the XP disk. I am just confused on what to do.

I really have read a ton of posts and know not quite enough of what to do at this point.

Thanks

carl

---

### Post by lha on 2006-02-03
[QUOTE=crhooker]I installed Ubuntu on an 80Gb disk, it owns the whole disk. I have decided that I need XP for some things so I went and got a 300Gb drive ($90 at Circuit City - what a deal!). I disconnected the Ubuntu drive, plugged in the new one, installed XP to a 50Gb partition and will format the remainder for data. I had hoped to use a boot manager program I found at sourceforge but no luck so...

I am thinking my config would be the XP disk as master and the Ubuntu as slave. I am not interested in resetting my BIOS everytime I want to boot XP.

It seems to me based on what I have read here and in other threads the quick fix might be to reinstall Ubuntu on the 80Gb drive (jumper as slave) and let GRUB write the MBR on the 300Gb disk? Of course if I can edit the GRUB file, put the Ubuntu disk as master and the XP disk as slave that would be fine too. I realize this is probably possible given the posts I have read. I have also seen posts about editing the boot.ini on the XP disk. I am just confused on what to do.

I really have read a ton of posts and know not quite enough of what to do at this point.

Thanks

carl[/QUOTE]

You're easiest off if you make Windows drive slave and Ubuntu drive master. Then open terminal (Applications->Accessories->Terminal) and type
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst
```
and paste the following lines in the very end of that file.
```
title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

Those other method need a more tweaking than this and are more susceptible to errors.

---

### Post by kgee on 2006-02-03
[QUOTE=lha]
and paste the following lines in the very end of that file.
```
title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

Those other method need a more tweaking than this and are more susceptible to errors.[/QUOTE]

Ok, so I was having nearly the exact same problem. Got my dual OS installed on two harddrives, but couldnt get winblows to load. I used this code exactly and it works. I even set my windows harddrive to a slave.

The only problem is that the bootloader throws an error before loading windows. I'm not one to complain when something works, especially if I understand how the process worked, but I'd like to get rid of the error. after the grub menu comes up and i choose windows, this pops up for about 20 seconds before it continues booting:

```

Booting Winblows
root 		(hd1,0)
File system type unknown, partition type 0X7
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

I can assume that most of what is here (except for the error line) is copied directly out of /boot/grub/menu.lst so i copied and pasted it exactly as i had written it into the file.

any suggestions? comments? words of wisdom?

Edit:

p.s. windows is on an 80 gig maxtor hard drive with an NTFS file system

---

### Post by lha on 2006-02-04
[QUOTE=kgee]Ok, so I was having nearly the exact same problem. Got my dual OS installed on two harddrives, but couldnt get winblows to load. I used this code exactly and it works. I even set my windows harddrive to a slave.

The only problem is that the bootloader throws an error before loading windows. I'm not one to complain when something works, especially if I understand how the process worked, but I'd like to get rid of the error. after the grub menu comes up and i choose windows, this pops up for about 20 seconds before it continues booting:

```

Booting Winblows
root 		(hd1,0)
File system type unknown, partition type 0X7
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

I can assume that most of what is here (except for the error line) is copied directly out of /boot/grub/menu.lst so i copied and pasted it exactly as i had written it into the file.

any suggestions? comments? words of wisdom?

Edit:

p.s. windows is on an 80 gig maxtor hard drive with an NTFS file system[/QUOTE]
Try if replacing 'root' with 'rootnoverify' removes that error.

---

### Post by kgee on 2006-02-04
[QUOTE=lha]Try if replacing 'root' with 'rootnoverify' removes that error.[/QUOTE]

it worked, no error line :)

thank you!

---

### Post by crhooker on 2006-02-05
lha,

thanks for the info. I will try it as soon as I resolve the latest and greatest issue now. My sound stopped the other day, replaced the motherboard and now get what looks like a BIOS error and am having difficulty (of course) getting the latest BIOS from the MB website.

Funny thing, if my XP disk is master I still see the error but it boots anyway, Ubuntu when it is the master (had not added your suggestions yet) fails to boot, I get:

Alert /dev/hdc1 does not exist. Dropping to a shell
/bin/sh: can't access tty; job control turned off
#

Not knowing what I was really doing I interupted GRUB on the next boot and tried the other boot options, but same message. I am going to search and see if this error is as a result of the BIOS issue, let's hope?!

Meanwhile burning live cd so I can at least go in and recover my stuff and maybe work on it as well, had backup but of course not yesterday so a few emails could get lost, oh well.

Thanks again for the dual boot tip.

carl

---

### Post by crhooker on 2006-02-05
Found a thread that discussed my boot issue, edited the GRUB file to correct the disk address issue and all is well. Ubuntu runnning and all is well.

thanks again.

carl

---

### Post by nicklogan on 2006-02-05
I'm having the exact same problem, would you please point me to that thread?
Thanks in advance.

---

### Post by crhooker on 2006-02-06
[QUOTE=nicklogan]I'm having the exact same problem, would you please point me to that thread?
Thanks in advance.[/QUOTE]

I hope this is how you do this, see the last post to edit grub on bootup

[http://www.ubuntuforums.org/search.php?searchid=3689431](http://www.ubuntuforums.org/search.php?searchid=3689431)

carl

---

### Post by confused57 on 2006-02-16
Being the ultimate noobie, I'm not sure where to paste the lines that lha provided into menu.lst.  I have 2 hd, windows xp slave and ubuntu master.
Kept getting error after pasting the lines after the 4th line in menu.lst & couldn't boot into windows.  I ended up copying and pasting the lines after:
## ##End Default Options## into menu.lst and now the only way I'm able to
boot either drive OS is to hit "Esc" to access the Grub menu.  Then I can select
which drive OS I want to boot(my antivirus didn't like it in windows, the real-time protection was disabled).

My question is exactly where in the menu.lst do I paste the lines:

title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

---

### Post by Sutekh on 2006-02-16
**confused57** you would probably be better off pasting those lines for Windows XP after this line in GRUB's menu.lst
```
### END DEBIAN AUTOMAGIC KERNELS LIST
```
Its near the end of the file.  Otherwise when an update occurs, the entry may get written over.  If you place the lines at the end they won't be modified.

---

### Post by lha on 2006-02-16
[QUOTE=confused57]Being the ultimate noobie, I'm not sure where to paste the lines that lha provided into menu.lst.  I have 2 hd, windows xp slave and ubuntu master.
Kept getting error after pasting the lines after the 4th line in menu.lst & couldn't boot into windows.  I ended up copying and pasting the lines after:
## ##End Default Options## into menu.lst and now the only way I'm able to
boot either drive OS is to hit "Esc" to access the Grub menu.  Then I can select
which drive OS I want to boot(my antivirus didn't like it in windows, the real-time protection was disabled).

My question is exactly where in the menu.lst do I paste the lines:

title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1[/QUOTE]
Those lines should be added to the end of menu.lst, after 
```
### END DEBIAN AUTOMAGIC KERNELS LIST
```
(If you want, you can add them above line
### BEGIN AUTOMAGIC KERNELS LIST
instead of the former.)

To make grub menu always visible (to get rid of pressing esc), find line
```
hiddenmenu
``` and replace it with
```
#hiddenmenu
```

---

### Post by confused57 on 2006-02-16
Thanks for the quick reply, it worked.  Sorry to be a pest, but how do I increase the time to make a selection of which HD OS I want to load?

---

### Post by confused57 on 2006-02-16
I found the thread for extending the time, changed the timeout from 3 seconds
to 10 seconds.  I think I can make a selection in a whole 10 seconds.

---

### Post by oliwally on 2006-06-07
Well done folks this all worked flawlessly on my system. It's the easiest thread to dual booting on 2 hds without disturbing the MBR I've read so far. 

Just fantastic!

---

### Post by bungaknotty on 2006-08-29
Hi I am tryin to dual boot just as you described here but for some reason when I try to boot the windows partition i get the error message, no disk found.  My windows hard drive (IDE) is NTFS and set as slave. can anyone help me

---

### Post by confused57 on 2006-08-29
> **bungaknotty said:**
> Hi I am tryin to dual boot just as you described here but for some reason when I try to boot the windows partition i get the error message, no disk found.  My windows hard drive (IDE) is NTFS and set as slave. can anyone help me

Check out this thread:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

Make sure your hard drive jumper pins are set to slave or cable select.

---

### Post by lha on 2006-08-29
> **bungaknotty said:**
> Hi I am tryin to dual boot just as you described here but for some reason when I try to boot the windows partition i get the error message, no disk found.  My windows hard drive (IDE) is NTFS and set as slave. can anyone help me

Can you access your Windows drive from Ubuntu? Does it show up in
```
sudo fdisk -l
```
or in System->Administration->Disks? If not, you should recheck your bios settings and hd jumpers.

---

### Post by bungaknotty on 2006-08-29
yes my hard drive shows up fine in ubuntu.  the jumper setting for Ubunbtu are set to master and windows set to slave.  I installed using the live cd and the installatio went smooth.  I editted the file just as u said but it would recognize my harddrive when I select windows.  Any ideas?

---

### Post by confused57 on 2006-08-29
> **bungaknotty said:**
> yes my hard drive shows up fine in ubuntu.  the jumper setting for Ubunbtu are set to master and windows set to slave.  I installed using the live cd and the installatio went smooth.  I editted the file just as u said but it would recognize my harddrive when I select windows.  Any ideas?

Please post the output of the command lha suggested:
```
sudo fdisk -l
```
The -l is a small "L"

Hopefully, that might tell us what's going on?

---

### Post by acorn22 on 2006-08-30
Is there any way to make it so after the timeout it automatically goes into windows instead?

-and-

After I get this all working, could I install [this]("http://www.ubuntuforums.org/showthread.php?t=208855") without ruining everything (in theory, of course)
What i mean is is that tutorial still applicable to GRUB when ts installed this way?

---

### Post by lha on 2006-08-31
Open menu.lst and find lines
```
title Windows ...
.
.
chainloader +1
``` and cut them. Paste between
```
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
``` and
[CODE]### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below[\CODE]

BTW, it's a good idea to make a backup of menu.lst before you make any modifications in it.

---

### Post by acorn22 on 2006-08-31
Ok I'm assumig that last post by lha was for me, right? ( Only the first half of my question.)

And to clarify,  I take the two lines only, or everything in between?

Sorry to be such a bother but I am pretty new to this.

---

### Post by confused57 on 2006-08-31
> **acorn22 said:**
> Ok I'm assumig that last post by lha was for me, right? ( Only the first half of my question.)

And to clarify,  I take the two lines only, or everything in between?

Sorry to be such a bother but I am pretty new to this.


You'd need to cut & paste your entire(not just the 2 lines) menu.lst Windows entry to where lha indicated.

---

### Post by acorn22 on 2006-09-01
Thank you so much :) I will re-boot now and test it.

ps- Is it ok that I titled the new entery "Windows XP" (not just Windows)

---

### Post by confused57 on 2006-09-02
> **acorn22 said:**
> Thank you so much :) I will re-boot now and test it.

ps- Is it ok that I titled the new entery "Windows XP" (not just Windows)

You can actually put whatever title you want, e.g. "My Windows XP", or whatever you wish...

---

### Post by acorn22 on 2006-09-02
Ok Everything works great :D

I should be happy it works I suppose but I would still like to know if there is a way to hide the other options. Like memtest and all that so all you see is XP and Ubuntu.

---

### Post by lha on 2006-09-03
> **acorn22 said:**
> Ok Everything works great :D

I should be happy it works I suppose but I would still like to know if there is a way to hide the other options. Like memtest and all that so all you see is XP and Ubuntu.

Find lines
```
# howmany=all
```
and
```
# memtest86=true
```
Replace them with
```
# howmany=2
```
and
```
# memtest86=false
```
This will make grub show manually entered boot options (Windows), two latest kernels for Ubuntu (in case your kernel upgrade goes bad) and recovery options for both kernels (if you ever forget your password).

You could even go as far as
```
# howmany=1
```
and replace
```
# alternative=true
```
with
```
# alternative=false
```
but don't recommend this. Some problems are easier to solve if you are able to fall back to an older kernel or boot your computer in recovery mode. Yes, you can boot in recovery mode and your older kernels even if they don't show up in grub. You just have to manually type the commands needed.

Instead of changing the value of howmany, you can remove older kernels when you are certain that the newest kernel works for you. (This might be better idea than setting howmany=1)

Apply changes by running
```
sudo update-grub
```

BTW, these lines aren't necessarily needed:
```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root
```

---

### Post by chrstphrtlbt on 2007-02-24
i have a big problem!

i got to add the Windows boot to GRUB, but when it does load it says "NTDLR is missing" and i have to restart. do i now have to reload windows files, or is the hard drive gonna have to be wiped. i'm very very worried. the xp drive has all of my work on it, ever. i've barely backed up because there's so much. i wanted to try ubuntu on the seperate hard drive to see what it was like, and it's caused nothing but trouble. i've now had to use ubuntu for the past 3 days, without access to my work on the xp drive. could anyone please help me?!

ubuntu is set up on the master 80gb drive, and xp is on the slave 250gb drive.

---

### Post by confused57 on 2007-02-24
> **chrstphrtlbt said:**
> i have a big problem!

i got to add the Windows boot to GRUB, but when it does load it says "NTDLR is missing" and i have to restart. do i now have to reload windows files, or is the hard drive gonna have to be wiped. i'm very very worried. the xp drive has all of my work on it, ever. i've barely backed up because there's so much. i wanted to try ubuntu on the seperate hard drive to see what it was like, and it's caused nothing but trouble. i've now had to use ubuntu for the past 3 days, without access to my work on the xp drive. could anyone please help me?!

ubuntu is set up on the master 80gb drive, and xp is on the slave 250gb drive.

Make sure your jumper settings are correct on your slave drive, all connections to the drive are properly installed & that your bios properly detects your slave drive...these are the obvious things to look for first...probably not the problem, but just wanted to mentioned if you haven't checked these possiblities first.

I guess you can't boot your Windows drive when you select your slave drive to boot first in bios?  If this is the case you may indeed need to repair the NTLDR:
[http://www.ubuntuforums.org/showpost.php?p=2203511&postcount=4](http://www.ubuntuforums.org/showpost.php?p=2203511&postcount=4)
you might need to temporarily connect your Windows drive as master, if you attempt repairing NTLDR...another way is to boot up a Windows install cd(not a recovery cd), press "r" for recovery, then FIXMBR to repair the mbr, then the command FIXBOOT will repair the Windows boot sector, see this thread:
[http://www.ubuntuforums.org/showpost.php?p=2204826&postcount=2](http://www.ubuntuforums.org/showpost.php?p=2204826&postcount=2)


Before you attempt to actually repair the NTLDR, you might want to open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
the -l is a small "L"
 
and 

```
cat /boot/grub/menu.lst
```
menu.lst is short for menu.list

Please post your entries to boot Ubuntu & Windows,  also, describe a little more how you installed Ubuntu, i.e. drives connected the way they are or did you switch drive positions after installing, boot order in bios, or anything else you can think of that might help.

With lha's permission, I summarized and wrote a "howto" from this thread:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

Also, here's an excellent tutorial for repairing Windows mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

You might want to burn a copy of the Super Grub Disk(500 kb download):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
the Super Grub Disk can boot Windows or Linux, as well as repair mbr of either.

---

### Post by NJC on 2007-03-07
> **lha said:**
> ```
title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```



lha;

Thanks! This worked flawlessly to dual boot between Win98 and Ubuntu 6.06. I'm happy to not have to touch Windoze MBR too. 

Prior to this I had both drives jumpered as Cable Select and would go into BIOS and switch boot order to which OS I wanted to start ... so this is A LOT faster. :cool:

---

### Post by pete stahl on 2007-03-13
> **lha said:**
> You're easiest off if you make Windows drive slave and Ubuntu drive master. Then open terminal (Applications->Accessories->Terminal) and type
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst
```
and paste the following lines in the very end of that file.
```
title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

One more thing, when I type the line sudo gedit menu.lst before I can get into gedit it asks for my password, is this normal
Those other method need a more tweaking than this and are more susceptible to errors.

I'm extremely new and a little dense to understanding how to get around in ubuntu. I did get the code typed in as I can't access the internet from ubuntu yet. Need to put the ethernet card in and take the wireless one out but that's another problem. I'm assuming the "0" in the code are zero's and all the "1" are number ones. When I boot my computer I see a very brief menu, and I mean brief and tried holding the number 1 down but it still boot the Primary ubuntu drive. Should this menu stay there? did I do something wrong? Both drive are jumpered to cable select. I does see both drive even though I don't know how to access files on the Windows drives yet, still working on that too. Guess I need a copy of ubuntu/Linux for morons. Thanks a lot for any help!

---

### Post by confused57 on 2007-03-13
Here's the lowdown:
menu.lst is short for menu.list
(hd1,0) is (hd-one,zero)
chainloader +one

Put a comment(#) in front of hiddenmenu(in /boot/grub/menu.lst) in order to see the grub menu at startup:
```
#hiddenmenu
```

Change your timeout to something like 10 seconds:
```
timeout 10
```

That should cover what you need to know, I had the same questions when I was a beginner.

You have to mount a partition in order to be able to access it from Linux:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
or
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

You can read an NFTS filesystem in Ubuntu, but not write to it...there is a program, which allows Linux to write to NTFS but it is experimental...some say it works OK for them.

---

### Post by pete stahl on 2007-03-13
Thanks for the quick response. The 2 extra lines help a lot. Able to dual boot now. Went by so fast before I could get to read the whole thing. Will try mounting the disk later, I'll let you know how that turns out. Seems like ubuntu/Linux is like a combo between Windows and DOS, has a like of windows stuff but you still need to enter code in manually.

---

### Post by confused57 on 2007-03-13
> **pete stahl said:**
> Thanks for the quick response. The 2 extra lines help a lot. Able to dual boot now. Went by so fast before I could get to read the whole thing. Will try mounting the disk later, I'll let you know how that turns out. Seems like ubuntu/Linux is like a combo between Windows and DOS, has a like of windows stuff but you still need to enter code in manually.
I used this thread to get my first dual boot setup over a year ago, so I'm familiar with setting up a system this way.  lha said he had no problem with my summarizing the info in this thread:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

Once you get your system setup and configured, you shouldn't need to use the terminal much...it's really pretty easy once you learn a few basic commands & configuration files, you'll eventually find the terminal easier than using the GUI.  I do remember using  DOS  6.2 back in my Win3.1 days...you can do much more with Linux "command line" than you could do in DOS.

People here in the forum are friendly and willing to help, so feel free to ask any questions, as they arise.   Linux & Ubuntu have been a challenge for me, but it's fun & I've learned a lot about OS & computers.  Welcome to the community.

Added:  There's some excellent info & links in this thread to help get you started:
[http://www.ubuntuforums.org/showthread.php?t=142716](http://www.ubuntuforums.org/showthread.php?t=142716)

---

### Post by phi1ip on 2007-04-23
> **lha said:**
> You're easiest off if you make Windows drive slave and Ubuntu drive master. Then open terminal (Applications->Accessories->Terminal) and type
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst
```
and paste the following lines in the very end of that file.
```
title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

Those other method need a more tweaking than this and are more susceptible to errors.


Your method seems to infer GRUB was already installed as you are editing the grub menu. 
When you install Ubuntu onto a new hard disk does Grub get installed even if there was no windows?

 I always have dual boot with windows on the same hard disk and cannot remember. 

I am helping someone install Ubuntu tonight, they have Ubuntu on the master hard disk, windows on the slave hard disk that was disconnected during ubuntu installation. But now they want access to windows if necessary. Is the above steps all that is necessary or do i need to install GRUB first? This could be a really dumb question if it was already installed, but do i need to know how to do this before i get there? if so then how? or is the above enough.....

---

### Post by lha on 2007-04-23
> **phi1ip said:**
> Your method seems to infer GRUB was already installed as you are editing the grub menu. 
When you install Ubuntu onto a new hard disk does Grub get installed even if there was no windows?

Yes, grub does get installed even without Windows. (It is possible to use other boot managers, but since the person who installed Ubuntu needs help with dual-booting, I doubt he/she doesn't know how to install Ubuntu without grub.)

---

### Post by Maxxxus on 2007-05-30
HELP!!!!  Noob here ! 

I tried to follow: 

cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst

After the last comand, I get " cannot open display: (null)

---

### Post by JATMartin on 2007-07-24
Thanks! This thread worked for me.

---

### Post by wolf510 on 2007-08-02
Greetings everyone. So I have tried doing exactly what this post says to duel boot my system. I have both of my harddrives set to cable select with Ubuntu being master and WIN XP being slave.
I also pasted this: 
         title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


at the end of menu.lst using these commands:
d /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst

When my comp boots it loads everything then emediatly loads XP as the os. The only way I am able to get into UBUNTU is if I hold down my boot menu key and tell it to boot from the master HD.
Anyone know why XP is taking over even though my bios says it is the slave drive and how do I fix it so I get some sort of menu that I can duel boot from.
Thanks for the help.

---

### Post by lha on 2007-08-07
> **wolf510 said:**
> 
When my comp boots it loads everything then emediatly loads XP as the os. The only way I am able to get into UBUNTU is if I hold down my boot menu key and tell it to boot from the master HD.
Anyone know why XP is taking over even though my bios says it is the slave drive and how do I fix it so I get some sort of menu that I can duel boot from.


Sounds like your bios is set to boot from the slave drive. :) Make sure that the master drive is set as the first boot device. (Or atleast has higher priority than the slave drive...) [Here's some examples on setting the priorities.]("http://www.hiren.info/pages/bios-boot-cdrom")

---

### Post by wolf510 on 2007-08-09
Thanks buddy. You were right. Now it boots directly into Ubuntu but does not give me the option to boot into XP. Is there some sort of screen where I can make a choice or do I only get control over duel-booting through my bios?

---

### Post by lha on 2007-08-09
> **wolf510 said:**
> Thanks buddy. You were right. Now it boots directly into Ubuntu but does not give me the option to boot into XP. Is there some sort of screen where I can make a choice or do I only get control over duel-booting through my bios?

You can add Windows into grub's menu. See the second post in this thread. Comment out the line (add a # in front of the line)
```
hiddenmenu
```
Then you will see a boot menu when you boot your computer. There's also a
```
timeout         3
```
line. The number tells grub how long it should show the boot menu before booting the default os.

---

### Post by wolf510 on 2007-08-09
Great Thanks man!!
Works like a charm. Thanks again

---

### Post by wolf510 on 2007-08-13
Ok so now I have a new problem. When I try booting into XP the windows XP splash screen comes up and then All I see is a black screen and my pointer. The log in menu never appears. The same thing still happens when I set XP to master and completely remove the Ubuntu hard drive. I can access my XP drive from within windows but need to get to it so I can run some of the programs I have there. Any ideas what I broke?

---

### Post by lha on 2007-08-17
> **wolf510 said:**
> Ok so now I have a new problem. When I try booting into XP the windows XP splash screen comes up and then All I see is a black screen and my pointer. The log in menu never appears. The same thing still happens when I set XP to master and completely remove the Ubuntu hard drive. I can access my XP drive from within windows but need to get to it so I can run some of the programs I have there. Any ideas what I broke?

Since this is a Windows XP issue, there's not much I can do to help you. Windows cd has some sort of boot sector repair or recovery option. Try if it fixes your problem. Remember to unplug your Ubuntu drive before you use the recovery or your Ubuntu will get messed up, too.

---

### Post by wolf510 on 2007-08-17
I tried it but it brought up a command prompt and I have no idea what to type there to fix the problem.

---

### Post by liligwna on 2007-08-24
Hi, I went to terminal and typed as directed cd/boot/grub, pressed enter and it says "no such file" - what did I not do?  Please reply I am stuck in the middle of this process now, Thanks

---

### Post by confused57 on 2007-08-24
> **liligwna said:**
> Hi, I went to terminal and typed as directed cd/boot/grub, pressed enter and it says "no such file" - what did I not do?  Please reply I am stuck in the middle of this process now, Thanks
It would probably be best to copy & paste the commands into a terminal, that way you don't have to worry about spacing, upper or lower case, "L" or "one", etc.

---

### Post by liligwna on 2007-08-24
Thanks, I pasted the commands and this is what I got:


moe@home:~$ cd /boot/grub
moe@home:/boot/grub$ sudo cp menu.lst menu.lst_backup                         <ENTER>

Password:                                                                                                 <mypassword then ENTER>

moe@home:/boot/grub$ title           Windows
bash: title: command not found
moe@home:/boot/grub$ root            (hd1,0)
bash: syntax error near unexpected token `hd1,0'
moe@home:/boot/grub$ savedefault
bash: savedefault: command not found
moe@home:/boot/grub$ makeactive
bash: makeactive: command not found
moe@home:/boot/grub$ map             (hd0) (hd1)
bash: syntax error near unexpected token `hd0'
moe@home:/boot/grub$ map             (hd1) (hd0)
bash: syntax error near unexpected token `hd1'
moe@home:/boot/grub$ chainloader     +1

Do you know what this stuff means?

Thanks for your response!

---

### Post by confused57 on 2007-08-24
> **liligwna said:**
> Thanks, I pasted the commands and this is what I got:


moe@home:~$ cd /boot/grub
moe@home:/boot/grub$ sudo cp menu.lst menu.lst_backup                         <ENTER>

Password:                                                                                                 <mypassword then ENTER>

moe@home:/boot/grub$ title           Windows
bash: title: command not found
moe@home:/boot/grub$ root            (hd1,0)
bash: syntax error near unexpected token `hd1,0'
moe@home:/boot/grub$ savedefault
bash: savedefault: command not found
moe@home:/boot/grub$ makeactive
bash: makeactive: command not found
moe@home:/boot/grub$ map             (hd0) (hd1)
bash: syntax error near unexpected token `hd0'
moe@home:/boot/grub$ map             (hd1) (hd0)
bash: syntax error near unexpected token `hd1'
moe@home:/boot/grub$ chainloader     +1

Do you know what this stuff means?

Thanks for your response!

The Windows entry should be copied in it's entirety to the very end of your menu.lst file...to access your menu.lst:
```
cd /boot/grub
gksudo gedit menu.lst
```

I've written a summary of lha's instructions in this thread:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by liligwna on 2007-08-27
It just gets more fun!  I kinda have a sick love for troubleshooting.  Anyway I made the changes in grub and windows shows as a boot option.  I tried to boot to windows and get this"Error 13: Invalid or unsupported executable format"
Then I did sudo fdisk -l and the partition info looks like this:

Disk /dev/hda: 13.5 GB, 13578485760 bytes
255 heads, 63 sectors/track, 1650 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1575    12651156   83  Linux
/dev/hda2            1576        1650      602437+   5  Extended
/dev/hda5            1576        1650      602406   82  Linux swap / Solaris

Disk /dev/hdb: 15.3 GB, 15371919360 bytes
255 heads, 63 sectors/track, 1868 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1868    15004678+  83  Linux

Where did my fat32 partitioned windows HDD go?  Its all changed - HELP!

---

### Post by liligwna on 2007-08-28
HELLLOO. . . IS ANYBODY OUT THERE?  Can somebody help me with this? (see last post)

---

### Post by confused57 on 2007-08-29
> ...I tried to boot to windows and get this"Error 13: Invalid or unsupported executable format"...
Please copy & paste the actual Window's entry from your /boot/grub/menu.lst...this error usually occurs if spacing is incorrect or something is entered incorrectly.

If you only have 2 hard drives, it's obvious that "fdisk -l" doesn't show a FAT partition; however, you might want to boot the Feisty live cd and see how Gnome Partition Editor sees your partitions.

Also, from the live cd or from your Ubuntu install, try mounting /dev/hdb1...or if it is automatically mounted in your installed Ubuntu, you might want to see what the contents of the partition are.

To mount the partition, open a terminal(Applications---Accessories---Terminal), enter(copy & paste):
```
sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
```
if /dev/sdb1 mounts with ext3 in the command, then the filesystem is ext3 & it "appears" that your FAT partition may be lost.  If it mounts, you can open Nautilus, open the media directory & see what files are listed.  Hopefully, Gnome Partition Editor will show it as a FAT32 partition.

You "might" be able to recover data, using testdisk:
[http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)
I haven't personally used testdisk, so I can't really offer any advice on how to do so...good luck with it.

---

### Post by ronjan41 on 2007-11-23
[SIZE="4"]I have the same set up but cannot save the changes to ,menu.1st as I don't have permission. It is read only. How do I save it?[/SIZE]

---

### Post by meierfra on 2007-11-24
Open a terminal (Applications->Accessories->Terminal) and type

```
gksudo gedit /boot/grub/menu.lst
```

This will open "menu.lst" with "read and write" permission

---

### Post by KuroYoma on 2008-06-18
Ok guys i have a big problem that has caused me all sorts of grief.

I had windows xp on my dell laptop. I used Casper 5.0 to copy my c partition to the f partition on my external hd.  Then i inserted a new internal hd (so i still have the xp one) and i have ubuntu on it. i have modified the menu.lst file so that wnds xp was added, when i boot up it crashes.  I changed root to rootnoverify, reboot and get "Error 12: Invalid device request."  Through grub's edit option i changed rootnoverify to root and it loaded WndXP splash screen for a split second and then a Blue Screen of Death Flashes and then instant reboot. When i change rootnoverify to root permanetly in the OS and then reboot i get "Error 5: Partition table invalid or corrupt."  Also nothing worked until i changed 

title Windows XP
rootnoverify (hd1,**[COLOR="Red"]1[/COLOR]**)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
remember the wndsXP partition is the SECOND PARTITION on the extHD.
When i boot directly from the external HD through the bios boot list nothing happens.

So menu.lst is
title              Windows XP
root               (hd1,1)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

and the fdisk -l is...
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00096851

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf87b4c9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       44619   358402086    7  HPFS/NTFS
/dev/sdb2   *       44620       49473    38989755    6  FAT16
/dev/sdb3           49474       60801    90992160    7  HPFS/NTFS


and thats another problem.  the FAT16 should be NTFS but as soon as i boot ubuntu it reads it as FAT16.

PLZ HELP ME

---

