---
title: "Unable to play DVDs"
date: 2009-02-07
forum: Hardware
---

### Post by HangingOutWithJim on 2009-02-07
Version 8.10 on old Fujitsu Amilo A 7620 laptop. 2600+ processor with 512 MB RAM. 40 GB Toshiba UDMA100 capable hard drive. Unknown (?) DVD/CD-RW drive (hdparm says model "HL-DT-STCD-RW/DVD DRIVE GCC-4241N").

System would crash with "Kernel panic -no syncing: Fatal exception in interrupt" whenever I'd try to watch DVDs or do something else that would involve transferring large amount of data from DVD drive. I managed to work this around by putting "options libata dma=1" into /etc/modprobe.d/options. 

Using DVD drive doesn't crash my system anymore but now DVD playback is extremely choppy. I usually can watch only couple of seconds before movie player hangs completely. I assume this is because my DVD drive is transferring data too slowly? Dmesg says about the drive "ata2.00: configured for PIO4". Is that the data transfer mode it's using now? 

I don't know much about Linux so any help would be appreciated.

---

### Post by cariboo on 2009-02-07
Choppy DVD playback usually indicates a video driver problem. What video driver are you using?

Jim

---

### Post by HangingOutWithJim on 2009-02-08
I finally found some information about my graphics driver. I hope this is the correct information you requested:

From Xorg.0.log
```

(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 6.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1

```
Graphics card is "01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] [1002:4c66] (rev 01)"

However, I doubt that the graphics driver is causing this. Before I changed that libata option, the DVD playback would be perfectly smooth before system would hang. Also, graphics have always worked otherwise perfectly smooth. It was only after I changed the DMA mode(???) for the DVD drive playback went choppy. DVD would play ok for about a second and then start to stutter and after that play OK, then stutter again etc. During this time DVD drive is constantly spinning up and down.

---

### Post by HangingOutWithJim on 2009-02-10
So, any ideas? I'd really love to use Linux on my old laptop but this kind of problems are really discouraging

---

### Post by HangingOutWithJim on 2009-02-12
No solution? Well, I guess I'll move back to Windows then.

---

### Post by icp on 2009-02-12
if the dvd use CSS you can try this:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```
or install "libdvdcss2"

---

### Post by HangingOutWithJim on 2009-02-12
> **icp said:**
> if the dvd use CSS you can try this:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```
or install "libdvdcss2"

Didn't help. Still the same choppy playback...

---

