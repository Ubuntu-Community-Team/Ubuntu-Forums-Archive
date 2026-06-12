---
title: "dell xps m1730"
date: 2014-04-19
forum: Hardware
---

### Post by TheTinyt1 on 2014-04-19
I have a Dell XPS M1730 duel core lap top and I have tried to run Ubuntu, Lubuntu, xubuntu, edubuntu on it and they all give me to same problem. I have not monitor on the lap top. I have to hook up a external flat screen to see anything. 
I have run these from live DVD's and a live Flash drive with the same results. my lap top screen is all white and you can see nothing.

What could be the problem?

---

### Post by mörgæs on 2014-04-20
Did you try boot options like **nomodeset**?

---

### Post by TheTinyt1 on 2014-04-20
I have no idea what a nomodeset is? Will try it if you can give me an idea where it is or how to do it.

---

### Post by Doug S on 2014-04-21
I have a Dell XPS M1730 also. For some test, I ran a desktop ubuntu 14.04 daily ISO a month or two ago on it just fine. The video display was O.K.
I could try again with the final ISO, perhaps tomorrow (it is late now in my time zone).

Edit: I tried the final 64 bit Ubuntu desktop 14.04 ISO, in "test drive" mode. The Dell XPS M1730 LapTop display worked fine. It takes awhile for the system to fully start up after clicking the "try Ubuntu" button, and for a time my screen was sort of white.

---

### Post by mörgæs on 2014-04-21
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by TheTinyt1 on 2014-04-30
I did as you suggested and it worked. I used to see this screen on other versions but it is great to know how to get to it when needed.

Thanks for the help...

---

### Post by SirWeazel on 2014-11-01
UPDATE: I found out my issue, the heatsink/thermal compound was junk and CPU constantly was throttling down do to thermal protection. I still have some testing, but performance is now where i expected it to be. Still curious, how other XPS M1730 laptops are doing? If need be i'll start new thread.

I'm curious how everything turned out for you. I have this same laptop. I had to boot with nomodeset for the laptop display to work properly. I also had to boot with [FONT=Monaco]processor.ignore_ppc=1 to prevent it from running at 800MHz constantly slowing it down. I don't know why this is, since the power adapter appears to be recognized correctly within the bios.[/FONT]

[FONT=Monaco]How has your performance been? Does it run as fast as you expected? [/FONT]
[FONT=Monaco]I ran "system profile and benchmark" hardinfo for some simple [/FONT][FONT=Monaco]bench-marking[/FONT][FONT=Monaco], and it as not been impressive. I not sure where my bottle neck is. I thought it might be my processor, but according to sensors the temp is where it should be.

So basically i'm just curious how other's performance has been with this laptop, and based on the results will influence me how much time to spend finding my issue. What specs/desktop enviroment/special setup?[/FONT]

---

