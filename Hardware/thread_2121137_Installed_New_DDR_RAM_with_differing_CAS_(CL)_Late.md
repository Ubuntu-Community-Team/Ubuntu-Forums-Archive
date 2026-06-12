---
title: "Installed New DDR RAM with differing CAS (CL) Latencies and Voltages"
date: 2013-03-01
forum: Hardware
---

### Post by Mark_in_Hollywood on 2013-03-01
The info below is based on a misunderstanding. I thought the memory stick I had was 1.8 volts and the new one I bought was 1.5 volts. They were both 1.8 and all that follows is UNTRUE.

MythTV, installed about a month ago has me very flummoxed. So I bought a new 2 gig stick of ddr2 ram. I know all the stories about ram has to be from the same maker and the timings and voltages must match, etc. BUT, I found an easy solution to get two different 2gig sticks, with both different voltages (1.5 vcc and 1.8 vcc) and two differing timings (5-5-5-15 and 5-5-5-18) to work together. I did not have to change any BIOS settings.

And this is so easy to do.

1 - unplug the power cord from the computer

2 - press and hold down the on/off switch for 5 seconds (let's the capacitors in the psu drain)

3 - remove all memory sticks from their slots, put them on static proof material

4 - plug the power cord into the computer and power up the computer - hear the beeps

5 - power down the computer, remove the power cord, press and hold down the on/off switch for 5 seconds

6 - install all memory sticks

7 - plug power cord back in to the computer - power up - you should be golden, I was.

---

### Post by CharlesA on 2013-03-01
You don't even need to do that.

You could just power the machine down, unplug the PSU and pop the new memory in, then boot back up.

The BIOS should detect compatible settings for the new memory.

---

### Post by Mark_in_Hollywood on 2013-03-01
I thought it best to clear any possible memories that the BIOS would have of the current memory. Thanks.

---

### Post by CharlesA on 2013-03-01
I guess you could reset the settings to factory defaults, but completely clearing it out shouldn't be needed.

---

### Post by Yellow Pasque on 2013-03-01
I don't think you can run different sticks on different voltages, so you should beware that one of your sticks is probably now overvolted (or undervolted).

---

### Post by Mark_in_Hollywood on 2013-03-01
As my original 2gig PQI (PC 6400) runs at 1.8±.1 volts, and the added 2gig of GSkill (PC 6400) runs at 1.5±.1 volts. I'm a happy camper. But I'm going to run memtest86+ ovenight and I'll post about that here if there is a significant problem.

---

### Post by Mark_in_Hollywood on 2013-03-01
Sorry, folks, between the advertising, the manufacturers' webpages, and the info on the clamshell that the GSkill came in, I see that I have 1.8 volt ddr2, only, so my bad, no mixed voltages allowed.

---

### Post by CharlesA on 2013-03-01
Sounds about right. I think The DDR2 I was running ran at 1.8V, while the DDR3 I am running now is at 1.5V.

---

### Post by Mark_in_Hollywood on 2013-03-01
So, Mr. Odd Job, please delete this post.

---

