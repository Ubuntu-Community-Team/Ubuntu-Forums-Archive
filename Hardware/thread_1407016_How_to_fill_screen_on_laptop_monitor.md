---
title: "How to fill screen on laptop monitor"
date: 2010-02-14
forum: Hardware
---

### Post by mag357 on 2010-02-14
Hi all, I am very new to using ubuntu and I have a little problem. I am using a Toshiba A25-S207 laptop and have ubuntu installed. How do I get ubuntu to fill the screen? I have a black border of about 1 3/8" around the ubundu window can someone help me with this?
Thanks in advance.

---

### Post by efflandt on 2010-02-14
It is very unusual for Linux to not automatically use full screen on a laptop.  Are you using standard Linux modules, or any proprietary video driver?  What kind of video does **lspci** say it is (or **sudo lspci -v** for more detail)?

What is your native screen resolution?  Does /var/log/Xorg.0.log give any clue what it sees and why it does not use that resolution?  What is the output of **xrandr**?

---

### Post by mag357 on 2010-02-14
> **efflandt said:**
> It is very unusual for Linux to not automatically use full screen on a laptop.  Are you using standard Linux modules, or any proprietary video driver?  What kind of video does **lspci** say it is (or **sudo lspci -v** for more detail)?

What is your native screen resolution?  Does /var/log/Xorg.0.log give any clue what it sees and why it does not use that resolution?  What is the output of **xrandr**?

Excuse my ignorance, but where do I look for the lspci or xrandr I am not familiar with those terms, sorry. But my laptop is using or set at 1024x768 resolution and the driver is:Trident CyberALADDIN-P4) V6.4616.22ICD_SE_NP

Thanks very much for your reply.

---

### Post by John_T on 2010-11-02
I suspect the OP has long since solved their problem or gone elsewhere, however, this thread showed up when I searched for a solotion to a similar problem, so I thought it would be worth posting here.

I've just installed 10.10 in a Toshiba A25
Initially it would only run at 800x600 with the black border described by the OP.
The display settings wouldn't allow me to go above 800x600, even though the native resolution is 1024x768.

I found [this thread]("http://lovinglinux.ubuntuforums.org/showpost.php?p=9543822&postcount=7"), which describes modifying the xorg.conf file.

I didn't *have* an xorg.conf file, but creating one as shown solved the probelm perfectly when I logged out and back in again.

---

