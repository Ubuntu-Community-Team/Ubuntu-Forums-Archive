---
title: "1005ha Webcam not showing up in 10.10"
date: 2010-12-06
forum: Hardware
---

### Post by rfdeshon on 2010-12-06
Hello all. I was attempting to use my webcam tonight when I discovered it is no longer working. After some digging, I've found that it is not showing up at all (nothing in lsusb or lspci relating to the webcam). I've checked and it is enabled in my BIOS. This is quite strange since the webcam has always worked for me without any issues in the previous Ubuntu releases I've used as well as a handful of other Linux distros I've tested on here. After searching the forums and Google for the past hour or so, I've found a handful of other people having the same issues but no one offering any solutions (or any help at all for that matter). Is there anyone out there with better search-fu than me who can point me to a fix and/or launchpad bug? I suppose if I don't get any response here I'll file my own launchpad bug... it makes me sad to see huge regressions in hardware support like this.

---

### Post by slooow on 2010-12-06
I have a similar issue although on lucid. It worked previously. I only updated the software and experimented with a wireless router configuration. Next thing the webcam does not show up anymore. Was using it in skype but checked with cheese and lsusb. I was thinking I somehow knocked the kernel module for the webcam out but I have no clue how it was called and google did not help.

---

### Post by monarchheels on 2010-12-06
Same problem here on an MSI U210. Webcam just suddenly stopped working in everything including Cheese.

---

### Post by slooow on 2010-12-06
It is working again for me. Not sure that applies also for 10.10. However check for modules with name "v4l". Stands for video for linux
```
#find /lib -name "v4l*"
```
Check also if such modules are loaded:
```
# lsmod | grep v4l
```
If there are not loaded, load the most likely candidate:
```
# modprobe v4l1-compat 
```

---

### Post by rfdeshon on 2010-12-09
Nope, fraid that didn't work. v4l wasn't loaded but loading v4l1-compat nor v4l2-common made any difference. Also, your modprobe command needs to be perpended by sudo. Also, I doubt that a kernel module is the problem given that the webcam isn't even showing up in lsusb/lsmod. Seems the kernel isn't even recognizing that the device exists.

---

### Post by slooow on 2010-12-19
You are right with sudo. However a code line starting with # is a shorthand for root. With ```
sudo -i
``` you get a root console. 
On my netbook the webcam has gone away also and I have not found any remedy. It does not show up on ```
lsusb
```.

---

### Post by slooow on 2010-12-19
rfdeshon, after a good night's sleep I found another [thread]("http://diogomelo.net/drupal/blog/10/webcam-problem-dell-inspiron") where they solved it. 
At the end of the chain is the driver uvcvideo which pulls in videodev, the two of which pull in v4l1_compat. Now the camera shows up in lsusb and works in cheese. Hope that helps.

---

