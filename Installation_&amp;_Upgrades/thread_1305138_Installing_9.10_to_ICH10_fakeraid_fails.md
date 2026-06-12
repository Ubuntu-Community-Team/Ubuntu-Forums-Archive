---
title: "Installing 9.10 to ICH10 fakeraid fails"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by davexunit on 2009-10-29
The installation of 9.10 went great until it was time to install grub, then ubiquity crashed. Ubiquity saw my fakeraid and let me partition everything correctly (unlike 9.04), but grub still fails to install.
Does anyone else have this problem?
Has anyone solved this problem?
Ubuntu's lack of proper support for software raids, which are becoming more and more common on motherboards (I have an asus p6t), is really disappointing.

---

### Post by davexunit on 2009-10-29
Solution found! I just followed the instructions found here: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
I followed the 9.04 instructions for after ubiquity completes (making sure I did not install grub in ubiquity).
It's a shame I still need to use command line trickery do get a fresh install working but I'm glad it works 'cuz ubuntu rocks my world aside from this issue.
I hope this short thread is of help to someone that faces the same problem.

---

### Post by jelvis on 2009-10-31
I am having the same problem but I have not succeeded in fixing it yet. (Using a DELL laptop with fakeraid, one vista partition and two for Ubuntu.)

Would you be so kind as to describe exactly the point where you started to follow the guide. I find it all very confusing and the guide seems to use the old version of Grub and not the new one.

Is it from Step 9 under "Live CD installation"?

Did you install the old grub version?

---

### Post by davexunit on 2009-10-31
> **jelvis said:**
> I am having the same problem but I have not succeeded in fixing it yet. (Using a DELL laptop with fakeraid, one vista partition and two for Ubuntu.)

Would you be so kind as to describe exactly the point where you started to follow the guide. I find it all very confusing and the guide seems to use the old version of Grub and not the new one.

Is it from Step 9 under "Live CD installation"?

Did you install the old grub version?
yes, I did use old grub. I followed the 9.04 instructions from after it tells you to run the ubiquity installer. I'm short on time right now but I can provide more details another time if you're still having trouble.

---

### Post by davexunit on 2009-11-01
Okay, let me try to break this down a little better.

1. From the live cd, run the installer as normal EXCEPT...
2. Click the "Advanced" button when you reach the last step before installation.
3. Uncheck the "Install bootloader" option.
4. After installation finishes, open a terminal.
5. run "ls -l /dev/mapper". This will show you the contents of your raid array. Here's mine: 
```
total 0
crw-rw---- 1 root root  10, 60 2009-11-01 06:01 control
brw-rw---- 1 root disk 252,  0 2009-11-01 06:01 isw_dgihajjefa_DaveRAID
brw-rw---- 1 root disk 252,  1 2009-11-01 06:01 isw_dgihajjefa_DaveRAID1
brw-rw---- 1 root disk 252,  2 2009-11-01 06:01 isw_dgihajjefa_DaveRAID2
brw-rw---- 1 root disk 252,  3 2009-11-01 06:01 isw_dgihajjefa_DaveRAID3
brw-rw---- 1 root disk 252,  4 2009-11-01 06:01 isw_dgihajjefa_DaveRAID4

```
"isw_dgihajjefa_DaveRAID" is my raid array.
isw_dgihajjefa_DaveRAID1, isw_dgihajjefa_DaveRAID2, etc. are my partitions.
You will need to refer to this info as we go on.
6. The following is copied directly from the tutorial I referenced earlier. Run these commands, replacing "isw_beeaakeeaa_five5" with the partition that ubuntu is now installed on.
These commands install dmraid and grub to the new ubuntu installation.
```
sudo mount /dev/mapper/isw_beeaakeeaa_five5 /target/
sudo mount --bind /dev /target/dev/sudo mount -t proc proc /target/proc/
sudo mount -t sysfs sys /target/sys/
sudo cp /etc/resolv.conf /target/etc/resolv.conf
sudo chroot /target/ 
apt-get update  
apt-get install -y dmraid 
apt-get install -y grub 
mkdir /boot/grub 
cp /usr/lib/grub/x86_64-pc/* /boot/grub/

```
7. The following steps configure grub.
```
grub --no-curses  // NOTE: you will now be at the grub prompt grub> 
grub> device (hd0) /dev/mapper/isw_beeaakeeaa_five 
grub> find /boot/grub/stage1
// NOTE: take note of this output, and replace the 'x's in the next steps with the numbers given here.
 
grub> root (hd'x','x') 
 grub> setup (hd'x') 
grub> quit
```
8. Run "update-grub". Say yes to creating a menu.lst
9. Now open the newly created menu list and make the following changes. Any editor can be used it is not required that you use nano # nano /boot/grub/menu.lst 
Change:
```
# groot=(hd0,0) TO # groot=(hd0,'x') 
root option in the boot entries  to root (hd0,'x') Replace the 'x' with the partition that was found earlier 

```

Add the Windows boot entry if need be. 
```
  title                 Windows
  rootnoverify (hd0,0)   # use the correct partition for Windows, of course
  makeactive
  chainloader +1
```
For all Ubuntu-related boot entries, such as ```

 title         Ubuntu ...
   root          (hd0,0)
   ...

```change (hd0,0) to (hd'x','x'), where the 'x's are the results from the grub find command earlier.
Save and exit nano. or what ever text editor you are using.10. Run "update-grub " again. It gave me some errors, I ignored them and everything still worked.

11. Run  "update-initramfs -u". I think this also gave me errors that I ignored and things still worked. 12. Run "nano /etc/modules". Add "dm-raid4-5" if it s not there.


I did this and everything worked. Hope it works for you. This is mostly a big copy/paste from the tutorial but hopefully it makes a bit more sense.

---

### Post by jelvis on 2009-11-09
Thank you davexunit for your thorough reply!

Unfortunately, I still did not get it to work. However, that might have been an error 60. I'll give it another shot in a few days.

---

### Post by jpichie on 2009-12-09
Everything works fine for me up until your step 7 (grub).
I get "unknown partition table specified" when typing "grub --no-curses" and I also get "error 15: File Not Found" when doing the find /boot/grub/stage1. I double checked to make sure I have the file, and it is under my grub folder.
This is really starting to frustrate me, I even gave the Lucid Lynx Daily a try, and it did not work with Grub2 yet (even though it is fixed).

---

### Post by darkod on 2009-12-12
How about when creating your RAID array leaving small partition at the beginning of the drive(s) outside the array and using it for ordinary none raid /boot partition?

---

### Post by quequotion on 2009-12-15
> **jpichie said:**
> Everything works fine for me up until your step 7 (grub).
I get "unknown partition table specified" when typing "grub --no-curses" and I also get "error 15: File Not Found" when doing the find /boot/grub/stage1. I double checked to make sure I have the file, and it is under my grub folder.
This is really starting to frustrate me, I even gave the Lucid Lynx Daily a try, and it did not work with Grub2 yet (even though it is fixed).

Be careful which partition you specify in grub for (hd0)!
```
ls /dev/mapper
``` should give you a list like
```
control brand_randomalphanumerics brand_randomalphanumerics1 brand_randomalphanumerics2
```You want to install grub on the primary partition. /dev/mapper/brand_randomalphanumerics (without a number at the end).
This partition is a container that specifies the filesystems and sizes of your other raid partitions.

---

### Post by gilson585 on 2009-12-20
you may also check my post which includes everything you need to install 9.10 on fakeraid [http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445)

---

