---
title: "Mounting a new drive"
date: 2010-03-06
forum: Hardware
---

### Post by avanrens on 2010-03-06
I have installed a new drive and need instructions to mount it. drive is /dev/sdc/ formated in ext 4

---

### Post by byStanderone on 2010-03-06
...have you set the mountpoint of your ext4 to / ?

---

### Post by avanrens on 2010-03-06
No I have not set the mount point I have not installed a new drive in ubuntu before

---

### Post by -kg- on 2010-03-06
Why would he want to mount it as root?  The only partition you should mount as root is your root partition.  This is another drive that he's installed...I assume for storage of some kind, since it is "dev/sdc."  I assume that since you indicate there is only one partition on it, that partition would be "sdc1."

You will need to assign a mount point, depending on what you want to use the partition as, and you will need to edit your fstab file to include it as mountable.

A good tutorial on this is found at [How To FSTAB.]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by byStanderone on 2010-03-06
...got your point kg...perhaps that's the peculiarity of an ext4 format, at least at this stage of its development, ...tho am not sure bout this...would search bout it...cause personally am not using ext4 for the time being...

---

### Post by avanrens on 2010-03-06
Thank you

---

