---
title: "External monitor support and suspend/hibernation is very poor"
date: 2011-11-20
forum: Hardware
---

### Post by awesan on 2011-11-20
I was using Ubuntu 10.10 happily for quite a while. I upgraded to Ubuntu 11.04 and started having all problems with external monitor. I use a HP laptop ([FONT=verdana,arial,helvetica][SIZE=-1]**HP Pavilion DV4-2160US) **that has a core-i5 processor with Integrated Intel Graphics card and use 24" external monitor (HP ZR24w - connected thru HDMI). Display would flicker often. If I had booted using external monitor and disconnect the monitor and boot the laptop, display would be blank. If I did the other way around also, sometimes display would go blank. And, I had to work-around by always switching to laptop display before shutting down and switching to external monitor only upon rebooting. Well, it was some trouble but I was dealing with it. Then, I installed "updates" and all hell broke loose. CPU usage was always shooting up to 99% and my laptop became unusable. As I lost faith in upgrading, I formatted and installed Ubuntu 11.10 fresh and the "CPU usage shooting to 99%" problem was gone with external monitor. However, if the display is turned off due to inactivity, it won't come back after a keystroke. Keep in mind that this is not suspend/hibernate scenario and just the display is turned off due to inactivity. I changed all settings to make sure the display does not go blank due to inactivity. All along, suspend/hibernate (10.04 / 11.04 / 11.10) did not work reliably at all. Most of the times, the display won't come back (even while not using the external monitor at all) with suspend/hibernate. I wrote start-up scripts that will launch all the applications, open documents, files and started always shutting down. Then, with Ubuntu 11.10 now, I tried connecting my second monitor (ACER AL1912) through VGA. Again, all hell breaks loose. dbus_daemon uses 90% CPU and the system is unusable. I have used the 2 monitor configuration peacefully without any issues with Ubuntu 10.04. I am very very disappointed with Ubuntu 11.04 and 11.10. I have spoken to my co-workers and people who have been using Fedora still like it and people who have been using Ubuntu have run into issues like mine and are switching to Fedora. All said, I hate to and completely reluctant to install any updates any more also to Ubuntu from the update manager. Windows-7 works fine and Ubuntu 10.04 worked fine except suspend/hibernation, so there are no issues with hardware. Any suggestions/recommendations?
[/SIZE][/FONT]

---

### Post by emilywind on 2011-11-20
It could be related to versions of relevant softwares used in Ubuntu or even to patches put out my Ubuntu. I recommend downloading Fedora 16 or OpenSUSE 12.1 and testing things out via a live USB or live CD of them (no need to install for this). If it works there, then the issue is likely in the versions of the Intel drivers or other things which Ubuntu uses or in patches it has created. From there we can see if there is a ppa which may update the relevant driver software and such. Cheers.

---

