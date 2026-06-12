---
title: "Installing problems with some pics"
date: 2008-11-27
forum: General Help
---

### Post by humby on 2008-11-27
Hello,

I just got Wubi and ran it. Everything went smooth. It said I have to reboot. So I did.

But here's what happens:

I boot Ubuntu.

I press ESC for the menu.

I choose normal install.

The Ubuntu logo shows up and then I end up on a command line screen. If I choose Live CD the same thing happens.

Any ideas?

---

### Post by Ex_Machina on 2008-11-27
i'm not sure but i think you have to reconfigure your graphics card, some googeling on busy box graphics card reconfire would do that job i think ;) i had a similair problem and fixed it that way but i forgot the commands.

====+++==update googeled for you and found the following==+++===

Do this:
sudo nano /etc/X11/xorg.conf

then scroll down the file and get to the Section "Device"
and set the driver to "vesa" like in the following example:
Code:

Driver "vesa"


Press:
CTRL+O to save the file (yes, overwrite it)
CTRL+X to exit

then type:
sudo /etc/init.d/gdm stop (or "kdm stop" if you use Kubuntu)
sudo /etc/init.d/gdm start (or "kdm start" if you use Kubuntu)

credits go to: Pinny Parlour
original threat: [http://ubuntuforums.org/archive/index.php/t-238756.html](http://ubuntuforums.org/archive/index.php/t-238756.html)

---

### Post by humby on 2008-11-27
Tried it but it doesn't work. Doesn't Ubuntu have to be installed first? And I can't get it to install in tge first place. I tried the option to install it in safe graphic mode but it still won't work. And I have no idea what's going on - that's my first attempt at Linux... except for some minor server administration things.

---

### Post by abn91c on 2008-11-28
try typing at the prompt exit then hit enter, you may need to do it twice

---

### Post by ago on 2008-12-01
Select verbose mode, and take a screenshot when it hangs.

---

