---
title: "[SOLVED] hardware issue"
date: 2008-08-22
forum: Hardware
---

### Post by nick2535 on 2008-08-22
i am having some problems with kubuntu being able to use my wireless keyboard / mouse combo and my wireless card i am not shure what it is because they worked perfectly on a diffreent motherboard in the same version of kubuntu 8.04 they also work perfectly on the same motherboard when i boot windows the two are probrably connected because every now and then they will work perfectly and when one is not working well the other is not.
the wireless card can not find the network when it is not working (and the network is present) and the mouse& keyboard just wont work for a few seconds and then it will work when the wireless card finds the network the mouse and keyboard have no trouble working. and the keyboard & mouse didnt act up untill i installed the drivers for the wireless card

---

### Post by cooke77 on 2008-08-22
When you installed the Network card, doing so changed the IRQ 'settings'...for your USB keyboard/mouse.
It (Network card) needs a IRQ setting of it's own.
Installing the Wireless drivers did not help, any.
And, there's a very good bet.....that you set your Wireless up as 'USB', too.
Wrong move.
Try setting it up....via your LAN. 
(That should give your Wireless Network it's own IRQ setting/Gateway, which it DOES require to work....and, give you back the use of your USB keyboard/mouse, at the same time.)

---

### Post by nick2535 on 2008-08-23
sorry i should have mentioned that the wireless card is pci i am a linux newbie and am trying to remember that i need to be more exact i am going to look in the bios and look at the IRQ settings and see if it still could be interfeering in that way

---

### Post by libra1780 on 2008-08-23
just a question..
got a wireless adapter as well (now using Pl), and i as far as i remember, my one found the network, but didn't connect until i downloaded the firmware.. maybe you forgot that..

look at your dmesg as well, or post it..

edit: oh, i forgot... my wireless keyboard hung while the driver tried to load the firmware.. :)

---

### Post by nick2535 on 2008-09-02
i have upgraded from kde3 to kde 4 and have not had problems scince

---

