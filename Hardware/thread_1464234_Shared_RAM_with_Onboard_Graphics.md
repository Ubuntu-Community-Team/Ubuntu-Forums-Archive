---
title: "Shared RAM with Onboard Graphics"
date: 2010-04-27
forum: Hardware
---

### Post by Greg Xix on 2010-04-27
I have a newer but cheaper laptop that came with 2gb of ram. I recently upgraded to 4gb(gotta love awesome deals on craigslist :KS).

I reinstalled to 64-bit so Linux could see all 4gb, but I was wondering if I can share some of the new muscles with the wimpy Intel integrated graphics. Perhaps 300-500MB.


Thanks.

---

### Post by carl4926 on 2010-04-28
If that option is available it will be in your BIOS settings.

---

### Post by Greg Xix on 2010-04-28
Unfortunately, my cheap Laptop came with a cheap and very limited BIOS, that doesn't have that option.

---

### Post by carl4926 on 2010-04-28
Then the answer is No. You can't do what you asked:(

---

### Post by Greg Xix on 2010-04-28
> **carl4926 said:**
> Then the answer is No. You can't do what you asked:(

Darn, I thought there might have been some sort of paging file that could be tweaked. I will contact my computer's manufacturer about the BIOS.

I have noticed the graphics are a bit better. So I was wondering if that by upgrading from 2gb to 4gb the laptop's hardware automatically allocates more 'Shared Memory'...perhaps?

---

### Post by cascade9 on 2010-04-28
Possibly- what model laptop is it?

---

### Post by Greg Xix on 2010-04-28
> **cascade9 said:**
> Possibly- what model laptop is it?


Compaq Presario: CQ50-139wm

Its that model that was specifically made for WalMart and released before Christmas 2008 for $299. I dont think they make/sell them anymore. It came with Vista installed <-- = Fail :(.....It ran slow and like garbage.

I exterminated Vista from it and installed Ubuntu-only on it, of course now it runs smooth except for the graphics. But like I said, it *might* have automatically allocated some more when I upgraded from 2 to 4gb because it looks slightly better, but I would love to customize the "Shared Memory" if possible.

---

### Post by cascade9 on 2010-04-28
> **Greg Xix said:**
> Compaq Presario: CQ50-139wm

Its that model that was specifically made for WalMart and released before Christmas 2008 for $299. I dont think they make/sell them anymore. It came with Vista installed <-- = Fail :(.....It ran slow and like garbage.

I exterminated Vista from it and installed Ubuntu-only on it, of course now it runs smooth except for the graphics. But like I said, it *might* have automatically allocated some more when I upgraded from 2 to 4gb because it looks slightly better, but I would love to customize the "Shared Memory" if possible.

Product specs here- 

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01600619&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01600619&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN)

From what I know about the [FONT=Arial]4500MHD, its possible for manufacturers to lock the max shared memory, or it can allocate memroy based on the amount of RAM in the system. With compaq saying 'up to' 765MB I would guess that it would allocate more if you have more memory. 

BTW, do you see the full 4GB on that machine? It would be interesting to know, if only because most of the chipsets with that video have a 4GB+ limit, not the 3GB comapq has listed. If you c an, I would bet that comapq has said '3GB' to avoid getting the typical 'but my machine has 4GB, why can I only see 3' questions from win32 users. Of course, you wont see 4GB (shared video) but anything over 3 would mean you are getting the full 4GB, minus shared video (and you could prossibly extrapolate how much RAM is allocated with 2GB and 4GB by checking with the right amount of RAM installed). [/FONT]

---

### Post by Greg Xix on 2010-04-28
> **cascade9 said:**
> Product specs here- 

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01600619&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01600619&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN)

From what I know about the [FONT=Arial]4500MHD, its possible for manufacturers to lock the max shared memory, or it can allocate memroy based on the amount of RAM in the system. With compaq saying 'up to' 765MB I would guess that it would allocate more if you have more memory. 

BTW, do you see the full 4GB on that machine? It would be interesting to know, if only because most of the chipsets with that video have a 4GB+ limit, not the 3GB comapq has listed. If you c an, I would bet that comapq has said '3GB' to avoid getting the typical 'but my machine has 4GB, why can I only see 3' questions from win32 users. Of course, you wont see 4GB (shared video) but anything over 3 would mean you are getting the full 4GB, minus shared video (and you could prossibly extrapolate how much RAM is allocated with 2GB and 4GB by checking with the right amount of RAM installed). [/FONT]


Actually I have a guide for my laptop, a larger PDF file that says the laptop is upgradeable to 4gb(2 x 2gb), which is exactly what I did. The BIOS can see all 4gb. And I did have to upgrade from 32-bit to 64-bit linux for the OS to see it.

---

### Post by cascade9 on 2010-04-29
> **Greg Xix said:**
> Actually I have a guide for my laptop, a larger PDF file that says the laptop is upgradeable to 4gb(2 x 2gb), which is exactly what I did. The BIOS can see all 4gb. And I did have to upgrade from 32-bit to 64-bit linux for the OS to see it.

Interesting...just one silly question, do you know if you got that PDF from the HP1 site, or from Compaq? 

(only asking because I've seen similar 'misakes' before and it would make my life eaiser as an upgrader).

---

### Post by Greg Xix on 2010-04-29
> **cascade9 said:**
> Interesting...just one silly question, do you know if you got that PDF from the HP1 site, or from Compaq? 

(only asking because I've seen similar 'misakes' before and it would make my life eaiser as an upgrader).



When you go to compaq.com and input the model number, in my case: cq50-139wm, it redirects you to the HP1 site. Going to HP.com and doing the same thing takes you to the same page.

[U]
[http://h10025.www1.hp.com/ewfrf/wc/manualCategory?lc=en&dlc=en&cc=us&lang=en&os=2093&product=3804159&](http://h10025.www1.hp.com/ewfrf/wc/manualCategory?lc=en&dlc=en&cc=us&lang=en&os=2093&product=3804159&)[/U]


I downloaded the 5th PDF from the bottom. Since that is the "Maintenance and Service Guide"

---

### Post by cascade9 on 2010-04-30
Heh, so its currently up? HP/Compaq really shouldnt let mistaeks like that past (unless I'm correct in my guess that the '3GB' they put on the page I linked to was to stop 32bit windows users from putting in 4GB and then asking 'were is my RAM'? It would make more sense to just put the real limit and then put '3GB for 32bit windows IMO but obviously they havent.) 

Interesting, filed for future use. Thanks ;)

---

