---
title: "Booting Ubuntu off of a USB Stick"
date: 2008-10-15
forum: General Help
---

### Post by Polaris2008 on 2008-10-15
I have run into a rather unique issue, or at least I think it is unique.

I have installed Ubuntu 8.04 onto a Kingston DataTraveler 8GB and it boots fine when I go into the BIOS and disable my Local HDD.  When I enable the Local HDD (Which has XP Pro on it), it gets to "GRUB Loading stage1.5" and just sits there.  There is no error message afterwards.

I have a feeling I just need to tweak the menu.lst to set GRUB to boot off the new drive, since I think my BIOS re-allocates the USB Drive to a different level (hd0,0) or something to that effect, but any other advice would be helpful at this point.

---

### Post by C.S.Cameron on 2008-10-15
In BIOS is your flash drive set as first hard disk?
Have you tried hitting Esc when you get to 1.5?
I am running Ubuntu off a 8G Kingston also and have not had this problem booting from a half dozen computers.
If your root is wrong in grub/menu.lst you should get an error stating no such drive or partition.

---

### Post by C.S.Cameron on 2008-10-15
A second thought,
there are a couple different ways to identify a partition in menu.lst,
like this:
kernel     /boot/vmlinuz-2.6.27-5-generic root=UUID=487c08ce-be53-4f38-8484-13652f6c7271 ro quiet splash
or like this:
kernel     /boot/vmlinuz-2.6.27-5-generic root=/dev/sdb1 ro quiet splash
if your menu.lst is using the second method it probably uses sda1,
if so try changing it to sdb1.
If you wish to use the flash drive on multiple computers it is probably best to be using the UUID description.

---

### Post by jerome1232 on 2008-10-15
I just wanted to second using the uuid, I think it'll save you some headaches.

---

