---
title: "Freeze After Login"
date: 2008-11-05
forum: General Help
---

### Post by jblah on 2008-11-05
Hello all. I'm kinda new to the world of ubuntu. I've tried ubuntu previously a while ago and am finally coming back to it. Yesturday I put in Ubuntu 8.04 in one of my older computers. I am now having issues after I login.

I used the ISO downloaded from the ubuntu to install 8.04 yesturday. It worked for a while after my updates and all that. Then for some reason, just as I was going to change the screensaver, horizontal lines came across the screen and it froze. I tried restarting it and the problem persisted.

I thought i had seriously messed it up so I reinstalled 8.04 today. It installed fine and I was able to login the 1st time. I downloaded updates and then was restarting after the updates as recommended and again I have the same horizontal lines show up after I login. I'm able to put in the username and password and hear the login music, however I don't see the bars at the top or the bottom. It freezes up just before then. I'm guessing this is a GNOME error? When I was running the LIVE CD while trying to solve this problem I also came across the error:

Error starting GNOME
Last error message was: did not receive a reply...


I'm not sure what the issue is. My old computer is a Celeron 1.4 (hp pavilion 512n). Any help will be greatly appreciated because I'm at a loss and have been looking for solutions on google but haven't been able to find one. 

Thank you.

---

### Post by Peter09 on 2008-11-05
TRy recovery mode - hit ESC at the grub prompt and select recovery mode. At the next menu select drop into command shell. The type startx at the prompt and hit enter. That may bring up a working GUI.

Shutdown, reboot and see what happens

---

### Post by jblah on 2008-11-05
thank you for your reply. I did what you said. I went into recovery mode and from cmd line i typed in startx and it loaded up ubuntu. i then logged out and typed in reboot at cmd line to restart it and I still got the same problem when i ran in normally out of recovery mode. 

do you have any other suggestions and what the cause of the problem might be?

---

### Post by Peter09 on 2008-11-05
Sounds like your gnome configuration is corrupt. You could try going through recovery mode and rename the .gnome directory in your 'real' user directory, save it as gnomesaved. 

Then try rebooting into your 'real' user directory. If you get a problem you can then rename it again to .gnome

---

### Post by jblah on 2008-11-05
Thanks for the reply and your willingness to help. I tried to find the .gnome folder when i started it up in recovery mode. However, I was unable to do so.

When I tried to SWITCH user in recovery mode (after i typed in startx) it gave me the error: GNOME display Manager not running. You might be using KDM, CDM or xdm. 

So I guess GNOME is not running at all for some reason. I'm not sure what triggered it to close. All i did previously (before) was change my background image. 

Is there some way i can reenable GDM? Thank you.

---

### Post by Peter09 on 2008-11-05
No, sorry did not make myself clear. In recovery mode you need to navigate to your normal user using nautilus. You need to move through the file system.

or

try the command at the recovery command prompt

```
sudo mv /home/<your user name>/.gnome /home/<your user name>/gnomesaved
```
where <your user name> is your login user name

---

### Post by jblah on 2008-11-05
hello. i tried doing what you stated. however, its saying "directory not found" there doesn't seem to be anything under the user name as a .gnome. very strange or i'm probably doing something wrong.

---

### Post by Peter09 on 2008-11-05
Just to check

```
sudo*mv*/home/<your user name>/.gnome*/home/<your user name>/gnomesaved
```

I have replace spaces with stars, when you do this command make sure that the spaces are correct

---

### Post by jblah on 2008-11-05
hello again. thank you for your patience with me.

that is what i had actually. i redid it again to make sure that i was right and i get the same problem which claims that /home/username/.gnome is not a valid directory. 

i don't have a problem with reinstalling ubuntu..however, i'm afraid that this same thing with result after i try to update. i'm not sure if it was because of the updates or something else that this error resulted.

---

### Post by Peter09 on 2008-11-06
Hi,
username = the name you login with

is that what you used?

---

### Post by ua6icab7 on 2008-11-06
Hot Promotion Storm of [WOW Gold](http://www.gold4power.com/) is Sweeping fiercely all around! Recently,we have tailored the unique World of Warcraft gold promotion for our valued customers.You could feel surprised that our [WoW gold](http://www.gold4power.com/) price are the cheapest on all the servers,especially on US server!Purchasing cheap WoW Gold from Gamelee.com is 100% safe; your account will not be suspended or banned for purchasing World of Warcraft Gold from us. Perfect Runescape Summoning! Recently we are offering the new skill of Runescape--Summoning.For all our valued Runescape Fans,it's no doubt that could be an unparalleled news.Do you want to miss this new skill?That can make you weather all the chanllenge and become the big cheese in Runescape!Plz trust us that our price is depend on the market,even cheaper than others,we will never set it random !Let's enjoy the hot storm you have never been to!

---

