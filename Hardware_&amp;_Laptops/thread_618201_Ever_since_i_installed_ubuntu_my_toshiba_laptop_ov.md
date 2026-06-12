---
title: "Ever since i installed ubuntu my toshiba laptop overheates"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by Girindor on 2007-11-20
Ever since I wiped windows xp off my toshiba laptop and installed ubuntu gutsy gibbon (linux newb) i have been having problems with the laptop overheating and turning itself off. it has become very loud, as the fans are continually in operation, (especially when i'm running firefox), and when i start games that i have installed via the "add/remove application" function, it becomes so hot after a few minutes that the games just crash on me.
i did not have these problems under windows xp. i love ubuntu, it is so much better, i think, but does anyone have any tips of what could be happening here? i was expecting ubuntu to be LESS resource intensive than windows xp and thus use less energy and generate less heat.... ?
Thanx for your help!

---

### Post by aethralis on 2007-11-20
Have look at this issue, this may be of help: [https://launchpad.net/ubuntu/+source/acpi-support/+bug/22336](https://launchpad.net/ubuntu/+source/acpi-support/+bug/22336) Scroll down to the end of page to see the latest posts.

---

### Post by daimaru on 2007-11-20
if you are unlucky owner of a toshiba satellite p100 series laptop then i feel your pain, but I just fixed mine it now runs perfectly. by the way check your nvidia-settings and look at your gpu temperature thats what was overheating on my laptop. 

here's a link to the solution, i was going to write down how i fixed mine, but you could also just check the launchpad link and the two other sites listed there. 

[http://ubuntuforums.org/showthread.php?t=580876&page=2]("http://ubuntuforums.org/showthread.php?t=580876&page=2")

---

### Post by Girindor on 2007-11-20
> **aethralis said:**
> Have look at this issue, this may be of help: [https://launchpad.net/ubuntu/+source/acpi-support/+bug/22336](https://launchpad.net/ubuntu/+source/acpi-support/+bug/22336) Scroll down to the end of page to see the latest posts.

thanks for your help, unfortunately i spent ages reading through this but can't make any sense of it at all... i'm afraid i'm not a linux pro yet! ;-)

---

### Post by daimaru on 2007-11-20
if you need help i can send you a full step by step when i finished writing it. just tell me before if you actually want to do this otherwise I won't bother going through all that tedious writing :p
EDIT: do you have a p100 toshiba ? and check your gpu temp by typing in terminal
nvidia-settings then selecting "thermal monitor"
if nvidia-settings is not installed just search for it with synaptic and install it. if you gpu temp is at 90°C and rising when running for example "glxgears" then you have the same problem as i did.

---

### Post by Girindor on 2007-11-20
hi Daimaru,

thank you so much, your help is greatly appreciated.

i have a toshiba tecra A2, mobile, centrino. ever since i have started having these problems with ubuntu, i have taken the battery out and run the laptop straight from the plug socket. under windows xp, it used to overheat sometimes, but hardly ever did it shutdown - it just used to slow to a crawl, then i'd ventilate it a bit, then it would be fine again.

now, it overheates much more frequently, when i'm running much less programs (i now only run ONE application at a time), and it actually happens almost every time.

i use "hardinfo" to monitor the temperature - after having been is idle it reads 55C, as soon as i touch it pretty much it goes up to 70 or 75C, and i have often caught it above 80C (82, etc...) ...obviously when it gets so hot as to shut down, i don't have time to check the temperature. also, when it is hot, hardinfo sometimes just closes itself as soon as i start it!

all this is happening although i have set the screen brightness to only 20% to save resources!!!

i really do appreciate help with this so much! thank you!

---

### Post by daimaru on 2007-11-20
this sounds more like a heatsink or dirty fan  problem then the problem i had with the nvidia gpu fan not turning on and my graphics card overheating. you should try cleaning the vents with high pressure air and maybe you have to open it up and clean the heatsink and reapply thermal paste. 
this [guide]("http://www.irisvista.com/tech/laptops/Toshiba-Tecra-A2/notebook-disassembly-guide.htm") on disassembling tecra A2 might help, but i guarantee nothing. if your not sure you should better go to a hardware store and have them do it for you.

---

### Post by Girindor on 2007-11-20
thanks for the advise... i think i'd better take it to a hardware store.....
do i have to open it up to clean the vents with high pressure air? if not, i might give it a try myself... how do i do that?

---

### Post by daimaru on 2007-11-20
just try it, but if it overheats so fast i think it must be real dirty and the thermal paste is probably not doing a good job anymore so you are most likely better of bringing it to the shop. 

hope it works out and there's not a more serious problem with it. good luck

---

### Post by Girindor on 2007-11-20
do you think if i ran xubuntu instead of ubuntu that might solve some of the problems? (less resource intensive)

---

### Post by aethralis on 2007-11-20
I think the problem is that ubuntu (or as far as I understand some other distros too) start to scale down processor performance when it starts to overheat quite late and instead try to use active cooling (fan). So, if the fan does not cool (dust etc) the temperature rises and machine shuts down. Try ```
cat /proc/acpi/thermal_zone/TZ00/trip_points
``` on your machine and see what it says (my thermal zone is TZ00, yours could be different). In this case the cleaning of fans could be the best solution you have at the moment.

---

### Post by imon9 on 2007-11-20
the easiest way to clean ur fan without opening the case is use a vacumm cleaner and suck the dust out.

it doesnt clean it 100% but i'll say at least 70% dust will come out

(plus, disclaimer: no gurantee it wont hurt ur laptop, but i do this to most of my laptop)

---

### Post by Girindor on 2007-11-21
thanks, i'll try both those things...

---

### Post by Girindor on 2007-11-24
> **aethralis said:**
> I think the problem is that ubuntu (or as far as I understand some other distros too) start to scale down processor performance when it starts to overheat quite late and instead try to use active cooling (fan). So, if the fan does not cool (dust etc) the temperature rises and machine shuts down. Try ```
cat /proc/acpi/thermal_zone/TZ00/trip_points
``` on your machine and see what it says (my thermal zone is TZ00, yours could be different). In this case the cleaning of fans could be the best solution you have at the moment.

i've vacuumed the dust out of my fans, and it seems to have improved. however, when i do anything resource intensive, it does still overheat and shut down. just now i was playing a game and suddenly the laptop started shutting down, i saw something about critical temperature of 85C had been reached and shutting down.

your terminal command doesnt work for me - is there a way of finding out what my thermal zone is, so i can try that instead of "TZOO"? thanks!

---

### Post by Girindor on 2007-12-05
ok, i've found my thermal zone, finally ;-)
...it's called THRM

it states the following:

critical (S5):           102 C
passive:                 102 C: tc1=9 tc2=2 tsp=1800 devices=CPU0 
active[0]:               102 C: devices= FAN 
active[1]:               102 C: devices= FAN 

clearly, 102 C is just really! too high for my laptop to cope. does anyone have a clue as to how it might be possible for me to lower the critical temperature, so that my laptop starts slowing down early enough?

thanks!!

---

### Post by Girindor on 2007-12-12
have meanwhile managed to find a solution to this myself, thought I'd share it in case anyone else has these problems...

I changed my cpu-frequency-governor from "ondemand" to "conservative". this means that it generally uses less cpu, and thus doesn't get as hot.

instructions at [http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling](http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling)

---

### Post by jakejas on 2007-12-16
I am having an overheating problem with my Compaq Evo N610c as well. I have Kubuntu, Studio ubuntu (gnome destop environment), and Xubuntu loaded on it. It still overheats when I use the Xubuntu desktop environment.

---

### Post by Girindor on 2007-12-26
I am getting really frustrated. The CPU-frequency scaling governor switches back to "ondemand" every time i boot up. Here: [http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling#Using_Frequency_Scaling_Governors](http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling#Using_Frequency_Scaling_Governors) 
it simply says to "set the governor in your rc.local, to make it used on every boot".

How do i do that? no idea! I have spent hours and hours searching the internet. I can't find any solutions, only loads of people who are having the same problems, with no solutions.

I used "slocate" to find the rc.local, and I have found TWO: one under /etc/rc.local and one under /etc/init.d/rc.local

Which one do I edit? Again, no idea. I have tried putting the script (and variants thereof) in both files, in all sorts of different places, to no avail. Everytime I reboot it loads the "ondemand" governor.

PLEASE, can someone help me. I am sick of my laptop overheating all the time. It didn't do that in Windows XP. How is it that in Ubuntu it is not possible to scale the CPU back to a sensible amount? I can barely run more than two or max. three applications at once without it crashing, it ALWAYS crashes when I try to rip a CD.

Does anyone know whether this is better in other linux distros. I'm thinking of reinstalling windows - which I hate, but at least it doesn't kill my laptop all the time :-(

---

### Post by Girindor on 2008-04-30
The only way I have managed to get it to work is by installing "Ubuntu Tweak" from getdeb.net
...it has some options to add a cpu frequency scaling option to the power management dialog of gnome. ...so with that i now use cpu governor "powersave" and have not had overheating troubles since (but it means my cpu is on a permanent 600Mhz instead of 1.5 Ghz...)

---

