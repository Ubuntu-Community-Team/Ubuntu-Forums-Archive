---
title: "ATI Xpress 1150 controlling shared memory"
date: 2010-02-15
forum: Hardware
---

### Post by crestfallentoo on 2010-02-15
hey guys,
this is my first post here, and also I'm a totally noob in Linux
I had installed a few years ago the Red Hat 8 or 9 but I quit after I saw I didn't had enough software for it... 
Now I'm back in Ubuntu 9.10 because I'm sick and tired of reinstalling Windows XP after 3 months because it's slowing down my system...and I'm determined to keep my Linux and slowly remove the XP

ok, so here's my situation:
I have an HP Compaq nx6325 notebook (yes, I know it's old)
it has: AMD Turion 64 x2 (dual core) (does it worth to install the 64 bit Ubuntu?)
1 GB RAM -  actually now I have only 876 MB
ATI Xpress 1150 with 128 RAM that shares another 128 RAM from the system 

When I got it I remember configuring from Windows, and as I remember from ATI Catalyst Control Center.. in the way so that the graphic card steals 128 MB from the systems RAM... 
well I don't play games anymore so I need that 128MB of RAM back... but... and here's the tricky part.. I can't find that option anymore... I don't know why but .. I can't find the section where I could choose if the graphic card should share some memory or not..
I called HP Support, and they didn't help much, I send an email to  ATI, and they say that the vendor or HP should offer support ... I've spend time on HPs forums...and still no solution
I know that it cannot be configured from BIOS (though a lot of people say that) but for this system it's not from BIOS, it was from somewhere within Windows
and I turn to you guys now..

I'm thinking if Linux is so configurable and so tweaking... I might be able to write some lines in some files in that way...that ... I will have my 1 GB back.. 
do you guys know if... and how to do this....???
thanks a bunch :)
btw.. should I install the 64bit version???
thanks Bye
Andrei :)

---

### Post by crestfallentoo on 2010-02-16
up...

---

### Post by benmoran on 2010-02-17
Hello, 
First of all welcome. Well, I asked pretty much the same questions as you a while back about the video card. It turns out that this card is a real oddball. I never was able to get an answer to how to change the memory under Linux. I hate to say it, but you might have to reinstall windows and the ATI proprietary drivers again in order to adjust it. The Linux version of ATI Catalyse Control Center (9.3), which was last supported on Ubuntu 8.10 before ATI dropped support, didn't even have this functionality. Sorry I can't offer any other suggestions, but hopefully someone else can. Reinstalling Windows just to change a tiny option is a bit of a pain in the ***. 

In case your not aware, you are now using the fully open source graphics stack. It's been advancing at a pretty phenomenal rate.

---

### Post by waynefoutz on 2010-02-17
I have the Xpress 1270. If you install Karmic, you are going to get SOME 3d out of the box. Not everything is going to work. If you install Hardy Heron (8.04) or Intrepid Ibex (8.10) and use ATI's catalyst driver, version 9.3, [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English")
You'll get full 3d. We are pretty much stuck with the open source drivers on the modern versions. If you aren't into gaming, or you don't mind dual booting XP and use that for games, then the open source drivers are ok. If you want a gaming rig that runs ubuntu, your best bet is to stick with Hardy for now and use the old catalyst driver I linked to. The good news is they are working on the open source drivers. I'm hoping when Lucid comes out in April our ATI cards will be fully functional again. Right now I'm running intrepid, but support ends for that in April. Hardy is good for another year.

As for controlling the shared memory..in my card I  make that adjustment in my system's bios. Is your's different??

---

### Post by crestfallentoo on 2010-02-17
hey,
thank you both for your explanations 
so, I understand that I can't do much in Linux, that's no biggie, I'll resintall Windows with it's full software from HP and hope to find that option where I change the shared memory...
@benmoran
yeah, I know it's a pain but I'm used to do this with Windows, that's why I'm changing to Linux :) to get rid of reinstalling the OS at every 3 months or so... 
@waynefoutz
I haven't played any games in the past year or so (though I've tried Nexuiz and Alien Invation).. I rather have some extra RAM for the system than my graphics card... and yes... my system is a little different,...I don't have that option in BIOS, my father also has an HP and he does have the option in BIOS... kinda weird machine I'm having :)

So...thanks again for your anwers.. 

btw... do you recommend I should switch to 64bit version?

---

### Post by waynefoutz on 2010-02-17
> **crestfallentoo said:**
> hey,
thank you both for your explanations 
so, I understand that I can't do much in Linux, that's no biggie, I'll resintall Windows with it's full software from HP and hope to find that option where I change the shared memory...
@benmoran
yeah, I know it's a pain but I'm used to do this with Windows, that's why I'm changing to Linux :) to get rid of reinstalling the OS at every 3 months or so... 
@waynefoutz
I haven't played any games in the past year or so (though I've tried Nexuiz and Alien Invation).. I rather have some extra RAM for the system than my graphics card... and yes... my system is a little different,...I don't have that option in BIOS, my father also has an HP and he does have the option in BIOS... kinda weird machine I'm having :)

So...thanks again for your anwers.. 

btw... do you recommend I should switch to 64bit version?

I'd go with the latest 32 bit version of Xubuntu. The Xfce environment is less intensive than Ubuntu's Gnome, You'll get better performance out of that little bit of RAM you got to work with. Since you aren't gaming with it, the open source drivers will work for you nicely. I don't see any advantage of going 64 bit.

---

