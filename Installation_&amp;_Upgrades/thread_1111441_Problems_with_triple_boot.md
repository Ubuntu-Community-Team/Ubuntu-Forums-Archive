---
title: "Problems with triple boot"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by ptaramelli on 2009-03-30
I' ve got a PC with 3 disks, I put XP on first, Ubuntu on 2nd, and OSX on 3rd. All instalations with one disk connected at the time. I edit the /boot/grub/menu.lst to put there XP ans OSX, in the BIOS I put to boot from 2nd (Ubuntu). 
From there I can of course boot UBUNTU, and OSX, but not XP.
I've got no problem before with triple boot in one disk.

I attached here the results of sudo fdisk -lu , cat /media/disk/boot.ini  and  /boot/grub/menu.lst.

Can Somebody help me with this??

Thanks from now

Pablo

---

### Post by Mark Phelps on 2009-03-31
Since you're booting from your "second" drive, it is the first drive that GRUB sees; therefore, GRUB does not see your XP drive as drive "0". My guess is that GRUB sees your XP drive as drive "1".  

So, change "root (hd0,0)" to "rootnoverify (hd1,0)" and see if that works.  Also, before that, insert the following:

map (hd1) (hd0)
map (hd0) (hd1)

This should work because when you installed Ubuntu, you automatically installed GRUB to the MBR of that drive.

---

### Post by ptaramelli on 2009-03-31
Thanks, I'm trying tonight (it's my home PC) and I told you. 

I 'd already tried :

(hd1,0) and
map (hd1) (hd0)
map (hd0) (hd1) (reading another post)
and it didn't work, but not with "**rootnoverify**", I forgot to tell you (but you may know it) that the error I've got in the first case was Error 13: Invalid or unsupported executable  format.

When it didn't work with the above, I let GRUB as it was before, and now (surprise) I can't make boot ths OSX!!!. I can;t see any changes!!

To boot one particular OS I've got , for the moment to put in the BIOS what drive to boot.

Pablo

---

### Post by ptaramelli on 2009-04-02
Mark: I've tried what you say, and I get "error 11: Unrecognized device string...", so I erase map - map .... and I enter in OSX with hd(1,0).

So I began to try in the windows line differents disks and partitions and this is what I got:
hd(0,0) Error 13
0,1 and 0,2 the same

hd(1,0) OSX as I said
1,2 amd 1,3 : "no such partition
and with 
hd(1,1) i've got:
The first time:
Starting up....
This is not a bootable disk, please insert a bootable floopy and press any key to try again.
I PRESS ENTER O SCAPE AND I GET:
Boot 0: MBR
Boot 0: Done this is not a bootable disk etc etc

I PRESS ENTER OR ESC FOR THE SECOND TIME AND I ENTER WINDOWS.

Well, not very elegant but I do what I want, but I don;t know why, and I don't like this.

If you still has the taste for it, I attach the screens of the gparted for the 3 disk, If you can give me some lights, i'll apreciate it.
thanks anyway
Pablo
P/D: I'll put those in another, I'm in windows and I have to enter Ubuntu.

---

### Post by ptaramelli on 2009-04-02
Here they are!
Pablo

---

