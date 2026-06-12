---
title: "Acer Aspire 5100 Suspend Problem on Ubuntu 8.04"
date: 2008-04-16
forum: Hardware &amp; Laptops
---

### Post by waldeck on 2008-04-16
Hi All,

I'm a newbie on Ubuntu but an oldie Red Hat/Fedora Core user. I successfully installed Ubuntu 8.04 on my Acer Aspire 5100 notebook and everything seems to be working perfectly out-of-the-box, wifi, wecam, and the whole shebang. Really great and pleasing!

However, after resuming from suspend my computer beeped and I found some messages which I transcribed below on the system log. I'm not sure what is wrong, since my notebook seems to be working perfectly afterward. Should I bother and restart it?

Waldeck

/var/log/messages excerpt:
Apr 16 07:12:44 platipus kernel: [    3.233567] hda: UDMA/33 mode selected
Apr 16 07:12:44 platipus kernel: [    3.284056] ACPI Exception (exoparg2-0442): AE_AML_PACKAGE_LIMIT, Index (000000007) is beyond end of object [20070126]
Apr 16 07:12:44 platipus kernel: [    3.284063] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.WMID.WMBA] (Node db025f78), AE_AML_PACKAGE_LIMIT
Apr 16 07:12:44 platipus kernel: [    3.287926] Restarting tasks ... <6>usb 1-4: USB disconnect, address 3

---

### Post by Dafty on 2008-05-21
I just upgraded to 8.04 from 7.10 on the same notebook (mines the UK version in case that makes any difference) and find my laptop wont recover at all from suspend. Instead I just get a black screen with white lines flashing all over it. No such problem noticed in 7.10. I've had to disable suspending for the time being.

This is the first report I've seen of the webcam working as well. What application were you using to test it?

---

### Post by waldeck on 2008-05-22
> **Dafty said:**
> I just upgraded to 8.04 from 7.10 on the same notebook (mines the UK version in case that makes any difference) and find my laptop wont recover at all from suspend. Instead I just get a black screen with white lines flashing all over it. No such problem noticed in 7.10. I've had to disable suspending for the time being.

This is the first report I've seen of the webcam working as well. What application were you using to test it?

Hi Dafty,

The sleep problem persists for me, but it mostly works. I simply ignore the "Failed to Suspend" message. Occasionally though, I'll experience a system lock up after some time.

What solved black screen for me was adding the following option to the kernel command line in grub: acpi_sleep=s3_bios,s3_mode

The screen still shows the flashing white lines for a few seconds, and the system will show a lot of disk activity upon resume from suspend to ram, but it should work.

As to the webcam, mine is working with ekiga and also with skype, but it's not working with the Adobe Flash player.

Hope this helps.

Waldeck

---

### Post by Dafty on 2008-05-25
Hmmm. In ekiga setup which video manager did you use? Not that it will help me much I suspect as I still get no device found after trying both V4L and V4L2.

Will give those kernel options a try.


Rich

---

### Post by Dafty on 2008-05-25
Hmm Kernel option made no difference for me.

Under System / Administration / Hardware Drivers do you have ATI accelerated driver enabled? I tried enabling it on my system previously and found that suspend still didn't work, and neither did hibernate. But without it enabled hibernate did work.


Rich

---

### Post by waldeck on 2008-05-26
> **Dafty said:**
> Hmm Kernel option made no difference for me.

Under System / Administration / Hardware Drivers do you have ATI accelerated driver enabled? I tried enabling it on my system previously and found that suspend still didn't work, and neither did hibernate. But without it enabled hibernate did work.

Rich

Hi Rich,

Yes, I do have that set, and I'm running the restricted drivers here, but I don't think this affects the camera. It is possible, although unlikely, that your hardware is slightly different than mine. Here are my relevant details:

lsusb:
Bus 003 Device 003: ID 5986:0100 Bison Acer OrbiCam

lspci:
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]

In ekiga (see the attached screenshot)
  video plugin: v4l2
  input device: USB2.0 Camera
  format: PAL
  channel: 0
  image: (none)

Please notice that AFAIK no special drivers were installed to get it to work, since my camera is Video Class compliant.

Waldeck

---

### Post by Dafty on 2008-06-13
Yep that's a different cam hardware than on my laptop.

Anyway I just completely buggered my ubuntu installation by installing some old packages from a very old ubuntu release :-) So I'll be going back to my original install disc I think and if suspend/hibernate once again work I'll be avoiding 8.04 like the plague.

---

### Post by Dafty on 2008-06-13
Yep re-installed 7.10 and suspend just works, straight off the CD with no other packages or twiddles installed. I therefore conclude that 7.10 is the ultimate ubuntu release and everything post 7.10 is bloated MSEmulating crap :-)

---

### Post by waldeck on 2008-06-13
> **Dafty said:**
> Yep re-installed 7.10 and suspend just works, straight off the CD with no other packages or twiddles installed. I therefore conclude that 7.10 is the ultimate ubuntu release and everything post 7.10 is bloated MSEmulating crap :-)

Oh no! not really. 8.04 is working just fine for me, with very few exceptions. One of them, perhaps the most important for me, is pulseaudio. This is due to lots of incompatibility issues.

Waldeck

---

### Post by bariscicek on 2008-07-21
I have the same problem with suspend that it does not bring screen back. However you could ssh to the machine. I tried to fix the problem, and what I figured out is you need to disable power management and re-enable it. Following commands would that:

```

$ vbetool dpms off
$ vbetool dpms on

```

If you add that to /etc/pm/config.d/dpms file and make it executable with chmod a+x /etc/pm/config.d/dpms , then you'll get the screen with resume. 

That worked for me for my acer notebook.

---

