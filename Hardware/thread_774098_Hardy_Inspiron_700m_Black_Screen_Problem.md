---
title: "Hardy_Inspiron 700m_Black Screen Problem"
date: 2008-04-29
forum: Hardware
---

### Post by breaddawson on 2008-04-29
Hi,all.

I'm using Dell inspiron 700m and i tried to installed linux on my laptop these days. I've installed 8.04 on it but found Black Screen showed up immediately after i click "Logout"/"Restart"/"Power Off". Keyborad did not respond, so did Hard Disk led. Actually, only power led and the cpu fan is still working. I have to press the power button several seconds to reboot it.

1. At first i think maybe xserver is down, but i can not switch to other terminals using Ctrl+Alt+F(1/2/3....)

2. The display card is Intel i855GM , and the driver was installed automatically by Ubuntu, i can get a 1280*800 resolution and compiz was performing quite well.

3. I checked the system log but found nothing. Actually , there're few messages during the black screen and next restart.

4. I'm using gnome,and i thought it may be caused by GDM, so i configured unbuntu to boot to a prompt line mode. and then startx manually. After this , "Restart" & "Power Off" is gone, but i can still get black screen after i click "Logout". I tired to using KDM, the problem remains.

5. Actually , the same problem was there when i tried Debian 4.0 Etch. I tried XFCE , Gnome & FVWM, only fvwm worked fine for me. And that's why i alter to Ubuntu.

6. I don't know if the infos below will help:

1) i've installed Winxp SP2,too.
2) Swap is 1G and on hda7
   Ubuntu is 6G andon hda8
3) I installed ssh server, and tried to use another pc to login to my machine. The connection is broken after Black Screen.


Did someone encounter the same problem? Or does someone is delight to help me? Thank u very much!....and if there's some infomation i should offer, plz let me know.

I really want to run Ubuntu on my laptop.

Thank u very much again.

---

### Post by fs3rp4 on 2008-04-29
I have have this problem to in my Compaq V6210 (1280X800) Nvidia card. Probably is the framebuffer.

---

### Post by breaddawson on 2008-04-29
> **fs3rp4 said:**
> I have have this problem to in my Compaq V6210 (1280X800) Nvidia card. Probably is the framebuffer.
framebuffer?
would u plz give some more details on this?
thank u very much!

---

