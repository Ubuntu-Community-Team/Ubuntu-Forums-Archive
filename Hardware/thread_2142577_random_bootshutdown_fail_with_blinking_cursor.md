---
title: "random boot/shutdown fail with blinking cursor"
date: 2013-05-06
forum: Hardware
---

### Post by debili on 2013-05-06
Hello.

I've recentlu installed 13.04 after a year of using 12.04, since then I have some issues with startup and shutdown. If i leave my  /etc/default/grub > GRUB_CMDLINE_LINUX_DEFAULT at the default ´quiet splash' I get a blinkig cursor at the upper-left of my screen and the computer randomly just refuses to boot; same goes for shutdown, it's like my pc would be stuck at this blinking cursor screen for a couple of seconds, then either shuts down, or just stays at this screen, I then have to manually switch off power. Also, I can't access the console while the default 'quiet splash' is set - that is, if I press ctrl+alt+F1...F6, all i get is this blinking cursor again.
now I tried to replace 'quiet splash' with nomodeset - as a result I could access the console from anywhere and login, no blinking cursor either by boot or shutdown, but then the computer would display a lot of text while booting and would boot even more randomly, sometimes stuck at boot; and would continue like when I press ctrl+alt+del; Or switch to ctrl+alt+F1, login and sudo service lightdm start, while F7 keeps stuck; (hope this makes sense)

I've found this info [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/499220](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/499220) , could somebody tell me if this could be a clock pboblem, and what are these clocks anyway, it's the first time I see this mentioned somewhere..Thank you!

would you have some suggestions on what could be the problem here? Is it safe to play around with the clock settings?

---

### Post by debili on 2013-05-06
I read in another post [http://ubuntuforums.org/showthread.php?t=1613132&highlight=clock+grub+boot](http://ubuntuforums.org/showthread.php?t=1613132&highlight=clock+grub+boot) that the boot options(you set for grub) also influence 'thermal events' - don't know if that might be related, but my pc also overheats... it's now 60degrees by idle, i've re-fitted the heatsink already but it didn't change, no matter at which RPM i set my cup&case fans, somehow it seems that the temps stay the same 45-60 idle, 80-85 when under full load... that's not ok i guess :/ there's also weird values on some sensors, especially CPUTIN: which is either -60, or +123,5 like now.
I've flashed my BIOS to the newest version a few months back, if that may mean something...

Thanks in advance for any input, I'm lost :(

---

### Post by debili on 2013-05-07
anyone?

---

