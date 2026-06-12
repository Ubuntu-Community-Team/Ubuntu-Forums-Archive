---
title: "[SOLVED] Tried installing applets for AWN, and now..."
date: 2008-09-14
forum: General Help
---

### Post by xj0hnx on 2008-09-14
AWN is gone?

I tried following this...

[http://linuxhelp.blogspot.com/2008/02/cool-awn-applets-to-adorn-your-ubuntu.html](http://linuxhelp.blogspot.com/2008/02/cool-awn-applets-to-adorn-your-ubuntu.html)

but now AWN is gone from System > Preferences. I noticed after reading comments that...

> Maybe I missed something but installing the applets package from this location actually demands install of the libawn-bzr package which would break the existing awn and the manager because they use another libawn package, wouldn't it?

So, did I uninstall it? Or is it just somewhere else right now?

---

### Post by xj0hnx on 2008-09-14
Ok, I seem to have reinstalled it, and I see the AWN Manager in System > Preferences, but the actual program AWN is not there. I set it to "Automatically start AWN on login", but it doesn't do.

Any ideas? Any info needed to help?

---

### Post by kestal on 2008-09-14
I think all you'd have to do to get AWN to work on start up is to create a new start-up session.

(through menu -> administration/preferences [COLOR="Gray"](I forget which one at the moment)[/COLOR] -> session).

Name: Avant
Command: Avant-Window-Navigator
Details: Avant Dock

then restart.

Tell me if that works for you.

---

### Post by xj0hnx on 2008-09-14
Unfortunately it didn't work :( I looked at my processes and it isn't there, or at least nothing that looks like it.

---

### Post by howefield on 2008-09-14
could the command be case sensitive ?

avant-window-manager

---

### Post by xj0hnx on 2008-09-14
> **howefield said:**
> could the command be case sensitive ?

avant-window-manager

I can open the manager, I need to open the navigator, the actual dock at the bottom of the screen. But it when I typed it with caps in teh command, it automatically changed it to lower case anyway.

---

### Post by kestal on 2008-09-14
are you on Gutsy or Hardy?

---

### Post by howefield on 2008-09-14
my typo, didn't mean "manager"

I'll install it, see what I get.

---

### Post by kestal on 2008-09-14
> **xj0hnx said:**
> I can open the manager, I need to open the navigator, the actual dock at the bottom of the screen. But it when I typed it with caps in teh command, it automatically changed it to lower case anyway.

What happens when you open up your terminal and type in "avant-window-navigator"?

Also, what version of Ubuntu are you on?

---

### Post by howefield on 2008-09-14
Yep, no probs at all, installed from synaptic and icon for the dock is in the applications > accessories menu and adding to the sessions list makes it start on boot up.

---

### Post by kestal on 2008-09-14
> **howefield said:**
> Yep, no probs at all, installed from synaptic and icon for the dock is in the applications > accessories menu and adding to the sessions list makes it start on boot up.

Yeah.. I am thinking that the applet installed may have broken his AWN. Its mentioned on the web page.

---

### Post by xj0hnx on 2008-09-14
> **kestal said:**
> What happens when you open up your terminal and type in "avant-window-navigator"?

Also, what version of Ubuntu are you on?

```
john@john-desktop:~$ avant-window-navigator
The program 'avant-window-navigator' is currently not installed.  You can install it by typing:
sudo apt-get install avant-window-navigator
bash: avant-window-navigator: command not found
john@john-desktop:~$ sudo apt-get install avant-window-navigator
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator: Depends: libawn0 (>= 0.2.1)
E: Broken packages
john@john-desktop:~$ avant-window-navigator
The program 'avant-window-navigator' is currently not installed.  You can install it by typing:
sudo apt-get install avant-window-navigator
bash: avant-window-navigator: command not found
john@john-desktop:~$ 


```

Hardy Haron Ubuntu 8.04

---

### Post by howefield on 2008-09-14
Load up synaptic package manager and from the Edit menu, select fix broken packages.

Don't know if it will work, but it will only take a few seconds to try it.

---

### Post by kestal on 2008-09-14
*Edit:* Hah, you beat me to it by 1-2 minute. if THAT doesn't work, try

sudo apt-get autoremove
sudo apt-get remove libawn0

then retry from synaptic, or

sudo apt-get install avant-window-manager

---

### Post by xj0hnx on 2008-09-14
> **kestal said:**
> *Edit:* Hah, you beat me to it by 1-1 minute. if THAT doesn't work, try

sudo apt-get autoremove
sudo apt-get remove libawn0

then retry from synaptic, or

sudo apt-get install avant-window-manager

It installed a bunch of applets, it was a package. Kind of weird that someone has a package to add applet that breaks the program that runs them.

---

### Post by kestal on 2008-09-14
Agreed. Then again, that tutorial to get it set up was for Gutsy and a year ago. The information is a bit outdated I think.

did you get it to reinstall?

---

### Post by howefield on 2008-09-14
of course, another solution if you are not tied to avant is to use another dock, cairo-dock beats them all, imho.

---

### Post by xj0hnx on 2008-09-14
Well, I got AWN back, but now it has only the one default applet :(

---

### Post by xj0hnx on 2008-09-14
> **howefield said:**
> of course, another solution if you are not tied to avant is to use another dock, cairo-dock beats them all, imho.

I tried Ksdocker, or something like that, and it started and ran, but since I am using dual monitors, it placed it directly in the middle between them. I tried Cairo, but couldn't get it to install. It's beena  long time since I messed with Linux, and remembering how to do minor things is coming back, just slowly.

Anyone have a newbie guide to installing Cairo-dock?

---

### Post by kestal on 2008-09-14
to go terminal and type

sudo gedit /etc/apt/sources.list

and at the bottom add:

```
deb http://repository.cairo-dock.org/ubuntu hardy cairo-dock
```

then save, exit.

while still in terminal, copy-paste

```
wget -q http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg -O- | sudo apt-key add -
```

Last but not least. in Terminal, add:

```

sudo apt-get update
sudo apt-get install cairo-dock cairo-dock-plug-ins

```

This was taken from: [https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

Hope it helps ;)

Good luck with your dual monitor stuff, Cairo Dock is pretty nifty. Its a bit overwhelming at first, but you'll get used to it.

---

### Post by howefield on 2008-09-14
Problem is cairo-dock will straddle both monitors that xj0hnx is using, same as Ksdocker. Don't know how that could be fixed.

---

### Post by xj0hnx on 2008-09-14
> **kestal said:**
> to go terminal and type

sudo gedit /etc/apt/sources.list

and at the bottom add:

```
deb http://repository.cairo-dock.org/ubuntu hardy cairo-dock
```

then save, exit.

while still in terminal, copy-paste

```
wget -q http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg -O- | sudo apt-key add -
```

Last but not least. in Terminal, add:

```

sudo apt-get update
sudo apt-get install cairo-dock cairo-dock-plug-ins

```

This was taken from: [https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

Hope it helps ;)

Good luck with your dual monitor stuff, Cairo Dock is pretty nifty. Its a bit overwhelming at first, but you'll get used to it.


Just felt I had to quote this again because it worked perfectly, thank you :)

[quote=howefield]Problem is cairo-dock will straddle both monitors that xj0hnx is using, same as Ksdocker. Don't know how that could be fixed.[/quote]

This is true, BUT you can fix it in the preferences for Cairo-dock, and position it so it is in the middle of just one monitor.

---

### Post by xj0hnx on 2008-09-15
Can you not change the icons for items on Cairo-dock?

Edit: Never mind, found it, you just have to dig a little.

---

