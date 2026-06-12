---
title: "cmi8788 chipset help!"
date: 2008-02-02
forum: Hardware &amp; Laptops
---

### Post by Truedream on 2008-02-02
hey guyz

i just reinstalled 7.10 and now the sound is not working. i was following the instructions on [this]("http://www.alsa-project.org/main/index.php/Matrix:Module-oxygen") page, just like i did before. 

Everything seems to go along just right until i've to insert the modules into the kernel.  **modprobe snd-oxygen** gives this error.```
cd-r@theusual:/usr/src/alsa/alsa-utils-1.0.16rc1$ sudo modprobe snd-oxygen
WARNING: Error inserting snd_oxygen_lib (/lib/modules/2.6.22-14-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_oxygen (/lib/modules/2.6.22-14-generic/kernel/sound/pci/oxygen/snd-oxygen.ko): Unknown symbol in module, or unknown parameter (see dmesg)
``` I've tried both the 1.0.16rc2 and stable 1.0.15 versions. Before i reinstalled Ubuntu 7.10, sound was working just fine.

heres lspci -v 
```
02:00.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
        Subsystem: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
        Flags: bus master, medium devsel, latency 64, IRQ 19
        I/O ports at df00 [size=256]
        Capabilities: <access denied>
```

Currently i'm using the OSS driver, which work just fine but the quality is not the same.  I've attached the log file for whole installation process. Any kind of help would be appreciated.

---

### Post by hsjC on 2008-03-06
Maybe there are not many cmi8788 users under linux/ubuntu, but this exact problem bothered me for a couple hours.

Here is what I did to solve it: 

Step 1: Remove alsa-base from synaptic package manager( for 7.10, alsa-base is 1.0.14 )
Step 2: Install alsa 1.0.16 as shown by the guide.

Hope this helps other linux newbies like me.

---

### Post by amihov on 2008-03-28
where did you find the guid how to install the new release of alsa?

---

### Post by hsjC on 2008-04-13
Sry amihov for such a late reply. I hope you have solved your problem by now. 

I followed this:

[http://www.alsa-project.org/main/index.php/Matrix:Module-oxygen](http://www.alsa-project.org/main/index.php/Matrix:Module-oxygen)

---

### Post by GG_HTPC on 2008-04-15
I Azuntech Meridian card based on CMI8788 as well. I tried steps given in your post to remove the ALSA packages from synaptic package manager and then tried to install ALSA libraries 1.0.16. Unfortunately, I still get the error message(s) when I try 'modprobe snd-oxygen' command.

Any ideas? thank you in advance.:confused:

---

