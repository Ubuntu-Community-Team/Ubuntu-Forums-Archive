---
title: "Ubuntu server login issue"
date: 2008-11-08
forum: General Help
---

### Post by L815 on 2008-11-08
I installed Ubuntu server, after that I installed xorg, slim, and fluxbox.

When I boot up, x starts slim just fine, but when I go to type something, or move my mouse nothing happens. 

I tried again but with gdm, same thing.

Anyone know what the issue is?

---

### Post by bodhi.zazen on 2008-11-08
what kind of mouse ?

---

### Post by L815 on 2008-11-09
Both the touchpad and the usb mouse don't work.

---

### Post by bodhi.zazen on 2008-11-09
Probably not what you want to hear, but can you try a ps2 mouse ?

I was asking more about the specific hardware, it manufacture of mouse / touchpad

And version of Ubuntu ?

Can you post your /etc/X11/xorg.conf ?

---

### Post by L815 on 2008-11-09
I can't because I don't have a ps2 slot on my laptop.

As for model, touchpad I believe is  synaptics, and usb mouse is a logitech.

It works fine when I use or install Ubuntu (non-server). I only get this problem with server. 

.....
Surprisingly my xorg configuration file is empty :lolflag:
So, I ran dpkg-configure xserver-xorg
Rebooted
Same issue

I'm going to try copying over the Ubuntu Live CD xorg over to this installation and see what happens before we try other solutions.

---

### Post by bodhi.zazen on 2008-11-09
Interesting, I am sorry but I do not know the answer. I assume you are on 8.10 and the issue is with the new X. The new X is supposed to "automatically" detect your mouse and other hardware and it is difficult to manually configure when automatic detection fails. I will watch this thread with some interest though.

Options may include, falling back to 8.04 (has an advantage on servers as 8.04 is LTS) or installing ubuntu-desktop.

---

### Post by L815 on 2008-11-09
My apologies. I forgot to mention the version I'm using, which is Ubuntu server 8.10.

---

### Post by bodhi.zazen on 2008-11-09
One other suggestion, copy the xorg.conf from an older version of Ubutnu.

---

