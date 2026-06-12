---
title: "Canon mfp scangearmp2"
date: 2022-08-30
forum: Hardware
---

### Post by col48 on 2022-08-30
My Canon MG4250 mfp has served me well when my Ubuntu was 16.04 Xenial and now I want it to do the same in 22.04 Jammy.

I have got printing working - including sending prints to queue up when the device has not yet been turned on, as I often don't need to print or scan in a day so don't 'automatically' turn it on at boot time.

Under 16.04 I used scangearmp (NB no '2') for scanning - I have a dim memory of not being able to get SANE or simple-scan to work or do what I want when I was setting it up some years ago.
So I want to use scangearmp or scangearmp2 in 22.04.

simple-scan works (but as far as I can see only saves to pdf, when I usually want to save to an image format).

But scangearmp2 (installed using synaptic) cannot find a scanner.  I don't think synaptic added any dependencies.

The following Terminal outputs (run while the mfp was turned on but idle) may be informative:
```
scanimage -L
Error my backend :	out of memory
device `pixma:MG4200_192.168.1.107' is a CANON Canon PIXMA MG4200 multi-function peripheral
device `airscan:w0:Canon MG4200 series-2' is a WSD Canon MG4200 series-2 ip=192.168.1.107

```The out of memory issue is strange.  I watched the resources graphs in System Monitor as the command ran and there was barely a twitch in CPU or Memory.  Plenty of both idle.

```
simple-scan
Error my backend :	out of memory

(simple-scan:13757): Gdk-WARNING **: 14:10:17.861: Tried to map a popup with a non-top most parent

```Despite these messages, simple-scan worked.

scangearmp2 just spends a while looking for scanners and then reports in a popup that it can't find any.

I am used to scangearmp and would like to get it (or its successor scangearmp2) to work.  Any help would be appreciated.

(But caring duties mean I can't keep a constant watch on the forum, so I apologise in advance for any seemingly slow response to any replies)

---

