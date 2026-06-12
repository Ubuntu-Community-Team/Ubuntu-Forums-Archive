---
title: "Laptop won't charge when turned on"
date: 2020-03-19
forum: Hardware
---

### Post by cjolley on 2020-03-19
Hi! I'm running Ubuntu 16.04 LTS on a Dell XPS 13 laptop. I'm using a StarTech USB-C dock to connect to a monitor, keyboard, etc. The dock is a little flaky sometimes (e.g., I need to make sure my laptop is already open when I connect to it, or it starts in low-graphics mode), but generally OK.

Until... I moved everything from my office to my home earlier this week for "social distancing." Now, suddenly, the battery no longer charges while I'm using the dock. However,
[LIST]
[*]It charges just fine when I use the original charger from Dell (unfortunately I can't do this while also using the dock)
[*]It charges using the dock when it's turned off or suspended, just not while I'm actually using it.
[*]In addition to moving, I also updated my kernel to 4.15.0-91-generic on Monday. This is probably the real problem.
[/LIST]

I'm going to try rolling back to a previous version of the kernel, but in the meantime I'm curious whether anyone else is seeing this problem.

--craig

---

### Post by cjolley on 2020-03-20
UPDATE: I tried restarting with a few different kernels (going back to 4.4.0-176-generic); none of them seem to solve the problem. So if it's not the kernel, I really don't know what's wrong.

I also tried running upower --monitor; the power daemon reacts when I plug/unplug the Dell charger, but not the USB-C cable connected to the StarTech dock.

---

### Post by him610 on 2020-03-20
Maybe you should consider a Dell dock, [https://www.amazon.com/Dell-Display-Docking-Station-D3100/dp/B00O0M46KO/?tag=wpcentralb-20&ascsubtag=UUwpUdUnU67546YYwYg]("https://www.amazon.com/Dell-Display-Docking-Station-D3100/dp/B00O0M46KO/?tag=wpcentralb-20&ascsubtag=UUwpUdUnU67546YYwYg")
Might be more likely to work for you. 
If you are working from home, you don't want to be short with your hardware.

---

