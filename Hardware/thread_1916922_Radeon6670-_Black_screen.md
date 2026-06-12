---
title: "Radeon6670- Black screen"
date: 2012-01-29
forum: Hardware
---

### Post by livemusic15 on 2012-01-29
Hi everyone, I'm currently experiencing what I believe is an incompatibility issue of some sort. I'm currently using onboard graphics, Nvidia Geforce6150 and everything seems to be working fine.
However, on installing my MSI build Radeon6670 video card, system fails to boot.
After the bios loads up, I get a black screen from which I cannot get past. 
Sometimes it appears to have a strip of light above this screen. Is it possible to download a driver or probably use the terminal to correct this. I'm sure it can be done :/

Please....and thanks for all the help in advance. :)

---

### Post by 2F4U on 2012-01-29
Did you try to pass nomodeset as a grub kernel parameter?

This site may have some additional hints on how to debug the problem:

[https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)

---

### Post by livemusic15 on 2012-01-29
> **2F4U said:**
> Did you try to pass nomodeset as a grub kernel parameter?

This site may have some additional hints on how to debug the problem:

[https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)

I did actually and that didn't seem to work.
I guess I'll read there and try again, Thanks.

---

### Post by varunendra on 2012-01-29
How does it work in Live mode?

You may wish to try other boot options as well: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) (for both live and installed sessions)

---

### Post by pme 72 on 2012-01-29
When you originally installed Ubuntu did you elect to install Nvidia drivers for your onboard graphics, Nvidia 6150?

---

### Post by Tk007LwZFJW5ej on 2012-01-29
I have a similar problem, although I didn´t install anything. After a fresh install, booting gives me nothing but a black screen after BIOS. However, I can login and the system works fine if I boot into recovery mode.  

I looked at the link that was posted, and according to the How It Works Section, my boot is failing on step 3:

¨If the kernel supports Mode Setting (KMS), it puts the video card into  its preferred resolution using a frame buffer (vesafb).  The framebuffer  is initialized with a purple background.¨ 

I´ve tried passing 

[code]
vesafb.nonsense=1
[code]

to grub before booting, but nothing changed.

---

### Post by livemusic15 on 2012-01-30
> **varunendra said:**
> How does it work in Live mode?

You may wish to try other boot options as well: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) (for both live and installed sessions)

I've tried these and I still got the same problem :|

No, I do not remember opting to install nvidia drivers....however, it was pre-installed during the installation.

When I try starting in safe mode as mentioned by 'Starkid', my screen now goes purple and looks like one of those old black and white movies 'lol' with all the lines on the display.

---

