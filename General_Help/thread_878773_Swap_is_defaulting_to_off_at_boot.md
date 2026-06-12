---
title: "Swap is defaulting to off at boot"
date: 2008-08-03
forum: General Help
---

### Post by dai_vernon on 2008-08-03
When I log in, I always start my system monitor, Conky.  It is set to monitor my swap among other things, and it aways begins at detecting 0 bytes of swap,

Going to the Partition Editor I can simply right-click Swapon on the swap partition and it is fine, conky detects it and it functions as it should.  Why is it defaulting to off?  How can I fix it?  My swap is very large, over 5 and a half gigs (sized by the hardy live CD), might that be a problem?

---

### Post by unutbu on 2008-08-03
Please post
```

cat /etc/fstab
```

---

### Post by coffeecat on 2008-08-03
> **dai_vernon said:**
> My swap is very large, over 5 and a half gigs (sized by the hardy live CD), might that be a problem?

Did you resize it after installing Ubuntu? If you did, the UUID will have changed and the UUID in the swap line in fstab will be wrong. As well as the contents of /etc/fstab that unutbu asked for, post the output of:

```
sudo blkid -c /dev/null
```

---

### Post by dai_vernon on 2008-08-03
First one

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=feb6854d-1a90-4b07-a955-a12e1c6f46aa /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=0540fdb5-93ad-46a9-aa60-1130c1d65180 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Second one

/dev/sda1: UUID="42BE45A5BE4591F9" TYPE="ntfs" 
/dev/sda2: UUID="2C88743C8874071C" LABEL="PRESARIO_RP" TYPE="ntfs" 
/dev/sda5: UUID="feb6854d-1a90-4b07-a955-a12e1c6f46aa" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="159c41a2-4206-4c05-9c99-4d536c989c9d" 

I did attempt to resize it because I felt that 5.6 gigs of swap was a bit excessive, but changed it back. Looking at this output, the UUIDs for the swap don't match.  Which is right?; how do I change it to be correct?

---

### Post by coffeecat on 2008-08-03
> **dai_vernon said:**
> Looking at this output, the UUIDs for the swap don't match.  Which is right?; how do I change it to be correct?

The output from blkid is the correct one. The one in fstab is what is was before you resized it.

Do this:

```
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
```The first line gives you a backup in case something goes wrong. With the second, you open fstab with the text editor where you can change the UUID to the correct one. Save and next time you reboot you should be OK.

---

### Post by dai_vernon on 2008-08-03
At least on this boot, the problem has been fixed!  Thank you so much!

---

