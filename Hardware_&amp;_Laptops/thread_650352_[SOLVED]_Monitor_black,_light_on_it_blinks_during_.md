---
title: "[SOLVED] Monitor black, light on it blinks during startup"
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by Aerin on 2007-12-26
Hi

Since the past few days during startup, the cpu switches on, and I can hear whirring sounds, but the moniter stays black, and the light on it blinks slowly. (about 1 second off and half a second on). I can realize that its not a case of booting up but not showing on the monitor since I cannot hear the sound of ubuntu logging in, and I have automatic login set up.  I have no choice but to hard reset the computer again and again, and just randomly it works after about 30(!) or so tries.  

Once it starts up even once, then if I restart or shut down it works too - as long as there isnt much time gap. 

I tried adjusting the power cord, as well as unplugging the monitor from the cpu. When I do the latter, the screen turns dark blue, and the led stays on and stops blinking. Again when I plug it in, it turns black and the blinking resumes. 

I have nothing other than ubuntu now, so there's no grub choice either. I dont think its an OS or grub problem, but a hardware one. Also the first thing that shows up on a normal startup is the video card message. (nvidia fx5200)

Thanks for helping! :D

---

### Post by Samhain13 on 2007-12-26
I believe that a blinking light from the monitor indicates that it isn't getting a signal from the machine. Maybe it's a graphics card issue?

---

### Post by mellowd on 2007-12-26
How far does the monitor stay on? i.e. when does it switch off because you say you see something when you first switch your pc on.

btw, a cpu is just a chip in the case, not the case itself.

---

### Post by Aerin on 2007-12-26
> **mellowd said:**
> How far does the monitor stay on? i.e. when does it switch off because you say you see something when you first switch your pc on.
When I first switch it on, it stays off. The monitor starts working after a while, after repeated switching on and off :(  After it starts working and successfully boots up, it keeps on working with no problems.

---

### Post by Aerin on 2007-12-26
> **Samhain13 said:**
> I believe that a blinking light from the monitor indicates that it isn't getting a signal from the machine. Maybe it's a graphics card issue?
When I unplug the monitor from the cpu, but not the power cord, it turns blue. And the blinking stops. Then when I plug it in again, the black screen and blinking resumes, it must be getting some signal then, right?

---

### Post by mellowd on 2007-12-26
you mentioned though that you see the video card message on startup, then exactly what happens? It could just be that ubuntu is using a range out of spec for the monitor, if it works and sometimes not then you need to check that your video card is properly seated in the slot. If it is you could have a faulty monitor or cable

---

### Post by Samhain13 on 2007-12-26
Aerin: Right. And you should be getting a floating box that says "No Signal". Is it possible for you to try using another monitor just to see if that one isn't busted?

---

### Post by Keith_Beef on 2007-12-26
> **Aerin said:**
> When I unplug the monitor from the cpu, but not the power cord, it turns blue. And the blinking stops. Then when I plug it in again, the black screen and blinking resumes, it must be getting some signal then, right?

You need to look at the documentation for your monitor.

Blinking may signify that the cable is attached, rather than that there is a signal,  maybe in power-saving standby mode.

The light on my own monitor, a Viewsonic, turns blue in some states, and yellow in others, and blinks in others...

B.

---

### Post by Aerin on 2007-12-26
After a lot of searching I finally found my monitor's manual. It said that when the light blinks every 1 second, the monitor is using the power management system. I noticed that on standby mode the same blinking happens.           

I also have no UPS.

---

### Post by Aerin on 2007-12-26
@mellowd: 
I said that 'normally' I see the video card message when the monitor starts up. Now I see nothing but a black screen on starting up. I repeat switching it off and on again, and just randomly it clicks and starts working. Sorry for being unclear, english isnt my first language. 

@Samhain13: 
Nope it isn't possible for me to try another monitor. 

@everyone: 
Thanks for your help thus far. I'm confused now... does this mean that the power supply needs fixing? And why does it work sometimes and then continues to work? Also does this mean that the video card seating isnt the problem anymore?

---

### Post by mellowd on 2007-12-26
> **Aerin said:**
> @mellowd: 
I said that 'normally' I see the video card message when the monitor starts up. Now I see nothing but a black screen on starting up. I repeat switching it off and on again, and just randomly it clicks and starts working. Sorry for being unclear, english isnt my first language. 

@Samhain13: 
Nope it isn't possible for me to try another monitor. 

@everyone: 
Thanks for your help thus far. I'm confused now... does this mean that the power supply needs fixing? And why does it work sometimes and then continues to work? Also does this mean that the video card seating isnt the problem anymore?

Check to make sure the video card is correctly in, if it is there is a problem with either the monitor cable or the monitor itself

---

### Post by Aerin on 2008-01-23
Sorry for not updating. A lot of googling revealed that capacitor leakage on the motherboard has the same symptoms. However I did not notice anything. I just kept the computer running 24/7 in sleep mode when I did not need it. Occasionally I shut it down. After about two weeks the problem went away by itself... weird. Maybe it was a problem with the power supply. 

Anyway I'm fine now. :)

---

