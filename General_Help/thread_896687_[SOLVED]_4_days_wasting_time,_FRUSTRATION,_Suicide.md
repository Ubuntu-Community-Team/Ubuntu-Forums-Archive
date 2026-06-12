---
title: "[SOLVED] 4 days wasting time, FRUSTRATION, Suicide!"
date: 2008-08-21
forum: General Help
---

### Post by Tony_photoplus on 2008-08-21
Mmm, Nvidia drivers and following loads of ways to load new drivers is driving me up the wall and about to kick the computer out down the road.  It would be easier to find a pirate version of WinXP, problem solved!!  I have just followed a way to rid all the computer of all present Nvidia drivers etc by using the terminal which I now know is the method of doing things.  I copied and pasted into the terminal a script after emptying all the Nvidia stuff and then it goes into a black screenm with white writting.  That flumuxed me, I couldn't copy and paste as I had done and I couldn't find my way back to the desktop.  Finaly it m,anaged to restart as there was no way I knew how to proceed from here.  Now Ubuntu loads and leaves me with the black screen with type on it.  The last thing it states is
*Running local boot scripts (/etc/rclocal)
And its stuck!! 

I have tried looking for the information again, but as this is on a different comp I have lost the link.  Now on triple dose of morphine (not a joke true, stressed out and makes pane worse).

I have tried so many ways to get the Nvidia Geforce 4MX to be accepted and the hours of anguish is beyond anyones temperament.

Any ideas how to progress from here?  Or am I looking at another 4 days of wasting my time?

Tony

---

### Post by stormtrooprdave on 2008-08-21
Have you tried using Envy? It automatically detects your graphics card and installs the correct drivers

From the website -

""Envy" is an application for Ubuntu Linux and Debian written in Python and PyGTK which will:
1) detect the model of your graphic card (only ATI and Nvidia cards are supported) and install the appropriate driver. However automatic detection can be overridden with the "Manual installation"
2) install the right driver for your card and all the required dependencies
3) configure the Xserver for you

Envy features both a GUI (which you can launch only inside a Desktop Environment) and a textual interface which you can use if, for example, you cannot start the Xserver."

Link - [http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by kirsis on 2008-08-21
If you can't boot properly anymore, try booting with a LiveCD. Then mount your Ubuntu partition to /, install Envy and the appropriate drivers through Envy. Then reboot and it should work.

To mount your Ubuntu partition to /, find out the device name of it (run gparted from the LiveCD). Then, when you know the right device name, do

```

sudo mount /dev/hda1 /

```
(Replace /dev/hda1 with appropriate device that is listed in gparted)

---

### Post by Tony_photoplus on 2008-08-21
Thanks for that I will try it.  But the frst thing I have to do is get the comp going first.  It is still in stuck mode I think I shall have to reload for the 5th time.  I wish I knew what I was doing.  I try and read the jargon but it isn't plain English.  I am like many - I want my hand held through these things.  It may seem tedious to a lot of the people who are in comp brain mode and Linux, but its a steep learning curve and not an easy one.  Its not Linux fault its the way the manufacturers have dealt with the production which is not Linux friendly.  

Tony

---

### Post by kirsis on 2008-08-21
When you turn it on and it stays on that one line you mentioned, try pressing Ctrl+Alt+F1.

If that presents you with a text login prompt, then it's X at fault. Either try installing the drivers with a LiveCD (if you have it) or try deleting /etc/xorg.conf (*sudo rm /etc/xorg.conf* after logging in in text mode)

If pressing Ctrl+Alt+F1 doesn't work, then I've no idea why it's not booting properly.

---

### Post by Tony_photoplus on 2008-08-21
Many thanks for your reply.  Couldn't get it to reboot as you said so having to relaod.  But, will then after the large downloads etc get the envy site up.  Because I have used all my bandwidth I am restricted to 128kb so its slow going, that also makes it frustrating.

Tony

---

### Post by Tony_photoplus on 2008-08-21
Alas no joy with Envy - Log statement -
python pulse.py nvidia 
root@photoclub-desktop:/usr/share/envy# python pulse.py nvidia
Envy - Version 0.9.10
ENVY ERROR: Your Operating System does not seem to be supported by Envy

Downloaded as it stated.  It could be that I have just only reloaded the OS again and no updates have been installed, so it could be certain factors.  Just guessing really.  

I am slowly downloading the updates once again.  That should take a few hours and now I have sit and waste my time as I can do my other work.  This has been one hell of a S**T drive of total time wasting.  I have three more to resolve and am not looking forward to it, it will be more time in HELL.  I suppose once its done I should have some knowledge in my poor morphined brain.

Tony

---

### Post by Tony_photoplus on 2008-08-22
[COLOR="Red"]**_[SIZE="6"]YES[/SIZE]_**[/COLOR]

[COLOR="Black"][SIZE="2"]Its all fixed and running what a marathon.  I have done so much work and hours that to tell you how actually I achieved it is amazing.  Thanks for the link on Envy it worked.  It should be standard on all Ubuntu downloads[/SIZE][/COLOR]

Tony

---

### Post by loell on 2008-08-22
please mark your thread as solve :)

---

