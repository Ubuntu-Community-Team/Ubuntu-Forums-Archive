---
title: "Ubuntu 12 clean install. Some issues"
date: 2012-10-24
forum: Hardware
---

### Post by elesbb on 2012-10-24
Hello, i have just clean installed my ubuntu partition with Ubuntu 12. I ran into two issues which i had with ubuntu 11 (figured they'd be fixed by now) but anyhow, doing the same steps as with ubuntu 11 only fixed my brightness issue.

However, the second issue i face is with my WiFi card not reconnecting after it resumes from sleep state. I tried to disable the n functionality as i did with 11 to fix this issue, but it didnt work, plus i would like to keep my n functionality as we now have an n router. 

My other concern, is the HDD HP protect smart feature. When the computer would get bumped, my HDD would park itself to avoid damage to the data plater, however, in ubuntu no such thing happens. 

I appreciate all your help! Thank you

---

### Post by rg4w on 2012-10-24
> **elesbb said:**
> ...the second issue i face is with my WiFi card not reconnecting after it resumes from sleep state.
You didn't mention which 12 you're using, 12.04 or 12.10.

FWIW, I had an intermittent problem with wifi not reconnecting under 12.04 which has not yet been evident since I upgraded to 12.10.

I should note, however, that I've only had 12.10 installed for a few days, so it's possible that I may see the problem in the future. 

Wifi seems to be one of those areas in which manufacturers exercise a surprising diversity for something that's supposed to be a standard.

It may be helpful if you could note the specifics of your wifi controller so we can maybe determine if your sleep issues have been addressed in previous bug reports.

---

### Post by elesbb on 2012-10-24
> **rg4w said:**
> You didn't mention which 12 you're using, 12.04 or 12.10.

FWIW, I had an intermittent problem with wifi not reconnecting under 12.04 which has not yet been evident since I upgraded to 12.10.

I should note, however, that I've only had 12.10 installed for a few days, so it's possible that I may see the problem in the future. 

Wifi seems to be one of those areas in which manufacturers exercise a surprising diversity for something that's supposed to be a standard.

It may be helpful if you could note the specifics of your wifi controller so we can maybe determine if your sleep issues have been addressed in previous bug reports.

Is 12.04 lts. I figured since its the "stable" release it would contain less bugs.

---

### Post by ahallubuntu on 2012-10-24
If you want help with WiFi issues, you need to provide specific details about the wireless card.  Open a terminal and type

```
sudo lshw -C network
```

and show the results here.  There may be known issues with your wireless card that can be worked around.

Your hard drive apparently has a shock motion sensor that can be monitored to stop the drive temporarily.  (Or the motherboard has the sensor.)  I'm guessing the software to monitor that is Windows-specific (something created by HP) that isn't going to work in Linux.  Still, this is not a standard feature of lots of laptops, anyway.  Lots of us live without motion sensors (even in Windows) on our cheaper laptop hard drives and get by, though it would be a nice bonus to have.

There have been some attempts to implement this kind of shock sensor protection in Ubuntu but I'm not sure how standard it is.  Try googling.  It may be too manufacturer-specific to have been generally implemented.  HP, of course, doesn't care about Linux so isn't going to help.

---

### Post by ahallubuntu on 2012-10-24
> **rg4w said:**
> 
Wifi seems to be one of those areas in which manufacturers exercise a surprising diversity for something that's supposed to be a standard.


A big part of the problem is that some manufacturers like Broadcom provide no end user support for their products and don't release drivers for them.  Broadcom, for example, only releases drivers for most of its products to computer manufacturers who only produce Windows or Mac drivers.  Getting Linux support from them requires a lot more work from Linux developers in those cases.  And there are "purity" issues with some of the drivers that do get produced, because Linux developers can't see the source code and don't know what's inside. 

Intel probably has the best Linux support for its wireless cards - they generally work automatically, though there have been a few cases where N wireless doesn't work reliably and users have been urged to downgrade to G (I haven't had this problem with any of my Intel wireless cards personally).  I use N speeds for local networking all the time and do need it - it's at least 2X faster than G and can save a lot of time in transferring files.

It is kind of baffling that Canonical (producer of Ubuntu) hasn't come up with a more robust wireless setup tool that simplifies getting your wireless card to work.  This has got to be one of the more frustrating barriers to user acceptance of Ubuntu on laptops.

---

### Post by nah40 on 2012-10-24
> **elesbb said:**
> Hello, i have just clean installed my ubuntu partition with Ubuntu 12. I ran into two issues which i had with ubuntu 11 (figured they'd be fixed by now) but anyhow, doing the same steps as with ubuntu 11 only fixed my brightness issue.

However, the second issue i face is with my WiFi card not reconnecting after it resumes from sleep state. I tried to disable the n functionality as i did with 11 to fix this issue, but it didnt work, plus i would like to keep my n functionality as we now have an n router. 

My other concern, is the HDD HP protect smart feature. When the computer would get bumped, my HDD would park itself to avoid damage to the data plater, however, in ubuntu no such thing happens. 

I appreciate all your help! Thank you

I have had the same 2 issues with an HP DV6T since installing Ubuntu 11.04. Still have it in 12.10. I spent many hours trying to fix this and finally just gave up.

---

### Post by ahallubuntu on 2012-10-24
> **nah40 said:**
> I have had the same 2 issues with an HP DV6T since installing Ubuntu 11.04. Still have it in 12.10. I spent many hours trying to fix this and finally just gave up.

A quick look at your posting history does not show any specific description of your problem, just a lot of replies on other threads saying you have the same kind of problem.

If you want help now, I suggest starting a new thread and post the exact wireless card you have (HP uses numerous different wireless cards in the same model).  Try the command

```
sudo lshw -C network
```


I would stick with 12.04 in your case, though, because it is more stable than 12.10 (which just came out), and you are more likely to find a solution that works.  Since your laptop is a few years old and not brand new, you should not need the latest/greatest version of Ubuntu just to use your wireless.

Sadly, because you have an HP laptop, one easy solution that I have on my Dell (replace the wireless card with one compatible with Ubuntu) isn't much of an option for you, because HP whitelists their wireless cards, so you can use only HP-approved wireless cards in your laptop (and only approved for YOUR laptop, not other models of HP laptop!).  If you had a Dell, Acer, Toshiba, etc. I would have suggested spending $10 on eBay to upgrade your wireless card...

---

### Post by elesbb on 2012-10-24
> **ahallubuntu said:**
> If you want help with WiFi issues, you need to provide specific details about the wireless card.  Open a terminal and type

```
sudo lshw -C network
```and show the results here.  There may be known issues with your wireless card that can be worked around.

Your hard drive apparently has a shock motion sensor that can be monitored to stop the drive temporarily.  (Or the motherboard has the sensor.)  I'm guessing the software to monitor that is Windows-specific (something created by HP) that isn't going to work in Linux.  Still, this is not a standard feature of lots of laptops, anyway.  Lots of us live without motion sensors (even in Windows) on our cheaper laptop hard drives and get by, though it would be a nice bonus to have.

There have been some attempts to implement this kind of shock sensor protection in Ubuntu but I'm not sure how standard it is.  Try googling.  It may be too manufacturer-specific to have been generally implemented.  HP, of course, doesn't care about Linux so isn't going to help.

Ahh yay replies from great user! :D sorry for the delayed reply. But as of now im in windows. But i made a text file of lspci and here is the wireless.

07:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
And that sucks about the Hard drive. I do remember when installing windows that i had to install what i can remember what an HP ProtectSmart software. I just googled that now and looks to be the protection that stops the HDD. And you are right about the sensor being on the mobo. As ive had other HDDs in this machine and they all did the orange light with a "chunk" (drive are parking itself) upon sudden movement. 

> **ahallubuntu said:**
> A big part of the problem is that some manufacturers like Broadcom provide no end user support for their products and don't release drivers for them.  Broadcom, for example, only releases drivers for most of its products to computer manufacturers who only produce Windows or Mac drivers.  Getting Linux support from them requires a lot more work from Linux developers in those cases.  And there are "purity" issues with some of the drivers that do get produced, because Linux developers can't see the source code and don't know what's inside. 

Intel probably has the best Linux support for its wireless cards - they generally work automatically, though there have been a few cases where N wireless doesn't work reliably and users have been urged to downgrade to G (I haven't had this problem with any of my Intel wireless cards personally).  I use N speeds for local networking all the time and do need it - it's at least 2X faster than G and can save a lot of time in transferring files.

It is kind of baffling that Canonical (producer of Ubuntu) hasn't come up with a more robust wireless setup tool that simplifies getting your wireless card to work.  This has got to be one of the more frustrating barriers to user acceptance of Ubuntu on laptops.

And yes this is the reason i booted back to windows. For i need my wifi! I do love ubuntu though. I am a Linusoft user xD never apple though ^^





As i stated in the OP, i have made a thread about this long time ago when ubuntu 11 came out and had it solved by diabling the N function. But as you have said, N is extremely fast and now that we have an N router, i would prefer to keep N capabilities. But thank you for your awesome reply. I hope the lspci was enough for you. Btw i am a slightly advanced user. I am totally familiar with grep and the command line so if you have any other codes for me to run just let me know!

THANKS!

---

### Post by funicorn on 2012-10-24
If you really want to try, add script into /etc/pm/sleep.d/ to restart your network-manager service so that it would reconnect your wireless network.

The rule of such a file is simple, pm-suspend is run with different actions, which for your case I guess is resume: case $1 in resume and service network-manager restart should take care of your problem.

P.S. If you can post the scripts in /etc/pm/sleep.d and /usr/share/pm/sleep.d, if any, it might help.

And also 'lsmod |grep mac80211' is key to determine what wifi driver is being used in your system. In your case it might be iwl*

---

### Post by elesbb on 2012-10-24
> **funicorn said:**
> If you really want to try, add script into /etc/pm/sleep.d/ to restart your network-manager service so that it would reconnect your wireless network.

The rule of such a file is simple, pm-suspend is run with different actions, which for your case I guess is resume: case $1 in resume and service network-manager restart should take care of your problem.

P.S. If you can post the scripts in /etc/pm/sleep.d and /usr/share/pm/sleep.d, if any, it might help.

And also 'lsmod |grep mac80211' is key to determine what wifi driver is being used in your system. In your case it might be iwl*

Ah thanks. I shall try that, however restarting the service wouldnt that make connecting take longer? oh and i am pretty sure its iwl driver being used. but i'll reboot quick and check

---

### Post by elesbb on 2012-10-26
Bumping this up cause i need this fixed

---

### Post by ahallubuntu on 2012-10-26
After resuming from suspend, my Dell laptop sometimes takes up to a minute on its own to re-scan/re-connect to my wireless network.  I have gotten in the habit of quickly disabling and re-enabling the wireless card from the keyboard.  On my Dell, it's Fn+F2.  I do that twice and then wireless comes up pretty quickly.  I guess I could find it a pain but I am so used to doing that now that I never think about it.

If you simply disable/re-enable your wireless card like I do after resume, does it then re-connect?  I guess if your laptop uses a little toggle switch to disable/enable WiFi instead of the key combo that my Dell uses, it could be a bit more annoying to do that after resume...

---

