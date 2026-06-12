---
title: "Dell Laptop with Targus Port replicator issues"
date: 2006-04-09
forum: Hardware &amp; Laptops
---

### Post by eprench on 2006-04-09
I own a Targus Universal USB port replicator, it is a very nifty device, it has 4 USB ports, 1 ethernet, audio in and out, and last but not least VGA.

This last one (the #%$^&# VGA) is the mother of all my troubles. It does not work, and not only it does not work, it floods the crap out of every  screen I open with:
[4297767.492000] pegasus 1-1.6:1.0: ctrl_callback, status -32

not only that, it floods my logfile, which fills the crap out of my harddrive and causes my computer to crap out after a couple of months.

PLEASE HELP!!!] (*,)

---

### Post by eprench on 2006-04-09
by the way, I forgot to add my hardware's information

Laptop:
Dell Latitude CSxH 500
Processor: P3 500mHz
Memory 256Mb

Port Replicator:
Targus ACP50
4 USB ports
1 ethernet
Audio in/out
VGA port

---

### Post by doconnor on 2006-07-14
Have you solved this problem yet?

I am having similar problems.  I have a Dell Inspiron 5150 and a Targus ACP50US.

The message I am getting is similar but mine ends witha  a STATUS -71.

I have searched the internet but have not found the solution.  I have not been able to get the external monitor to work.

The only sounds I get are from the notebook speakers. The mouse, keyboard and printer worked thru the port replicator without me doing anything.

Thanks,

Dale

---

### Post by eprench on 2006-07-15
I was having serious issues with that junk, it was flooding my log, and eventually making the whole thing go haywire. However, there is a way to "jerryrig" the situation. You can set a partition for the log, and set it to dump every 24 hours and rewrite the log. This worked for me, but it still made the computer sorta slow, and it was impossible to do any cool geeky stuff with it because it was constantly flooding the non-gui (not sure of the name). I am done with this problem because I recently got a new laptop (w00t!) and since it is a Hell, it has a lot of propietary hardware that will not run on Linux. 

About the speaker issues, make sure you go to system and set the audio card on the replicator to be the default, and then go to your player and tell it to use that card instead of the one on board, so, just add a 1 after it. The VGA, has issues, and the error it generates is USB related. How to fix it is a mystery, as there are very little people cheap enough to use Linux, and still rich enough to afford $150 on convenience for a port replicator.

---

