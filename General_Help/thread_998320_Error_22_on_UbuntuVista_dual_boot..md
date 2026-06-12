---
title: "Error 22 on Ubuntu/Vista dual boot."
date: 2008-11-30
forum: General Help
---

### Post by Snake847 on 2008-11-30
I just erased my ubuntu partition to create a new one on a new HD. I also know from reading some posts that my problem is caused by this.
When I start my pc i get:
Verifying DMI Pool Data ...........
Boot from CD:
Boot from CD:
GRUB Loading stage1.5 .


Grub loading, please wait...
Error 22

I am lost and have no idea how to fix this. Any help would be of great help!

---

### Post by zeigfried on 2008-11-30
Boot with your windows cd.
Go to recovery console and type ```
fixmbr
```.
This will erase grub from your mbr and make windows boot directely.
You can always reinstall grub later.

Cheers

---

### Post by Snake847 on 2008-11-30
I do not have a windows CD. I am making a recovery disk on my lap top but I do not think it will help. The PC did not come with a windows disk in the first place(eMachines with windows installed on HD). Any ideas?

---

### Post by caljohnsmith on 2008-11-30
To replace Grub, you can install a Windows MBR (Master Boot Record) from the **Ubuntu Live CD** by opening a terminal (Applications > Accessories > Terminal) and doing:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/[COLOR="Blue"]sda[/COLOR]
```
"sda" should be your internal HDD, but you can change it if necessary. Let me know how that goes or if you run into problems. :)

---

### Post by Snake847 on 2008-11-30
As stated above I have no windows CD.

---

### Post by Snake847 on 2008-11-30
I am downloading a new 8.04 install. This is what I had on it. I do have a 8.1 64bit CD which is what I was planning on installing but it does not work.

---

### Post by pcjunkie on 2008-11-30
How did you get windows without a windows CD? Are you using a whitebox pc like Dell or Acer?

If you need a MBR google that or get XP light from TPB or something, that should help with the MBR issue...

Anyways,.

When grub loads try using shift e

edit the menu list 

Use the live CD to find out where the ntldr file or boot.ini file is located.

If its there then grub is looking at the wrong disk.

---

### Post by Snake847 on 2008-11-30
Yes sir, it is an Acer. I found a vista recovery ISO on PCworld. every walkthrough I read so far talks about a live CD of Vista or Ubuntu, which I do not have.
edit: some more details.
When I decided to format that partition I also installed a second HD which is new and formatted it as well.

---

### Post by Snake847 on 2008-11-30
update: booting from live ubuntu 8.04 CD does not work:
boot from CD:
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

---

### Post by zeigfried on 2008-11-30
Well we can't teach you how to get a Windows CD or disk in order to do what you must... But I'm quite sure you will find a way  :lolflag:.
The best setup for dual booting two hds is Windows and it's own MBR in one hd and linux plus grub in the other (if anything goes wrong you can boot Windows without the need of a Live CD)

---

