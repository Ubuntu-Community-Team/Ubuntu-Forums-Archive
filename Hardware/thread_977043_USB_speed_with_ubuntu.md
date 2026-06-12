---
title: "USB speed with ubuntu"
date: 2008-11-09
forum: Hardware
---

### Post by flyingsliverfin on 2008-11-09
I installed ubuntu on my 2gb SanDisk Cruzer, but its really slow. Is it just because of a slow USB connection or is it because of ubuntu? Is there any way to make the USB connection faster?

---

### Post by frankleeee on 2008-11-09
> **flyingsliverfin said:**
> I installed ubuntu on my 2gb SanDisk Cruzer, but its really slow. Is it just because of a slow USB connection or is it because of ubuntu? Is there any way to make the USB connection faster?

When you say slow what do you mean, give a more detailed description if you want help.

---

### Post by hapveg on 2008-11-10
I'm in a similar position.

I've just installed Ubuntu 8.10 to a flash drive, a 4gb Corsair Survivor, specifically picked because it was one of the fastest drives available.

Installing ubuntu took about an hour. Loading Firefox takes about 30 seconds.

Is there a way to check if ubuntu is treating this drive as usb 1.1 instead of usb 2.0? I may be jumping to incorrect conclusions, but it'd explain the really slow speed.

---

### Post by C.S.Cameron on 2008-11-10
I've been running 8.10 since alpha as a Full install on a 8 GB Kingston as my main O/S. Home and root partitions are formatted in Reiserfs, I have no complaints about speed. Virtual box is a bit slow at times when I'm running windows in it, but I think this is normal.

Have also been testing usb-creator with persistent installs on Kingston 2 GB and 4 GB flash drives.
I have separate home-rw and casper-rw partitions also formatted Reiserfs. This is not a bad system either, but boots seem to take longer after installing ATI drivers. This my be due to not removing Nvidia drivers first.

---

### Post by flyingsliverfin on 2008-11-11
for frankleeee: well, loading is really slow, (booting), when I check its not ever using more than 100 Mb of RAM, and the CPU is never being used more than half, yet it can't load 2 things at the same time, and even 1 app takes over a minute.

---

### Post by Sylchat on 2008-12-03
> **hapveg said:**
> 
Is there a way to check if ubuntu is treating this drive as usb 1.1 instead of usb 2.0? I may be jumping to incorrect conclusions, but it'd explain the really slow speed.

You can try:
```
lspci | grep -i usb
```

or
```
hwinfo | grep usb.version
```

You may want to try to copy an ISO from 2 USB using Nautilus and check the speed.

USB 1 is 0.2MB/s, USB 1.1 is 1.5MB/s, USB 2.0 is 60MB/s...
...in theory of course. :p

---

### Post by flyingsliverfin on 2008-12-04
I definetly don't get 0.2MB/s, or 60MB/s, and it's usually about 1 MB/s. Must be 1.1:mad:(I thought it would be 2.0!!! when I bought it)

---

### Post by mykrob on 2008-12-11
I'm getting similar problems. This issue doesnt happen on my Hardy machine, but on my Intrepid machine, USB transfer of a file on the local hard drive to a connected USB flash drive averages around 3-5MBPS, with several stalls while transferring.

---

### Post by mykrob on 2008-12-12
I did some testing this morning. The first thing, I removed the module ehci_hcd and tried.. Still slow.. Next I removed the module uhci_hcd, then re-added the module ehci_hcd, and my flash drive works as it should. I transfer 300MB in less than 10 seconds..

Maybe this will help someone get to the root of the problem.

Are there any adverse effects to running minux the uhci_hcd module? If not, as a temporary workaroun, you may try blacklisting the "offending" module.

---

### Post by flyingsliverfin on 2008-12-14
where are these modules?

In the ubuntu filesystemon my flashdrive?

just wondering... how do you know what these modules do?

im a beginner, so what IS a module?
the definition I made up was a piece of a program that executes when it is told to (like a function in a language). if it is that.... wouldn't it be bad to remove it incase it is needed?

---

### Post by mykrob on 2008-12-15
a module is essentially a piece of code or software that can be loaded or unloaded at will at the kernel level.

I think most people think of them as "drivers", if you will.

These modules can be loaded or unloaded via the command line.

Open a terminal, and to remove the desired module, type:

```


sudo rmmod uhci_hcd


```

of course to remove any other module, just change the module name. 

uhci_hcd is the usb 1.1 module

this module will still load automatically on boot. I didn't want to blacklist the module until i test this theory some more.
Blacklisting prevents a module from loading on startup.

To reload the module in the same session without rebooting, type:

```


sudo modprobe uhci_hcd


```

hope this helps

---

### Post by mykrob on 2008-12-16
More testing reveals some interesting information...
I tried my normal USB flash drive, a less than 1 month old SanDisk 4GB stick. I also tried a USB hard drive, a 320GB that gets its power from USB as well.

The hard drive had MUCH better write speed, around 19MB/sec. The USB stick could sustain roughly 5MB/sec.

Looks like the device used makes a big difference as well.

Even with this said, the performance of both device in Windows is leaps and bounds faster. Also, testing the same devices in Kubuntu 8.04, they work at about the same speeds they do in Windows..

Something fruity is definitely up with USB transfer in 8.10 :(

---

### Post by spinanicky on 2009-01-30
Always has been that way. I was just thinking that maby its because our drives are ntfs formatted.... would linux be happier if they were formatted differently?

Only down side to that is then reading the drives in windows haha.

---

