---
title: "[SOLVED] Display problems intel 810e chipset"
date: 2008-12-26
forum: Installation &amp; Upgrades
---

### Post by preacher2B on 2008-12-26
I'm having issues with a new install of Ubuntu 8.10 on an older pc. I have checked my cd for errors and have found zero. I ran diagnostics on my hard drive, quick and extended, which came up with zero problems.

So here's the issue...
I can boot up normally to the login screen with no problems. After signing in, my display starts to act up.

First off when I drop-down the menus I get distorted colors, but the buttons act properly.

When I opened the terminal from accessories, I get a blank white screen. There is nothing but white in the upper left quadrant of my screen. The main menu bar along the top is active (I can still use it), but **I cannot do anything via the terminal**.

I have installed all updates. Then I tried to reinstall. No success. 

I'm running a P3 933mhz, 384 MB RAM, 40 GB Western Digital HD, on an old Dell board (I think it's Foxconn), which is mainly a Dimension L933r.

Thanks for the help in advance. (This one is for my kids)

---

### Post by infamous-online on 2008-12-26
I have to ask, what video card are you using? Is it the built-in vga, or an aftermarket pci card? 

The reason I ask, because I have an old IBM machine with similiar specs as your pc, but I never received that error in question. So what exactly is it saying or doing sinc you're not allowed to view your terminal?

Last question, have you had a look at the event viewer? I know that's what it's called for windows but linux has something similiar to that, so see if you can check that and see what error it says.

---

### Post by linuxbastard on 2008-12-26
Hi,

Have you tried changing screen resolutions?  Also disabling any desktop effects?

---

### Post by preacher2B on 2008-12-26
> **infamous-online said:**
> I have to ask, what video card are you using? Is it the built-in vga, or an aftermarket pci card?

The video is an onboard [Intel 810e]("http://www.intel.com/design/chipsets/810/810e.htm") chipset.

> So what exactly is it saying or doing sinc you're not allowed to view your terminal?

By terminal I am referring to the "command line" terminal found under Applications-->Accessories-->Terminal.

It shows up as a white screen in the top-left quadrant of my screen.

I have discovered that I can write in commands, but I cannot see what I have written. I have not had success with copy and paste, but I have been able to run: ```
sudo nautilus
```

I have tried running nano, but it hasn't worked. There may be an error message, but I can't read it.

I don't know if all this helps, but I hope it gives you an idea of what is and isn't happening.

---

### Post by preacher2B on 2008-12-26
> **linuxbastard said:**
> 
Have you tried changing screen resolutions?

Yes and I my screen was resized incorrectly. I lost all of my desktop functions as well. Ctrl-Alt-Bckspc got me back to the login screen and back to my earlier dilemma.

> Also disabling any desktop effects?

Just tried it **AND IT WORKS!**:D Such a simple answer, I guess I'm a little rusty.

Thanks for the help.

---

