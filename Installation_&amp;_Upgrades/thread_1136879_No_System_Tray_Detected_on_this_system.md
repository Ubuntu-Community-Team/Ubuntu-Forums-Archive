---
title: "No System Tray Detected on this system"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by irv on 2009-04-25
The first time booting after upgrading to 9.04 I get this message:
[IMG]http://wabasha-server.net/Screenshot-HPLIP%20Status%20Service.png[/IMG]
I don't have any idea what this is? Any help would be great.
Thanks

---

### Post by kpkeerthi on 2009-04-25
Right-click on the panel, and add a System tray

---

### Post by irv on 2009-04-25
> **kpkeerthi said:**
> Right-click on the panel, and add a System tray

The problem is when I right-click on the panel, there is no System tray to select in the "Add to Panel".

---

### Post by irv on 2009-04-29
Every time I restart my system I still keep getting this same error. Am I missing something from the upgrade to 9.04? Any help out here?
Thanks

---

### Post by NavyJoe on 2009-04-29
I dont have a panel or a system tray.  they only way I could figure out to bring up firefox was start a help page and look for help online.  that's the only thing I can do.  What other options are there besides:
4 Days Ago 10:20 AM
kpkeerthi 	
Re: No System Tray Detected on this system
Right-click on the panel, and add a System tray

Cus that aint getting the job done!

---

### Post by irv on 2009-05-02
> **NavyJoe said:**
> I dont have a panel or a system tray.  they only way I could figure out to bring up firefox was start a help page and look for help online.  that's the only thing I can do.  What other options are there besides:
4 Days Ago 10:20 AM
kpkeerthi 	
Re: No System Tray Detected on this system
Right-click on the panel, and add a System tray

Cus that aint getting the job done!

You are right. When I Right-click on the panel and do an add to panel the option System tray is not there.
I keep getting this error every time I start the laptop and I don't know how to get rid of it.

---

### Post by Alterax on 2009-05-02
Try adding a "Notification Area".

---

### Post by irv on 2009-05-02
> **Alterax said:**
> Try adding a "Notification Area".

I added the "Notification Area" and rebooted and I get the same error.
Thanks for the tip anyway.

---

### Post by irv on 2009-05-04
We can mark this one solved. How I finial got rid of this error message was by going to Synaptic, click the Status bar on the left, in the windows above, click Not Installed (residual or config) and mark all for complete removal. By doing some cleaning up it got rid of it.

---

### Post by Prokash on 2009-07-17
I'm having the same problem, but the screen also flicker, I can't click to the panel and add.

Is there a way to fix this. I just updated to 9.04 from 8.10.

Please help!!!

No way to get to shell command. 

Thanks in advance
-p

---

### Post by irv on 2009-07-18
> **Prokash said:**
> I'm having the same problem, but the screen also flicker, I can't click to the panel and add.

Is there a way to fix this. I just updated to 9.04 from 8.10.

Please help!!!

No way to get to shell command. 

Thanks in advance
-p

Actually the problem came back and it was being caused by HPLIP which is a utility for my HP printer. I reported a bug and here was the fix.
When the HPLIP Status Service was trying to load in the notification area in the panel I would get this error, so I had to change the command line for loading the HPLIP Status Service.

sh -c "sleep 15; exec hp-systray"

I changed 15 to 45, and ever since no error message at startup. I got this help from Gyorgyi Toth who said, "I am just a regular user, so just gave it a try, but maybe somebody knows, whether it is an option that delays startup somewhat, and this way Hplip does not want to climb onto the system tray "too early".

---

### Post by celem on 2009-09-15
Adding a "Notification Area" cured the problem for me.
I use Ubuntu 9.04 and the newest version of HPLIP downloaded from HP, instead of the repository version, which was giving me segfault problems..

---

