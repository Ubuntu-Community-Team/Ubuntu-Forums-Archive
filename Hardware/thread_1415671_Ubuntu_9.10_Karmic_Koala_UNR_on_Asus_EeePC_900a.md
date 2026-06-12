---
title: "Ubuntu 9.10 Karmic Koala UNR on Asus EeePC 900a"
date: 2010-02-25
forum: Hardware
---

### Post by Sven6210 on 2010-02-25
[COLOR=black][FONT=Verdana]As I have received the question several times in the last couple of weeks I would like to post here a small manual of the modifications necessary in Ubuntu 9.10 Karmic Koala UNR to run smoothly on an Asus EeePC 900a - at least on my one.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]The original Ubuntu installation had the following two problems:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]1. [/FONT][/COLOR][COLOR=black][FONT=Verdana]The WiFi/wireless key on the keyboard was not working properly[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]2. [/FONT][/COLOR][COLOR=black][FONT=Verdana]The microphone did not work properly[/FONT][/COLOR]
 
**[COLOR=black][FONT=Verdana]1. WiFi/wireless key on the keyboard[/FONT][/COLOR]**
[COLOR=black][FONT=Verdana]I was able to switch the wireless off but when switching it on I had to restart the computer before I was able to reconnect to the wireless network.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]All I had to do was pass the following parameters to the kernel command line:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]pciehp.pciehp_force=1 pciehp.pciehp_poll=1[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]The detailed steps:[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]1. sudo gedit /etc/default/grub[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]2. edit the line with GRUB_CMDLINE_LINUX_DEFAULT and change it to:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]GRUB_CMDLINE_LINUX_DEFAULT="pciehp.pciehp_force=1 pciehp.pciehp_poll=1 quiet splash"[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]3. sudo update-grub2[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]4. Restart the system[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Now you can toggle WiFi/wireless on and off - you get reconnected to the wireless when you switch it on again.[/FONT][/COLOR]
 
 
**[COLOR=black][FONT=Verdana]2. Adjusting the microphone[/FONT][/COLOR]**
[COLOR=black][FONT=Verdana]The microphone had a lot of background noise and the usage of Skype/Ekiga was not possible with the original setting.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I had to ajust the ALSA configuration file (/etc/modprobe.d/alsa-base.conf) in order to solve this issue[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]The detailed steps:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]1. sudo gedit /etc/modprobe.d/alsa-base.conf[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]2. Search in the file whether a line including 'snd-hda-intel' exists, if so please delete that line[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]3. Add the following two lines to the configuration file:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]===start here===[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]# eeePC 900a patch[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]options snd-hda-intel index=0 model=quanta[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]===end here===[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]4. Restart the system.[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Verdana]With these two changes my Asus EeePC 900a works very well with Ubuntu. Currently I only have some trouble with my UMTS device from Huawei (the E5830). Apart from that everything works very well and I like Ubuntu 9.10 a lot. I am looking forward to the Ubuntu 10.04[/FONT][/COLOR]

---

### Post by mörgæs on 2010-02-25
Thanks! 

Maybe you could add a post on [http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/) pointing to this thread. Would be helpful to a lot of people.

---

### Post by Mal Bridgeman on 2010-04-28
[COLOR=DarkRed]I have installed the Beta 2 of Lucid Lynx on my PC901 and can confirm the WiFi Toggle fix you have documented here works on that.

Previously the Fn+F2 would turn off the WiFi *and* Bluetooth but a reset in BIOS was needed to get them back.

Now the WiFi toggles properly and the Bluetooth is unaffected.

HTH
Mal[/COLOR]

---

### Post by superchef on 2010-05-01
Back when I ran karmic (full desktop version), I tried this and it worked on my eee 900ha (a 900a with a hard drive) allowing me successfully toggle wifi on and off. I've been running the desktop version of lucid on my eee since Beta2, and this procedure did work. When lucid officially came out on thursday, I did a clean reinstall of LL UNR on my 900ha, and this technique still doesn't work.

The error that I get is after I've made the addition to the grub text file. When I run sudo update-grub2, I get this response:

sam@sam-laptop:~$ sudo update-grub2
/etc/default/grub: 10: pciehp.pciehp_poll=1: not found

Any suggestions?

---

### Post by Mal Bridgeman on 2010-05-01
> **superchef said:**
> Back when I ran karmic (full desktop version), I tried this and it worked on my eee 900ha (a 900a with a hard drive) allowing me successfully toggle wifi on and off. I've been running the desktop version of lucid on my eee since Beta2, and this procedure did work. When lucid officially came out on thursday, I did a clean reinstall of LL UNR on my 900ha, and this technique still doesn't work.

The error that I get is after I've made the addition to the grub text file. When I run sudo update-grub2, I get this response:

sam@sam-laptop:~$ sudo update-grub2
/etc/default/grub: 10: pciehp.pciehp_poll=1: not found

Any suggestions?
[COLOR=DarkRed]
I did a clean install on the launched version too and it worked out of the box without having to make this alteration.
HTH
Mal[/COLOR]

---

### Post by superchef on 2010-05-02
I figured out the problem! I did some research online about what pciehp was, and all of the examples that I found showed pciehp.pciehp_force=1 *after* quiet splash. I tried it and it worked.

Therefore, my edit to grub looks like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pciehp.pciehp_force=1 pciehp.pciehp_poll=1 "

...instead of this:

GRUB_CMDLINE_LINUX_DEFAULT="pciehp.pciehp_force=1 pciehp.pciehp_poll=1 quiet splash"

I don't know why it matters what order you put it in, but now my Fn + F2 wifi toggle works! :)

---

### Post by Sven6210 on 2010-05-10
Actually I might also have another explanation for the problems you have. Did you copy/paste from my threat? If you did so, you used

[COLOR=black][FONT=Verdana]GRUB_CMDLINE_LINUX_DEFAULT=”pciehp.pciehp_force=1  pciehp.pciehp_poll=1 quiet splash”[/FONT][/COLOR]
[FONT=Verdana, sans-serif]
instead of

[/FONT][COLOR=black][FONT=Verdana]GRUB_CMDLINE_LINUX_DEFAULT="pciehp.pciehp_force=1  pciehp.pciehp_poll=1 quiet splash"[/FONT][/COLOR]

You can see the difference? In the threat there are the [COLOR=black][FONT=Verdana]”” instead of "". So my mistake. If you use the [/FONT][/COLOR][COLOR=black][FONT=Verdana]”” grub can not "understand" the command and returns an error message.

The right line should be:
[/FONT][/COLOR][COLOR=black][FONT=Verdana]GRUB_CMDLINE_LINUX_DEFAULT="pciehp.pciehp_force=1   pciehp.pciehp_poll=1 quiet splash"[/FONT][/COLOR]

---

### Post by KB8NO on 2011-04-25
A year has gone by since the last post but I'm using Ubuntu 10.10 and the 900a WiFi toggle still has the same problem, turns off but will not turn back on again.  Curiously, I also have a 900 and it toggles fine.  The fix noted here solved the problem.  I initially had the same problem as superchef because pasting the grub line into the terminal program did not work and I got the same "not found" error.  However, when I pasted superchef's line into grub it worked as it was billed.  I looked and looked until I finally figured out the subtle quotation text error as the reason the first paste did not work.  It is nice to have the toggle finally work right on the 900a.

---

### Post by Sven6210 on 2011-05-17
The modification for the WiFi switch is also applicable to Ubuntu 10.04 LTS as well as 10.10. I did not yet install 11.04 but I would not be surprised if I still would need to do it.

---

