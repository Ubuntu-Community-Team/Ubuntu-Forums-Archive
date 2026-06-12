---
title: "[SOLVED] Help, Wubi stops at grub prompt..."
date: 2008-10-26
forum: General Help
---

### Post by omittones on 2008-10-26
I tried to install Wubi 8.04 on my Asus A6JC laptop. I have WinXP installed on C: partition, and I want to install Wubi on D: After the first reboot, it stops at grub> prompt and doesn't want to continue.

---

### Post by Orlsend on 2008-10-27
Maybe in reality it dint stop and it rather going real slow.

Try defragmenting the forlders or the hardive where the wubi files are.

---

### Post by omittones on 2008-10-27
> **Orlsend said:**
> Maybe in reality it dint stop and it rather going real slow.

Try defragmenting the forlders or the hardive where the wubi files are.

I don't think that would help. When I boot, i get grub> prompt. And I can type in it. When I press ESC I get this menu:

find /ubuntu/disks/boot/grub/menu.lst
find /ubuntu/install/boot/grub/menu.lst
find /menu.lst
find /boot/grub/menu.lst
find /grub/menu.lst
commandline
reboot
halt

I tried all of the find entries, but nothing happens.
I'll try to defrag now, it will take a while...

---

### Post by ago on 2008-10-27
Use wubi 8.10 [http://wubi-installer.org/devel/minefield](http://wubi-installer.org/devel/minefield)

It might be that your hard disk is not "visible" at boot time.

---

### Post by omittones on 2008-10-27
> **ago said:**
> Use wubi 8.10 [http://wubi-installer.org/devel/minefield](http://wubi-installer.org/devel/minefield)

It might be that your hard disk is not "visible" at boot time.

Disk IS visible, atleast the C: partition is. When I try to find *menu.lst* manualy with *config* directive, path autocompletion works, but I can only browse C: partition.

I tried 8.10 first, but it stoped even before it got to grub (cmain()...Opening default...Failed problem). I then tried with 8.04, and that's what I'm doing now :)

I ran chkdsk on my D: drive, and it found no problems. I'm defraging now, so I'll check back when it's done.

---

### Post by ago on 2008-10-27
> **omittones said:**
> Disk IS visible, atleast the C: partition is. When I try to find *menu.lst* manualy with *config* directive, path autocompletion works, but I can only browse C: partition.

Well if you installed on D: and cannot browse D: from grub console it means that the drive is not accessible. You can try newer grub4dos builds. See also the sticky post on grub.

---

### Post by omittones on 2008-10-28
> **ago said:**
> Well if you installed on D: and cannot browse D: from grub console it means that the drive is not accessible. You can try newer grub4dos builds. See also the sticky post on grub.
You're right, I defraged C: and D: with JkDefrag and now I can access only some of dirs, and when I can't Error 18 pops out (Inconsistent file system).
I read the sticky (hyperlinks don't work, site has moved) and I can't find fstest.exe anywhere on the new site. I PMed bean123 for help on finding fstest.
As for upgrading grldr, I assume wubildr is in fact grub4dos loader, so I downloaded grub4dos 0.4.4 (from [http://download.gna.org/grub4dos/](http://download.gna.org/grub4dos/)) and copied grldr and grldr.mbr over wubildr and wubildr.mbr on my C: and D: partition. Now, however, I receive "Cannot find grldr in all drives".

BTW, thanks for putting up with me, I'm not about to give up yet, I really need this to work :)

---

### Post by ago on 2008-10-28
If you use the new grub4dos the instructions are the following:

1) extract grldr and grldr.mbr onto C:\ (do not rename them)
2) change your bootloader (boot.ini for XP) to point to grldr.mbr as opposed to wubildr.mbr
3) copy c:\ubuntu\winboot\menu.lst to C:\

---

### Post by ago on 2008-10-28
Here you find the latest version [http://nufans.net/grub4dos/](http://nufans.net/grub4dos/)

---

### Post by omittones on 2008-10-28
Oh yeah, progress has been made \\:D/

But now, I get installation menu, and when I choose Normal, screen goes black, and the only visible thing is blinking underscore. I tried to select Verbose, same thing.
I think this isn't supposed to be normal, because the HDD led isn't blinking, so that means no disk activity, right?
Should I wait more?

Edit: I left it to blink for 30 mins, and nothing...

---

### Post by ago on 2008-10-28
try safe graphic mode

---

### Post by omittones on 2008-10-28
Awesome, I'm writing this from my new Wubi installation :)
I had to uninstall ubuntu from D:, install it on C:, defrag it with JkDefrag, and finaly select "Install in safe graphic mode", and that did the trick.
Thanks!

---

### Post by ferraz75 on 2010-03-31
I have exactly the same problem commented here ("Starting cmain()" stuff)

I've tried to follow the instructions but as I have Vista on my laptop, I'm having problems with 2). I've searched on the net and finally I found that there's no boot.ini here. 

> **ago said:**
> If you use the new grub4dos the instructions are the following:

1) extract grldr and grldr.mbr onto C:\ (do not rename them)
2) change your bootloader (boot.ini for XP) to point to grldr.mbr as opposed to wubildr.mbr
3) copy c:\ubuntu\winboot\menu.lst to C:\

Instead of that there's something called BCD files. In the microsoft's webpage they say to write bcdedit with the commandline ('cmd'), but it only says information:
```

Sector de arranque del modo real
---------------------------------
Identificador                      {6a023....}
device                             partition=C:
path                               \ubuntu\winboot\wubidlr.mbr
description                        Ubuntu

```
This is only the part referring to ubuntu


At this point I've tried to rename wubildr as grldr, wubildr.mbr as grldr.mbr and all the possible combinations but I've only achieved more problems.

Thanks in advance


Ferraz75

---

### Post by ferraz75 on 2010-03-31
Update: I've burned a livecd in order to attemp saving some important files. But I cannot find them. 

Any suggestion?

Update 2: I've replaced the wubildr file in c:/, trying to follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=798283&highlight=no+wubildr&page=4"), but it seems that I don't have kernel. Is it possible? I've no 'vmlinuz-...' like file at boot/
What can I do?

Thnx!

---

### Post by wmalik on 2010-11-23
> **ferraz75 said:**
> Update: I've burned a livecd in order to attemp saving some important files. But I cannot find them. 

Any suggestion?

Update 2: I've replaced the wubildr file in c:/, trying to follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=798283&highlight=no+wubildr&page=4"), but it seems that I don't have kernel. Is it possible? I've no 'vmlinuz-...' like file at boot/
What can I do?

Thnx!
Did you manage to find a solution to your issue? Because I have the exact same issue.

---

### Post by bcbc on 2010-11-23
> **wmalik said:**
> Did you manage to find a solution to your issue? Because I have the exact same issue.

You should create a new thread and explain more details.

If you upgraded from 10.04 to 10.10, then copy the c:\ubuntu\winboot\wubildr over c:\wubildr.

If you need to recover data try [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/) (point it at the \ubuntu\disks\root.disk file)

---

