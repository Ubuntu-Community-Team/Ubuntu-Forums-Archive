---
title: "Scanner not detected Brother DCP-J4110DW"
date: 2014-11-17
forum: Hardware
---

### Post by eckifolki on 2014-11-17
Hello,
i had installed with 
```
sudo bash linux-brprinter-installer-2.0.0-1 DCP-J4110DW
```
from the brother support site. Printing succeeded. Later I discovered, Sanner doesnt work. I installed the new driver:
```
brscan4-0.4.2-4.i386.deb
```
Then I tried scanning and got error note:
```
folki@folkinet:~$ scanimage >test.tif
scanimage: open of device brother4:bus5;dev8 failed: Invalid argument
folki@folkinet:~$
```
Please help, how I could get running the Brother DCP-J411DW-Scanner

:-)

---

### Post by leclerc65 on 2014-11-17
Did you do this ?

```


   sudo gedit /lib/udev/rules.d/40-libsane.rules

    Add the following 2 lines before "LABEL="libsane_rules_end"".

    # Brother scanners
    ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"


```

---

### Post by eckifolki on 2014-11-17
Hi leclerc65, genius!

First id did not work after saving the file with the udev rules. But then I shut down and restarted. Afterwards all okay!

Thanks a lot
Volkmar

:smile:

---

