---
title: "Selected a language but everything is english"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by jarl on 2009-10-30
Hi.

During installation of Kubuntu 9.10 Karmic (from scratch) I selected danish as my language, but after installation everything is english.

I noticed there was a light-bulb icon in the system tray, hitting that opened up a window explaining that danish was not yet installed, and asked if I wanted to install it. I clicked yes but I ran into same problems as [bug 463435](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/463435)), so it failed. The light-bulb icon is now gone and I seem to be stuck to english.

I am pretty sure the setting are all set for danish language, but the packages are not installed. How do I (graphically) start the "light-bulb" application again to ask me to install danish?

Jarl

---

### Post by jarl on 2009-10-30
I find these old posts (from 2006)
[http://ubuntuforums.org/showthread.php?t=129506](http://ubuntuforums.org/showthread.php?t=129506)
[http://raviratlami1.blogspot.com/2006/10/how-to-add-another-language-and.html](http://raviratlami1.blogspot.com/2006/10/how-to-add-another-language-and.html)

In both posts it says I shoud go to System > Administration > Language Support. But on my newly installed Karmic there is no "Administration" in the "System" menu.

Anyway I would expect the light-bulb applicatino to show up in the system tray as long as I have not installed the language support for the selected/configured language.

Jarl

---

### Post by pro003 on 2009-10-30
thats not possible, you just cant see it... upper left corner of your screen, theres Applications - Places - System --------all with their sub menus... you just take a good look again.

---

### Post by jarl on 2009-10-30
To reproduce my experience (in any languag) Do the following:

1. Install Kubuntu (maybe also ubuntu) from CD (with no network attached, not even wireless), but choose you a non-english language

2. When installation is finished and booted first time, there is a light-bulb in the system tray. Click that and it will ask you to install your language, click OK, continue as far as you can, but it will eventually fail due to lack of network. The light-bulb will be gone by now.

3. Reboot with network. Now the light-bulb is gone, so you wont be asked again to install your non-english language.

Jarl

---

### Post by jarl on 2009-10-30
> **pro003 said:**
> thats not possible, you just cant see it... upper left corner of your screen, theres Applications - Places - System --------all with their sub menus... you just take a good look again.

OK. I use Kubuntu, so things may be a little different. First of all there is nothing in upper-left corner.

I click on the "K" in the lower left corner  of the screen. Here I options for different menus I have "Favorites", "Application", "Computer", "Recently Used", "Leave". In "Applications" I find "System", but there is no "Administration".

Jarl

---

### Post by mgc8 on 2009-11-04
@pro003 -- Please pay attention to what people write, he stated clearly he was using **K**ubuntu, which does not have any top bar like the Gnome variant, and obviously the settings are different!

@jarl -- I had the same problem, you can solve it like this:
1. Go to K -> Settings -> System Settings (it may also appear under "Favorites")
2. Choose "Regional and Language", then "Select System Language"
3. The prompt to install language-packs should appear again, let it complete, afterwards you should be able to choose the language from a list.

HTH,
Mihnea

---

