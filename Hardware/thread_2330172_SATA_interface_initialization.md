---
title: "SATA interface initialization"
date: 2016-07-08
forum: Hardware
---

### Post by irishetalon007 on 2016-07-08
I have a laptop with a SATA interface for removable drives. I interchange between a Bluray Disc drive and a DVD Disc drive on the laptop. An interesting phenomenon is that the computer does not recognize either of the drives when inserted unless there was a drive in the SATA bay at boot. Is there a way using command line to manually intialize the SATA interface to use a drive, even if a drive was not present during boot on the SATA interface?

Thanks!

---

### Post by squirrel3 on 2016-07-08
Could you perhaps post pictures of your hardware? I'm familiar with SATA but I do not know what your setup looks like.

---

### Post by irishetalon007 on 2016-07-08
[IMG]https://s31.postimg.org/6hwovq1ej/615_ZMYmhh_RL_SL1000.jpg[/IMG]
The hardware looks like this. It's standard in laptops of the past few years.

---

### Post by squirrel3 on 2016-07-09
[COLOR=#303030][FONT=&amp]I know this is the code for mounting, via terminal. 
[/FONT][/COLOR]
sudo mount /media/cdrom0/ -o unhide

---

### Post by irishetalon007 on 2016-07-09
the problem isn't that it's not automounting. When I do "sudo lshw" when a drive is inserted in the bay and one was present at boot, I get:

>      *-scsi:1          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RAM UJ8B1
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: H.03
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc


However, if a drive was not present during boot, and then a drive is inserted and I do "sudo lshw", nothing shows up!

---

