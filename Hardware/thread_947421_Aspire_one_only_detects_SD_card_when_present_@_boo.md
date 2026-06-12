---
title: "Aspire one only detects SD card when present @ boot time"
date: 2008-10-14
forum: Hardware
---

### Post by Reech.out on 2008-10-14
Hi,

I recently bought an aspire one netbook, and of course the pre-installed Linpus was quickly replaced by an ubuntu hardy.

I followed the guide at [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)
And everything I tried so far worked, except for the Card reader.

When an SD card is present at boot time ubuntu detects it and I can freely switch it for any other in the same slot,
if however I insert a card in the second slot nothing happens.

If I boot without an SD card inserted it won't detect cards inserted in either slot.
(the /dev/mmcblk0p1 entry, which is mounted when booting with SD inserted, isn't even there)

Also if I run ```
setpci -d 197b:2381 AE=47
``` I get:```
setpci: Warning no devices selected for `AE=47`.
```


I hope someone here can point me in the right direction?:confused:

---

### Post by Reech.out on 2008-10-15
Almost solved,

For some reason the "***/usr/local/sbin/jmb38x_d3e.sh***" doesn't run on startup.
Which is why "***setpci -d 197b:2381 AE=47***" gave me an error.

```
wget [http://petaramesh.org/public/arc/projects/AcerOne_Ubuntu/jmb38x_d3e.sh](http://petaramesh.org/public/arc/projects/AcerOne_Ubuntu/jmb38x_d3e.sh)
sudo chmod 754 jmb38x_d3e.sh
sudo mv jmb38x_d3e.sh /usr/local/sbin/

```
I assumed this piece of code made sure the jmb38x_d3e.sh would run on startup...

Do I need to create a symlink in /etc/rc.d ,or is there a more elegant solution?

---

