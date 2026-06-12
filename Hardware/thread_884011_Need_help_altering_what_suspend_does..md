---
title: "Need help altering what suspend does."
date: 2008-08-08
forum: Hardware
---

### Post by etchnstketch on 2008-08-08
*Solution found* I am planning to make a HOW TO with a compilation of all the fixes I have had to do.
Please kill thread in the mean time. 

To start, I am a n00b. I have no idea what I am doing.

After spending forever on these forums trying to get my laptop to fully function with Ubuntu (7.10 and now 8.04), I have come very close, right now I am battling the suspend function.

I am on a Toshiba A215-S7422.
I noticed that my laptop would go into suspend mode, but not wake up successfully. The problem is with the wireless card, (which I have beat into submission finally!) In order for me to get the suspend to work properly I have to turn off the wireless drivers and then put the laptop to suspend, and everything works fine. After it wakes, I can simply turn on the wireless drivers again and I am back to normal.

QUESTION:
How do I customize my suspend function to run some commands before it does its thing, and to run some more commands after it wakes?
Specifically, I need to call: ```
sudo /wifi/wlan0down 
``` before it suspends and ```
sudo /wifi/wlan0up 
``` after it wakes.
I have lots of faith in Ubuntu being fully customizable, but maybe it is impossible? Any help will be appreciated!

Thanks!

---

