---
title: "command line and keyboard problems"
date: 2011-01-04
forum: Hardware
---

### Post by Floydicus on 2011-01-04
so im new to ubuntu and ive been searching through forums to try to learn how to use the terminal. ive found a couple links to update the bios in my dell inspiron 1501 laptop and to download a fan controller program, both with problems. the one main problem is with the bios tutorial, the one command that i have to use is sudo getSystemId, and whenever i input this command into terminal i keep getting a message saying command not found, i also have gone into synaptic and even tried using the terminal to install the file libsysbios-bin, but synaptic cant find it and terminal wont install it, some assistance would be greatly appreciated considering im following the instructions perfectly and its not working how they say it should

[http://ubuntuforums.org/archive/index.php/t-896232.html](http://ubuntuforums.org/archive/index.php/t-896232.html)
[http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate](http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate)

the other problem i have is some of my keyboard buttons dont respond right, and im not sure if its because my keyboard is bad or ubuntu is not responding correctly, some of the problems im having are the tab key not responding at all, and some keys not responding when i hold down shift (like the $ or the @, sometimes i have to mash those buttons until they show up), so again, any help or advice would be greatly appreciated

---

### Post by gordintoronto on 2011-01-04
You've got three different problems all mixed together, which makes it hard to help you. To eliminate the third one: when you install Ubuntu, you select a keyboard. I think you selected the wrong one. You might be able to fix this in System/Preferences/Keyboard.

The Dell BIOS update article is dated. Did you actually manage to install libsmbios-bin? There is no such file in the current version of Ubuntu. (By the way, what version of Ubuntu did you install?) I did find libsmbios2 in System/Administration/Synaptic Package Manager. (Synaptic is a lot more user-friendly than installing everything from the command line. The advantage of the command line is that you can copy/paste a command more easily than click here, select this tab, click on that box.)

getSystemId is in the smbios-utils package, which you can install using Synaptic. After you have installed it, you can right-click on the package in Synaptic and select "properties," and one of the properties is a list of the files. One of the files should be getSystemId. Upper and Lower case are significant in Linux; Docs and docs are completely different.

In your message, I did not see any problem related to Dell Tweaks. Was there any problem? The Tweaks article is almost 2 1/2 years old, which is five versions of Ubuntu.

---

### Post by Floydicus on 2011-01-04
i have 10.10 installed, and no i didnt manage to install libsmbios-bin, and that was one of the main reasons the dell tweaks article didnt work for me, because i couldnt get that to install i couldnt get the command getsystemid to work, but im going to try downloading the packages you suggested with synaptic package manager, ill let you know if it worked

---

