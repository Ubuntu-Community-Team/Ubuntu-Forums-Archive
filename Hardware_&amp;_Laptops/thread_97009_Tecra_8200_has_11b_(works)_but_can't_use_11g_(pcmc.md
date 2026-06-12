---
title: "Tecra 8200 has 11b (works) but can't use 11g (pcmcia)"
date: 2005-11-30
forum: Hardware &amp; Laptops
---

### Post by ubunny on 2005-11-30
Hi,

I have a laptop where it has an internal 802.11b wireless card and a pcmcia 802.11g wireless card also.  I want to use the 11g as this is hooked up to a pigtail antenna giving me an extra db boost on the gain.  This works perfectly fine in XP mode since the 11b has a physical switch (toshiba tecra).  Windows only sees the 11g and away I go.

Ubuntu however, I only get the 11b card to successfully receive the IP from ifup/dhclient commands.  All attempts to get the 11g to receive any signals fail 

have used the networking applet to disable both connections, and this basically takes out any ath0 (11g) /eth1 (11b) references in the /etc/network/interfaces file.

manually, i run 11b and 11g sudo scripts to :
set the essid, and key 

in addition set the 11g card to use 

sudo iwpriv ath0 authmode 2 

for apparent 64 bit encryption but the card lights rather than blink together, blink one then the other back and forth.  Any ideas here?  It's a proxim orinoco gold.

Issue Two:
I would like to stop the ubuntu login from auto-establishing the network connections since this just hangs the bootup.  I can then put my scripts into the startup function of the gnome desktop where I can be in control of my changes to my work-wireless environment.  I know the interfaces file is supposed to help me here, but let's save that for later and just get this to work.

anything that pops into your head (regarding these issues hehe) please reply.

kind regards
u

---

### Post by ubunny on 2005-11-30
[http://ubuntuforums.org/showthread.php?t=96731](http://ubuntuforums.org/showthread.php?t=96731)

this thread seems helpful and I'll try it and repost to my thread on how it went.  Issue Two though, how to kill the auto networking would really help.

thx

---

