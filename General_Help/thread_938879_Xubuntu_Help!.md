---
title: "Xubuntu Help!"
date: 2008-10-05
forum: General Help
---

### Post by ethan brand on 2008-10-05
OK, so I have finally decided to once again try out a Linux distro since the days of Mandrake and the choice came down to Xubuntu. I set up a dual boot with Windows XP because I still need Microsoft for Word, Excel, and Remote Desktop for work. Well, the thing is blazingly fast and Compiz is super fun to use. I was initially worried about the functionality of my wireless adapter (Linksys WUSB600N) but a wrapper I found did the job perfectly.

Now, here is the funny thing. The wrapper works better than either the standard Linksys program or the default windows connection manager. By better, I don't really mean the quality of the connection but the speed at which the initial authentication and connection is established. In Linux the connection is nearly instantaneous but in Windows, it takes 30+ seconds before I can surf the web. Well, ****! It's a small thing, but this has caused me to almost exclusively use Linux ever since I've installed it, except when I need Remote Desktop. I do not play much games anymore and e-mail and internet is really all I need so this is totally working out for me.

Now, if I can completely eliminate windows from my life I think I'll be fine with it but in order for that to happen, I need to somehow use Remote Desktop or something like it in Linux. Is this possible? And how about Word and Excel?

---

### Post by ethan brand on 2008-10-05
Ok. Simple google search is all that was needed.

rdesktop works perfectly for connection to a windows machine.

openoffice opens word and excel.

Problem solved.

---

### Post by MaindotC on 2008-10-10
You said you found a wrapper to get your WUSB600N working.  What method did you use?  I got it working using ndiswrapper but after about an hour of usage the device seems to shut off.  The green light is still illuminated but I can't access any network services.  Thanks!

---

### Post by ethan brand on 2008-10-10
I'm also using ndiswrapper (version: 1.52, vermagic: 2.6.24-19-generic SMP mod_unload 586) with my WUSB600N but the stability of my connection is rock solid. The wireless driver I'm using (unsure about the version) is the one supplied with the adapter out of the box.

I'm just a newbie Linux user so I'm not quite sure of the reason for your connection drops. Does your wireless connection icon still display the bars when this happens?

---

### Post by MaindotC on 2008-10-10
Damn, yours never drops :(  I did ndiswrapper -v and I got the same output but it didn't say 586.  Did you use the gui or do it via command line?  I can't imagine that would make any difference but I just want to make sure the gui is calling v 1.9.

---

### Post by MaindotC on 2008-10-10
I tried it via command line and I made sure I used v 1.9 and it said it was already installed so I'll just assume gui doesn't matter.  Just seems odd after usually an hour it stops working.  I wish I at least knew how to troubleshoot these issues.

Anyone willing to take a look at my logs?

---

