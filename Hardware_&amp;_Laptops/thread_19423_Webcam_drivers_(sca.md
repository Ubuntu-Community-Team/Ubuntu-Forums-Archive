---
title: "Webcam drivers (sca"
date: 2005-03-11
forum: Hardware &amp; Laptops
---

### Post by DrTiger on 2005-03-11
Hi!

Me and some others are experiencing trouble recompiling the spca50x drivers (for webcams) witht the latest stable kernel in Ubuntu hoary... we get an error "invalid module format" ... any idea?

uname -a
Linux andi 2.6.10-4-386 #1 Thu Mar 10 03:25:00 GMT 2005 i686 GNU/Linux

sudo modprobe spca5xx
FATAL: Error inserting spca5xx (/lib/modules/2.6.10-4-386/kernel/drivers/usb/media/spca5xx.ko): Invalid module format

Something rotten in the state of denmark? I'm pretty sure I installed the correct kernel headers...

---

### Post by mac57 on 2005-03-11
I'm afraid I can't help, but I was wondering where you got the kernel sources? I just got Ubuntu 5.04 today and tried out the live CD. I went into Synaptic and started looking for the usual package "kernel-sources" but there isn't one - in fact nothing with "kernel" as part of it. What is the package that I need to get the correct source for the kernel?

I suspect that this is the trouble - wrong kernel source. I am having troubles with my Logitech Quickcam Pro, and I am suspecting it is the same thing (has been on other distros). That is what sent me looking for kernel sources in the first place. Thanks.

---

### Post by DrTiger on 2005-03-11
I didn't get any kernel sources. I upgrade my kernel package (earch for something called linux-* and linux-headers. the linux headers are needed for driver compilation. I will try to download proper sources though...

---

### Post by gio on 2005-03-12
same here:
1) downloaded "http://mxhaard.free.fr/spca50x/Download/spca5xx-20050301.tar.gz"
2) installed linux headers (in my case "apt-get install linux-headers-2.6.10-4-686")
apt-get install linux-headers-`uname -r` 
3) compiled & installed spca5xxx (no errors msgs)

my problems:
- "Invalid module format" for spca5xx.o
- failed to compile spcaview ("http://mxhaard.free.fr/spca50x/Download/spcaview-20050101.tar.gz")

---

### Post by gio on 2005-03-12
Now it works!
"apt-get install camstream" magically fixed everything!
I tested my webcam with Camorama (after a reboot).

---

### Post by DrTiger on 2005-03-13
Oh... well I fried my kernel somehow -.- maybe it works when I get back to the current kernel -.-

Does this camstreams package install the drivers by itself?

---

### Post by gio on 2005-03-13
[QUOTE=DrTiger]
Does this camstreams package install the drivers by itself?[/QUOTE]

No, but after installing it modprobe worked.  :-k

It creates /dev/video0 and maybe it configures something else.

---

### Post by DrTiger on 2005-03-14
For me it didn't create /dev/video0, and afaik the drivers would do that anyway, now the camstreams package. For me the invalid format remains after a lot of reinstallation, modprobin etc

---

### Post by gio on 2005-03-15
[QUOTE=DrTiger]For me it didn't create /dev/video0, and afaik the drivers would do that anyway, now the camstreams package. For me the invalid format remains after a lot of reinstallation, modprobin etc[/QUOTE]
Have you tried to plugin the webcam before modprobing?

---

### Post by tomcat23 on 2005-03-24
This combo worked for me. Surprising, actually. I'm using an old Intel cs430 webcam, and camorama crashes when I resize the video. Is there a forum post about how webcams work uder linux and how to change the configuration?

---

