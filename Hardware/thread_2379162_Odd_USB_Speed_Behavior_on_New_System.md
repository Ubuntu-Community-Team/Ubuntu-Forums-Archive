---
title: "Odd USB Speed Behavior on New System"
date: 2017-12-01
forum: Hardware
---

### Post by rebeltaz on 2017-12-01
On my old (10.04LTS) system, I had a 2tb USB hard drive connected that was auto-mounted via fstab using the following command:

```
UUID=df479888-2010-485f-a620-0fab6516fab6     /mnt/multimedia         ext4    auto,users,rw,exec,sync 0       0
```

which worked perfectly. 60-90MB/sec transfer speeds. I transferred everything to a new system (with 16.04LTS) and the transfer speeds to this same drive dropped to 2MB/sec. I changed the fstab entry to:

```
UUID=df479888-2010-485f-a620-0fab6516fab6     /mnt/multimedia ext4    defaults        0       0
``` 

and the speed increased to about 7MB/sec. I noticed that if I plugged another drive in, speeds were up to about 90MB/sec. So I deactivated the fstab entry, rebooted the computer and just plugged the drive in. Sure enough, speeds were back up to ~90MB/sec like they should be. That's great, but I need this auto-mounted to a specific mount point so it can be accessed over my network by other devices.

Any idea why this is acting this way?

-=[EDIT]=-

OK... this is odd. After all of the above messing around, I resinstated the fstab entry so that I could at least access the drive until I/we could figure this out. When I started, the USB drive was assigned to /dev/sdc1. Now, after I rebooted the computer with the reinstated fstab entry, the USB drive is showing up as /dev/sda1 instead, with the main drive as /dev/sdb, and the speed is up where it should be. So... two questions... 1) why did the /dev assignment change and B) does it hurt anything for the main drive to be showing up as /dev/sdb instead of the usual sda?

---

### Post by rebeltaz on 2017-12-14
No, huh?

---

### Post by Autodave on 2017-12-14
Can I answer your question? Not a chance: sorry. However, if it ain't broken, don't fix it.  

If it is being accessed like needed, I would leave it alone.

---

### Post by rebeltaz on 2017-12-14
> **Autodave said:**
> However, if it ain't broken, don't fix it.  

lol... that is my standard response, but... in this case I tend to agree with two caveats. I am the kind of person how really likes that "why" question... why things do what they do or don't do what they should. That's how I learn how to fix future issues. Secondly, I just want to be sure that the main drive being labeled anything other than sda is ok.

---

### Post by Autodave on 2017-12-14
My Linux drive is sdb, Win10 is sda.  And I have 600 gig on the Win drive that I also use for Linux.

I am with you when you say you like to know the "why" for future reference. That is partly why I looked at this post again: was hoping someone had given a much better answer than I gave. :-)

---

