---
title: "mdadm to convert sda1(+sdb1) to md1"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by iaw4 on 2009-03-09
Simple mdadm question (before I destroy my data):

I have two working partitions on my working hard drive /dev/sda.  I bought an identical drive and hooked it into /dev/sdb.  I now want to convert my sda partitions into raid with sdb.

sfdisk /dev/sda | sfdisk /dev/sdb made the partition tables the same.

do I use "create" or "assemble"?

if I do mdadm --create /dev/md1 --level=1 /dev/sda1 /dev/sdb1, will mdadm be smart enough to know that /dev/sda1 is the master copy, and mirror to /dev/sdb1?

/iaw

---

### Post by lha on 2009-03-09
Please, read [/usr/share/doc/mdadm/rootraiddoc.97.html]("file:///usr/share/doc/mdadm/rootraiddoc.97.html"). It describes the process which converts your system to one with raid. You can start from 2.2 Verify your RAID savvy Kernel. (rootraiddoc.97.html is part of the mdadm package.)

---

### Post by iaw4 on 2009-03-10
thanks.  I did, and I can now sort of boot.  my problem is figuring out how to get raid1 into the kernel or initrd.

my preference would have been to have md and raid1 in the kernel, but I am afraid that most of the ubuntu mindset/distro are about modules, and I don't want to screw up on further upgrades.  I wish ubuntu had an addon that distributed an initrd that was raid savvy.

so, is the standard recommended "ubuntu way" for everyone to build their own initrd?

/iaw

---

### Post by iaw4 on 2009-03-10
to clarify:

when I tell grub at bootup to use as the root device /dev/md1, I drop into busybox and find that (although raid is now in the /proc/modules that I see), /dev/md1 (my root drive) does not exist.

I now boot to the old hard drive partition /dev/sda1, which ironically [in its /etc/fstab] then sets the new degraded raid array of /dev/md1 to be the root partition.  this works.

I believe this is because I have to create my own initrd.  another question---where is mkinitrd on ubuntu?

sincerely,

/iaw

---

### Post by lha on 2009-03-10
> **iaw4 said:**
> 
I believe this is because I have to create my own initrd.  another question---where is mkinitrd on ubuntu?

Take a look at mkinitramfs.

I didn't have to create my own initrd's. I checked my initramfs-tools configuration files, and they did not contain explicitly any raid configuration. Therefore, I believe that a simple
```

sudo update-initramfs -u

```
might create the initrd you need. In case it doesn't, you can force modules into initrd by listing them in /etc/initramfs-tools/modules.

---

### Post by iaw4 on 2009-03-11
thanks for the pointers.  I did create my new initramfs.

alas, something weird is still going on here.  I am still dropping into initramfs.  now, /proc/modules tells me that md_mod and raid1 are in the modules (good), but /proc/md* still does not show up.   Grrrr... what else can possibly go wrong when it comes to linux putting up the appropriate device?  does the initramfs need special udev or devfs system configurations?

I only hope that ubuntu 9* is going to have RAID1 in its standard, non-alternate installation method as an option.  this is painful.

more help still highly appreciated.

regards,

/iaw

---

### Post by lha on 2009-03-11
Which version of Ubuntu are you using? Which versions of packages initramfs-tools and mdadm you have installed? Some versions don't support booting with degraded arrays without tweaking: [https://help.ubuntu.com/community/Installation/SoftwareRAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID"). Check the changelogs (/usr/share/doc/initramfs-tools/changelog.gz and /usr/share/doc/mdadm/changelog.Debian.gz) to make sure that your version supports booting from degraded raid arrays.

---

### Post by iaw4 on 2009-03-12
thanks for sticking with me.  I should have the latest versions of everything.  In this case,

  initramfs-tools (0.92bubuntu16) intrepid-proposed; urgency=low
  mdadm (2.6.7-3ubuntu8) intrepid; urgency=low

I don't think that I have this problem here.  when it dropped to the initramfs, I tried

/sbin/mdadm --assemble --scan

but this gives three errors:

CREATE user root not found
CREATE group disk not found
No arrays found in config file or automatically

I also looked at the /etc/mdadm/mdadm.conf file.  It is the identical as that used by the successful-booting-from-sda1-with-/dev/md1-as-root version.  how does madm figure out from /proc/partition what sd*'s are part of a RAID array?  it does not seem to contain this sort of information, which I would guess is required to assemble the array.

Still stymied.

regards, /iaw



> **lha said:**
> Which version of Ubuntu are you using? Which versions of packages initramfs-tools and mdadm you have installed? Some versions don't support booting with degraded arrays without tweaking: [https://help.ubuntu.com/community/Installation/SoftwareRAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID"). 

Check the changelogs (/usr/share/doc/initramfs-tools/changelog.gz and /usr/share/doc/mdadm/changelog.Debian.gz) to make sure that your version supports booting from degraded raid arrays.

---

### Post by lha on 2009-03-12
> **iaw4 said:**
> thanks for sticking with me.  I should have the latest versions of everything.  In this case,

  initramfs-tools (0.92bubuntu16) intrepid-proposed; urgency=low
  mdadm (2.6.7-3ubuntu8) intrepid; urgency=low


Ok, these have the ability to boot from degraded arrays. However, it might not be enabled. You could run 
```
sudo dpkg-reconfigure mdadm
```
and enable it.

> **iaw4 said:**
> 
I don't think that I have this problem here. when it dropped to the initramfs, I tried

/sbin/mdadm --assemble --scan

but this gives three errors:

CREATE user root not found
CREATE group disk not found
No arrays found in config file or automatically

I also looked at the /etc/mdadm/mdadm.conf file.  It is the identical as that used by the successful-booting-from-sda1-with-/dev/md1-as-root version. 

I admit that it is possible that your problem lies somewhere else, but let us still try some things.

It is no wonder that
```
/sbin/mdadm --assemble --scan
```
doesn't work. When you boot your computer, it initially mounts the initrd.img as root file system - in effect, your root file system does not contain mdadm.conf at the time when Ubuntu tries to assemble md devices. Try if
```
mdadm --examine --scan | mdadm --assemble --scan
```
does something useful.

Are your raid partitions of type fd (Linux raid autodetect)? You can verify this by running
```
sudo fdisk -l
```

> **iaw4 said:**
> how does madm figure out from /proc/partition what sd*'s are part of a RAID array?  it does not seem to contain this sort of information, which I would guess is required to assemble the array.

My conception of this issue is that each partition which is part of a md device contains the information that is required.

---

### Post by iaw4 on 2009-03-12
thanks again lha.  the light is beginning to shine.

first, the sudo dpkg-reconfigure mdadm indeed told me that I was configured for booting only with a non-degraded array.  (this is a strange default, because the usual idea of RAID is not to shut down when one drive goes south.)  I fixed this.

then, I rebooted.  dropped into busybox initramfs again.  now, I tried your next suggestion:

mdadm --examine --scan

and voila, the md drives are here.  unfortunately, piping this into mdadm --assmble --scan did not work.  fortunately, the following did work:

mdadm --examine --scan >> /etc/mdadm/mdadm.conf ; mdadm --assemble /dev/md1

exit, and the reboot proceeds just fine.

now I just need to figure out how to get the initramfs to do this by itself.  not as easy as I first thought.  after the full boot, I cd to /etc/initranfs-tools/conf.d, and see whether I can throw the output of the "mdadm --examine --scan" onto the end of the file /etc/initramfs-tools/conf.d/mdadm (there is no mdadm/mdadm.conf, but this file seems to be the same.)   I do

 mdadm --examine --scan >> /etc/initramfs-tools/conf.d/mdadm

and then

  update-initramfs -u

now, this command immediately reports the error:

update-initramfs: Generating /boot/initrd.img-2.6.27-11-generic
/etc/initramfs-tools/conf.d/mdadm: 19: ARRAY: not found

[the fd byte is indeed set on the single partition that is the degraded 1-partition root partition.]

so, now the question boils down to what the recommended way is to get ubuntu to mdadm-examine+scan and then use it.  Is there a way to get it into the /etc/mdadm/mdadm.conf file that sits inside the initrd, for example?

regards,

/iaw

---

### Post by lha on 2009-03-12
I'm not sure what would be the best thing to do in this situation. Maybe you should follow the instructions in [https://help.ubuntu.com/community/Installation/SoftwareRAID#Updating startup script]("https://help.ubuntu.com/community/Installation/SoftwareRAID#Updating startup script"). (Just the Updating startup script-part.) I am, however, puzzled by the mixed information that is given about booting degraded arrays.

---

