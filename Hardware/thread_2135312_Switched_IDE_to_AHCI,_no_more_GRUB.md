---
title: "Switched IDE to AHCI, no more GRUB?"
date: 2013-04-13
forum: Hardware
---

### Post by gupti on 2013-04-13
I decided to switch the IDE setting in my BIOS to AHCI for potentially better performance. After changing it, my computer would no longer boot at all, even if I changed back to IDE. It hangs at "Loading Operating System...", so I do not even have access to GRUB at all.

I have tried using meijer.o's suggestion in [this]("http://ubuntuforums.org/showthread.php?t=1040648") thread, as well as chrooting from a live USB into my system to update the GRUB, but I'm still stuck. Updating the BIOS didn't help either, currently at version F10a.

I have a Gigabyte GA-990FXA-UD3 revision 1.0 motherboard and a Phenom II x4 965 processor, and will post the contents of what fdisk -l shows me from the live USB as soon as possible. Thanks for any help given! :)

---

### Post by oldfred on 2013-04-13
I had my system in IDE mode for years since I was booting XP. When I got my SSD, I had to turn on AHCI and then XP was finally retired. I did go back and forth a couple of times changing BIOS, but never had any issues with grub.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by gupti on 2013-04-14
Here is what boot-repair generated: [http://paste.ubuntu.com/5706716/](http://paste.ubuntu.com/5706716/)

Hopefully won't need to do a re-install...

---

### Post by ahallubuntu on 2013-04-14
~

---

### Post by gupti on 2013-04-14
Solved it! I did a boot-repair with recommended settings and gave me back GRUB with Ubuntu. A simple grub-update gave me Windows again in GRUB. All I need to do is change a few registries in Windows to be compatible with AHCI and I'll be set. Thanks for the help!

---

