---
title: "USB Connection to Canon bcj-3000"
date: 2008-10-07
forum: Hardware
---

### Post by cheruvim on 2008-10-07
I'm not sure if this is a printer driver or usb driver question. I have a canon bjc-3000 hooked up to a dell opteron (I think). I'm finding that when I queue things up into the print spooler, printing doesn't start right away. I have to unplug the printer from the computer and then plug it back in again before the spooler starts to send print jobs to the printer.

I have waited and waited to see if the spooler would start the jobs on it's own, however, the printer just hangs and all jobs in the spooler are listed as pending.

Any advice on how to get around having to unplug and plug my printer every time I print.

Thanks in advance,
Cheruvim.

---

### Post by cheruvim on 2008-10-07
I should mention that I am using CUPSd and Gutenprint as the main driver for the printer. The usb driver is the default one that  I believe gets installed with ubuntu..

Thanks again,
C.

---

### Post by phidia on 2008-10-07
To troubleshoot this you could try and print from a terminal, Use the "lp" command-for example "lp /home/cheruvim/testpage.txt" (See man lp for more details). The idea behind this is that the terminal may provide more output about the problem.

You could also see if you can update your cups or gutenprint drivers.

---

### Post by cheruvim on 2008-10-15
Hey, sorry for the late response... I tried lp -c (for spooling since most apps do this) and no problem.. I'm not sure where the trouble could be now. I'm guessing it has to do with the way the apps communicate with the shell to get documents printed. If maybe there was a way I could see what command they were using (iow, what flags they used) I could perhaps reproduce this, but so far no go. I'll keep trying to see if I can reproduce it. So, I guess for now I'll just unplug and replug the usb in.

I'm guessing that maybe the hardware layer changes the id of the printer (ala lshw) so when the spooler daemon sends documents to the printer it's sending to the wrong port?? Again is there a way to get dbg (or what's the name of the native ubuntu debugger?) to display what the spooler is doing when it recevies documents..

Yikes.. very convoluted... Sorry.

---

### Post by cheruvim on 2008-10-22
> **cheruvim said:**
> Hey, sorry for the late response... I tried lp -c (for spooling since most apps do this) and no problem.. I'm not sure where the trouble could be now. I'm guessing it has to do with the way the apps communicate with the shell to get documents printed. If maybe there was a way I could see what command they were using (iow, what flags they used) I could perhaps reproduce this, but so far no go. I'll keep trying to see if I can reproduce it. So, I guess for now I'll just unplug and replug the usb in.

I'm guessing that maybe the hardware layer changes the id of the printer (ala lshw) so when the spooler daemon sends documents to the printer it's sending to the wrong port?? Again is there a way to get dbg (or what's the name of the native ubuntu debugger?) to display what the spooler is doing when it recevies documents..

Yikes.. very convoluted... Sorry.

I noticed that since this was posted that an update to cupsd was issued. Since this update was installed (I didn't record any info about the update but it was the latest one since my last post to this thread), this problem has not been reproduced. I think we have it solved. Thanks all for your help! :)

---

### Post by cheruvim on 2008-12-27
Well I hate to reopen old wounds, but this problem has been reproduced and should be classified as not solved. I noticed it happens alot when printing from one application and then printing from another.. I also noticed that this happens alot with the latest version of the Viewer default PDF Viewing application provided by Ubuntu.

Well, the diagnostic procedures above didn't provide any info, however I have a snippet of the dmesg log which seems to track when I pull the usb printer cable out of the machine and then plug it back in:

[405383.260452] usblp0: nonzero write bulk status received: -71
[405383.334974] usb 3-1: USB disconnect, address 2
[405383.335195] usblp0: removed
[405388.655727] usb 3-1: new full speed USB device using uhci_hcd and address 3
[405388.833707] usb 3-1: configuration #1 chosen from 1 choice
[405388.840672] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04A9 pid 0x1051
[597456.901893] audit(1228787726.139:3): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=21939 profile="/usr/sbin/cupsd" namespace="default"
[1011837.302722] usblp0: nonzero write bulk status received: -71
[1011837.474238] usb 3-1: USB disconnect, address 3
[1011837.474452] usblp0: removed
[1011843.702475] usb 3-1: new full speed USB device using uhci_hcd and address 4
[1011843.880475] usb 3-1: configuration #1 chosen from 1 choice
[1011843.887425] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x04A9 pid 0x1051
[1853548.184555] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[1853736.867159] usb 3-1: USB disconnect, address 4
[1853736.867353] usblp0: removed
[1859447.616609] usb 3-2: new full speed USB device using uhci_hcd and address 5
[1859447.794585] usb 3-2: configuration #1 chosen from 1 choice
[1859447.801492] usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x04A9 pid 0x1051
[1859492.819796] usblp0: nonzero write bulk status received: -71
[1859492.985717] usb 3-2: USB disconnect, address 5
[1859492.986062] usblp0: removed
[1859494.856376] usb 3-2: new full speed USB device using uhci_hcd and address 6
[1859495.029618] usb 3-2: configuration #1 chosen from 1 choice
[1859495.044135] usblp0: USB Bidirectional printer dev 6 if 0 alt 0 proto 2 vid 0x04A9 pid 0x1051
[1861168.453974] usblp0: nonzero write bulk status received: -71
[1861168.461921] usb 3-2: USB disconnect, address 6
[1861168.462138] usblp0: removed
[1861169.944178] usb 3-2: new full speed USB device using uhci_hcd and address 7
[1861170.126895] usb 3-2: configuration #1 chosen from 1 choice
[1861170.141074] usblp0: USB Bidirectional printer dev 7 if 0 alt 0 proto 2 vid 0x04A9 pid 0x1051
[1994236.719188] usb 3-2: USB disconnect, address 7
[1994236.719358] usblp0: removed
[1994246.133531] usb 3-1: new full speed USB device using uhci_hcd and address 8
[1994246.367557] usb 3-1: configuration #1 chosen from 1 choice
[1994246.373505] usblp0: USB Bidirectional printer dev 8 if 0 alt 0 proto 2 vid 0x04A9 pid 0x1051
[1994278.735212] usblp0: nonzero write bulk status received: -71
[1994278.854047] usb 3-1: USB disconnect, address 8
[1994278.854342] usblp0: removed
[1994283.075471] usb 3-2: new full speed USB device using uhci_hcd and address 9
[1994283.253457] usb 3-2: configuration #1 chosen from 1 choice
[1994283.266492] usblp0: USB Bidirectional printer dev 9 if 0 alt 0 proto 2 vid 0x04A9 pid 0x1051


You see that I have to keep plugging it out and putting it back in again, even after restart. I believe it has something to do with nonzero write bulk status received ( since that is when you see me disconnecting the printer... ) However I am still mystefied by this.

Hope this may shed some light on this subject.

Thanks again,
Cheruvim.

---

