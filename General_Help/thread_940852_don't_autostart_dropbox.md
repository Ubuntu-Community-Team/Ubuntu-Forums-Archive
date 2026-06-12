---
title: "don't autostart dropbox?"
date: 2008-10-07
forum: General Help
---

### Post by smain on 2008-10-07
Hi all

I've installed the Dropbox for Nautilus plugin... now whenever I boot up my computer, the dropboxd service starts too..
How can I remove this autostart, anyone that uses it who knows?... Can't see the service in sysv-rc-conf, and neither in

Smain

---

### Post by infinito on 2008-10-14
dropboxd starts with your GNOME session (in fact, when Nautilus is launched). You can find some tips on how to disable it in here: 
[http://forums.getdropbox.com/topic.php?id=3575](http://forums.getdropbox.com/topic.php?id=3575)

---

### Post by wobblyheadedjon on 2008-10-14
I have the opposite problem.  Suddenly, my dropbox has stopped launching at start up and I have no idea why.  It worked for a few days and suddenly stopped.  I am running Intrepid, 32 bit.  Any way to get it to start again at startup

---

### Post by infinito on 2008-10-14
> **wobblyheadedjon said:**
> I have the opposite problem.  Suddenly, my dropbox has stopped launching at start up and I have no idea why.  It worked for a few days and suddenly stopped.  I am running Intrepid, 32 bit.  Any way to get it to start again at startup

Does the tray icon show on panel?

---

### Post by wobblyheadedjon on 2008-10-14
> **infinito said:**
> Does the tray icon show on panel?

no, and I have no idea how to manually start dropbox either...so I'm kind of up the river...

---

### Post by infinito on 2008-10-14
> **wobblyheadedjon said:**
> no, and I have no idea how to manually start dropbox either...so I'm kind of up the river...

Try to reinstall the [dropbox nautilus extension]("http://www.getdropbox.com/download?dl=nautilus-dropbox-packages/0.4.1/nautilus-dropbox_0.4.1-1_i386_ubuntu_8.04.deb") and to remove the dropbox daemon folder (rm -fr ~/.dropbox-dist), then quit nautilus nicely and launch it again (nautilus -q; sleep 2; nautilus) to see if it gives you any error message.

---

### Post by wobblyheadedjon on 2008-10-14
> **infinito said:**
> Try to reinstall the [dropbox nautilus extension]("http://www.getdropbox.com/download?dl=nautilus-dropbox-packages/0.4.1/nautilus-dropbox_0.4.1-1_i386_ubuntu_8.04.deb") and to remove the dropbox daemon folder (rm -fr ~/.dropbox-dist), then quit nautilus nicely and launch it again (nautilus -q; sleep 2; nautilus) to see if it gives you any error message.

That seems to have taken care of my problem.  At least it loaded at start this first time around.  thanks a ton.  Good luck on figuring out the origional problem of this thread.

---

### Post by mia.king on 2009-03-12
I agree, I dislike people starting things automatically, esp if it is a connection to the internet.

What does irritate me somewhat, is that is is apparently easier for a windows user to stop dropbox from autostarting (startup folder)... but for ubuntu... there is no easy way!!

The current method seems to be either uninstall it or disable it after it has started up, for it hides somewhere (perhaps in the ?nautilus / ?ubuntu desktop boot up sequence). 

This seems somewhat ironical to me. I expected there to be one line to be deleted from an obscure file that would fix this problem. But little do I know.


--------------
Apparently:

To stop the dropbox daemon: (won't affect the icon in tray)

- click on tray icon: stop dropbox
- start-stop-daemon -o -c <user> -K -x /home/<user>/.dropbox-dist/dropboxd
- killall dropboxd


To restart daemon:

- click on tray icon: start dropbox
- start-stop-daemon -b -o -c user -S -x /home/user/.dropbox-dist/dropboxd


To automate this:
- Ubuntu8.10Menubar ! System ! Preferences ! Sessions
- add new startup item
- start-stop-daemon -o -c <user> -K -x /home/<user>/.dropbox-dist/dropboxd
 

[Thanks Cam: [http://forums.getdropbox.com/topic.php?id=4409&replies=2#post-30310]](http://forums.getdropbox.com/topic.php?id=4409&replies=2#post-30310])

---

### Post by Pifilatakanemu on 2009-12-15
any news on this topic?
i'd rather prefer to start dropbox by myself whenever i need it....

---

### Post by eph2 on 2010-05-31
Hello, 

i removed dropbox icon from system tray. How to get it back? I have tried to re-install nautilus-dropbox package without no success. 

Dropbox is working fine. Only lost one icon. :P

---

