---
title: "Ubuntu cannot load graphical interface"
date: 2008-07-28
forum: General Help
---

### Post by PharmaPhunk on 2008-07-28
Ok so I'm running Ubuntu 6.06 (I do plan on eventually upgrading) and everything has been going great. Everything seemed generally normal when I first turned on the computer today, however right before the login screen came up, the screen turned blue and a grey box informed of this error:

```

Failed to start the x server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem YES NO

```

Well I went to yes, I was asked for my username and psswrd which I provided, however it didn't "diagnose" anything. I was just staring at a terminal.

I am still very new to Ubuntu and linux in general so I don't have the slightest clue as to how to fix this. Any help will greatly appreicated(sp?).

---

### Post by ellgor on 2008-07-28
Hi,

Try this, when you reach the terminal type in the following:

sudo dpkg-reconfigure xserver-xorg

it will probably ask for you password, enter it and a new window will open.
Now unless you know what specific items you have (graphics card etc.) you can accept the defaults presented (use the arrow keys to move up and down the options, and the right arrow will highlight the OK, and enter accepts) until you come to the resolution settings, at the top will be 1270, or similar, working their way down, if you see a star against anything higher than 1024 delete it by using the spacebar, continue till the end and exit.
If a message pops up saying that a system restart is required do so, if not type in : 

sudo reboot

Upon restart things should be back to normal, hope this helps.

Regards, Ellgor.

---

