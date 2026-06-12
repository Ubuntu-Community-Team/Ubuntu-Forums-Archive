---
title: "laptop heating up pretty bad and fans not kicking in."
date: 2006-08-21
forum: Hardware &amp; Laptops
---

### Post by 0okami on 2006-08-21
ok im worried... i have a 4150 inspiron and im assuming the fans should kick on after the temps reach a certain level. im hitting temps as high as 71c / 159f. I ended up cutting epsxe off in fear of frying the cpu/board. 

Im under the impression the system has two fans but i only hear one, and its always operating low. See attached screenshot please with my conky config showing details. 

Any advice is welcome.

(epsxe running. Game is tales of destiny.  CPU is maxing at 100%. This cuases the system to heat up and fast. Any other time it runs about 2-3% idle 46c / 114 f. )

---

### Post by em3raldxiii on 2006-08-21
Coupla questions:
 
How long has this problem been occurring?  Have you always run Ubuntu, and if not did the probem occur under previous conditions?  Does your computer have the battery that Dell is recalling because computers have been bursting into flames?  Have you entered your BIOS to verify the temperature information in case conky is lying to you?  Does your computer run at 100% CPU activity for extended periods of time, or is it just peaking during game transitions or other processor-heavy activities?  If you *know* that this is hardware related, do you still have a warranty on your computer?
 
Otherwise, I'd say you **might** have a fan failure.  It's not so grevious if that's the case - it could be changed out fairly easily.

---

### Post by 0okami on 2006-08-21
> **em3raldxiii said:**
> Coupla questions:

How long has this problem been occurring?  Have you always run Ubuntu, and if not did the probem occur under previous conditions?  

I bought my notebook at a yard sale 2 weeks ago $115.00 (sweet deal i think) 

WinXP was hosed and it just needed an os install. As far as i remember, i recall hearing the fans speed up, however, im not certain for 100% sure. I will throw xp on another laptop hard drive and see what happens. But first i have to figure out how to do a network install of xp... the cd drive was not part of the deal (didnt have it - only floppy.). 

> **em3raldxiii said:**
> Coupla questions:
Does your computer have the battery that Dell is recalling because computers have been bursting into flames?  


ZoMG! I was not aware of that! I will have to research that once i get home. 

> **em3raldxiii said:**
> Coupla questions:
Have you entered your BIOS to verify the temperature information in case conky is lying to you?  


I looked around the A06 bios, but i did not see any info related to fans or temps. Only battery. 

> **em3raldxiii said:**
> Coupla questions:
Does your computer run at 100% CPU activity for extended periods of time, or is it just peaking during game transitions or other processor-heavy activities?  


Only when running epsxe it will max out like that. 

> **em3raldxiii said:**
> Coupla questions:
If you *know* that this is hardware related, do you still have a warranty on your computer?


Being bought at a yard sale, im sure warranty is probably gone. it's an old inspiron 4150 notebook. 

> **em3raldxiii said:**
> Coupla questions:
Otherwise, I'd say you **might** have a fan failure.  It's not so grevious if that's the case - it could be changed out fairly easily.
 

Thanks! this will help me trouble shoot a bit further. I will post back with updates results.

---

### Post by David Corrales on 2006-08-22
Try installing the package **i8kutils**. It's designed especially to manage fans and temperatures in Dell laptops :)

---

### Post by em3raldxiii on 2006-08-22
Hehe, great deal, 115 bucks eh?  As long as it works ;)

I admit I didn't look up your model number ... my bad :oops:.  But you appear to be safe from the spontaneous combustion problem.

It's not uncommon for a computer to go from moderately cool to very hot in a relatively short period of time - it's not like a stove heating element that takes a little time ... it's more like a lightbulb that instantly gets hot when the load goes from near 0 to full capacity.  And getting some processors up over 70C isn't terribly unusual.  In fact, my Athlon Thoroughbred 1.33 GHz processor on my old computer runs at 50+ idle and over 70 at full load.  Yes, this is oddly hot, and yes, it means the processor will likely burn out.  But I have put so much extra cooling in the case that it sounds like a hoover.  It's old though ... and it's lasted me this long ... it doesn't owe me anything.  Now, if this is a Pentium Celeron based on the PII chip, those temps would REALLY worry me!

So follow David's advice.  I have never used that utility, but you should be able to sudo apt-get install it.

Keep us posted!

---

### Post by 0okami on 2006-08-24
ok, im back. I loaded windows and I activated a program called: 
"I8kfanGUI" Dell Inspiron/Latitude/Precision fan control utility
[http://www.diefer.de/i8kfan/index.html](http://www.diefer.de/i8kfan/index.html)

I set the manual fan control and put the fan on high, fan spins way up. So the fan is ok.  I dont have a dead fan ^_^ but now i have to find out why is dapper or my notebook it self is not activating that fan to high spin. is there a place to change temperature sensitivity in linux to make the fans kick on at say 60c?  

I need to find out what is the max temp the cpu can handle before the fan should go into high spin mode. 
------- edit ---
Ok, I found out the'kick in' temperature is quite high with current BIOS revisions (usually at 75°C-85°C). ZOMG! 
---- end edit --- 

Also does anyone know for sure if the inspiron 4150 has 2 fans? or just one? 


Im going to put the machine under load in windows to see if it auto kicks on to high... bbl.

---

### Post by 0okami on 2006-08-24
problem solved. In the end it was just my paranoia getting the best of me. The CPU fan kicked into high at 75c in both dapper linux and windows XP. 

So, nothing to worry about here. ^_^

---

### Post by em3raldxiii on 2006-08-24
Well, it shows you are concerned about your hardware, which is more than I can say about most computer users.  :D  Kudos to you for being diligent :D

---

