---
title: "Which logs to check in case of system crash?"
date: 2008-10-20
forum: General Help
---

### Post by Green_Star on 2008-10-20
From couple of days, my system is frequently hanging. When ever I try to start fileZilla my system hangs, but I also observed it hanged in my other several instances which is not related to filezilla, so I think filezilla is not the problem. Once my system stuck the only option I have is to manually powercycle(reboot) the system, Ctrl+Alt+F1, Alt+F1, Ctrl+Alt+Backspace etc doesnt work. 

So my question is , once I reboot my system, how to check which causing that problem? I am not that good at checking logs i mean which and where etc. 

Thanks in advance.

---

### Post by phidia on 2008-10-20
Take a look at this [keystroke method]("http://txt.binnyva.com/2007/09/reboot-linux-when-hung/") of restarting a hung/frozen system It's better for your hardware.

You can look at log files from System > Administration. Although you will find much more in /var/log. Look at messages, xorg.log, and fail.log maybe others?

---

### Post by Green_Star on 2008-10-20
> **phidia said:**
> Take a look at this [keystroke method]("http://txt.binnyva.com/2007/09/reboot-linux-when-hung/") of restarting a hung/frozen system It's better for your hardware.

You can look at log files from System > Administration. Although you will find much more in /var/log. Look at messages, xorg.log, and fail.log maybe others?

Thanks for your quick reply. I tried some other magic key sequence but didn't work, next time I try this. Yes, it is better for my hardware, and buy the way my computer is located in basement hanging from ceiling. And I am on main floor, so to reboot it I have to walk down to basement and I have to wait 30sec to 60 sec to start again. (for some reason my system doesnt start immediately )

doesn't those messages shows only current running messages but not before the reboot? Any way I will check those.

---

### Post by phidia on 2008-10-20
> doesn't those messages shows only current running messages but not before the reboot? Any way I will check those.

No the log files in /var/log are continually updated however all activity is recorded there. Keep in mind that there is a lot of data to read through there, and if you have a idea what is causing the problem a creative use of 'grep' could be a time saver.

---

### Post by Green_Star on 2008-10-20
As I told you, I am not able to figure out what's the problem, I think I have to check the logs with the time I rebooted. I see all the logs are logged with there times. 

By the way, if system is completly stuck then how come linux going to write the logs about the problem? Is it make sense to check the logs?

---

### Post by phidia on 2008-10-20
Just because the gui desktop crashes or freezes does not mean all processes are stopped, and usually the system captures the last activity before a full crash anyway (it only takes the system fractions of a second to produce the log files-generally)

---

### Post by Green_Star on 2008-10-21
My machine hanged again, actually I tried to hang it to know the cause of the problem. keystroke method didn't help me to do the reboot. After hard reboot the machine I checked System > Administration -> Logs, I checked all the logs, I didnt find anything which related to my problem. 

Back to my hang problem, I have three disks, and one of them is SATA, my ubuntu hanging when ever I try to access that drive ( from nautilites, didn't tried from command prompt). This drive used to work very well. I will try to access this from command prompt and also try from recovery mode and let you know. I guess that drive could be the cause of the problem.

---

### Post by rodkerbs on 2010-11-24
I am in the same boat. Just loaded 10.10. System is awesome except for complete random hangs. The screen is there but the mouse and keyboard don't move. No flashing lights, no nothing. I have looked at more logs than necessary, even though winter is fast approaching :) Is there a capture app that I could leave running that would snag some tasty info before the whole thing goes?

---

