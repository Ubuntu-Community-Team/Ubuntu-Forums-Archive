---
title: "Getting VGA display to work on laptop without screen."
date: 2019-10-03
forum: Hardware
---

### Post by knowledge-heart on 2019-10-03
Hi Guys,
I have a laptop with ubuntu 18.04 LTS installed on it. It is a thinkpad T400

Recently, the default LCD monitor developed a snag and stopped working. I sent it for repair and understood that the LCD is dead.
I asked the technician to remove the LCD altogether and send the laptop base and LCD back to me.

Now i connected the base to my LCD monitor which i had lying around using the VGA port. The laptop boots up perfectly. I get the GRUB selection screen to choose between windows and Ubuntu.
However once i choose ubuntu, all i get is a purple screen. after sometime, i can see the mouse cursor, and access the tty2 screen with Alt F2.

Basically, Ubuntu is still showing the homescreen on the non existent Laptop LCD and considering this VGA monitor as a second screen towards its right.

I tried the xrandr command in tty2 but it shows an error "Can't open Display".
Is there anyway i can force ubuntu to use ony the VGA port as the display? like Windows+P with Windows 7 etc?
I tried fn key shortcuts,all the things i could try which were suggested on other similar articles. But nothing worked.


I then decided to switch to Kubuntu (which i was procrastinating anyway) to get around this issue. I inserted the bootable USB, But sadly after the Kubuntu screen, all i see is the default kubuntu wallpaper. Even Kubuntu is using the non existent laptop LCD screen to display all the icons and windows.

Please help me out.
I'll try all boot string commands/bash commands you guys ask me to do.

Thanks in advance.

---

### Post by mastablasta on 2019-10-04
try to access system settings in Kubuntu using right click. then you should be able to set default monitor.

or change monitors.xml file:
[https://askubuntu.com/questions/863/change-primary-monitor](https://askubuntu.com/questions/863/change-primary-monitor)
[https://askubuntu.com/questions/1043337/ubuntu-18-04-login-screen-display-settings](https://askubuntu.com/questions/1043337/ubuntu-18-04-login-screen-display-settings)

in my case i changed it via GUI interface. however nvidia still throws the boot sequence to monitor (the large screen) LG TV that is supposed to be off (and is off). They also throw display there in some games such as World of Padman and Battle for Wesnoth (when going full screen).

---

