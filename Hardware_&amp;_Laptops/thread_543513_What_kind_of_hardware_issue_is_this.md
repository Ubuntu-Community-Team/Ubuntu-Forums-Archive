---
title: "What kind of hardware issue is this?"
date: 2007-09-05
forum: Hardware &amp; Laptops
---

### Post by Hmarroqu on 2007-09-05
I have 2 ghz processor with 629mb of mem  (128+512) .  Now the issue im having is that when the box loads and also when im doing tasks with lets say at the least 2 pgrms open such as firefox and gaim, there are brief 3-6 second lock ups, like lag.  i placed a system monitor on my panel and i notices that it shows that the CPU goes to 100% at times.  My take is that its the cpu but its 2ghz?!?!? 

any input on this?:):)

---

### Post by eggdeng on 2007-09-05
Dupe.

---

### Post by eggdeng on 2007-09-05
Some process is tying up the CPU but which one? You can get a list of running processes and a pid for each by typing ```
ps -A
``` or ```
ps ax
``` in a terminal. if you see any likely candidates, to see how much CPU its using, try ```
top pid1 pid2 etc
``` where pid1, 2, etc are the process ids you got earlier .
My guess though would be that it's the graphics driver. Try editing your xorg.conf to revert to the vesa driver and see if symptoms persist.
2GHz is plenty processor but you're a little tight on RAM, especially if you're running Beryl & co.

---

### Post by Hmarroqu on 2007-09-07
> **eggdeng said:**
> .
My guess though would be that it's the graphics driver. Try editing your xorg.conf to revert to the vesa driver and see if symptoms persist..

how would i do that?

---

### Post by Hmarroqu on 2007-09-07
Well i just figured out that at some peaks , especially when im loading pages, firefox takes up to 80% of my cpu,  or at least thats what the system monitor shows.
I find it odd that with 2ghz , a program like firefox uses up to 80%.  any suggestions?

---

### Post by eggdeng on 2007-09-07
```
apt-get install opera
``` Very lightweight & has some nice features these days.:)

---

### Post by Officer Dibble on 2007-09-07
What model motherboard do you have?

---

### Post by Hmarroqu on 2007-09-07
> **Officer Dibble said:**
> What model motherboard do you have?

i have no idea, this comp im using was an old emachines, not to old obviously if it has a 2.0 and ran xp previously but as far as model, i have no clue, i would like to knw myself.

---

### Post by Hmarroqu on 2007-09-07
eggdeng , hows is opera with plugins like flash and jaba? how bout built in mplayer like in firefox?

---

### Post by eggdeng on 2007-09-08
I got flash working just by editing the ~/.opera/pluginpath.ini file and pointing it to the firefox plugins folder. As for mplayer, the wiki [http://ubuntuforums.org/showthread.php?t=543513]("http://ubuntuforums.org/showthread.php?t=543513") has this to say
> As of now (May 2007), embedded video playback does not work well in opera. The probably best plugin, mozilla-mplayer, works only partialy and requires [WWW] manual compiling. You can try vlc, gxineplugin or totem, but it is probably adviseable to just use Firefox for sites as [WWW] [http://www.apple.com/trailers](http://www.apple.com/trailers)

---

### Post by Officer Dibble on 2007-09-08
The reason I was asking for the model of your motherboard is so that I could find out if it can handle more than 512MB RAM or not. At the moment it should be reading 640MB RAM considering the sticks you have in at the moment.

Of course there are reasons why your Motherboard *might* read as being 629MB as opposed to 640MB, but finding out the motherboards capacity would be simpler than exploring all the other options first.

---

### Post by eggdeng on 2007-09-08
Be inclined to agree with that. Upgrading the RAM is probably the easiest way to go.

---

### Post by Hmarroqu on 2007-09-08
so if its capacity were up to 512 then any more would freak it out is what your saying? cause i was considering getting another 512 stick but would that be futile?  another thing i noticed is that this was not an issue up until recently and the only thing i have done recently is add a 4 usb hub to my usb ports, thats it.  thanks for helping me out with this mystery. i appreciate it alot. im gona disconnect some things and run some trials to see if i can find any changes.

EDIT PS:

well i just took out the 128mb out  and left the 512 in.... so far so good, i hope this is the problem, i have not seen the symptoms so far.  ill keep this posted, and once again i thank you all for helping me out on this.   one of the many reasons i will never leave ubuntu or the community.

---

### Post by Hmarroqu on 2007-09-09
well, with only the 512 in, it ran ok for a little and i tired to make it spike, and it did not. although after watching pirates of silicone valley on it i came back and my cpu usage spiked again, this is driving me nuts.   i tried to find out what it could be by disconecting hardware externally as well as internally and theres still no damn change!.  As im writing this, the comp has spiked and lagged about 6 times.  Could it maybe be the power source? cause i do have a not so powerful one? but does that affect the cpu?

---

### Post by Officer Dibble on 2007-09-09
> **Hmarroqu said:**
> well, with only the 512 in, it ran ok for a little and i tired to make it spike, and it did not. although after watching pirates of silicone valley on it i came back and my cpu usage spiked again, this is driving me nuts.   i tried to find out what it could be by disconecting hardware externally as well as internally and theres still no damn change!.  As im writing this, the comp has spiked and lagged about 6 times.  Could it maybe be the power source? cause i do have a not so powerful one? but does that affect the cpu?

We need to know what hardware you have, motherboard and CPU. As I am just learning Linux as an OS I am unsure how you get this information, but once you can tell us we can pin the problem to it being an OS issue or Hardware issue.

In all honesty it could be a few things, the size of your swap file, low spec hardware performance, etc. But we need to know what sort of kit we are looking at. For example, if you were sitting in front of IBM's Deep Blue we could rule out hardware specs as being the problem... :)

---

### Post by Mrmental on 2007-09-09
I don't mean to panic you, but there are all kinds of hardware issues that can cause your computer to go slowly, and some of them are downright unpleasant. A Hard drive that is beginning to fail often causes slow down, as it has to keep retrying to read from failing sectors. A good trick with desktops is to listen to the sound of the drive seeking, but with quieter laptop drives, the unhappy sound of a hard-drive dying is easy to miss. I would suggest running a check with something like maxtor powermax.  Doing a deep scan with [powermax]("http://www.majorgeeks.com/Maxtor_Powermax_d1386.html") often takes a long time, so if I were you I'd do it overnight, having backed up any essential data first.
Again, it's probably not the hard drive, but it's worth checking.
If it's not the hard-drive, many other hardware faults can cause slow down. Faulty memory has different symptoms than hard drive failure and on the whole, if your memory is faulty, you'll know about it. Sometimes however, subtle damage doesn't throw up as much trouble. The ubuntu live-cd can run a check on your memory for you. Running a scan with that is also a good idea.
I know this stuff is probably teaching you to suck eggs, but when I repair computers for people, especially laptops, I always run these checks, and it's often helped me diagnose some otherwise intractable problems. For example, a friend asked me to put ubuntu on his brand new laptop because windows was "Too god-damned slow". When I ran a check on his memory, I realised that it was slow because he had 1024mb of Ram of which only 768mb was working. This was on a brand new laptop, which just goes to show that these things happen more often than you think.
I hope this helps. Actually, I don't. I hope this is completely irrelevant and your problem is a lot more benign. It'll cost you less money that way!:)

---

### Post by Hmarroqu on 2007-09-09
> **Officer Dibble said:**
> 

In all honesty it could be a few things, the size of your swap file, low spec hardware performance, etc. But we need to know what sort of kit we are looking at. For example, if you were sitting in front of IBM's Deep Blue we could rule out hardware specs as being the problem... :)

what do you think a good swap size is? 

And i will try to solve the mystery of what motherboard i have.  I picked it up from an office that was moving.  I payed 30 bucks for  motherboard, power source and hdd and got the rest from other comps so this is a Frankenstein i built .

Thanks for the insight to "mrmental":)  Since my last   post i did run a mem check with only my 512 in it and it came out ok.  I will check my HDD which could have some issues since i have no clue where i found it from but aside from that i do not hear any abnormal sound with the hdd freaking out.

---

### Post by Officer Dibble on 2007-09-10
> **Hmarroqu said:**
> what do you think a good swap size is? 


Well if your motherboard can handle the 640MB you want to fit, multiplying that by 1.5 gives you 960MB... so make your swap file/patition 1GB... should be enough. :)

---

