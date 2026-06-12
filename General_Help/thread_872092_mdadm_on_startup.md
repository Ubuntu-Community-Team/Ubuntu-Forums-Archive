---
title: "mdadm on startup"
date: 2008-07-27
forum: General Help
---

### Post by clievers on 2008-07-27
Hi there, I've recently been working with mdadm. I installed the new mdadm-2.6.7 from source, as the one with apt-get was older. I've got so I have 3 drives in a RAID 5. My problem is this... When I boot the computer I had to run:
```
sudo modprobe md
sudo mdadm --assemble --scan
sudo mount /dev/md0 /storage/array
```
I fixed the first line (modprobe) by adding an "md" line to the /etc/modules, but after I log in I still have to run the 2nd and 3rd lines above. If I just put an entry in the /etc/fstab it fails to auto mount, as the raid assemble hasn't run yet.

I've seen various posts on the net that talk about a file in /etc/init.d/mdadm or so, but I do not have this file. I imagine this is what I need to be able to have the mdadm raid assemblies run at startup. Where can I find this file / example of how to do this? I have looked in the mdadm src directory, but I am not seeing anything obvious. :confused:

Thanks.

---

### Post by fjgaude on 2008-07-27
First off, if I understand your situation, is you have to place a line in your /etc/fstab file to auto load the array:

```
/dev/md0 /storage/array ext3 defaults 0 2
```

The config file you seek is actually in **/etc/mdadm/mdadm.conf**.

You should not need to change it unless you make changes in the array, and then know what you are doing. Some material:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)

then study **/usr/share/doc/mdadm/FAQ.gz**  and **md.txt.gz**

Keep us informed on how you are doing.

---

### Post by clievers on 2008-07-27
Yes, I had the line in my fstab, but it wouldn't work as md0 doesn't exist until I do my "mdadm --assemble ..." command. I do have the /etc/mdadm/mdadm.conf file. It looks like:

DEVICE partitions
ARRAY /dev/md0 level=raid5 num-devices=4 metadata=00.90 UUID=893d2332:9ecfb2c3:9f87f5a1:b34af474

---

### Post by fjgaude on 2008-07-28
Okay, does your array actually have this UUID as listed in the conf file: UUID=893d2332:9ecfb2c3:9f87f5a1:b34af474 

You can find the real UUID with this command:

```
sudo mdadm -D /dev/md0
```

You will note that all the drives using the -E command on one of them have the same UUID... That's how mdadm assembles the array when a --scan is done.

---

### Post by clievers on 2008-07-28
Yes, the UUID in my /etc/mdadm/mdadm.conf file is the same as the UUID shown in the mdadm -D command above:

[I]mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.91
  Creation Time : Fri Jul 25 21:08:12 2008
     Raid Level : raid5
     Array Size : 1953519872 (1863.02 GiB 2000.40 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Jul 28 09:32:58 2008
          State : clean, recovering
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

 Reshape Status : 60% complete
  Delta Devices : 1, (3->4)

           UUID : 893d2332:9ecfb2c3:9f87f5a1:b34af474
         Events : 0.390358

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       49        2      active sync   /dev/sdd1
       3       8       33        3      active sync   /dev/sdc1[/I]


Thanks.

---

### Post by clievers on 2008-07-28
(It's "recovering" as I added a fourth drive yesterday afternoon, and it's currently still reshaping my array - gosh it's slow).

---

### Post by fjgaude on 2008-07-28
I can't think of anything else to try to get the array to automount.

Good luck with the drive addition.

---

### Post by clievers on 2008-07-28
Okay, thanks for trying.
The array reshaping is going much faster now. I increased the "max" number, instead of only the "min", for the "/proc/sys/dev/raid/speed_limit_max" entry.  :D  sweet

---

### Post by clievers on 2008-07-28
Okay, this undoubtedly is probably not the correct way of doing it, and I will have to investigate to get it "proper" in the future, but at least it is working for now.

I created a file in my /etc/init.d called "mdadm-custom", with the same ownership / permissions as the other files. In this file I have:
```
#!/bin/sh

#################################
# Custom work for mdadm on boot #
#################################

# I don't specify a specific array. This will assemble all.
mdadm --assemble --scan

# Start the monitoring process
nohup mdadm --monitor --mail=cory --delay=300 /dev/md0 &
```

Then, in my /etc/rcS.d I created a symlink to this file
```
sudo ln -s ../init.d/mdadm-custom S33mdadm-custom.sh
```
where the "S33" is a number smaller then the number in front of the mountall script, in my case: S35mountall.sh. This way, my custom script will run before the mountall, which my mount info is located in my fstab.

So before it mounts, it runs my script which assembles all arrays found in my /etc/mdadm/mdadm.conf file, then it starts monitoring, then it runs the system mountall and my array is mounted. So far so good.

:D

As always, if anyone knows of the proper way to do this, please post, but at least it's working right now.

---

### Post by fjgaude on 2008-07-29
Now that we know we have a race condition, maybe this might work also:

/usr/share/initramfs-tools/init   # to stop a race condition with md
   145 maybe_break mount
   146 sleep 10
   147 log_begin_msg "Mounting root file system..."
sudo /usr/sbin/update-initramfs -uk all    # run to rebuild the image

See what you think.

---

### Post by clievers on 2008-07-29
Thanks for the reply.
I'm not sure that I ever had a race condition, because there didn't ever seem to be "anything" that would assemble the array. It would never mount, because the array didn't exist yet. By adding my script, it finally initializes the array using the mdadm assemble tool.

---

### Post by fjgaude on 2008-07-29
Okay, lost my head... good luck with **mdadm**, I've had it.

---

### Post by clievers on 2008-07-29
Well, I could also be wrong. I'm certainly no expert.
My colleague just told me to check into either mkinitrd or mkinitramfs, maybe there are some options to have it "auto" do the md. I will certainly do this at some point. An interesting problem...

Thanks

---

### Post by Krupski on 2008-07-29
> **clievers said:**
> Yes, I had the line in my fstab, but it wouldn't work as md0 doesn't exist until I do my "mdadm --assemble ..." command. I do have the /etc/mdadm/mdadm.conf file. It looks like:

DEVICE partitions
ARRAY /dev/md0 level=raid5 num-devices=4 metadata=00.90 UUID=893d2332:9ecfb2c3:9f87f5a1:b34af474

Here's a wacky... but easy way to setup a RAID device.

First, install MDADM.

Then, create your array... i.e. 'mdadm -C blah blah...'

Next, UN-install MDADM and delete the /etc/mdadm/mdadm.conf file and the /etc/mdadm directory.

At this point, you have no MDADM driver installed, no config file but drive(s) with a RAID signature on them.

Now, RE-install MDADM and *it* will auto-generate the new /etc/mdadm/mdadm.conf file... complete with the proper ARRAY line and proper GUID. It will do the "initramfs' thing for you... all by itself!

Good luck!

-- Roger

---

### Post by fjgaude on 2008-07-30
> **Krupski said:**
> Here's a wacky... but easy way to setup a RAID device.

First, install MDADM.

Then, create your array... i.e. 'mdadm -C blah blah...'

Next, UN-install MDADM and delete the /etc/mdadm/mdadm.conf file and the /etc/mdadm directory.

At this point, you have no MDADM driver installed, no config file but drive(s) with a RAID signature on them.

Now, RE-install MDADM and *it* will auto-generate the new /etc/mdadm/mdadm.conf file... complete with the proper ARRAY line and proper GUID. It will do the "initramfs' thing for you... all by itself!

Good luck!

-- Roger

Yes, this sure works... that's the way you start when you move an array to a new computer. Works everytime I tried!

---

### Post by clievers on 2008-07-30
When you guys install mdadm, do you use package manager, or do you install from source? I installed from source...

---

### Post by fjgaude on 2008-07-30
I have always installed from the repository, using apt-get... no source, just the .dep.

---

### Post by clievers on 2008-07-30
Yes, I try to do that too. But since I'm still running Feisty, the mdadm in the repository was a couple versions/releases behind, and for my critical data I wanted the newest version, as I was doing rebuilding, growing, etc.
Thanks.

---

### Post by Krupski on 2008-07-30
> **clievers said:**
> When you guys install mdadm, do you use package manager, or do you install from source? I installed from source...

You should always use 'apt-get install package-name' because it handles any dependencies the target app may have. If you install a raw .deb file, it may not work because the other stuff it "needs" isn't installed (i.e. the dependencies).

-- Roger

---

### Post by clievers on 2008-07-30
I agree with that statement. I didn't install mdadm from a .deb though, I compiled and installed from source.

---

### Post by fjgaude on 2008-07-30
Yes, and that source was the latest and likely not appropriate for Feisty. Just a thought.

When I recall all the changes that have occurred to the kernel, md and mdadm, it is a wonder that your array works at all.

---

### Post by clievers on 2008-07-30
> it is a wonder that your array works at all

... so you're saying I'm awesome?  :D   lol lol lol
first time's a charm.

---

### Post by fjgaude on 2008-07-31
Something like that, yeah!

---

### Post by prince_of_hackers on 2008-07-31
I am running 6.06 SPARC server edition, and while I have the mdadm startup script, apparently it and the mdadm.conf file aren't necessary, as the kernel auto assembles the array first thing on boot - the script only assembles arrays that are listed in mdadm.conf that aren't already running. According to one of the software RAID howto's I read, all newer kernels should do this automatically, and although I am sure it is possible to disable this capability when compiling the kernel, I wouldn't see why a stock kernel would do so...

---

### Post by thulben on 2009-09-17
> **Krupski said:**
> Here's a wacky... but easy way to setup a RAID device.

First, install MDADM.

Then, create your array... i.e. 'mdadm -C blah blah...'

Next, UN-install MDADM and delete the /etc/mdadm/mdadm.conf file and the /etc/mdadm directory.

At this point, you have no MDADM driver installed, no config file but drive(s) with a RAID signature on them.

Now, RE-install MDADM and *it* will auto-generate the new /etc/mdadm/mdadm.conf file... complete with the proper ARRAY line and proper GUID. It will do the "initramfs' thing for you... all by itself!

Good luck!

-- Roger

I know this is an old thread, but I had good luck with not quite as large a hammer.  Here's what I did:

[LIST=1]
[*]Move off /etc/mdadm/mdadm.conf
[*]dpkg-reconfigure mdadm
[/LIST]
Hope this helps someone as I've been banging my head against it for a while!

---

### Post by rickyrockrat on 2011-02-02
Here's what I did:
Make sure the correct md UUID is in etc/mdadm/mdadm.conf,
then added this line to the very beginning of do_start in the file
etc/init.d/checkfs.sh:

mdadm -A --scan

I'm running Hardy on my server where it used to not boot at all since my md array had things like var on it.

Haven't tried the mdadm re-install yet.

---

