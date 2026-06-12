---
title: "New video card/monitor issues"
date: 2008-05-30
forum: Hardware
---

### Post by Sham885 on 2008-05-30
I upgraded my video card to an ati x1650.  After getting a blank screen when trying to load ubuntu I selected recovery mode from the startup list and used the "sudo dpkg-reconfigure xserver-xorg" command and selected the generic fglrx driver.  I had issues selecting the correct settings for my Pixo AT500S vga monitor.  It just kept saying out of range, even after using the suggested settings listed online, except when I put it on a really low size and refresh rate.  Then it went to bright white and I could barely make out some shapes.  Playing with monitor settings didn't fix it and I was forced to reboot again.  This morning (I gave up at 2am last night) I got out my dell crt monitor and reconfigured with that.  It autodetected, I rebooted, it showed the ubuntu loading picture, went to text for a scan, and then went blank and stayed that way.  So I'm back on xp, actually in safe mode, which is having issues again with virus and adware despite multiple antivirus programs so it won't run normally.  I can barely do anything.  I'm lucky to get a webpage to load and a program to open.

What do I need to do to fix ubuntu?  Eventually I'd like to run dual monitors since I have both the crt and vga out here anyway and my card supports it.  First I need to get it working on one monitor though.

---

### Post by Sham885 on 2008-05-30
Is there a way to load ubuntu with internet connection in a text only mode?  I can use recovery mode to give text commands but it does not connect to the internet so I can't download updates to the driver.

---

### Post by hotweiss on 2008-05-30
> **Sham885 said:**
> Is there a way to load ubuntu with internet connection in a text only mode?  I can use recovery mode to give text commands but it does not connect to the internet so I can't download updates to the driver.

I'd use the EnvyNG drivers:

> sudo apt-get install envyng-core

sudo envyng -t

This will install the Catalyst drivers from terminal.

---

### Post by Sham885 on 2008-05-30
I can't get things off the internet in ubuntu.  Unless it came on the live cd I don't have it.  That seems to be the problem.  I did have internet when ubuntu would load properly but I just tried to update the drivers from the command prompt I was using and it didn't have internet.

---

### Post by Sham885 on 2008-05-31
Well I sort of got it to boot from live cd.  I couldn't read the text.  It was just squares.  I hit ctrl+alt+F1 to see what messages it was giving me and then went back and tried to enter a username but nothing I entered worked when I know what my username is.  I couldn't type anything after hitting ctrl+alt+F1.  I hit every other F key :lol: got it to show various screens but nothing I could type a working command into.  I'm about ready to wipe it and reinstall from scratch. ](*,)

---

