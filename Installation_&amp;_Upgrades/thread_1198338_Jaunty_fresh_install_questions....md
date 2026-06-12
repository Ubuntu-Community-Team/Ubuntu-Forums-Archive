---
title: "Jaunty: fresh install questions..."
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by neocortex on 2009-06-27
Hello ALL!
After some time wandering around in various Linux distributions, I just installed Jaunty. I was so happy back with Dapper 6.06. Then, I was a bit disappointed with some latter versions (7.10, 8.04). Then, turned to Debian, Fedora etc., and now I am back. It seems that Ubuntu is one of the most solid Linux end-user distributions if you care for stability (not too much for bleeding edge and hobby, but for work) and good support. And Jaunty behaves very nice.
Now, just two questions to make minor adjustments:
1) How to make Bluetooth permanently off? It always starts on when I (re)boot.
2) I would like to purge Evolution and to install Thunderbird. How to do the first (purge Evolution)? I know that Evolution is deeply embed ed in Gnome and that is the thing I like with minimal Debian installation, where only evolution-data-common is needed.

Thanks in advance,
PM

---

### Post by philcamlin on 2009-06-27
sudo apt-get purge evolution 

sudo apt-get install thunderbird :popcorn:

---

### Post by Therion on 2009-06-27
I'm running Karmic at the moment, but I'm thinking you should be able to go to System/Administration and click on "Services".  From there you can select/deselect what services you want running at startup.  Bluetooth being one of them.

As for Evolution, is it necessary that you totally purge it out of existence?  Or could you simply remove it from your menus and forget it's there?  You can right-click on the Applications menu and then "Edit Menus" to remove all references to Evolution.  That would be the simple solution.

> **philcamlin said:**
> sudo apt-get purge evolution 
That should be either:```
sudo apt-get remove evolution
```

or

```
sudo apt-get remove --purge evolution
```
if you want to remove the configuration files too; but for the reasons you state above, the simpler solution would be to remove it from the menus.

---

### Post by starcraft.man on 2009-06-27
Go to Preferences > Startup Apps > Uncheck the blue tooth manager.

System > Administration > Services > Uncheck bluetooth.

And if it's running on the current session just open the system monitor under admin and kill it as a process (bluetooth-applet).

Second question a bit of a problem. As you noted it's deeply embedded in GNOME. I'd just leave it as is and install thunderbird by your preferred means from the repositories. Then just set it to be your default client for firefox mailto links and ya should be good. I personally just leave thunderbird open on one of my boxes constantly to get my mail as it comes in. Oh and remove it from your menus, by right clicking applications and unchecking it from the submenu internet.

---

### Post by neocortex on 2009-06-29
I did both things:
> Go to Preferences > Startup Apps > Uncheck the blue tooth manager.

System > Administration > Services > Uncheck bluetooth.
But my bluetooth light is still on. What now? I just simply want to have my bluetooth off, and a possibility to turn it on if and when needed.

Thanks!
PM

---

