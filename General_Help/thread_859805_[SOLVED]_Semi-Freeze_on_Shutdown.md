---
title: "[SOLVED] Semi-Freeze on Shutdown"
date: 2008-07-14
forum: General Help
---

### Post by MatthewPlanchard on 2008-07-14
Okay so for the past couple of days now when I go to shut down Ubuntu, the panels disappear and then I just get a freeze with the wallpaper still showing. The mouse is movable, I think. I will check and make sure tonight when I turn off the computer.

The weird thing is that if I press the power button on my computer the screen switches to a console window and then the system shuts down. I will try my best to note what text it shows this evening when I shut down the computer.

This does not occur on restarts.

In the meantime, while I'm working on specifics, does anyone have any suggestions?

---

### Post by tramir on 2008-07-14
Can you try the following: press CTRL-ALT-F1. This will switch to a command-line login. Log in as yourself (username-password), and then type 
```
sudo reboot now
```
Try to write down any message error message that shows up, especially after "Stopping GDM", and post them here..

---

### Post by MatthewPlanchard on 2008-07-15
Okay the mouse is definitely still movable after the panels disappear, and then the system just hangs for a while. When I hit the power button, it switches to black screen, white text, and the last line is 

/dev/sda something
Setting Advanced Power Management to 0

Then a few messages pop up about Network Manager, several of which have FAILED at the end of the line.

Per your suggestion, I tried rebooting from another tty with sudo reboot now and rebooted successfully, seeing the same messages about Network Manager and all that.

It's as though Ubuntu is beginning the shut down process and simply pausing until I hit my power button. There are no error messages whatsoever.

Any ideas? :confused:

New news: I just discovered it also happens on reboot. So, um, yeah.

---

### Post by tramir on 2008-07-15
You might have [this bug]("https://bugs.launchpad.net/ubuntu/+bug/222233"). Can you check it?
There also seems to be a solution mentioned in [this post]("http://ubuntuforums.org/showthread.php?p=4858236#post4858236"), but I don't exactly know if that would help you entirely. Can you look at these links and report back?

---

### Post by MatthewPlanchard on 2008-07-16
That was the exact bug, and surprisingly enough, it was having Keytouch installed that was hanging the system, as described in [this post]("http://ubuntuforums.org/showpost.php?p=4881216&postcount=25").

Thanks for your help!

---

### Post by tramir on 2008-07-16
Glad you figured it out and it works now. Can you please mark the thread as solved, so that other people with this problem can find the solution easier?

---

