---
title: "Fully disabling the close-lid trigger on laptop?"
date: 2010-01-09
forum: Hardware
---

### Post by gewone on 2010-01-09
Hi!

I've got an ancient Thinkpad. It runs quite well, except for one thing. The signal sent out by that little plastic button that gets pressed when lid is closed, is messy. About 2 out of 5 times, closing and re-opening the lid causes the screen never to go on again. Constantly blank, that is.

However, I then tried remotely SSH:ing into the box, and that won't answer neither, so some malicious IRQ crash (or suchlike) has obviously occured, although LCD screen is blank so I couldn't "debug" even if I wasn't such a novice (that I am) ;^

The laptop can stand with a constant flytime on weeks, as long as I don't [physically] close/re-open the lid, since this is where sh*t goes wrong.


Now, for y'all "TLDR":ers out there, skip to this part.

I was happy when I noticed that Ubuntu comes with a configuration applet (Power prefs) for setting desired action for lid close. However(!), I just wish that there was an option "Do nothing!" -- eg. don't blank the screen, but do exactly nothing.

Is there any way to get this behaviour? Some sort of manual line in some configuration file? Even tho the option isn't provided by GUI..? Or is [really] my only option to go grab the cutting pliers from the toolbox, and simply physically eliminate that little plastic button? ;P


Regards~

And ty for all answers.

---

### Post by Alex!!!! on 2010-01-09
So, you mean you close the lid and it might not turn on? What do you mean by saying 'button'? You mean the lid presses it and doesn't deactivate? If not, there is no 'do nothing', it is in Vista... But, DO NOT EVER TOUCH VISTA! You might find some downloadable thingy, but I highly doubt that. You may PM or e-mail me and provide more info. I might find something out.

---

### Post by kesman on 2010-01-09
I would also like to know how to completely disable the lid performance, since I'm using my laptop as a media machine with my tv as the primary display, and I would like to keep the lid closed all times. I'll be searching for the solution and post here if I found one.

EDIT:
I found it. Here are the steps:
ALT+F2 and type gconf-editor
Then browse to apps/gnome-power-manager/buttons and change the lid_ac value to "nothing" without quotes. You can change the lid_battery to nothing as well if you want.
I hope this helps you!

---

### Post by buster2209 on 2010-01-09
System > Preferences > Power Management

There will be two tabs; "On AC Power" and "On Battery Power"

Within each tab is the ability to select what the laptop does when the lid is closed > "When laptop lid is closed:"

Choose what you want!

---

### Post by kesman on 2010-01-10
How about you read the first post again? There's no "do nothing" option in the power management.

---

### Post by JoJerome on 2010-01-10
**Need help with this here!**

Just installed Karmic on a Compaq laptop. When the lid is closed it completely loses the ability to boot (quite a headache finding a fix for that).

Tried the fix above:
alt+f2 then typing gconf-editor
I get nothing. No response at all. "Enter," pulling the drop down menu, nothing.

Tried the other fix above:
System -> Preferences -> Power Management.
There is no such option "Preferences -> Power Management.
Closest I could find is "System Settings -> Display -> Power Control."
But the only options are how many minutes until standby, suspend, power-off. Nothing about laptop lids.

Need help! Ideally I'd like to be able to set closing the laptop to initiate sleep mode. At the least I would like closing the lid to not kill Kubuntu altogether.


;)

---

### Post by Schrodinger's Cat on 2010-01-12
thank you thank you thank you! worked perfectly, now I can destroy my HD at will by walking around with it runnning...JK... but at least I can close it and walk away without it going buh-bye...

---

### Post by gewone on 2010-01-15
I tried Kesman's solution, without any luck though. However, it seems that my problems may be hardware-related. I also entered Thinkpad BIOS and disabled "Screen blank" aswell as "Suspend on close lid", also that gconf-editor setty, like I said, wo/ any luck ;(

However, my internal LCD is acting so weird. I close my lid, wait a couple of seconds, and re-open it, then it came back (I was getting my hopes up at this time). However, no sucess until the action is considered somewhat stable, so I reprocessed. This time, I got some "?" popup on-desktop about CRT not being able to reconnect right, something like that. Also, my whole display was "shivering" -- badly. Shaking horizontally, that is, Like, shaking 5-7 centimeters back and forth.

Gasp. I thought that it perhaps would re-connect stable if I reprocessed once more. So I dod. The shaking remained after closing/re-opening the lid though. I reprocessed a forth time, this time my display did not come back up after re-opening the lid. It was blank, and I reckon (by LAN activity check) that the system was prolly frozen "beneath" aswell, since I couldn't SSH in. Hard reset was my only solution. Sigh. I will prolly never get this ship rocking smoothly, I still can't help to wonder what it could be though..

---

### Post by rahulkumarc on 2010-01-15
gewone - looks like you may have a hardware issue, the shaking says that theres something loose inside your Thinkpad, my guess would be the cable from the LCD to the motherboard.

I am sorry to say but its time to bring the TP to a hardware guy.

---

### Post by gewone on 2010-01-24
Actually, I think I need to re-bump this one.

I've come to narrow down the issue further more. It seems to be X-related after all. As I described earlier, problem occurs after close-reopen lid, and not always.

As I've running a few services on this laptop (trying to have it act as co-server, sort of), I was not very pleased with this "unreliable" behavior. I started wondering if X could have something to do with it. So I searched for threads on how to "terminate" X. Finally got the 'sudo service gdm stop' command, and executed it.

Then, when lying in 'oldschool style' console only, I can press-release the little close-lid-trigger-button repeatedly. When I press it, screen is blank; when I release it, screen comes back alive.

So, it may not be a hardware issue after all. Look, when I get these horizontal shakes n all, I notice an error msg "Cannot config CRTC 57" (the letters can be somewhat different, but the number is 57 for sure).

So, you advanced guys out there. Please tell me if I could get X to act completely "not at all" on close lid? Or just blank/"unblank" it, as in console..? I did set the values to "nothing" for those two values in config (described earlier in this thread), but it doesn't seem to do the trick.

Any other ideas would be much appreaciated. My current work-around is to only 'startx' when I need to be at the laptop physically, and then terminate X before I close the lid. Awergh..

---

### Post by AGlory on 2010-03-15
I was having the exact same problem on my eeepc in Lucid Lynx (shivering and all), so I thought I'd chime in with my solution.

First off, the inability to set the lid to "do nothing" in power management is damned annoying.  What makes matters worse is that the functionality still exists, but has been missing from the graphical power management since intrepid.  Here's how to put it back:
```

gconftool-2 --type string --set  /apps/gnome-power-manager/buttons/lid_ac  "nothing"
gconftool-2 --type string --set  /apps/gnome-power-manager/buttons/lid_battery  "nothing"
```No need to reboot, and that puts the "do nothing" back into the power management frontend and selects it by default.  

This worked immediately, but I noticed that if I left the lid closed for a few minutes, the screen would be blanked again upon opening.  After some digging, I found the screensaver to be the culprit.  Make sure that your screensaver DOES NOT lock your session when it engages.  For whatever reason, that mechanism seems to act as a hook for this bug.

Hopefully this works for you!

---

### Post by Pougnet on 2010-03-15
You could try the other methods listed aboce or you could do it the old fashion way...if it is a little ost like peice of plastic that goes down and pushes a button to sense it has closed you could get some tin snips and cut it off if you never want it to work again.

---

### Post by gigdaddy on 2010-03-15
> **AGlory said:**
> I was having the exact same problem on my eeepc in Lucid Lynx (shivering and all), so I thought I'd chime in with my solution.

First off, the inability to set the lid to "do nothing" in power management is damned annoying.  What makes matters worse is that the functionality still exists, but has been missing from the graphical power management since intrepid.  Here's how to put it back:
```

gconftool-2 --type string --set  /apps/gnome-power-manager/buttons/lid_ac  "nothing"
gconftool-2 --type string --set  /apps/gnome-power-manager/buttons/lid_battery  "nothing"
```No need to reboot, and that puts the "do nothing" back into the power management frontend and selects it by default.  

This worked immediately, but I noticed that if I left the lid closed for a few minutes, the screen would be blanked again upon opening.  After some digging, I found the screensaver to be the culprit.  Make sure that your screensaver DOES NOT lock your session when it engages.  For whatever reason, that mechanism seems to act as a hook for this bug.

Hopefully this works for you!

Dude, if you ever find yourself in Arlington, Texas, I owe you a beer.  Many thanks!

---

