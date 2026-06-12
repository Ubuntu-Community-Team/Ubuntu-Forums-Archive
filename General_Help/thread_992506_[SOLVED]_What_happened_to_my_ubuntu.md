---
title: "[SOLVED] What happened to my ubuntu????"
date: 2008-11-24
forum: General Help
---

### Post by Jammanuser on 2008-11-24
Hi, i just recently installed ubuntu 8.10 on top of my Vista OS, using wubi-installer, and up until now it was running ok!!! i just tried to boot into ubuntu, and got the following error: "crc error" and then on next line: "system halted" 

does anyone know what the hell is going on? i even tried getting in using the safe mode, but got the same error! :mad: 

Thanks in advance!!!

---

### Post by ago on 2008-11-25
You might have to run chkdsk /r from within windows in the drive where you installed Ubuntu. See the Wubi Guide for more info.

---

### Post by Jammanuser on 2008-11-25
> **ago said:**
> You might have to run chkdsk /r from within windows in the drive where you installed Ubuntu. See the Wubi Guide for more info.

where's the Wubi Guide???? :confused:

sorry! i'm a noob to ubuntu!!!

---

### Post by ago on 2008-11-25
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Jammanuser on 2008-11-25
> **ago said:**
> You might have to run chkdsk /r from within windows in the drive where you installed Ubuntu. See the Wubi Guide for more info.

well...i just ran a disk check (which took over an hour, i might add!) and after it was done, it went to a blue screen that said: "a problem has been detected on ur computer, and it has shut down to prevent damage to ur computer", or something to that effect!!! well...i rebooted my computer, managed to get into Vista once, and it screwed up before it finished the startup process, so i had to an improper shutdown, after which when i restarted it, it gave me first the options of booting into either Vista or Ubuntu (as normal), and i chose Vista, and then i got a screen with options of either starting windows normally, or running startup repair (recommended). well...first i chose to start up Windows normally, but it failed, flashing a blue screen for a split second, and then automatically restarting, and sending me to the exact same place where i choose to start up Windows normally or launch startup repair!!! i tried once again to start up normally, hoping the result would be different, but got the SAME ******* message!!! :mad:  and so i finally launched startup repair, and its only through pure luck, i think, that it worked, and i managed to get into Vista again, and come back here to make my report!!!

i would be thankful if u do not suggest a stupid disk check again!!! :mad:

---

### Post by Jammanuser on 2008-11-25
> **ago said:**
> [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

thanks for the link! :) i'll be sure to read it...especially after obtaining the result i just obtained running the disk check as u said!!!

---

### Post by damis648 on 2008-11-25
> **Jammanuser said:**
> i would be thankful if u do not suggest a stupid disk check again!!! :mad:

Do not blame anybody for suggesting it, it is just the obvious choice if there seems to be a filesystem error. Do not bite the hand that feeds you. Back to the problem, it sounds you might have a serious issue here, with Windows or its filesystem. Now, did you run `chkdsk /r` or just `chkdsk?`?

---

### Post by Jammanuser on 2008-11-25
> **damis648 said:**
> Do not blame anybody for suggesting it, it is just the obvious choice if there seems to be a filesystem error. Do not bite the hand that feeds you. Back to the problem, it sounds you might have a serious issue here, with Windows or its filesystem. Now, did you run `chkdsk /r` or just `chkdsk?`?

right! i apologize! i'm just kind of pissed off about it right now...i'll get it over it though! as for whether it was 'chkdsk/r' or just 'chkdsk', its the former!!! chkdsk/r! i typed in that command in my command prompt, and it scheduled it to run chkdsk when i rebooted! and then when i rebooted, and performed the disk check, those r the results i obtained!!! ^^^^

---

### Post by damis648 on 2008-11-25
Hm... can you recall the exact error of the blue screen? Was it 'IRQL_NOT_LESS_OR_EQUAL'?

---

### Post by Jammanuser on 2008-11-25
> **damis648 said:**
> Hm... can you recall the exact error of the blue screen? Was it 'IRQL_NOT_LESS_OR_EQUAL'?

unfortunately no! i'm not sure of the **exact** error on the blue screen, other than that it said that a problem had been detected, and my computer had been shut down to prevent damage to my computer...i think there were a lot of letters and numbers, but the error u described above doesn't ring a bell!

Sorry! :(

---

### Post by damis648 on 2008-11-25
Can we get a Windows expert in here?? I'm trying to think... sorry, I cannot come up with anything else... can you boot up in safe mode?

---

### Post by Therion on 2008-11-25
What would really be helpful would be the error code from the BSOD itself.  If the BSOD is repeatable then the next step is to stop XP from automatically rebooting so we can capture the error code, other wise diagnosing a BSOD is nigh impossible.  

To stop the "Auto-Reboot" function:

Go to Start/Control Panel/System
Go to **Advanced**
Under the Startup and Recovery section, click **Settings**
Under **System Failure** un-check "Automatically restart"

Off the top of my head I can tell you that BSOD's are frequently caused by corrupted video drivers - that's one possibility - but without the specific error code it's not possible to speculate further.  You could attempt to do a System Restore, basically rolling back your system's user settings to a prior, known good, state.  Running chkdsk /r was good advice and still is.  Running SFC (System File Check) from the Run command might be good if you have you Windows install CD.

---

### Post by Jammanuser on 2008-11-25
> **damis648 said:**
> Can we get a Windows expert in here?? I'm trying to think... sorry, I cannot come up with anything else... can you boot up in safe mode?

nope!!! i can't! i get the same error...i.e. the one that said: "crc error" and on the next line "system halted"!

it really sucks!!! :(

---

### Post by Jammanuser on 2008-11-25
> **Therion said:**
> What would really be helpful would be the error code from the **BSOD** itself.  If the BSOD is repeatable then the next step is to **stop XP** from automatically rebooting so we can capture the error code, other wise diagnosing a BSOD is nigh impossible.  

To stop the **"Auto-Reboot"** function:

Go to Start/Control Panel/System
Go to **Advanced**
Under the Startup and Recovery section, click **Settings**
Under **System Failure** un-check "Automatically restart"

Off the top of my head I can tell you that BSOD's are frequently caused by corrupted video drivers - that's one possibility - but without the specific error code it's not possible to speculate further.  You could attempt to do a System Restore, basically rolling back your system's user settings to a prior, known good, state.  Running chkdsk /r was good advice and still is.  Running SFC (System File Check) from the Run command might be good if you have you Windows install CD.

what does "BSOD" stand for??? i'm sorry! i don't know what it means! :) and i have Vista, not XP, at the moment!! and what did u mean by "auto-reboot function"???

---

### Post by Therion on 2008-11-25
> **Jammanuser said:**
> what does "BSOD" stand for??? i'm sorry! i don't know what it means! :) and i have Vista, not XP, at the moment!! and what did u mean by "auto-reboot function"???
Sorry for that, I should have read more closely.  Since you're running Windows Vista, I'm sorry, but I can't be of any help.  Vista is a totally different animal than XP.

BSOD, by the way, stands for Blue Screen Of Death.  That's the catchy term for a what Windows calls a "Fatal Error", that being that one effectively crashes your system.

Sorry for the confusion and good luck with your problems.  I wish I could be of some help.

---

### Post by Jammanuser on 2008-11-26
> **Therion said:**
> Sorry for that, I should have read more closely.  Since you're running Windows Vista, I'm sorry, but I can't be of any help.  Vista is a totally different animal than XP.

BSOD, by the way, stands for Blue Screen Of Death.  That's the catchy term for a what Windows calls a "Fatal Error", that being that one effectively crashes your system.

Sorry for the confusion and good luck with your problems.  I wish I could be of some help.

ok...no problem!!! i like that term by the way! its a good description of it!!! 

Still waiting for a solution to the CRC error...

Next person! :lolflag:

---

### Post by tmsbrdrs on 2009-01-03
crc errors are never a good thing. CRC stands for cyclical redundancy check and on one machine I was using it meant that my mother board was bad. Your best bet at the moment would be to take it in to a computer repair place, one of the small shops where the guys are willing to talk to you who have extra parts in a box somewhere and who could build a new computer in their sleep is your best bet. Let them know exactly what you're seeing and when it started. My best guess would be that there is a problem along that particular line. It's either in your hard drive or on your mother board. Just to be safe, go to [www.iobit.com](www.iobit.com) and download advanced systemcare, I think that's what it's called now anyway. Run this and it will at least eliminate some of the potential problems. Also, run an antivirus program and an antimalware program, I recommend malwarebytes antimalware just because it's a system saver and it's compatible with vista. If this is software based in any way that was downloaded, the combination of malwarebytes, advanced systemcare and an antivirus program of your choice will take care of it. Otherwise, it's something you'll need to get fixed by the professionals for now. Hopefully it's just a hard drive issue if it is, those are cheap these days and since you're going to Ubuntu anyway, you might as well start fresh. You can always ask if they can pull your info off the drive somehow unless you're one of the smart ones who make a backup of the important stuff.
By the way, if my system crashes, I'm screwed. I'm smart, but I'm lazy.

---

