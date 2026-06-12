---
title: "Webcam working only few seconds (QuickCam Communicate STX)"
date: 2012-09-08
forum: Hardware
---

### Post by yankeeDDL on 2012-09-08
Hi,

I have a Logitech QuickCam Communicate STX.
It worked fine on 10.04, but I have recently upgraded to 12.04.1 and the video now works only for a few seconds.
I have installed OpenSUSE with the same results.
I am back on Ubuntu and I have tried both the 32bit and the 64bit versions, with identical results.
I have tried the PRELOAD fix (an example: [http://ubuntuforums.org/archive/index.php/t-997807.html](http://ubuntuforums.org/archive/index.php/t-997807.html)) but it makes no difference, except that I was not able to use the fix it on the 64bit installation. This was intended for a different issue anyway, but it's all I found.

I checked both Skype and Cheese and they behave the same: the video starts, the brightness adjusts automatically as usual, but after few seconds (variable between 5-10, more or less) the video simply freezes.
Quit and restart Cheese (or Skype) and everything works again. For few seconds.

The installations have been clean on a new HD and I have temporarily removed all additional drives, so the system only sees 1 HD.

During installation the webcam goes on asking me if I want to grab a picture: the issue is already there and the video stops quickly.

I have also installed the video driver (non-free) in case the issue was reproducing the video, rather than grabbing it, but no change.

I am not sure what else to try: I am afraid that the driver simply no longer works on the most recent Linux kernel version. Any thought on what else to try to debug this issue?

Thanks.

---

### Post by samwilhide on 2012-09-09
Having similar problems on a different computer with different webcams. Inspiron b130 with Logitech c270z have been searching on google and various forums for a while with no results. Only interesting thing I've found is that the problem doesn't exist on my ibook G3 running PowerPC lubuntu 12.04.

---

### Post by yankeeDDL on 2012-09-10
I have solved teh problem.
First of all, I have found this website, which seems quite relevant and points out a bug in Linux Kernels (covering a relatively long time span: from v2.3.37 to v3.5 inclusive): [http://www.ideasonboard.org/uvc/faq/](http://www.ideasonboard.org/uvc/faq/)

I tried the solution and seemed to help a bit but it was still not usable.
The solution requires to unplug-replug the webcam for testing, so to make it more practical for me I brought the cable on a different USB port and it worked like a charm.

Conclusion, as far as I understand it: some changes in the linux kernel might have triggered a different power management (the website above especially mentiones v2.6.37 where some changes on autosuspend were made.
I am speculating that some of these recent changes have affected the "stability" of cameras connected through (certain) USB hubs.

So trying a different USB port (the safest bet are the ones directly on the motherboard, of course) and applying the fix pointed above might fix the problem.

Good luck.

---

