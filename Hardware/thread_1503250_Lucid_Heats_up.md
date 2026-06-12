---
title: "Lucid Heats up"
date: 2010-06-06
forum: Hardware
---

### Post by 1Michael1 on 2010-06-06
Hi, so I upgraded my laptop (HP ProBook 4510s) to Lucid Lynx a couple of weeks ago and I've noticed that it overheats (Shuts off) very frequently. Just by browsing the web with google chrome and chatting some with Pidgin causes a shut down. 

The main reason why I changed from Windows to Ubuntu on my laptop half year ago was due to the blue screens of death I gotten all of the time because of the overheating. And then it went a lot better when I made the swap to Karmic Koala and the laptop was running a lot more smoothly.

So yeah, I've tried a lot of different things like; I ain't using the power cable when the battery is already full. I'm having the laptop on a pile of coins so the laptop is about 1-2 cm above the table so it wouldn't get too hot under the laptop. 

The only thing that has changed (Which I'm aware of) is that the drivers for my videocard has start working on 10.04. (It wasn't compatible with Karmic Kaola).

I ain't running anything unecessary apps such as Compiz etc. 

So anyone got some ideas what I should do?
Should I downgrade the laptop to 9.10 again?
This is quite a big deal for me since whenever I've been using CodeBlocks for 10 minutes of uptime the laptop just shuts down. Though I can browse the webs for an hour or two until it shuts off.

Thanks a lot for your interest,
Micheal.

---

### Post by Rolo linux on 2010-06-06
Hi 1Michael1:

I think what  you have is a hardware problem. Malfunctioning  fans, dust in the vents ...
Have you  checked that the laptop fan is running?
[IMG]http://www.google.com/images/cleardot.gif[/IMG]

---

### Post by 1Michael1 on 2010-06-06
Yeah the fans are running, I opened the laptop up and surprisingly I didn't find too much dust there. Tho the dust I found did I blow off. The Windows has gone better after so but Lucid Lynx is still the same. Getting warm incredible fast.

---

### Post by kabloink on 2010-06-06
It's possible the cpu scaling is not working correctly. There have been other posts mentioning that the scaling was stuck on performance on their laptops and they had to manually choose ondemand after each boot.

If you haven't already, add the cpu frequency scaling applet to gnome and check to see what the scaling is set at. It it's on performance, set it to ondemand and see if that helps with the overheating.

---

