---
title: "Desktop suddently powers off. Help!"
date: 2009-06-15
forum: Hardware
---

### Post by dmears on 2009-06-15
Hi,
I built a box around the Gigabyte GA-E7AUM-DS2 motherboard. The case I used was a generic cheap Rosewill case with a 500W power supply. CPU is an Intel Core2 Duo E8200 (I think) with 4G RAM. I'm using the on board HDMI video and S/PDIF to display video on an LCD TV and pipe audio through a home theater.
 
I use a Debian amd64 kernel 2.6.11 (lenny) and the nvidia VDPAU graphics drivers.
 
What's happening is that at seemingly random times the computer will abruptly power off. There are no kernel error messages before this happens. I can turn it back on and it's another turn at the slots seeing how long it will stay up. Sometimes for a few days, other times for a few minutes.
 
I boot off of an external USB drive and I use external USB drives for storage. sensors show the CPU cores running fairly cool around 38 deg. C, though I have no way to tell if that's accurate. The air coming out of the box is not particularly warm. I periodically monitor CPU temps when watching video, but I've never seen them go over 40 degrees.
 
My suspicion is that the power supply although new (approx 3 months) is having problems OR my GPU (integrated GeForce 9400 on the mother board) is heating up and triggering a shutdown. 
 
Do motherboards have temperature based triggers on the GPU? Any way I can run a stress test to see what specifically causes this? 
 
I'm trying to avoid swapping components in and out without a good idea of what's going on. Has anyone seen anything similar? 
 
Thanks!

---

### Post by Sin@Sin-Sacrifice on 2009-06-15
So the pc just shuts down or cuts power entirely? If the latter you might want to get the power supply checked/replaced. If the former then theres some kind of conflict and that´s beyond me. You might want to check to see that nothing is touching inside the box... I had that problem with the box I&#7743; on now. I took out a screw holding the MB and that solved the problem. I figured it out by pushing the ram back in after checking it and when I put pressure on the board it started to boot and shut back down after releasing. I did that 2 more times and then took out the center screw and the problem went away. Must have been shorting somewhere. It really sounds like a hardware issue without kernel errors. If it´s actually shutting down... hehe good luck finding a solution without a reinstall. Wish I could be of more help.

---

### Post by dmears on 2009-06-15
Thanks - the box doesn't go through an orderly shutdown. Just a sudden loss of power. I'll take both your suggestions - tighten everything down and see if that helps. What's odd is that I can reboot after a reset, and the box works perfectly well otherwise.

---

### Post by Sin@Sin-Sacrifice on 2009-06-15
Ooh... yeah. Check the connections from the power supply too. Might be something not touching enough in that case.

---

### Post by IcarusR on 2009-06-16
Try removing everything (including cables) except the mobo. 
Use an air duster aerosol (available from Maplin) to blow out all the ram slots & other connections. 
Blow out the CPU fan & heat sink. Do not let the air 'spin' the fan, put something in between the blades then blow out. 
Blow out the PSU fan & case. Then rebuild it making sure everything is seated correctly & positively. 
Then try it. 

Don't forget to use electrostatic protection. This can zap components without you knowing, causing them to fail at any time.
Google for more info.

I have had components 'creep' in use causing similar problems. Took ages to pin down.

Good luck

---

### Post by dmears on 2009-06-17
Thanks - it's been up for almost two days now, in which time I've watched a fair amount of video using the VDPAU drivers. Temps have remained well below trigger levels. If I see more crashes I'll take the system apart and try to figure out one part at a time.
It's a fairly new system so I don't think dust is a problem yet, but it might be a component in the PSU that's creeping to failure.

---

