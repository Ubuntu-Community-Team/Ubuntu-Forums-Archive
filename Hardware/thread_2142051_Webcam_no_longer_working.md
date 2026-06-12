---
title: "Webcam no longer working"
date: 2013-05-04
forum: Hardware
---

### Post by Squidge1980 on 2013-05-04
Hi all,

First time poster, but have been using Ubuntu on and off for a while.

I had been using 12.04/10 on my HP 6735s laptop without issue's.

Webcam had been working as well, but since upgrading to 13.04 the webcam no longer works. 

It doesnt even show in the 

```
lsusb
```

or 

```
lspci
```

I have followed [http://www.linlap.com/hp-compaq_6735s](http://www.linlap.com/hp-compaq_6735s) through the link for webcam, and nothing.

Tried Cheese, and Skype. Both showing no video (no webcam selectable)

When running ```
gstreamer-properties
``` i get this output:

```
(gstreamer-properties:23567): Gtk-WARNING **: Unknown property: GtkDialog.has-separator

(gstreamer-properties:23567): Gtk-WARNING **: Unknown property: GtkDialog.has-separator
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device "/dev/video0". [v4l2_calls.c(493): gst_v4l2_open (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1:
system error: No such file or directory]

```

Please can someone help?? :(:(

---

### Post by sanderj on 2013-05-04
When you live-boot  12.04/10  (from stick/CD), the webcam works? If so: can you post the lsusb USB id and the output "dmesg | grep -i video"?

Disclaimer: I'm no webcam expert at all, but hopefully the above gives a lead.

---

### Post by Squidge1980 on 2013-05-05
Hi sanderj,

Thank you for your reply.

I have just tried it via LiveCD[USB], but it still does not show the webcam. I get the same output.

Here is the output from the above grep cmd:

```
$ dmesg | grep -i video
[    0.770688] pci_root PNP0A03:00: ignoring host bridge window [mem 0x000cc000-0x000cffff] (conflicts with Video ROM [mem 0x000c0000-0x000ce9ff])
[    1.148086] pci 0000:01:05.0: Boot video device
[   16.648460] ACPI: Video Device [IGFX] (multi-head: yes  rom: no  post: no)
[   16.648679] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:00/LNXVIDEO:00/input/input4


```

---

### Post by sanderj on 2013-05-05
You tried a 12.x liveCD, right? And the webcam was not there? 
In your original post you said "Webcam had been working as well,"?

---

### Post by Squidge1980 on 2013-05-05
@sanderj,

Correct it was working. I am doing a fresh install of 12.10 at the mo, so will get back once complete

---

