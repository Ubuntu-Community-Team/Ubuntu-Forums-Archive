---
title: "Ubuntn 7 beta is magnificent but ..... there some problems with sound card and  fan"
date: 2007-04-01
forum: Hardware &amp; Laptops
---

### Post by DO55 on 2007-04-01
Ubuntn 7 beta is magnificent specially the new network manager , now i can connect without any problem with WPA wireless  
but .....
1- the fan always on with my notebook amilo 3438G 
2-also the sound not working (ALC880 sound card )

how can i solve this problem ,  i hope those problems been  fixed in the final release

**i have same problems with ubunto 6.10  !!

---

### Post by mayhemt on 2007-04-01
I can help u on 2nd one. ( had the same problem)

do this cmd & u should see the result shown.

```

mrt@Bluhills:~$ ls -l /dev/snd
total 0
crw-rw-rw- 1 root audio 116, 8 2007-04-01 17:28 controlC0
crw-rw-rw- 1 root audio 116, 7 2007-04-01 17:28 pcmC0D0c
crw-rw-rw- 1 root audio 116, 6 2007-04-01 17:28 pcmC0D0p
crw-rw-rw- 1 root audio 116, 5 2007-04-01 17:28 pcmC0D1c
crw-rw-rw- 1 root audio 116, 4 2007-04-01 17:28 pcmC0D2p
crw-rw-rw- 1 root audio 116, 3 2007-04-01 17:28 seq
crw-rw-rw- 1 root audio 116, 2 2007-04-01 17:28 timer

```

if you see crw---------, thats the problem.
simply do this, your sound work fine. try autodetect later (System>preferences>sound on gnome menu)

```

sudo chmod 666 /dev/snd/*

```

search deeper in forums for 1st problem... :guitar:

---

### Post by dbulante on 2007-05-24
I have similar problem with same sound card.  Tried the solution presented and it didn't work.

---

### Post by Brinstar on 2007-05-24
the cpu is most likely due to you not having uncommented the relevant parts of 

/etc/rc.d/rc.modules 

i.e. the acpi_cpufreq line

or not having installed your graphics card drivers. This is such a common problem on Linux that i think it should be a sticky somewhere.

Also try getting cpufrequtils, that helped me tremedously.

---

