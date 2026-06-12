---
title: "Low graphics mode"
date: 2012-09-13
forum: Hardware
---

### Post by asearle on 2012-09-13
Hi Everyone,

I was attempting to get a graphics tablet working and so removed a number of files with a view to re-installing these.

One of the files was ... xserver-xorg-input-wacom

Then, when I rebooted the computer, I got the following message ...

The system is running in low-graphics mode
Your screen, graphics card, and input device settings could not be detected correctly.  You will need to configure these yourself.

I clicked on OK and a further screen appeared ...

What would you like to do?
run in low-graphics mode for just one session
... other options

With the choice Cancel or OK

Here I tried clicking on OK but found that, as far as I could see, I had no keyboard or mouse to do that.

I feel really stupid that I de-installed an important file (I remember it was highlighted in red when I selected it for deletion) but what I really need now is a way to re-install that file.  And I am blocked by the fact that I do not seem to be able to select anything on the "What would you like to do?" screen

Can anyone help me with this?  Maybe pointing me to a HOWTO on the use of Low-graphics mode or installing files/packages from the command prompt?

Many, many thanks,
Alan

---

### Post by asearle on 2012-09-13
After some searching I found that with ctrl-alt-F1 I could get a command line terminal up.

Then I tried reinstalling the file that had removed ...

sudo apt-get install xserver-xorg-input-wacom

... which seemed to install correctly.

I then rebooted but got the same problem with the "low graphics mode" screens with the dead keyboard and me being stuck at the "what would you like to do?" screen.

I'll keep searching but hope that someone has an idea for me?

Regards and thanks,
Alan

---

### Post by asearle on 2012-09-13
I found this suggestion ...

[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx)

... and tried running ...

sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core

... which ran successfully.

But I'm still getting the low graphics mode screens which then in the end don't let me into low graphics mode.

I was really pleased that I was able to re-install the component that I had removed but was surprised that it didn't fix the problem and am starting to get worried now.

Any ideas would be most gratefully received.

Many thanks,
Alan

---

### Post by asearle on 2012-09-13
I found these instructions ("gdm") ...

[http://askubuntu.com/questions/10664/how-do-i-fix-ubuntu-is-running-in-low-graphics-mode](http://askubuntu.com/questions/10664/how-do-i-fix-ubuntu-is-running-in-low-graphics-mode)

... and yes! my log-in screen returned. Wonderful!

But I find that I can log in and the mouse cursor appears (and is active) with a misty purple and white background but the system does not go further.

Any ideas for me?

Many thanks,
Alan

---

### Post by typhoon_tip on 2012-09-13
How you removed those files in the first post ? Manually or with apt-get remove ?

---

### Post by asearle on 2012-09-13
The solution that I found involved activating "gdm".  Is that the classic gnome frontend?

I have installed 12.04 with the new-style frontend so maybe my problem is that the solution (re-)installed the old frontend which no longer exists on my PC.

Any tips for further adjustment/settings would be a great help.

Many thanks,
Alan

---

### Post by asearle on 2012-09-13
> **typhoon_tip said:**
> How you removed those files in the first post ? Manually or with apt-get remove ?

I removed them with Synaptic.

---

### Post by asearle on 2012-09-13
> **asearle said:**
> The solution that I found involved activating "gdm".  Is that the classic gnome frontend?

I have installed 12.04 with the new-style frontend so maybe my problem is that the solution (re-)installed the old frontend which no longer exists on my PC.

Any tips for further adjustment/settings would be a great help.

Many thanks,
Alan

I used this syntax ...

sudo apt-get update
sudo apt-get -d install --reinstall gdm
sudo apt-get remove --purge gdm
sudo apt-get install gdm

... and am convinced that if I had had classic Gnome Desktop it would have worked.

So what I think I need now is the equivalent syntax for the new Ubuntu Desktop.

It would be great if someone could point me in the right direction.

Many thanks,
Alan

---

### Post by asearle on 2012-09-13
Yippee:  I fixed the problem with ...


    sudo apt-get install --reinstall ubuntu-desktop
    sudo reboot

I'm very pleased about that.

The moral of the story is don't de-install any packages marked in red.

You live and learn!

Bravo to Ubuntu for its robustness and flexibility.

Regards,
Alan

---

### Post by typhoon_tip on 2012-09-14
```
sudo apt-get install --reinstall ubuntu-desktop
sudo reboot
```

I wanted to post this after your reply :) Good you solved it anyway !

---

