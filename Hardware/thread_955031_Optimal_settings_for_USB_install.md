---
title: "Optimal settings for USB install?"
date: 2008-10-21
forum: Hardware
---

### Post by abeowitz on 2008-10-21
I've install Ubuntu 8.10 on a 4G USB stick.  Seems to be going quite well, though performance is a bit slow, since this stick is only about 18MB/s read.

Things like noatime and data=writeback seem to help a bit.

I also found that hdparm -a0 seems to help, too.  My guess is that a large read-ahead would impact performance a bit by getting sectors it doesn't need.

Ideally, I want the kernel to cache as much as possible.  

Question is, how to do that?  

What sysctl, /sys, /proc settings might assist in this?  Any way to delay writes longer?

So, ultimately, any ideas on optimizing for a low latency, low throughput disk io instead of medium latency, high throughput?

---

### Post by abeowitz on 2008-10-24
OK, here's some cool stuffs for running off of USB sticks...

Using a RAMDISK, you can bypass a lot of 'temporary' disk IO, minimizing USB access AND minimizing wear leveling erasing.

Provided you have some extra RAM.  (These tweaks are useful for ALL systems, not just USB.)


**tmpfs**

tmpfs is a ramdisk of sorts.

Add this line to /etc/fstab
tmpfs           /tmp            tmpfs       auto,size=512M,uid=0,gid=0,mode=1777 0 0 

and mount it.  (Best not to do during an X session, as /tmp is in use.)

Also symlink /var/tmp there too.


(You may have to make tmpfs larger if you make temp CDROM images using /tmp...)


**Firefox**
Change your browser's disk cache to /tmp
[http://kb.mozillazine.org/Browser.cache.disk.parent_directory](http://kb.mozillazine.org/Browser.cache.disk.parent_directory)

Great for privacy and performance.



**apt**

All those package downloads are temporary.  Why waste megabytes of erase cycles on these?  

Move the apt cache dir to /tmp and the only disk writes will be the actual updates.  (And your apt-get upgrade will be faster, too.)

mkdir -p /tmp/archives/partial
mv /var/cache/apt/archives /var/cache/apt/archives_backup
ln -s /tmp/archives /var/cache/apt/archives

Note: add 'mkdir -p /tmp/archives/partial' to /etc/rc.local to make it 'permanant'

Now, do your apt-get updates/installs, etc.

When done, do an apt-get clean to release the space back to RAM.


**ELEVATOR**
Using elevator=noop seems to help with running on a USB stick...  Will benchmark with bonnie++ when I get a chance.

---

