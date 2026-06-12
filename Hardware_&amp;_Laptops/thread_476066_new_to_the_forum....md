---
title: "new to the forum..."
date: 2007-06-16
forum: Hardware &amp; Laptops
---

### Post by steelfan81 on 2007-06-16
hello there....

i apologize in advance if this hasn't been posted already. if it has, please feel free to direct me to the correct link and close this thread in the process....

i have a few questions in regards to your OS.

1. can i install it on my HP laptop when windows is not currently working? i tried to do a windows recovery last night, and it froze (long story).

2. can i use my memory stick to boot into your OS? and if i can, would i be able to access those files that are already on my hard drive? 

what i am trying to do is try out the new OS on a trial basis, but at the same time, try to access my important (to me) files that are still on there. i don't have my XP recovery disk with me (at work, disk 300 miles away), so i'm looking for options here. 

thanks in advance for your replies..... :)

---

### Post by steelfan81 on 2007-06-16
another question of mine.... 

3. my laptop is wifi capable, and is my main connection to the web outside of work.... what must be done to re-gain that capability?

---

### Post by croto on 2007-06-16
Hi, welcome to the forum!

If you want to install Ubuntu on the hard drive together with Windows, first you will have to make the windows partition smaller. It is *strongly* recommended that you first defrag and run checkdisk on the windows partition before resizing. Since your windows is not working I'm afraid there could be some inconsistencies in the file system which would lead to total disaster (loss of information) while resizing the partition. So my advice would be to wait until you fix Windows before installing Ubuntu.

It is possible to boot  Ubuntu from a memory stick. But I would suggest first you boot from the live CD. Very likely you will be able to access your data on the windows partition (and make a backup!)

Depending on what wireless card you have, it may just work, or you may have to install some driver. Try and see what happens.

Good luck!

---

### Post by steelfan81 on 2007-06-16
4. does DOS recognize memory sticks as boot devices? 

thanks for the reply....

i have no blank CDs to write to; i don't get off work til 11pm EST tonight and tomorrow night..... i do have two memory sticks tho, a 1GB and 2GB.... 

what i want to do is save my important (to me) files to the work computer temporarily, then let the repair people do whatever needs to be done...

going to try it now, and see what happens.....

---

### Post by IntuitiveNipple on 2007-06-16
If you have access to another Windows PC that can read/write to your memory cards it is possible to install the Ubuntu Live CD to the flash-memory card, and, if your problem-PC can boot from USB flash-memory cards, it should be possible to boot Ubuntu from it simply by ensuring the PC's BIOS boot setting checks the USB device before the hard drive.

The 'Live CD' (aka Flash memory install) will, if it can handle all the PC's hardware, eventually get to a minimalist looking desktop. The menu at the top will let you explore.

By default Ubuntu can read Windows NTFS file-systems and you should find them from the Places->Computer menu, which will open a Nautilus file-explorer window.

This article on installing an older version of Ubuntu to a USB Flash memory stick might help, but I hope you're reasonably technical!

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

