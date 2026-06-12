---
title: "Xfce -- you guessed it -- crashed (using LiveCD)"
date: 2010-01-11
forum: Hardware
---

### Post by mastablasta on 2010-01-11
I tried to Live Xubuntu 9.10 CD on an old laptop with 1.2Ghz processor and 256 MB RAM. I wanted to test it before installing it. The point is that current WinXP work too slow on this notebook, so i was hoping Xubuntu would provide a faster solution. SInce the notebook is used only for internet chatting, browsing and creating some HTML pages. occasional movie is also being watched on it. 
 
I read that Xubuntu needs minimum 192MB to run a live CD.
The CD ran ok (although slow since it's from CD). And once the system was loaded i tried some programmes which opened with about the same speed as the one in current WinXP config (not much of an improvement, but i was hoping this would be faster later). But as soon as i tried to exit the Xubuntu instead of getting the buttons for shutdown etc. the Xfce crashed (with a crash message). Menus dissapeared. I can still exit the computer by right-clicking the desktop and choosing the log out. what i don't understand is why the crash occured? I also happened on second occasion while i was using Firefox3.5. First the applicationsbutton dissapeared, then the firefox icon and finally it crashed (all menues & taskbar dissapeared) although i am still in the graphical interface. 
 
Funny though i can switch to console (i think this is how it is called - ctrl+alt+F1) and back just fine. also there are no error messages recorder there.
 
I read about bugs on this issue, but they all have older date. Am i to asume this is an old bug that was never solved? what would cause the xfce to crash?
 
Theer was also a bunch of error messages upon loading but as i read this bug is cause by bad CD burn (which is not the case here as i treid it on another ocmpšuter and it loaded fine).
 
What do i loose if i would use alternate CD? if it's just graphical interface it would be ok as long as the whole thing works faster...

---

### Post by kerry_s on 2010-01-11
256mb ram and you want speed? upgrade your ram.

the alternate is just a text mode installer, you'll get the same gui.

sounds to me you may have some hardware issues going on though.

---

### Post by snowpine on 2010-01-11
Hi mastablasta,
I would recommend:

1) Check the CD for errors (this is one of the options on the first screen when you boot from the Live CD)
2) Get more RAM if possible

It is normal for the Live CD to be slow (it will be faster once you install it to the hard drive). It is hard to diagnose the crash without more information, but one possibility is that you simply ran out of ram (especially if you don't have a swap partition). I recommend installing (with a proper swap partition and more ram if possible) and applying all available updates (maybe the crash is due to a bug that's been fixed) before you reach a final verdict on Xubuntu.

---

### Post by mastablasta on 2010-01-11
unfortunatelly i got this notebook and found out that more ram is not really a possibility. well actually the most i could increase (if i could find it) would be another 128MB ram. And to think this notebook has a sticker on it saying WinXP ready :D. kind of like that one 640kB RAM should be enough for everyone statement. 
 
Anyweay the motherboard can't handle more ram. Wish i could just stick 1GB ram inside then i probably wouldn't even consider Xubuntu Linux. I went with it because it is similar to Ubuntu only lighter on the system. I was hoping it would speed up the computer since it needs less ram (WinXP no SP work OK with 256, but with any SP you need at least 512MB ram to work it normally). Not to mentione the system increase in disk size subtantially, even if i deleted all unnecessary files. So i was hoping Linux could step in for these basic tasks (chatting, emails and HTM writing in text or WYSIWIG editor). besides there are no antivirus that need to run in linux or heavy duty protective firewalls...
 
Well unfortunatelly Xfce just crashed without giving any specific reasons. That's an odd way to go by the way. run out of ram and pop goes the GUI... 
 
I will try the CD on another (faster computer) to see if there are any errors on it. Then i plan to try a duual boot instalation. This computer also only has 20 GB HDD, so i need to make a linux partition - about 8 gb should do (since the requirements for Xubuntu means i tneeds 2 gb for system and then about 1GB for swap and the rest for data.

---

### Post by snowpine on 2010-01-11
Please re-read my previous post carefully. The "Check CD for errors" feature will verify the integrity of your CD, and I also recommend applying all updates and bug fixes. 

There are hundreds of Linux distributions (or "distros"). Xubuntu is not particularly lightweight, in fact I would say its system requirements are a little bit higher than Windows XP. You might consider a distro like Puppy that's specifically designed for low-RAM computers. Good luck!

---

### Post by arubislander on 2010-01-11
Whatever distro you decide on (Crunchbang is another possibility if you want to stay in the Ubuntu fold, but even on that 256 MB might be asking too much of too little) you shouldn't waste 1 GB on a swap partition if you only have 256 MB RAM... I'd settle at 390 MB, so you have enough for hibernation even if you do decide to upgrade your RAM.

BTW. I had an ancient HP laptop with 256 MB.. I googled around and found it could hold up to 512 MB... Had to do some more googling to find the type of memory it could use, and then some to find a supplier, but I succeeded, so I guess so could you.

---

### Post by mastablasta on 2010-01-12
Well i already googled for RAM for this one. Unfortunatelly it can only hold 384 MB. 
 
I already invested in a new batery and a PCIMCIA WiFi card. Both investments were sort of failed investments. Batery helped me a few times, but WiFi card... well i found out i can't log on to Uni network and i don't use WiFI at home anyway.
 
On top of this the computer has overheating problems (it's one of those "hot" AMD porcessors), so it tends to shut down or crash & restart even in WinXP. The computer got so hot that it melted small legs under it (apparently a couple of times). So i just plan to use it as long as it work and more like a netbook or the kind of thing you can take along and not worry if it gets stolen :D. 
 
Better buy a new computer (i already got an eye for Ubuntu equiped Dell or HP that can handle Ubuntu well out of the box) after this one get's completelly worn out than upgrade. Though the LCD screen is still good and i like the shape of it.
 
Maybe i will try Damn Small Linux. That one really needs little resources.... Or Puppy.

---

### Post by cascade9 on 2010-01-12
If its got hot enough to melt things, its probably got hot enough to cause all sorts of nasty problems inside the laptop case. You've probably got a hardware issue, and thats causing your crashing,etc. 

BTW, if you havent already, I'd try blowing out any vents (with a 'can of air') at least. If it was me I'd pull off every cover on the laptop and clean out everything you can.

---

### Post by mastablasta on 2010-01-12
Already on "to do list". I plan to get a compressed air can. i heard it might help.
 
I think also the legs plastic was bed. Computer does get hot but never really, really hot. Though it does overheat in summer. It's just an old computer i got for free so i can't expect a lot.
 
At least i did some work in library when i had to.

---

### Post by mastablasta on 2010-02-02
Tried again LiveCD of Xubuntu and Ubuntu. Both GUI crash after a while. Ubuntu crahsed (gtk- crashed), but until then it was working surprisingly fast. i would estimate even faster than Xubuntu. 
 
Haven't tried Kubuntu yet. I tried Mint 8, but that one requires more ram and the loading takes too long. So i shut it down soon after.
 
Anyway the linux can be shut down normaly either from terminal or via right cliclin on desktop (cause it doesn't totlally crahs just some menues disspear).
 
Liek some postres above i too speculated this is due to overheating (the notebook where the DVD drive is does get quite hot). However when i showed it to my brohter he said the same thing happneed to him (and he has a desktop with a bit older Radeon, ADM processor, 2 GB ram...). He couldn't pinpoint the source of the problem and didn't even bother since he was just testing, but he said he never saw it before (he uses 9.04 at work). 
 
I also tried LiveCD DSL and Puppy, both worked beautifully, but i think i need more from the computer than they could offer. 
 
I will still try Kubuntu if the issue is the same i will just wait until next release comes out and hopefully will be more stable. If i can find a way to backup the defaul system restore files (which take almost 5 GB on 20 GB disk), i will try to install Ubuntu on it with dual boot to WinXP. Only i doubt this will happen since the notebook only has DVD rom :o.

---

