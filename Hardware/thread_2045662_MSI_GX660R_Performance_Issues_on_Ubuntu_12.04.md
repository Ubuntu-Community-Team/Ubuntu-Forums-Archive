---
title: "MSI GX660R Performance Issues on Ubuntu 12.04"
date: 2012-08-21
forum: Hardware
---

### Post by dwigyit on 2012-08-21
I'd been having problems with my MSI GX660R on Ubuntu 11.10, but almost all were fixed in Ubuntu 12.04. The performance issue, however, remains, and I was wondering if someone could help me resolve it.

Boot time is really long, even when compared to very old laptops running the same OS, and is anything from 40 seconds to over a minute -even after BIOS - before the login screen is reached. It then typically takes over five or even over ten seconds to get into Unity (depending on whether I've logged in before since a reboot), whch is much longer than on other laptops. Loading applications like Firefox and even lightweight ones like Audacious is also slower than on other, less powerful laptops, by quite a few seconds, and there seems to be constant HDD activity during the loading time.

Despite this, Windows 7 on the same laptop boots very quickly, so I'm convinved it's an Ubuntu issue. I just did a quick test and Ubuntu booted in 49 seconds compared to Windows 7 only taking 24. I've never seen Ubuntu over twice as slow as Windows before.

I made an AskUbuntu question about it, but didn't get very far. Hopefully here it's easier for me to reply here with the output of any commands you might want.

Thanks for any help :)

---

### Post by howefield on 2012-08-21
So moved.

---

### Post by dwigyit on 2012-08-24
Here's the output of the commands which I was asked for in the AskUbuntu question - in case they are of any help to anyone:

Bootchart -  [http://imageshack.us/photo/my-images/4/bootchartl.png/](http://imageshack.us/photo/my-images/4/bootchartl.png/)

Output of dmesg: [http://paste.ubuntu.com/1081359/](http://paste.ubuntu.com/1081359/)

Output of /var/log/kern.log : [http://paste.ubuntu.com/1081363/](http://paste.ubuntu.com/1081363/)

Output of /var/log/syslog : [http://paste.ubuntu.com/1081365/](http://paste.ubuntu.com/1081365/)

---

### Post by dwigyit on 2012-08-27
I'm now quite convinced it's a hard disk access problem - the HDD light flashes like mad for over a minute after I log in and programs are really slow to load/use during that time. Any cold-started program takes longer than on other machines to open - even though they should be much faster given the relativly high-spec hardware. 

Programs, once loaded, are really quick (when it's just processor and RAM at work), so that's why I think the HDD is the issue. Well, Ubuntu's handling of it; it works fine on Windows.

---

