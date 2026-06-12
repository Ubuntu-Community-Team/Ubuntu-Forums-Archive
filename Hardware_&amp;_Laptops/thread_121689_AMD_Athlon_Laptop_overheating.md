---
title: "AMD Athlon Laptop overheating"
date: 2006-01-25
forum: Hardware &amp; Laptops
---

### Post by nickbaker77 on 2006-01-25
Hi all,

I'm totally new to linux and recently installed Breezy on my Packard Bell IGO laptop (which has a mobile AMD Athlon 1800+ processor).

Thing is, it just seems to get steadily hotter until it crashes - this laptop also has overheating issues running windows if I use it for long enough, and doesn't have any thermal sensors as far as I can tell (Speenfan under windows is not able to detect any and I can't find anything in the BIOS about temperature).

I'm not doing anything CPU intensive, the clock speed is 300MHz every time I've looked. Also can't find anything in the /proc/acpi directory and /fan is empty, /thermal_zone is also empty. I've looked in /processor/CPU0 and I can see info in the info, limit, power and throttling files which seems to indicate that throttling is working.

So what do I do? I don't know if powernow is running (how can I check) or maybe there is some software/package I can get to somehow increase the cpu fan usage on this dodgy laptop (can't take it back to shop as its about 5 years old now!)

Any ideas or pointers appreciated!

Cheers

Nick

---

### Post by byen on 2006-01-25
hey nickbaker,
Here is something that you might look into...
for checking temp and fan info you might wanna look into the program ["gkrellm"]("http://www.ubuntuforums.org/showthread.php?t=121002&highlight=gkrellm") this is a stand alone graphical program that gives you the cpu, temp (etc) information.  If you want to have a prog that monitors temp sitting on your task bar try  emifreq-applet (this is in the repositories)

Now coming back to the temp issues.. there is a [how-to in this forums]("http://www.ubuntuforums.org/showthread.php?t=85917") which help you get the right kernel for your processor (I have a AMD athlon 2800+ ).. after I tried that out my laptop still over-heats but now it takes over 100 mins compared to the usual 60 minutes of normal use.. try it out and see if it works.
I see this is your first post.. Welcome to Ubuntu!

Edit:
PS- if you are installing a new kernel as mentioned in the How-To...yours would be K7

---

### Post by nickbaker77 on 2006-01-26
Hey thanks man - I will check those out as soon as I get chance,

best regards

Nick

---

