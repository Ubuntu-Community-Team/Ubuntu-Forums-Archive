---
title: "Dual-booting Ubuntu and Debian"
date: 2008-11-25
forum: Hardware
---

### Post by Mostly Harmless Eccentric on 2008-11-25
So, I have a laptop, and some time ago, I put Ubuntu on it, occupying the whole drive. Recently, I've decided I wanted to sample a different distro and settled on setting up a dual-boot with Debian, and having a shared space in between to keep data I want to use on both. I want the data partition mounting at start-up on both sides. I haven't quite managed it in Ubuntu yet, and any suggestions would be helpful. I found a guide for it that I followed, but it didn't seem to work.

However, my main question is if I can possibly use the original Ubuntu install, which is exactly how I want it and in perfect working order, to fix the Debian side, given that I find I'm able to mount the Debian partition and manipulate it from the Ubuntu side (Though I haven't done it yet). 

The problem I'm having with Debian is a relatively minor one, compared to what could be going wrong. It boots OK, no problems with it and grub, no issues logging in, and everything in the file system seems to be in the right place and working properly. The only problem I'm having is that it will only boot directly to terminal. It gives an error message that talks about problems with X-Window Server, about not being installed and/or configured. I look at the info it gives you about the problem and the only places where anything seems out of order are a couple entries near the bottom:
"Fatal error: No screens found"
"(EE)No devices detected"
"(==)Using config file "/etc/X11"

I'm not sure yet if the internet is working on the Debian side. I don't think it is. That's why I was hoping I could use Ubuntu to fix it: they're fairly close systems, both with Gnome desktops by default. I was hoping I could use that to get Debian working properly, then once Debian will start Gnome, then I could switch it to KDE, which is what I want over there. So, basically, does anyone know a way I can use Ubuntu to get Debian's desktop working, or failing that, how I can get the desktop there working at all?

---

### Post by Mostly Harmless Eccentric on 2008-11-25
Also, when I went to resize my partitions, I discovered the default swap space it had set up when I was running Ubuntu alone was 8GB, which seems unusually high. I tried setting it lower, but discovered lowering it had obvious effects on Ubuntu's performance. Why does it seem to require so much?

---

### Post by Sef on 2008-11-25
> Also, when I went to resize my partitions, I discovered the default swap space it had set up when I was running Ubuntu alone was 8GB, which seems unusually high. I tried setting it lower, but discovered lowering it had obvious effects on Ubuntu's performance. Why does it seem to require so much?

8 GB is way too much swap.   The [swap partition]("https://help.ubuntu.com/community/SwapFaq?action=show&redirect=SwapSpace") should be 1 GB at the most, though you can go up to 2 GB.  But anything else is too much.

---

### Post by Mostly Harmless Eccentric on 2008-11-26
That's what I thought, but when I decreased it, everything slowed down to a crawl, and sped up right away when I put it back. How do I get it behaving?

---

