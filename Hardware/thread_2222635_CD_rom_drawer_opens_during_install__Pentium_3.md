---
title: "CD rom drawer opens during install / Pentium 3"
date: 2014-05-07
forum: Hardware
---

### Post by demiurgetheartisan on 2014-05-07
Here's a strange one for ya! I am trying to breathe life into an ancient machine. (pavilion 7850) with 512MB RAM and 900MHz processor. It seems to go along with the install beautifully, and then ...BAM! the darn CD tray opens up just at a time when the "installing files" prompt begins. which is at about 85% through the process. man this is frustrating! ](*,)Any ideas how to prevent this ghost tray opener from spooking my computer?

---

### Post by Bashing-om on 2014-05-07
demiurgetheartisan; Humm ?
Maybe this "ancient machine" is not pae enabled ?
Boot the liveDCD to terminal;
run terminal command
```

cat /proc/cpuinfo

```
look in the flags field for 'pae, sse, sse2'. If not present ya want a non-pae kernel installation.
see:
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)
[http://ubuntuforums.org/showthread.php?t=2211590](http://ubuntuforums.org/showthread.php?t=2211590)

Then again, maybe you are pushing the machine beyond what it can do with the release you are installing;
maybe:
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)
make sure ya verifiy the .iso :
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Burn the .iso as an image
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Boot to the boot option screen in the liveDVD once burned and -> "check disk for defects"

Try once more to install.
There are a number of threads on the forum in respect to installing on old hardware. Many are committed to this ideal.

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mörgæs on 2014-05-08
According to this
[http://www.cnet.com/products/hp-pavilion-7850-piii-933-mhz-monitor-none-series/specs/](http://www.cnet.com/products/hp-pavilion-7850-piii-933-mhz-monitor-none-series/specs/)
you have a Pentium 3 which supports PAE but not SSE2, so you will get a problem with Flash.

Performance is less than poor, but if you want to install anyway I suggest the [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall").

---

