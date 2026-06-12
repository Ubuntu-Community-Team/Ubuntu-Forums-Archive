---
title: "USB drives and Olympus camera probs"
date: 2010-12-02
forum: Hardware
---

### Post by mattfreeman on 2010-12-02
Hi, Im a first time Ubuntu (netbook version) user, on an acer netbook
I've been searching google and I can't seem to find a solution for my problems.

[B]Im finding it hard to transfer files between osx on my macbook and ubuntu on my acer netbook some usb hard drives work some don't. Any solutions?

Also I can't seem to get any recognition from Ubuntu when I plug in my Olympus camera.
I want to get the pics of the cam and onto the computer.[/B]

Where am I go going wrong?
Thanks in advance guys!

P.S
Should I move this to the multimedia category? I wasn't sure where it should go.

---

### Post by searchfgold6789 on 2010-12-02
> **mattfreeman said:**
> 
Im finding it hard to transfer files between osx on my macbook and ubuntu on my acer netbook some usb hard drives work some don't. Any solutions?
Make sure that the file system you are using is something general such as FAT32, instead of ext4. You can do this, as well as reformat the disk, using a tool such as "Disk Utility" or (preferably) GParted.
Of course, it may just be a problem of it mounting automatically. Try seeing what the disk is using GParted, and then mounting it from the command line (terminal). So, for example, if you look in GParted and the USB HD is /dev/sdc1, then you would say in the terminal:```
sudo mkdir /media/mountpoint
sudo mount /dev/sdc1 /media/mountpoint
```
> 
Also I can't seem to get any recognition from Ubuntu when I plug in my Olympus camera.
I want to get the pics of the cam and onto the computer.
Maybe Olympus has some goodies for your specific camera on their website. Of course, you could always get a USB camera card reader for your computer, or use the one already on it if it is available.
> 
P.S 
Should I move this to the multimedia category? I wasn't sure where it should go.This is the perfect place for this thread.

---

### Post by mattfreeman on 2010-12-02
OK, sounds a bit intense but I'll give it a go...
hmmm....
The camera comes up as a FAT16 Format in the OSX disc utility, is this any good?
I can't see how I can change this format.
The USB key is FAT32 Format.
Ubuntu Netbook only recognises it when it's empty. If I put a file on it from OSX then Ubuntu doesn't even recognise it.

There is a card reader in the Netbook, I put my card in and again, nothing happens.

Thanks for your help!

---

### Post by mattfreeman on 2010-12-02
OK, so I have installed Gparted and it looks great.
When I refresh devices the lights on my USB key and Camera flash but they never appear in the list.

In the list there is:

/dev/sda1 - ext4 146GB (I assume this is the Netbook internal HD)
/dev/sda2 - extended 2.93GB (I have no idea what this is, it was present before I connected devices)
/dev/sda5 - linux-swap 2.93GB (Again, no idea what it is and it was also present before I connected devices)

I'm not sure where to go from here...
Please and thank you :)

---

### Post by mattfreeman on 2010-12-03
Is anybody out there?
:p

---

