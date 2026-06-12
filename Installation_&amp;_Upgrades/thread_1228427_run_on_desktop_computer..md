---
title: "run on desktop computer."
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by SxNdave on 2009-07-31
Hi,

I've been a user on and off of Ubuntu on my desktop machine for some time, I recently acquired a Samsung NC10 netbook with XP preloaded and decided I would run Ubuntu on it instead of the main system. I found the netbook remix which I must say I'm extremely happy with it, the home screen makes the system very easy and intuitive to use. Top stuff!

Recently I've been running Win7 RC on my desktop instead of Vista on my windows partition and have become quite at home with the new toolbar that everything can be pinned to for quick navigation. There are some things I can't live without windows for but for everything else I'm trying to use Linux based OS's so I can learn more about them :).

I see the netbook remix as an ideal way for me to quickly get the point and shoot kind of operation I've been getting from my win7 install on Ubuntu and would like to install it onto my main machine. From some other posts around I have assertained that the remix can be added as a selection of patches from the package manager so I belive I have 2 options to get this going:

1, Install the Netbook Remix onto the machine and add the required drivers (nVidia Restricted etc...)

2. Install the standard 9.04 on the main machine and apply the Netbook Remix patches vis the package manager.

Any advice or pointers in the direction of some reference material on this would be appreciated.

Is the underlying OS any different between the 2 versions?

While I'm here, is there a keyboard shortcut to display the home screen, or a way to set one up/record a macro? Failing that is there a library that is local to my machine that I can use to access the method that is called when the 'minimize all/home screen' toolbar button is mouse clicked.


Sorry that seems a little long winded now on read-back.

---

### Post by snowpine on 2009-07-31
Netbook Remix should run just fine on a "non-netbook" computer, assuming it meets the minimum system specs. You should be able to install it in either of two ways:

1. Install Netbook from scratch: [https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)
2. Convert an existing Ubuntu install with a simple terminal command:
```
sudo apt-get install ubuntu-netbook-remix
```

---

