---
title: "Grub Error 22"
date: 2008-10-20
forum: General Help
---

### Post by GuiGuy on 2008-10-20
Hi all,
I'm mucking about with setting up xubuntu on some hardware leftovers. The HDD is a SAMSUNG 80GB SATA drive, which I think used to be  a WindowsXP boot disk.

I allowed the xubuntu installer to do its own thing, ie I allocated all of the HDD to xubuntu. 

On a reboot I am getting grub error 22, which seems to relate to a missing or damaged MBR

I tried fixing the MBR using the Acronis recovery  system, but the "Copy MBR" option does not enabled. 

Any help on getting the disk back and getting it to boot?

Many TIA

Cheers

---

### Post by caljohnsmith on 2008-10-20
Do you get the Grub error before seeing a Grub menu or after you see the Grub menu and choose Ubuntu? And do you see anything about "Press ESC to see menu" on start up? 

How about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump

```
And we can work from there. :)

---

### Post by GuiGuy on 2008-10-20
> **caljohnsmith said:**
> 

How about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump

```
And we can work from there. :)

Thanks for the post. I was getting the error immediately after the "Grub Loading..," message. IE, no menu.

Anyway, I did a fixmbr from a WinXP CD. Seems to be OK now. 

A question though; doesn't the Ubuntu installer sort out a working MBR?

Thanks

---

### Post by caljohnsmith on 2008-10-20
> **GuiGuy said:**
> Thanks for the post. I was getting the error immediately after the "Grub Loading..," message. IE, no menu.

Anyway, I did a fixmbr from a WinXP CD. Seems to be OK now. 

A question though; doesn't the Ubuntu installer sort out a working MBR?

Thanks
Putting Windows boot code into the MBR with "fixmbr" will allow you to boot directly into Windows, but didn't you still want to be able to boot into Xubuntu? I thought your original intention was to get Grub working so you could boot either Windows or Xubuntu.

---

### Post by GuiGuy on 2008-10-21
> **caljohnsmith said:**
> Putting Windows boot code into the MBR with "fixmbr" will allow you to boot directly into Windows, but didn't you still want to be able to boot into Xubuntu? I thought your original intention was to get Grub working so you could boot either Windows or Xubuntu.

It's Xubuntu only. However I'm generally too stupid to be playing with linux (see sig line) :biggrin: so couldn't figure out how to get the MBR back on the disk except with fixmbr from the WinXP install.

Anyway, it worked but it would be useful to know how to do it with linux (ubuntu) only. 

regards

---

