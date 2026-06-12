---
title: "Bluetooth problem RESOLVED"
date: 2008-01-17
forum: Hardware &amp; Laptops
---

### Post by John Jason Jordan on 2008-01-17
I have a Thinkpad T61 which comes with bluetooth built in. I installed Gutsy x86_64 right after taking the computer out of the box, wiping out Windows XP Pro that was already installed. Gutsy happily found and configured the bluetooth.

After a few weeks I bought a Logitech V270 bluetooth mouse. Again, it "just worked." And then I bought a set of Sony DR-BT50 audiophile headphones (awesome sound!). This time it took a bit of finagling to get them working, but once I discovered and installed Blueman I got the phones paired up and all was well.

However, there was a problem. Every time I moved the mouse the sound would cut out. I thought this might be related to the CPU affinity, so I entered into some discussions about it on this thread:

[http://ubuntuforums.org/showthread.php?t=385163&highlight=affinity](http://ubuntuforums.org/showthread.php?t=385163&highlight=affinity)

Unfortunately, none of the suggestions there made any difference. I thought I was doomed to having the sound cut out when moving the mouse. 

And then the Logitech V270 mouse died. It just up and died. And it was s refurb with no warranty from Logitech, so I was SOL. I shopped for a new one and ended up buying a Razer Pro|Click mobile bluetooth mouse. It arrived today and I just finished getting it paired up and working. 

The first thing I did after getting the new mouse working was to turn on the headphones and launch Rhythmbox. As I sit here typing this I am listening to a symphony with the headphones. I can move the mouse all over, click on anything, and the sound never cuts out. Yay!

So the whole problem was that flaky Logitech V270 mouse. I heartedly disrecommend it and instead suggest the Razer, which you can get for a bit over $50 at Amazon or Dell. It costs a bit more, but it's definitely worth it.

---

### Post by John Jason Jordan on 2008-01-26
Well, this just sucks. My new Razer died yesterday. Just like the Logitech V270, it lights up, Gutsy sees it just fine, but it no longer connects. 

I got it from Amazon, so back it goes I guess.

Edit: Never mind. I found the answer and got it working again. From googling, evidently having a bluetooth  mouse just stop working is not unusual. What got it working again for me was to turn on the pairing button, then go to the command line and do:

sudo hidd --search

For some reason it loses its pairing. And afterwards the Blueman utility is no longer able to get it connected. The above command evidently resets something so it works again. That is, until it stops working again. Then back to the comand line, rinse, repeat.

---

