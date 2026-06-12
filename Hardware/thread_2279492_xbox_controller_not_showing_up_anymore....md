---
title: "xbox controller not showing up anymore..."
date: 2015-05-23
forum: Hardware
---

### Post by john397 on 2015-05-23
Currently running latest version of ubuntu. I had my xbox controller working great with Dolphin emulator. Then I installed mupen64 and had some problems getting the Z button to map with RB. The controller would just vibrate when I pressed the Z button in game. So I was messing around in the terminal and tried following some tutorial on mapping the joystick via xboxdrv. I had no success trying to achieve that and I followed the tutorial commands that led me to "blacklist" and "lock" the controller. Now the xbox controller doesn't show up anymore or work for either emulators or games. I entered the following command:

[PHP]sudo apt-add-repository ppa:rael-gc/ubuntu-xboxdrv [/PHP]

[PHP]sudo apt-get update && sudo apt-get install ubuntu-xboxdrv[/PHP]

Then I restarted my computer. Still no luck. 
When I run  [PHP]sudo xboxdrv[/PHP]

I get

> -- [ ERROR ] ------------------------------------------------------
No Xbox or Xbox360 controller found
john@john-desktop:~$

How do I get my xbox 360 controller showing up  in ubuntu and working with my games/emulators again? I dont want to mess with the terminal again because I messed everything up apparently.

---

### Post by john397 on 2015-05-24
bump

---

