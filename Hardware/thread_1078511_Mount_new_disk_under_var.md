---
title: "Mount new disk under /var"
date: 2009-02-23
forum: Hardware
---

### Post by mobcdi on 2009-02-23
Hi there,

I'm trying to configure my ubuntu 8.04 so that a new disk is mounted in the /var folder, that is to say I would like all files folders created in /var to be stored on a second disk (200GB). I've install GParted to handle the partitioning of the disk but I want to make sure any steps I do occur in the correct order. 

GParted shows the 2nd disk as /dev/sdb but I have not created any partitions on it yet.

My question is because the /var folder already exists and contains about 700MB of files and folders as part of the ubuntu installation what steps do I need to carry out to enable me to mount my new disk there without breaking anything?

---

### Post by mobcdi on 2009-02-24
I guess what I'm asking is how do I stop all activity on the var folders, copy all the files to a temp location, mount the new drive and copy the old files back before starting all the services that might be accessing.

Does ubuntu 8.04 have the same as "safe mood" in windows?

---

### Post by taurus on 2009-02-24
Try using the LiveCD then.

---

### Post by mobcdi on 2009-02-25
> **taurus said:**
> Try using the LiveCD then.

Can you expand on how I might use the LiveCD in that way?

---

### Post by JW3 on 2009-02-25
> **mobcdi said:**
> Can you expand on how I might use the LiveCD in that way?

1) boot from livecd (or knoppix, or any other cd-only distro).
2) mount both disks. Now the /var from your original installation is inactive (since you are running the livecd!), and you can't break anything that's running and using var (since nothing is using it!)
3) copy the var folder from the original disk to the new disk. Use cp -a to preserve metadata.
4) move the var to var-bck (should something go wrong)
5) modify the fstab on the original hard disk so that it mounts a partition from the new disk as /var
6) reboot from the hard drive

j.

---

### Post by mobcdi on 2009-02-25
I partitions sdb using gparted then booted from a liveCD and after remembering that there was 3 "disks" now (liveCD memory, original disk sda, new disk sdb) I started work

This is the change I made to my fstab file on sda but it doesn't seem to mount sdb correctly for me
#Begin mount
/dev/sdb1 /var ext3 defaults 0 2
#End mount

I did manage to copy my original /var over to the new drive (sdb) and there is only 1 partition of type ext3 on it.

I also deleted my /var folder on sda (after I took a copy) so all I need to do (I think) is get the correct entry in the fstab file

---

