---
title: "Weird nVIDIA driver troubles"
date: 2016-01-10
forum: Hardware
---

### Post by blade4 on 2016-01-10
Hi all, this one's more of a discussion question. 

I've been trying to see if I can completely disable my nVIDIA card on my MSI GT-70 laptop ( card make : GTX 670M ). The laptop has a handy feature in that the power button backlight changes color depending on which card is being used ( white for integrated intel card, orange for the nVIDIA card ) 
I'm running wiley at the moment and have installed the latest intel graphics drivers for linux. I had the idea that if I removed the nouveau driver and kept the intel one, ubuntu would default to the intel driver ( I did not have any proprietary nVIDIA driver at this point in time ) 

My ubuntu setup was already using the intel driver ( white backlight , grep and lspci -v all confirmed this ) so I simply did "apt-get purge xserver-xorg-video-nvidia" and rebooted. 

Upon reboot I noticed that the power button backlight had changed to - you guessed it - orange. Ubuntu was apparently using the discrete card even though I had removed its drivers. I did some quick checks with grep , lspci and some additional stuff I saw on google ( this was about a week ago so I don't remember everything I did ). Turns out, BOTH of my cards were being used. 

I fixed it by reinstalling nouveau but it does bring up an interesting question -  why would the nVIDIA card be used if its driver was unavailable ? 

I tried googling this up but couldn't find much. I guess people don't usually ask to disable a discrete graphics card on linux . 

Thoughts ?

---

