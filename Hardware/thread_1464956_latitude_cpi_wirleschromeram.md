---
title: "latitude cpi wirles/chrome/ram/"
date: 2010-04-28
forum: Hardware
---

### Post by kmsalex on 2010-04-28
i know this is a lot to put into one post but it doesn't seam right to brake it up into 4 different threads since they all have to do with the same box.

OK since this past august i have been tinkering with a latitude cpi d266xt, it was an old laptop given to a teacher/friend/ by another teacher/friend. but before he gave it to her he formatted the hardrive, over the summer me and a few other people were helping her paint her paint her classroom and i stumbled across it in the closet. I took it home and first i tried puppy Linux which took about a day to get the right screen settings. but after i got puppy going i realized this was going to be used by people that are most used to the windows xp stylee of doing things. up till now i wasn't to firmuler withLinuxx i had never even heard ofUbuntuu, but after somegoogilingg i stumbled across it and desisted to use 5.10
(it was the earliest version i could find) it took a few days to get that working but once i did i turned to try and get the internet working after a little while of tinkering with my roungter (at the time i didn't have a wireless one i had the Internet working) but the wirless wasn't working. so now i turned to win 2000 wireless was still not working. this was a week or so after i started with it and my summer was drawing to a close. so i installed ms word and put it in a corner till September i gave it back and when she found out Internet didn't work she put it in a file cabinet and never tuched it.

Around January i got Ubuntu on my main computer thats when i desisted to give the latitude another chance. by this point i had discovered xubuntu. so idesisteded to give 9.10 a shot. after a lengthy install i booted into the slowest desktoI'd'd worked with in a while. just opening the system-monitor would max out the CPU 100% the ram usage was surprisingly low at about 80mb out of 128mb with about 40-60mb swap. lunching Firefox would take about 45 seconds. now it was about 7:00 pm and after sitting in a classroom alone since 4:00 pm staring at a slowly moving progress bar with error message after error message during the install i had had it. i was ready to throw it agents a wall but realizeded that would accomplish nothing. so i put it back in the file cabinet and when home some time in march i tried again with xubuntu 8.04 with a much faster install but similar performance. so i put it back in the file cabinet again and again when home. now its late April and i have desisteded to give this one more shot with xubuntu 6.06. 

Now here is issue one, the wireless pci card, i think is probably my fault when i first brought the laptop home i stopped at a neighbor and i wanted to show him how old it was but when i opened the case the card feel out about 3 feet to a asphalt driveway I'm prity sour that killed it if it wasn't all ready dead. so i was looking at some relay cheap replacements (as I'm not going to be using this and I'm not going to ask for the money)
[http://www.amazon.com/gp/product/B00074EK1Y/ref=pd_luc_sbs_01_02](http://www.amazon.com/gp/product/B00074EK1Y/ref=pd_luc_sbs_01_02)
[http://www.amazon.com/Belkin-F5D8013-Wireless-Notebook-Card/dp/B000RMT90I/ref=pd_cp_e_3](http://www.amazon.com/Belkin-F5D8013-Wireless-Notebook-Card/dp/B000RMT90I/ref=pd_cp_e_3)
the first is a g and the second is an n, i would defiantly pay the extra $2 for the n but I'm not sour if 6.06 will even support the g card or if the mob will. if they will do you think they will support the n card?

The second problem is 6.06 comes with Firefox 1.5 which is slow to load and to old for flash or Java now i could upgrade to 3.6 but as much as i love Firefox i know it somethimes runs lagy even on my current system and has a prity good sized memory foot print compared to chrome or opra. so i when i try to install chrome with a .deb pakage i get a genaral could not open "insert filename" check to see if the file is corrupted and then something about checking your permission level. i think that might have something to to with it not asking for my password like ubuntu normally would if i try to do something like installing a program. if anyone has any suggestions on that they would be greatly appreciated. also if anyone has other browsers that would run better on a 233mhz pII please feel free to suggest. 

also i was considering uping the ram to the max 256mb but i can't find any cheap options, if anyone can find 2 128 mb sticks for under 15 dollores let me know. i was also thinking about getting a cheap 4gb ide ssd to replace the 12 year old 3.4 gb hard disk. which i have a bad feeling is geting ready to fail any time now.
 

 Sorry if this post got to be a little bit longer then I had originally hoped. just answering one question is greatly appreciat :)

---

### Post by kmsalex on 2010-05-01
*bump*

---

### Post by kmsalex on 2010-05-01
*bump*

---

### Post by snowpine on 2010-05-01
Hi kmsalex, this is probably not the answer you are hoping for, but I would not recommending spending any money to improve this particular computer. Even if you buy a new wireless card and max out the ram, you will not meet the minimum requirements for Ubuntu:

> The Recommended Minimum System Requirements should allow you to run an installation of Ubuntu well. While you can usually run Ubuntu on hardware of lower (and sometimes much lower) specification, performance will necessarily suffer. Most users (especially those new to Ubuntu) risk frustration if they ignore these suggestions.

Ubuntu Desktop (GUI) Installation
1 GHz x86 processor
512 MiB of system memory (RAM)
5 GB of disk space
Graphics card and monitor capable of 1024x768
CD-ROM drive
Sound support
Internet access

I would recommend running a lightweight distro (such as Puppy Linux, which you said worked fine) and saving your money towards a newer computer. Used Pentium 4 computers are often available under $100 and will run Ubuntu easily.

ps Ubuntu 6.06 is no longer supported. You need to use 8.04 or newer.

---

### Post by kmsalex on 2010-05-01
But i'm not running ubuntu i'm runing xubuntu 6.06 which have significantly lower requirements then that, and i can use 6.06 i just won't get security updates anymore. 
In the last few hours i've been trying out lubntu 10.04 (beta 3 is the newest) in virtual box with 128mb ram cap, 2mb video cap, and the processor as low as i can set it to 1ghz and its been ruing at about a third of the 128mb ram watching youtube videos smooth with google chrome as the default. and i'm not going to buy a new computer out of my pocket when i'm not going to even use it. keep in mind my primary source of income is cutting lawns with an annual income of about 300 Dolores. But i do appreciate the suggestion.

---

### Post by snowpine on 2010-05-01
I think your project sounds fun. I am not trying to discourage you from getting Linux onto that laptop, just helping you find a solution that will satisfy. 

Lubuntu sounds very promising! (I haven't had a chance to try it yet.) I would recommend you go with a current release rather than an old one like Xubuntu 6.06. Lack of security updates is only half of the problem with 6.06--the other half is that software will be out of date and you will have a hard time installing the latest applications like Firefox 3.6, Chrome, etc. These developers do not "package" their applications for 6.06 any more, since it is an obsolete platform. :)

---

### Post by kmsalex on 2010-05-02
Ok I've desited to go with lubuntu i have 10.04 beta 3 installed and its running smother then xubuntu 6.06 by a considerable margin. It comes installed with chromium as the defualt so that solves that problem. Also i don't think upping the ram is relay necessary but it if i can find a realy good deal i might take it.
The manger next step is choosing the wireless card, i am still looking at the same 2 cards 
[http://www.amazon.com/gp/product/B00074EK1Y/ref=pd_luc_sbs_01_02](http://www.amazon.com/gp/product/B00074EK1Y/ref=pd_luc_sbs_01_02)
[http://www.amazon.com/Belkin-F5D8013-Wireless-Notebook-Card/dp/B000RMT90I/ref=pd_cp_e_3](http://www.amazon.com/Belkin-F5D8013-Wireless-Notebook-Card/dp/B000RMT90I/ref=pd_cp_e_3)
lubuntu should be able to recognise either of them the question is whether or not the mob will be able to detect them.
lastly I'm still considering a 4gb ide ssd if i can find one under $20.

---

