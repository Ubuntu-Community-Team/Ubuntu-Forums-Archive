---
title: "Speed up your VAIO"
date: 2008-05-30
forum: Hardware
---

### Post by stfb on 2008-05-30
I have a VGN-AR 41S.
I have gain speed by putting "idle=poll" on the kernel options.
Now my VAIO runs faster (10 seconds less to boot for exemple).

Could someone try this on his VAIO ? (even if it's not a AR series).

Here is the way to do it:

Edit the menu.mst file by typing :
sudo vi /boot/grub/menu.lst

You should have somewhere a bloc like this near the end of this file :
## ## End Default Options ##

title           Ubuntu 8.04, kernel 2.6.24-17-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=af39a330-6cc9-4375-bf3b-7942addad39f ro quiet splash
initrd          /boot/initrd.img-2.6.24-17-generic

Add at the end of the kernel line the option "idle=poll" like this :
root=UUID=af39a330-6cc9-4375-bf3b-7942addad39f ro quiet splash idle=poll

Reboot and check if it's booting and working faster.

---

### Post by kerry_s on 2008-05-30
hmmm, never heard of that boot option. i'll give it a go in a bit.

that was not good, it pegged my cpu to full, ran the temp all the way up, so the fan then stayed on. bad juju, i rebooted 3 times just in case it was just stuck, as soon as i removed it everything is back to normal.

i'm using a vaio pcg-f430 450mhz 256mb ram.
hold on i'll do some pics.

---

### Post by rewz on 2008-05-30
Works fine for me! 

Sony Vaio VGN-NR11S



Thanks:)

---

### Post by kerry_s on 2008-05-30
yeah, i just googled " idle=poll ", it's known to burn out some cpu's.
i found " idle=halt " which seems to do almost the same thing but the temp is normal and the cpu is still set to full, i think that would be safer.

---

### Post by stfb on 2008-05-31
Here is the meaning of idle=poll :

idle=poll
Don't do power saving in the idle loop using HLT, but poll for rescheduling
event. This will make the CPUs eat a lot more power, but may be useful
to get slightly better performance in multiprocessor benchmarks. It also
makes some profiling using performance counters more accurate.
Please note that on systems with MONITOR/MWAIT support (like Intel EM64T
CPUs) this option has no performance advantage over the normal idle loop.
It may also interact badly with hyperthreading.

---

