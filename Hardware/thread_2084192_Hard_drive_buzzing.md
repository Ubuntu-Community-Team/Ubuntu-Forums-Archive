---
title: "Hard drive buzzing"
date: 2012-11-14
forum: Hardware
---

### Post by Chris_82 on 2012-11-14
Hi all,

after connecting an hard drive to an USB adaptor, it first started retracting its head every two seconds, then ran fine but added a high pitch buzzing sound.
[You can listen to it here.]("http://yourlisten.com/channel/content/16927235/hard_disk_buzzing")
According to Palimpsest there are no bad sectors. Booting on the disk runs with normal speed.

It almost sounds like it is touching inside but then it would not even boot. Could it be the motor that is close to dying?

It is a 6 year old 2.5'' 100Gb Hitachi SATA 7200RPM.

---

### Post by ahallubuntu on 2012-11-14
Hard drives fail all the time, sometimes without warning.  (Sometimes you get an early S.M.A.R.T. warning if you  monitor S.M.A.R.T., which I consider worth doing.)

So the first rule is: make regular backups.  That should be the rule even with a brand new drive (which could fail even if only one week old), but because this is an old drive, I'd be extra vigilant with backups.

As for the sound: are you sure it is screwed in securely with four screws (or as many as you can)?  I'm sometimes lazy and use only two screws to secure a hard drive and sometimes that leads to a little rattle and hum...

---

### Post by Chris_82 on 2012-11-14
> **ahallubuntu said:**
> Hard drives fail all the time, sometimes without warning.  (Sometimes you get an early S.M.A.R.T. warning if you  monitor S.M.A.R.T., which I consider worth doing.)

Well Palimpsest reads more or less the same data and it is not really failing yet.

> **ahallubuntu said:**
> 
So the first rule is: make regular backups.  That should be the rule even with a brand new drive (which could fail even if only one week old), but because this is an old drive, I'd be extra vigilant with backups.

I know about backups. This is solely about the sound :-) The hard-disk is a spare, no valuable data on it.

> **ahallubuntu said:**
> 
As for the sound: are you sure it is screwed in securely with four screws (or as many as you can)?  I'm sometimes lazy and use only two screws to secure a hard drive and sometimes that leads to a little rattle and hum...

Well when using the USB adaptor there are no screws whatsoever, but then I installed it in a laptop with all of the screws, and the sound is the same. The sound definitely comes from inside the hard-disk.

---

### Post by QIII on 2012-11-14
Fast-spinning device + buzzing = bad juju.

---

### Post by Yellow Pasque on 2012-11-15
The only thing I can think of is using the Hitachi tool to try playing with AAM and such: [http://hddguru.com/software/2006.01.20-Hitachi-Drive-Feature-Tool/](http://hddguru.com/software/2006.01.20-Hitachi-Drive-Feature-Tool/)

---

### Post by Grenage on 2012-11-15
> **QIII said:**
> Fast-spinning device + buzzing = bad juju.

Indeed!

It may outlive you, or it may die tomorrow; SMART data is just a handy tool, rather than a HD health bible.  Just make sure you won't be caught with your pants down if it fails.

Oddly enough, that's the same advice one would give for a hard drive in any state!

---

### Post by Chris_82 on 2012-11-15
> **Temüjin said:**
> The only thing I can think of is using the Hitachi tool to try playing with AAM and such: [http://hddguru.com/software/2006.01.20-Hitachi-Drive-Feature-Tool/](http://hddguru.com/software/2006.01.20-Hitachi-Drive-Feature-Tool/)

Thanks for the idea. I played around with AAM in HDtune (no need to run from a Live CD), and when going from minimum to maximum (maximum performance and also hard-disk access "noise"), the average access time goes from 16.4 to 16.0 ms, but that's it. The loud constant noise is the same and I think it is the motor as it really is doing it from the start of the spinning until the very end when it is switched off.

---

