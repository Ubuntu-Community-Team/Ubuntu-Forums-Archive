---
title: "Oh,boy I screwed-up"
date: 2005-12-24
forum: Installation &amp; Upgrades
---

### Post by sonicj on 2005-12-24
I had ubuntu linux and windows xp pro installed on the same hardrive.My freind just gave me his old 4.GB harddrive so I wanted to delete ubuntu off my hard drive and put it on the one he gave me.So I went into the windows manegement console(I think thats what it's called) and deleted the partion with ubuntu linux on.The next time I restarted my computer I got this error.
"Grub loading 1.5

Grubloading please wait..
error 22.                     "

And after that the computer would stop booting .I don't get that litle box that let's me chose bettwen windows or linux. what did I do wrong?Can I fix it?

---

### Post by ardchoille on 2005-12-24
[QUOTE=sonicj]I had ubuntu linux and windows xp pro installed on the same hardrive.My freind just gave me his old 4.GB harddrive so I wanted to delete ubuntu off my hard drive and put it on the one he gave me.So I went into the windows manegement console(I think thats what it's called) and deleted the partion with ubuntu linux on.The next time I restarted my computer I got this error.
"Grub loading 1.5

Grubloading please wait..
error 22.                     "

And after that the computer would stop booting .I don't get that litle box that let's me chose bettwen windows or linux. what did I do wrong?Can I fix it?[/QUOTE]
You removed Ubuntu from your system, but you didn't change the grub boot loader. I recall that there is a way to boot into Widows "rescue mode" and restore a broken MBR (master boot record - it's on the first sector of the master drive I believe). The MBR tells the system where to look for the boot partitions and your MBR still has grub on it and grub is still looking for the partition that held Ubuntu. You need to find out how to restore the MBR using Windows.. or maybe the Windows boot disk. I haven't used Windows in years, so I am unable to help with this.

---

### Post by sonicj on 2005-12-24
I read somewhere about the MBR. I have windows xp pro So do I use that Ms-dos thing?

---

### Post by OscarGortez on 2005-12-24
hehe... sounds like something i did... cept i was all like "I don't want want ubuntu anymore" then i fucked up like that... installed windows XP in the partition where ubuntu was to see if i could get that dual boot screen back... couldn't ... oh well... anyway I talked to me friend and he convinced me to try ubuntu again... funny how that works huh?  all in all i never got the original windows OS to boot again... 

i'd say maybe you have to change something with the boot.ini or config.sys files in windows...

either that or do what i did and make a clean install...

---

### Post by ardchoille on 2005-12-24
[QUOTE=sonicj]I read somewhere about the MBR. I have windows xp pro So do I use that Ms-dos thing?[/QUOTE]
Maybe a windows forum can better help you with this?

---

### Post by ardchoille on 2005-12-24
[QUOTE=OscarGortez]hehe... sounds like something i did... cept i was all like "I don't want want ubuntu anymore" then i fucked up like that... installed windows XP in the partition where ubuntu was to see if i could get that dual boot screen back... couldn't ... oh well... anyway I talked to me friend and he convinced me to try ubuntu again... funny how that works huh?  all in all i never got the original windows OS to boot again... 

i'd say maybe you have to change something with the boot.ini or config.sys files in windows...

either that or do what i did and make a clean install...[/QUOTE]
No, no, if he installed Ubuntu, then he installed grub and grub is still there even though he removed the partition that held Ubuntu. That is why he is getting that grub error. When he sees the grub error, the windows files haven't even begun to load yet, so it has nothing to do with the windows files.

What he needs to do now is restore the MBR so it only sees/boots the partition that holds Windows.

---

### Post by sonicj on 2005-12-24
> i'd say maybe you have to change something with the boot.ini or config.sys files in windows...

I said I can't get into windows

> Maybe a windows forum can better help you with this?
The MBR only applys to windows?

---

### Post by cmcgeecc on 2005-12-24
I know exactly what you need to do.  You all are right about fixing the MBR (Master Boot Record).  Here's how you do it...

Find your windows cd and boot from it.  There should be a key at the start of the cd boot that says press ___ to boot in recovery mode (i think it's F3 but I'm not sure).  That will give you a command line.  Type fixmbr and answer yes.  That should do it.  Then just boot and you'll get into windows

---

### Post by sonicj on 2005-12-24
Allright thanx.I could not get to a computer in a 4 mile raidus beacase my computer wont boot and my internet was acting-up.I'll try that later.

BTW:Is talking about anything near windows bad on this forum?

---

### Post by ardchoille on 2005-12-24
[QUOTE=sonicj]I said I can't get into windows


The MBR only applys to windows?[/QUOTE]
No, the MBR doesn't apply to only Windows. I was thinking that a Windows forum would be the quickest and easiest way for you to learn how to use Windows to fix the MBR, though - but cmcgeecc proved me wrong.

---

### Post by sonicj on 2005-12-24
[QUOTE=ardchoille]No, the MBR doesn't apply to only Windows. I was thinking cmcgeecc proved me wrong.[/QUOTE]



"cmcgeecc"?

---

### Post by garenasix on 2005-12-26
if you got your windows disc you can fix your MBR pop in the disc click the repair option a dos like console comes up type 1 if that where your windows is on the c drive hit enter key youl get something like 
c\WINDOWS>
type in fixmbr next to that hit enter
it will ask for you admin password type it in hit enter
it will ask if you realy wanna do it type y hit enter
it will fix MBR then reboot you should get your windows back then you can install unbuntu on that other harddrive

---

### Post by sonicj on 2005-12-26
Would that work with the windows xp cd?
Would that work with the linux cd too?

---

### Post by cstudent on 2005-12-26
MBR stands for Master Boot Record. It's placed at the begining of your hard drive. To restore it you can boot up with your XP CD and go into recue mode. I can't recall exactly what things look like, but it should be fairly intuitive. The command to restore the MBR is fixmbr.

---

### Post by garenasix on 2005-12-26
[QUOTE=sonicj]Would that work with the windows xp cd?
Would that work with the linux cd too?[/QUOTE]

it el work for windows with the XP cd you uninstalled your linux already you said so no the linux disc wont work less you wanna reinstall it back on the HD then it will put grub back and you will have linux windows again

---

### Post by anil_robo on 2005-12-27
To restore MBR so that windows would boot normally after deletion of ubuntu partition, boot with a windows bootable disk (Bootable floppy or XP CD in repair mode) and type this:
```
fdisk /mbr
```

---

