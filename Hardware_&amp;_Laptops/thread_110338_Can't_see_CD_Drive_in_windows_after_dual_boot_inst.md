---
title: "Can't see CD Drive in windows after dual boot install of ubuntu"
date: 2005-12-30
forum: Hardware &amp; Laptops
---

### Post by PDXlewis on 2005-12-30
Hello,
   This might be a obvious issue, forgive my newbieness. I am a huge fan of the ubuntu (a non-grumpy newbie) and have finally had a chance to get a second harddrive to dual boot ubuntu with windows xp. I have my master drive as ubuntu 5.10 (80gb) and a secondary with my old install of xp (20gb). All is going pretty dang well. I can boot to either OS and everything works great in ubuntu (even stuff I thought might be a problem). However, when I go back to windows I can't see my cd/dvd drives. I have a cd rewrite drive and a dvd rom drive. I see them in ubuntu.

I saw something on this in the forum earlier but haven't found it yet. 

A side note on this is that I would like reload my windows OS. Can't  do that without the cd drive to read from.

---

### Post by audax321 on 2005-12-30
You say you have Windows on a secondary drive and from my experience maybe this is causing the problem.  I've heard Windows likes to install itself as primary master, first partition (hda1).  I had a setup similar to yours, but what happened to me was that one time I was using Windows and the OS locked up. Then whenever I booted into Windows or Linux my sound card refused to be recognized. A few weeks ago I got a new hard drive so I formatted everything and set it all up again with Windows installed on hda1 and Linux on hdb and I haven't had the problem since. Try booting off the xp drive with it plugged in as primary master. If the CD drives start working all of a sudden, the problem might be related to this.

---

### Post by abovett on 2005-12-30
Hi

I suspect that by moving your Windows drive from Master to Secondary you've confused Windows (easy to do!) about what devices are where. This is really a Windows problem not a Ubuntu one, but I'll try to help.

1. Did you move the CD/DVD drives or are they still connected to the same IDE bus?

2. Can you see the CD/DVD drives and both hard disks in Device manager? If so try deleting the CD/DVD drives and rebooting.

3. If you remove the Ubuntu drive and make the Windows drive a master again do the CD/DVD drives reappear?

Let me know how you get on - depending on the answers to the above questions I may be able to suggest a few other things to try. If it goes too far off-topic we may have to take it out of the forum though.

HTH

Andy B

---

### Post by PDXlewis on 2005-12-30
[QUOTE=abovett]
I suspect that by moving your Windows drive from Master to Secondary you've confused Windows (easy to do!) about what devices are where. This is really a Windows problem not a Ubuntu one, but I'll try to help.
[/QUOTE]

This is sounding familiar to me again. Both you and audax321 mentioned this and I am betting this will be the deal. don't want to confuse windows if I can help it....


[QUOTE=abovett]
1. Did you move the CD/DVD drives or are they still connected to the same IDE bus?

2. Can you see the CD/DVD drives and both hard disks in Device manager? If so try deleting the CD/DVD drives and rebooting.

3. If you remove the Ubuntu drive and make the Windows drive a master again do the CD/DVD drives reappear?
[/QUOTE]

1. No, I did not move anything yet. 
2. Can't see the drives in device manager.
3. haven't done the master/slave switch yet, but will find out next. 

Thanks for the quick response, both of you. You made my guessing feel more confident. And I appreciate it, I know this is not an ubuntu issue. I may not spend too much time trying to make them play nice together if I don't see results with the drive swap. I think I need to buck up and give my wife the windows machine and make a new ubuntu machine. excellent.....
****

---

### Post by PDXlewis on 2005-12-31
Thanks again. swapped my drives (windows to master now) and reloaded both my discs in the right order. I can see my drives and everyone is booting happy like. 

This rules

Tim

---

### Post by abovett on 2006-01-01
Glad you sorted it.

I've done a number of dual boot machines. I always try to load Windows first, and leave it where it expects to be. The installers for most linux distros are good enough to detect Windows and give a boot option for it when they install Grub or Lilo so it's generally not a problem - plus Linux is a lot less fussy about where it "lives" regarding drives, partitions etc.

Andy B

---

