---
title: "HOW TO:  Run Thunderbird in System Tray (Background)"
date: 2008-11-07
forum: General Help
---

### Post by shortcut144 on 2008-11-07
Tired of Thunderbird hogging your taskbar?  Shove him in the system tray then!

Be sure you actually have Thunderbird installed before attempting this.

This may work with other e-mail programs.

To do this.

Step 1.  Goto the terminal and enter:
```
sudo apt-get install alltray
```

This program puts programs in the system tray, really handy and lightweight.

Step 2.  Test it.  In the terminal type:
```
alltray thunderbird
```

In your system tray the cool logo should showup along with the thunderbird interface.  

That is pretty much it.  Now that you have the code "alltray thunderbird".  You can throw that into launchers and your startup commands to have thunderbird ready on startup.

While thunderbird is in the system tray, you will still get alerts when you have new messages.

Note:  Minimizing Thunderbird puts it in the taskbar.  When you close thunderbird, it does not actually close, it just goes to the system tray.  To really close thunderbird you need to right-click the tray icon and click exit.

Enjoy!

For Xubuntu users:  To add this item to your startup.  Goto Applications/Settings/Settings Manager.  Then click on "Autostarted Apps".  Click the "Add" button and input your details and the "alltray thunderbird" command into the command box.

Rest of you I dunno your startup apps, I have only use Xubuntu.  Maybe your nice community can tell you that.

---

### Post by xeriouxi on 2008-11-10
That's real nice info for people, shortcut144!

I recently posted a request to add a docking function like this for Evolution but it said it infringed the HIG for GNOME. I can respect where they are coming from but does that mean they should not give at least an option for the user? I feel the HIG is a little OTT in terms of flat-out saying "NO" to any optional functionality, personally. Here's hoping that Thunderbird might put native docking into version 3! =)

---

### Post by beercz on 2008-11-10
Thanks for this shortcut144.

Nice little app, really useful.

---

### Post by Devon64327 on 2009-10-17
devon@devon-desktop:~$ alltray thunderbird

Alltray: no system tray/notification area found.
I will wait..... I have time....

In the meantime you may add a system tray applet
to the panel.



why is my terminal talking to me?

---

### Post by tetsuoharry on 2009-10-18
thought I'd throw in a simple script for those using alltray and launching from docks, desktop icons etc...

basically it stops alltray launching another instance of the application

```

#/bin/bash

if [ "$(pidof nameofapp)" ]
then
nameofapp
else
alltray nameofapp -s
fi

```

call the script what you like ie alltraythunder

```

chmod a+x alltraythunder
sudo mv alltraythunder /bin

```

then simply use the name of the script to launch it 

I'm sure there is an easier way to do this, but my ways more fun :D

harry

---

### Post by Dirtpile on 2009-11-01
An even easier way:

FireTray add-on.  Use version 1.11 though, 2.+ has an issue that causes it to open in the next workspace to the right or off screen if you only have one workspace.

You can download it here: [http://code.google.com/p/firetray/downloads/list](http://code.google.com/p/firetray/downloads/list)

And yes I tried alltray but just couldn't get it to work.

---

### Post by Algus on 2009-11-01
Thank you for posting this.  I was using MinimizetoTray in Windows but it doesn't work to well in Windows.  

This will be super helpful for me.

---

### Post by Crowder on 2009-11-02
hey guys, i just made an awesome discovery (for kde users). All you have to do in the kde desktop is open the menu editor - right click on the application menu to get there. From that point, just find the shortcut, don't change the command, just check the box that says "place in system tray." Voila!

Isn't that great?

---

### Post by Crowder on 2009-11-02
> **Crowder said:**
> hey guys, i just made an awesome discovery (for kde users). All you have to do in the kde desktop is open the menu editor - right click on the application menu to get there. From that point, just find the shortcut, don't change the command, just check the box that says "place in system tray." Voila!

Isn't that great?

I'm talking about KDE4 under karmic by the way.

---

### Post by kkady32 on 2009-11-02
cann use thunderbird-traybiff too.

---

### Post by Fighting_Ace on 2009-12-08
> **Crowder said:**
> I'm talking about KDE4 under karmic by the way.

Thnx very much. This was the easy solution I wanted ;) .

---

### Post by obscurant1st on 2010-05-02
i love you dude.
I was searching for it for long time!! :)

---

