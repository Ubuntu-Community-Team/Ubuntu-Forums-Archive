---
title: "Open Office crashes my system on 8.04"
date: 2008-07-14
forum: General Help
---

### Post by hansteam on 2008-07-14
When I try to run Open Office Word it crashes my system, freezing the screen and requiring a hard restart. This problem is new and it did not occur at the time of the upgrade from 7.10. 

I have tried 

```
 apt-get remove openoffice.org 
```

then

```
 apt-get install openoffice.org 
```

This didn't help at all...

Any ideas?

---

### Post by coolaj86 on 2008-07-14
apt-get purge openoffice # will remove configuration files as well

mkdir ~/OLD_CONFIG
mv ~/.openoffice* ~/OLD_CONFIG/

Try this too:
[https://wiki.ubuntu.com/CommonUpgradeProblems](https://wiki.ubuntu.com/CommonUpgradeProblems)

---

### Post by hansteam on 2008-07-15
I tried the apt-get purge as per your recommendation. It didn't work. I also tried setting up a new user and switching to that user. OpenOffice still wouldn't load, but it didn't completely lock up the computer. I was able to do a soft restart and I got the following error printed over and over again with different addresses at the beginning of each line.

```


address ata1.00:status:{DRDY ERR}
address ata1.00:exception Emask 0x0 SAct
address ata1.00:BMDMA stat 0x24
address ata1.00:cmd c8/00:08:83:15:2d/00:00:00:00:00/e9 tag 0 dma 4096 in



```

This repeats with a long address in brackets at the beginning.The address changes with each line.

EDIT: Also, this loop seemed unending. At one point the screen went blank, but the loop started after a few seconds.

---

### Post by coolaj86 on 2008-07-15
I did a quick google on your error message. It lead me here:
[http://ata.wiki.kernel.org/index.php/Libata_error_messages](http://ata.wiki.kernel.org/index.php/Libata_error_messages)

You may have found a kernel regression. Or perhaps your hard drive is dying.

Do you think you can figure out how to run smartmond and fsck on your drive to check it for error? You should find instructions pretty quick if you search the forums and the wiki.

If you find errors or your drive, you might need a new drive. If not report this as a bug.

[https://launchpad.net/ubuntu/+bugs?field.searchtext=exception+emask](https://launchpad.net/ubuntu/+bugs?field.searchtext=exception+emask)

---

