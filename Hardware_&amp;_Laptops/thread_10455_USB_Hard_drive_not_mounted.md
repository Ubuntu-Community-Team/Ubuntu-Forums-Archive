---
title: "USB Hard drive not mounted"
date: 2005-01-07
forum: Hardware &amp; Laptops
---

### Post by enquiry on 2005-01-07
I have a Freecom Classic 160 GB external USB hard drive (fat32 formated). It works perfectly under Windows XP.

Under Ubuntu it is not auto mounted when I plug it in. I can't get it mounted manually either. It does however appear as a USB mass storage interface in the Device Manager.

The command dmesg gives me the following output: ```
new high speed USB device using address 3
usb 4-6: control timeout on ep0in
usb 4-6: string descriptor 0 read error: -71
[...]
usb-storage: probe of 4-6:1.0 failed with error -1
usb 4-6: string descriptor 0 read error: -71
[...]

```
What can I do to make the hard drive work under Ubuntu? I am somewhat new to Linux, and not a very advanced user.

All help is much appreciated.

---

### Post by philip41 on 2005-01-09
I have the exact same drive, and the same problem,I have searched and searched, and found many similar threads. I have tried most of the solutions but so far to no avail.
I am sure the problem is user rather than system, as i am new to Linux also( so new i feel as though i have never used a pc before.).

My dmesg is as below.


> 
usb 3-3: new high speed USB device using address 7
usb 3-3: control timeout on ep0in
usb 3-3: string descriptor 0 read error: -71
usb 3-3: string descriptor 0 read error: -71
usb 3-3: string descriptor 0 read error: -71
usb 3-3: string descriptor 0 read error: -71
usb 3-3: string descriptor 0 read error: -71
usb-storage: probe of 3-3:1.0 failed with error -1

p.s this is my first post, so hello to all.

---

### Post by enquiry on 2005-01-09
I tried getting it to work with the Ubuntu LiveCD. It didn't mount automaticaly, but I did however get it to work by mounting it manually ( mount -t vfat /dev/sda1 /mnt/sda1 ).

In my installed version I don't have the device sda1 in /dev. I've tried making it with ./MAKEDEV sda1, but then I get the message ```
./MAKEDEV: don't know how to make device "sda1"
```

---

### Post by philip41 on 2005-01-09
[QUOTE=enquiry]I tried getting it to work with the Ubuntu LiveCD. It didn't mount automaticaly, but I did however get it to work by mounting it manually ( mount -t vfat /dev/sda1 /mnt/sda1 ).[/quote]

Where do i find out the bit about SDA1 or whatever, because when i type as you have above i just get.
(mount point /mnt/sda1 does not exist)


> In my installed version I don't have the device sda1 in /dev. I've tried making it with ./MAKEDEV sda1, but then I get the message ```
./MAKEDEV: don't know how to make device "sda1"
```

Same here.

Below is what i see in device manager.

---

### Post by enquiry on 2005-01-10
[QUOTE=philip41]Where do i find out the bit about SDA1 or whatever, because when i type as you have above i just get.
(mount point /mnt/sda1 does not exist)[/QUOTE]
On the LiveCD the mount point /mnt/sda1 exists. My installed version does not have this mount point by default, so if I want it I would have to create it first ( sudo mkdir /mnt/sda1 ). The problem here (I guess) is mounting a device that does not appear in /dev

---

### Post by philip41 on 2005-01-10
[QUOTE=enquiry]On the LiveCD the mount point /mnt/sda1 exists. My installed version does not have this mount point by default, so if I want it I would have to create it first ( sudo mkdir /mnt/sda1 ). The problem here (I guess) is mounting a device that does not appear in /dev[/QUOTE]

Thanks i will give that a go then.

---

### Post by enquiry on 2005-01-10
[QUOTE=philip41]Thanks i will give that a go then.[/QUOTE]
Perhaps I was a bit unclear, but creating a mount point does not solve the problem. I still can't make the hard drive mount under my installed versjon of Ubuntu (on the LiveCD, however, it mounts without any problems).

I really do think we need help from someone more experienced if we are to solve this problem ...  :-(

---

### Post by philip41 on 2005-01-10
[QUOTE=enquiry]Perhaps I was a bit unclear, but creating a mount point does not solve the problem. I still can't make the hard drive mount under my installed versjon of Ubuntu. 

I really do think we need help from someone more experienced if we are to solve this problem ...  :-([/QUOTE]

I have to agree.

But for me it is not to much of a problem now as today i bought a machine specificaly for linux :D , but i still have Ubuntu on my other machine so i will still from time to time try to solve the problem.

---

### Post by wazoo on 2005-01-10
Usually, there are at least four things you have to do with a USB drive.

1. Find out where it is. Plug it in, and type in a terminal window:
             fdisk -l     (that's an 'el')

The device you're looking for should show up. In my case it is indeed /dev/sda1 -- and I'm afraid I don't know what else it would be, or how to make one. But let's see it comes up as /dev/doobedoo (it won't!).

2. Create a directory for it, as noted above in the thread:

            $sudo mkdir /mnt/usbdrive       (or whatever you want to call it, so long as it doesn't conflict with something else)

3. Mount the device from step 1 to the directory in step 2.  For instance:

            mnt -tvfat  /dev/doobedoo mnt/usbdrive 

(the -tvfat is to tell Ubuntu what type of file system it is)

Good luck!

---

### Post by enquiry on 2005-01-11
Thank you wazoo, but unfortunately it still doesn't work.

sudo fdisk -l makes a list of available disc partitions. The USB hard drive does not show up in this list (no wonder, as it doesn't even appear in /dev), so still no luck  :cry:

---

### Post by wulf on 2005-01-11
Did it ever work? Over Christmas, I tried my brother's USB memory stick. The first time I used it, everything happened automatically. Thereafter, it was a bit of a pain - no automounting, although I did manage to manually access it.

Right now I'm borrowing a digital multitrack (Fostex MR-8) which has a USB output. Again, when I first connected it up (last night), everything happened automatically (*/dev/sda1* appeared, it got mounted to */media/sda* and a folder opened pointing to that application). Later on, after recording a new track, I tried again and got nothing.

My hacked together solution was to kill *gnome-volume-manager*, restart it and try again, which worked (although it was getting late and I'm a bit hazy on the details, so I won't try to lay down any roadmap of what to do). Did you have similar symptoms (worked first time, not again) or is yours a different class of problem?

Wulf

---

### Post by enquiry on 2005-01-11
[QUOTE=wulf]Did it ever work? Over Christmas, I tried my brother's USB memory stick. The first time I used it, everything happened automatically. Thereafter, it was a bit of a pain - no automounting, although I did manage to manually access it.

[...]

Did you have similar symptoms (worked first time, not again) or is yours a different class of problem?[/QUOTE]Actually I belive it did work the very first time I plugged it in. Before you mentioned it, I was uncertain if it had actually worked, or perhaps I was hallucinating or something  8-[ , 'cause it never worked again for no apparent reason.

---

### Post by philip41 on 2005-01-11
[QUOTE=enquiry]Thank you wazoo, but unfortunately it still doesn't work.

sudo fdisk -l makes a list of available disc partitions. The USB hard drive does not show up in this list (no wonder, as it doesn't even appear in /dev), so still no luck  :cry:[/QUOTE]

Same result here with mine.

---

### Post by viuks on 2005-02-03
I have Freecom 80Gb drive and same problem - not listed /dev/sda. It was not problem before, when I used Mepis. It was not problem, when I installed ubuntu. But it is problem now, when I reinstalled ubuntu. Maybe it was, becouse I used ubuntu hoary before, and it just do this problem in warty. I will try to put on upgrade my ubuntu in this night. Maybe it will give some good results.

---

### Post by viuks on 2005-02-04
Yes, I updated tu hoary, and now there is no problems get Freecom hdd running. I will try on my other laptop update hotplug and/or kernel in warty. I have feeling that hotplug is the one.

---

### Post by viuks on 2005-02-08
Try install newest version of pmount!

---

### Post by enquiry on 2005-02-13
[QUOTE=viuks]Try install newest version of pmount![/QUOTE]
 I have installed Hoary on an other HDD, just to test, and now the Freecom hard drive works very well! I will try installing a newer version of pmount under Warty, and see what happens. I don't think installing Hoary as the primary OS is a good idea at this point. I have found it to still be quite buggy, so I'll wait till April.

---

### Post by jmather on 2005-02-22
Could someone explain perhaps how you can install the newest version of pmount on Warty?  I have a freecom drive and I'm having the same issues....I'm not planning on upgrading to Hoary until it is released....?????

---

