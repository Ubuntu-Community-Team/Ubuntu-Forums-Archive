---
title: "Hardy Upgrade and NVIDIA issues"
date: 2008-07-18
forum: General Help
---

### Post by ffahog on 2008-07-18
I have the same problem described in the beginning of this thread:

[http://ubuntuforums.org/showthread.php?t=860993&highlight=remove+reinstall+nvidia+driver&page=2](http://ubuntuforums.org/showthread.php?t=860993&highlight=remove+reinstall+nvidia+driver&page=2)

I upgraded from 7.10 to 8.04 a few weeks ago and have been living with the consequences since. After trying the solutions presented in that thread, I am still in need of some help.

When I used the terminal to remove and reinstall the nvidia driver, I ended up with a usable screen resolution; however, there were still some problems. For example, anything utilizing accelerated graphics or 3d effects do not work. It is clear that all is not well.

(Also, there are a couple of odd side effects: For example, I believe the computer is having trouble detecting my monitor(?), and because of this I cannot run 'gksudo nautilus' to edit files and directories as a root user. Another weird side effect is that my log-in screen shows only about 60% of the screen, and when I try to "scroll" around the unseen portions of my screen with the mouse, it doesn't work.)

Now, as for the solutions. Envy doesn't appear to work for me. Whereas manually removing and installing nvidia-glx results in what I've described above, removing the driver (manually or with Envy) and reinstalling it with Envy results in the same 'low graphics mode' problem. I've tried different combinations of uninstalling, installing, restarting, and doing it manually and with Envy—none seem to work.

What's interesting is that I'm using Ubuntu with another hard drive (40gb) on this same computer. On my second hard drive, I installed 7.10 but immediately upgraded to 8.04, after which I installed the nvidia driver without a breeze. So I know that it can work in principle. It's just that my upgrade to the new kernel on THIS hard drive screwed with it, and I can't figure out the right steps to solve the problem.

Is there anyone that can help? I'd greatly appreciate it!

---

### Post by Mgiacchetti on 2008-07-18
clean installs are always the place to begin.   dont think youll need envy on a clean install, try the live cd and see if 8.04 notifies you that "proprietary drivers need to be installed for hardware to work correctly"

---

### Post by ffahog on 2008-07-18
> **Mgiacchetti said:**
> clean installs are always the place to begin.   dont think youll need envy on a clean install, try the live cd and see if 8.04 notifies you that "proprietary drivers need to be installed for hardware to work correctly"

A clean install typically means about 3-4 hours of work for me, moving important files around and backing up, getting everything reinstalled, reconfigured, the settings the way I like it, etc. No thanks. I don't buy the "clean install to fix it" philosophy.

Is there any further information I can give that would help someone diagnose my problem?

---

### Post by raysgremlin on 2008-07-18
I cant help with your problems, but many thanks for the "gksudo nautilus" command.
I have being trying to edit a file for the last 3 days (I am only a babby at this OS):popcorn:

---

### Post by ffahog on 2008-07-24
Bump: Was reminded of this today when I went to play XMoto. A simple game, but if the NVIDIA GeForce 3 isn't configured, I can't play it. :(

Can anyone help?

---

