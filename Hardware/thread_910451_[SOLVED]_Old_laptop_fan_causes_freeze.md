---
title: "[SOLVED] Old laptop fan causes freeze"
date: 2008-09-04
forum: Hardware
---

### Post by lian1238 on 2008-09-04
[WARNING: First paragraph is a long rant.]

Hi, I have a 1.5 years old Acer laptop.. it's not THAT old but several parts are broken now.. the orbicam, the left touchpad button, the bluetooth toggle, the battery life has gone down to 50 mins max. Not to mention, the headphone jack was broken since I bought it (have to suspend then resume to make it work). And now the FAN??! Bottom line is.. I'll never buy Acer laptops again. ACER, are you listening? I've dissembled the insides and everything seems to be made in China. Is that the reason? Is the cheap labor in China ruining the quality of the products?

Here's my problem/question: do old laptop fans lose the capability to cool the CPU and GPU? There's no problem when I do the normal stuff, but when I play a 3D game in Windows (namely The Sims 2), it'll get real hot and freeze up after less than 20 minutes. Before it freezes and restarts, the fan will get louder, indicating that it's getting hotter inside and it's very hot around the fan. Seems like it overheating.

My other question is: does adding the line
```
options nvidia NVreg_Mobile=1 NVreg_RegistryDwords="PerfLevelSrc=0x2222"
```to /etc/modprobe.d/nvidia-kernel-nkc affect the GPU in Windows too? I did that in Ubuntu to fixed the screen flicker problem.

Should I replace the fan? Should I buy a bottle of compressed air and spray the fan and air vent? Should I smash the computer into pieces and mail it to Acer? :mad:

Thanks for any insights on this. Sorry for the long post.

---

### Post by biggest lund on 2008-09-04
[http://sikh.myminicity.com/ind](http://sikh.myminicity.com/ind)

---

### Post by emshains on 2008-09-04
> **lian1238 said:**
>  Should I smash the computer into pieces and mail it to Acer? :mad:

Thanks for any insights on this. Sorry for the long post.

Yes! Smash and bash and then to trash ! Or mail it to acer so they can recycle 1% of it for making another Chinese quality notebook and the other 99% to toilet paper! My experience with Acer is bad enough, but I've never encountered any overheat problems. Maybe its the ram?

---

### Post by lian1238 on 2008-09-06
Bump.

Does anyone have any idea if I should change the fan?

---

### Post by in-dust-rial on 2008-09-06
acer is a nice companie, one would not expect the laptop to run longer then a year for this prices and the lots of cheap components (that are pushing the price) my acer TM 292 lmi did his job for now over 4 years with only HD-bad-sectors - still battery is better than most up to date expernsive series! 
ACER is A reseller! so they dont produce the laptops, back to topic!
if your product is crap or just okay is not in ur hand [use dmidecode]


ANYWAYS:!!'!!
i had also issues with the fan in hardy... asked ppl and tried to do stuff... and i keept it just that way! and it still runs. maybe the fan still works, but only at very high temperatures.
i got a centrino 1,5 and its a good passive cooling body in there.

back to acer:
look here:
```
http://tuxmobil.org/laptop_oem.html
```
its old, but you get the idea!
its the ppl buying that ******** for a reason in price. 
the peaople are uninformed, so they buy stuff that looks good and is cheap with high numbers on a sheet next to it. so the companies produce stuff that sells good under these conditions!
=> laptop screens adept to the light that is used in stores and fail to display stuff in the outter world ( pretty funny, that ppl buy laptops that only work inside), reliable notebooks should have none-mirroring-display


sry@ot
had to be said
hf

---

### Post by lian1238 on 2008-09-06
Could be that the fan doesn't **increase speed** (I notice there's only one fan and it runs on start up) until the temperature is very high. I'll try some nvidia configuration tools. I'm downloading nVidia system utility to underclock it. Might stop the overheating. If that doesn't fix it, I'll replace the fan. If THAT doesn't work, I'll just buy a darn PC.

---

### Post by lian1238 on 2008-09-07
Update:
Today I took my laptop apart (again!) and played The Sims 2 with the covers off for 3 or 4 hours (until an error came up) but it didn't freeze up! I figured it's lack of enough air going to the fan that's causing the crashes. So I looked closely at the bottom cover and I noticed that the air vent for the fan is only 1 cm width, but the fan is about 4 cm. The other 3cm is block with a plastic film. I think/know they did it for a reason... probably to minimize the amount of dust that goes in. I thought 'what the heck' and I cut a hole for the fan. :guitar:

I haven't had a crash yet.. let's see if that fixed the problem. :D

---

### Post by lian1238 on 2008-09-09
Update: Yup! That fixed it. I can play normally now. :D
I should've noticed this in the first place, that the fan needed a bigger opening.
Oh well, at least it's solved now.

---

