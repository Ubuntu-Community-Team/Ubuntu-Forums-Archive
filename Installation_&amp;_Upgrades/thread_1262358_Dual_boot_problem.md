---
title: "Dual boot problem"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by Gaspacho79 on 2009-09-09
Hello, first of all thanks in advance for any kind of assistance you guys could provide me. I've been reading this forum for quite a while now, and now is the first time I need to ask a question cause I didn't find anything similar. I, as any other linux user, am used to the search button lol. By the way, nice forums.

Well, the problem is, I had Ubuntu installed for quite a while now in this computer. I knew that when you have windows and install ubuntu you get the choice to dual boot. So now I installed windows cause I wanted to do so, but you don't automatically get the dual boot choice, neither you can boot from the ubuntu CD to make one. I don't want to install ubuntu again to dual (or triple) boot, I know I can do so, cause ubuntu or any other GNU/Linux recognizes 2 OS installed on the system

My question is, which's the best way now to create a dual boot with ubuntu as the default?

Thanks for the answer or the URL of a similar problem.

Oh and by the way, it just occurred to me, perhaps I could use windows F8 to boot ubuntu, I'll check that now.

---

### Post by raymondh on 2009-09-09
> **Gaspacho79 said:**
> 
Well, the problem is, I had Ubuntu installed for quite a while now in this computer. I knew that when you have windows and install ubuntu you get the choice to dual boot. So now I installed windows cause I wanted to do so, but you don't automatically get the dual boot choice, neither you can boot from the ubuntu CD to make one. 

My question is, which's the best way now to create a dual boot with ubuntu as the default?
.

When you installed windows, did you make sure you did not overwrite your ubuntu installation?  One way to check is to boot into your liveCD and go into live session (try ubuntu...).  Access a command prompt and type (as well as post back output)

```
sudo fdisk -l
```

small L, not I nor 1.

If Ubuntu is still there, and after installing windows, did you try to re-install GRUB (as windows' bootloader would have overwritten the MBR) ?

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Gaspacho79 on 2009-09-09
Raymond:

Thank you VERY much for your assistance.

Yes, I made sure that windows didn't delete my ubuntu installation, I'm certain is still there, you'll see why now. It's in another partition though. It was recommended that way.

Now I have another problem, now I used your thread to re-install GRUB. I did it successfully. However, now I cannot boot to windows (crap). When I boot, GRUB says, press esc to enter the menu (as usual) and I do not have any windows installation there, just 2 ubuntus and 2 ubuntus recovery mode and 1 ubuntu memtest.

Weird. Do you know what's the next step? I am using ubuntu now, and I cannot access windows, I'm exactly the other way around I was when I started the thread. Windows Installation wasn't deleted cause I just installed GRUB and did nothing else.

Thank you again, seriously.

---

### Post by confused57 on 2009-09-10
Please post the output of "sudo fdisk -l" as raymondhenson suggested, then someone should be able to give you the correct grub entry to boot Windows.

---

### Post by Gaspacho79 on 2009-09-10
Really sorry about that, I really forgot. 

Here's the output:

```

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf85bf85b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5211    41857326    7  HPFS/NTFS
/dev/sda2            5212       24321   153501075    5  Extended
/dev/sda5            5212       23581   147556993+  83  Linux
/dev/sda6           23582       24321     5944018+  82  Linux swap / Solaris

```

Thanks for reminding me. :)

---

### Post by confused57 on 2009-09-10
It shouldn't be to difficult to add an entry to boot XP from grub, first open a terminal:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo gedit /boot/grub/menu.lst
```
then add this entry to the very end of your menu.lst:
```
title     Windows XP <---or name it whatever you want
root        (hd0,0)
makeactive
chainloader   +1
```

Also, you won't need to press "Esc" to access the grub menu when booting if you place a # in front of hiddenmenu, i.e.
```
hiddenmenu
```
to
```
#hiddenmenu
```

quit & save

---

### Post by Gaspacho79 on 2009-09-10
I love you!

I even understood what you did, so next time, I will be able to do this myself. However, I didn't get the part of "makeactive" nor the part of "chainloader +1".

Thank you, thank you, thank you so much.

And of course, thanks raymond too!

---

### Post by confused57 on 2009-09-10
> **Gaspacho79 said:**
> I love you!

I even understood what you did, so next time, I will be able to do this myself. However, I didn't get the part of "makeactive" nor the part of "chainloader +1".

Thank you, thank you, thank you so much.

And of course, thanks raymond too!
Great, glad you were able to boot XP from grub...I just
intervened because raymond wasn't logged in at the time.

This explains a little about chainloading:
[http://members.iinet.net.au/~herman546/p15.html#2._Chainloader](http://members.iinet.net.au/~herman546/p15.html#2._Chainloader)

Makeactive probably isn't needed, since "fdisk -l" showed the boot flag on your XP partition...linux doesn't normally need the makeactive line.

---

### Post by raymondh on 2009-09-10
Well done gaspacho79.  Thank you for your assitance confused57.  

Happy Ubuntu-ing.

---

