---
title: "Screen has black squares intermittently - &quot;BadWindow&quot; messages"
date: 2021-07-11
forum: Hardware
---

### Post by oygle on 2021-07-11
For the last few weeks the screen/monitor on this Dell laptop has been  intermittently having these black squares. They appear for a second or two then disappear. I initiall y thought it was the laptop screen on its way out, but looked at the file .xsession-errors

> 
qt.qpa.xcb: QXcbConnection: XCB error: 3 (BadWindow), sequence: 12983, resource id: 54536997, major code: 18 (ChangeProperty), minor code: 0


Thousands of these messages, but I don't know how frequently that file is cleared ? Found a post at [https://superuser.com/questions/1451901/how-to-suppress-qxcbconnection-xcb-error](https://superuser.com/questions/1451901/how-to-suppress-qxcbconnection-xcb-error) , but that is only how to suppress the messages.

Is this a bug ?  Or how can I fix it please ?

---

### Post by QIII on 2021-07-11
Could you attach an image, please?

If you can't print screen at the time, snap a picture with a cell phone and paste it as an attachment.

---

### Post by oygle on 2021-07-12
> **QIII said:**
> Could you attach an image, please?

If you can't print screen at the time, snap a picture with a cell phone and paste it as an attachment.

To catch it will be very hard, as it goes within a second or two, disappears, then later it may appear again. It is very much like the picture at [https://silicophilic.com/black-box-keeps-flashing/](https://silicophilic.com/black-box-keeps-flashing/)

It does seem to be more prevalent when there are quite a few Firefox windows/tabs open, and as I move from one to the other, the black boxes appear. Different sizes, different positions, so it may be resources ??  I did check the Nvidia driver, to make sure I was using the correct one, and it is.

Relating to that link, I did adjust the brightness a few weeks ago, as it was too dull. The contrasts is not great either, and I can get a deeper/better view when I hook up a large monitor.  Although I haven't done that for quite a while.

Thanks for your help.  :)

---

### Post by Autodave on 2021-07-13
I would hook up another monitor and see if it does it with that.  You may also want to check your connections and try another cable.

---

### Post by oygle on 2021-07-21
> **Autodave said:**
> I would hook up another monitor and see if it does it with that.  You may also want to check your connections and try another cable.

Thanks for your reply. I did have another monitor hooked up, but of course it can only be hooked up as HDMI and it is a reflection/mirror of the laptop. So yes, it did happen on the external monitor, because the source was the laptop.  The laptop screen/monitor is directly connected, internally, there are no external cables (other than when I hook up via HDMI)

---

### Post by Autodave on 2021-07-21
Can you give us make and model of the laptop please?  Also, where did you get the nVidia driver from?  What driver is installed?

---

### Post by oygle on 2021-07-21
> **Autodave said:**
> Can you give us make and model of the laptop please?  Also, where did you get the nVidia driver from?  What driver is installed?

It's a Dell Inspiron 3542 - Specs are at [https://downloads.dell.com/manuals/all-products/esuprt_laptop/esuprt_inspiron_laptop/inspiron-15-3542-laptop_reference%20guide_en-us.pdf](https://downloads.dell.com/manuals/all-products/esuprt_laptop/esuprt_inspiron_laptop/inspiron-15-3542-laptop_reference%20guide_en-us.pdf)

```
$ ubuntu-drivers devices
```

> WARNING:root:_pkg_get_support nvidia-driver-390: package has invalid Support Legacyheader, cannot determine support level
== /sys/devices/pci0000:00/0000:00:1c.4/0000:08:00.0 ==
modalias : pci:v000010DEd00001341sv00001028sd00000653bc03sc02i00
vendor   : NVIDIA Corporation
model    : GM108M [GeForce 840M]
driver   : nvidia-driver-390 - distro non-free
driver   : nvidia-driver-418-server - distro non-free
driver   : nvidia-340 - distro non-free
driver   : nvidia-driver-460 - distro non-free
driver   : nvidia-driver-450-server - distro non-free
driver   : nvidia-driver-470 - distro non-free recommended
driver   : nvidia-driver-460-server - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin

When I look in Synaptic, there is a **nvidia-driver-460** , plus other **nvidia-*****-460** packages installed.  There is also a **X.Org X server -- Nouveau display** driver installed, so I don't know if any conflicts ??

It's either the laptop screen on its way out, or resources. I say resources because although this is a quad code CPU and I think 8 Gb RAM, plus plenty of disk, it is VERY slow the last few months. Applications , try to open, the 'wheel' spins for up to 10 or 15 seconds, plus a number of apps just don't load. Have to keep trying until they do.

Oops, I just realised I should have **470** installed, as per the bash display

---

### Post by oygle on 2021-07-21
Have now installed nvidia-driver-470 and uninstalled nvidia-driver-460

---

### Post by Autodave on 2021-07-22
I hope that the 470 driver fixes it, but I doubt that it will.  What happens if you boot the maching using a USB installation stick?

---

### Post by oygle on 2021-07-22
> **Autodave said:**
> I hope that the 470 driver fixes it, but I doubt that it will.  What happens if you boot the maching using a USB installation stick?

Yes, the 470 didn't fix it. What will booting from a usb stick prove or not prove, when the problem is intermittent, and there were hundreds of updates since the initial installation. It is only perhaps matching something now against something that was, so where will that lead to ?

I've just seen this post at [https://ubuntuforums.org/showthread.php?t=2465060](https://ubuntuforums.org/showthread.php?t=2465060) , and looking through that forum and this one, many video problems. What's the solution ?

---

### Post by Autodave on 2021-07-22
Is this one of those with 2 video cards in it?  I believe that it might be.  Is it possible to disable either one of them in the BIOS?  Has the BIOS been updated?

---

### Post by oygle on 2021-07-22
> **Autodave said:**
> Is this one of those with 2 video cards in it?  I believe that it might be.  Is it possible to disable either one of them in the BIOS?  Has the BIOS been updated?

From [https://downloads.dell.com/manuals/all-products/esuprt_laptop/esuprt_inspiron_laptop/inspiron-15-3542-laptop_reference%20guide_en-us.pdf#Cedar_15_specs.indd%3AVideo_1](https://downloads.dell.com/manuals/all-products/esuprt_laptop/esuprt_inspiron_laptop/inspiron-15-3542-laptop_reference%20guide_en-us.pdf#Cedar_15_specs.indd%3AVideo_1) there is only one video card. The BIOS is updated.  Thanks for your help though.

---

### Post by him610 on 2021-07-22
What happens if you remove the nvidia drivers and just use the nouveau driver only?

---

### Post by Autodave on 2021-07-24
I may be wrong, but when I look at the specs from the link that the OP provided, I seem to think that there are 2 cards here: the on-board one and then the nVidia one.

---

### Post by oygle on 2021-09-04
> **him610 said:**
> What happens if you remove the nvidia drivers and just use the nouveau driver only?

Good idea. I'll have to backup everything first though. Nothing worse than no monitor when trying to troubleshoot.

> **Autodave said:**
> I may be wrong, but when I look at the specs from the link that the OP provided, I seem to think that there are 2 cards here: the on-board one and then the nVidia one.

Dell have advised that the nVidia GPU is a chip , and the  integrated GPU is part of the CPU.  There are still thousands of these messages in .xsession-errors

> qt.qpa.xcb: QXcbConnection: XCB error: 3 (BadWindow), sequence: 30742, resource id: 46247738, major code: 18 (ChangeProperty), minor code: 0

Also, noticed this in the boot log

> kernel: nvidia: loading out-of-tree module taints kernel.
kernel: nvidia: module license 'NVIDIA' taints kernel.
kernel: Disabling lock debugging due to kernel taint

The following from ```
inxi -Fzx
```

> Device-1: Intel Haswell-ULT Integrated Graphics vendor: Dell driver: i915 v: kernel bus ID: 00:02.0 
           Device-2: NVIDIA GM108M [GeForce 840M] vendor: Dell driver: nvidia v: 470.57.02 bus ID: 08:00.0 
           Display: x11 server: X.Org 1.20.11 driver: modesetting,nvidia unloaded: fbdev,nouveau,vesa 
           resolution: 1366x768~60Hz 
           OpenGL: renderer: NVIDIA GeForce 840M/PCIe/SSE2 v: 4.6.0 NVIDIA 470.57.02 direct render: Yes

---

### Post by oygle on 2021-09-23
I have made no changes to the drivers. On the 7th Sept I changed the Firefox settings as per  [How To Fix Firefox Black Screen Issue]("https://techcult.com/how-to-fix-firefox-black-screen-issue/") , and there have been no problems since. So I will have to assume that fixed it, and will mark this as solved.

(The "BadWindow" messages still appear in .xsession-errors , however I think that is a QT bug)

---

### Post by oygle on 2021-10-06
Just an update - I have not had the black square issues since following the advice in regards to a Firefox configuration ( [https://techcult.com/how-to-fix-firefox-black-screen-issue/](https://techcult.com/how-to-fix-firefox-black-screen-issue/) ). Currently have 35 tabs open and no black squares at all. So it is fixed/resolved.

---

