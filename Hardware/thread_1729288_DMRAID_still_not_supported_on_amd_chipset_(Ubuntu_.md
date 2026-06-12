---
title: "DMRAID still not supported on amd chipset? (Ubuntu 11.04 beta)"
date: 2011-04-14
forum: Hardware
---

### Post by alraz on 2011-04-14
Hello.

Just installed Ubuntu 11.04 beta 2 and noticed that it does no longer throw an error when running DMRAID with my amd chipset, however, it won't recognize any of my partitions:

```

alraz@ubuntu-x4:~$ sudo dmraid -r
/dev/sdd: pdc, "pdc_cehihgiebg", stripe, ok, 1498031530 sectors, data@ 0
/dev/sdc: pdc, "pdc_cehihgiebg", stripe, ok, 1498031530 sectors, data@ 0
/dev/sdb: pdc, "pdc_cehihgiebg", stripe, ok, 1498031530 sectors, data@ 0


```

This raid is made of 3x1.5TB disks, so, it's beyound the 2+GB limit for MBR. I created the partitions under windows a long time ago as "GPT". If I run some other disk utilities like gparted, they recognize the raid as a 2.09 TiB disk.

I've read in other forums that GPT is not very well supported by dmraid, but those posts are from the end of 2009, so... I'm curious... does anybory know what's the current state?

---

### Post by srs5694 on 2011-04-15
I haven't done much with RAID and GPT, but I've seen suggestions that using the kpartx program can overcome the problems. This tool creates device file entries for the device you specify, so if your RAID device is, say, /dev/mapper/pdc_cehihgiebg, you'd run:

```

kpartx /dev/mapper/pdc_cehihgiebg

```

That will then create the necessary partition entries.

I'm not sure about integrating this into your startup system, though (I'm not positive, but I think the results of kpartx will go away when you reboot, so you'd need to run it automatically on each boot). You might want to try a forum search on "kpartx"; that should produce some posts with more details.

---

### Post by alraz on 2011-04-15
Thanks for the info, sadly, it did nothing to help me :(

```

alraz@ubuntu-x4:~$ sudo kpartx -l /dev/mapper/pdc_cehihgiebg 
alraz@ubuntu-x4:~$ sudo kpartx -a /dev/mapper/pdc_cehihgiebg 
alraz@ubuntu-x4:~$ sudo kpartx -l /dev/mapper/pdc_cehihgiebg 
alraz@ubuntu-x4:~$ ls /dev/mapper/
control  pdc_cehihgiebg

```

Maybe there is something else I have to do... (dmraid was already running)

By the way: this is not a boot RAID, I use it as data storage only, and have another disk with my partitions for OSes.

Finally, I also tried this:
```

alraz@ubuntu-x4:~$ sudo kpartx -l -v -g /dev/mapper/pdc_cehihgiebg 
alraz@ubuntu-x4:~$ 

```

---

### Post by srs5694 on 2011-04-16
I'm out of ideas, then. With any luck somebody with more RAID experience than I will be able to suggest something.

---

### Post by alraz on 2011-04-16
Thanks anyways ;)

---

### Post by ronparent on 2011-04-16
You didn't say what raid level you are using on the array. A three disk array is most often raid 5. If that were the case dmraid -l indicates that raid 5 is not supported for the pdc chip set. In any event it is certainly not a stripe.

---

### Post by alraz on 2011-04-16
Hello.

That's true, I forgot to mention that this is a raid 0, not 5.

Maybe Windows did a mess of my partitions... wouldn't be the first time...

---

