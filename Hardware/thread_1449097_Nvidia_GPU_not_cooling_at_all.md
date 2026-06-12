---
title: "Nvidia GPU not cooling at all?"
date: 2010-04-07
forum: Hardware
---

### Post by Airris on 2010-04-07
I've put linux onto a few computers now in the course of things, but it's all been desktops until I could clear enough space on my laptop for a WUBI install. And the install went great... until I realized how hot it was getting.

Some poking and installation of lmsensors later, I confirmed : the GPU starts out at 52 C (the same temperature it idles at when I'm booted in Windows), and steadily increases without apparent end. Fan noises are not apparent, and the fan for that graphics card is LOUD, I can tell when it's running. Additionally : this is during very low intensity activity : having a terminal open and midori open for internet.  

When it got up to 70 C I decided it was time to shut off and end the experiment.  On Windows, the hottest this card will get is around 62, and usually once the fan kicks in, it'll stay at 52-54 C even under high activity (rendering high polygon count 3D scenes in openGL).   I've asked a bit about this in chat and read up on similar situations, i think my case is a little different since it looks like the thing isn't just running hotter, it's not trying to cool itself... which poses a large obstacle with trying to use ubuntu on this computer. 

A few extra notes : 
1) I tried to remove the nvidia drivers to see if the defaults would handle it properly, but I apparently botched that and X won't come up unless I run in low graphics mode, but all the nvidia stuff is removed and the problem still persists, indicating maybe this happens with the default drivers too? (The problem existed before I broke X, so I'm not worrying about that currently, since if I can't fix this I can't have linux on this laptop, so I'm not going to bother trying to fix any other problems besides the main one).  <br />

2) Compiz may be helping the thing heat up faster, but unless there's a bug in Compiz that disables fans, I don't think it's the problem (also, stuff is still happening in low graphics mode)

3) Someone posted that temperature sensors report differently in Windows/Linux, which i originally thought might be the problem, but since I got lmsensors sayings starts off at the same temperature as Windows during boot, I think the two operating systems are in agreement about the temperature, it's just running a lot hotter on Ubuntu for some reason.

4) Some software packages have been installed but the only hardware extra installed was the closed source graphics drivers. 

5) Any suggestions/experiments to help diagnose this will have to be things I can try in less than 10 minutes time. Since I don't want to turn my graphics card into a brick, I can't have Ubuntu running very long. (I didn't time how long it gets to 70 C, but it's probably in the 10-20 minute range).

 6) It's quite possible this particular card isn't well supported, the 2500M is a lot less common then the other cards in the Quadro line, most people that bought this laptop from Dell have 1500's.  

Details/Specs: 
-Dell Precision M90 Laptop 
-Ubuntu 9.10 -Graphics card : Nvidia Quadro FX 2500M  
-Problem exists with Nvidia closed source binary version 185, possibly also with default drivers (see above)

---

### Post by realzippy on 2010-04-07
70 C  is not much for a gpu....

---

### Post by doas777 on 2010-04-07
In my experience, most vid cards spend a lot of time over 60c under moderate operation. I had one that sat at 86C all the time, until I replaced the cooler. 
most of these GPUs are rated for safe operating temperatures in excess of 90c so 70 is probably not a problem.

GPUs are always very slow to cool back down. CPUs just up and down all the time but gpus are less volatile.

my nvidia cards do cool themselves as needed (at least those with fans) under ubuntu, but I'm not sure if the code to do it is in the driver or the APCI. if it is APCI then there is probably little to do, and if it is the driver, it may not be quite compatible. I've had a few cards that were almost completely compatible, except for the one feature I needed....
what model of card is it?

[http://www.nvnews.net/vbulletin/showthread.php?t=47962](http://www.nvnews.net/vbulletin/showthread.php?t=47962)

---

### Post by yacine911 on 2010-04-07
> **realzippy said:**
> 70 C  is not much for a gpu....
that true 70 c is not too much for a gpu but it can frieze your motherboard

---

### Post by doas777 on 2010-04-07
> **yacine911 said:**
> that true 70 c is not too much for a gpu but it can frieze your motherboard
hmmmm? do you mean that that temperature would not be safe for a CPU? for older CPUs 70 was my limit, but with the core2's/naehalems/athalon2's etc the safe core temp is in excess of 100. the temp you need to watch out for in those cases is the northbridge/apic.

---

### Post by Airris on 2010-04-07
Nvidia Quadro FX 2500M.

70 C might not be outrageously high, but I don't know if it would have just kept going up after that. I think the heat limit on this card is also lower than usual, the first one died on me and had to be replaced, and the tech replacing it mentioned offhand that they get a ton of reports about this particular model cooking itself, something about it being a poor choice for mounting in a laptop.

And either way, the exact same hardware is behaving significantly differently under two operating systems, something isn't right here.

Windows side : I did another test to confirm things, actively telling it to redraw the same 3D scene over and over again for 15 minutes which kept the GPU at full usage. It peaked at 64, then the fan sped up and it was back down to 57 within 2-3 minutes.

So here you have it, working properly : this card should get around that high during intense activity, then level out to 57. I don't think it's over-worrying when on linux it starts out at the same temperature, then climbs to 70+ from light activity.

:::

The only other thing I can think of is perhaps the linux drivers have different temperature thresholds, is there a way I could play with the settings to make it match the fan behavior for windows? This laptop's not fresh out of the box anymore, I like being cautious about temperature.

---

### Post by yacine911 on 2010-04-07
> **doas777 said:**
> hmmmm? do you mean that that temperature would not be safe for a CPU? for older CPUs 70 was my limit, but with the core2's/naehalems/athalon2's etc the safe core temp is in excess of 100. the temp you need to watch out for in those cases is the northbridge/apic.
ok to be clear i thing 70 it's ok for gpu cuz nvidia says that gpu can Handel heat up to 115C till your computer shut down but i don't trust nvidia ''i had a very bad experiance with my geforce 8400 gs""

---

### Post by doas777 on 2010-04-07
> **yacine911 said:**
> ok to be clear i thing 70 it's ok for gpu cuz nvidia says that gpu can Handel heat up to 115C till your computer shut down but i don't trust nvidia ''i had a very bad experiance with my geforce 8400 gs""
I also had trouble with an 8400 (and 8200, 8300, 8500). last time I checked those were all on the ubuntu incompatible hardware list:
[http://ubuntuforums.org/showthread.php?t=361237&highlight=8400](http://ubuntuforums.org/showthread.php?t=361237&highlight=8400)

one good place to check before buying is:
[http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

you'll see my review of my 8400 here:
[http://www.ubuntuhcl.org/browse/product+asus--en8400gs-silent?id=6874](http://www.ubuntuhcl.org/browse/product+asus--en8400gs-silent?id=6874)

---

### Post by yacine911 on 2010-04-07
> **doas777 said:**
> I also had trouble with an 8400 (and 8200, 8300, 8500). last time I checked those were all on the ubuntu incompatible hardware list:
[http://ubuntuforums.org/showthread.php?t=361237&highlight=8400](http://ubuntuforums.org/showthread.php?t=361237&highlight=8400)

one good place to check before buying is:
[http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

you'll see my review of my 8400 here:
[http://www.ubuntuhcl.org/browse/product+asus--en8400gs-silent?id=6874](http://www.ubuntuhcl.org/browse/product+asus--en8400gs-silent?id=6874)
for me i know one thing i will never buy a nividia or HP product that for sure

---

### Post by doas777 on 2010-04-07
> **yacine911 said:**
> for me i know one thing i will never buy a nividia or HP product that for sure
yeah, I understand why you feel that way. i've had way worse problems with ATI cards though, so I'll stick with nvidia for now.

---

### Post by Airris on 2010-04-07
There's no reviews for the card I'm using there though. So I'm still in the dark here. 

Poking around I also noted the -nv driver 9.10 is packaged with says it can handle this card -_-

So, my question from before, is there something i can use to play with the fan settings? I can have it turn on according to my liking in that case.

---

### Post by mrbeasley on 2011-02-14
> **Airris said:**
> There's no reviews for the card I'm using there though. So I'm still in the dark here. 
 
Poking around I also noted the -nv driver 9.10 is packaged with says it can handle this card -_-
 
So, my question from before, is there something i can use to play with the fan settings? I can have it turn on according to my liking in that case.
 
Hi.I was wondering if you resolved this problem.I just recently purchased a used Dell Precision M90 with the Nvidia fx card 2500m stock installed and am having simular problems.I did try this
[http://linux.aldeby.org/nvidia-powermizer-powersaving.html](http://linux.aldeby.org/nvidia-powermizer-powersaving.html) but even with the coolbits mod the temp still ran in the mid 60's even with my three fan Cooler Master underneath.You will notice that the Nvidia sub setting video windows lists the gpu set to "maximum performance"..always.After trying unsuccesfully to lower gpu temp with coolbits I reset the cfg back and reinstalled the driver.The gpu sits around 53 and gets into the 60's with the one game I have installed.Quakewars.The game loads but the mouse doesn't funtion.
 
The sound on this M90 is always turned off because of fear of blowing the speakers.The driver is not coded properly.I'm not complaining as I have no coding ability..just making an observation.BTW,when I purchase this lap it came with Windows 7 Ultimate and had no sound issues and the gpu sat in a comfort zone most of the time.I removed Windows because it was an illegal copy.Just for the record even with all these lil problems I love Ubuntu and thanks to all working on this OS.
 
Regards, peter

---

### Post by Airris on 2011-02-14
Installing 10.04 instead of the 9.x versions resolved the issue for me. Make sure you put on the nvidia drivers and you should be fine... 

Btw, don't take me as an authority on this. But from my experience. 53-64,65,66 is the range your 2500M should be at. If the fan doesn't kick in past that range, you have a problem. It might still be safe past that. But 65,66 is where windows drivers will always start to kick the fans to higher gear (if they haven't already).

And you want to keep it cool. That graphics card doesn't handle heat well, I've had it replaced several times. Good luck!

---

