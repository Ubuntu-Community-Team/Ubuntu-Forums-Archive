---
title: "[SOLVED] Swap /dev/sda and /dev/sdb?"
date: 2008-11-01
forum: Hardware
---

### Post by TheJimtasticOne on 2008-11-01
I've got two hard disks - one's an IDE 80GB drive, the other SATA 250GB. The IDE drive comes up as /dev/sda, and the SATA /dev/sdb. Is it possible, and how, to change this so that the IDE drive is /dev/sdb and the SATA drive is /dev/sda? This is basically because all my operating systems now boot off the SATA drive, so I want the drives to be named as such. It's a cosmetic thing, but I was wondering whether it's possible or not.

---

### Post by TheJimtasticOne on 2008-11-01
Bump.

---

### Post by Yellow Pasque on 2008-11-01
I know it's possible, but it requires writing udev rules, which most people won't find fun.

---

### Post by TheJimtasticOne on 2008-11-01
Thanks - could you point me in the direction of a howto or something? I'll give it a go.

---

### Post by Yellow Pasque on 2008-11-01
[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

---

### Post by TheJimtasticOne on 2008-11-01
Thanks, that helped me fix it.

If anyone's interested, I created a file called 10-local.rules in /etc/udev/rules.d:

> # If the kernel matches a device as sda, change it to sdb.
KERNEL=="sda", NAME="sdb"

# Vice versa.
KERNEL=="sdb", NAME="sda"

---

### Post by krustybaguette on 2012-03-28
> **TheJimtasticOne said:**
> Thanks, that helped me fix it.

If anyone's interested, I created a file called 10-local.rules in /etc/udev/rules.d:

A few years ago you had a problem similar to what I now experience and were able to solve it. 

I have two drives in a Lenovo laptop. The first is a 500GB SATA drive housing my primary OS Linux Mint (derivative of Ubuntu) and Windows 7. The second drive is and IDE drive mounted in an optical drive bay adapter which connects to the computer via an PATA connection. (the latter is NOT what I remembered but it IS what Control Center/Hardware/Disk Utility reports. The second drive has WinXP and Bodhi Linux on it. All four OSes work fine when both drives are installed.

The problem of drive switching occurs when I swap out the second (IDE) hard drive to use the optical bay for my DVD Multi Recorder. I see the same GRUB menu as always but cannot boot Linux Mint, however, Win7 still works. BTW, LM is at the top of the list and Win7 is at the bottom, although I doubt that is significant.

The error message when trying to boot LM is '/dev/sda6 not found' or something to that effect. LM exists on /dev/sdb6 when I have both drives installed. I have the same problem trying to boot LM if I detach the laptop from the docking station which houses the second drive.

You described your situation as mainly cosmetic, but for me it is more of a problem. I can only guess it came about due to various changes I've made, such as "downgrading" to Linux Mint 9 after I had "upgraded" to LM12 a while back. Due to a few glitches (Gnome3 I think) I decided to go back to the most recent version that will be supported until April 2013 at which point I'll probably install LM13. There was a time when I didn't have this problem and I'd like to get back there!

I wonder if I could solve the problem by removing the Bodhi Linux installation from the secondary disk and possibly either reinstalling or re upgrading my Mint installation from a USB stick??? If both drives remained in place during these changes I would think the new GRUB installation would end up on the same drive as LM and would point to it whether or not the DVD bay was occupied by the optical drive or the hard drive adapter.

All suggestions welcome!

edit: Since my laptop sees my primary drive as sdb when both hard drives are installed, wouldn't changing it to sda only exacerbate the problem? I need a solution that will let me swap in and out the optical drive and the secondary hard drive and still be able to boot from the primary hard disk which is currently named sdb. 

Maybe the easiest solution is to buy an external USB DVD writer;)

krustybaguette

---

