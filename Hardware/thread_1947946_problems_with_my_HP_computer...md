---
title: "problems with my HP computer.."
date: 2012-03-27
forum: Hardware
---

### Post by IdanSuper on 2012-03-27
Today I installed Ubuntu 11.10 on the computer, everything works fine except for two problems: the LED of the WI-FI blinking all the time which is connected to some, there I also have another problem with the LED on the silencing of the volume buttons on multimedia (touch buttons) does not change to red when muted, blue all the time .. Thank you!
edit: I have HP Pavillion dv6700 model: hp dv6928US

---

### Post by Mark Phelps on 2012-03-29
Don't mean to be discouraging (as someone may come along with a fix to either of these), but these "special" LEDs and buttons on PCs tend NOT to be supported well in Linux.  All too often, they require special drivers which simply aren't available -- more often the case with laptops than with desktops.

You may simply have to live with these inconveniences to use an OS on the PC that the OEM did not design it to use.

---

### Post by IdanSuper on 2012-03-31
so there are nothing that i can do with it? that's only my problem.. without this annoying led everything will be perfect..

---

### Post by Bucky Ball on 2012-03-31
You might try this:

[http://ubuntuguide.net/stop-the-blinking-wireless-led-light-on-ubuntu-10-10-laptops](http://ubuntuguide.net/stop-the-blinking-wireless-led-light-on-ubuntu-10-10-laptops)

It is for 10.10 but that's fine and I found it here:

[http://ubuntuforums.org/showthread.php?t=1592576](http://ubuntuforums.org/showthread.php?t=1592576)

... (there is also another fix on that link) after digging about here:

[http://us.yhs4.search.yahoo.com/yhs/search?p=HP+Pavillion+dv6700+flashing+led+ubuntu&fr=altavista&fr2=sfp&iscqry=](http://us.yhs4.search.yahoo.com/yhs/search?p=HP+Pavillion+dv6700+flashing+led+ubuntu&fr=altavista&fr2=sfp&iscqry=)

---

### Post by IdanSuper on 2012-04-04
thank you very much I'll try it... and what about the mute led? it can't to change to red when muted? it need to be all the time blue? in windows it's work.. thanks!

---

### Post by IdanSuper on 2012-04-04
oh and I chacked the first method below with add the line on the file and restart and it doesn't work for me.. the wi-fi keeps blinking..

---

### Post by IdanSuper on 2012-04-05
[font=arial]up! Help please!!
[/font]

---

### Post by IdanSuper on 2012-04-08
Up! it doesn't fixed yet..

---

### Post by IdanSuper on 2012-04-10
up! I need help!

---

### Post by IdanSuper on 2012-04-12
[font=arial]up!
[/font]

---

### Post by Mark Phelps on 2012-04-12
OK, so you've been bumping for a week -- with no positive results.

Suggest you go back and read my post #2, especially the part about having to live with the limitation.

When a problem involves special drivers, all to often, it is simply NOT solvable in Linux due to the unavailability of those drivers.

---

### Post by IdanSuper on 2012-04-14
the first problem were seems to solved (WI-FI led) through this command: echo "options iwl_legacy led_mode=1" >> /etc/modprobe.d/wlan.conf in terminal as root, but my second problem with the sound led doesn't, what can I do that when the volume is mute the sound led will be red and not just blue all the time? thanks..

---

