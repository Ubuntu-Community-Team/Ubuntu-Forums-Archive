---
title: "Ubantu install hangs at configuration screen - &quot;Preparing for Installation.."
date: 2006-01-10
forum: Hardware &amp; Laptops
---

### Post by dcon on 2006-01-10
Ok..so I finally broke down and did it. Having been unable to install Ubantu on my old Sony VAIO via the CD drive, I pulled the hard drive and installed it from another machine.  I snapped it back into the VAIO and everything looks ok for a bit before it hangs.  Here's the sequence:

The Ubantu splash screen comes up and there's a flurry of activity and then it hands on the blue Ubantu configuration screen. The message states that its Installing Packages - Preparing for installation..."

Then an hour goes by and it stays at 0%...nothing doing. Any thoughts?

---

### Post by michaellars on 2006-01-16
[QUOTE=dcon]Ok..so I finally broke down and did it. Having been unable to install Ubantu on my old Sony VAIO via the CD drive, I pulled the hard drive and installed it from another machine.  I snapped it back into the VAIO and everything looks ok for a bit before it hangs.  Here's the sequence:

The Ubantu splash screen comes up and there's a flurry of activity and then it hands on the blue Ubantu configuration screen. The message states that its Installing Packages - Preparing for installation..."

Then an hour goes by and it stays at 0%...nothing doing. Any thoughts?[/QUOTE]

I am having the exact same problem on my Acer travelmate notebook.  I had it freeze at 0%, and then I restarted it and it froze at 5% with the message "preparing for installation..."  The rest of the comuter seems to function as in the cd-rom drive opens and the battery lights come on and off with connecting and disconnecting the power/battery.  The activity light does not flash at all though.  I booted the installation with "linux vga=771 noapic nolapic" also, which helped with the screen not freezing during the actual installation.   


Please help!

---

### Post by michaellars on 2006-01-16
[QUOTE=dcon]Ok..so I finally broke down and did it. Having been unable to install Ubantu on my old Sony VAIO via the CD drive, I pulled the hard drive and installed it from another machine.  I snapped it back into the VAIO and everything looks ok for a bit before it hangs.  Here's the sequence:

The Ubantu splash screen comes up and there's a flurry of activity and then it hands on the blue Ubantu configuration screen. The message states that its Installing Packages - Preparing for installation..."

Then an hour goes by and it stays at 0%...nothing doing. Any thoughts?[/QUOTE]

I am having the exact same problem on my Acer travelmate notebook.  I had it freeze at 0%, and then I restarted it and it froze at 5% with the message "preparing for installation..."  The rest of the comuter seems to function as in the cd-rom drive opens and the battery lights come on and off with connecting and disconnecting the power/battery.  The activity light does not flash at all though.  I booted the installation with "linux vga=771 noapic nolapic" also, which helped with the screen not freezing during the actual installation.   


Please help!

---

### Post by efox on 2006-01-16
i had the same problem. I loaded ubuntu no problem onto my desktop. But i bought a amd turion laptop and im having the hardest time installing..ive tried 7 times...

anyways, what i did to overcome to the hanging that you are experiencing is that i loaded it with "expert noapic nolapic"

it takes longer because almost every setting it will ask you, but if you kinda know whats going on, then you should be ok. Im a complete n00b and i got past that part. 

I did the entire installation but my problem seems to be with the display at the end..it flickers and in the end im left with a dos like screen for my login and password and such. There is no graphical interface what so ever.

---

