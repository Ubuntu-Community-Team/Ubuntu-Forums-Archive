---
title: "[SOLVED] Login screen in wrong resolution."
date: 2008-07-15
forum: General Help
---

### Post by JohnFUSA on 2008-07-15
I installed Ubuntu 8.04 using the Wubi installer. At first login the screen res was fine but after I got to the desktop it was set to large (640x480) after searching through the forums I found out how to change it to suit my monitor, I set this to 1024x768 witch is fine at the desktop. After rebooting the login screen came up in what looks like 640x480 I cant even see the boxes for entering user name and password. I assumed correctly that they were out of sight and logged in blindly. I would like to have the whole screen visible for obvious reasons. I then set my login setting to automatic to see what would happen, I then rebooted and now my desktop is off screen also I now have got the desktop back to normal settings but the login screen is still wacked. If anyone knows how I can correct this please let me know.
 I am new to Linux so please be specific with answers.

My current hardware configuration is: Asus p5ne motherboard
Intel core2 duo 2.2ghz
nvidia 8500 gt 512 mb
Viewsonic ps790 19 inch crt

---

### Post by nwubie on 2008-07-16
Hi JohnFUSA !

You need to save the resolution settings to the X Configuration File so that they're loaded at startup.

I'll assume that you can connect to the internet in Ubuntu. If you haven't done it yet install the nvidia drivers :

System => Administration => Synaptic Package Manager => Settings => Repositories. Tick "Main", "Universe", "Restricted" and "Multiverse". Close and reload. This will ensure that you have access to all the repositories.

System => Administration => Hardware Drivers.
It'll prompt you to install the latest proprietary nvidia drivers.

You may need need to restart the X session by pressing ctrl+alt+backspace

Then from a terminal type 
**gksu nvidia-settings**

Click on server display configuration, adjust the resolution and refresh rate then click on Save to X configuration file so that the settings are used when Ubuntu starts.

---

### Post by JohnFUSA on 2008-07-16
> **nwubie said:**
> Hi JohnFUSA !

You need to save the resolution settings to the X Configuration File so that they're loaded at startup.

I'll assume that you can connect to the internet in Ubuntu. If you haven't done it yet install the nvidia drivers :

System => Administration => Synaptic Package Manager => Settings => Repositories. Tick "Main", "Universe", "Restricted" and "Multiverse". Close and reload. This will ensure that you have access to all the repositories.

System => Administration => Hardware Drivers.
It'll prompt you to install the latest proprietary nvidia drivers.

You may need need to restart the X session by pressing ctrl+alt+backspace

Then from a terminal type 
**gksu nvidia-settings**

Click on server display configuration, adjust the resolution and refresh rate then click on Save to X configuration file so that the settings are used when Ubuntu starts.

Thanks nwubie, I had the driver already installed but the settings part is questionable. In the terminal I typed gksu nvidia-settings and hit return, it asked for my password which I entered then it went to the original prompt, no new window appeared, nothing?

---

### Post by nwubie on 2008-07-16
My mistake, you need to install the nvidia-settings package before the Nvidia X Server Settings utility is available.

Either via synaptics :
System => Administration => Synaptic Package Manager  => browse for nvidia-settings

Or via a terminal : 
sudo apt-get install nvidia-settings

---

### Post by JohnFUSA on 2008-07-16
Thanks very much nwubie that worked like a charm. I would like to learn more about some of the terminal commands. Is there any documentation for an old windows guy like me? (I did use a little bit of dos years ago)

---

### Post by nwubie on 2008-07-16
You're welcome.

Unlike with msdos (command.com came with about 30 different commands) there are way too many commands in Linux to know them all.

Here's a start for the most basic ones :
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[https://help.ubuntu.com/8.04/basic-commands/C/](https://help.ubuntu.com/8.04/basic-commands/C/)

To get a list of all commands starting with one or several characters just input those characters in a terminal and press tab twice. If there's only one command that starts with those characters pressing tab once will autocomplete the command.

To get help about a command type **man** followed by the name of the command. To exit the help press **q**

---

### Post by JohnFUSA on 2008-07-16
Thanks again nwubie all your help is greatly appreciated!!!

---

### Post by Dale Sexton on 2008-07-16
> **nwubie said:**
> My mistake, you need to install the nvidia-settings package before the Nvidia X Server Settings utility is available.

Either via synaptics :
System => Administration => Synaptic Package Manager  => browse for nvidia-settings

Or via a terminal : 
sudo apt-get install nvidia-settings

Done as you said and nvidia-settings are not in Synaptic Package Manager or terminal.

---

### Post by nwubie on 2008-07-16
Make sure you're connected to the internet. Have you done this :
> **nwubie said:**
> System => Administration => Synaptic Package Manager => Settings => Repositories. Tick "Main", "Universe", "Restricted" and "Multiverse". Close and reload. This will ensure that you have access to all the repositories.

Also note that nvidia-settings is only to be used with nvidia cards and the nvidia proprietary drivers installed.

---

