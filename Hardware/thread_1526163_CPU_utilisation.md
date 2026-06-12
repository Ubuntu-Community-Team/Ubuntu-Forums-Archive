---
title: "CPU utilisation"
date: 2010-07-07
forum: Hardware
---

### Post by togden on 2010-07-07
I'm running Ubuntu SE 10.04 on an EEEPC 1000, 2GB ram 8+32GB HDD & 1.6GHz Atom processor.

I am newish to linux, new in terms of experience, but ive had it a while, and have gotten the basic idea to some extent.

I'm too incompetant to work out how to boot the ubuntu netbook installer, so i gave up, I've tried twice USB stick bootstraping, and gave up both times, in favour of my external DVD drive. I couldnt work out for the life of me what i was doing wrong and im not new to pc hardware or non linux software.

Anyway, the issue im having is ubuntu seems to be shredding all the power my little atom chip has, just on idle, just the static utilisiation is 50%, i don't expect to get impossible performance out of it, but just watching videos on you tube causes uses all the processor time and im left with less about 5 or 10 fps, which means my net book aint got so much net. so realy what im asking is how best do i solve this, given my knowledge base, dare i say it windows xp in its collosal gargantuan performance was faster on the net when i had that.

Options before me that i am aware of are:

Work out how to rip out some of the useless software and lower the static CPU utilisation.

Stop being ignorant and work out how to bootstrap a USB stick drive to try another distro.

Get seriously lazy and re-install windows xp

Decide its not worth my time and stick with my slow albeit sacreligiously cool satanic wall papers.

Im open to anything i havent considered, and any usefull advice on what i have.

Many thanks to anyone who is willing to give their time to my rather ignorant self.

---

### Post by xifer on 2010-07-07
would be good to know exactly what processes are consuming cpu time.  In a terminal window run the ''top'' program.

---

### Post by togden on 2010-07-07
Thanks, I now know how to look at running processes!

HHmm, apparently I was actually completely wrong about the static usage, its realy fairly low (about 10%) but when watching said videos gtk-gnash uses 100% of the cpu (in addition to the rest of the processes which use about 20% between them.

I'm guessing thats the programme that plays the videos.

So is there anything that can be done about that?

---

### Post by Shadowstripe on 2010-07-07
youtube is probably set to 720p change it to 360p

just tested this on my mini 9 same cpu can not handle 720p in flash on youtube and 480 is a little choppy

---

### Post by xifer on 2010-07-08
> **togden said:**
> Thanks, I now know how to look at running processes!

HHmm, apparently I was actually completely wrong about the static usage, its realy fairly low (about 10%) but when watching said videos gtk-gnash uses 100% of the cpu (in addition to the rest

Have a look at this thread. 

[http://ubuntuforums.org/showthread.php?t=588831](http://ubuntuforums.org/showthread.php?t=588831)


seems the answer is to remove the package


sudo apt-get remove --purge gnash gnash-common mozilla-plugin-gnash

---

### Post by togden on 2010-07-08
Thanks for that, but having removed the SWF player, how do I get it back, I guess the question I'm really asking is, what flash player, if any can I use that wont use all my processor time? In the mean time I'm going to try a different browser as Godzilla Fire fox is'nt the lightest of programs

---

### Post by togden on 2010-07-08
Solution-Install chrome. 

I'm sorry guys, I sold my soul to google well over a year ago, and this is just another re-enforcement that it was a well informed choice, chrome plays vids flawlessly,(I'm guessing it comes with a built in flash player) with other stuff going on at the same time, no problems, much love and thanks for the help, but I think Ive found my solution. Oddly, now firefox plays them fine too, so logicaly i could have installed and then never used chrome, but there is a clear difference in performance now.

If anyone else is reading this for a final solution to a simmilar problem, after installation of chrome on the older 1.6GHz atom, SWF videos at 360p use 70-80% of the cores processor time, including the browser. It uses more like 90% when not in performance mode. But you still get about 25-30 frames per second so not noticably poor like before.

And many thanks to the contributors above.

---

