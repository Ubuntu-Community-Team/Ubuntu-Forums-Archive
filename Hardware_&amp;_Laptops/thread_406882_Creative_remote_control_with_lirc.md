---
title: "Creative remote control with lirc?"
date: 2007-04-11
forum: Hardware &amp; Laptops
---

### Post by idumych on 2007-04-11
I have a creative remote that uses a usb reciever,and I'd like to use it with feisty. I found this brief howto on these forums, but it’s missing some crucial information that I can’t figure out on my own. Could someone please fill in the gaps and write a step by step set of instructions for me please?

> Eureka! now the remote control works!

How-to use the Creative Rm-1500 remote control with sound blaster live! external USB on ubuntu 6.10 Edgy.

1. Install Lirc:
sudo apt-get install lirc

2. Modify /etc/lirc/hardware.conf
LIRCD_ARGS="-d hw:External"
DRIVER="alsa_usb"

4. Edit /etc/lirc/lircd.conf
copied from a section of this file:
[http://lirc.sourceforge.net/remotes/....conf.alsa_usb](http://lirc.sourceforge.net/remotes/....conf.alsa_usb)

5. Edit the file ~/.lircrc

6. reboot

7. sudo /etc/init.d/lirc start

8. Test with irw

9. sudo irexec (can be started at boot as a daemon with the --daemon option)

Thanks!


---

### Post by idumych on 2007-04-12
Still not working...

---

### Post by jimdaworm on 2007-04-13
Hi,

I never quite got this going.  The truth is I havent tried in sometime and never with ubuntu.  This guy claims to have it working under linux and has some documentation here:

[http://ecto.teftin.net/rm1500.html](http://ecto.teftin.net/rm1500.html)

I hope this helps, if you get it going tell me I might try it this weekend.:guitar:

:::EDIT:::
If your refering to this thread its not going to work as the reciever in that card is built into it NOT an exter usb device.
[http://ubuntuforums.org/showthread.php?t=346374&highlight=How-to+use+the+Creative+Rm-1500](http://ubuntuforums.org/showthread.php?t=346374&highlight=How-to+use+the+Creative+Rm-1500)

---

### Post by idumych on 2007-04-13
Thanks for replying

I already downloaded that package a few days ago, and I couldn't figure it out. If that's the only solution I guess I could tinker with it some more.

---

### Post by Faust942 on 2007-04-18
I don't have a USB reciever and only the tiny credit card remote. I have a Toshiba Satellite 4600 running Ubuntu 6.10.

How do you get this working under LIRC?

---

