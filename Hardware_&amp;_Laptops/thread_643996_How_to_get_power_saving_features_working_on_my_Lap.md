---
title: "How to get power saving features working on my Laptop"
date: 2007-12-18
forum: Hardware &amp; Laptops
---

### Post by Gillimaster on 2007-12-18
Hello everyone.

I am fairly new to Ubuntu. I have the 7.10 Gutsy release. When I run my laptop off of battery I don't get a choice to set the CPU speed for battery life nor do I get the option to change the brightness of my screen. I tried the live cd version of GNOME and it offered setting the CPU speed under power manager 2.20 but it also didn't allow to dim the screen. If I were able to do these 2 things I would be able to get rid of my windows xp. If anyone could help me out or point me in the right direction I would appreciate it.

My laptop is a Fujitsu T4010 (tablet pc). 1.6GHz Pentium M and 1GB Ram

Thank you!

---

### Post by jpittack on 2008-02-13
Before you choose an option for booting into an OS/Kernel at the GRUB start up screen, you should be able to use your hot keys that you use in XP to change the screen brightness.  It will be permanently set at that brightness, although I sometimes try to use the hotkey again, and it defaults to full brightness.  After you find a comfortable level of brightness, choose to boot into Ubuntu.

If you are comfortable using the terminal, you will be able to adjust the CPU speed through an easy applet.

Right click on the top panel, and choose "add to panel".  From there, find the cpu frequency scaling applet.  Add it in.  This will only report what is going on.  To gain control over the CPU, folow the next commands.

Open a Terminal from Applications>Accessories>Terminal.  Enter the following command and put in your password afterwards.  The password will not show up on screen.

> sudo dpkg-reconfigure gnome-applets

Reply Yes to the question with enter.  Left-click the applet, and choose either a frequency or a power plan.  On-demand is the default.

If you unplug the laptop, or plug it back in, restart, suspend, hibernate, shut down, or restart, it will reset itself to on-demand.  There is a way to make something else the default, but I do not know how to do that.

Conservative will allow scaling to all frequencies, it just won't do it right away.  Powersave will keep the CPU at the lowest frequency possible.  Performance at the highest.

Let me know if you encounter any problems!

---

