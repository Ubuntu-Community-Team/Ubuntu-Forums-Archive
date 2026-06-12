---
title: "GRUB Questions"
date: 2008-08-02
forum: General Help
---

### Post by RATM_Owns on 2008-08-02
Since I'm the worst at starting off a thread or anything like that (at least I'm aware of it) I'll get to the point.

1) How do I make it so it automatically boots to Ubuntu and skips GRUB unless I hold ESC (I'm pretty sure that's how it works)

2) I have tons of other entries for other kernels, should I use the newer kernel and remove the older ones or keep the one I have?
There's 2.6.24-16 through 2.6.24-20 with normal boot and recovery mode for all of them.

3) I have Windows Vista entries on there still. I deleted my Windoze partition and grew Ubuntu. However, it still has Windows for (hd0,1), which is the same as Ubuntu. I'm pretty sure I should delete the two entries?

4) I have two memtest things which are pretty much exactly the same. The first one and second have the same name and both point to the same place. So should I delete the second one?

4) I don't know if this really goes into GRUB, but when I deleted Windoze and grew Ubuntu to fill the space, Ubuntu was still /dev/sda2, how could I move it to /dev/sda1 and fix GRUB to use that?

Thanks.

---

### Post by geirha on 2008-08-02
1. Edit /boot/grub/menu.lst (gksu gedit /boot/grub/menu.lst) and remove the comment (marked with red) on the line that says ```
[COLOR="Red"]#[/COLOR]hiddenmenu
```

2. Uninstall the kernels you don't want and they'll automatically be removed from the menu. uninstall the appropriate packages starting with "linux-image-".

3. Yep, remove it. Edit it like in answer 1, and remove the windows section (should be about five lines, starting with "title Windows ..."

4. If they are equal, delete one of them. Odd that there are two of them though.

4. Whether it is name /dev/sda1 or /dev/sda2 is irrelevant to ubuntu. If you want to change it, you have to delete /dev/sda2 and create a new one. I would not recommend that. Just keep it as is.

---

### Post by Elfy on 2008-08-02
> **RATM_Owns said:**
> Since I'm the worst at starting off a thread or anything like that (at least I'm aware of it) I'll get to the point.

1) How do I make it so it automatically boots to Ubuntu and skips GRUB unless I hold ESC (I'm pretty sure that's how it works)

2) I have tons of other entries for other kernels, should I use the newer kernel and remove the older ones or keep the one I have?
There's 2.6.24-16 through 2.6.24-20 with normal boot and recovery mode for all of them.

3) I have Windows Vista entries on there still. I deleted my Windoze partition and grew Ubuntu. However, it still has Windows for (hd0,1), which is the same as Ubuntu. I'm pretty sure I should delete the two entries?

4) I have two memtest things which are pretty much exactly the same. The first one and second have the same name and both point to the same place. So should I delete the second one?

4) I don't know if this really goes into GRUB, but when I deleted Windoze and grew Ubuntu to fill the space, Ubuntu was still /dev/sda2, how could I move it to /dev/sda1 and fix GRUB to use that?

Thanks.

1 - edit the menu list and remove the # from #hidden menu

2 - remove the old images from synaptic, it will update grub - search for ```
linux-image
``` - I would keep at the minimum 2 newest ones

3 - you can remove the windows items if they no longer apply just by deleting them

4 - you can remove one of the memtests

4 - I have 1 partition on one of my partitions labelled as sdb2 - I would not worry too much if I was you

To backup and edit menu list

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.0208
gksudo gedit /boot/grub/menu.lst
```

---

### Post by mikewhatever on 2008-08-02
> **RATM_Owns said:**
> 
[I]Before you start, backup with **sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup**.
[/I]
1) How do I make it so it automatically boots to Ubuntu and skips GRUB unless I hold ESC (I'm pretty sure that's how it works)

[I]Open grub menu for editing with **gksudo gedit /boot/grub/menu.lst** and locate the following sections near the top:

[QUOTE]## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
[/I]

*Set timeout to 5 and remove the hash mark (#) from hiddenmenu.*

2) I have tons of other entries for other kernels, should I use the newer kernel and remove the older ones or keep the one I have?
There's 2.6.24-16 through 2.6.24-20 with normal boot and recovery mode for all of them.

*Open Synaptic and search for linux-image. Locate the kernels you don't need and mark them for removal. Grub will be updated automatically.*

3) I have Windows Vista entries on there still. I deleted my Windoze partition and grew Ubuntu. However, it still has Windows for (hd0,1), which is the same as Ubuntu. I'm pretty sure I should delete the two entries?

*They are safe to delete.*

4) I have two memtest things which are pretty much exactly the same. The first one and second have the same name and both point to the same place. So should I delete the second one?

Not sure. I think every new kernel adds three entries (regular, recovery, memtest). Deleting redundant kernels may get rid of that too.

4) I don't know if this really goes into GRUB, but when I deleted Windoze and grew Ubuntu to fill the space, Ubuntu was still /dev/sda2, how could I move it to /dev/sda1 and fix GRUB to use that?

*Why? What's wrong with it on sda2?*

---

### Post by RATM_Owns on 2008-08-02
My menu.lst is a little weird then. Doesn't have a #hiddenmenu line. So I changed the timeout to 5 and added hiddenmenu on the line under it.

```
default 0
timeout 10
password --md5 $1$Y7u8U$55CKWvXfFTdDmV9ov23zp1

title Ubuntu 8.04.1 Hardy Heron
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=a7a7f143-00f6-4936-972a-932170109674 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04.1 Hardy Heron (recovery mode)
lock
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=a7a7f143-00f6-4936-972a-932170109674 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root 

title Windows Vista
root (hd0,1)
chainloader +1
savedefault
makeactive

title Windows Vista
root (hd0,1)
chainloader +1
savedefault
makeactive

title Ubuntu 8.04.1, kernel 2.6.24-20-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-20-generic root=UUID=a7a7f143-00f6-4936-972a-932170109674 ro quiet splash
initrd /boot/initrd.img-2.6.24-20-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-20-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-20-generic root=UUID=a7a7f143-00f6-4936-972a-932170109674 ro single
initrd /boot/initrd.img-2.6.24-20-generic

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=a7a7f143-00f6-4936-972a-932170109674 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=a7a7f143-00f6-4936-972a-932170109674 ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, kernel 2.6.24-18-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=a7a7f143-00f6-4936-972a-932170109674 ro quiet splash
initrd /boot/initrd.img-2.6.24-18-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=a7a7f143-00f6-4936-972a-932170109674 ro single
initrd /boot/initrd.img-2.6.24-18-generic

title Ubuntu 8.04.1, kernel 2.6.24-17-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-17-generic root=UUID=a7a7f143-00f6-4936-972a-932170109674 ro quiet splash
initrd /boot/initrd.img-2.6.24-17-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-17-generic root=UUID=a7a7f143-00f6-4936-972a-932170109674 ro single
initrd /boot/initrd.img-2.6.24-17-generic

title Ubuntu 8.04.1, kernel 2.6.24-16-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=a7a7f143-00f6-4936-972a-932170109674 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=a7a7f143-00f6-4936-972a-932170109674 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
quiet
```

---

### Post by geirha on 2008-08-02
Ah, your menu.lst is heavily edited, and the AUTOMAGIC-comments are gone, so ubuntu doesn't know how to update it anymore. I recommend you rename your current menu.lst and then run ```
sudo update-grub
``` in a terminal. If it doesn't find /boot/grub/menu.lst, it will create a new one and add all currently installed kernels.

---

### Post by RATM_Owns on 2008-08-02
I just rebooted into the new kernel and now it's 800x600 screen resolution instead of 1440x900. And Ubuntu can't detect my graphics card.

How can I fix this? -_-

---

### Post by geirha on 2008-08-02
In your previous menu.lst, you had -16 as the default kernel. Now you probably have -20. Am I right? Try selecting one of the older kernels at the boot menu and see if they work. 

As far as I know. the -20-kernel is not released yet. You probably have the hardy-proposed repository enabled. Disable the hardy-proposed repository and uninstall the -20-kernel for now.

---

### Post by RATM_Owns on 2008-08-02
Oh. Well I uninstalled the older kernels.
I do have -19 still though.
But I fixed it. Thank you envyng-gtk.

---

