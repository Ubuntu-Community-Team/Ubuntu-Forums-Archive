---
title: "Problem with Install Ubuntu, sidux and windows vista"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by miros84 on 2008-12-23
Hello everybody. I have a question a little complicated. I had installed ubuntu and windows vista to one computer. Everything was going well. I Could choose one or the other OS to boot. After I installed sidux  I can start only sidux. The ubuntu and the windows are still there, appearing in the group manager, but they did not start, there any way to edit this for me to start again ubuntu and windows vista?

---

### Post by lemming465 on 2008-12-26
Some Linux installers are politer about picking up other OS variants than others; evidently sidux is one of the ruder ones.  For purposes of this discussion I'll pretend you have a disk layout like

/dev/sda1 - NTFS - Vista C:
/dev/sda2 - ext3 - Ubuntu /
/dev/sda3 - swap - Ubuntu/sidux
/dev/sda4 - extended
/dev/sda5 - ext3 - Sidux /

If you post the output from **sudo blkid; sudo fdisk -lu; df -m** we can give you advice that actually matches your disk layout.

I'm going to assume that you are using the Grub bootloader on the MBR of /dev/sda.
In **sudo gedit /boot/grub/menu.lst** you need to add paragraphs for the other OS's.  The Vista one would look like:```

title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

For the Ubuntu one, you can either do something similar ```

title		chain to ubuntu
root		(hd0,1)
chainloader	+1

```

or you can mount the ubuntu partition and copy out of its /boot/grub/menu.lst file, e.g. ```

sudo -i
mkdir /media/sda2
mount /dev/sda2 /media/sda2
less /media/sda2/boot/grub/menu.lst

```
You're looking for a chunk corresponding to your favorite kernel; it probably looks something like: ```

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		6d4473c7-72c8-4bfa-b7e5-06300feb2f33
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6d4473c7-72c8-4bfa-b7e5-06300feb2f33 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

```
You'll have to find the appropriate UUID for your filesystem; mine won't do you any good :-(  Remember that Grub calls disks "hd", not "sd", and numbers disks from 0, not "a", and partitions from 0, not 1.  So Linux sda3 is Grub (hd0,2).

---

### Post by miros84 on 2008-12-27
Thank you very much. Very usefull information. I could fix my problem yet. I only want to ask if that's correctly: 

title		chain to ubuntu
root		(hd0,1)
chainloader	+1

or must be that:
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		6d4473c7-72c8-4bfa-b7e5-06300feb2f33
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6d4473c7-72c8-4bfa-b7e5-06300feb2f33 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

 I meen if I put only the root if it´s enought?

---

### Post by caljohnsmith on 2008-12-27
Since it is unclear what OS controls you booting process, miros84, how about doing:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your problem might be.

---

### Post by lemming465 on 2008-12-28
The *root (hd0,1) / chainloader +1* might work, but only if your Ubuntu install was on sda2, and the original grub stage 1.5 went there. I suggested it because it was easy and had a good likelihood of working.  If your original Ubuntu install was on some other partition then the ",1" in the (hd0,1) will have to be adjusted; you want one less than the ubuntu partition number seen in the output of *sudo fdisk -lu*.

If the simple solution doesn't work, you'll need to migrate a paragraph from your ubuntu grub menu.lst into your sidux one.  The *title Ubuntu 8.10, kernel 2.6.27-11-generic ...* example I quoted was from my system and won't work at all on yours, as the kernel version, UUID, and initrd paths will all be wrong.  The reason I included it was to help you recognize yours when you went looking for it.  You have to use your stuff (see previous post with the mount & less).

---

