---
title: "Using a Wacom Bamboo Fun as a gaming device"
date: 2008-04-17
forum: Hardware &amp; Laptops
---

### Post by arelis on 2008-04-17
**I got a bit further. Check the third post in this thread**

I have gotten my Wacom Bamboo Fun (which is a USB tablet, made by Wacom) to work with Ubuntu [(using _this_ guide)](http://ubuntuforums.org/showpost.php?p=4253232&postcount=133), and i've done some gaming with it in Nexuiz (which is a First-person shooter). While not it's intended use, it's pretty fun. However, i still had to use my keyboard while gaming with it. So i came up with an idea to have one button (or more) on that tablet act as a "modifier key" that switches around all the other buttons on the tablet (there are four, minus one is three) to do something different.
The tablet looks like this:
[img]http://www.gamtronics.com/catalog/BambooFunMS_large.gif[/img]

For example, take this configuration:
< : Walk forward
FN1 : Walk backwards
> : Switch weapon
FN2: Modifier key

While pressing FN2, this becomes:
< : Strafe left
FN1: Strafe right
> : Jump
FN2 : (When modifier key is released, switch back)

How would i configure my tablet like that?

---

### Post by Distro Jockey on 2008-04-17
As I mentioned on IRC:

[http://www.nabble.com/short-howto-for-wacom-bamboo-fun-on-ubuntu-7.10-gutsy-to14142265.html](http://www.nabble.com/short-howto-for-wacom-bamboo-fun-on-ubuntu-7.10-gutsy-to14142265.html)

---

### Post by arelis on 2008-04-17
I got a bit further by examining the xsetwacom and wacomcpl tools. Seems you can bind custom keybindings to a key. So you can bind one to a modifier key (such as alt), and then have them behave differently when you hold that key. Problem is, nexuiz (and most other games) use modifier keys as normal keys, so when you, for example, want to assign that modifier key + button1  in nexuiz, it thinks you want the action to happen when you press the modifier key, but not the modifier key + button1.

So if anyone knows the name of a program that switches keys around when you press a certain key, would you please reply?

---

