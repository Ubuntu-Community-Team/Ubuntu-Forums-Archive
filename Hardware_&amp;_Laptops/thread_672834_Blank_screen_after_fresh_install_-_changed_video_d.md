---
title: "Blank screen after fresh install - changed video driver....now wat?"
date: 2008-01-20
forum: Hardware &amp; Laptops
---

### Post by spandanj on 2008-01-20
Hi,

i just did a fresh install of ubuntu 7.10 on Dell inspiron 6400 with ATI radeon mobility X1400.

the FIRST thing i did when it turned on was go to screens and resolution and changed my driver to ati from default. it asked to me log off to take effects. so i did log-off. but i just got blank screen. so i restarted it the the shut down button on my laptop - still blank screen. 

so, then i read a couple forums and did the following in recovery:
                dpkg-reconfigure -phigh xserver-xorg
- chose ATI ->resolution 1280x800 - restarted ===== still blank screen
- same as above but with 1024 - restarted -========== still blank screen

Now, i m gonna try VESA driver....see what happens...

can someone tell me what to do.....(MY GOD, i just installed the system....atleast give me a few minutes with it.)

Thank you for your help

---

### Post by c0met on 2008-01-20
My approach would simply be to reinstall the system. I did a similar thing once and while it's good to learn new things, I couldn't be bothered trying to solve the problem when a re-install was easier.

---

### Post by spandanj on 2008-01-20
PROBLEM SOVLED....DONE!

so, like i said in my first post, i selected VESA again, and then restarted, and it seemed to work. upon restart, i updated my system, and installed the restricted video drivers. Then, i was in business.

I would think that linux, or any other operating system would warn before you select something that is not compatible with your hardware instead of giving you  blank screen.


YOur suggestions about reinstall-----i thought about doing that, but i had just installed the system. PLUS, i didnt know how GRUB was going to handle another linux install. so i didnt wanna do that. 

ANYHOW, problem solved...t hank youu.

---

