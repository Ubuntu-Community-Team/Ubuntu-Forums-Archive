---
title: "Temperatures Tray Icon"
date: 2007-12-06
forum: Hardware &amp; Laptops
---

### Post by JiminyJones on 2007-12-06
Well, I'm not exactly sure this is the correct forum to post this, so if you're a mod and you think "omg this is sooooo wrong", please move the topic to the appropriate forum.

Moving on, I made a small application that resides in your tray and displays your hard drive and GPU temperatures, here's a screenshot: 
[IMG]http://img406.imageshack.us/img406/6924/screenshotrf4.png[/IMG]

So...anyway, I made this for myself (in C#) because i got tired of going to the terminal and manually checking temperatures, and thought "heck, someone else might need this", so, before you download make sure you have the following:

a) mono - allows you to run C# apps
sudo apt-get install mono
b) hddtemp - allows you to see your hard drive temperatures
sudo apt-get install hddtemp
c) an Nvidia GPU (and make sure you have nvidia-settings in your /usr/bin dir)

If you have everything above installed, it should work - to run it just cd in a terminal to where ever you put it and type "mono ./TempTrayIcon.exe", you can obviously create a launcher the same way.

IMPORTANT: the first time you run it, you'll get a password prompt. that's not me trying to hack your computer and steal your stuff, that's only because you can only run hddtemp with administrative privileges.

So...file's attached, post any feedback/bugs/whatever here.

---

