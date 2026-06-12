---
title: "Questions about sharing a /home partition among *buntus"
date: 2008-09-07
forum: General Help
---

### Post by Piraja on 2008-09-07
Dear Aysiu,

first and foremost: thanks a million for your the superb Psychocats tutorials! 

I have a question and a suggestion concerning the excellent "Create a separate home partition" guide. 

The suggestion is that the paragraph beginning with "If you find that you are running out of room on your old partition and you're pretty confident everything is working as it should be" might have the "If" etc. somehow highlighted (e.g. "[COLOR="Red"]IF AND ONLY IF[/COLOR]..."). 

Must I tell you why...? Well, I had my first try a couple of months ago and might have been a little too impatient, copy-pasting the commands... The second try was a success, anyway.

The question is prefaced as follows: Now, having Ubuntu with Gnome (and Fluxbox as a very nice WM option) on a 20GB partition (sda3) of my laptop and a separate 10GB home partition (sda1), I decided to install Xubuntu on another 10GB partition (sda6). Just for another try (I had Xubuntu earlier but uninstalled it in favor of the Gnome flavor; I have also tried out Linux Mint and Fluxbuntu on this "experiment" partition, sda6).

Now comes the question itself: How do I make the separate home partition (sda1) _the_ home partition of the Xubuntu installation, too (sda6)?

Regards,

Pajari (aka Piraja)

P.S. (edit): Could it be that all I have to do is to add the following line to the fstab file on sda6:

```
/dev/sda1 /home ext3 nodev,nosuid 0 2
```

P.P.S. (edit 2): Well, obviously not, if I don't want to have the hidden configuration and profile files too to mess up Xubuntu...

P.P.P.S. (edit 3): Maybe I'll just copy those directories and documents I want to have on sda6 and keep them in sync (with Unison).

---

### Post by aysiu on 2008-09-07
> **Piraja said:**
> Dear Aysiu,

first and foremost: thanks a million for your the superb Psychocats tutorials! 

I have a question and a suggestion concerning the excellent "Create a separate home partition" guide. 

The suggestion is that the paragraph beginning with "If you find that you are running out of room on your old partition and you're pretty confident everything is working as it should be" might have the "If" etc. somehow highlighted (e.g. "[COLOR="Red"]IF AND ONLY IF[/COLOR]..."). 

Must I tell you why...? Well, I had my first try a couple of months ago and might have been a little too impatient, copy-pasting the commands... The second try was a success, anyway.

The question is prefaced as follows: Now, having Ubuntu with Gnome (and Fluxbox as a very nice WM option) on a 20GB partition (sda3) of my laptop and a separate 10GB home partition (sda1), I decided to install Xubuntu on another 10GB partition (sda6). Just for another try (I had Xubuntu earlier but uninstalled it in favor of the Gnome flavor; I have also tried out Linux Mint and Fluxbuntu on this "experiment" partition, sda6).

Now comes the question itself: How do I make the separate home partition (sda1) _the_ home partition of the Xubuntu installation, too (sda6)?

Regards,

Pajari (aka Piraja)

P.S. (edit): Could it be that all I have to do is to add the following line to the fstab file on sda6:

```
/dev/sda1 /home ext3 nodev,nosuid 0 2
```

P.P.S. (edit 2): Well, obviously not, if I don't want to have the hidden configuration and profile files too to mess up Xubuntu...

P.P.P.S. (edit 3): Maybe I'll just copy those directories and documents I want to have on sda6 and keep them in sync (with Unison).
Your post kind of confuses me. And, honestly, I'm not really a separate /home expert. The tutorial is adapted from another tutorial I don't fully understand. I've used it once myself (just ot make sure it works), but I don't know enough to troubleshoot that one.

Mind if I make yours a support request in its own thread?

---

### Post by Piraja on 2008-09-07
> **aysiu said:**
> Mind if I make yours a support request in its own thread?
No, I wouldn't mind. But I'm not sure whether this is really a high priority issue. As Carthik says in her/his(?) post at [Ubuntu blog]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/"), "Having the '/home' directory tree on it&#8217;s own partition has several advantages, the biggest perhaps being that you can reinstall the OS (or even a different distro of Linux) without losing all your data." 

That makes sense. But, as I finally figured out through an empirical experiment of adding the mentioned line into the fstab file (of the fresh Xubuntu install on sda6), the configuration files in the /home partition (say, sda1) affect indeed, not only the original install (as in my case, on sda3) but also the different distro install (on, say, sda6).

But why did I want "regular" Ubuntu (Gnome) on one partition and Xubuntu (XFCE4) on another in the first place? Well, I haven't even completely convinced myself about the rationality of all this. I just had Xubuntu's install cd lying around and wanted to refresh my memory about the features, speed and usability, etc. (it's not quite the same as adding xfce4, as an optional DE, to an existing Ubuntu install with Gnome). Just another experiment. I don't know how the "conf" files would behave if the original partition had Ubuntu and the fresh install was, say, OpenSuse, and would it be easy to share one common "/home" for both distros. Probably not??

Thanks for your interest in this rather wayward question posed by a big fan of the Psychocats tutorials.

P.S. (edit): Just one more thing... To make it more meaningful and more interesting to have Xubuntu on a separate partition (without sharing the separate /home partition among the two different *buntus, because it turned out rather tricky) I upgraded the Xubuntu install to the Intrepid alpha version. A safe way to try it out (it's probably pretty stable already at this point, of course).

---

### Post by Piraja on 2008-09-09
Sharing the /home partition among the two *buntus was not so tricky after all, as I finally figured out. Below, I will keep referring to the home partition as **sda1**, the "regular" Ubuntu partition (running Gnome by default and Fluxbox as an option) as **sda3**, and the Xubuntu Intrepid partition (running XFCE4 by default and Fluxbox as another option) as **sda6**.

I had previously installed the XFCE4 desktop on **sda3** but uninstalled it. There were still a couple of directories in my home folder (on **sda1**) pointing to the XFCE4 install. Those remnants had some undesired features I wanted to get rid of (such as reconfigured xfce4-panels) and get the Xubuntu defaults instead, as a starter. I deleted those obsolete folders (xfce4 and xfce4-session) from the .config directory (there was some other location, too, but I'm no longer sure which directory it was; the point was to delete all the xfce4 stuff from all the pertinent hidden folders in the home folder, anyway). 

A remaining slight inconvenience is that when I log on to the new Xubuntu Intrepid install on **sda6**, I get a message asking me whether I want to make gnome.desktop as my default for future sessions (obviously not) and claiming that xfce desktop is not installed on my desktop (which is not correct). So I choose "Just log in" and voilà, here comes the Xubuntu splash and the XFCE4 desktop....* I haven't figured out how to get rid of the slightly annoying logon dialogue yet, but otherwise the shared separate /home partition on sda1 works quite well for both sda3 and sda6.

Anyway, this is not really a support request, I just wanted to tell you that sharing the /home partition works more easily than I first thought.

*) ... and this is how it looks like at the moment:

[[IMG]http://www.aijaa.com/img/t/00031/2697877.t.png[/IMG]](http://www.aijaa.com/v.php?i=2697877.png)

---

### Post by Piraja on 2008-09-10
One thing I did not take into account when I fiddled with the themes and panel settings in Xubuntu (sda6) is that these configuration changes affect also Ubuntu's Gnome configuration (on sda3) through the "dot-folders" on the home partition (sda1), so that tweaking the xfce4-panel, for instance, affects also the gnome-panel settings, and the same applies also to the themes, window borders, etc. 

For an over-sensitive aesthete, who likes to have different desktops and window managers and keep them highly personalized, like me, this is a little bit annoying. But I must emphasize that this is just a personal peculiarity and does not really diminish the advantages of having a separate home partition.

---

### Post by vanadium on 2008-09-10
I would not at all recommend to share the same /home between different operating systems: things are really not designed to work like that.

It is perfectly fine though to keep your own user data on a separate partition to be accessed and used from within different operating systems. You can easily "integrate" your data by creating symbolic links to them in the different home directories of the different operating systems.

[quote=aysiu]And, honestly, I'm not really a separate /home expert. The tutorial is adapted from another tutorial I don't fully understand. I've used it once myself (just ot make sure it works), but I don't know enough to troubleshoot that one.[/quote]

It is great work nevertheless. Being able to present this in clear instructions on a nice website that is well navigable is an art in its own.

I always wondered if in the mean time there are alternative easier commands that are equivalent to the "cpio" command in the tutorial (e.g. cp or rsync with appropriate options) (but now I am going greatly off-topic ...).

---

### Post by mixmaster on 2008-09-10
Given that the only significant difference between Ubuntu and Xubuntu is the window manager (and to a lesser extent the default applications), why do you need separate installs for each.  Simply install ubuntu then install xubuntu-desktop and you can flip between them from the startup flash screen.

If you are really masochistic, it is possible to set up a multi-screen system with a different window manager on each screen.

---

### Post by Piraja on 2008-09-10
Hi Mixmaster! As I said,

> **Piraja said:**
> Well, I haven't even completely convinced myself about the rationality of all this.

Let's say I just wanted to test sharing a /home partition (e.g. sda1) among two different installations (Ubuntu, Xubuntu) on two different partitions (e.g. sda3 & sda6). It works with the two different *buntus, but with certain inconveniences. Having figured that out now, the next step is that I'll probably just reformat the sda6 Xubuntu install and do something else with it (and _not_ try to share the /home among e.g. the existing Ubuntu install and, let's say, FreeBSD!).

I'd say that the WM is not the only meaningful difference, since the FM's are significantly different too. Unlike Thunar, Nautilus can handle Samba shares, at least after the latest updates (at least if you don't mount them as root — if I do "gksudo nautilus" I still cannot mount the shares, but as a regular user I can).

You're absolutely right about installing xubuntu-desktop alongside the regular Gnome Ubuntu. No need to install on another partition. I used to have Linux Mint on sda6, it was very nice but a little resource-hungry for my 256MB laptop, at least with the default setup.

---

### Post by snowpine on 2008-09-10
I believe it is safe to share a /home partition if you use different user names for the different distros.

---

### Post by vanadium on 2008-09-11
> I believe it is safe to share a /home partition if you use different user names for the different distros.
This is correct. At that point, both distros will be working with different directories.

---

