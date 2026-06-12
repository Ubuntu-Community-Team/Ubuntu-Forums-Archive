---
title: "How to uninstall Windows XP from a happy, clean Ubuntu!"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by nintennuendo on 2008-12-14
How?  

I installed Ubuntu yet again after committing myself to not buying things that can otherwise be shared freely.  

So, now I've got ubuntu dual-booted, but I can't get rid of the XP in gparted.  I would've cleaned the grub list but didn't know if it'd matter.   What should I do?

---

### Post by logos34 on 2008-12-14
you need to unmount the partition first before you can delete it.

post your

sudo fdisk -l

---

### Post by nintennuendo on 2008-12-14
if anyone can tell me how to post in code too, i'd be grateful.  I can't seem to figure it out.

nick@Nicktop:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48374836

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5286    42459763+   7  HPFS/NTFS
/dev/sda2            5287        7296    16145325    5  Extended
/dev/sda5            5287        7206    15422368+  83  Linux
/dev/sda6            7207        7296      722893+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x170a8ae2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS

---

### Post by logos34 on 2008-12-14
> **nintennuendo said:**
> if anyone can tell me how to post in code too, i'd be grateful.  I can't seem to figure it out.

if you mean 'paste' code in the terminal, then:

ctrl+shift+v

---

### Post by nintennuendo on 2008-12-14
I do not, I obviously did that, I meant posting in a seperate sub-window in the post on this forum.  But how can I get rid of windows

---

### Post by logos34 on 2008-12-14
you've got two windows system partitions, sda1 and sdb1.  Not sure why gparted won't let you delete them, unless they're mounted like I said.  You might try booting the ubuntu live cd and using system>admin>partition editor (gparted) there--maybe it won't give you problem

add:
> re: separate subwindow:

click 'reply', the on the 'wrap/bubble' icon (farthest right after 'picture' icon) in the mini toolbar

---

### Post by nintennuendo on 2008-12-14
If i can unmount them, would I just delete the XP info from grub?

edit:  wellll, I unmounted, deleted in gparted, and now i've a big 43gb chunk that won't be allocated =(

---

### Post by logos34 on 2008-12-14
now,

gksudo gedit /boot/grub/menu.lst

remove the windows entries at the bottom

do the same for /etc/fstab

Format the unallocated space in gparted with 'New'...create new ext3 partition expand your linux / to take up the space

---

### Post by nintennuendo on 2008-12-14
delete this whole bit, right?:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


and what of this mess do i delete?:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=56f23937-8c0f-472e-b2c8-a2f130221ea3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=f49eb8f8-697c-4054-b8b3-9c16e8aba907 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by logos34 on 2008-12-14
> **nintennuendo said:**
> delete this whole bit, right?:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

yep, whole thing

No xp entry in fstab so leave it

---

### Post by nintennuendo on 2008-12-14
alrighty, well, did that, couldn't resize so the main partition would take on the other one, so i did ctrl+alt+backspace after everything was done, but then nothing happened.  so after 10 minutes or so, i powered off and came back on.  now i have no panel or whatever controls alt+f2.  so yeah.  Any ideas?

---

### Post by logos34 on 2008-12-14
hmm.  wonder what happened...the deleted windows wasn't even close to ubuntu (which is inside extended partition sda2).  To expand / to take up the empty space left by xp you have to boot again from the live cd, swapoff to unmount sda6, then drag left border of the extended (sda2) to the front of the disk, then you can expand / to the front.  

Try alt+ctrl+backspace to restart the desktop.  If it's still funky reboot the live cd and run filesystem check:

sudo fsck /dev/sda5

---

### Post by nintennuendo on 2008-12-14
SO i did this:

nick@Nicktop:/usr/bin$ sudo debconf gnome-panel
[sudo] password for nick: 
Can't exec "gnome-panel": No such file or directory at /usr/share/perl/5.10/IPC/Open3.pm line 168.
open2: exec of gnome-panel failed at /usr/share/perl5/Debconf/ConfModule.pm line 59

nothing happens.  also something with --shutdown and pkill panels.  nothing does anything.


edit:  so i was cleaning something from system>sessions and i deleted a few things, but i can't remember what they are.  i'm guessing that matters..??

---

