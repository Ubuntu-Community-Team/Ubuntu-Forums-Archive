---
title: "Harddisk Spin Down while booting from SD-Card"
date: 2009-03-09
forum: Hardware
---

### Post by Inkululeko on 2009-03-09
Hello!
I installed Ubuntu 8.10 on a SD-Card in order to avoid high activity of my laptop harddisk, which is quite noisy. Because the BIOS of my laptop doesn't support booting from the internal SD-Card Reader, I created a boot partition on the internal harddisk with the kernel and initrd on it. Booting works well. Unfortunately, the harddisk is not used for some time, while loading hardware drivers. The harddisk goes into sleep mode. When in the next stage of booting, something accesses the harddisk, it wakes up again. 
It would be really nice, if this short sleep-mode period of the harddisk could be avoided. Is there any trick (kernel option, ....) with which I could set up the spin-down timeout of the harddisk? I guess hdparm doesn't work in such an early stage of booting?

jules

---

### Post by Inkululeko on 2009-03-10
Maybe this information helps:

with bootchart, you can see a little I/O acitivty peak, when the harddisk wakes up (at 26 seconds) :

[http://dl.getdropbox.com/u/140367/bootchart_spindown.png]("http://dl.getdropbox.com/u/140367/bootchart_spindown.png")

dmesg gives some information about what is happening at 26 seconds, but I don't understand why this wakes up the harddisk:

[http://dl.getdropbox.com/u/140367/dmesg_spindown.txt]("http://dl.getdropbox.com/u/140367/dmesg_spindown.txt")

any ideas?

---

### Post by Inkululeko on 2009-03-12
Obviously, the script "vol_id" does cause the wakeup. Intersting is, that it is not excecuted everytime. I didn't find out wich service is using vol_id at startup, so I tried to keep the harddisk busy with smartctl till the point is reached, where vol_id is mostly excecuted. Is there a more elegant way to keep the device busy for a certain time? Doing something useless like fetching smart-information is rather an ugly solution...

jules

---

