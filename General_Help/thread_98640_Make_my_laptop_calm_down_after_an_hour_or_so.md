---
title: "Make my laptop calm down after an hour or so"
date: 2005-12-03
forum: General Help
---

### Post by berlinbrown on 2005-12-03
I don't what I am looking for exactly.  But, I know my monitor/machine desktop suspend down after an hour of usage.

How can I get my laptop to do the same.  Also, is there any damage or anything incurred in the event I just let a laptop run continuously.

Am, I looking for acpi configurations/suspend/hibernate settings?

It is an IBM thinkpad 21 - 800mhz with ubuntu 5.10 updated to kernel 2.6.10

---

### Post by shawnzyoo on 2005-12-03
i use a program that i got called Power Preferences
it allows you to set when it sleeps
i found it in this forums

---

### Post by berlinbrown on 2005-12-03
Is that found through synaptic manager

---

### Post by berlinbrown on 2005-12-04
Ok, I found it and I think I am getting closer.

So, in the event somebody has a similar issue.  Well, it seems like the default power management/screen saver is just for desktops?  The screen saver has options for powermanager, but I think that is just for the monitor.

I couldn't find the desktop oriented harddrive shutdown, I know it is there though.

For the laptop, this is what I am doing.  I went for gnome-screensaver and the gnome-power-manager.  It looks like there might be a conflict between this one and the older screensaver.  I disabled gnome-saver for the time being.

gnome-power-manager doesnt boot at launch.  I can start it from a terminal, and it comes up on the desktop panel.  It has the suspend/hibernate options.  I tested those, it goes into hibernate/suspend mode; but I can't bring the system back up?
So, I have to reboot. 

So that is where I am at now.  I havent tested automatic mode.

---

### Post by berlinbrown on 2005-12-06
I gave up.  I couldn't get my laptop to launch in power management mode. Hibernate, sleep.  I hope all that powermanagement stuff is just a myth.

I wound up just having gnome-screensaver turn off my laptop screen.

I guess my problem.  The default powermanagement doesnt like the newer stuff.  For example.  I have power-managemer by default that doesnt have any hibernate/sleep functions.  So, I enabled the gnome-powermanager which has hibernate/sleep in an hour, but it won't start on bootup?

Anybody solve this with breezy and mainly a thinkpad(800mhz)

---

