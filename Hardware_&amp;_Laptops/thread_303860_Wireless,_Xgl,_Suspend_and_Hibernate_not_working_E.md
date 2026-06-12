---
title: "Wireless, Xgl, Suspend and Hibernate not working Edgy and Inspiron 6400"
date: 2006-11-20
forum: Hardware &amp; Laptops
---

### Post by arthur_kalm on 2006-11-20
Hi everyone,

I just want to say that I'm quite disappointed with Edgy at this point in time. I've been using Ubuntu for a while (since Hoary) and found it an amazing distro. When I got this laptop, almost everything worked out of the box with Dapper (what didn't was trivial to set up). I decided to upgrade to Edgy and I'm extremely disappointed with it. Nothing seems to work in Edgy. 


For starters, the wireless refuses to work. I have a Broadcom 1390 WLAN. I followed a couple of guides: [This guide worked **PERFECTLY** in Dapper]("http://www.ubuntuforums.org/showthread.php?t=257684&highlight=inspiron+6400+howto") and I tried [this one]("http://www.ubuntuforums.org/showthread.php?t=297092&highlight=inspiron+e1505+wireless") as well.

The driver installs with ndiswrapper:
arthur@ares:~/laptop_setup/wireless$ ndiswrapper -l
installed drivers:
bcmwl5          driver installed, hardware (14E4:4324) present (alternate driver: bcm43xx)

(this is strange since I blacklisted bcm43xx).

Then, when I tried to set an alias to wlan0, I get the following:

arthur@ares:~/laptop_setup/wireless$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
couldn't add module alias:  at /usr/sbin/ndiswrapper line 717.

](*,) 


Onto XGL, the ATi drivers install fine and work well. However, when I go to try and install XGL, everything becomes unstable with crashes when I try to shutdown as well as the terminals (Ctrl + Alt + F*) are not working, I get some weird coloured lines there. Again, this was working perfectly in Dapper.


Furthermore, suspend and hibernate don't work. When I suspend, it just sits there with a blank screen and doesn't respond to anything. Hibernate has the same effect.


I really want to use Edgy because I get access to new versions of software that I want to use, however, it seems to be extremely unstable and, well, "edgy". Thanks in advance for any help you can provide.

---

### Post by Serenader on 2006-11-21
Same problem. Suspend and Hibernate do not work. I tried a few different things, nothing works. These are really the most important features that are required in any os that claims to support laptops. I am a big fan of linux and I have been using Linux it for quite some time, but I find it annoying to reboot every time.

---

### Post by arthur_kalm on 2006-11-21
Serenader, Dapper worked out of the box with suspend and hibernate (albeit sometimes (rarely) it would fail to suspend or hibernate). Keep and eye on this thread, but if nothing comes up, switch to Dapper like me like me :P

---

### Post by Serenader on 2006-11-21
> **arthur_kalm said:**
> Serenader, Dapper worked out of the box with suspend and hibernate (albeit sometimes (rarely) it would fail to suspend or hibernate). Keep and eye on this thread, but if nothing comes up, switch to Dapper like me like me :P

I dont want to switch back. It takes time and I have to reinstall a whole bunch of other software and configure them. Is there an easy way to downgrade.

---

### Post by Serenader on 2006-11-21
Well, I tried suspend using Dapper Live CD and I have the same problem. Can the problem be laptop specific.

---

### Post by arthur_kalm on 2006-11-21
You have an Inspiron 6400? What hardware?

---

### Post by Serenader on 2006-11-22
> **arthur_kalm said:**
> You have an Inspiron 6400? What hardware?

Its an acer aspire 3000. :-(

---

