---
title: "Intel 945GM Screen Resolution in VBox/XUbuntu on Vista"
date: 2008-10-25
forum: Hardware
---

### Post by diemseven on 2008-10-25
Hello All:

Thanks for having these forums available and for all your work with Ubuntu.

I am a very new Linux user and have noticed that my issue is a very difficult one to answer - at least according to my research up to now.

I am running XUbuntu in Sun XVM VirtualBox 2.0.4 and cannot seem to find the right way to get my video settings to operate at the correct resolution.

I want to run 1280x800@60 on an Intel 945GM Integrated Controller. Right now, I am only able to run in 640x480 and 800x600.

I tried running sudo dpkg-reconfigure -phigh xserver-org, and got no video setting options (just keyboard).

I also tried running and installing 915resolution, but it does not recognize my Intel chipset, which I *assume* is because I am running in VirtualBox, which is passing the driver settings to XUbuntu.

To make a long question short: Does anyone know how to get an Intel 945GM to work in XUbuntu on VirtualBox 2.0.4?

Thank you for your time.

DiemSeven

---

### Post by mikewhatever on 2008-10-25
Try running <sudo displayconfig-gtk>. I am not sure Xubuntu has the tool, but a bit of guessing wouldn't hurt.

---

### Post by diemseven on 2008-10-25
Thank you for your reply. I found the fix, which is running Sun xVM VirtualBox Guest Additions, then rebooting (Ctrl+Alt+Backspace). I decided to to do a full reinstall of XUbuntu and following the directions I found here:

[http://srackham.wordpress.com/using-virtualbox-20-to-host-xubuntu-804-on-windows-xp/](http://srackham.wordpress.com/using-virtualbox-20-to-host-xubuntu-804-on-windows-xp/)

I followed the above step-by-step, and even though it is written as instructions for WindowsXP, it worked on my Vista machine.

(!) :D

Thank you again for your reply, mikewhatever.

DiemSeven

---

