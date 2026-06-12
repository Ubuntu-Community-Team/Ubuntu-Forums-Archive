---
title: "Laptop Power Management"
date: 2006-03-17
forum: Hardware &amp; Laptops
---

### Post by teasum on 2006-03-17
New to Ubuntu here, but I love it.  Lots of threads mention the biggest hurdle for laptops running Ubuntu is wireless, but mine seems to be working fine.  I dual-boot Breezy and XP on a Dell Inspiron 8600, and my big problem is power management.  The battery life is not only poor, it's bizarre.  

Basically, I only get two hours under Ubuntu--much longer in XP.  But the wierd part is that the battery monitor steadily declines for a while and then suddenly (and I mean almost instantaneously) drops down to 4 or 5%.  I tested it last night, and it jumped from 47% to 4%.  The scary thing is, it's not just the monitor reading things incorrectly.  My battery also has an external LED monitor on it, and I checked it constantly while testing--and it too dropped to almost zero.

The only apps I had running at the time were OpenOffice2, Firefox, and Rythymbox.

Last but not least, hibernation or standby do not work.  The computer will suspend, but it will not boot on startup.  Instead of a bootsplash, I get a wierd vertical striped screen.

I'd like to switch to Ubuntu, but this issue is making it difficult.  Any ideas?

---

### Post by aggiechemist on 2006-03-17
Does anything seem to be comsuming a lot of power?

Ideas:
Fans constantly on?
Hard drive always going? (you should be able to hear it spinning)
High CPU usage?
High virtual mem usage? (goes back to the hard drive thing)

If we can figure out what is using the power, then maybe it will show us where to fix.

---

### Post by teasum on 2006-03-17
It doesn't seem to be consuming an inordinate amount of power.  I have the CPU freq. applet running, and it's only rarely above the minimum (600mHz).  As for the fan, it seems to be running allright--however, since I'm a bit of a newbie I'm not sure how to check it properly (i.e. temp, fan speed, etc.).  The disk is not spinning too much, as far as I can tell.  Virtual memory shouldn't be a problem with only three apps and 768m RAM.  

I installed Gkrellm to try and monitor such things, but it doesn't seem to indicate anything special.  Also, there is some error reading the fan speed on my laptop, so it won't tell me anything there.  I didn't have that running yesterday when I did my test.  I can try again tonight with gkrellm running and see if there are some unusual spikes in any of the areas you mentioned.

Perhaps I should back-up here: is there a way to 're-set' my power management?  Perhaps uninstall/reinstall some packages (i.e. without reinstalling the whole OS)?

Thanks!

---

### Post by aggiechemist on 2006-03-17
Hmmmm... I'd watch the battery life when OpenOffice isn't running. That program is a notorious resource hog. I've got to wonder if that was a problem. I much prefer using Abiword for word processing and Gnumeric for spreadsheets, they are much faster and less resource intensive.

As for the suspend/hibernate stuff, I'm not sure it ever works well (in any form of Linux). It is one of the areas still being polished. I know the ACPI and APM are the things that handle it, so maybe you can learn something from man apm and man apmd. Personally, I've just gotten into the habit of not using the suspend on my system.

Good luck!

---

### Post by teasum on 2006-03-17
Thanks for the advice.  I'll try again tonight without OpenOffice running.  Can Abiword support Asian languages?  That's the main reason I use OpoenOffice, because I'm looking for something minimally different from M$ Word.  And I *guess* I can live without the hibernation for now.  I hope they can improve on it with Dapper.

On another note, what worried me the most wasn't the short battery life per se, but the *instantaneous* drop from 40+% to 4%!  If it just drained away at a high rate (e.g. because of a constantly running fan, high CPU usage, etc.), it would be ok... but is there anything to explain the battery just dropping out like that?

Anyhoo, thanks foor the advice.

---

### Post by aggiechemist on 2006-03-17
The instant drop is definitely strange. Acutally, the best reason I can think of for that would be an intermittent short causing a rapid discharge. Which is bad. But I'm not electrical engineer, so don't tret that as absolute.

Abiword is very much like using Word. Same button layout and menu's and options basically. I'm not sure how it is with Asian language support, but it is pretty widely used so I would think it has pretty good support.

---

### Post by teasum on 2006-03-22
Sorry for the long delay in following up on this.  I didn't do as precise a test this time, but basically, I still have the problem with the battery power dropping rapidly.  I had my laptop unplugged with minimal CPU, fan, and HD activity, and something like 40-ish5 remaining.  A couple minutes later, I come back kto an error message saying my battery is critically low!  So, same old problem.  

I'm hoping someone out there has some advice... perhaps I should reinstall some packages?  Should I try gnome-power-manager (which I recently noticed in Synaptic)?

I really hope power management for laptops is improved under Dapper, because, as it is, I use Ubuntu when plugged in at home, but if I'm away, I have to use XP.

---

### Post by radoon on 2006-03-29
Hi there,

How old is you laptop and/or battery?  I noticed on my laptop (kind of old) that the battery dropped from 70% to 10% instantly as it drained.  This is when I was running WinXP on it.  This was caused by the battery being at the end of its life cycle, and possibly incorrect charging procedures (such as not draining completely on the first 2 or 3 runs).

I replaced my battery with a new one and get constant usage now.

---

### Post by teasum on 2006-03-31
[QUOTE=radoon]How old is you laptop and/or battery?  I noticed on my laptop (kind of old) that the battery dropped from 70% to 10% instantly as it drained.  This is when I was running WinXP on it.  This was caused by the battery being at the end of its life cycle, and possibly incorrect charging procedures (such as not draining completely on the first 2 or 3 runs).[/QUOTE]

I bought my laptop (including battery) in 2003, so I don't think it's that old.  I haven't noticed the rapid drop while running XP, however.  That's also, perhaps, because I haven't used XP in a while (I like Ubuntu!).  I'll try draining my battery and recharging to 100%, and then see what happens.  

Does anyone know of any howto's re: laptop power management?  It seems to be a pretty consistent problem for a lot of people.  Even if I had crappy battery life with Ubuntu for some reason, I wouldn't be too worried if standby and/or hibernation worked.  Unfortunately, if I leave my computer on and unplugged while this rapid drop occurs, the computer will just run out of power --not a healthy thing for my hard drive (or the rest of my computer).

Thanks!

---

### Post by json684 on 2006-04-18
This just happened to my computer too! I'm running a hp DV1000, and it dropped from around 50% to 5%. At least I'm not alone. I wasn't doing anything really power intensive either.

---

### Post by jasongrieves on 2006-04-20
Welcome to the cheap and dead cells in your battery club :)  Same exact thing on my Inspiron 8600.  Solution, new battery :).  I'm not willing to pay the 150 or so...

---

### Post by pocket on 2006-04-22
I think there is more to it than the battery life.  i dual boot xp.  I ca run in xp for 2+ hrs on my hp zt3000 lappy, but ubuntu dapper doesn't allow for 10 minutes from a full charge before it pops a low batt warning and shuts down.  i think thers a bug in the acpi logic

---

### Post by ozorba on 2006-04-22
This may be due to the CPU Speed. I have been observing odd behaviour with my laptop. The CPU speed keep on switching between 800MHz and 1.6GHz (I have a Centrino 1.6MHz laptop), whereas it was sitting at 600MHz most of the time when I was running Breezey.

It may be the ACPI. Has anyone got any idea?

---

### Post by mainmojo on 2006-04-22
The laptop battery issue seems to be a pain in the neck for most of us laptop users. It could be a bug in acpi. I have a 3 month old laptop (sony viao) and gnome-power-manager occassionaly warns me of low battery life even when its clearly showing a 97% charge. Is anyone checking for the laptop-mode status? You can do this by:

cat /proc/sys/vm/laptop_mode

It should have a non-zero value in there when running off your battery- I think. I have to keep restarting the laptop-mode daemon (/etc/init.d/laptop-mode restart) every now and then. Now, there are two laptop-mode packages provided by ubuntu - I don't know which one is responsible for what: one is called "laptop-mode", and the other "laptop-mode-tools". Which one should be installed (or should both be).

Battery Issues:

My battery life differs considerably from my windows install - It drains much faster when running dapper. I have no clue why. Also, truth be told, gnome-screen-saver eats up a lot of power when running (full cpu) so dont leave it on too long.

Another issue is that my laptop *occassionally* hibernates when I unplug my ac-cable after a full recharge - very weird and annoying and yet so hard to debug since no /var/log/messages are displayed.

Any way, everything else works fine and dapper is much snappier than XP - the difference is palpable. I'll try assist with the debug as much as I can if any devs need any info. The laptop is a sony vaio VGN-FS790 and has the current Dapper Flight-6 and dual boots XP.

---

