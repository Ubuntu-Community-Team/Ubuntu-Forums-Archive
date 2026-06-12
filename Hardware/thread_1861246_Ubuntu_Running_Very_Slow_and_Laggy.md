---
title: "Ubuntu Running Very Slow and Laggy"
date: 2011-10-15
forum: Hardware
---

### Post by nepalinux on 2011-10-15
Hi,
I've this laptop(HP DV6) with good specs having i7 core @ 1.6GHz, 4 GB RAM, 650 HDD and 1 GB NVIDIA GEFORCE(With CUDA) graphics driver. I was using ubuntu 10.10 and I used to experience some lags and system hang-up frequently but not much.

Recently, ubuntu 10.10 hanged a lot. It took around half minutes to come to grub menu at startup and after then took another 2/3 minutes to reach to login screen and another 5 minutes to reach the home screen of the user. Then the menu used to freeze and mouse also freezed frequently. The programs would start very slowly and would hang frequently. For example, Firefox would take around 30 secs to load. Then it would hang in each new events such as clicking on the address bar, hovering in the menu, clicking on any buttons, right clicks, etc. 

I tried some of the suggestions given in the forum regarding ubuntu 10.10. I installed the 2.36 kernel and nothing improved. I checked the CPU usages and RAM usages with top and system monitor and everything was fine. I checked Hard Disk status with GSmartControl and everything was fine.

Frustrated, I upgraded my ubuntu to 11.04 and still the same problem persists. I feel like throwing away this machine but still I've some hope from this forum. I can't live like this with this laptop. Please share your ideas or experiences on what could have gone wrong. I would like to know if there is something I can do except fresh install. Fresh install would be my last bet however right now I don't have enough hard disk space to backup all my files in linux partition and I don't have any external storage devices.

Regards
Nepalinux

---

### Post by diasf on 2011-10-15
How are the smart values of your HD?

That happened to me, the windows XP would take half an hour to boot.... my hd was almost dead... And to take that long to load grub, well, your disk is probably dying as well...

Try booting from a liveCD.... that way you can boot up the whole system without really using the hd... if is still slow, it isn't the hd, but if it is fast as should, then you have your culprit.

---

### Post by nepalinux on 2011-10-15
> **diasf said:**
> How are the smart values of your HD?

That happened to me, the windows XP would take half an hour to boot.... my hd was almost dead... And to take that long to load grub, well, your disk is probably dying as well...

Try booting from a liveCD.... that way you can boot up the whole system without really using the hd... if is still slow, it isn't the hd, but if it is fast as should, then you have your culprit.
Hi thanks for your reply. When I did smart test, overall health self-assessment test was labelled as PASSED but I've found that the raw value of **Current Pending Sector Count** is 761. I think this is the reason for the failure. Is there any way to decrease this count? Maybe hdd nulling or whatever?

---

### Post by diasf on 2011-10-16
Some smart values are not that relevant... and some hd problems are not detected by smart. For instance, mine passed the test as well, but it was dead either way. Try the liveCD

---

### Post by nepalinux on 2011-10-16
> **diasf said:**
> Some smart values are not that relevant... and some hd problems are not detected by smart. For instance, mine passed the test as well, but it was dead either way. Try the liveCD
LiveCD is working perfectly so I am now sure its the HDD issue. Anyone has succeeded to revert back the bad sector counts? Or should I buy the new HDD?

---

### Post by diasf on 2011-10-16
You can try a low level format, using a software the driver's manufacturer provides (at least was that way a couple years ago), but, personally, I wouldn't trust the drive again.... (never let that drive be the only copy of important stuff, etc)

---

### Post by nepalinux on 2011-10-16
> **diasf said:**
> You can try a low level format, using a software the driver's manufacturer provides (at least was that way a couple years ago), but, personally, I wouldn't trust the drive again.... (never let that drive be the only copy of important stuff, etc)
Yeah I understood your point and its only copy of all my important stuffs. I bought that laptop by saving for long time. I don't have money to buy a new laptop HDD right now. Can you recommend me a decent laptop hard drive to keep it in my future-buy list?

---

### Post by diasf on 2011-10-16
Not really..... tbh I think it's more luck of the draw than anything.... so just grab the one you can, when you can...

(I said luck of the draw because for every brand that ppl complain about you can find a lot of ppl saying good things and vice-versa... so it's just to pray that your specifically will work :P)

---

### Post by diasf on 2011-10-16
btw, isn't still on warranty? (or garanty, forgot the english term for that... when the manufacturer swap out malfunctioning stuff)

---

### Post by snowpine on 2011-10-16
Just a suggestion, try a Live CD that loads completely into RAM such as Puppy Linux or SliTaz. This will completely remove the hard drive from the equation.

---

### Post by nepalinux on 2011-10-16
> **diasf said:**
> btw, isn't still on warranty? (or garanty, forgot the english term for that... when the manufacturer swap out malfunctioning stuff)
The warranty date passed two months ago so out of luck in getting replacement. I wish I had this disk failure thing two months ago.

> **snowpine said:**
> Just a suggestion, try a Live CD that loads completely into RAM such as Puppy Linux or SliTaz. This will completely remove the hard drive from the equation.
I'm using live CD right now however I frequently need to open files from hard drives.

---

### Post by madjr on 2011-10-16
HDDs can degrade for many reasons, specially force shutdown the computer off using the off/on button in the laptop by pressing it a few seconds straight.

---

### Post by nepalinux on 2011-10-16
> **madjr said:**
> HDDs can degrade for many reasons, specially force shutdown the computer off using the off/on button in the laptop by pressing it a few seconds straight.
Well this is not the reason for degradation of my laptop's hdd. Never done forced shutdown.

---

### Post by madjr on 2011-10-16
> **nepalinux said:**
> Well this is not the reason for degradation of my laptop's hdd. Never done forced shutdown.

Ok good, then it seems the disk was a bit faulty when you got it, too bad the warranty is already over... ;/

not sure if a technician can do anything about it, but would be cheaper anyway to just get a new one when you can.

At least for now is nice that linux gives you an option to use it from usb or memory without a disk in the meantime for an emergency situations like this.

---

