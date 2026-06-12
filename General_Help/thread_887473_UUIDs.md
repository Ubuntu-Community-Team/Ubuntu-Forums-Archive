---
title: "UUIDs"
date: 2008-08-12
forum: General Help
---

### Post by jeepers on 2008-08-12
I am getting ready to Tfr my ubuntu to another HDD, and was reading a howto that recommends getting rid of UUIDs and just having /dev/, Heres my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=5da5bc25-127c-4cd2-ba6d-553533320186 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=b64f0e02-6cbe-4895-ae9c-4dbb4942107a none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

**Do i just delete them or is there a procedure for removing them**, I will also have to remove them from GRUB menu.lst as per this:

# ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=5da5bc25-127c-4cd2-ba6d-553533320186 ro


cheers

---

### Post by Nepherte on 2008-08-12
I'm not really sure why you'd want to replace UUIDs with /dev entries. The UUIDs are unique, /dev are not.

---

### Post by hyper_ch on 2008-08-12
(1) when posting any config file or terminal output use [noparse]```

```[/noparse] as brackets around. Makes it easier to read

(2) Lines starting with
```

#

```
are comments. This means they have no influence on the configuration.

(3) By looking at the fstab, how would you now read all the individual entries and how would you modify them?

[(4) I don't get your problem about the UUIDs... they work wonderful)]

---

### Post by Jose Catre-Vandis on 2008-08-12
For ease of understanding what is going on, while you get setup, probably best to go the /dev/sd* route for your fstab. Once you are up and running you can discover the correct UUID for your new HDD and replace the /dev/sd* entry if you want to. When adding or reconfiguring HDDs I tend to use /dev lines.

---

### Post by nazish on 2008-08-12
easiest way to transfer is to replace the uuid's with their corresponding device id's.
 
e.g.
# /dev/sdc1
UUID=5da5bc25-127c-4cd2-ba6d-553533320186 / ext3 relatime,errors=remount-ro 0 1
replace this > UUID=5da5bc25-127c-4cd2-ba6d-553533320186 with /dev/sdc1
 
you can always generate uuid's later. Also in your grub menu.lst file replace the corresponding uuid's with the device id's.

---

### Post by mcduck on 2008-08-12
Actually if you clone the disk with "dd" it should keep the same UUIDs for partitions..

---

### Post by jeepers on 2008-08-14
Thanks for the replies...i have been reading a "howto" on transfering Ubuntu from one drive to another drive, and the recommendation was to get rid of the UUID's, apparently the "can" cause problems when trying to boot of the new drive.

There are quit a few programs available that will Clone a HDD, Just determining which one is the best/easiest to use is the problem.

I have my Ubuntu set up the way i want it now, and shudder at the thought of having to do a re-install.

Actually now that i think of it...is it possible to do a backup of all my stuff to a NTFS HDD ( i have a 250Gb Downloads HDD) and then after i install Ubuntu on my new Drive, reinstall all my Ubuntu stuff...from my Downloads drive. ?.

The reason i'm asking is that i have been reading some horror stories of people who have used DD to clone drives.

cheers

---

