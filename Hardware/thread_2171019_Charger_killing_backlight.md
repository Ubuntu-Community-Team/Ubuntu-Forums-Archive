---
title: "Charger killing backlight"
date: 2013-08-28
forum: Hardware
---

### Post by wgw on 2013-08-28
In the last week the backlight on my Thinkpad T60 has been going off for no apparent reason, usually after about 2 minutes after logging on. After a bit of experimentation, I found that it happens only when the charger is plugged in (with or without the battery). I tried another battery and another charger (all configurations) with the same behavior, so I don't think it is a battery or a charger issue: it could be software, or it could be a circuit board component that handles power switching gone bad. 

I found this remark: 

> The only think i can think of is that the backlight is turning brighter when you plug in the ACadapter, most do. And you have a problem with the inverter and the additional power draw overloads it. Go into powermanagement and set the screen to the same brighness on AC as when on battery, apply, then plug in the charger and see.

(I don't know what an inverter is! But overload I do understand.)

Three questions: 

1) how do I set the brightness so that when the charger is plugged in it remains low? 
2) Is there any way to diagnose the power changes on the board or circuit board power problems? 
3) Any tips whatsoever?!

Right now my workaround is to charge the battery, work for an hour or two, suspend, charge, then unplug charger and repeat. It does make me take a break, but not always when it is convenient....

Thanks!

---

### Post by wgw on 2013-08-28
I will post here a log of my troubleshooting, in case others are bamboozled by a backlight problem.

The answer to 1) was gconf: [http://www.ossramblings.com/set_battery_backlight_dim_amount](http://www.ossramblings.com/set_battery_backlight_dim_amount). I set battery_ac to 90. 

So far so good. 

But I really think it is a hardware issue, since I had a plug problem before this started. I may have zapped a component.

---

### Post by wgw on 2013-08-28
Nope: the adapter was plugged in and it was running fine until I touched the screen; the backlight went off. 

Must be a cracked board at the plug that is only sensitive when the adapter plug is in. So to test that, I should plug in the adaptor with no power then jiggle the plug (or screen?). If it doesn't go off, then it is a short coming from the adapter, probably at the plug :(.

---

### Post by wgw on 2013-09-11
Final solution: replace the LCD panel. (Next step: see if I can repair the old one by replacing the bulbs)

Since my symptoms were all over the map, I thought it might be something other than the bulbs. Sometimes it would go blank when I moved the panel, always going blank when I plugged in the charger, but if I lowered the brightness it would work longer. I could generally get the screen back by switching resolution (F7), but not when it was charging and at full brightness. 

This link was the most helpful: [http://www.ebay.com/gds/Diagnosing-laptop-backlight-problems-/10000000005308726/g.html](http://www.ebay.com/gds/Diagnosing-laptop-backlight-problems-/10000000005308726/g.html) 

Also, these helped as well: 

[http://forum.notebookreview.com/lenovo/466512-thinkpad-t60p-display-problems-inverter-card-backlight.html](http://forum.notebookreview.com/lenovo/466512-thinkpad-t60p-display-problems-inverter-card-backlight.html)
[http://www.insidemylaptop.com/ibm-thinkpad-screen-went-blank/](http://www.insidemylaptop.com/ibm-thinkpad-screen-went-blank/)
[http://www.laptoprepair101.com/laptop/2011/12/08/most-common-laptop-hardware-problems/](http://www.laptoprepair101.com/laptop/2011/12/08/most-common-laptop-hardware-problems/)
[http://superuser.com/questions/441503/cause-fix-of-laptop-screen-flickering-when-moving-lid](http://superuser.com/questions/441503/cause-fix-of-laptop-screen-flickering-when-moving-lid)

Solved! But after much fussing. (I hate to take my computer to the repair shop -- do I really want to put the sensitive data on my hard drive in the hands of an unknown repair person ?)

---

### Post by tgalati4 on 2013-09-11
I have a T43p with a dimming display.  These machines are workhorses, but the displays have always been a weak spot.  Either the CFL's are weak, poor quality, or just supplier variation.  Because the rest of the chassis is solid, good hinges, bezel, keyboard, they are worth repairing.  But as you will discover a pain.

At least you can get parts.  Many laptops are just throw-away.

Create a bootable linux USB key and take the hard drive out.  The tech just needs to be sure the display will light up after the repair.  Get a USB enclosure for your hard drive and make a backup to a desktop machine.

---

