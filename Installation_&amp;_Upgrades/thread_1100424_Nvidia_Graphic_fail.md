---
title: "Nvidia Graphic fail"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by Mermariemiau on 2009-03-19
[FONT="Lucida Console"][SIZE="3"][B][COLOR="SeaGreen"]I have an Nvidia 5200go on my laptop, and when I upgraded Ubuntu I had a problem: after upgrading and rebooting it tells me that a fail on Nvidia doesn't let the driver initialize properly i suppose. It only let's me start Ubuntu with a generic configuration. When Ubuntu is loading a windoy pops up saying:

Ubuntu is running in low-graphics mode

(EE) NVIDIA(0) Failed to initialize the nvidia Kernel module please ensure
(ee) Nvidia(0) That there us a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0) That the NVIDIA device files has been created properly
(EE) NVIDIA(0) Please consult the NVIDIA README for details.
(EE) NVIDIA(0) ***Aborting***
(EE) Screen(s) found, but none have a usable configuration

 I would like to know hoy to solve this problem. Thanx for your help.[/COLOR][/B][/SIZE][/FONT]

---

### Post by taurus on 2009-03-19
Have you tried reinstalling nvidia driver for your graphic card in System -> Administration -> Hardware Drivers?

---

### Post by Mermariemiau on 2009-03-19
[FONT="Impact"][FONT="Lucida Console"][SIZE="3"]**[COLOR="SeaGreen"]Well, actually the problem is that I have 2 drivers to choose from, but it doesn't matter which one I choose it doesn't work, I always have to enter on low-resolution mode. Would I have to dlete them and reinstall ?? How could I do it if that is the case ?? My Ubuntu version is 8.10 if that helps[/COLOR]**[/SIZE][/FONT][/FONT]

---

### Post by Mermariemiau on 2009-03-19
[FONT="Lucida Console"][SIZE="3"][COLOR="SeaGreen"]**I uninstalled the driver and reinstalled but still when i start Ubuntu it doesn't recognize my Nvidia driver and I have to go on with the generic one ...**[/COLOR][/SIZE][/FONT]

---

### Post by avtolle on 2009-03-19
As you did not provide any specs for your laptop, I've no idea whether [http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support](http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support) is applicable. I'll hazard a guess that there is an issue with your processor, given the error message, but whether said guess is correct is another matter.

---

### Post by Mermariemiau on 2009-03-20
[FONT="Lucida Console"][SIZE="3"][COLOR="SeaGreen"]**I have reinstalled the Nvidia drivers. Uninstalling them completely and reinstalling them it still doesn't detect my graphic card. When I am able to enter normally (now I am able to enter normally sometimes) it doesn't let me change the resolution (800x600). What can I do ?? I was thinking about installing the new Ubuntu 9.04 Beta hoping that might solve my problem, do you think this might help me ?? Thanx**[/COLOR][/SIZE][/FONT]

---

### Post by taurus on 2009-03-20
Post the output of this command from a terminal.

```
lspci | grep VGA
```

---

### Post by Mermariemiau on 2009-03-22
[FONT="Lucida Console"][SIZE="3"][COLOR="SeaGreen"][B]I have put the command you told me to and it tells me the following:

01:00.0 VGA compatible controller: nVidia Corporation NV34M [Geforce Fx Go5200 64M] (rev a1)

[/B][/COLOR][/SIZE][/FONT]

---

