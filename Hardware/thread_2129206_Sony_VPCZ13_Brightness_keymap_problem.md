---
title: "Sony VPCZ13 Brightness keymap problem"
date: 2013-03-25
forum: Hardware
---

### Post by Dr.Fuzzy on 2013-03-25
Hi people,

On my laptop (Sony VPCZ13) am running this deamon [https://code.google.com/p/vaio-f11-linux/wiki/AutoDimmingBacklightDaemon](https://code.google.com/p/vaio-f11-linux/wiki/AutoDimmingBacklightDaemon) and these patches [https://launchpad.net/~shiba89/+archive/vaio-kernel](https://launchpad.net/~shiba89/+archive/vaio-kernel) for the ambient light sensor and backlit keyboard to function properly, plus other laptop specific hardware. While everything works OK, for some reason, while in the Unity session, the brightness can be adjusted using the Ctrl-Fn-F5 or F6 combination instead of Fn-F5 or F6. More specifically if I press Fn-F5 or F6 then the brightness bar pops up, the screen brightness goes up to max, and even though the bar increases/decreases the brightness doesn't. If I choose the Ctrl-Fn-F5 or F6 (or even Shift-Fn-F5 or F6) combination the brightness adjusts fine but without the graphic pop up notification. Recently, I accidentally discovered that if I log on to the Xfce desktop everything works fine (Fn-F5 or F6 and graphic pop up notification)! I suspect that my prob has to do something with the way gnome maps the brightness keys and the some conflict with the deamon, but I have no idea how to remap them. So far I've tried different suggestions found here and there, including a popular one which is to insert [COLOR=#000000][FONT=Ubuntu Mono]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [/FONT][/COLOR]**acpi_backlight=*vendor***[COLOR=#000000][FONT=Ubuntu Mono]" in /etc/default/grub, but , [/FONT][/COLOR]even though [COLOR=#000000][FONT=Ubuntu Mono]this [/FONT][/COLOR]allows me to adjust the brightness with Fn-F5 or F6 [COLOR=#000000][FONT=Ubuntu Mono]unfortunately [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]disables the [/FONT][/COLOR][AutoDimmingBacklightDaemon]("https://code.google.com/p/vaio-f11-linux/wiki/AutoDimmingBacklightDaemon") 

Any help, ideas would be much appreciated!

---

### Post by Dr.Fuzzy on 2013-03-26
no one...?

---

