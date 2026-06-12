---
title: "Accidently installed/upgraded to Ubuntu 9.04 server edition.......please help"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by benwesting on 2009-04-21
As the title suggests i very stupidly upgraded from ubuntu 8.10 to 9.04 and didnt read the details explaining that it was just the server edition. Normally i would just obtain a new ubuntu disc but the problem is my disc drive doesnt work and hasnt for a while. I do however have an external harddrive with ubuntu 8.10 on it. Im connected to the internet. Ive tried so many commands andf got no where. Im admittedly a novice at Linux and any help whatsoever with this would be greatly appreciated. I really dont want to lose all my data on my laptop for a 2nd time in a year :(

---

### Post by mikewhatever on 2009-04-21
Is there a problem with 9.04 server?

---

### Post by davetv on 2009-04-21
If you mean that you have no desktop window manager then try this

sudo aptitude install ubuntu-desktop

---

### Post by benwesting on 2009-04-21
There doesnt appear to be any desktop or GUI! Im pretty much a noob at all this linux stuff but ive tried everything to get the desktop back and it just wont happen. Keeps coming up with its failed to fetch anything.

---

### Post by benwesting on 2009-04-21
Yep ive tried that, it comes back with E: i wasnt able to locate file for the usplash package. This might mean you need to manually fix this package. 
E: internal error: couldnt list packages to download.

Amongst alot of other stuff lol its begins to build the dependency tree before that always say 0 newly installed and 507 not upgraded.

I shouldnt be allowed near computers sometimes:rolleyes:

---

### Post by coffeecat on 2009-04-21
Did you try 'sudo apt-get update' before trying to install ubuntu-desktop?

---

### Post by benwesting on 2009-04-21
I did yes and no luck im afraid

---

### Post by benwesting on 2009-04-21
I appreciate people's input so far but any more suggestions from anyone cos im stumped still!

---

### Post by coffeecat on 2009-04-21
> **benwesting said:**
> I appreciate people's input so far but any more suggestions from anyone cos im stumped still!

I'm sorry I haven't posted back before, but without a working optical drive I'm rather short of ideas. So, a bit of brainstorming....

Does the laptop support booting from USB? If so, is there any chance of your borrowing a USB CD drive? Because if you can, you could boot from a live CD, copy the data files from the laptop HD to a USB drive in the live environment, and then do a fresh install. Failing that...

> **benwesting said:**
> I do however have an external harddrive with ubuntu 8.10 on it.

I'm not quite sure what you mean by that. Can you boot from it? If so you will able to copy your data files from the internal HD to an external device.

If you can do that then you can think about reinstalling. One way would be to download the net install iso (which is only 11MB). There must be some way of getting that onto a USB device in a bootable form - probably with unetbootin, although I have no experience of this. If you can boot from the net install iso, you can do a complete install with a text-based installer - very similar to the alternate CD installer. I've done it myself - it's quite easy. You need to be sure that the ethernet connection works, and it takes about a couple of hours because it has to download everything that makes up a standard installation.

Let me know if that's a possibilty and I'll give you the link to the iso download page and also do a bit of digging to see how to convert an iso to a bootable USB device.

---

### Post by benwesting on 2009-04-23
Thanks for the reply mate, busy at work at the moment but ill get online this afternoon and give what you said a go, will let you know how i get on! I think i can boot form my external hard drive as it shows up in the BIOS so.....
I didnt think about plugging the ethernet cable back into the laptop as i have WiFi, so will plug that in to!

---

### Post by benwesting on 2009-04-24
Right, ive done it, i have a new ubuntu 8.10 desktop on my laptop. BUT, i need help with a few more things if possible please....

1. It only boots from the new USB flash drive i had to buy, does anyone know how i change this?
2. I seem to have a load of different partitions now asd my hard drive is def smasller, is there anyway to delete the partitions i do not need.
3. Before i delete those partitions i need to try and recover old files form the previous ubuntu install i had, is that possible?

Thanks Coffeecat for previous help, anymore advice is extremely welcome!!

---

### Post by coffeecat on 2009-04-24
1. Yes
2. Yes
3. Yes

:wink:

For the first, do you mean that if you do not have the usb drive plugged in, nothing happens, but that if the usb drive is plugged in, it boot into the hard disc installation. If so, it means that grub has been set up to boot from the usb drive, and that there's nothing in the mbr of the internal drive. We just need to know which partition is your root partition, after which you can run a couple of grub commands, and that should reconfigure grub to boot from the internal disc.

Open a terminal and post the output of the following command. Post the output in [noparse]```

```[/noparse] tags to keep the formatting, otherwise it's a mess. Keep the usb flash drive plugged in. I want to see what's on that as well.

```
sudo fdisk -l
```For 2, install Gparted from the repositories. Once installed, you'll find it in System > Adminstration > Partition Editor. But before deleting anything, let's see what's on your HD.

For 3, simply go to the Places menu. You should see entries somewhere in there for the partitions other than the ones mounted at bootup. Simply click on the one you want and it should be automounted and a Nautilus window will open. Then you can copy off files to an external drive.

---

### Post by benwesting on 2009-04-24
Im just upgrading to 9.04 atm, as soon as its finished ill try all of the above! I really do appreciate your help mate, its nice to know there is a great little community with people willing to take time out to help others! Id be lost otherwise! And now when i get my laptop in a few months ill dual boot windows and linux instead of just having windows!

---

### Post by benwesting on 2009-04-24
The only other problem is that the desktop continuosly freezes, which is the reason i tried to update in the 1st place and got into this place. Its just done it again and i have to turn the pwoer switch off and start again. Its just random freezes. Hoping myabe upgrade to 9.04 will help it, if it stops freezing enough to upgrade :)

And i just spoke to soon, as it forze whilst upgrading its gone back to just the text edition and no desktop again. Im d/l KUBUNTU 9.04 now and will give that a go i think and see how we get on! Does the same apply in regards to partition deleting and data recovery on Kubuntu?

---

### Post by benwesting on 2009-04-28
> Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa5bc8f6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 1989 MB, 1989148672 bytes
62 heads, 62 sectors/track, 1010 cylinders
Units = cylinders of 3844 * 512 = 1968128 bytes
Disk identifier: 0xb0bcd68e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *      838545      902718   123339962   78  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(518, 102, 15) logical=(838544, 58, 50)
Partition 1 has different physical/logical endings:
     phys=(743, 0, 62) logical=(902717, 41, 15)
Partition 1 does not end on cylinder boundary.
/dev/sdb2          112610      314401   387841909+  10  OPUS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(205, 7, 0) logical=(112609, 34, 14)
Partition 2 has different physical/logical endings:
     phys=(920, 235, 50) logical=(314400, 21, 34)
Partition 2 does not end on cylinder boundary.
/dev/sdb3          486359      985639   959615034   8b  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(260, 125, 54) logical=(486358, 38, 56)
Partition 3 has different physical/logical endings:
     phys=(893, 46, 60) logical=(985638, 2, 35)
Partition 3 does not end on cylinder boundary.
/dev/sdb4           88791       90956     4161558    a  OS/2 Boot Manager
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(269, 111, 50) logical=(88790, 44, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(90955, 57, 50)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


Sorry its taken me a while to reply. Anyway, this is what it says!

---

