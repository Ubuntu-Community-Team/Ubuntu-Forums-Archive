---
title: "Reinstall of Windows.."
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by AoSteve on 2009-07-02
Alright, heres the setup....   I've reinstalled Windows Vista on a different hard drive and need to know how exactly to edit my menu.list file to allow booting to windows.  I'm not on the Ubuntu partition as of right now but I know I'm going from SDA0 to SDA1.   Is it as simple as changing the "location" in the list?
 
Before...
 
Raptorx 150gb:
Part1: Windows
Part2: Ubuntu
Part3: Linux Swap
 
Now...
 
Raptorx 150gb:
Part1:  To be stretched over with Ubuntu partition
Part2:  Ubuntu
Part3:  Swap
 
WD800JB:
Vista...
 
 
So how would I go about changing that setup?
 
Thanks in advance, I've never dealt much with the grub or menu.list files and don't want to "permascrew" it up.

---

### Post by presence1960 on 2009-07-02
Boot into ubuntu and open a terminal and run > sudo fdisk -l that is a lowercase L. Post the output here. and we'll get your windows entry in menu.lst so you can boot windows.

---

### Post by AoSteve on 2009-07-02
Well, here's the main thing I'm worried about.   I was originally booting from the Windows partition on my RaptorX.  I reinstalled on a totally different drive and want to take over that old partition with Linux.   Now,  would that cause a problem wanting to boot like that?   Wouldn't that remove the original bootup files since they were originally on the Raptor?

---

### Post by presence1960 on 2009-07-02
not exactly, because the windows bootloader is on the MBR which is a spot before the first partition on a drive. But what you can do is keep that disk as first boot and set GRUB up on the MBR. Post the output of that command and I'll give you the commands to place GRUB in MBR and also your windows entry for menu.lst

---

### Post by AoSteve on 2009-07-02
Ok, let me boot up ubutnu  :)

---

### Post by presence1960 on 2009-07-02
> Thanks in advance, I've never dealt much with the grub or menu.list files and don't want to "permascrew" it up.

How do you think we learn what we know? Some is thru reading but most is by getting in there and permascrewing things up so we have to repair them. After you start repairing your messups you begin to understand the nature of not only the problem but also the nature of the solution. If you don't get in your linux and try things your knowledge won't grow much.

---

### Post by AoSteve on 2009-07-02
Talk about "growing"   LOL!!!!   I broke it good here...  LOL   The Microsoft Boot Loader has TWO options..  Vista and Vista, and neither lead me to my Ubuntu Install..  LOL!   

I have officially broke it this time.   Officially broke it, totalled, destroyed.. dumbdified.

I know, I know, it's not destroyed, just gotta get it to where I can boot it up now.   Hmm..   I bet the Live CD would help...   But Alas, I haven't got one handy, what's a good burning utility for Ubuntu that will burn from an ISO image?  I've NEVER burned a CD from Linux, so it's time for even more learning.   And yes, I break stuff all the time...   Just look at my avatar and my signature, I broke the spelling of Ubuntu pretty good for my conky! :)

---

### Post by presence1960 on 2009-07-02
When you installed Vista I hope you set your WD drive to first boot in BIOS. If so make sure your raptor is set as first boot in hard drive boot order in BIOS. Then reboot. if it doesn't bring up GRUB we can boot into the Live CD and restore GRUB.

If you didn't set your WD as first boot when you installed windows then Windows wrote to the MBR of your raptor disk. You would have gotten a message from the windows installer to the effect that windows needs to write to a disk, but it is not an NTFS partition.

---

### Post by presence1960 on 2009-07-02
brasero and k3b work for me for burning.

---

### Post by AoSteve on 2009-07-02
The Raptor was disconnected during the install, so that's not it.  It must of done something afterwards when the original windows started to boot up...   I was trying to get into Ubuntu and it said "Windows BootLoader"    I've never seen it before...   I had set the raptor as the first boot device since the install..   I don't get it...

Gonna make a LiveCD here now..

---

### Post by presence1960 on 2009-07-03
> **AoSteve said:**
> The Raptor was disconnected during the install, so that's not it.  It must of done something afterwards when the original windows started to boot up...   I was trying to get into Ubuntu and it said "Windows BootLoader"    I've never seen it before...   I had set the raptor as the first boot device since the install..   I don't get it...

Gonna make a LiveCD here now..

still need the results of ```
sudo fdisk -l
```

---

### Post by presence1960 on 2009-07-03
Boot from the Live CD and follow this:

1```
. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, if raptor is hd0. 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

it's getting late & I need to sleep as I have work tomorrow. Without the output from sudo fdisk -l I can't give you specifics for the above. You want to use your ubuntu partition for #5 root (hdx,y). In # 6 you want to use setup (hd0) or setup (hd1). use whichever one is your raptor. Then finally you will have to edit your windows entry in menu.lst. It should look like this, but without seeing your sudo fdisk -l you may have to edit the (hdx,y):

```
title          Microsoft Windows 
rootnoverify   (hd1,0)
map            (hd0) (hd1)
map            (hd1) (hd0)
chainloader    +1
```

Give it a whirl and see what happens. post back there are others here who can help. I know I saw merlinus and raymondhenson on here just a little while ago. if not I will check back in the AM.

---

### Post by AoSteve on 2009-07-03
Sounds like a good plan.  I just now got the CD all done and ready.  I'm going to go pop it in and see if I can get this to work out right.  :)

I will post back as soon as I find out what's what with Grub.   I'd rather just boot from the raptor and load grub from there.  Then from there go with the selection to boot off of the WD800JB.   :)   Thanks for the help!

---

### Post by AoSteve on 2009-07-03
**sudo fdisk -l**
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdea76e4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9179    73728000    7  HPFS/NTFS
/dev/sda2            9180       18241    72790515    5  Extended
/dev/sda5            9180       17689    68356543+  83  Linux
/dev/sda6           17690       18241     4433908+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30402   244196352    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb571e27d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9730    78148608    7  HPFS/NTFS

```


The 250GB is my storage drive, I know that, but it made it a LOT easier to understand..  I think I can get it from here, if not.. I'm sure someone will know what to do.

---

### Post by merlinus on 2009-07-03
If you are booting from sda first, and windows is on sda1 and linux on sda5, as it appears from the results of sudo fdisk -l, then try this:

```
sudo grub
root (hd0,4)
setup (hd0)
quit
```Then you would add this to the end of menu.lst:

title windows
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by AoSteve on 2009-07-03
/dev/sdc is what the new windows disk is located on..  I know that, but I still can't get it to work!

I don't get it, I've used grub like was said..   The NTFS partition on the raptor is now an EXT3 partition that will be used for storage for my linux fun, like VM boxes and the like..   

Either way, I can't get this stupid thing to boot from the raptor at all.  I've even tried setting a boot flag to the ubuntu partition..

/dev/sda1   *           1        9179    73728000    7  HPFS/NTFS
/dev/sda2            9180       18241    72790515    5  Extended
/dev/sda5            9180       17689    68356543+  83  Linux
/dev/sda6           17690       18241     4433908+  82  Linux swap / Solaris

The /dev/sda1 is the partition that I'm ridding myself of in favor of Linux storage...  I need  /dev/sda5 to boot up, I don't know what I'm doing wrong LOL

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb571e27d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9730    78148608    7  HPFS/NTFS

That's the new "working" windows partition...   Everytime I boot it goes STRAIGHT to that..  I don't know what else to do...   How would I set that up through grub on the LiveCD to get back to ubuntu?

---

### Post by merlinus on 2009-07-03
Linux does not need a boot flag, only windows.

What is the booting order of your hdds in bios?  If sda is first, then the grub commands I gave should work, but obviously the windows entry in menu.lst needs to be different.

---

### Post by AoSteve on 2009-07-03
Well, when I take the WD800JB (windows disk) completely out, it just tells me I need bootable media blah blah blah.. and the bios can't find anything..  

I'll go in and try it again...   I don't know what I'm doing wrong LOL   I just want to boot off of the raptor.  I'd like to be able to disconnect the WD800JB and still boot, but right now I can't as there's "no bootable media"  LOL

---

### Post by AoSteve on 2009-07-03
Well I can get into Linux now...  Everything is good on this end, now only to get windows to boot..

```

title windows
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

```

Would I need to change the "rootnoverify" to something like  (hd2,1) ?

```

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdea76e4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9179    73730286   83  Linux
/dev/sda2            9180       18241    72790515    5  Extended
/dev/sda5   *        9180       17689    68356543+  83  Linux
/dev/sda6           17690       18241     4433908+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30402   244196352    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb571e27d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9730    78148608    7  HPFS/NTFS

```

That's the updated fdsik -l  from within ubuntu off the Raptor...  I've tried entering your addition for "menu.lst" and it just told me there's basically no media...  I don't want to "booger" it up.

---

### Post by merlinus on 2009-07-03
Some progress, eh?  Change the windows bit in menu.lst to:

title Windows
rootnoverify (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
makeactive
chainloader +1

---

### Post by AoSteve on 2009-07-03
Sweet bud!  Thanks a ton for the help!   I guess I should download a "Grub" manual!   After some T&E I got it...  But tell me something..

What does the  "map" option do?  rootnoverify sets the boot HDD correct?   I'm not sure about all that.  I'll download a manual or "man grub" or the like and learn!  Better to know when you need it then when this happens!  LoL   Thanks again to the both of you!

Presence and Merlinus, you guys rock!  Wouldn't have got it working right without ya!  Thanks a TON.  I appreciate it!  Good to know I can boot into windows when I have to for school and run ubuntu at all other times! :)

---

### Post by merlinus on 2009-07-03
Great news!  Glad everything is working.

rootnoverify indicates your windows partition, in this case third hdd, first partition.  But since windows needs to believe it is the first thing, the map statements trick it into that.

Numbering for these sorts of statements begins at 0 (zero).

---

### Post by AoSteve on 2009-07-03
Yeah I understand the numbering.   I think my next "linux project" is going to be Grubbing.  LOL   I usually take something and learn about it as much as I can.  Conky was a fun one that I've become more than just an addict to...  LOL   I've heard of grub being customized pretty good.  I've even heard of images being put into them!   That sounds like a fun project!   Thanks again for the help!   I'm definitely happy it's working correctly!  Couldn't have done it without the help!

---

### Post by merlinus on 2009-07-03
grub 2 will be part of karmic koala (9.10).  It's a whole different ballgame, from the little I can understand.  So get a headstart and help us out when it comes time!

---

### Post by presence1960 on 2009-07-03
Good job there Aosteve. Glad you got it working. Now you see why i wanted sudo fdisk -l output.

---

### Post by AoSteve on 2009-07-03
Yep!  You guys saved me a LOT of trouble!  So I can boot all together now and not worry about my Windows disk being the first shot and it can sit there and boil over for all I care.  If it wasn't for my school software, I wouldn't have Vista installed, not even in a VBox.  :)

Thanks guys, I think I'll find out about Grub 2 also! :)   This is one of those moments you look back and say to yourself, "See I learn something new everyday!"   And you guys were the teachers for the "Grub 101" lesson for the day, well night LoL

---

