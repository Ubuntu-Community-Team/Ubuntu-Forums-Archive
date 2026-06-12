---
title: "Ubuntu on USB. Can't see rest of USB?"
date: 2010-08-02
forum: Hardware
---

### Post by tkott on 2010-08-02
Hi,

I successfully installed Ubuntu 10.04 on my usb drive using the instructions [here]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/"). However, since I have a large usb key, and I would like to use it to hold data files from my windows machines as well, I would like to use the rest of the space on the key as well. 

From what I understand, I would have to mount the USB that is already powering Ubuntu. Is this at all possible, or is the rest of the filespace on the USB key "lost"?

TIA

---

### Post by tkott on 2010-08-02
Of course, as soon as I post, I figure out that the filesystem is available under /cdrom/. Now my question is whether there is a way to make specific folders within that folders to be readable without a sudo command. I think what I need to do is change the owner from root to ubuntu. 

I tried ```
sudo chown ubuntu:ubuntu Files/
``` but that just returned ```
chown: changing ownership of `Files/': Operation not permitted
```.

Any thoughts on this? Or will I have to constantly "sudo" my way around?

TIA

---

### Post by Fafler on 2010-08-03
Right now you are just running a live CD of the pen drive. Why not make a "real" installation instead? Just boot from the CD with the pen drive connected and choose it as the destination drive. If you know your way around the partitioner, make a FAT32 partition in the beginning of the drive for data for data and a EXT3 (EXT2 is better for use on flash drives because it doesn't use a journal as therefore do fewer writes but it has to be cleanly unmounted and USB drives tend to be physically removed every now and then so i stick with EXT3). Also go without a swap partition. Remember to format the FAT32 partition and edit you /etc/fstab to include the option noatime for your root filesystem* and you are ready to go :-D

* In my case, i would have to change 

/dev/mapper/oxygen-root /               ext4    errors=remount-ro 0       1

to

/dev/mapper/oxygen-root /               ext4    errors=remount-ro,noatime 0       1

---

### Post by tkott on 2010-08-03
@Fafler,

You're probably right that the easiest way to go is to just install it on my usb key. Will booting from the USB key still work without changing my windows laptop setup? (I.e., select boot from USB and things will work?)

I also assume that I can partition things as necessary before the installer?

> **Fafler said:**
>  Also go without a swap partition. Remember to  format the FAT32 partition and edit you /etc/fstab to include the option  noatime for your root filesystem* and you are ready to go :-D

* In my case, i would have to change 

/dev/mapper/oxygen-root /               ext4    errors=remount-ro 0       1

to

/dev/mapper/oxygen-root /               ext4    errors=remount-ro,noatime 0       1

I presume that the Ubuntu installer has some "advanced" options to set things like no swap partition?

Also, when would I change the /etc/fstab file: post install, right?

Thanks

---

### Post by snowpine on 2010-08-03
I would suggest, rather than following a tutorial from some random 3rd party website, that you follow the official instructions on the Ubuntu site:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Note that the official Ubuntu USB Creator has a "persistence" option that will allow you to save documents, settings, and installed applciations onto your flash drive.

---

### Post by tkott on 2010-08-03
> **snowpine said:**
> I would suggest, rather than following a tutorial from some random 3rd party website, that you follow the official instructions on the Ubuntu site:

[https://help.ubuntu.com/community/Installation/FromUSBStick ]("https://help.ubuntu.com/community/Installation/FromUSBStick")

The instructions I used started [here]("http://www.ubuntu.com/desktop/get-ubuntu/download") (I selected windows, usb key, how to) but I neglected to write that. I would imagine that these are pretty formal instructions. 

> **snowpine said:**
> Note that the official Ubuntu USB Creator has a  "persistence" option that will allow you to save documents, settings,  and installed applciations onto your flash drive.

Yes, that is what I tried at first. However, that doesn't allow me to read write from Windows, which is the point here. 

Thanks for the link, it actually references [these instructions]("http://mintarticles.com/read/operating-systems-articles/how-to-install-portable-linux-ubuntu-on-a-bootable-usb-flash-drive-from-sun-virtualbox,13641/"), which will be what I try next.

---

### Post by oldfred on 2010-08-03
I just installed to the USB as if it was a second drive.

Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

Standard full install to flash or SSD Lucid would be similar to Karmic:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
See post #19 C.S.Cameron ( But I do not unplug hard drive, just use advanced button to install to USB) 
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)

---

### Post by tkott on 2010-08-03
> **oldfred said:**
> I just installed to the USB as if it was a second drive.

Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

Standard full install to flash or SSD Lucid would be similar to Karmic:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
See post #19 C.S.Cameron ( But I do not unplug hard drive, just use advanced button to install to USB) 
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)

Thanks, all those links are super useful. Gonna install now, we'll see how it goes!

---

