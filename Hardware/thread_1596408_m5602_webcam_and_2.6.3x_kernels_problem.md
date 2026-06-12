---
title: "m5602 webcam and 2.6.3x kernels problem"
date: 2010-10-14
forum: Hardware
---

### Post by titomax82 on 2010-10-14
Sorry for my poor english and my poor linux experience, but I will try to make  my best.

These are all the details I collected till now:


Notebook: Packard Bell EasyNote MX67-P-023  lsusb: Bus 001 Device 004: ID 0402:5602 ALi Corp. Video Camera Controller
This webcam does "not" work with:
- Ubuntu Karmic 2.6.31
- Ubuntu Lucid 2.6.32
- Ubuntu Maverick 2.6.35
- Latest versions (downloadable on october 2010) of: Slax, Slax Remix, Knoppix, DSL, Puppy, Mint, Mandriva, openSUSE; I can't try them all again to know the exact kernel version, but for sure 2.6.3x

Webcam "works" with:
- Ubuntu Jaunty 2.6.28
- Ubuntu Karmic with a "trick": Karmic is originally shipped with 2.6.31, then I installed kernel 2.6.29 and webcam worked, but there where major system problems and system crashes with this combination
- Mandriva 2009 2.6.29 

Drivers are not installed in a second moment, they already come with kernel. So, I think it's not a particular distro's problem, but a kernel issue, infact every 2.6.28 or 2.6.29 distro works at first try, instead every 2.6.3x doesn't work (webcam detected,
but no correct video output).


[http://hardware4linux.info/component/26591/](http://hardware4linux.info/component/26591/) reports 2.6.29 kernel as the last working Many people all over international forums report webcam stopped working after a kernel update.


In programs like gstreamer-properties, Camorama, aMsn, Emesene, Skype or Cheese it's recognized as "USB 2.0 Camera" For example, in aMSN->preferences->other->Audio Video:
- select device box: "v4l2: USB 2.0 Camera"
- select channel box:" ALi m5602"
- and in the video box where image should appear: "unable capture from device" (blank screen)  

These 2 terminal commands give no different result:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so program_to_test
or
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so program_to_test 


Just one thing a noticed...but i don't know if it's important or not: when trying the unlucky (for me) kernels webcam light was off and it went on only when a program requested it; with the lucky (for me) kernels webcam light is always on since startup; I have to underline that my webcam has no activation button (like some FN+x or hardware button), nor it require a particular software activation... 


Testing the 6 kind of sensors (Lucid 2.6.32):
modprobe -v -r gspca_m5602
modprobe -v gspca_m5602 force_sensor=1   (then 2...3...)
(Sensors are: OmniVision OV9650, Samsung s5k83a, Samsung s5k4aa, Micron mt9m111, Pixel plus PO1030, OmniVision OV7660)

1,2,4,5,6 give a blank static image with some stripes and dots
3, insted, give a blank screen, but not static, less stripes and dots, but moving
However correct sensor (detected) is s5k83a 


There are some attachments with Jaunty and Lucid (m5602.zip):
#1: Several Jaunty outputs
#2: Several Lucid outputs
#3-4-5: Screenshot in Lucid
#6-7: lsmod in jaunty and lsmod in lucid
#8: dmesg comparison between jaunty and lucid
#9: modinfo comparison between jaunty and lucid
#10: v4l-info comparison between jaunty and lucid


""My personal conclusion"":
m5602 drivers were well implemented in 2.6.28 and 2.6.29 kernels but something changed in 2.6.3x kernels

Can this problem be solved this problem?
Or is there a way to get back? I mean using jaunty drivers in lucid or maverick?

I hope in your help

---

### Post by titomax82 on 2010-10-15
i'm desperate...

---

### Post by utilitytrack on 2010-10-24
And where the link to your bug ticket?? :))

**"ALi Corp. 5602 (m5602) webcam not working on (some?) newest kernels (2.6.31, 2.6.32, 2.6.35)" **[https://bugzilla.kernel.org/show_bug.cgi?id=16575]("https://bugzilla.kernel.org/show_bug.cgi?id=16575")

All people who experienced similar problems are welcome to share your skills, logs, questions and comments there.

---

