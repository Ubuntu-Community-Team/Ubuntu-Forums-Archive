---
title: "xubuntu on satellite doesn't read usb drive?"
date: 2008-08-21
forum: Hardware
---

### Post by Daverobb on 2008-08-21
I'm running xubuntu 7.10 on a toshiba satellite laptop with a celeron processor. Xubuntu doesn't recognize my 200gig usb drive at all and i wondering if anyone knows how i can mount it??  This help would be greatly appreciated as it would allow me to migrate a lot of files into a safer environment as i think the laptop is on it's way out.

---

### Post by adrien214 on 2008-08-21
can you post the outcome of the following command in your terminal (after pluging your drive) :

[COLOR="Silver"]...:~$[/COLOR] lsusb

then we can figure out if xubuntu sees your hdd...

---

### Post by Daverobb on 2008-08-24
sorry for taking so long - had another power problem with the laptop but now back.
```
[CODE]
lsusb
Bus 001 Device 002: ID 067b:2506 Prolific Technology, Inc. 
Bus 001 Device 001: ID 0000:0000  
```[/CODE]

It's interesting - the first entry is the flash drive - I tried he drive on a desktop using ubuntu and it shows up as the same.  So why do I not have any access to it through the desktop?

---

### Post by adrien214 on 2008-08-30
do you have any other USB hardware hooked to your laptop ?
I think that your first entry refers to you usb drive (you are talking about a flash dirve..)

Check that you have the ntfs-3g packages to manage the NTFS drives:

```
sudo apt-get update
sudo apt-get install ntfs-3g ntfsprogs
```

Try to unplug and plug your external drive and see if any harddisk icon shows up on the desktop.

If it doesn't, try to force mount you drive:

open a terminal and type:
```

sudo mkdir /media/ext-hdd
sudo chmod 777 /media/ext-hdd
sudo mount -t ntfs-3g /dev/sdb1 /media/hd-ntfs -o force
```

Your external drive should be now visible on the desktop, if it's not, check in your /media folder (at the root of the file system)

To unmount your device, open a terminal and type:

```
sudo umount /media/ext-hdd
```

 or right click on the icon and unmount...

please note that you can name your external hard drive anything you want, just replace* ext-hdd *in the above commands. This post is a condensed version of [this one]("https://answers.launchpad.net/ubuntu/+question/16872").

---

