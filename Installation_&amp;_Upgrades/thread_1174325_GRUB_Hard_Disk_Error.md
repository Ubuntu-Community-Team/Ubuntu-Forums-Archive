---
title: "GRUB Hard Disk Error"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by savemefromwindows on 2009-05-30
Hi, new to ubuntu, been trying to install for 3 days now and getting very frustrated. Installed 9.04 from the LiveCD, all I get on reboot is GRUB Hard Disk Error. Have googled this, and been totally baffled by the 'fixes' suggested, as they're way beyond my understanding and appear mostly to relate to dual-boot issues. Downloaded Super Grub, and puzzled my way through the charmingly idiosyncratic interface, but to no avail. My BIOS is up to date, the hard drive is fine, I don't have an XP install disk, just a Recovery CD which doesn't give an option to start XP Recovery Console. 

I can boot into Ubuntu via the CD, but as I'm using a sub-notebook without an internal CD drive, I don't want to have to lug a CD round with me just to be able to boot into Ubuntu.

Can someone please step a confused old codger thru this in a reasonably slow and idiot-proof way? I *really* don't want to go back to XP, but have reached the end of my tether. Please help.

machine is Toshiba Libretto u100, 30gb drive, 1gb ram

fdisk -l produces:

Disk /dev/sda: 29.7 GB, 29734387200 bytes
255 heads, 63 sectors/track, 3615 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaacda3a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3460    27792418+  83  Linux
/dev/sda2            3461        3615     1245037+   5  Extended
/dev/sda5            3461        3615     1245006   82  Linux swap / Solaris

Very many thanks for your patience.

---

### Post by lindsay7 on 2009-05-30
Try this from the live cd. 

sudo grub
find /boot/grub/stage1
(it will give a (hdx,y)
root (hdx,y)
setup (hd0)
quit


and reboot

---

### Post by badaveil on 2009-05-30
> **lindsay7 said:**
> Try this from the live cd. 

Sudo grub
find /boot/grub/stage1
(it will give a (hdx,y)
root (hdx,y)
setup (hd0)
quit


and reboot

Hi

I'm having a "GRUB loading stage 1.5." error and am following your advise

line1 "sudo grub" was OK but line2 ,enter, reads "error 27: unrecognized command". How now?

---

### Post by lindsay7 on 2009-05-30
badaveil,


That needs to be a small s in sudo
did you enter your password after you entered sudo grub?

and did you put a space after find?

---

### Post by badaveil on 2009-05-30
> **lindsay7 said:**
> badaveil,


That needs to be a small s in sudo
did you enter your password after you entered sudo grub?

and did you put a space after find?

Yes did all that
line 1 was "sudo grub" (all lower case yes thank you)
 I just jumped that find line and tried line 2 "root (hd0)" and it went through
"setup (hd0)" gave message"cannot find selected partition"

---

### Post by badaveil on 2009-05-30
lindsay7?.... :-(

---

### Post by merlinus on 2009-05-30
Try:

root (hd0,0)
setup (hd0)

---

### Post by savemefromwindows on 2009-05-30
> **lindsay7 said:**
> Try this from the live cd. 

sudo grub
find /boot/grub/stage1
(it will give a (hdx,y)
root (hdx,y)
setup (hd0)
quit


and reboot

Hi Lindsay7, thanks for your input. Tried this, got encouraging messages from the terminal, but still no joy on reboot (same error as before).

I´ve even tried deleting all the partitions with Gparted and reinstalling, and trying your method again, thinking perhaps the boot sector had become corrupted, but still the same.

UPDATE: Sorted!! used this code:

root (hd0,0)
install --stage2=/boot/grub/stage2 /boot/grub/stage1 d (hd0) /boot/grub/stage2 p (hd0,0)/boot/grub/menu.lst

...courtesy of this thread: [http://ubuntuforums.org/showthread.php?t=363355&page=4](http://ubuntuforums.org/showthread.php?t=363355&page=4)

---

