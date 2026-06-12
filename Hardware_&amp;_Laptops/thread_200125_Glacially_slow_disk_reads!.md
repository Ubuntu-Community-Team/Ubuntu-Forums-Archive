---
title: "Glacially slow disk reads!"
date: 2006-06-19
forum: Hardware &amp; Laptops
---

### Post by RandomJoe on 2006-06-19
I've tried searching Google and the forums, but can't find anything quite like I'm experiencing.  I'm hoping that just means I did something dumb, but...!

I have a Latitude C840 laptop (P4 1.8GHz, 512MB RAM, 40GB HDD) that has run Slackware 9 (with 2.6 kernel) / KDE beautifully for a very long time.  I'm now trying Ubuntu 6.06 and the HDD disk access times are glacial!  Running 'hdparm -Tt /dev/hda' gives wildly varying times, from as high as 12MB/sec to as low as 400kB/sec (buffered disk reads - the cache reads are routinely around 700MB/sec).

Operationally, loading larger apps such as Firefox take significant amounts of time.  When opening a terminal window, I often have to wait 10-20 seconds before the prompt appears.  Getting UT2k3 going takes many MINUTES!  Once the app is loaded into memory, everything runs just as fast as before.

The thing that makes me rule out hardware is I can reload the dd image of my old Slack 9 install and everything is very fast and responsive.  

UT is pretty much my best comparison, as I know it's identical on both installs.  With Slack9, the HDD reads continuously and gets the game going with only a short hesitation.  With Ubuntu 6.06 the HDD only sporadically reads in short bursts - as indicated by the HDD light - and takes, again, many minutes to get going.

I have tried doing some 'hdparm' tuning, it appears by default the only "high performance" item that's turned on is DMA, but so far nothing has changed this behavior.

While I know things are "bigger" (bloated, if you will... ;) ) with newer releases, I'm only using about 260MB of 512MB RAM and the system shows no sign of struggling otherwise.  Anyone have suggestions or ideas where to look?!?  While it's _usable_ as-is, it really is quite annoying as I know this machine has a lot more capability than I'm getting right now!

Thanks!

---

### Post by gerbman on 2006-06-20
[QUOTE=RandomJoe]I've tried searching Google and the forums, but can't find anything quite like I'm experiencing.  I'm hoping that just means I did something dumb, but...!

I have a Latitude C840 laptop (P4 1.8GHz, 512MB RAM, 40GB HDD) that has run Slackware 9 (with 2.6 kernel) / KDE beautifully for a very long time.  I'm now trying Ubuntu 6.06 and the HDD disk access times are glacial!  Running 'hdparm -Tt /dev/hda' gives wildly varying times, from as high as 12MB/sec to as low as 400kB/sec (buffered disk reads - the cache reads are routinely around 700MB/sec).

Operationally, loading larger apps such as Firefox take significant amounts of time.  When opening a terminal window, I often have to wait 10-20 seconds before the prompt appears.  Getting UT2k3 going takes many MINUTES!  Once the app is loaded into memory, everything runs just as fast as before.

The thing that makes me rule out hardware is I can reload the dd image of my old Slack 9 install and everything is very fast and responsive.  

UT is pretty much my best comparison, as I know it's identical on both installs.  With Slack9, the HDD reads continuously and gets the game going with only a short hesitation.  With Ubuntu 6.06 the HDD only sporadically reads in short bursts - as indicated by the HDD light - and takes, again, many minutes to get going.

I have tried doing some 'hdparm' tuning, it appears by default the only "high performance" item that's turned on is DMA, but so far nothing has changed this behavior.

While I know things are "bigger" (bloated, if you will... ;) ) with newer releases, I'm only using about 260MB of 512MB RAM and the system shows no sign of struggling otherwise.  Anyone have suggestions or ideas where to look?!?  While it's _usable_ as-is, it really is quite annoying as I know this machine has a lot more capability than I'm getting right now!

Thanks![/QUOTE]The output of hdparm -Tt looks pretty low. What is the output of```
sudo hdparm /dev/hda
```

---

### Post by odix on 2006-06-20
Hi, we have discussed this issue in this [thread]("http://www.ubuntuforums.org/showthread.php?t=188901"),

The reason of the slow performance is that hald is probing the cdrom (dvd) drive, which is on the same bus with the harddisk. I've the same issue on my dell 8200, the problem raises with dapper, maybe kernel version greater than 2.6.13 and hald kombination.

Hopefully one of the maintainers pay attention to this problem

regards

---

### Post by RandomJoe on 2006-06-20
Ah, I see my '1337' searching skills have let me down again! :)  Typical...

That is definitely my problem.  I tried the suggested fixes of disabling CD polling and it helped a little, but not much.  Completely shutting down 'dbus' brought everything back nicely - 752MB/sec cache and 25MB/sec disk reads.  That's without any 'hdparm' tuning.  Of course, other things then quit working without dbus!

Thanks for the help!  I'll also be hoping for some improvements here.

---

