---
title: "EMIfreq won't throttle"
date: 2005-07-03
forum: Hardware &amp; Laptops
---

### Post by Dark79 on 2005-07-03
Please excuse my newbie-ness ;)

Ok, so I finally got powernow and cpufreq to work after doing some searches here, but I'm not too fond of them controlling frequencies themselves.

So I installed the emifreq applet and added it to my panel since it's supposed to allow you to manually control throttling. But when I click it, there's no menu to do this. It basically runs at 100% all the time. How do I get the menu to come up so I can choose a different frequency?

Thanks in advance!

---

### Post by JLB on 2005-07-04
you must start emifreqd as root or set it up to run at startup. emifreqd which is the daemon, must be run as root.

try this.

open the console

sudo emifreqd


Can you throttle now?

JL

---

### Post by Dark79 on 2005-07-05
[QUOTE=JLB]you must start emifreqd as root or set it up to run at startup. emifreqd which is the daemon, must be run as root.

try this.

open the console

sudo emifreqd


Can you throttle now?

JL[/QUOTE]

Thanks for the help. I actually figured it out before checking back here ;) 

But, emifreqd must be run from root (sudo -s -H emifreqd) to work. If I just do sudo emifreqd, I get an error about not having authorization. 

So my new question is, how do I get it to run at boot so I don't have to login to root to get emifreqd running. Thanks!

As a side note, I installed emifreq 1.8 thinking I just needed a new version. If anyone else tries to compile it, make sure your configure command looks like: 

./configure --prefix=/usr/

Otherwise everything gets installed in the wrong dir, and emifreq won't show up as an option when you right click a panel and select "Add to panel". 

I'm sure that's probably elementary for everyone else, but as a newb it took me a while to figure it out on my own ;)

---

### Post by Dark79 on 2005-07-05
Hmm, I guess it does work with a simple "sudo" command. So I guess that makes the solution to my problem a lot easier. I should be able to figure it out from here. Thanks!

---

