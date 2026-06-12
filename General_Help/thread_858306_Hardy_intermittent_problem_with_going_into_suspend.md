---
title: "Hardy intermittent problem with going into suspend"
date: 2008-07-13
forum: General Help
---

### Post by MadeTheSwitch on 2008-07-13
Hello,

Around 3 months ago I went cold turkey and switched from WinXP to Hardy. First of all, I want to say I love it; when things work well (which is most of the time), my user experience is significantly improved over Windows. However, I have a small number of issues that are driving me to extreme frustration, the only thing holding me from switching back is a sense of a dread I develop from thinking about doing so.

Following is one of them, the number 1 frustration and priority. I am not sure how to go about figuring this one out, but I've spent the past two months and haven't been able to find anything, although there are a lot of discussions around the general topic. Any assistance would be greatly appreciated.

Hardware: Lenovo X61s (type 7668-CTO)
OS: Ubuntu Hardy, all the latest updates

Summary: when trying to go into "suspend" mode, occasionally the laptop will not complete the suspend action, and will require a reboot. 

Description: the problem occurs when I click on the "suspend" button in the Ubuntu menu, or I close the lid. Most of the time the laptop will suspend properly. However, on occasion it will instead do the following:

1) The laptop will "drop" out of the GUI and switch to text mode. 
2) I am presented with a screen of data.
3) The sleep light starts blinking and continues to do so.
4) The laptop will not complete the sleep action (I've left it overnight in this mode but it did not change). 
5) The CPU, fan etc seem to continue to work normally; certainly, the laptop remains heated and does not cool down, and it is functional to a degree. See side note #4.
6) No matter what I do, I cannot "convince" the laptop to either complete the sleep action, or return from it. It stays in this "zombie" mode until I do a hard reboot. 

Side notes: 
1) Hibernate works properly, although I use it a lot less so it may just be lucky.
2) I used to have a problem with freezes in the screensaver. I though it was related. However, changing my screen saver from the walking ant to the matrix seems to have cured that problem. I note it just in case it IS somehow partially related. 
3) I followed instructions elsewhere to reduce the number of "harddrive polls". I don't know if this is related either, but I used the "99-hdd-ugly-fix" solution posted elsewhere, and using 180 on AC and 128 on battery. Again, I don't know if it's related but I am mentioning it since it makes that one part of my install "non-standard". 
4) I tried CTRL-ALT-F1 to open a console and log in. This works fine. I can travel around the file system in command line. However, I cannot seem to perform any SUDO actions; they "hang" the console, and I then have to open another console to do anything else. This includes trying to restart GDM, trying to reboot or shutdown properly, or pretty much any other SUDO action. 
5) The only consistent remedy, if you will, is that I can use the REISUB trick to disable everything. However, the B part does NOT work. That is, the machine claims it is "resetting", but nothing further happens; the sleep light is still blinking, and text is still on the screen, etc. I still have to manually press the power button long enough to perform a "hard" reset. 
6) I can't find any indication in the log files that something went wrong. I've looked at all of them even when in console mode; nothing seems to be written to the logs. I'm happy to attach log files if anybody wants specific ones; this happens often enough that a new crash like this will definitely occur in the next 3-4 days. 
7) The problem is intermittent. It can happen several times a day and then not happen in several days. 

Again, thank you in advance for any assistance.

---

### Post by MadeTheSwitch on 2008-07-13
It's amazing how active this forum is... but now my question is buried on page 8 or something and nobody's ever going to see it... 

PleaseBegBegPlease? Anyone able to point me anywhere?

---

### Post by Redrazor39 on 2008-07-13
This is horrible. 

I have the problem in which suspend will never complete. Still a blinking horizontal cursor.

I don't know what to do, nobody seems to want to help, and fixing suspend/hibernate is still the #1 idea on ubuntu brainstorm and not even marked as "work in progress"

---

### Post by mempman on 2008-07-13
> **MadeTheSwitch said:**
> Hello,

Around 3 months ago I went cold turkey and switched from WinXP to Hardy. First of all, I want to say I love it; when things work well (which is most of the time), my user experience is significantly improved over Windows. However, I have a small number of issues that are driving me to extreme frustration, the only thing holding me from switching back is a sense of a dread I develop from thinking about doing so.

Following is one of them, the number 1 frustration and priority. I am not sure how to go about figuring this one out, but I've spent the past two months and haven't been able to find anything, although there are a lot of discussions around the general topic. Any assistance would be greatly appreciated.

Hardware: Lenovo X61s (type 7668-CTO)
OS: Ubuntu Hardy, all the latest updates

Summary: when trying to go into "suspend" mode, occasionally the laptop will not complete the suspend action, and will require a reboot. 

Description: the problem occurs when I click on the "suspend" button in the Ubuntu menu, or I close the lid. Most of the time the laptop will suspend properly. However, on occasion it will instead do the following:

1) The laptop will "drop" out of the GUI and switch to text mode. 
2) I am presented with a screen of data.
3) The sleep light starts blinking and continues to do so.
4) The laptop will not complete the sleep action (I've left it overnight in this mode but it did not change). 
5) The CPU, fan etc seem to continue to work normally; certainly, the laptop remains heated and does not cool down, and it is functional to a degree. See side note #4.
6) No matter what I do, I cannot "convince" the laptop to either complete the sleep action, or return from it. It stays in this "zombie" mode until I do a hard reboot. 

Side notes: 
1) Hibernate works properly, although I use it a lot less so it may just be lucky.
2) I used to have a problem with freezes in the screensaver. I though it was related. However, changing my screen saver from the walking ant to the matrix seems to have cured that problem. I note it just in case it IS somehow partially related. 
3) I followed instructions elsewhere to reduce the number of "harddrive polls". I don't know if this is related either, but I used the "99-hdd-ugly-fix" solution posted elsewhere, and using 180 on AC and 128 on battery. Again, I don't know if it's related but I am mentioning it since it makes that one part of my install "non-standard". 
4) I tried CTRL-ALT-F1 to open a console and log in. This works fine. I can travel around the file system in command line. However, I cannot seem to perform any SUDO actions; they "hang" the console, and I then have to open another console to do anything else. This includes trying to restart GDM, trying to reboot or shutdown properly, or pretty much any other SUDO action. 
5) The only consistent remedy, if you will, is that I can use the REISUB trick to disable everything. However, the B part does NOT work. That is, the machine claims it is "resetting", but nothing further happens; the sleep light is still blinking, and text is still on the screen, etc. I still have to manually press the power button long enough to perform a "hard" reset. 
6) I can't find any indication in the log files that something went wrong. I've looked at all of them even when in console mode; nothing seems to be written to the logs. I'm happy to attach log files if anybody wants specific ones; this happens often enough that a new crash like this will definitely occur in the next 3-4 days. 
7) The problem is intermittent. It can happen several times a day and then not happen in several days. 

Again, thank you in advance for any assistance.



Power issues with laptops are tough to get working 100% with ubuntu because most hardware manufacturers provide zippo information in regards to power settings to the ubuntu community.  

With my laptop I have suspend that works well, but hibernate never works.  Its very touchy and basically there is no silver bullet for your problems.  I would recommend you do what I did: search the internet for ubuntu and your laptop model.  It is highly likely that someone was able to maximize configurations for you laptop and has posted a solution online somewhere.  Why struggle and re-invent the wheel when you don't have to. 


Also, I think you didn't get a lot of responses to you original posting is because that thing is a dread to read.

---

### Post by MadeTheSwitch on 2008-07-14
> **mempman said:**
> Power issues with laptops are tough to get working 100% with ubuntu because most hardware manufacturers provide zippo information in regards to power settings to the ubuntu community.  

With my laptop I have suspend that works well, but hibernate never works.  Its very touchy and basically there is no silver bullet for your problems.  I would recommend you do what I did: search the internet for ubuntu and your laptop model.  It is highly likely that someone was able to maximize configurations for you laptop and has posted a solution online somewhere.  Why struggle and re-invent the wheel when you don't have to. 

Also, I think you didn't get a lot of responses to you original posting is because that thing is a dread to read.

Thank you; I've done many google searches, but I'm trying to them based on the model rather than the problem. One thing I've dug up already is a BIOS update process for the x61s which may end up helping.

Hardy does work out of the box with the x-series, though. 

I thought I did well by including as much detail as possible. I apologize for writing too much.

---

### Post by kecsap on 2008-07-14
I have also X61s with latest Hardy (64-bit), but I don't have any problem with the suspend.

For me, this is my best-Linux-compatible laptop so far.

I have only a small issue with the docking station:

[http://ubuntuforums.org/showthread.php?t=845039&highlight=x61s](http://ubuntuforums.org/showthread.php?t=845039&highlight=x61s)

---

### Post by MadeTheSwitch on 2008-07-14
> **kecsap said:**
> I have also X61s with latest Hardy (64-bit), but I don't have any problem with the suspend.

For me, this is my best-Linux-compatible laptop so far.

I have only a small issue with the docking station:

[http://ubuntuforums.org/showthread.php?t=845039&highlight=x61s](http://ubuntuforums.org/showthread.php?t=845039&highlight=x61s)

Thanks.

Yes, I know; the laptop works really well with Ubuntu, and I am extremely happy with it - except for a very small list of problems. Unfortunately, two of those are so severe that they might drive me back to WinXP if I can't solve them. This is one.

---

