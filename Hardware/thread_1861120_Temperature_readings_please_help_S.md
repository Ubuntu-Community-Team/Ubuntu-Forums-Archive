---
title: "Temperature readings please help :S"
date: 2011-10-15
forum: Hardware
---

### Post by dnazer on 2011-10-15
Hello, I recently began experiencing a problem with my Nvidia GPU (GT 330M). Before we go any further I'll give you the system specs: 
Sony Vaio VPFC1290s 
Geforce GT330 M 
6 GB DDR3 RAM 
Intel Core i7 740 qm (1st gen) 
500 GB HDD 

My gpu usually idles around 45 C and tops out at 80-90 C on heavy games. The CPU idles around 55 C and goes till mid 70s under high loads. (measured using speedfan on windows 7 and Im_Sensors (ring sensor screenlet) in ubuntu 10.10) 

I was on Ubuntu 10.10 (maverick) yesterday and an update came up so I installed it. My fan started going louder than usual given the load (VPCF 1290s are known to have a loud fan but this was unusual even for me; ive had this computer for over a year). I shrugged it off as nothing and booted into windows 7. Now windows 7 wanted to update so i updated that as well. I noticed that the fan is going louder than usual under the load so I decided to look into it. My gpu was running at 70 C. There were no graphic heavy applications, and my usually hot cpu (usually hotter than gpu) was running at 55 C (idle). On windows 7 my gpu began to idle around 60 C, which isn't bad given that it can reach 90 C without shutting my system down. However, at any given moment, it would jump up to 72 or 75 in 1 second and then jump back down to 60 again. Luckily the fan would respond accordingly. On ubuntu, the problem seems to be much worst. I open chrome, the gpu jumps up to 90C. That's a bit high for chrome  (even though compiz is very demanding, my gpu handles it no problem until now)... 

So here I am asking for help because I have no idea what's going on. On one hand I was thinking that the updates perhaps made my gpu fan idle at a higher clock rate but that still doesn't explain the jumps in temperature under small loads. I thought about a faulty sensor but I have no way of checking that. And since the 90C jumps last for about 5-10 seconds each time, the laptop's exterior doesn't get hot. I'm confused as to what's going on and I hope that you guys will be able to help me out. I work under a hardware technician (I'm a student trying to learn a bit from him and am currently in 2nd year computer eng.) I may require things to be "dumbed down" a bit or preferably explained in detail. Whatever I don't understand I'll relay over to him. I am planning on opening the laptop up next week when I work with him. Any help would be much obliged. 

UPDATE: 
Restored windows 7 to before the update, the gpu still runs hotter than usual. But I did notice that the some of the CPU cores jump in temperature with the gpu. 

In ubuntu, things are much worst. A single right click will run the gpu up to 80 C. However I've noticed that the air it's pumping out isn't as hot as it should be. In fact its as hot as it was when it was idle, just coming out at a higher speed. Could this mean that it's a problem with my bios? (the bios is up to date). I can't restore ubuntu because I didn't backup before the update :( .

---

