---
title: "Installing a custom app to run on every boot."
date: 2008-08-23
forum: General Help
---

### Post by Xuor on 2008-08-23
I have written an application in Python. As part of the install process for this app, I wish to install certain commands to run on every boot.

I have packaged these into a single shell script. I have looked into using update-rc.d to run this script on every launch, but I don't seem to have the correct syntax to make it successful. All other suggestions I can kind involve hacking specific scripts such as /etc/rc.local, which I don't want to do. I have no desire to mess with anyone's potentially custom-made startup script.

Any thoughts? Suggestions? Ideas?

---

### Post by LateNiteTV on 2008-08-23
in /etc/rc.d/rc.local add the line:
```
/path/to/script
```

---

### Post by Xuor on 2008-08-23
> **LateNiteTV said:**
> in /etc/rc.d/rc.local add the line:
```
/path/to/script
```

Two problems with this:

1. I specifically stated that I don't want to hack specific user-configurable scripts. I want to allow for clean install/uninstall, with no fear of the user accidentally axing my startup command.

2. My stock Ubuntu installation does not include an /etc/rc.d folder. I have rc0.d through rc6.d, as well as rcS.d and the file rc.local

---

### Post by LateNiteTV on 2008-08-23
google.com

---

### Post by Xuor on 2008-08-23
> **LateNiteTV said:**
> google.com

Thanks, but I've tried that, as I alluded to in my first post. "all other suggestions I can [f]ind involve..." I can't find anything on Google, so I came to the Ubuntu community forums, looking for someone who knows more than I do and is willing to help with specific answers.

On the one hand, I appreciate the fact that you took the time to offer assistance. On the other hand, you would have been a lot more helpful if you'd read my request before answering it.

---

### Post by techstop on 2008-08-23
You can't add it to your list of startup programs under System>Preferences>Sessions>Startup Programs?

---

### Post by Xuor on 2008-08-23
> **techstop said:**
> You can't add it to your list of startup programs under System>Preferences>Sessions>Startup Programs?

*laughs* Sorry, but that's not what I'm looking to do. I have written a custom application of my own, for redistribution to others. I want to cause my custom installer to automatically set that application to launch on boot. Setting it to start on boot on my own personal system, via the System Preferences menu, is not what I want to do.

I want a portable, non-end-user-interaction-required method of setting up my program for auto-starting.

---

### Post by techstop on 2008-08-23
*laughs* at your attitude to someone trying to help. Good luck.

---

### Post by Xuor on 2008-08-24
*sighs* Ah, the vagaries of text-based communications. The laugh was not aimed at your attempt to help, merely at myself for my seeming inability to properly communicate what I wanted. My OP stated in what I thought were clear terms what I needed, but the only responses so far have failed to address my issue.

The laugh was certainly not intended to cause offense, and I apologize if you took it as such. As I said to the first respondent, I appreciate the fact that you took time to help. I'm simply rather frustrated that the phraseology of my original post seems either utterly opaque to the readers, or not worth the time to read and comprehend.

If I knew how to correct and further specify my question, I would do so.

---

### Post by lswb on 2008-08-24
The update-rc.d and similar scripts _are_ the standard methods for configuring the proper symlinks for running programs or services at startup. Installing a script in /etc/init.d with the proper symlinks in the rcx.d files is the standard method used by other software packages, allowing normal installation/removal by the package manager. Why not look at how those packages do it?

---

### Post by koenn on 2008-08-24
> **lswb said:**
> The update-rc.d and similar scripts _are_ the standard methods for configuring the proper symlinks for running programs or services at startup. Installing a script in /etc/init.d with the proper symlinks in the rcx.d files is the standard method used by other software packages, allowing normal installation/removal by the package manager. Why not look at how those packages do it?

yes, something like that.
your install procedure should place the startupscript in /etc/init.d, 
and create a symlink to it in the runlevel dirs (etc/rcX.d, with X=2,3,4,5 )
the symlinks have a specific form
eg  /etc/rc2.d/S30gdm -> etc/init.d/gdm
the S means Start, and the number defines the order in which startup scripts are run. you should probably use 99, so your app starts after all other runlevel-config is finished.

update-rc.d is a tool to automate such things. You can do something like
```
update-rc.d foobar start 99 2 3 4 5 . 
```
to create an S99foobar script in runlevels 2 3 4 5, assuming the script /etc/init.d/foobar exists.

---

### Post by Xuor on 2008-08-24
Thank you, sirs--both koenn and lswb.

At lswb: When it comes to creating a standard software package of my own, is there a particular packager creator that you would recommend? I've briefly checked the man page for dpkg, which seems to hand off build responsibilities to dpkg-deb. Is this a good option to use, or should I look elsewhere?

At koenn: Your instructions are pretty much what I've been looking for. I'd tried update-rc.d in the past, but without apparent success, and your help was appreciated. However, I still have an issue, in that my final script command is not being successfully executed.

The final command is intended to launch my python GUI application, but that's not happening. I'm wondering if it's because I'm trying to launch it before starting X11, but I don't know how to do it any other way.

I've tried both
```
update-rc.d foobar defaults 99
```
and
```
update-rc.d foobar start 99 2 3 4 5 .
```

(I've also run "update-rc -f foobar remove" between attempts.)

Thanks for your help.

---

### Post by lswb on 2008-08-24
I can't recommend a package creator, it's beyond my experience. However, I don't believe that a gui program is appropriate for an init.d script either. I didn't realize that's what you were talking about til now. If the program runs under X, then X must be running first, there is no way around that AFAIK. Is your app something like a panel applet? Are you meaning to have a full interactive application open whenever a user logs in? Does it require a particular window manager or DTE, (gnome, kde, xfce, etc) or just X? Does it need GTK or QT or ??? What about a system that doesn't run X on startup, like many servers?

Again, existing packages have a means to install commands in users session preferences or in the desktop menu; I don't know exactly how they do it, but the capability is there and can be observed.

---

### Post by mssever on 2008-08-24
> **Xuor said:**
> The final command is intended to launch my python GUI application, but that's not happening. I'm wondering if it's because I'm trying to launch it before starting X11, but I don't know how to do it any other way.
If you're running a GUI, then an init script probably won't work. For one thing, all init scripts run as root, and you probably want your GUI to run as a normal user. For another thing, you really don't have X available until a user logs in. (It isn't enough to simply wait for gdm to start.)

There are some scripts under /etc/X11 and /etc/gdm that you can evaluate to see if it will work. Of course, what works for gdm might not work for kdm, so you might need to handle both situations. Also, you might be better off adding it to the user's startup items. If you manipulate the gconf settings directly, you should be able to automate installation and uninstallation cleanly.

---

### Post by ilrudie on 2008-08-25
Copy the script into /etc/init.d/
Then sym link your script into the rc*.d that corresponds to the runlevel you want it to run at (probably rc2.d).  You will notice that all the scripts start with a capital 'S' and two digits in the rc*.d folders.  In order for your script to run it must also start with like that.  Lower numbers are run first so if your script requires anything else to be running make sure it has a higher number than what it requires.  Also this works for services/daemons so your gui line will need to be removed from the startup script and run once you login.  Possibly use a lanucher to make an icon?  Not sure how to autorun a gui app after login.

---

### Post by Xuor on 2008-08-25
> However, I don't believe that a gui program is appropriate for an init.d script either. I didn't realize that's what you were talking about til now. If the program runs under X, then X must be running first, there is no way around that AFAIK. Is your app something like a panel applet? Are you meaning to have a full interactive application open whenever a user logs in? Does it require a particular window manager or DTE, (gnome, kde, xfce, etc) or just X? Does it need GTK or QT or ??? What about a system that doesn't run X on startup, like many servers?

At lswb: Yeah, sorry about that. I didn't fully realize that was my original question, either. It took some testing and tweaking to determine that my pre-gui setup commands were actually being run. I thought everything was failing, not just the GUI launch. The particular application is a music player/server that will minimize to a tray icon on launch. It's window manager independent, but uses QT.

> There are some scripts under /etc/X11 and /etc/gdm that you can evaluate to see if it will work.

At mssever: I'm looking at the /etc/X11/xinit/xinitrc and /etc/X11/XSession files. It appears that the xinitrc file is the place to add my command, but adding the command there doesn't work. Manually sourcing xinitrc launches everything properly, but it doesn't work at login.

But again, I really don't want to hack any potentially user-customized files. Is there a way to simply add a file to the /etc/X11/initrc folder or someplace similar that would launch the file for me? Something as simple as dropping a shortcut into the Windows Startup menu?

> You will notice that all the scripts start with a capital 'S' and two digits in the rc*.d folders. In order for your script to run it must also start with like that. Lower numbers are run first so if your script requires anything else to be running make sure it has a higher number than what it requires.

At ilrudie: Thanks for the explanation. I had a vague awareness of what was going on, but that gives me a better feel for it.

---

### Post by mssever on 2008-08-25
> **Xuor said:**
> The particular application is a music player/server that will minimize to a tray icon on launch. It's window manager independent, but uses QT.In that case, you probably don't want something that applies system-wide. You want something that applies to a specific user.

> At mssever: I'm looking at the /etc/X11/xinit/xinitrc and /etc/X11/XSession files. It appears that the xinitrc file is the place to add my command, but adding the command there doesn't work. Manually sourcing xinitrc launches everything properly, but it doesn't work at login.

But again, I really don't want to hack any potentially user-customized files. Is there a way to simply add a file to the /etc/X11/initrc folder or someplace similar that would launch the file for me? Something as simple as dropping a shortcut into the Windows Startup menu?
I think you want to configure the startup items. In Gnome, you can do this from the sessions dialog. I haven't found where the settings actually live (it isn't in gconf for some reason). KDE doubtless has a different place (I don't use KDE, so I can't be much help, there). IceWM keeps its startup config in ~/.icewm/startup.

---

