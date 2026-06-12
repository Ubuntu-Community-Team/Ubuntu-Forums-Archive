---
title: "Nvidia graphics card problems"
date: 2009-07-20
forum: Hardware
---

### Post by Isoas on 2009-07-20
Hello everyone, I just installed Ubuntu 9.04 and I have a 64 bit Asus laptop with a 9500M gs graphics card. The problem started when I tried to change the visual effects settings under appearance to "Normal". Something automatic happened with my drivers updating or something and then my computer froze. When I restarted I began to continuously get this error message - 

(EE) NVIDIA(0): Failed to load the NVIDIA kernel module
(EE) NVIDIA(0): ***Aborting***
(EE) Screen(s) found, but none have usuable configuration

Then, I get a message telling me that I have to run Ubuntu in low graphics mode. There are a few different options to look at error logs and stuff, but I have no idea what any of them mean.

After that I get a strange screen that says:

"There already appears to be an X server running on display :0. Should another display number be tried? Answering no will cause GDM to attempt starting the server on :0 again. (You can changeconsoles by pressing ctrl-alt plus a function key such as ctrl-alt-F7 to go to console 7. X servers usually run on consoles 7 and higher. "

At that screen i have tried starting the server again on :0, but I get the same screen again. I have also tried pressing ctrl-alt-f7, but that just takes me to a command line. If i just press enter, it gives me the message

"The specified display number was busy, so this server was started on display :1"

When I go to hardware drivers, it says I have:
"NVIDIA accelerated graphics driver (version 180) [Recommended]"

and underneath says:
"This driver is activated but not currently in use."

If I go to NVIDIA X Server settings it gives me the message:
"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

I'm brand new to Linux and have no idea what to do, so I hope I provided enough information. Any help would be greatly appreciated.

-Thanks in advance!

---

### Post by Isoas on 2009-07-21
bump
please can someone help me or at least direct me to a forum where I would get more replies?

---

### Post by wojox on 2009-07-21
Hit ctrl+alt+f1

type sudo dpkg-reconfigure x-server-xorg
then
type sudo /etc/init.d/gdm/start
then
type startx

---

### Post by Isoas on 2009-07-21
Thank you! I am at work right now but will try that as soon as I get home!

---

