---
title: "Generally on a laptop, is 8.10 worth it right now?"
date: 2008-10-31
forum: Hardware
---

### Post by bodselecta on 2008-10-31
I only started using Ubuntu about 6 month ago after buying a fairly powerful Dell XPS 1530 and I've loved it. I'd had some experience with *nix before but nothing serious, so using it as a desktop and a development laptop was new.
Everything I need I can get from Ubuntu and it runs so much better, but as a developer, some things were a bit painful to figure out and get working.

Everything worked eventually though, apart from wifi with the intel iwl3945 driver which regularly fails to load at boot and I get drop outs when it does load.

So is it worth upgrading to IBEX just yet and will I have to go through all the same configuration fixes/linking etc?

I had a quick look through the install notes and didn't see anything regarding wifi driver updates, but I'm presuming there's been an update as the drivers are released with the kernel now. 
Have they been updated?

It's the one last thing keeping my windows partition going because by booting into windows then back to ubuntu, it seems to wake the wireless card up.

Any advice or experience so far is greatly appreciated

Cheers

---

### Post by jheaton5 on 2008-10-31
I started with Hardy on my laptop and experienced considerable trouble getting my wireless iwl4965 card to function properly. I did a fresh install of intrepid beta around the first of October.  Everything, including the wireless card worked perfectly out of the box.  I have not had a minute's problem with intrepid throughout the last month of development and upgrades.

---

### Post by n0manarmy on 2008-10-31
I've been waiting for Ibex because of the problems I had with my Lenovo T400 wireless not working and was elated to find it was supported right out of the box. I'm not so much a developer as I work in the IT industry as support but I feel that if there's ever been a time to force myself to play in the *nix world, it's now.

Baring the fact that the Intel video card drivers still aren't fully functioning, it's been good so far.

---

### Post by Newtothegame on 2008-10-31
I am on an Inspiron 6400 started with 8.04 and installed 8.10 last night. So far its great. My wireless card is working, it didnt work out of the box tho. Also, its not using the proper drivers, which I have a post in general fourm asking about. 

But all in all, this release is more user friendly than the last. IMO

Also, the icing on the cake today for me was my BT mouse connection didnt take sudo commands.

Major issues I have been reading about are dealing with video cards, so look into those first and be prepared to use terminal if it doesnt find it. I am not sure if mine would have upgraded cause I killed it before upgrading.

---

### Post by laney_1 on 2008-10-31
im waiting because of problems found around the forums:

fan failure: fan fails to start up, frying the laptop.

fan stick on: fan seems to stay on 100% when nvidia driver is installed.

there maybe more minor ones but these are the most serious.

---

### Post by bodselecta on 2008-11-01
Thanks for all the replies.
It looks like a fairly mixed bag from what I've seen in the forums.

I too have an nvidia 8400 card and that worries me a bit so I'll probably hang back for a while to see how things develop.

What actually gets installed though on a regular release like this and what gets overwritten? I've made lots of configuration/environment changes to get things working with the tools I develop with, and it'd be good to know what I'd need to revisit.
Thanks again

---

### Post by Yellow Pasque on 2008-11-01
If you're using your machine for critical production, then I would recommend against upgrading to Intrepid unless you have a good reason (e.g. a program requires the latest libc version).

> What actually gets installed though on a regular release like this and what gets overwritten?
Your whole OS gets upgraded. During the upgrade process, if you've customized configuration files, you'll be asked whether you want to keep your customized configuration file or install the new configuration file.

---

### Post by sdennie on 2008-11-01
I'm surprised you are having problems with an XPS M1530.  I'm not using Intrepid but I am using Network Manager 0.7 and kernel 2.6.27 (which is what Intrepid has).  I've noticed that for weak wifi signals, that combination is noticeably better than what is in Hardy.  It may be worth it to upgrade in your case.  Or, ask if anyone else is having your particular problems in the Dell subsection of this forum.  I believe that Dell engineers even respond there.

---

