---
title: "Dell Inspiron 8600 - Cannot detect any network devices :("
date: 2006-01-05
forum: Hardware &amp; Laptops
---

### Post by anshumanoz on 2006-01-05
Hello,

I am a newbie and I had posted this question in another category in the forums but didn't get an answer to solve my problem.

I have a DELL Inspiron 8600 laptop. It has a Pentium-M processor and consequently is using that for wireless connection to my wireless cable modem. I am not using any 3rd party tools or cards - just plain and simple centrino processor for a wireless connection. This works fine in Windows XP Professional.

I installed ubuntu for the first time ever (actually first ever linux installation). On the system tray (Sorry for windows terminology), I see an icon and I click on it and it says "No network devices found" or something to that effect. I have the WEP key, the IP Address etc with me but I guess all of that is useless until a network device is detected.

What should I do? I've been trying for a few days now! Help....

Anshuman

---

### Post by Zelut on 2006-01-05
Ok... let me dive into this one too.  We really need a sticky for wireless support.

Ok, I contributed to a wiki on setting up wireless.  First of all I'd like you to read thru it & see what progress you can make on your own.  If/when you get stuck feel free to reply/email/IM me so we can get you going.

[http://wiki.ubuntu.com/forum/hardware/ndiswrapper](http://wiki.ubuntu.com/forum/hardware/ndiswrapper)

I suggest starting below at Step One (my contribution) with careful attention to step 2.  THIS IS THE TRICKY PART.

---

### Post by anshumanoz on 2006-01-06
Ok, I'll try the steps as outlined in your wiki and see where I get to. Fingers crossed, it should all work. I'll reply regardless...

Just one question though - in your wiki post when you say things like "sudo dpkg -i ndiswrapper-utils_1.1-4ubuntu2_i386.deb", I presume you want me to type this in the command window (windows terminology again)?

---

### Post by anshumanoz on 2006-01-06
Ok, this is weird and I don't know how this happened but my problem is fixed. Last time I entered the WEP key and the correct IP address, subnet mask etc. BUt, I couldn't get ubuntu to detect my network device, so I gave up and posted the question on this forum.

BUt, today I restarted my laptop and booted into ubuntu and lo and behold, it worked! IN fact, i am writing this reply from within firefox within Ubuntu. So, I guess the relaiable old restart fixed the problem.

Finally now I start using ubuntu :)

---

