---
title: "Edgy crash on Dell Latitude Laptop"
date: 2007-02-12
forum: Hardware &amp; Laptops
---

### Post by cliowa on 2007-02-12
I had Ubuntu 6.06 working fine (absolutely zero problems) on my Dell Latitude Laptop and recently I performed a distro-upgrade (using apt-get) to 6.10, which doesn't work anymore.

Now when the Laptop boots I get to the login screen, but then it somehow shuts down, but not really: it goes into some kind of hibernating mode, where I can get it back on for a second, but then it switches off again. I never get to logging some user in.

The exact same thing happens if I boot using an older kernel.

If I boot in recovery mode it tells me that "Assembling Raid Arrays" failed.

As I'm relatively new to linux, I don't have the slightest clue as to what to do.

(I already googled for hours and looked up the Raid Arrays thing, which seems to be a known bug; nevertheless it might be useful)

Best regards and thanks
Cliowa

---

### Post by cliowa on 2007-02-12
Might installing Xubuntu (in command line mode) help?

Thanks for any help...Cliowa

---

### Post by saint1943 on 2007-02-12
I also have a dell latitude laptop (l400) and it does this same thing.  I can not login because the sleep mode kicks in after about 2 seconds at the login screen.  Please help.

---

### Post by cliowa on 2007-02-14
Maybe this problem is caused by some xserver issues. I already gave that a try and installed the latest xserver. Do you think that getting an older version might help? How would I do that?
Thanks for any help...Cliowa

---

### Post by cliowa on 2007-02-14
Actually I don't think it's the xserver.

I started the xserver from command line mode as root after a recovery boot. It works fine.

The problem I have is that when I log out and get to the "real" login screen it goes to sleep.

Several times I got an error message complaining that
"There was an error starting the GNOME Settings Daemon.
Some things, such as themes, sounds, or background settings may not work correctly."

Do you think this could have anything to do with the problem I'm facing?

Another question: When I'm in recovery mode I can select (System-> Preferences) "Install" which "installs this system permanently to my hard drive", as if I were using a Live CD, which clearly I'm not. So: can I safely do this, or do I have to fear the loss of my personal files?

Any help would be appreciated...Cliowa

---

### Post by jfdarv on 2007-03-28
[http://www.ubuntuforums.org/showthread.php?p=2366306](http://www.ubuntuforums.org/showthread.php?p=2366306)

---

