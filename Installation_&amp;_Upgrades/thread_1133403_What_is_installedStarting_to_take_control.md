---
title: "What is installed/Starting to take control"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by Vock on 2009-04-22
Hello all, and in advance thanks for all the help so far and the help i'm about to recieve.

I've been playing around and getting used to Ubuntu for a year now from switching from windows and want to learn a bit on how to take better control of my system, by first streamlining it a bit, the only problem is that I haven't a clue what to do.

I'm used to windows, where everything that is installed is easily found in the nice add/remove programs list, but that doesn't exist here as far as I know of. I'm aware of top and system monitor to see what's running on my computer at any time but what I would like to know is:

- How to find out what drivers are installed and actually being used, vs. the ones that are installed and not being used, and how easy is it to remove them?
- Do I really need pulseaudio and Alsa installed?
- Is there any way to find out what software has come installed and is it really as simple as deleting folders to remove software? Anything else that needs removing beyond config files? (nothing like registry keys etc?)


Thanks again

---

### Post by cariboo on 2009-04-22
Synaptic package manager will give you a list of installed programs when you click the status button. To find what modules are loaded, open a terminal and type:

```
lsmod
```

Remember one of the big differences between Windows and Linux is that installed programs don't use any ram until they are needed. 

To turn off unneeded service go to System-->Preferences-->Startup Programs and uncheck the programs you don't want to run at startup, then go to System-->Administrations-->Services, click the unlock button and stop the services you don't need.

---

