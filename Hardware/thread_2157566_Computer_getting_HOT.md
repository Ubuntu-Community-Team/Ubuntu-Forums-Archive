---
title: "Computer getting HOT"
date: 2013-06-25
forum: Hardware
---

### Post by ThatNewGuy on 2013-06-25
I dont know if its just me or not but i Have windows 8 and Ubuntu 12.10 installed on my laptop. I swear when I run Windows 8 my computer (the keyboard area by the fan) is mainly cool unless im using like google sketchup or playing a blu ray movie. When I use Ubuntu its hot from the get go and when im using Blender its hotter but never over heats or anything just really hot like more than usual.
Any thoughts or solutions?

ThatNewGuy

---

### Post by TNFrank on 2013-06-26
You can do a " sudo apt-get install acpi" from terminal then do a "acpi -t" to see what temps you're actually getting.  You can also install Jupiter to adjust your CPU load and see a quick view of CPU temp(do a search on you favourite search engine for "Jupiter Power Management" then follow the steps to install from terminal).  Sometimes some Linux versions will cause your processor to run hotter because they tend to run it all out and don't throttle back like Windows will do but you'll trip the thermistor and shut down before you'd burn anything up so don't worry about causing any damage. Still, it is a good idea to keep an eye on things.

---

### Post by ThatNewGuy on 2013-06-26
Thank you for your response, Perfect answer to my problem thanks.

---

### Post by ThatNewGuy on 2013-06-26
Yup found the culprit. I was reading about 64 C for idle and 74C for youtube videos. I knew instantly that was way too hight so I took my laptop apart cleaned the dust and put some royal purple on the fan post to lube it. Also re did the thermal paste which was cracked and dried up. glad i took it a part now then later. So i re-checked the temp and im 45 C idle and 52-55 youtube watching. 
Thanks a million

---

### Post by TNFrank on 2013-06-26
I was going to suggest you check the fan area for dust bunnies but didn't know how much you'd know about taking your computer apart. I found a nice big dust bunny in my wife's fan when I installed the new keyboard.  
Your new numbers sound about right. My old HP nc8230 runs around the high 40's, mid-50's unless I'm doing the clamTK scan then it sometimes gets to 80*C but my critical point is 105*C so I'm still good with plenty of room.
Glad you got things figured out, congrats.:KS

---

