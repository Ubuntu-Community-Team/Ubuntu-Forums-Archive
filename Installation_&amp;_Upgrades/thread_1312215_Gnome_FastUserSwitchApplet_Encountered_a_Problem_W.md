---
title: "Gnome_FastUserSwitchApplet Encountered a Problem While Loading"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by wewantutopia on 2009-11-02
I'm now on my 3rd computer doing the 9.04 -> 9.10 Karmic and overall so far pretty painless.  This last computer has given me a problem.  Right after it boots I get an error that says 

The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".
Do you want to delete the applet from your configuration?

The menu in the top left (of my configuration) that allows you to log of, shut down etc and shows the status of pidgin/empathy is no longer there.  

Anyone else having this problem or know the solution?  The other 2 systems I've updated haven't had this problem...odd.

On a side note, I also have 3 icons on my second monitor so if the first is off I can quickly standy, restart, and shutdown.  The restart icon no longer works.  The command the button uses is:  shutdown -r now   I wasn't sure if they were related.  Thank you!

---

### Post by wewantutopia on 2009-11-03
Well after spending this past time reading I figured out the correct, but missing, applet in Karmic is indicator-applet-session not the fast user switch.  I deleted fast user and out of curiosity checked synaptic and sure enough indicator-applet-session was not installed.  I find this weird because the update did this automatically on my other two systems.  I installed the packages but nothing.  Restarted... no error because i removed fast user from my configuration but no indicator-applet-session menu.  

I checked my 2 other systems and if I right click on the panel indicator-applet-session is an option to add to my panel.  This system doesn't have this as an option even though I installed it.  I then completely removed I-A-S and reinstalled it.  Nothing.  Restarted, nothing.  So I'm back to square 1 but with new knowledge.  Any ideas?

---

### Post by ionFreeman on 2009-11-04
I'm also having this problem, but I have the indicator-applet-session installed. Where did you do all this reading?

---

### Post by beloved88 on 2009-11-04
I've been usuing Karmic/XP for 4 or 5 days now, no major problems until this one.  My experience so far has been good, except for this issue.  Earlier today, when i tried to log out or restart the computer, i got no response.  I eventually used a ctr-alt-delete to bring up a shutdown menu to restart, and when i logged back in after reboot, i saw that error message.  It seems that it just showed up recently, could one of the updates have caused the issue?

---

### Post by diskotek on 2009-11-10
some problem here, i tried this but didn't worked for me:
> sudo apt-get install gnome-applets

---

### Post by pa7two on 2009-11-16
This works :-) Had three PCs showing me the same Gnome_FastUsersSwitchApplet error :-(

Open a Terminal:

Code:
sudo /etc/init.d/gdm stop

Code:
sudo aptitude reinstall gnome-applets

Code: 
sudo aptitude reinstall gnome-applets-data

Code:
sudo /etc/init.d/gdm start

>> Reboot

>> When rebooted: 

Code:
sudo apt-get update

Code: 
sudo apt-get install **ubuntu**-desktop gdm

Code: 
sudo /etc/init.d/gdm restart

---

### Post by Captain_Glen on 2009-11-22
I can confirm that pa7two's solution works.  But only if you haven't deleted the file.

If you have do this first:

```
rm -rf .gnome .gconf .gconfd .metacity
```

Note this will wipe all your gnome settings.  You will have to reconfigure everything to your liking.

---

### Post by Rolandmaffia on 2011-07-15
> **diskotek said:**
> some problem here, i tried this but didn't worked for me:

I used this command:

> sudo apt-get install --reinstall indicator-applet*

and it installed me the proper things. 
(I recently removed unused things, like gwibber, but it must be installed to use indicator.)

That solved my problem...

---

