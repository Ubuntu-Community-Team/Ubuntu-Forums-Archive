---
title: "How to properly install a new video card"
date: 2015-07-22
forum: Hardware
---

### Post by arberto2 on 2015-07-22
Hi!
I've bought a new video card, an MSI Geforce GTX 750.
My pc's got dual boot, so I turned it off, I've installed the card and I rebooted the pc.

On Windows everything gone fine.

On Ubuntu I've found an huge problem: it wont start.
It actually starts, but I can't see nothing because the monitor is flashing so fast that I can't even see what's behind. Like when you're updating your video driver, but longer.
And after 15-20 minutes like that a login form appear... but I removed the login form at the startup! 

Anyway, when I insert the password it turn back to flash fast for 15 minutes than the login again... 

Did I fu**ed up my Ubuntu? 
How can I fix it?

Thanks!

---

### Post by Bashing-om on 2015-07-22
arberto2; Hello;

Maybe it is just a case of removing the old driver, and installing the new driver for the new card.
What was the card that you replaced, so we can track down the old driver. ?
And to properly install a driver we need to know the release that you are running .

I can anticipate that you will have to utilize a boot parameter ' nomodeset' OR the recovery console to effect repairs.
We will get to that when the time comes .

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]it is fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by arberto2 on 2015-07-22
Actually I haven't  installed any video driver by myself, I was using the drivers Ubuntu found during installation for Intel i5, I had no addictional video card before.

Should I use recovery console for install the correct driver?

---

### Post by ajgreeny on 2015-07-22
At the grub menu hit "e" when the Ubuntu line is highlighted.  This allows you to edit the grub entry for Ubuntu.

By using the cursor keys go to the kernel line where "quiet splash" is shown at or near the end, and add nomodeset to the list, ie giving you "quiet splash nomodeset" or you can just replace quiet splash with nomodeset, then use Ctrl+X to boot.  This change will only be used for this one boot, and may give you a low resolution display, but it should allow you to use the Additional Drivers utility to add the appropriate driver for your new card, after which nomodeset should not be needed any more.

EDIT:
It seems that Bashing-om (see below) knows a lot more about nvidia cards than I do, never having used one, so perhaps go with his suggestion.

---

### Post by Bashing-om on 2015-07-22
arberto2; Yeah;

I do expect that if you boot to the recovery console; enable networking there, and "resume normal boot" you will get to the GUI - degraded graphics -. Here active "Additional Drivers" from Software Sources and install the recommended driver . 
IF you are on 14.04, the latest drivers are not available, and we will have to redo this procedure from a terminal, and add a PPA to obtain the required driver. Release 15.04 foes contain the latest drivers .

If required
[INDENT][INDENT]we can do that too
[/INDENT][/INDENT]

---

### Post by SeijiSensei on 2015-07-22
I have the same card, and it is working with the nvidia-331 package in the 14.04 repositories.
```
sudo apt-get install nvidia-331
```

For more details on how I dealt with this card, and some additional problems I faced concerning HDMI audio, see this thread: [http://ubuntuforums.org/showthread.php?t=2287674](http://ubuntuforums.org/showthread.php?t=2287674)

---

