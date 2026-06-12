---
title: "Installing windows xp --- ubuntu 8.10 is already present(dual boot)"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by rahul_supersaiyan on 2009-06-25
Hello everybody,

I am using hp dv2000 notebook.
I have ubuntu 8.10 installed in it.
Due to personal work, i need win xp urgently.

I put in xp SP2 cd thinking that it would rewrite MBR and i thought later on that i could fix mbr using grub to get back to ubuntu i.e. i would then have both xp and ubuntu.
The problem is that the screen goes blank after displaying the message
"Setup is inspecting the hardware ...".

I am pretty sure it is not problem of the CD as it is same with any other xp cd and also this is not my DVD reader problem.

There are 2 causes that i found relevent after googling.
1)Sata hdd is problematic with win xp SP2.
This i find a bit relevant as my notebook is a new one and uses SAtA but still i feel this is not the cause because if i had tried installing XP without ubuntu pre-installed then it would have worked...
2)I feel XP cd cannot detect the ubuntu entries in the MBR and so it goes blank. This is the one i suspect the most...

One way i found out was to install Vista and then remove vista and then install XP(vista can probably detect ubuntu entries in mbr??!!)... but it would remove my ubuntu and various other files...

I do not want to lose ubuntu.

Is there any wayout of this problem....
Any help would be greatly appreciated...

---

### Post by presence1960 on 2009-06-25
did you use gparted from the Ubuntu live CD or gparted Live cd to shrink ubuntu's partition to create space for XP. if you insert the XP CD with no unallocated or free space, or no NTFS partition the install will not be able to proceed. Windows does not know how to act in reference to other OS's filesystems.

After installing windows you will have to restore GRUB to MBR and windows bootloader will overwrite GRUB.

---

### Post by cybergalvez on 2009-06-25
just install virtualbox and run XP in that, it works great!

---

### Post by presence1960 on 2009-06-25
> **cybergalvez said:**
> just install virtualbox and run XP in that, it works great!

If your machine has enough RAM to designate to VirtualBox and you don't want  3D graphics then you should be alright with virtual box.

here is a link to virtualbox: [http://www.virtualbox.org/wiki/End-user_documentation](http://www.virtualbox.org/wiki/End-user_documentation)

---

### Post by rahul_supersaiyan on 2009-06-27
> **presence1960 said:**
> did you use gparted from the Ubuntu live CD or gparted Live cd to shrink ubuntu's partition to create space for XP. if you insert the XP CD with no unallocated or free space, or no NTFS partition the install will not be able to proceed. Windows does not know how to act in reference to other OS's filesystems.

After installing windows you will have to restore GRUB to MBR and windows bootloader will overwrite GRUB.

Firstly, i apologise for late reply...I didn't had net access...

I already have a NTFS partition of size 32.5GB...so thats not the issue...
Can u tell me a way to erase whole of MBR using gparted or anyother Application...
If i do this then probably Win XP cd can detect my HDD MBR...
Any HELP would be greatly appreciated...

One more thing Virtual Box is not an option for me as i have to use a bit heavy applications like visual studio with lots of guI... I don't think i can do away with Virtual Box...Anyways ill try it out once...

---

