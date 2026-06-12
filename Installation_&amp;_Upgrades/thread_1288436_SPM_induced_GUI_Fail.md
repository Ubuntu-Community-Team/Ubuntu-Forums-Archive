---
title: "SPM induced GUI Fail"
date: 2009-10-11
forum: Installation &amp; Upgrades
---

### Post by Mostly.Harmless on 2009-10-11
Hello again,

It appears I am highly skilled at making my own computer melt down with the synaptic package manager. I'm once again appealing for help via the graces of the LivesessionCD.

I was going to start learning python, so I could be more Ubuntu friendly. I found some manuals for Python 3.0, I then installed Python 3.0

I read how to start python from the console, typing "python"

It started the old python 2.6. In the SPM it stated that 2.6 was the "default" version.

So, thinking what I though was logically, I set about removing what I think were python 2.6 related files, which would make 3.0 the defualt. I think I removed a few, when on my second go around one of them came up in the "Essential" category when it has that little box asking you to confirm and listing the actions that will take place.

At this point, I decided to back off, I closed the SPM with no further action.


I noticed that alot of icons on my toolbar appeared broken, namely the firefox one and the "forcequit" button. Also there were alot of icons/graphics missing from the dropdown menues.

SPM would not open again giving me some error, Firefox would open but not go to any site or do anything operational.

I decided to restart, and It booted normally up to the ubuntu "loading screen" which I can only describe as the black screen with the ubuntu icon and the loading bar, just before the GUI appears.

From there I got a few errors and it loads to the MS dos type screen. 


So,

Everything hardware/essential system stuff appears to be working. In live session I can access my HDD's and all my files and folders are there. In the Dos type screen I can enter various commands and navigate around my folders.

It appears that its just the GUI which does not work. 

WHAT I HAVE TRIED:
I have read around for a "repair installation" and done my research. I found a command which from memory was sudo apt-get install --fix-broken. this seemed to be just what I wanted, figuring I may have just removed an essential OS file by accident.

I ran this command, It gave me a list of files and said they were automatically installed and were not required. I then ran the suggested command which removed them.

Im a new/low end user but the system did not appear to tell me anything was wrong. 

My friend who is slightly better than I suggested that I somehow turned off my Nvidia drivers, which was causing the trouble with the GUI.

I was wondering if such a repair install was possible as I'd rather not wipe and start again. I can if I must, as I can backup essential work files etc on external HD's using Live session.

Or, is there anything else that could help me?

Thanks
/Self made disastermaster

---

### Post by Intrepid Ibex on 2009-10-11
I'll try to help you ^^.

> From there I got a few errors and it loads to the MS dos type screen. 
You mean (linux) console :)?

> I ran this command, It gave me a list of files and said they were automatically installed and were not required.
They are actually **packages**, not **files** :).

At console you could type "nano /etc/X11/xorg.conf" and look for the section "Device". From there change the
```
Driver "nvidia"
``` to
```
Driver "nv"
```


**E:** [B]Also, as I'm really not the one to explain all this stuff, the OP's problem is basically that he can only access the console - not even gdm.

I'm not entirely sure, but it seems that he removed python 2.6 (with all the packages needing it) in hopes of getting the just installed 3.0 to be the default one.[/B]


You can try installing python-2.6 (or whatever it was) with 'sudo apt-get install python-2.6' but this will not bring back the lost critical packages.. I'm pretty clueless here if one of "nv"s dependencies is python 2.6, sorry.

If you can log in graphically with "nv" driver, you could open sypantic -> check from the history what it was you removed and install that stuff back (if you didn't remove them from synaptic, I'm again clueless).

---

### Post by Mostly.Harmless on 2009-10-11
Thanks for the help, I'll try those console commands when Im in the 'linux console' ha.

--> At least I learned what that was called. 

Does anyone know what/how I uninstalled critical files? As I said before, I didnt actually remove python 2.6, and as soon as something was labeled as 'essential' byt the SPM I backed off and took no further action. 

Im actually really stumped. How was I actually able to destabilize my OS with a few unwarned clicks on SPM...

---

### Post by Intrepid Ibex on 2009-10-12
Just calling Synaptic Package Manager "Synaptic" will prevent confusion :).

But yeah, someone using ubuntu here could give the list and make 'sudo apt-get install...' list about it.. quite frankly I'm still clueless.

---

