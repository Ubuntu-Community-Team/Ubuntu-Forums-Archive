---
title: "Tricks for bring the system temp down"
date: 2006-01-19
forum: Hardware &amp; Laptops
---

### Post by lgmdaniel on 2006-01-19
At the moment my CPU for my XP Athlon runs at about 50c with a system temp of about 31c, I've got a thermaltake cooler on the cpu and a large 120cm case fan blowing (low speed) air out. Is there anything else I could do to bring the temp down? Any little tricks? I already have round ide cables.

---

### Post by codejunkie on 2006-01-19
add a fan to the top of the case blowing upward, since hot air rises most cases have a pocket of hot air sitting at the top of the case right where the cpu's located on most motherboards adding a fan there will make a noticeable diff in tempratures. also on some cases you can add a fan to the front, have it pull cool air in and your exaust fan's blowing outward will also make a big temp drop if that's not enough you could also lap the heatsink, not recomended if you don't know what your doing because you could even raise the cpu temp or in the worse case kill your processor if you try it read up on it first. if you have money to blow there's also water cooling plus it looks good and you earn some bragging rights with your friends hope one of these helps.

---

### Post by lgmdaniel on 2006-01-19
I was thinging about a fan in the side or the top, though these will require some cutting of the case.
I've had the fan at the front but I thing with the lack of venting in the front I'm not sure it did muke, the case I have has lots of little vents along the side.

---

### Post by mcduck on 2006-01-19
For AthlonXP you can also try athcool. It's in the repositories, and works like CpuIdle and similiar programs on Windows, dropping CPU temperature when system is idle.

But try it on your own risk, It caused some system freezes for me with Hoary, altough seems to work fine with Breezy. It depends a lot on your motherboard.

```

sudo apt-get install athcool
sudo athcool on  -- to start athcool
sudo athcool off -- if you wish to stop it

```

Other than that, it's all about making the air flow in the case better. Fan on the top or behind the case is good, but you must also make sure that cool air has some way to get in to case. From the bottom of the case if possible, but bottom of the front panel is good too. And if you choose to make a hole for extra fan, you should also cut the case fan grills away, they limit air flow and cause some noise too.

By the way, 50C isn't that high for AthlonXP. It doesn't support frequency scaling or any other features that are used to keep later CPU's cool when idle. As long as it doesn't rise high above 60C under continuous 100% load you have no problem.

---

### Post by lgmdaniel on 2006-01-19
Thanks.. that should help, I'm tryin to get the temp down so that the noise level drops. Its a bit loud now that we have our son asleep across the hall, so its less about performance any more about noise polution. I did look at padding the case but I don't want to over heat the cpu. If I can get the temp down the CPU fan will quieten down to as its temp controlled. Its also all on a limited budget...;) 
I'll give a few of those things a try.

---

### Post by Azion on 2006-01-19
What thermal paste did you put on the heatsink?
Was it the one that came in the box?

---

### Post by lgmdaniel on 2006-01-19
[QUOTE=Azion]What thermal paste did you put on the heatsink?
Was it the one that came in the box?[/QUOTE]

Nope.. I went out and bought some cool master stuff...

---

### Post by Phlosten on 2006-01-28
I have had issues with my athlon XP 2000+ CPU and high temperatures. As we are in summer here we are getting 35 to 40+ degree temperatures routinely and sometimes the air con just doesnt keep up well. I have even got to the point of moving the computer office from one room to share with my daugthers room.

But today I am back into windows because the cpu is getting to 60+ degrees even tho we have air con on and 4 case fans ( 2x on front sucking air in, 2x on back sucking air out) plus cpu fan and psu fan. In windows i use a utility from MSI called cooler XP which cycles down the cpu when idle and usually drops it down to 34/35 degrees when idle.

I have been trying to find a suitable alternative in Ubuntu but wasnt aware of the athcool, which I am going to look at.

---

