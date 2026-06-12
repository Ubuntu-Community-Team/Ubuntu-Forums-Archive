---
title: "How do I tell which video card I have?"
date: 2008-08-25
forum: General Help
---

### Post by kline on 2008-08-25
Hey Guys,

How do I tell what make of video card I have in my system?  I've checked in /etc/X11, but haven't found it?  My server is an AMD 2.8GHz, 1GB RAM, 160G drive, with an unknown audio [ probably built in ] and an unknown video.
I am running 6.06 "LTS" and waiting for the next LTS ... or if I can upgrade from whatever is current, I'll just buy that and upgrade.   I believe my default Desktop is Gnome, if there is some "system info" dialog.

I am buying a used 3.0MHz ThinkPad with 160G drive, 2G RAM and intend to drop in something that Just-Works {tm}--Ubuntu  For right *now*, I need help finding out the current video card to see if it will support a WideScreen LCD.

sign me, "clueless"

thannks in advance!

---

### Post by Sycron on 2008-08-25
> 3.0MHz ThinkPad
lol ?

Now it's 8.04 hardy Heron LTS.

---

### Post by sisco311 on 2008-08-25
try:
```
sudo lshw -C video
```

---

### Post by kline on 2008-08-25
> **sisco311 said:**
> try:
```
sudo lshw -C video
```

Thanks!   I was a hardware major --- BUT back in ye olden Vax days.  Can you tell me what this means?

  *-display
       description: VGA compatible controller
       product: 661/741/760/761 PCI/AGP VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@01:00.0
       version: 00
       size: 128MB
       width: 32 bits
       clock: 66MHz
       capabilities: vga cap_list
       resources: iomemory:d8000000-dfffffff iomemory:e1000000-e101ffff ioport:d000-d07f irq:5
pts/3 12:48 <ethos> [5023] 

It blows me away that I've got 128Megs of video ram --- can that be correct?  I know nothing about these new flat-panel displays, like in particular, the ones that are high the new WIDE High-Def TV sets.  Is there any URL that can tell me if my SiS would even drive a "wide screen" LCD.  Currently, I'm doing 1280x1024 on a Hitachi CRT.

Suggestions? best guesses?

---

### Post by kline on 2008-08-25
> **Sycron said:**
> lol ?

Now it's 8.04 hardy Heron LTS.

Why the "LOL"?  My un-bought ThinkPad or the fact that I'm stuck with 8.06!
I can't remember the name, but the number? much easier.

BTW, this 6.06 haven't crashed once.  It had upgraded flawlessly since '06; push-button.  So kudos to all the ubuntu-hackers who make this work.

---

### Post by coffeecat on 2008-08-25
> **kline said:**
> 
       product: 661/741/760/761 PCI/AGP VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]

From what I've read, you're lucky to be getting a 1280x1024 display with a SiS chipset. SiS seems to be the video manufacturer with the least interest in Linux.

> **kline said:**
>  Is there any URL that can tell me if my SiS would even drive a "wide screen" LCD. Currently, I'm doing 1280x1024 on a Hitachi CRT.

It might be worth searching these forums or using [http://www.google.com/linux]("http://google.com/linux") to search for your video chipset but from what I've read you won't get widescreen resolution with the SiS driver.

> **kline said:**
> It blows me away that I've got 128Megs of video ram --- can that be correct?

Yes, but if that's onboard video it will be using that much of your system RAM.

> **kline said:**
> Why the "LOL"?  My un-bought ThinkPad or the fact that I'm stuck with 8.06!

Or 6.06 even? :wink: I think the "LOL" was about your 3.0MHz Thinkpad. That's a mighty laid-back Thinkpad. Or did you mean 3.0GHz?

---

### Post by kline on 2008-08-25
> **coffeecat said:**
> From what I've read, you're lucky to be getting a 1280x1024 display with a SiS chipset. SiS seems to be the video manufacturer with the least interest in Linux.



It might be worth searching these forums or using [http://www.google.com/linux]("http://google.com/linux") to search for your video chipset but from what I've read you won't get widescreen resolution with the SiS driver.

I'll ask around.  So long as something reasonable works until I can give away this bare-bones system, I'll be happy.   But things worked from day-one with this chipset.  I did try 1600x1200; don't remember if it worked.  

It's worth noting that these widescreen displays are new; or at least I didn't seem then a year or 18 months ago.




Yes, but if that's onboard video it will be using that much of your system RAM.



Or 6.06 even? :wink: I think the "LOL" was about your 3.0MHz Thinkpad. That's a mighty laid-back Thinkpad. Or did you mean 3.0GHz?

LOLOL!  Yeah, got to agree.  My first CP/M was a 4MHz 8085 (IIRC).  Yes, I did indeed mean 3Ghz, not 3Mhz!  thanks much.

---

