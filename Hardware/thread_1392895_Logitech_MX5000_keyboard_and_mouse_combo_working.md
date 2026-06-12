---
title: "Logitech MX5000 keyboard and mouse combo working"
date: 2010-01-28
forum: Hardware
---

### Post by rossco on 2010-01-28
Hi all,

I have a Logitech MX5000 keyboard and mouse combo.  I had not been using it for a long time since originally trying to get it to work with Ubuntu a few years ago and not having any success.  I decided recently to blow the dust off it and give it a try on 9.10 Karmic Koala.

I was happily surprised that Bluetooth has improved markedly in the latest release(s).  Once the Bluetooth is up and running I can scan and find my mouse and keyboard with minimal fuss (I think the keyboard took a number of tries to get going).  I installed KeyTouch from the repositories and I can access a lot of the multimedia keys as well!  Now I might try playing around with mx5000-tools to see if I can make use of the lcd display on the keyboard.

I have one problem though which if solved would make everything perfect.  The supplied USB bluetooth dongle has two modes, an embedded and bluetooth mode.  In the former mode it is supposed to emulate a wired keyboard/mouse to the OS while in the latter it acts in bluetooth mode.  When the system boots or if you just plug in the dongle while running it doesn't switch to bluetooth mode.  Is there a way to get it to do this?  I believe there is a utility hid2hci which was in one of the bluetooth packages but got moved to udev-extras (which isn't provided in Ubuntu 9.10).  Is this what I need to use to switch modes?  

Currently the only way to get it to go into bluetooth mode is to hold the connect button on the dongle down while (re)inserting the dongle.  This is not an ideal solution as I want to plug the dongle in the back of my desktop where it will be relatively inaccessible.

---

### Post by rossco on 2010-02-01
Hi all,

Just thought I'd come back to this page and say that I think that I've found the solution.  Based on the information here:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=567237]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=567237")

I changed the 70-hid2hci.rules file as described and the dongle now seems to switch into bluetooth mode without having to hold in the button.  I'm still going to continue testing this solution to confirm that it works.

Also since the link I posted is attached to a bug report I may reply to it once I'm satisfied that it works all the time and it may get committed.  So eventually this should work out of the box!

---

### Post by schmidtbag on 2010-02-14
hey have you gotten the screen to work?  last time i tried using the mx5000-tools, it wasn't compatible with ubuntu 9.10 due to hidraw being changed to hiddev, or vise versa (i forget, its been a while)

---

### Post by rossco on 2010-02-15
I have installed the mx5000-tool's using checkinstall but it seems to have put the library in a non-path location so I get the following error:

```
mx5000-tool 
mx5000-tool: error while loading shared libraries: libmx5000.so.0: cannot open shared object file: No such file or directory
```

I haven't tried fixing this error yet.  I'm still enjoying the fact that the keyboard and mouse are working.  If I get it to work I'll post back.  It doesn't look like the mx5000-tool's code has been worked on in a long time so we might be stuck.

---

### Post by schmidtbag on 2010-02-15
i've contacted the creator of the program and he basically said that he's too lazy to spend 2 hours (according to him) to make the drivers work for newer distros.  i didn't get the same problem as you but it is a bit inconvenient that this is happening.

i'm aware that lcdproc has support for it but for some strange reason, the drivers don't exist in it.  i got lcdproc for this vfd i have and it also just happens to not have the driver for that.  it has all the drivers but those 2 and 1 other, which i find very coincidentally inconvenient.  i didn't try the debian package for lcdproc but maybe you can get some luck with that instead

---

### Post by rossco on 2010-02-16
I managed to solve the error I was getting.  Trick was to run 'sudo ldconfig'.  Not sure if it works after reboot or not.  Doesn't seem to be a PATH variable thing as changing that did not fix anything.

Too bad the original dev isn't interested in fixing this.  Running any commands with 'sudo mx5000-tool ...' doesn't do anything - no errors either.  Maybe the original dev could outline what he thinks needs to be changed to make things work and we could approach someone else for a fix?  Maybe it would be possible to get the code included in lcdproc?  Then its likely to have good support for the future.

---

### Post by schmidtbag on 2010-02-16
so are you saying you currently have the screen working in ubuntu 9.10?

---

### Post by rossco on 2010-02-16
No.  When I try and run any command nothing happens, the prompt returns without error (and without doing anything on the lcd display).  I was just saying I managed to get around the error I posted above where it was complaining that it couldn't find the library file (libmx5000.so.0).

---

### Post by schmidtbag on 2010-02-16
well like i said, its because of the device file.  i can't remember if its /dev/hidraw or /dev/hiddev that its looking for, but one of those was replaced with the other.

i never tried this, but you could try using a symlink.  i can't imagine the device files are significantly different from each other and a symlink might just trick it into working

---

