---
title: "Thinkpad X31 video issues with Xubuntu 7.10"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by camdecoster on 2008-01-10
I recently installed Xubuntu 7.10 (Gutsy) on my Thinkpad X31. Everything appeared to work correctly with the Live CD and installation, but when I rebooted, the splash screen wouldn't display and the boot time was around 3 minutes to get to the login screen (when video finally showed up). Looking at the screens and graphics applet, I saw that the VESA driver was being used. Does this mean that there is an issue with the video card? I've installed Ubuntu gutsy on this laptop before with no problems, so I don't understand why xubuntu wouldn't work correctly. Any ideas?

---

### Post by camdecoster on 2008-01-11
Bump.

---

### Post by xeth_delta on 2008-01-11
Have a look at "/var/log/Xorg.0.log" and search for the lines starting with EE, those describe errors.
Can you repeat the problem after rebooting?

Xeth

---

### Post by camdecoster on 2008-01-11
I'll have a look at the log file when I get home. When I reboot, the long boot time is still there. I should mention that I tried changing the video driver to ati and radeon, but it made no difference.

---

### Post by xeth_delta on 2008-01-11
> **camdecoster said:**
> I'll have a look at the log file when I get home. When I reboot, the long boot time is still there. I should mention that I tried changing the video driver to ati and radeon, but it made no difference.

How did you change it? From /etc/X11/xorg.org? I say change the driver to radeon, and check whether you gave hardware acceleration:
```
glxinfo | grep -i direct
```

---

### Post by buellman on 2008-01-11
I think its a well known bug.
You have to edit /etc/usplash.conf
Change the Resolution to: xres=1024 yres=768
Then do
sudo update-initramfs -u -k `uname -r`
reboot

Greets. Buellman

---

### Post by camdecoster on 2008-01-11
Can you post a link to the bug report? I tried that line of code and it didn't work.

---

### Post by buellman on 2008-01-12
No. Sorry. I don't know the link to the bug report but if you search in the forum you will find ppl with the same problem.
I have a X31 to and for me editing the line fixed the problem.

Greets. Buellman

---

### Post by camdecoster on 2008-01-12
buellman, I got it to work. The 'uname -r" part didn't work, but I replaced it with 'all' and that fixed things. Thanks for everyone's help. This thread can now be closed.

---

### Post by buellman on 2008-01-13
Nice to hear, that it works now for you :-)

Greets. Buellman

---

### Post by ageilers on 2008-01-27
Worked great for me. Faster boot time and splash screen is visible. I will be trying this on my T23 for fixing the splash screen resolution.

---

