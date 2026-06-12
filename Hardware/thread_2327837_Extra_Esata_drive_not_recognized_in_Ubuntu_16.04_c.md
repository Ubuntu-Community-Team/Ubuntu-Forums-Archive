---
title: "Extra Esata drive not recognized in Ubuntu 16.04 console"
date: 2016-06-15
forum: Hardware
---

### Post by Mike E Tomlinson on 2016-06-15
I had been using Ubuntu 14. LTS
Now I have switched to 16. LTS 
 My problem is when I switch on my system I see both SSD and 1.5 TB drives in the Computer console. But the 3TB drive won't show up there
It does show up in the Disks program though.
P.S.
it did show up in 14. Lts

---

### Post by xen3 on 2016-06-17
I have no experience with Ubuntu (Unity) currently. But that is odd indeed. I hope you find a solution, but I cannot test it for you. Regular console (command line) programs to use, to test, are:

"df" -- will show any mounted filesystem
"lsblk" -- will show all the devices whether they are mounted or not, including their size, so you can identify the drive from there

eSATA actually runs as regular SATA. Therefore, there is no difference in operation; so it cannot be caused by it being an external drive.

Although it could be an issue with hot-plugging, but I don't know, haven't recently used it (I mean connecting the drive while the computer is running).

So the first question, obviously, would be: what happens if you connect the drive before you boot the system? Is that your usual use case?

Then, does it show up in "lsblk" ? Then: can you manually mount it? E.g. if you can identify it from "lsblk" as being "sdc" then it should also show its partitions. Then, if for example the first partition is sdc1, you could try to mount it with "sudo mount /dev/sdc1 /mnt" to see if that works.

---

### Post by Bucky Ball on 2016-06-18
@xen3: Have you ever used an eSATA drive in Ubuntu? What you're saying is nice in theory, but not a reality in Ubuntu. Ubuntu is notoriously problematic with eSATA in my experience and I haven't had one 'plug and play' since 10.04. 

The eSATA drive worked fine until 12.04 and I managed to get it working there eventually and [even wrote a tutorial]("http://ubuntuforums.org/showthread.php?t=2161837&highlight=esata"), but that was it. Those fixes didn't seem to work in 14.04 and I use USB3 and don't even bother with eSATA now, although I'd rather be using eSATA.

@Mike E Tomlinson: You might want to try that link above and see if it helps. Curious to know. Good luck.

---

### Post by sudodus on 2016-06-18
eSATA drives are like SATA drives for me too. I mount them manually with the command mount (unless I boot from them :-) ).

```
[COLOR="#505050"]sudo mkdir /mnt/ptxy  # only once[/COLOR]

sudo mount /dev/sdxy /mnt/ptxy
```

where x is the drive letter, y is the partition number and I have created the directory ptxy (to be used as a mount-point).

For eSATA disks that I use for backup I prefer to make a label and an entry in /etc/fstab and mount easily via the label.

---

### Post by xen3 on 2016-06-18
> **Bucky Ball said:**
> @xen3: Have you ever used an eSATA drive in Ubuntu? What you're saying is nice in theory, but not a reality in Ubuntu. Ubuntu is notoriously problematic with eSATA in my experience and I haven't had one 'plug and play' since 10.04.

uDev gives me shivers....

I really meant not hotplugging, but using it from boot. When I had a eSATA enclosure (or was using it, I still have it) I never disconnected the drive. eSATA is a very stationary technology to my mind. But I also meant that electronically, SATA and eSATA are the same. An eSATA port is just connected to a SATA port.

So what I meant to say was: don't hotplug it, just boot with it and see if it works, first.

---

### Post by Bucky Ball on 2016-06-18
In that case, as sudodus has mentioned, addit it to the fstab so it boots with the machine like an internal drive is all you should need to do.

---

### Post by sudodus on 2016-06-18
I have the boot option **noauto** in fstab, and I hotplug, mount, backup, unmount and unplug my backup disks via eSATA. I have done it for years. It works.

If you want it connected all the time, skip noauto and mount it at boot like suggested by Bucky Ball.

---

### Post by Mike E Tomlinson on 2016-06-22
sorry i didn't get back to you folks. Was out of town for a ffew days.
I haven't tried anything yet but will. When out of town I brought my laptop. 
I have ubuntu 16.04 lts on it. I tried to hook up the same drive with my docking station.
I used a USB connection. The drive shows up in Disks but it shows up as a 600 gig drive and it's a 1.5 tb
It doesn't show up in the control pannel.    I don't know if there is anything to this but someone once told me that
once you use windoze 8.1 or newer Microsoft has make so you can't get into a drive with ubuntu.  Is that true?
I'll try all your suggestions and get back to you Thank you so  very much for your suggestions.

---

### Post by Bucky Ball on 2016-06-22
> **Mike E Tomlinson said:**
> ... once you use windoze 8.1 or newer Microsoft has make so you can't get into a drive with ubuntu.  Is that true?

[FUD]("https://en.wikipedia.org/wiki/Fear,_uncertainty_and_doubt") and no doubt muttered to you by someone who didn't know any better. What was their general opinion of Linux? Yes, Linux also breaks your hardware, rewires your house while you're out, starts wars and is good for no one? Wouldn't be the first, not the last. :|

If the drive is formatted in something Linux recognises (and I'm guessing your partitions are NTFS) then there is no reason whatsoever it won't be seen. You've already said you can see it in Disks.

Do this. Open a terminal land run 

```
sudo blkid
```

Is your eSATA drive there? I thought it might be. The partition should be called '/dev/sda**', or something like that. Open another terminal and

```
sudo mkdir /mnt/test
sudo mount /dev/sda* /mnt/test
```

... where 'sda*' is the details of your partition and remembering your details maybe different, sdb5 for example, so you need to change 'sda*' to the correct details for your eSATA partition, NOT the whole drive.

Now open a file manager and go to /mnt/test. See your partition mounted and the files on it? Please confirm.

'Disks' is seeing it, it's just not mounting, that is your issue. Not the fact that Windows has performed some black art on the drive, thus rendering it impenetrable to the evil penguin-warlock Tux!

---

### Post by Mike E Tomlinson on 2016-06-23
I tried your suggestion and still can't get it to show in file manager.  This is a link to the page of the commands. you gave me.
[IMG]http://i.imgur.com/3ikQcFf.png[/IMG]
I must have messed something up I guess. 
What did I do wrong? Seems like I should take up a different hobby. 
I'm 63 and trying my hardest to understand. I hope you will be patient with me.
it took me an hour to figure out how to post that picture  LOL

---

### Post by Bucky Ball on 2016-06-23
Yes, you won't get far that way. Just run this and post back the output between code tags, don't bother with the screen shots. (See the green link in my signature for how to do code tags).

> sudo blkid

---

