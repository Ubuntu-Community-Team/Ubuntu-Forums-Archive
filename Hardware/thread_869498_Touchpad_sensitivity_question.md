---
title: "Touchpad sensitivity question?"
date: 2008-07-24
forum: Hardware
---

### Post by gabriella on 2008-07-24
How do I control the sensitivity of the touchpad on my laptop? Right now how I have things set up it's a lot less sensitive under Linux than under Windows. Anyone else have this problem?

Some touchpad clicks will work if I click realy hard but mostly they dont. When I'm trying to launch something from the desktop a double click usually  won't do it and I have to resort to using the left hand button below the touchpad. System/Preferences/Mouse gives me a touchpad option but theres nothing to set the sensitivity.

Hardy 8.04
Compaq Presario M2000

---

### Post by DapperMe17 on 2008-07-24
Hi Gabriella,

Download "Gsynaptics", or is it "Gynaptics"...anyway, you get the picture....from the repositories.

Once installed, go to "System/Preferences/Touchpad" and you be able to adjust your laptop touchpad settings.

You may get a pop-up box that says to add an entry to a file. Go ahead and follow that to a "t" & your in business:popcorn:

---

### Post by gabriella on 2008-07-25
> **DapperMe17 said:**
> Hi Gabriella,

Download "Gsynaptics", or is it "Gynaptics"...anyway, you get the picture....from the repositories.

Once installed, go to "System/Preferences/Touchpad" and you be able to adjust your laptop touchpad settings.

You may get a pop-up box that says to add an entry to a file. Go ahead and follow that to a "t" & your in business:popcorn:


Uhmmm....? When I go to System/Preferences/Touchpad now I get the following warning:

"GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

How do I set SHMConfig = true? and where do I find those files? :confused:

---

### Post by Tomlin on 2008-07-25
The file etc/X11/xorg.conf will have something similar to the following.


Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        **Option          "SHMConfig"             "on"**
        Option          "HorizScrollDelta"      "0"
EndSection

You'll need to add the bolded text.

This should do the trick.

Good luck.

---

### Post by gabriella on 2008-07-27
> **Tomlin said:**
> The file etc/X11/xorg.conf will have something similar to the following.


Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        **Option          "SHMConfig"             "on"**
        Option          "HorizScrollDelta"      "0"
EndSection

You'll need to add the bolded text.

This should do the trick.

Good luck.

OK that seems straightforward enough. I presume I just edit the file and then save it? 

Problem is when I go to save it, it won't because I "dont have the necessary permissions" How do change it so I do? Maybe a silly question but I'm just learning!

---

### Post by eldragon on 2008-07-27
do gksu gedit /etc/X11/xorg.conf


that will give you admin permissions

---

### Post by gabriella on 2008-07-27
> **eldragon said:**
> do gksu gedit /etc/X11/xorg.conf


that will give you admin permissions


OK what am I doing wrong? I get the following:

mbdb@m2000:~$ do gksu gedit /etc/X11/xorg.conf
bash: syntax error near unexpected token `do'
mbdb@m2000:~$ 

I also went to xorg.conf via the file browser but it won't let me change pemission because I'm "not the owner" grrrr:confused:

---

### Post by argosreality on 2008-07-27
> **gabriella said:**
> OK what am I doing wrong? I get the following:

mbdb@m2000:~$ do gksu gedit /etc/X11/xorg.conf
bash: syntax error near unexpected token `do'
mbdb@m2000:~$ 

I also went to xorg.conf via the file browser but it won't let me change pemission because I'm "not the owner" grrrr:confused: just run "sudo gedit /etc/X11/xorg.conf" without the quotes at the command line. That'll give you superuser level permissions to do the edit. However, I strongly recommend making a backup of xorg.conf before making any changes that way if you make a mistake its easy to roll back. Just run

"sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak" from the command line. If X breaks you can just replace the modified one with the bak file using the same command

---

### Post by gabriella on 2008-07-28
hmmm?  I've edited xorg.conf and saved it. 

But when I go to System/Preferences/Touchpad it --still-- tells me that "GSynaptics can't initialize" (and to set "SHMConfig" "true")

I've saved it as both "true" and "on" with same result. Any ideas??

---

### Post by gabriella on 2008-07-28
OK I may have jumped the gun on this. Maybe it needed a reboot or something? But anyway GSynaptics will now initialise and I can adjust the touchpad settings.

I am not yet convinced it's solved my problem though. It seems to me that the sensitivinty of the touchpad varies between different functions. eg when I try to launch Firefox or another appication on the desktop it takes a VERY hard double click on the icon to do it. However moving arround between funtions or tabs and it seems much more sensitive

---

### Post by DapperMe17 on 2008-07-29
Gabriella,

I'm glad you got it working...there is a touchpad slider in the system/prefs/touchpad setting manager. 

If the default options aren't what you're looking for, the xorg file can be manually edited...however, it will require some forum searching, time & effort.

Or, you can try to get by on the options offered by Gsynaptic.

---

### Post by eldragon on 2008-07-29
yes, every time you modify xorg.conf you have to restart the xserver for changes to take effect.

good luck

---

### Post by gabriella on 2008-07-29
OK thanks guys for all the help. I think I've mostly got it sorted now. I'll play with it for a few days and see.

---

### Post by macvr on 2008-09-02
> **gabriella said:**
> 
I am not yet convinced it's solved my problem though. It seems to me that the sensitivinty of the touchpad varies between different functions. eg when I try to launch Firefox or another appication on the desktop it takes a VERY hard double click on the icon to do it. However moving arround between funtions or tabs and it seems much more sensitive

i too have the very same problem, clicking seems very difficult
any body has a solution for this?[even though i'v got gsynaptics]
click locking for dragging also doesnt work properly

this touchpad problem is my only ubuntu experience killer!

i was stuck in beginner's forum with no help[http://ubuntuforums.org/showthread.php?t=890352]("http://ubuntuforums.org/showthread.php?t=890352")

i'v filed a bug report too:[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/259289]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/259289")

---

### Post by mocoloco on 2008-09-03
On my laptop gsynaptics (system/prefs/touchpad) didn't affect my sensetivity much either, I had to manually set it in xorg.conf.  I recently posted in another thread, you can [see the details here]("http://ubuntuforums.org/showthread.php?t=902542").

---

### Post by macvr on 2008-09-03
> **mocoloco said:**
> On my laptop gsynaptics (system/prefs/touchpad) didn't affect my sensetivity much either, I had to manually set it in xorg.conf.  I recently posted in another thread, you can [see the details here]("http://ubuntuforums.org/showthread.php?t=902542").

so even if i have gsynaptics, i need to set things in Xorg...

does this mean i have to uninstall gsynaptics or is it ok to use both simultaneously?

can i set the vertical scrolling area width?

---

### Post by mocoloco on 2008-09-03
You don't need to remove gsynaptics.  You should be able to play with those settings to tweak them to your liking, although I know this is a pain since you have to log out and back in to see each change :(
It might be a good idea to backup your xorg.conf file first, that way if you mess something up and can't get in to the gui you can restore your backup and be back to where you are now.
back it up with
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.backup
```

If you get stuck later and need to restore it, hit Ctr+Alt+F2 for a text terminal, and type
```
sudo cp /etc/X11/xorg.backup /etc/X11/xorg.conf
```

---

### Post by macvr on 2008-09-03
thank you, atleast i know now what i need to do....

didnt get any directions in the beginers sections!!!

EDIT: worked... now my touchpad works fine

---

### Post by kruzztee on 2008-09-06
I used the instruction written above. But now i can't seem to have a tap function in my Toshiba Portege M200 touchpad.

Secondly... how to enable the accelaration in the touchpad?

---

