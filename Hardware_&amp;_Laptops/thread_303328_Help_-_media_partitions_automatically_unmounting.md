---
title: "Help - media partitions automatically unmounting"
date: 2006-11-20
forum: Hardware &amp; Laptops
---

### Post by closey on 2006-11-20
Hi all,

I'm having a bit of trouble with my partitions in Ubuntu Edgy Eft (upgraded from Dapper Drake). I can successfully mount them at boot into the /media/shared and /media/windows locations as I have defined in the /etc/fstab file, but they seem to get unmounted after I don't use them for a period of time. I would prefer very much so if these would stay mounted! In Dapper I didn't seem to have this problem.

Here's my /etc/fstab entries:
```
# /dev/sda1 -- converted during upgrade to edgy
UUID=582628EC24C0CEDB /mnt/windows ntfs defaults,nls=utf8,umask=000,gid=46 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=42bba046-a8c8-40a8-b705-76b915eec8e3 /mnt/shared ext3 defaults 0 1
```

These partitions are on the same SATA hard disk as the Ubuntu install. When I mount the partitions into the /mnt directory instead, I don't seem to get the problem.

Any help would be appreciated, thanks :)

---

### Post by hal10000 on 2006-11-20
Hi, you say that your partitions are to be mounted into [COLOR="Red"]/media/share[/COLOR] and [COLOR="Red"]/media/windows[/COLOR], but your fstab says it is mounted into [COLOR="Red"]/mnt/shared[/COLOR] and [COLOR="Red"]/mnt/windows[/COLOR]. I wonder if you may find them in the /mnt rather than in /media?

---

### Post by closey on 2006-11-20
> **hal10000 said:**
> Hi, you say that your partitions are to be mounted into [COLOR="Red"]/media/share[/COLOR] and [COLOR="Red"]/media/windows[/COLOR], but your fstab says it is mounted into [COLOR="Red"]/mnt/shared[/COLOR] and [COLOR="Red"]/mnt/windows[/COLOR]. I wonder if you may find them in the /mnt rather than in /media?

Ah, my bad - I have them set to /mnt now because in /media they get unmounted automatically. I'd prefer to have them in /media but if I put them in there they do get unmounted. In /media it's better because they then appear in the desktop and other places in nautilus.

---

### Post by hal10000 on 2006-11-20
That's very strange, maybe it has something to do with the automount system; try [COLOR=Red]mount [COLOR=DimGray]in a xterm and look if there is an entry like **auto** or something like this.
As a workaround you may bookmark the mountpoint (mnt/share and /mnt/windows) in nautilus.
[/COLOR][/COLOR]

---

### Post by closey on 2006-11-20
Yeah there's no extra parameters... from the output of 'mount':
```
/dev/sda5 on /media/shared type ext3 (rw)
```

The only thing related to auto mounting is the /smb automount I have set up. I might try fiddling with power settings in case something odd is happening in there.

---

### Post by closey on 2007-01-20
> **closey said:**
> Yeah there's no extra parameters... from the output of 'mount':
```
/dev/sda5 on /media/shared type ext3 (rw)
```

The only thing related to auto mounting is the /smb automount I have set up. I might try fiddling with power settings in case something odd is happening in there.

I think the problem here was that k3b was incorrectly accessing the wrong SCSI devices. This bug has been fixed in the latest pre-release I think. All good now, I think :)

---

