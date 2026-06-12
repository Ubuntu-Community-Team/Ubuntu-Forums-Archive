---
title: "Enable VGA after boot with intel driver"
date: 2008-12-18
forum: Hardware
---

### Post by slonbg on 2008-12-18
Hi,
I have a fresh new installation of ubuntu 8.10 on a toshiba laptop. The machine has a vga out, which I connect to my tv. The video card is intel i855, and ubuntu uses the intel driver.

If I boot the machine with the VGA cable plugged in, it displays everything in a clone mode both on the laptop's LCD and on the TV, exactly as expected.

But if I boot it without the VGA cable plugged in, and latter plug the cable, I could not find a way to enable the TV, even if xrandr shows that it detects the VGA output as connected.

I have searched the forums, and googled a lot, and have found the following solutions, but neither one works for me:

1. some guys were saying that just restarting X should solve the problem, but not for me - the tv screen is still blank

in order to not restart X, as suggested in other posts, I tried:

2. xrander --output VGA --auto --same-as LVDS - this runs without any errors, but no output

3. some guy have reported that he was able to start it by restarting the acpid service - this did not work.

So, any other ideas how I can approach this problem, so I do not have to reboot the machine in order to watch a movie? It's linux after all, one does not need to reboot all the time :)

---

### Post by albandy on 2008-12-18
Did you try using the fn key and the screen symbol in your keyboard? It works for me.

---

### Post by slonbg on 2008-12-18
albandy, I tried. Fn-F5 works to toggle between LCD/VGA/Both only during the grub menu. I.e. I boot the machine w/o vga cable, and stop on the boot menu. Then plug the cable, and with Fn-F5 I can change the displays.

But this does not work once the X is started. If I plug the VGA cable after the login screen is displayed, or after login, it does not work any more. Even if I change to a text console with Alt-F1, it does not show it any more on the VGA display, actually Fn-F5 does not work any more.

While in a normal login, if I hit Fn-F5, if flashes the LCD screen, but nothing else changes.

---

