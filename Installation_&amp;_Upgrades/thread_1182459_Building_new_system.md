---
title: "Building new system"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by matamoscas on 2009-06-09
As the title says, I am building a new desktop to replace my laptop.

I am happy not to buy the "LATEST and GREATEST" hardware, as I already know from past experience -- buying what was HOT six months ago, can save you anywhere from 25-50%, depending on trends/market.

I have decided on AMD for many reasons...

Where I am having a hard time making a decision is where to draw the line.  I am further aware from back in the day, older hardware worked better on linux than piping brand new, bleeding edge hardware.  Is this still the case?

I could go Phenom II X4 quad-core (I mean that sounds nice), and assuming I don't have install problems, that would be nice =)  But, should I just get slightly older hardware, from like last year?

Thanks in advance...

---

### Post by H2SO_four on 2009-06-09
my mobo is not recommended, unless you like to endlessly try to get HDMI and optical audio working correctly.  And random screen freezes.  My experience may not be everyones.

---

### Post by sendblink23 on 2009-06-09
I'm pretty sure that would run alright

All you need is a Good Graphics Card, Wireless, Ethernet, Sound Card (that you read around that works flawlessly in Linux *make Sure Latest, so they can work on the Motherboard to that Processor*)

Any DVD RW/DL, Mouse, Keyboard would work out of the box

You can get as many ram as you want.. that Processor is already 64bits it can handle anything

---

### Post by synapsys on 2009-06-09
I see no problem with the latest processor..... a 64 bit arch is a 64 bit arch. I am currently running an asus p5Q-e with intel core 2 quad processor with absolutely no problems whatsoever.

---

### Post by matamoscas on 2009-06-09
> **sendblink23 said:**
> I'm pretty sure that would run alright

All you need is a Good Graphics Card, Wireless, Ethernet, Sound Card (that you read around that works flawlessly in Linux *make Sure Latest, so they can work on the Motherboard to that Processor*)

Any DVD RW/DL, Mouse, Keyboard would work out of the box

You can get as many ram as you want.. that Processor is already 64bits it can handle anything

Interesting..

I was planning on using the onboard sound, so I need to confirm that it works in linux.  "good graphic card" is still kind of a work in progress. =) I was thinking of nabbing a cheap old (and quiet) ati radeon 3850, since it was rather cheap, little older dual dvi card.  I am not sure if I should go ATI or NVidia =(  I am still trying to figure that out. I am leaning towards ATI -- for the sole reason that my only experience so far is with them -- and while problematic to say the least, at least drivers exist.

I was gonna also the onboard LAN. My house is already wired - my wife is paranoid of "electro smog" so I have to turn off the wifi when she is home =)

---

### Post by sendblink23 on 2009-06-09
can you post the name of the MOBO? 

So that I can search around n Google to try to help you out.. to get things (hardware) that work for Linux especially at least out-of-the-box so you don't have any hassles with it upon installation

Since its obvious you will be doing a Backbone Computer

---

### Post by matamoscas on 2009-06-09
It's a Gigabyte GA-MA790FXT-UD5P
The built-in audio chip is a Realtec ALC889A codec. I don't really care about all the fancy bells and whistles features on the audio, I just want it to have one working audio (stereo also good) line out. =)

I don't like to annoy my neighbors. =)

Ok, check that..

I think I am leaning towards the Gigabyte GA-MA770T-UD3P.  It's an earlier board, with the chief difference being that this one only has one 16x PCIe slot, whereas the other one has two. As, I am pretty much retired from hardcore gaming, I will likely never install TWO legit graphics card. I plan to get one anyway, in the off chance I want to try a new game, every now and then. But, it is mostly a place-holder card.  Nvidia or ATi??

---

### Post by bp0 on 2009-08-20
> **matamoscas said:**
> I think I am leaning towards the Gigabyte GA-MA770T-UD3P.

The Gigabyte GA-MA770T-UD3P has some problems. 
The onboard NIC is not well supported in Ubuntu. It is a Realtek chip RTL8168c/8111c which is just barely supported in Linux. In its current state you can not enable any offloading except rx-checksum, and you'll get some weird latency problems. Also, the link will go up and back down 3 or 4 times when the computer first starts.
The onboard audio is an AMD/ATI chip that implements Intel HD-Audio "Azalia". The problem here is that it is very very soft, and only supports 16-bit output. Also, there will often be crackling when two applications try and play music.
The other really annoying problem with this motherboard is that when you "Shutdown" in ubuntu, the computer turns off, but when you turn it on again it will power-up but not boot. So after you turn it on, you must hold the button for ~4 seconds to turn it off, then wait a bit, then turn it on again. The problem doesn't happen if you shutdown from Windows.
These are my experiences anyway, and if it is somehow my problem only then I would be glad to read your solutions.

---

