---
title: "Cannot login after update"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by thatsPipe on 2009-11-11
After today's update, I can no longer log into my kde desktop. My computer boots up fine and loads kdm but once I enter my password and hit enter, the screen goes black for a moment and then just goes back to the kdm login screen again. 

I have an NVidia card that I compile the drivers myself but they don't appear to be the problem (I tried several different versions that I have saved on my computer but no difference.) I'm figuring this is not something wrong with my graphics drivers but probably with kdm or kde itself. 

Checking /var/log/syslog after attempting to login shows the following:

localhost kdm_greet[6102]: Cannot load /usr/share/kde4/apps/kdm/faces/.default.face

I've also tried starting kde from the tty using 'startx' but no luck. It just comes back to the commandline with the last line saying 'ddxSigGiveUp: Closing log' The only error that I see in /var/log/Xorg.0.log is:

(EE) Logitech G9x Laser Mouse: failed to initialize for relative axes.

Checking out /var/log/kdm.log I found the following lines:

(EE) Failed to load module "type1" (module does not exist, 0)
(EE) Failed to load module "freetype" (module does not exist, 0)
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) Logitech G9x Laser Mouse: failed to initialize for relative axes.
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) XKB: No components provided for device Virtual core keyboard
[config/dbus] couldn't register object path
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server



Anybody have any ideas of what is wrong? I need to get this computer back up and running ASAP.

---

### Post by thatsPipe on 2009-11-11
So I installed the 'ubuntu-desktop' package with aptitude and was able to log into a gnome desktop through gdm. Trying to login to gnome with kdm resulted in the same behavior (black screen for a sec then back to kdm). Logging into kde from gdm works so I'm pretty certain at this point that the problem is with kdm itself. 

At this point, its not a huge issue that I need to use gdm instead of kdm but does anybody have any ideas for debugging this issue? I've tried reinstalling kdm from the commandline ('aptitude reinstall kdm') but no luck.

---

### Post by Rumtum Tugger on 2009-11-12
I have the same problem, but why call it "not a big issue"? I consider a problem that renders a system totally unusable as fairly critical!

Regards,
Tugger

> **thatsPipe said:**
> So I installed the 'ubuntu-desktop' package with aptitude and was able to log into a gnome desktop through gdm. Trying to login to gnome with kdm resulted in the same behavior (black screen for a sec then back to kdm). Logging into kde from gdm works so I'm pretty certain at this point that the problem is with kdm itself. 

At this point, its not a huge issue that I need to use gdm instead of kdm but does anybody have any ideas for debugging this issue? I've tried reinstalling kdm from the commandline ('aptitude reinstall kdm') but no luck.

---

### Post by carlosfehr on 2009-11-13
I get the same problem in my laptop, that was working pretty well, after this morning update, and I cannot log into kde...
anybody has some idea wath's happening?
It has some relation with the nvidia drive or is only a problem with kdm!??
Any ideas welcome
I made dpkg-reconfigure kdm... and nothing good
also i made service kdm... and nothing...

any help around
regards

---

### Post by carlosfehr on 2009-11-14
Hello
I reached to start the machine via startx, and I found some problems with xsane, and some crashings with konqueror,inxsane didn't recognize the scanner, but i reached to by changing the permissions to the usb, (today I did it again).
This only in case that can help to the people to reach the bug.
but the login screen dont let me go further.. it crashes to the black screen!!!
thanks
carlos

---

### Post by miscojones on 2009-11-14
I have the same problem after yesterday's "automatic update"...
I shutted down the PC and this morning...: TA-DAAAA!" Can't login on my user account

As I have created another (desktop only)  user some days ago, I could login with that second one with no problem, but my "first choice" user remains looping between login screen -blank secren-login screen

This kind of problems make me think that  K.K. is at BETA yet, and I  feel like a guinea pig.......

I have never had such kind of problems with J.J. even after all those updates.

It's a problem only related to the new "Login Interface"

For the guys at UBUNTU, on behalf of this "so marvelous" new login screen (I've never seen such a stkinking graphics before)  "when something works fine.......DON'T TOUCH ANYTHING!" 

I've to leave you, pals...I need to reboot with WINDOWS, in order to have my profile working . damnit!

I'll make some tries this afternoon and if I catch a glimpse on anything, I'll post here.

Really annoyed.
Me

---

### Post by zerobaba on 2009-11-15
Guys, I have a similar problem.

 After the updates earlier this week, my KDE desktop refused to come up, and (presumably after a successful autologin) sent me to "reduced graphics" dialog instead. It complained that the freetype module could not be loaded, which is actually harmless as far as I know. The reduced graphics mode itself was unable to boot as well (blank screen lockup), but the preceding dialog (reconfigure graphics / etc) did appear.
 
 Using CLI login, I was able to trace down the problem to kdm as well, so it might just be related to OP's issue. Perheps this is how the same bug manifests if I have autologin configured.

 Anyways, now I boot KDE using gdm (which is a shame, as it does not allow me to shut down from KDE, only logout is available). This is still a serious problem, and I guess it may easily be a showstopper for less experienced users.

---

### Post by lapique on 2009-11-26
I ran the update Jaunty --> Karmic on 2 PC's :
- PC1 : I deleted the old packages when prompted ; everything OK
- PC2 : I did NOT delete the old packages when prompted ; same problem as you, guys

Could it explain ?

---

### Post by chessmani on 2009-11-26
Same problem here... install the latest graphics drivers and keep rebooting. After 3-4 times I can get KDE, maybe it works for you as well.

---

### Post by richardy on 2009-11-26
Hi,
I have exactly the same problem with xubuntu - either i get a login screen but cant get any further or i get the start of the login screen and then everything locks up.

Its enough to send yi back to windoze.

Tried to install new vid drivers (via system -> hardware drivers after logging in thru failsafe gnome) but got a message saying there were no propriety drivers to install.

cheers.

---

### Post by lapique on 2009-11-26
> **richardy said:**
> 
Its enough to send yi back to windoze.
cheers.

I think your are an impulsive man !

Chessmani, could you please explain how you updated the graphics drivers ? I think I don't have proprietary drivers.

Thanks.

---

### Post by lapique on 2009-11-27
As the wrecked PC is at my father's place, I connected to it via 
```
ssh -X USER@HOST
```
I could run systemsettings on my own X server. But the problem is that when I was clicking on the sections that need root priviledges (like session/connection options), it would not show the dialog, since it could not connect to my display...

So I tried to enable autologin in /etc/X11/kde4/kdm/kdmrc (or something similar), without success.

Running applications over ssh on another desktop proves the problem is not so bad, but I can't find it. I'll probably end up with a fresh install.

---

### Post by lapique on 2009-12-01
I actually ended up with a fresh install, which was probably quicker than an upgrade, and could recover all user data and configuration. It works like a charm, now.

---

### Post by ebonweaver on 2009-12-02
I just installed a fresh download of Ubuntu 9.10.  I then logged in and it told me there were something like 140 updates, so I installed them.  Now Ubuntu is useless as it kicks you back to the login screen immediately on login.  Based on this thread, I'd say this is an EXTREMELY critical bug in the current patch updates that needs to be fixed before every Ubuntu user is left with an unusable system.  I'm not impressed with my first experience of this OS, I'd think it would be free of "bricking" by now.  I hope the developers are taking note of this and correct the issue with the updates and can offer us a way to unbrick our systems without a complete re-install.

---

### Post by levicivita on 2009-12-14
Same problem here.  Fresh install of Mythbuntu 9.10.  Worked fine for a while, but then started getting this error all of a sudden.  Spent hours searching the forums.  Seems like a legitimate bug.  Very frustrated.  Not ready to go to Windows yet (I've 4 separate Ubuntu machines) but quite pissed at Ubuntu right now.

Installing 'ubuntu-desktop' now, as per one of the posts above.  Even if it works, it is a massively suboptimal solution.

---

### Post by munchkinmunchkin on 2009-12-15
> **ebonweaver said:**
> I just installed a fresh download of Ubuntu 9.10.  I then logged in and it told me there were something like 140 updates, so I installed them.  Now Ubuntu is useless as it kicks you back to the login screen immediately on login.  Based on this thread, I'd say this is an EXTREMELY critical bug in the current patch updates that needs to be fixed before every Ubuntu user is left with an unusable system.  I'm not impressed with my first experience of this OS, I'd think it would be free of "bricking" by now.  I hope the developers are taking note of this and correct the issue with the updates and can offer us a way to unbrick our systems without a complete re-install.

I have exactly the same problem and haven't yet found a solution other than re-installation. Luckily I still have 8.04LTS on my main computer which has been virtually trouble free for well over a year.

---

### Post by NuttBoxer on 2009-12-17
My version of this issue seems slightly different.  

1.  Install Ubuntu 9.10(Karmic Koala), install all updates, still ok.  
2.  Create two additional user accounts both unprivileged.  The username for one account is "guest".
3.  Log off the master account and the login screen is displayed, but the box in the middle of the screen that should display the available accounts to login with is blank.  Also the bar along the bottom of the screen only shows the star icon that allows configuration of things like onscreen keyboard, and change in screen contrast.  
4.  Press the power button on the front of my computer to bring up the shut down/re-start/hibernate menu and select restart.  A message is displayed stating the gdm welcome something is not responding do you still want to proceed.
5.  I say yes, the computer reboots, and loads up the same login screen with a blank middle box where the usernames should be listed.

I have another computer running the same version(9.10) with one user account, and have never had this problem.  Sounds like Koala has some serious issues needing to be fixed.

---

### Post by AndBurns on 2010-02-07
I also have had this problem.  For a while I was able to get around it by determining that the problem was that for some reason on boot up, my system was resetting the ownership of my home directory to root.

As a result (I presume) when kdm started up it was unable to write (and perhaps even read) from/to the directory and froze during the load.

I got around this by dropping down to a TTY session (Ctl-Alt) F2 and stopping KDM, changing the owner of the home directory and re-starting kdm
```

sudo stop kdm

chown andrew \home\andrew

sudo start kdm
```

Now, however, even that does not work and I am frozen out.

Grrr.

Any ideas / solutions out there?

---

### Post by drhans2 on 2010-02-07
This is how I corrected my problem after getting the upgrade... I had the same issues..Logon loop which I was able to rectify by setting the screen resolution to 1280 x 960 the default for a new install of Unbuntu. That proved to be too hard on the eyes.... And I was still getting admin privileges errors.. would not let me mount the HD...  So I went back to the previous release..9.04.. and all is good.. I'm thinking that 9.10 is not yet ready for prime time... Seems like way to many people are having the same problems with it... Here's the link to the post that worked for me.. thanks again to darkod...
[http://ubuntuforums.org/showthread.php?t=1399336](http://ubuntuforums.org/showthread.php?t=1399336)

---

