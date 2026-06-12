---
title: "Nvidia graphics driver problem..."
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by NayC on 2009-05-02
Hi, 
 
I just installed ubuntu "within windows" which also allows me to boot either Vista or Ubuntu (9.04).
 
Installing is fine, but then when I get into ubuntu and install the recommended NVidia drivers, on reboot it goes into a command line prompt. After a little search apparently I should be able to get back to the GUI using "startx" but that returns the error "no screens available"?
 
I have an 8800GTX and not entirely sure if the recommended driver (is it 173, or something?) actually supports my gpu. Is there a way to remedy this new change from the command line or just get into the GUI again? Or I could re-reinstall again! either way, if i get back into the GUI, how should I go about an update?
 
Sorry, Linux novice here!
 
Any help would be very appriciated, Cheers, Nay.

---

### Post by RedSingularity on 2009-05-02
The current nvidia driver is 180 now.  Try that one and see if it supports your card.

---

### Post by NayC on 2009-05-02
Oh, sorry, that is the one that ubuntu installed. I remeber now. 173 is the one found in the add/remove programs! I looked through the 173 compatibile list and it supports almost every "8800" card, but mine didn't appear to be in the list after a pretty hard look. Could this be why and if so would it be the same for the 180 release?
 
Could someone please check in their add/remove programs if the driver in that list supports the "8800GTX"?
 
Cheers.

---

### Post by RedSingularity on 2009-05-02
It says it does.......did you try downloading the driver directly from Nvidia and installing it?

---

### Post by NayC on 2009-05-02
Ye, It brung up a list with three sections saying do you want to install the recommended drivers etc. The "180" driver was at the top of this list. Then it installed, and finished. I reboot the machine for the drivers to take affect and then am now stuck in a command prompt. The drivers had to download then install, so I assume thats ubuntu getting the latest update and installing it. 
 
Any ideas?

---

### Post by RedSingularity on 2009-05-02
Can you get back to the graphical interface?  
If not type this command in the command screen:  sudo apt-get autoremove nvidia-180-modaliasas

This will remove the current driver so you have a GUI again.

---

### Post by NayC on 2009-05-02
After doing a little test.
 
Install OS. Reboot again to make sure. Fine
 
Install updates. Reboot. Fine
 
THEN, i looked at the recommended gpu drivers again. There was three in a list. They where the Nvidia drivers 180 [Recommended], 173 and 96. Rather than go for the 180 which previously broke my install, i choose the 173. This did the same but differently.
 
When the OS started it did some checks, everything appeared ok other than "PulseAudio" or something which had a red '*' next to it. The list continues to "checking battery status" and says [OK] to the right of it. It freezes here, no matter how long I wait. I press the power off button and it says GNOME desktop manager shutting down and then computer turns off.
 
Try again and it takes me to a command prompt login. I can log in, but that is as far as I can get. This "startx" if it is the correct way to try enter the GUI again still brings the error message "No Screens Detected".
 
Thats as far as I can get. Any ideas on what this could be?
 
If it helps i'm running (well trying) the Ubuntu 9.04 32-bit (64b CD wouldn't do anything on my comp) on a core i7 machine with 6GB of 1866MHz ram and 2x 8800GTX's currently both in the machine, but with the SLi bridge detatched. Could having either the two gpus in there without an SLi connection be the source of the problem at all? Or should I re-connect them for now, or remove one? If these may be the cause... 
 
Any ideas appreciated as I'm wanting to learn how to use linux and its features, but wont progress leaving things like drivers to standard stuff. 
 
Cheers, Nay.

---

### Post by NayC on 2009-05-02
Cheers again shadow. I will try that now.

---

### Post by NayC on 2009-05-02
I tried what you just said (but with '173', as i currently was trying that). Yes it removed it (i believe as it did lots of stuff without fail). But then I have no way back into the GUI. If 'startx' isn't the way, then could someone please inform me how to return from to the GUI from the Command prompt.

This is really beging to bug me now! lol.

---

### Post by RedSingularity on 2009-05-03
You are correct startx is supposed to start the GUI.  In terminal type "sudo apt-get autoremove xserver-xorg-video-nv"  

Restart the computer and see what happens.

---

### Post by NayC on 2009-05-03
Nope, nothing. Does some deleting of the files requested.

startx is still bringing me 'Fatal Server Error - "No Screens Found"'...

:(

---

### Post by ashfallen0 on 2009-05-03
Post up your xorg.conf I had a similar issue with my m1750 with it's 9800GTX SLI.  once updated to 180, it stopped detecting my laptop's screen properly.  After doing nvidia-xconfig, it had an res that the screen wouldn't handle.  I updated that file to reflect the native 1920x1200 res, and it handled the screen properly afterwards...
also, if you're stuck at command prompt, it may be dumping you there with the x server already running, try CTRL+ALT+F9, or ' sudo /etc/init.d/gdm stop ' then ' sudo startx '... i've run into various times with nvidia upgrades that occasionally it fails from the graphic login to the prompt. My old HP laptop has a startup freeze that can only be solved by holding the space bar until the login and then desktop shows; or by quickly tapping the power button.

Hope any of this helps

---

### Post by NayC on 2009-05-03
> **ashfallen0 said:**
> Post up your xorg.conf I had a similar issue with my m1750 with it's 9800GTX SLI.  once updated to 180, it stopped detecting my laptop's screen properly.  After doing nvidia-xconfig, it had an res that the screen wouldn't handle.  I updated that file to reflect the native 1920x1200 res, and it handled the screen properly afterwards...
also, if you're stuck at command prompt, it may be dumping you there with the x server already running, try CTRL+ALT+F9, or ' sudo /etc/init.d/gdm stop ' then ' sudo startx '... i've run into various times with nvidia upgrades that occasionally it fails from the graphic login to the prompt. My old HP laptop has a startup freeze that can only be solved by holding the space bar until the login and then desktop shows; or by quickly tapping the power button.

Hope any of this helps

Cheers! I just ran nvidia-xconfig and this is what it posted.

Using X Configuration file "/etc/init.d/gdm"

WARNING: No Layout specified, constructing implicit layout section using sreen "Default Screen"

WARNING: Unable to find CorePointer in X Configuration; attempting to add new CorePointer section

WARNING: The CorePointer device was not specified explicitly in the layout; using the first mouse device

WARNING: Unable to find CoreKeyboard in X Configuration; attempting to add new CoreKeyboard section

WARNING: The CoreKeyboard device was not specified explicitly in the layout; using the first Keyboard device

ERROR: Unable to write to directory '/etc/X11'



Well thats what I got and tried the 'startx' afterwards and CTR+ALT+F9 etc aftwards and, nothing... thanks for trying though!

---

### Post by ColShag on 2009-07-02
I have this exact same problem, I'm putting 9.04 on my brothers Nvidia board with 2 high end cards attached.  Anyone find a workaround?

---

### Post by slamhound on 2009-07-02
To get my two cards working, I had to follow the steps in my previous reply to another poster.  I had to run nvidia-xconfig -a (the -a tells it to enable all gpus).  See the post for more details (and a workaround for one bug that might come up):

[http://ubuntuforums.org/showpost.php?p=7452633&postcount=2](http://ubuntuforums.org/showpost.php?p=7452633&postcount=2)

---

