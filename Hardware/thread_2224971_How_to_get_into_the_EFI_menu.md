---
title: "How to get into the EFI menu?"
date: 2014-05-19
forum: Hardware
---

### Post by tar0n on 2014-05-19
Hi guys,

I have installed Kubuntu on a laptop with pre-installed Windows 8 Pro. I have completely removed Windows (after a dd backup) and repartitioned everything. Before doing that, I went to the (U)EFI menu (out of Windows 8) and chose "Legacy Mode", i. e. it behaves like a normal old BIOS. I did this because I didn't want to read into all that EFI stuff, when after my first Kubuntu installation it wouldn't just start. With Legacy mode on, it worked.

But now I wanted to use the Windows 8 Pro CDs that were delivered with my computer to install it into a virtual machine and use WinConn for some Windows apps (like error-free MS Office, for some big files where the Wine-Office crashes).
I have installed Virtualbox from the repos, but when I try to start the Win 8 installation/recovery CD in the virtual machine, it says that "VT-x" needs to be activated. This seems to be some hardware-level virtualization stuff, which normally you can enable in the BIOS (or EFI).

But how do I get into the EFI menu? In Grub, it's not available. I then tried to start with the Live-CD-USB-Stick, because according to Ubuntuusers Wiki you can go to "check my CD" and (before you press Enter) press "E" to get to the editor and type in some boot options to get to something like "insmod efifwsetup    fwsetup". Didn't work because "E" does nothing and I have no idea to open the editor there.
Another option would be to add some lines starting with "menuentry" in the grub.cfg of my installed Kubuntu. But my grub.cfg seems to have a new/other layout, not the simple old one with "menuentry" lines.

So, is there an easy way to get to the EFI firmware menu? It can't be so hard, right?

---

### Post by grahammechanical on 2014-05-19
As far as I know Linux/Ubuntu does not give us access to the BIOS/UEFI system. Maybe Windows does give that access. I do not know that either. I think that you need to press some kind of key to load the BIOS/UEFI settings utility. On my machine I tap Del as the machine boots. Other motherboards may use a different key. This motherboard setting utility does its stuff well before Grub loads. So, Grub will not give us an option to enter BIOS/UEFI settings.

Regards.

---

### Post by oldfred on 2014-05-19
Getting into UEFI is before grub loads. Often f2 but varies greatly by vendor.

 UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

If you installed in UEFI mode grub would also have a entry to revert to UEFI. But I do not know if in CSM mode it it is installed or works.
      
>  menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {

 fwsetup

 }

---

### Post by tar0n on 2014-05-20
Unfortunately, neither F2 nor the "Assist"-key work, even though I found those information in various forums.

I should say, that when Kubuntu was installing (in Legacy mode), I don't think it has left the EFI partition. But then again, everything starts. I'm a bit confused about this part. I mean, the old BIOS was just a chip and not space on the harddisk. But here, there had been this partition at the beginning.

---

### Post by oldfred on 2014-05-20
The new UEFI is a more capable chip, has a CSM or emulator for BIOS, includes NVRAM to allow it to store some settings. 
The efi partition on the drive is more like the MBR, except that you can have any number of operating systems that install boot files each into their own folder. Or like lots of MBRs.

If really interested in some of the differences:
       Technical info on Legacy BIOS and  UEFI AMI AptioMar 2012 -  20 MIn
[http://www.youtube.com/watch?v=dRMIvY7BiL4](http://www.youtube.com/watch?v=dRMIvY7BiL4)

Sometimes a total cold boot works. If a laptop turn off power and remove battery. press power switch to drain residual power. then wait a bit and reboot, trying correct key for UEFI/BIOS.

What computer/model is it?

---

### Post by norbert23 on 2014-05-20
What do you mean with "Assist" key?
Absolutely shutdown your notebook and try pressing F1, F2 or Del key. Try pressing them very often in a row.
Otherwise search the web how to access BIOS (or EFI - don't differ at this point) on your notebook.
A lot of BIOSes nowadays have a fastboot mode where the BIOS hardly 'shows' at all - so you have to be quick after switching your machine on...

---

### Post by tar0n on 2014-05-22
Thank you for your ongoing help! This is a great forum :)

I have a Sony Vaio Pro 13. It has an "Assist" button above the F keys, which normally (had I not removed the recovery partition as well) starts a special Sony program which enables you to repair your Windows or restore the computer to factory settings.

Unfortunately, I can't remove the battery, so I'm not sure how to do a "total cold boot"...

I think I had fastboot disabled before I installed Linux.

---

### Post by tar0n on 2014-05-22
Ah guys, I SOLVED IT:

I had to press this "Assist" button BEFORE starting. It is like a second Power button, which brings me to the Vaio Care menu :)

---

