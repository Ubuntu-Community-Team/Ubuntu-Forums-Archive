---
title: "Problems, video and playback on 4K monitor and R9 R270 AMD. Ubuntu 14.04"
date: 2015-04-28
forum: Hardware
---

### Post by pblackstock on 2015-04-28
For a number of years I have happily used Ubuntu. However,I am having  all sorts of problems now since I upgraded my video card and monitor. My  monitor is a Benq 4k monitor, but I decided to upgrade my video card to  a AMD R9 270. I have installed the latest drivers from AMD, fglrx. This  is when my problems started as follows: 
1) I can no longer play flash in firefox, the Adobe Flash plugin keeps  crashing. 
2) Playing Youtube videos at full screen is like watching a slideshow,  really slow, it seems like there is no hardware acceleration. Flash or  HTML5 both are slow. 
3) I tried switching to Chrome as a workaround for the flash issue,  which worked fine at the start, but now Chrome is unusable as all it  does its keep flickering on my desktop when I start it up.  
I guess firstly, is this all fixable? Or is a combination of 4k, AMD etc unusable on Ubuntu? Any help would be greatly appreciated. Thanks.

---

### Post by QIII on 2015-04-28
Hello?

Which point release of 14.04 are you using?

Do you have the proprietary graphics driver installed?

What are the rest of your hardware specs?

---

### Post by pblackstock on 2015-04-28
Thanks for responding.

I am using 14.04 with all the latest updates, at least that is what its telling me.

Yes the l Proprietary AMD driver is installed and shows active in the Additional Drivers application.

I am running with  
AMD FX(tm)-8350 Eight-Core Processor × 8, 
Asus M5A99X EVO Rev2 990X AM3+
Noctua NH-L12 LP CPU Cooler
2x4 VENG LP CML8GX3M2A1866C9B
MB082SP 2.5/3.5 SSD Bracket
120G KTC V300S37A/ 120G SSD

If you need anything else, just let me know!

---

### Post by pblackstock on 2015-04-29
Come on , has anyone got any ideas?
I tried forcing Firefox to use Hardware Acceleration last night, what a mistake, Firefox was so glitchy graphically speaking just like Chrome stated above. The only thing I can surmise here is that Hardware Acceleration has serious problems for me at the moment and software driven video is too slow, I can't win!!!

I am being prompted to upgrade to 14.10, am I likely to see any improvement?

Help please!?!? :(

---

### Post by QIII on 2015-04-30
I run 14.04.2 (Kubuntu with an Ubuntu dual boot) with the Hardware Enablement Stack and the fglrx driver from the trusty-proposed repo.  (There is a bug in the installer for 14.04.2 which is committed in trusty-proposed but has not yet hit trusty main.)

My primary machine's hardware:

AMD FX-8350
AMD R9 290X
Gigabyte GA-990FXA-UD3
16GB
Noctual NH-D14
Samsung Evo 840 SSD
500GB mechanical
Silverstone Strider ST1500 PSU
3 x 1920x1080 monitors

So, similar except for the monitor.

I don't have any of the same issues.

So...

Take a look at the ATI driver wiki in my signature.  I added a section titled "4. Enabling Video Hardware Acceleration"  See if that helps.

I would certainly think your GPU would work with a 4k monitor, so I'm not leaning to that as the issue at this point.

I recommend against upgrading to 14.10 since that goes EOL in July and you'd just have to upgrae to 15.04 then.  That would take you out of the LTS rotation -- but that would be OK if you are not worried about uprading every six months.  In any case, I don't think the release is the issue.

---

