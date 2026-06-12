---
title: "Synaptics Touchpad on Vaio - not working in 14.04"
date: 2014-04-24
forum: Hardware
---

### Post by Mark_Edwards on 2014-04-24
Hi all,

I'm new to Linux. I tried installing Linux Mint 16 x64 last week on my 4 year old Sony Vaio PCG-3C1M, but the touchpad didn't work properly. Symptoms are the touchpad was almost non responsive, the buttons intermittently worked, and the touchpad itself kept doing tap to click actions by itself, so keeps clicking links and closing things, and occasionally jumping to different locations on the screen when i don't want it to. I tested with a USB external mouse and that works fine. I posted on the Mint forums, but didn't get any responses other than a suggestion to use a mouse as a workaround, and wait for the next version of Mint based on Ubuntu 14.04. So i decided I would just try Ubuntu 14.04 instead, but guess what, I have exactly the same problem.

I can confirm it worked perfectly on Windows 7 immediately prior to installing Linux, so it isn't a hardware problem. As i'm fairly new to Linux i'm not sure how to troubleshoot this. I ran xinput -list which told me i have a "SynPS/2 Synaptics TouchPad" I also found a thread (with a different issue) about the Synaptics touchpad which said to run 

sudo apt-get update
sudo apt-get install synaptics

So i tried this. The latter wasn't found, but the output suggested to run sudo apt-get install tpconfig instead, which i did. But this hasn't fixed the problem either. I'm thinking this is a driver problem, but there are no drivers for Linux on the Sony site for this model so not sure how to go about fixing it or where to obtain correct drivers, assuming this is what the problem is. I'd be greatful for some guidance on how to fix this?

TIA

---

### Post by Mark_Edwards on 2014-04-24
Update. I was working ok with the mouse for about half an hour, then lost all use of the left and right buttons. Touchpad buttons didn't work either, but the cursor was still working on both touchpad and mouse. Waited a good 5 minutes to see if the button control came back but nothing. Unplugging the mouse from the USB port and reinserting into the same port and also a different port didn't fix either. I had to press the power button to force a shutdown in the end, as i had no control of the laptop.

xinput -list shows the mouse as a "Microsoft Microsoft Basic Optical Mouse". Can't imagine its the fault of MS for once ;)

Any help greatfully received?

---

