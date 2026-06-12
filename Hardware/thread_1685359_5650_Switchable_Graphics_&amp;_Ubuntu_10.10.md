---
title: "5650 Switchable Graphics &amp; Ubuntu 10.10"
date: 2011-02-10
forum: Hardware
---

### Post by JGignac on 2011-02-10
I have a HP Pavillion DV6-3073ca which has a switchable ATI 5650 and integrated graphics chip.  I have been looking all over the web to find out how I can get this setup working perfectly in UBuntu 10.10 but I have been confused by many different methods and mixed responses from people who use them.
Right now this is the only thing keeping me from using Ubuntu full time.
What I am asking from you guys is what is the most straightforward and reliable way to get this kind of a set up working for me? Do i need to install both drivers? What is an outline of what i need to do?

---

### Post by ubuntuforums on 2011-02-18
I have the DV6-3070ca with the same problem.

All I want to know is how I can use my ATI Mobility 5650 rather than my Intel 4500MHD. I have Counter Strike: Source running, but it's running off of the 4500MHD rather than my 5650 so I'm getting close to nothing in FPS. How can I use my 5650 instead?

---

### Post by adduds on 2011-03-01
> **ubuntuforums said:**
> I have the DV6-3070ca with the same problem.

All I want to know is how I can use my ATI Mobility 5650 rather than my Intel 4500MHD. I have Counter Strike: Source running, but it's running off of the 4500MHD rather than my 5650 so I'm getting close to nothing in FPS. How can I use my 5650 instead?

i had to go into the bios of my acer

Graphics: Switchable (change to discrete) as long as you have fglrx driver installed should work mate :) basically forces xorg.conf to auto recognize your radeon

ps i'm jealous i can't get cs:s to load when i launch through steam or wine programs steam cs:s :(

---

### Post by argiebong on 2011-03-01
Hi, I also have a dual graphic card laptop, MSI CX420. I also looked for solutions but I don't believe there is one yet. You can either use one of the graphic cards from boot up through bios but not both. There is also a driver for ATI cards for Ubuntu in their site.

---

### Post by Yellow Pasque on 2011-03-01
If you want to use fglrx/Catalyst, you must disable the IGP (if possible). If your BIOS doesn't allow you to turn off the IGP, you're screwed in terms of using fglrx. You can still use open-source drivers and the vga_switcheroo (google it) script to switch back and forth.

---

### Post by argiebong on 2011-03-01
> **Temüjin said:**
> If you want to use fglrx/Catalyst, you must disable the IGP (if possible). If your BIOS doesn't allow you to turn off the IGP, you're screwed in terms of using fglrx. You can still use open-source drivers and the vga_switcheroo (google it) script to switch back and forth.

Thank you very much. This is very useful.

---

