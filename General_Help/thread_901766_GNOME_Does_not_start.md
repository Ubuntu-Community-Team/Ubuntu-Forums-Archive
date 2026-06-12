---
title: "GNOME Does not start"
date: 2008-08-26
forum: General Help
---

### Post by jman1013 on 2008-08-26
Hi all...

My problem is that as soon as I login to Ubuntu, GNOME does not start. In other words, I don't see the panels, my desktop wallpaper, or my icons. All I see is the cursor with the login screen's orange-like color. I have installed IceWM as a backup Window Manager, but I would like GNOME back.

I have tried reconfiguring Xorg by entering ```
sudo dpkg-reconfigure xserver-xorg
```

This did not work. Neither did reinstalling ubuntu-desktop.

Thanks,
Jordan

---

### Post by mssever on 2008-08-26
Try logging into the failsafe terminal. From there, type ```
gnome-session &
``` Hopefully, you'll get some error messages that will provide some idea of what's wrong.

---

### Post by jman1013 on 2008-08-27
Ok, I think that the problem may be with Metacity, and not with GNOME. I tried running:

```
gnome-session &
```

and that returned the an error that it could not open the file:

```
~/.metacity/sessions/default0.ms
```

Then, I tried running "gnome-session &" in an IceWM xterm session, and GNOME suddenly started up. But the Ubuntu Human theme did not appear, and the panels were in the default GNOME theme, not the Human style like it should have. Then, a few seconds later, I heard the Ubuntu start-up sound and the themes loaded up except for the window title bars (they kept my IceWM theme).

jman1013

---

### Post by mssever on 2008-08-27
> **jman1013 said:**
> Ok... when I typed "gnome-session &" (Without the quotes), I got the following message.
```
(gnome-session:5738): Gtk-WARNING **: cannot open display:
```Being a complete Ubuntu noob, I have no idea what this means.:confused:
You did this from the failsafe terminal session? (i.e., you went to the graphical login screen, hit F10, Chose "session", and selected "Failsafe terminal"?

If so, that's certainly an odd error. What does this produce? ```
echo $DISPLAY
```

---

### Post by jman1013 on 2008-08-27
No, I had also recently installed KDE to try it out if GNOME could not get working. So that replaces GDM with KDM, and I didn't know how to get into the failsafe terminal. So, I switched KDM back to GDM, and got the results that were in my edited post above.

Sorry for any confusion :oops:

---

### Post by mssever on 2008-08-27
> **jman1013 said:**
> Ok, I think that the problem may be with Metacity, and not with GNOME.
You can test that by starting metacity from a failsafe session: ```
metacity &
```If Metacity comes up, then load your configuration: ```
gnome-settings-daemon &
```You can actually piece together your your session that way if you know the names of the various pieces.

---

### Post by jman1013 on 2008-08-28
I tried that, and found that the problem is NOT metacity. It loads up fine. Its just that nothing else from GNOME will. (My icons, wallpaper, and panels).

Also, after a couple minutes, (after trying to run "gnome-session &" from a failsafe terminal), a window pops up saying the following:

---------------------------------------------------------------------------
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

-------------------------------------------------------------------------

After that appears, my panels, wallpaper and icons appear, but none of the panels and window title bars are in the correct theme! :confused: 

And what's even more strange is that after about 2 mins., I hear the Ubuntu startup sound, and all of the themes become normal.:confused:

---

### Post by mssever on 2008-08-28
Have you tried manually starting gnome-settings-daemon as I mentioned above? It sounds like some of your settings might have gotten corrupted somehow. The bad news is that I don't know how to fix that short of deleting all your dotfiles (and consequently all your settings). The good news is that I've had this problem a couple of times, and each time it's fixed itself after a while. I don't know what caused it, and I don't know what fixed it.

---

### Post by jman1013 on 2008-08-28
Yeah, I did try running "gnome-settings-daemon &" and I got that same message. How would I go about deleting these dotfiles, or would it just be easier to re-install Ubuntu. btw, I'm completely backed up, so I won't lose anything.

---

### Post by mssever on 2008-08-28
An additional sanity check before attempting anything more drastic: Create a new user ```
sudo adduser testuser
``` and see if you can log in normally with that user. If you can't, then something's really screwy with your system.

Otherwise, if you reinstall and restore your home directory from your backups, you're likely to encounter the same problems as before, because you'll still have your dotfiles (dotfiles are files and directories whose names begin with a dot; in this case I'm specifically referring to dotfiles in your home dir). You can start by deleting dotfiles whose names relate to Gnome. But be warned: You'll lose a lot of settings by doing this. And some apps (notibly Tomboy) store there data in dotfiles, so you could end up losing some data. Of course, you can selectively restore from your backups. If deleting the Gnome-related dotfiles is insufficient, try deleting ~/.local. If that still doesn't work, keep deleting dotfiles until you get something that works.

---

### Post by Bliepo32 on 2008-08-28
Are you using an ATI videocard? Because that might be the cause of your problems.

---

### Post by mssever on 2008-08-28
Wait. Before you delete dotfiles, I just re-read your error message. It's possible you have a problem with dbus. Type ```
ps -ef | grep dbus
```and make sure that dbus is running.

---

### Post by jman1013 on 2008-08-28
No, I'm not using an ATI card (sadly, I'm stuck with an SiS630/730. YUCK!). Thanks for the reply though.

I tried logging in with the three other user accounts on this system, and none of them worked either. Also, running the check to make sure that dbus was running only told me that, in fact it was running. I'll try deleting the dotfiles, and if that fails I will reinstall Ubuntu. (It just so happens that I installed Ubuntu about 3 months ago. All of my files from my old Windows XP install were already backed up, so I'm not losing much, if not anything.)

Thanks for all the help though!

---

### Post by mssever on 2008-08-28
> **jman1013 said:**
> No, I'm not using an ATI card (sadly, I'm stuck with an SiS630/730. YUCK!). Thanks for the reply though.

I tried logging in with the three other user accounts on this system, and none of them worked either. Also, running the check to make sure that dbus was running only told me that, in fact it was running. I'll try deleting the dotfiles, and if that fails I will reinstall Ubuntu. (It just so happens that I installed Ubuntu about 3 months ago. All of my files from my old Windows XP install were already backed up, so I'm not losing much, if not anything.)

Thanks for all the help though!
Sounds like reinstalling might be the simplest option.

---

### Post by jman1013 on 2008-08-28
Oh well, what can ya do!


Thank you for all you help though.
I REALLY appreciate it.

---

