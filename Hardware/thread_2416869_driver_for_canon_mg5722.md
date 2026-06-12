---
title: "driver for canon mg5722"
date: 2019-04-16
forum: Hardware
---

### Post by jgw on 2019-04-16
This is a bit embarrassing.  I had a previous thread that told me where to go to get the proper driver.  Apparently I lost it.  Anyway, I downloaded it, (cnijfilter2-5.20-1-deb.tar.gz) then installed it.  then I went back to my printers to see what happened.  My printer is running without a driver and I have absolutely no idea how to install the driver.  I searched but found nothing, I then thought to install from database (nothing really there, tried a couple but they failed),  then I noticed that I now had another printer.  The one I was using (for a while) was canon mg5700,  now I also have canon_mg5700_series printer.  that last one doesn't accept jobs (it has no address although the other one has 'localhost' as an address).  This gets even better.  I can no longer print multiple pages, just one at a time.  I also tried removing the mg5700_series printer, it deleted it and then it came back (and keeps coming back).  

My real problem is that this printer has been working fine for well over a year with no problems.  I obviously did something clever but have no idea what.  

So, I have no idea how to assign the driver that I downloaded and installed.
I have two printers listed but only one works and one doesn't accept jobs
I am, basically, screwed.

Thoughts?

---

### Post by brian_p on 2019-04-16
> **jgw said:**
> 
So, I have no idea how to assign the driver that I downloaded and installed.
I have two printers listed but only one works and one doesn't accept jobs
I am, basically, screwed.

You definitely do not need any Canon printer drivers. See

[https://wiki.debian.org/QuickPrintQueuesCUPS](https://wiki.debian.org/QuickPrintQueuesCUPS)

However, you do seem to be in a bit of a mess and the printer entry which doesn't accept jobs is a little bothersome. Please confirm that the device is on the network and post the output of

```
lpstat -t
```

Say what application you are printing from and what is shown in its print dialog.

---

### Post by brian_p on 2019-04-16
Would you also give the output of
```
lpstat -l -e
```

---

### Post by jgw on 2019-04-17
Thank you for the replies!

The HP_ENVY_Photo_6200 printer is on the network and connected to my wife's computer.
I have two dymo labelwriters (Bought the second when the first didn't work - then I found it did work after I found the driver <sigh>)

greg@gregdown:~$ lpstat -t
scheduler is running
system default destination: MG5700
device for Canon_MG5700_series: ///dev/null
device for HP_ENVY_Photo_6200_series_641030_: ipps://HP48BA4E641030.local:631/ipp/print
device for LabelWriter-400: usb://DYMO/LabelWriter%20400?serial=08041415134237
device for LabelWriter-400-Turbo: usb://DYMO/LabelWriter%20400%20Turbo?serial=05050508452559
device for MG5700: dnssd://Canon%20MG5700%20series._ipp._tcp.local/?uuid=00000000-0000-1000-8000-60128B27F963
Canon_MG5700_series not accepting requests since Tue 16 Apr 2019 03:02:30 PM PDT -
	reason unknown
HP_ENVY_Photo_6200_series_641030_ accepting requests since Wed 17 Apr 2019 09:47:16 AM PDT
LabelWriter-400 accepting requests since Mon 25 Mar 2019 10:25:00 AM PDT
LabelWriter-400-Turbo accepting requests since Mon 25 Mar 2019 01:21:54 PM PDT
MG5700 accepting requests since Tue 16 Apr 2019 02:38:40 PM PDT
printer Canon_MG5700_series disabled since Tue 16 Apr 2019 03:02:30 PM PDT -
	reason unknown
printer HP_ENVY_Photo_6200_series_641030_ is idle.  enabled since Wed 17 Apr 2019 09:47:16 AM PDT
printer LabelWriter-400 is idle.  enabled since Mon 25 Mar 2019 10:25:00 AM PDT
printer LabelWriter-400-Turbo is idle.  enabled since Mon 25 Mar 2019 01:21:54 PM PDT
printer MG5700 is idle.  enabled since Tue 16 Apr 2019 02:38:40 PM PDT

greg@gregdown:~$ lpstat -l -e
Canon_MG5700_series permanent ipp://localhost/printers/Canon_MG5700_series file:///dev/null
HP_ENVY_Photo_6200_series_641030_ network none ipps://HP%20ENVY%20Photo%206200%20series%20%5B641030%5D._ipps._tcp.local/
LabelWriter-400 permanent ipp://localhost/printers/LabelWriter-400 usb://DYMO/LabelWriter%20400?serial=08041415134237
LabelWriter-400-Turbo permanent ipp://localhost/printers/LabelWriter-400-Turbo usb://DYMO/LabelWriter%20400%20Turbo?serial=05050508452559
MG5700 permanent ipp://localhost/printers/MG5700 dnssd://Canon%20MG5700%20series._ipp._tcp.local/?uuid=00000000-0000-1000-8000-60128B27F963
greg@gregdown:~$

I just deleted the mg5700_series printer and it seems to have taken.  I really won't know until I reboot.

---

### Post by brian_p on 2019-04-17
Did the mg5700_series printer return after a reboot?

Please stop cups-browsed
```
systemctl stop cips-browsed
```
and say which printers are no longer visible (if any).

---

### Post by brian_p on 2019-04-17
Something for you to think about:
> device for Canon_MG5700_series: ///dev/null
This device will send a job to nowhere. It will disappear.

I am puzzled as to why you have it because a real effort by a user has to be made to use it. It should not be the result of any auto-setup procedure. (I'd also expect it to be /dev/null).

---

### Post by brian_p on 2019-04-19
The interchange  appears to have come to a grinding halt.

Has something which is upsetting or non-useful been  said?

---

### Post by jgw on 2019-04-27
Thank you for the replies.  I was down for a bit. 

I think I fixed the problem.  I got rid of the printers (except for my wife's which is just there).  Then I reinstalled the dymo and the canon mg5700.  I had to choose the driver for the dymo and the canon defaulted.  Both work..........    

Thanks again!!

---

