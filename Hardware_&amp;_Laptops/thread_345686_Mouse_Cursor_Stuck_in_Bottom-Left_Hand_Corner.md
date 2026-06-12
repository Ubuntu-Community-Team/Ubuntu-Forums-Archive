---
title: "Mouse Cursor Stuck in Bottom-Left Hand Corner"
date: 2007-01-24
forum: Hardware &amp; Laptops
---

### Post by WedgeHG on 2007-01-24
Upon startup the mouse cursor darts to the lower left of the screen. If I use the touchpad to try to move it away from the corner it will move but darts right back as if I was moving it down and left quickly. Reminds me of a joystick that isn't calibrated correctly.

Here's the weird part: if I plug in an external ps2 mouse then it begins to function properly. Both the mouse and the touchpad work just fine. Even after the mouse is removed, the touchpad continues to work.

This problem isn't unique to Ubuntu. It has happened with every linux distro that I have tried.

This isn't a major problem since I can work around it easily enough but it is annoying to have to plug in a mouse every time I start the thing up. Any help you could provide would be greatly appreciated.


The laptop is a Dell Latitude C640. Please let me know what (if any) additional information you need. Thanks in advance.

---

### Post by scrooge_74 on 2007-01-24
I have been having a very similar situation with no luck here at the forum.  I f i find an answer  i will let you know

---

### Post by adampyre on 2007-05-15
BUMP

I've been looking for a precise fix for this myself. I have come across many xorg configs that will "shotgun fix" it, but it doesn't give me all of my touchpad features, like page scrolling. I have a Dell C610 myself, not the 640. I bet all DellCXX have this?

Who is a Ubuntu/peripheral guru?

Thank.

---

### Post by WedgeHG on 2007-06-05
Could you post a link to one of those "shotgun" fixes please?  Even that would be a huge improvement for me since my page scrolling doesn't work anyways :p 

Thanks.

---

### Post by Michl on 2007-08-14
Same problem here with a C610.  It is not constant though.  It does it for a
while and then gets back to norml.

---

### Post by llangwm on 2007-11-11
I also get this problem with a C610 ... other people have said that this is a problem with the hardware NOT the OS. Evidently it is something to do with the keyboard mouse.
Have looked about and seen this ([http://www.laptopsunlimited.com/dellmouse/dellmouse.htm](http://www.laptopsunlimited.com/dellmouse/dellmouse.htm)) site ... but I haven't tried it yet myself.  So I don't know if it works!

---

### Post by boomzilla on 2007-12-12
I had a similar problem on a Dell C610 I recently purchased. In windows the trackpad would work fine, but as soon as i installed 7.10 the mouse would wander rather quickly to the bottom left of the screen. I found some similar complaints online and more than a few how-to's. There are two things that could be wrong:

1) The nipple in the middle of the keyboard has degraded and is sending bad signals.
2) The trackpad circuitry is being shorted out by a metal support


If the wandering only happens when you have the laptop on a non-level surface and returns  to normal when it's on a flat surface, odds are #2 is the problem. If it's happening all the time, it's probably #1.

To fix #1:
Find the service manual online and follow the instructions to get your keyboard loose. Once you remove the screws on the bottom of the laptop it will be held on by the data cable for the keyboard and nipple. Pull the data cable off and inspect it. You should see a large ribbon and a small ribbon feeding into a plastic connector. The connector can be pried apart by the ends with a small flathead screwdriver. Once apart, pull the smaller ribbon out of the connector, then reassemble it. Plug the connector back into the motherboard, leaving the little ribbon free. Reattach the keyboard and boot up. The wandering mouse should be gone!

To fix #2:
Find the service manual online and follow the instructions to get the palm rest loose. You will have to remove the keyboard and screen before the palm rest can come loose. On the bottom of the (very flimsy!) palm rest you'll see a metal support that lays over the back of the trackpad. Remove the screws that hold this on and get it out of the way. Put some sort of non conductive material over the back of the trackpad. **do not use an anti-static bag as they are designed to conduct static along the outside of the bag!** Once that is done, reattach the metal support and reassemble the laptop. This should alleviate any trackpad movement due to short circuits.


Hope this helps!!

Also, when dissassembling, take your time and make sure you're removing the right parts! It's also good to put the screws in separate piles with notes to remind you which component they secure, etc.

---

### Post by bluedragon436 on 2007-12-22
> **llangwm said:**
> I also get this problem with a C610 ... other people have said that this is a problem with the hardware NOT the OS. Evidently it is something to do with the keyboard mouse.
Have looked about and seen this ([http://www.laptopsunlimited.com/dellmouse/dellmouse.htm](http://www.laptopsunlimited.com/dellmouse/dellmouse.htm)) site ... but I haven't tried it yet myself.  So I don't know if it works!

This is what I did and it fixed the issue I was having with my cursor acting up on my laptop...not too hard either..and while I had it all apart, I removed the stupid little screen material under the cooling fan, and now all of my internal temps are way cooler than they were...every little bit helps on the temperature...

---

### Post by fhlh on 2007-12-24
If you go to Dell and get the updated driver you can disable the "eraserhead". This will stop the random movement.... no need to hack the keyboard...
opps, that's a windows driver....
can some linux driver guru add this disable feature to the driver??

:guitar:

---

