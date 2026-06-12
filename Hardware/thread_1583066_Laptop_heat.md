---
title: "Laptop heat"
date: 2010-09-27
forum: Hardware
---

### Post by xbobby_bobx on 2010-09-27
Hi guys ok I'm having this problem with my laptop since it's the only computer i have and i dont have enough money to buy one but here is the problem
 
my hard drive is getting over heated (i guess) when i use it for like 5 minute i can feel the heat of it its like so hot when i type sensors i get an avg of 52-55 which i guess is a normal CPU speed but I can't measure my hard drive heat and im really concerned about it. I need ubuntu on my laptop because it's fast and stable more than my windows vista 
 
Oh and when i go on my windows side i cant barely feel any heat. I know there is a lot of threads about this problem but is there any way to measure my hard drive temp?
 
and if its hotter than the normal what should i do to reduce the heat?
 
<eMachines/ E625/>

---

### Post by TBABill on 2010-09-27
I suspect the heat you feel is more likely coming off your CPU or graphics card rather than from the hard drive. Your hard drive spins at the same RPM in Win or Ubuntu. If your hard drive is getting hot under Ubuntu where it is of concern it is probably doing so by picking up the heat from a nearby device that runs cooler in Windows.
 
A couple things you can do to make it run cooler are:
 
1. Make sure you are using the proprietary graphics driver for your graphics card/chip. This is crucial when heat is a concern. 
 
2. Add the CPU frequency scaling applet to the top panel by right clicking the panel and select "add to panel", then choose it from the list. Once it is on the panel, just left click it and select ondemand. That runs you at about 1/2 speed on your CPU until the system requires more power and it automatically jumps up, then returns when not needed.
 
3. Use Adobe Flash and Sun Java. Open source apps for flash and java work your machine harder.
 
I believe there is an app or aplet to monitor hard drive temp specifically. Check that list in "add to panel" and also search synaptic for "temperature" and scan the results list.

---

### Post by ajgreeny on 2010-09-27
What graphics card does the computer have?
What version of ubuntu do you run?

There have been several threads of overheating of laptops in particular running 10.04, Lucid, where the kernel does not work properly with power management (I can't remember the right acronym, but KMS, I think) leading to great overheating when some ATI and nvidia cards are installed.

I can not run Lucid on my laptop as it gets incredibly hot, but Karmic is fine, and that machine has an ATI 9000M card.  Try Karmic perhaps, or even the beta version of 10.10 which I believe will be a lot better as it has a later kernel where KMS works fine.  Even the alpha3 version of 10.10 does not overheat on my laptop, though I have not yet updated it to the beta.

---

### Post by IcarusR on 2010-09-27
I would clean out the air vents with an air duster aerosol (they are cheep) first before changing to 9.10. (switch off first)
Laptops are susceptible to dust build-up in the small air ducts. Even if it does not resolve your problem it will help with cooling in the long run.

> on my windows side i cant barely feel any heat

Sorry just re-read OP properly.

---

### Post by amireldor on 2010-09-27
I'm having a similar problem. I'm on HP Pavillion dv6282 machine. Will be monitoring this thread :)

---

### Post by gordintoronto on 2010-09-27
You should install HDDtemp and sensors-applet using Synaptic.

---

### Post by angryfirelord on 2010-09-27
I would say the problem is the Radeon X1200. Under Windows, the card is using the proprietary driver, which means that it is also employing power-saving features that reduce heat. Under Linux, it is using the open-source driver, which to my knowledge doesn't have much of a power saving feature. The next Ubuntu release should have a working KMS, so you should see better results when it's released.

You can try UMS if you don't mind some tinkering: [http://www.overclock.net/linux-unix/731469-how-power-saving-radeon-driver.html]("http://www.overclock.net/linux-unix/731469-how-power-saving-radeon-driver.html")

---

### Post by jcolyn on 2010-09-27
To determine hard drive temp first check synaptic to see if hddtemp is installed then at the terminal enter ```
sudo hddtemp /dev/sda
```

---

### Post by c00lwaterz on 2010-09-28
I have problem also in laptop heat. I suspect GPU and fan. GPU gets so hot but fan is not running. I tried many tips and help but nothing works even other distros did not work.
Toshiba m900

---

### Post by gordintoronto on 2010-09-28
Message 24 of this thread:
[http://ubuntuforums.org/showthread.php?t=1420247&page=3](http://ubuntuforums.org/showthread.php?t=1420247&page=3) 
might be helpful.

---

### Post by TBABill on 2010-09-29
This is a very preliminary observation since I just upgraded to 10.10beta last night, but after the upgrade (did not reinstall fresh...upgrade was flawless) I did notice my machine was much cooler than Lucid. I used the same configuration items, such as CPU scaling, in both. I did run some videos and my temps rose, as normal, but my fan reacted appropriately and varied in speed as necessary. The temps of the heat exiting the machine were a bit cooler, but my sensors do not report correctly so I cannot be certain. Mine is stuck reporting 26.8C regardless of the situation. I have installed lm-sensors and others, but nothing seems to change for CPU temp reporting (Intel Core i3-330m).
 
Anyway, I would not suggest moving to the new beta (or is it RC now?) for most people but if you have an empty partition you can install it on to try it out to compare heat results it could be a possibility for you. Just keep in mind I have only used Maverick for a few hours so my observations are not thorough yet.

---

### Post by tadaskr on 2010-09-29
The problem why Lucid is so hot, because GPU always runing on maximum clock, but normal Lucid is coming with 2.6.32 kernel and it can't change GPU clock. If there is any way to change it to on demand mode then much heat problems could be fixed

---

### Post by amireldor on 2010-09-29
Since I installed `hddtemp` I did not feel my hard disk get hot as before. Maybe I'm dreaming and maybe it's still early to tell because only a few days passed.
I'll post again if it gets hot.

---

### Post by ricks.wesley on 2010-09-29
It may not be your HD which is getting overheating; it could be your other possible hardware config.

---

### Post by ajgreeny on 2010-10-01
It may well be worth your trying the newer kernels from the ubuntu kernel ppa repository.  I am running kernel 2.6.35-22 on lucid with no problems at all.  I tried it on a laptop that would not even run lucid as it got burning hot, but with the updated kernel it runs nice and cool again.  Make sure you get the right kernel for your system architecture, and it's probably worth also installing the two header files as well, appropriate for your system architecture.
[http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu)

If it does not help there is no problem removing that kernel in synaptic.

---

### Post by Jimtheplanner on 2010-10-07
Hi Folks,

I've done a little experiment....As my hard drive gets quite hot. I have a WDC WD3200BEVT-22ZCT0 in my laptop.

When I run Ubuntu 10.04 I get: ~
> 50-52°C

When I run Mandriva 2010.1 I get

> 40-42°C

The above are averages, where I've taken the temp at random time over the course of a day. The Manufacturer WD recommends a max of 60°C. However; when I google around the general consensus is the lower the running temp the long an HD will last.Although 10°C may not seem a lot it is rather noticeable.

So is there a way to lower the Ubuntu HD temperature? As I write I have 

> sudo hddtemp /dev/sda
/dev/sda: WDC WD3200BEVT-22ZCT0: 50°C


Jim

---

### Post by xbobby_bobx on 2010-10-14
Well I was successful to reduce my HDD temp but now I have a new problem the CPU temprture is getting really high minimum of 50 maximum of 57 i know you are gonna say this is not hot but if you have a laptop use it for 2 hours then go and check your charger if it's not hot that means you are so lucky my charger is getting so hot and the CPU too while on windows its pretty warm and I tried to install the property drivers but i discoverd it will mess up my computer so no any other ideas?

---

### Post by xbobby_bobx on 2010-10-14
My graphic card is ATI x1200 open source driver and i dont think its the problem check PCLINUXOS its actually colder than the windows itself i would love to install it on my laptop but its not a wubi and i dont trust the dircet install anymore. And yeah its not a graphic card problem.

---

### Post by xbobby_bobx on 2010-10-14
And why PCLINUXOS is sooooooooooooo cold? its perfect for laptops and desktops but what is the special thing that makes it cold is it the kernel or what?

---

### Post by TBABill on 2010-10-14
You may be using the newer kernel on PCLinuxOS. I believe I am using 2.6.33-5BFS on PCLinuxOS, which may handle your graphics GPU better than the 2.6.32 kernel in Ubuntu. Other users previously mentioned you could try to use a newer one in Ubuntu to try it out and your experience with PCLinuxOS may support their suggestion to try on Ubuntu.

---

### Post by xbobby_bobx on 2010-10-14
I never used PCLINUXOS but a lot of people said it's actually cold and I can confirm that too well I don't want to touch my kernel I don't want to mess up my computer :/.

---

### Post by TBABill on 2010-10-14
Adding another kernel will not affect the current kernel. Grub2 will show both on startup and ask which you choose to use. If you don't like the new one you can just remove it or just boot into the other one instead. It won't hurt your system to try.

---

### Post by xbobby_bobx on 2010-10-14
Ok I'm gonna give a kernel upgrade a shot but if it mess my grub file and give me the stage 1.5 error 22 my teacher will kill me because i do my whole work on this computer but anyway I was reading that ATI drivers suck on Ubuntu so they asked me to install the property drivers which I have nooooooooo idea how to do it any help to install them?

---

### Post by TBABill on 2010-10-14
Ok....first thing is to NOT do a kernel upgrade if you aren't sure how and that is a production machine. Until you can find a how to I'd suggest doing some search to walk through the whole process. I assumed you were more experienced and I don't want you to bork anything on a machine you count on.

The video part is easier but you have to know which driver you need. The proprietary driver will make the most heat difference anyway. Post the output of > lspci in a terminal.

---

### Post by xbobby_bobx on 2010-10-14
Mine is ATI radeon x1200 but too late i messed up my computer now I dont have the visual effects anymore and I want my old settings back :(

---

### Post by xbobby_bobx on 2010-10-14
Now how do I restore everything? if there is no way to do it will have to reformat and reinstall ubuntu again and probably not installing it at all i think this is the end of journey with linux it's really bringing me a headache i do like it but i cant keep it on my laptop. well i hope someone will help me with this again my graphic card is AT Radeon x1200 with i dont know how to say this but yeah i dont know what driver i have now its really messed up now :/

---

### Post by TBABill on 2010-10-15
Ok, depending on the situation I may also need some assistance from others to help you get back up to speed. But we will need to know the current state of your machine. Here are some questions I have that will help clarify where it stands, but there will surely be more questions as well. Linux isn't bad at all to work with but there are some things you have to do and learn along the way to help better understand how it is different in how it operates and configures than Windows. It's not bad, just different, and the first month or two is very enlightening if you stick with it and remember what you learn going through a few pains. And if it's a production machine like yours, ask questions, do lots of searches on the forums for answers from people who did the same or similar before you and take extra cautions to protect your working partition (once working). I recommend making 2 partitions, even if one is fairly small, just to play around and not care if you bork something on that partition. Just my 2 cents...so many here worked with me to help me along the way and there is a wealth of info here and on the help.ubuntu.com site when you need it. And Google is a great asset as well since there are other Ubuntu sites to assist also.
 
1. When you tried to install another kernel how did you do it? Preferred method is to just go into Synaptic, find the kernel you want (make sure it's 32bit or 64 bit, depending on what version you installed - don't try to switch between them), select mark for installation and click apply. Then reboot, select the new kernel in Grub 2 and see if it works. If it doesn't just reboot and select the old one till you can figure out why the other didn't work or just to stick with what was working before.
 
2. How far will your machine boot up? At what stage does it stop and do you get any error messages? What are they if you do get them?
 
3. Can you boot into safe mode?
 
4. Did you try to install any display drivers when you did the kernel install?
 
5. Did you do anything else or perform updates at the same time as the kernel install? Updates, config, apps, etc?
 
This should help get us started. You can always boot from the LiveCD and mount your home folders to create a backup of your data. That should not have been affected unless you tried to reinstall Ubuntu. And if you do get all your data off, then if something has failed and cannot be restored you can just reinstall right over your existing install and then copy your files back into your home folders.

---

### Post by xbobby_bobx on 2010-10-15
I'm really really sorry to waste your time I do feel bad now but last night I messed up my video card so bad on ubuntu side and I thought that my information on Ubuntu not that important to me just few pictures and some commands I saved tp learn more about Ubuntu just to let you know I'm not a total noob I actually activated my wirless card on my own without any deep research anyway I alreardy partioned my HDD with 10 GB which i think it's enough to me but I removed my Ubuntu 10.4 LTS from the machine after what happened and decided I will install it again but this time I will upgrade/add the new Kernel which I heard it's kinda worse but i will give it a shot oh and by the way is Ubuntu 10.10 better or worse? I went to the website and they said the BCM 4012 will not work on it which its my wirless card. I know I have a bad luck but if you know anything about 10.10 please tell me ok?
ps. kernel 35 is not the package manager :(

---

### Post by TBABill on 2010-10-15
Ok I'll do my best. To answer if 10.10 is better or worse is difficult because I don't have the same machine. I have 10.10 working fine on a Dell with the same wireless as you and I helped someone get theirs going as well here: [http://ubuntuforums.org/showthread.php?t=1593649](http://ubuntuforums.org/showthread.php?t=1593649) So wireless should not be an issue.
 
The video card part is not as easy. I think support for the 1200 is gone in 10.10 but I only base that on threads I have seen in the forums. Search for your specific card model and 10.10 in your search criteria and see what you find. I would just be safe and go with 10.04 if I were you. I think if you search for your model video card and 10.04 you may find the exact answer of how to get it going. The drivers are in the repo but it is imperative you do two things: 1) install the right one and 2) remove the open source driver if you get your proprietary one installed. The system has to know what to use in order to work properly.
 
I honestly don't believe kernel version is your issue but only you can know based on your findings installing, updating and getting drivers going. I also would recommend installing the video driver AFTER all updates are applied. There are likely some kernel updates in there that may improve what you experienced before you install the driver.
 
Bottom line from my perspective is I recommend sticking to 10.04 till you know enough about configuring and tweaking your machine to jump into 10.10 where there have been posted issues with that video card on the forum. The open source drivers are supposed to work much better on 10.10, however, but I cannot personally attest to that. Do lots of searches before jumping into a fix, and trust the [SOLVED] threads before any others to confirm the fix proposed actually solved the problem posted.

---

### Post by xbobby_bobx on 2010-10-15
Oh I don't make updates to my Ubuntu since i got the kernel panic thing 3 times after the update I stopped doing it but i will follow what you said and stick with my 10.04 because I trust what you say and for the Graphic card it's ok don't worry I'm not going to try again to install them I will stick with the default :) but I guess the temp thing will stick with me if I don't make a move should I try the kenrel upgrade?  and Don't worry about the 10.10 I will install it tonight just to see how it's look like i will follow your guide to activate the WIFI and I will never use NDISWRAPPER :P oh well you helped me a lot but I will give you the updates about what will happen is that ok with you? pleaseee. :P

---

### Post by TBABill on 2010-10-15
No worries about updates...ask and post away. And if you run into various issues don't be afraid to make a separate post for each problem separately. You'll get much better help if you focus each post on a single problem. It gets too confusing mixing them together if a lot of people try to help out and sometimes the messages get confusing when you go try to follow some of the recommendations.
 
Anyway, yes I recommend a fresh install, then run all the updates. After all that then you can take each configuration step one at a time (wireless, then video, then whatever else, such as printer and other devices, additional software). By isolating them to step by step you eliminate any confusion for yourself and you can more clearly post your issues if you need assistance.
 
I have the same wireless card you do. I never use ndiswrapper. I do my install, do my updates, the go to system>administration>hardware to see if there is a recommended proprietary driver available. For mine it was the Broadcom STA driver and it works flawlessly. Let the system recommend a driver before you try to install anything. And there is no need to install anything from outside the repos unless you exhaust all the possibilities for your video card, but only do that after your system is updated and stable. And you should only need to plug into an ethernet port on your router one time to get the updates and driver. After that you should be good to go wirelessly.
 
We can fix the heat issue after you get the video driver working properly. That's the key to most heat since I am pretty sure 10.04 defaults to ondemand cpu frequency scaling. The rest is Adobe Flash (not Gnash), Sun Java (not open java/iced tea plugin). Hopefully the whole combination of things keeps your temps in the mid 40's/50s under normal use to mid 60's under heavy use and heavy flash apps. I'm not sure mine even reaches the 60s anymore but at one point I had a machine on Karmic that hit 80 and I shut it down, then on 10.04 on initial release as well so I switched. The kernel settings have improved since then and I run cool again.

---

### Post by xbobby_bobx on 2010-10-15
I don't have A router or any possible eithernet connection so yeah I guess I will have to go and Search fourms about how to make things work properly well The first thing I'm going to do is use Wubi for sure then install the 10.10 and as what you said I will get the WIFI first which i think i will do the same steps as my 9.10 and 10.4 going to the ISO and install dkms and dpkg then the BCM STA driver its the easiest thing I ever did on the previous versions but im not sure about this one is it the same?

---

### Post by TBABill on 2010-10-15
There may be a way to get it from the LiveCD but I have not had to so that may be a good one to post right now as a separate post. Just "how do I enable the Broadcom STA driver for a Broadcom BCM4312 wireless adapter from the LiveCD since I have no access to an ethernet port?"

---

### Post by xbobby_bobx on 2010-10-15
It's Ok i know how it works you will just insert the disc and it will do the whole thing but in my case I use the ISO image which I have to install everything manually but i will take your advice because it might never work you know.

---

### Post by TBABill on 2010-10-15
Actually the CD won't install that driver automatically because it is proprietary. That's why I suggested posting a question on the forum asking if there is a way to get it off the CD after the installation is complete. I have seen where others made it work but I'm not sure how to do it.

---

### Post by xbobby_bobx on 2010-10-15
O.o really? then wht it worked for me on 9.10 and 10.4? it says BCM STA has been installed when i got to jockey or the property hardware manager I can actually see it activated and ready to go that is weird maybe they changed it? I don't know by the way are you gonna help me if i had another problems? cause actually you are the best guy who ever helped me through this so yeah thank you :)

---

### Post by TBABill on 2010-10-15
I'll help however I can. Just post if you need assistance :)

---

### Post by xbobby_bobx on 2010-10-15
Ugh!!!! Ok I installed 10.10 and it worked so good WIFI recording Compiz and other stuff that i felt its better than 10.4 but the problem is the CPU temp is 57c as a maximum and normal as 52c this is kinda normal but check the HDD temp it's 53 with no decreasing well I used it without my cooling pad but i guess if I use the cooling pad it will go back to 47c as a maximum any ideas about this kenrel?.

---

### Post by TBABill on 2010-10-16
Those are pretty normal temps. I'm not sure you can get the system much cooler than it is running. Most machines I have seen don't hit critical temps until 90+C. Mine all hit max at 99 before shutting down. I have never let them get above about 85 and that was when there was a flaw in 10.04 that was quickly corrected in the kernel. I get into the 60s under heavy flash app use but other than that I stay around 50-55C.

---

