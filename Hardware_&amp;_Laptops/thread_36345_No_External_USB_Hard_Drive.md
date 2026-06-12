---
title: "No External USB Hard Drive"
date: 2005-05-23
forum: Hardware &amp; Laptops
---

### Post by notorious on 2005-05-23
I am unable to access my external hard drive. I've searched for a while to solve this but no go yet.

I've tried:

-- mount /dev/sda(1-5)
... and got can't find /dev/sda (1-5) in etc/fstab or etc/mtab

-- mount /dev/sda(1-5) /mnt/extHD
... and got only root can do that

-- sudo mount /dev/sda(1-5)
... and it asks for a password and won't accept mine

Everything looked good in device manager.

---

### Post by Stealth on 2005-05-23
If you're using 5.04, its using the 2.6 kernel right? That would mean its not called sda, but I think uba...

Also, I just connected my WD External HDD, w/o any other USB devices on it, and it came out to sdb#. Didn't you get a little icon on your desktop?

---

### Post by Teren on 2005-05-23
[QUOTE=Stealth]If you're using 5.04, its using the 2.6 kernel right? That would mean its not called sda, but I think uba...

Also, I just connected my WD External HDD, w/o any other USB devices on it, and it came out to sdb#. Didn't you get a little icon on your desktop?[/QUOTE]
 Try ```

$ sudo mount -t vfat /dev/sdX /mnt/extHD

```

Change the sdX to yours.

---

### Post by notorious on 2005-05-23
I'm pretty sure it is the 2.6 kernal. There is no icon on the desktop for my external. My HD light flashes during initial start up so I know that ubuntu is finding it. Using knoppix from CD and HD had no problem with any devices at all and my external was coming up as "sda."

I tried using "uba" as suggested
.... can't find /dev/ubaX in /etc/fstab or /etc/mtab

using "sdb" I got the same thing.

Now I went
--sudo mount -t vfat /dev/sdX /mnt/extHD
... mount point /mnt/extHD does not exist

How do I create this mount point?
 ](*,)

---

### Post by Teren on 2005-05-24
[QUOTE=notorious]I'm pretty sure it is the 2.6 kernal. There is no icon on the desktop for my external. My HD light flashes during initial start up so I know that ubuntu is finding it. Using knoppix from CD and HD had no problem with any devices at all and my external was coming up as "sda."

I tried using "uba" as suggested
.... can't find /dev/ubaX in /etc/fstab or /etc/mtab

using "sdb" I got the same thing.

Now I went
--sudo mount -t vfat /dev/sdX /mnt/extHD
... mount point /mnt/extHD does not exist

How do I create this mount point?
 ](*,)[/QUOTE]
 ```

$ mkdir /mnt/extHF

```

;)

---

### Post by notorious on 2005-05-25
What I had to do was plug it into one of the back usb ports and away it went. All partitions are now shown on the desktop. I tried linspire too to see if I could get my external to go but still had the same problems. Windows and Knoppix allowed me to use my drive from the front usb ports. This makes me think that there's a driver issue with ubuntu & linspire. All my usb ports are v2 so I checked the device manager listing. Being plugged into the back It was showing my drive being plugged into usb 2. There were 3 listings for usb1.1 controllers so I'm assuming that ubuntu is recognizing the front ports as 1.1 which may be creating the conflict and not allowing me to use my drive from the front.

Any suggestions?

 :-)  -- I would like to thank everyone whose responded, thanks for the info --  \\:D/

---

