---
title: "I installed a new CPU + fan and now my computer crashes randomly"
date: 2011-08-13
forum: Hardware
---

### Post by RockPaperSissors on 2011-08-13
3 months ago I turned my computer into a **Ubuntu 11.04/windows vista** dual boot system, Linux has a learning curve but it was well worth learning. Up until now, I have been learning how to use Ubuntu by trial and error and when I couldn't solve a problem I found solutions to it on Google or these forums, but now I have run into a problem I cannot find the solution on my own and I need the community's help. 

1 month ago I installed a new CPU chip and fan on my computer hoping it would boost the performance of my computer, but ever since I installed it my computer shuts off without warning seconds after starting it up. After I restart the computer, it makes it past the GRUB I have been using to dual boot the system and past the log in screen then shuts down after starting up a program, the problem becomes worse with each passing day as the shut downs become more and more frequent. lately, I have noticed that drivers are malfunctioning, it is beeping which I believe to be a sign that it is overheating, and earlier today it failed to start up at all, I find this problem strange because my windows side of the dual boot starts up with little to no problems, although it is significantly slower than normal.

the specs of my computer are as follows (the Ram has been upgraded beyond what the following says, but I'm not sure by how much)

[LIST]
[*] **CPU: **AMD Sempron 3200+ 1.8Ghz, 128KB Cache *_**(Old CPU)**_*
[*]_**CPU**_*_**:**_* AMD Athlon 64 X2 6000+ Windsor 3.0GHz 2 x 1MB L2 Cashe Socket AM2 125W Dual-Core Processor ADX6000CZBOX *_**(New CPU)**_*
[*] **Motherboard: **[ECS GeForce 6100SM-M ]("http://www.ecs.com.tw/ECSWebSite/Products/ProductsDetail.aspx?detailid=685&DetailName=Specification&MenuID=7&LanID=9")
[*] **Chipset: **NVIDIA GEFORCE 6100/NFORCE 405
[*] **Devices**
[LIST]
[*] 80 GB SATA, 7200rpm, 8 MB cache
[*]52X/32X/16X DVD/CD-RW Combo
[*]Memory Card Drive
[/LIST]
 
[*] **Memory:** 512MB SDRAM, DDR2-533MHz
[*] **Operation System:** Windows Vista Basic with DVD Playback
[*] **Accessories Box **
[LIST]
[*]PS2 optical mouse w/ scroll wheel
[*]PS2 Multimedia Keyboard w/ 6 hot keys
[*]2 Stereo Speakers
[*]User Manual
[*]Quick Setup Sheet
[*]Full OS Restore DVD
[/LIST]
 
[*] **Port Connectors **
[LIST]
[*]2x PS/2 Ports
[*]1x VGA Port
[*]6 x USB ports (2 front, 4 back)
[*]2 Set Audio Port (front and back)
[*]1x Serial Port
[*]1x Parallel Port
[/LIST]
 
I thought there might be a problem with the BIOS so i looked that up too I am not sure that it has been updated for a while, I looked for an update online but the places I saw looked a little shady so i held off on trusting them.
[/LIST]
**BIOS**

[LIST]
[*]Phoenix Award WorkstationBIOS v6.00pg
[/LIST]
If anyone has any ideas on how to solve this problem, then please help me find a solution, If i do not find a solution soon I am going to just completely reinstall Ubuntu and hope that solves it, although it probably won't. Thanks in advanced for any advice that can be provided and if you need anymore information please ask and I will provide it.

---

### Post by Avoozl on 2011-08-13
Does it also shutdown when you boot into Vista?  If so (I suspect it will) then reinstalling Ubuntu won't help.  Something went wrong when you installed the new CPU and fan.  You are probably right that it is overheating.  You should try checking the CPU temperature, which you can usually do in the BIOS.  It's likely either your fan or heatsink are not properly secured.

---

### Post by sbraz on 2011-08-13
this is weird. :O
try resetting bios to defaults, check if there's a bios update too.

---

### Post by Avoozl on 2011-08-13
Oh also, when your computer beeps those are actually error codes.  You can look them up online somewhere to find out what they mean depending on how many times it beeps and whether the beeps are long or short.

Anyway, reading your post again a little more carefully this is definitely a case of something being wrong inside your box (nothing to do with the Ubuntu OS).  You're gonna have to open it up again eventually.


Don't install BIOS updates from the shady websites you found.

---

### Post by RockPaperSissors on 2011-08-13
it is strange, when I boot up in windows it doesn't shut down randomly but it run extremely slow, and prolonged use makes it beep at me.
 
 I messed a little with the BIOS, but ill try resetting it to see if that changes anything. when i looked at the CPU temp. in BIOS it was normal, there wasnt anything wrong with it.
 
 another thing to add is that if i started up my ubuntu and let it sit and did nothing for about 10mins sometimes the problem would just go away on its own and I could do anything on my computer for hours without any problems.
 
the slow run time in windows and the random shut downs started almost imediately after installing this new chip so that leads me to believe that it is something in the hardware not connecting, i looked in the System Monitor and the computer recognizes the new chip so i dont think theres a problem with communications within the computer. ill look into this beeping thing more and see where that leads me, thanks for the quick replies

---

### Post by sbraz on 2011-08-13
> **Avoozl said:**
> Don't install BIOS updates from the shady websites you found.
i understand ECS is not a great brand but why not to trust the main website?

here it is:
[http://www.ecs.com.tw/ECSWebSite_2007/Products/ProductsDetail.aspx?detailid=685&CategoryID=1&DetailName=Bios&MenuID=52&LanID=0](http://www.ecs.com.tw/ECSWebSite_2007/Products/ProductsDetail.aspx?detailid=685&CategoryID=1&DetailName=Bios&MenuID=52&LanID=0)
[COLOR=RED]**i do not recommend flashing bios from windows. _[SIZE="3"]since your system is not stable as it is i'd reinstall the old cpu, check if it's stable, then flash from a pure dos enviroment.[/SIZE]_**[/COLOR]

---

### Post by IWantFroyo on 2011-08-13
Check your hardware's manual for voltage. My computer would randomly shut down with Ubuntu as well, until I found the manual and realized that my chipset voltage was too low. I upped it to the max, and now it works fine.

---

### Post by elgordodude on 2011-08-13
What are the beeps? 

e.g. three short. one long two short, etc

That's a motherboards way of telling you something is wrong, when googled with the mobo / bios we can find out what it's trying to say...

---

### Post by RockPaperSissors on 2011-08-13
I cant get it to beep anymore when i boot to windows :( once it is warmed up it works normally, oddly enough it still shuts off randomly in ubuntu

---

### Post by RockPaperSissors on 2011-08-13
I got this new chip off of Ebay so it didnt come with a manual :(, ill try looking one up online

---

### Post by sbraz on 2011-08-14
> **RockPaperSissors said:**
> I got this new chip off of Ebay so it didnt come with a manual :(, ill try looking one up online

[http://www.ecs.com.tw/ECSWebSite_2007/Products/ProductsDetail.aspx?detailid=685&CategoryID=1&DetailName=Manual&MenuID=52&LanID=0](http://www.ecs.com.tw/ECSWebSite_2007/Products/ProductsDetail.aspx?detailid=685&CategoryID=1&DetailName=Manual&MenuID=52&LanID=0)

---

### Post by RockPaperSissors on 2011-08-19
I looked at the updates and downloaded the one centered around CPU temp. and operations, I am going to restart my computer after this post and reset the updated BIOS i downloaded, although i do not think that will solve the problem.

 I also looked into the possibility that there was a problem with the power being supplied to the CPU, my power supply was 300watts and i upgraded it to a 500watts power supply, so if the CPU needed more power it would be well supplied. 

I was not able to replicate the beeping noises that my computer made while it was in windows, but I looked up what that might mean on Google and this site popped up [HTML]http://pcnineoneone.com/howto/bootprob2/[/HTML] the BIOS I have is an Award, so it suggests that either theres a problem with the ram or there was a video error, but since my video was fine during the beeps that leads me to believe that it was a ram issue.

My thoughts on this are that either this new CPU chip is faulty to begin with, my motherboard is starting to go belly up on me, or that there is something wrong with my ram thats needs further investigation. With this information my first action is going to be to test the CPU chip because all of these problems started when it was introduced into the system, so tomorrow I plan on reinstalling my old CPU chip and fan and seeing how that alters my computer (I say tomorrow because I don't have anymore of that CPU oil that you are supposed to use when installing CPU chips lol. :()

If anyone has anything that might help me solve this problem or any ideas on what might be the problem please post your ideas, I gladly except any help I can get; and thanks in advanced.

---

### Post by RockPaperSissors on 2011-08-20
I replaced the new CPU with the old one and now my computer is working perfectly, i guess this new chip was too fast for my motherboard or it was faulty or something else; either way the problem is solved, thanks to everyone that chipped in and help with my problem.

---

### Post by kerry_s on 2011-08-20
> **RockPaperSissors said:**
> I replaced the new CPU with the old one and now my computer is working perfectly, i guess this new chip was too fast for my motherboard or it was faulty or something else; either way the problem is solved, thanks to everyone that chipped in and help with my problem.

maybe you didn't have the cooler/fan seated properly. i'd put a new layer of arctic silver & try the new 1 again.

---

### Post by bcschmerker on 2011-08-20
> **sbraz said:**
> [http://www.ecs.com.tw/ECSWebSite_2007/Products/ProductsDetail.aspx?detailid=685&CategoryID=1&DetailName=Manual&MenuID=52&LanID=0](http://www.ecs.com.tw/ECSWebSite_2007/Products/ProductsDetail.aspx?detailid=685&CategoryID=1&DetailName=Manual&MenuID=52&LanID=0)I RECOGNIZE THIS BOARD!  This is the same mobo that gave me nothing but trouble under 8.04-LTS Hardy, and the problem is apparently rooted in the BIOS.  Elitegroup Computer Systems, unfortunately, uses Windows-centric firmware tools that, for me, resulted in uncommanded shutdowns without so much as unmounting the hard-drive volumes; I found the problem to be across all CPU's and chipsets in ECS' motherboard lineup.  Further details of the root cause are in 67GTA's topic [The DSDT Thread](http://ubuntuforums.org/showthread.php?t=1147474).

Recommend immediate rebuild of your system on a [Gigabyte®](http://www.gigabyte.com.tw/) or [Asus®](http://www.asus.com/) mobo of the same size format and chipset, as both manufacturers utilize the Intel® iACP firmware tool suite, which is known friendly to all operating systems.

---

### Post by Actonix on 2011-08-21
> **RockPaperSissors said:**
> I replaced the new CPU with the old one and now my computer is working perfectly, i guess this new chip was too fast for my motherboard or it was faulty or something else; either way the problem is solved, thanks to everyone that chipped in and help with my problem.

Like you say, with everything back to normal with the old CPU in place it could be a problem with the new CPU itself or it could have been an incorrect setting - both CPU's might use different voltages for starters - this is one of the first areas I would opt to look at.

Ordinarily your mobo' bios should be able to identify the processor and make all the required adjustments but when it doesn't you need to make those adjustments yourself - in order to do so you need info on the CPU and the only way you can do this without having the manual available is to look for it on the internet - visually examine the back of chip for identification, might be as much as 5 lines of info to take down and aid your search for info, with AMD chips it can be a bit of a pain as they can be obscure and in that instance you might be well advised to contact them directly - with the chip installed, switch on, enter the BIOS and update first thing and if you have it right you should be off to a flying start with your upgraded PC - you might do well to check out the settings that need to be modified with your old CPU still in place.

Alternatively, with the CPU installed you could load up window, 
... navigate to the control panel Start > Control Panel

... open the "System" control panel. or System and Security > System  in Windows 7


and here you should have a pop-up window appear that should gives the  technical specifications of your computer. This includes the producer of  the CPU, it's power and it's core number. This information together  identifies your specific CPU.


or alternatively use a utility like CPU-Z

... if you go down the above routes try and prepare by checking that you can do so satisfactorily with the old CPU in place.

 
 - should probably be no need for my saying so but be careful while handling your CPU, always try to hold it using the corners of the chip and try to avoid touching or bending the pins - also beware of static as it can easily kill the chip without any damage being visible - try and reduce any static charge before handling by first touching an earthed appliance ie your computer case or chasis which should be plugged in to the wall socket even if the switch on the wall socket is off

---

### Post by theskin on 2011-08-21
> **kerry_s said:**
> maybe you didn't have the cooler/fan seated properly. i'd put a new layer of arctic silver & try the new 1 again.

I agree , i had a similar problem years ago and was told to reseat the cpu and heatsink and it worked :)

---

