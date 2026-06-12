---
title: "Hp Dv9010 Laptop Freezing During Boot/in Console - Solved (hopefully)"
date: 2007-03-07
forum: Hardware &amp; Laptops
---

### Post by watson540 on 2007-03-07
OK. Man you guys I had so many problems since I got this laptop. My worst problems being that I couldnt even make it to the login prompt 80 percent of the time. Most of the time the box would freeze 2 seconds after grub kickstarts it.

I tried it all, noacpi acpi=off pci=biosirq irqpoll, any and all combinations, each with their own downfalls, and none worked - although some had a placebo effect.

Man I never want to give up on linux which is why i spent 3 hourse just rebooting, locking up, doing it again. I would never get a lock in X although while at a console anytinhg could freeze me. By now you're like wtf did he do?? What could it be?!

Well it was an accident, even the boxes that lock up have to look pretty too, so i set the line vga=791 in menu.1st to set up a nice 1024x768 resolution to look at while my box was locking up all the time and killing my hardware.

Friggin lo and behold guys. Ever since i used this option (by accident, never thought it would make a diff. in hard locks) I have not had a hard lock yet!, plus the console looks prettier too. I just wanted to throw this out there cause I know I'm not the only one experiencing hard locks on these laptops. It doesn't make much sense at all as to why it works or has any effect on lock ups.

I would LOVE to hear anyones flames/comments as to why this is effective/works or why you think it's just a placebo effect for me.

---

### Post by serag on 2007-03-07
I have the hp dv9010ca and i had to use noacpi acpi=off to do the inital install and to install the nvidia drivers.  Once i did all the updates and set up the system as i liked, i was able to remove that noacpi acpi=off option from grub and the system still boots up fine and i have access to all the features that were disabled before (battery, cpu throttling,etc)

---

### Post by watson540 on 2007-03-07
Whenever I used acpi=off the nvidia driver would complain  that the card was edge triggered( a consequence of the option), plus i think that option killed my broadcom 4311 also, so it wasnt an option for me :(. i have a crappy card though mines a dv9010us it has the geforce go 6150 i think..supposed to be 128 meg shard ram on the card..but it reports itself as being 256 shared

@serag - what is the resolution of your framebuffer (boot splash/console) , also what video card do you have?? i imagine yours is a step up from mine. I saw one like mine, same case and everything only better gpu and bigger hd for a few hundred more at circuit city...figures i find something better after i buy this.

---

### Post by serag on 2007-03-07
Mine is the same as yours, just the Canadian english version(AMD 64 X2 1.8, 120gig hd, 2 gig memory)  I have the nvidia 6150 Go, supposed to be 128, but reported at 256 also.  I have my resolution set at 1440x900_60, not sure what it is at boot splash.
I tried getting everything working using the 64 bit 6.10, but it wifi would never work, finally installed the 32 bit version and everything works great.

---

### Post by watson540 on 2007-03-07
Well maybe it is all a placebo effect for me. It almost leads me to believe that I got a batch of bad ram in my box. I did a memtest86 but only had enough patience to see it halfway through ...that was 30 minutes :) ... I wonder why it is that our cards report 256?? I was thinking maybe it DID actually have 128 onboard and then 128 shared. Makes sense but thats too much to ask for, heh.. Everything else on this notebook was a steal, i got it for 1220$ us. I just had to sacrifice with the video card, cause where else ya gonna get 2 gigs in a notebook for under 2 grand right? :) .. I dont game anyway but i'm sure it would handle anything on the shelves to date.

@serag - I Also got lightscribe going under edgy, took a lot of un-necessary work though :)

---

### Post by serag on 2007-03-07
in regards to the video card, i think that they might have mislabled it.
[http://shopping.hp.ca/cStoreCA/BaseDetails.asp?PType=58&ProductLineId=25&FamilyId=111&BaseId=3483&BEId=5&Lang=EN]("http://shopping.hp.ca/cStoreCA/BaseDetails.asp?PType=58&ProductLineId=25&FamilyId=111&BaseId=3483&BEId=5&Lang=EN")
That link is for the dv9210ca, which is identical to the 9010, but it has vista pre-installed, and the 6150 is listed at 288 megs

---

### Post by watson540 on 2007-03-07
Wow, thats some mistake! too bad they couldnt have mislabled a card with at least dedicated memory :)

---

### Post by watson540 on 2007-03-08
I have already instructed 2 seperate people in 2 sepeate threads to do the things i outlined here, they have reported that it also works for them! its something about these laptops and their resolution that makes them freeze. i hope people find this thread instead of posting new ones ...there's a good 4 of them in the past day with this problem

---

### Post by serag on 2007-03-08
see this thread if you want to get your webcam working
[http://ubuntuforums.org/showthread.php?t=373843](http://ubuntuforums.org/showthread.php?t=373843)

---

### Post by COJ@K on 2007-05-23
Hello. I also have the dv9010ca and I set up a triple boot with XP, Vista and Ubuntu 6.10. I installed Ubuntu with noacpi acpi=off, but then once I installed it I cant seem to get it to boot. Could anyone please help me out, and hopefully guide me in a little more detail since I am new to the whole concept of linux and still learning. 
Thanks. All help greatly appreciated! :D

---

### Post by COJ@K on 2007-05-24
Hmmm... @SERAG. Do you think you could guide me through what you did to set up your laptop?
Thanks.

---

