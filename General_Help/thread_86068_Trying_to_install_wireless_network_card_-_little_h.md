---
title: "Trying to install wireless network card - little help?"
date: 2005-11-04
forum: General Help
---

### Post by monomaniacpat on 2005-11-04
I've just got hold of a Linksys wireless network card (WPC11 v.4) and am having trouble installing the drivers. Having visited [http://rtl8180-sa2400.sourceforge.net/](http://rtl8180-sa2400.sourceforge.net/) and downloaded the drivers and having extracted the file, when I attempt to cd to relevant file, it says 'no such file or directory'. 

Is there any other way of installing the drivers?

---

### Post by aclaunch on 2005-11-04
How did you extract it-from the command line with "tar XXX" or via the GUI? I've noticed that the GUI "archive manager" wants to extract things in place even though it gives the option of "Where to extract?". 

Good Luck,
Alan

---

### Post by monomaniacpat on 2005-11-04
I tried it on command line first, but it said 'old option'g' requires an argument'. So I extracted via the GUI.

---

### Post by aclaunch on 2005-11-04
Is this file in tar.gz format? Usually the command is "tar -zxvf filename.tar.gz" According to the man page "g" is for incremental backup/extraction.

Alan

---

### Post by monomaniacpat on 2005-11-04
Tried that way I get the following response:

tar: rtl8180-0.21.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by aclaunch on 2005-11-04
Try deleting the download and redownloading it; it may have been corrupted. I just googled the file, dl'd it and it opened fine.

Alan

---

### Post by BIGtrouble77 on 2005-11-04
Check this out:
[http://lxer.com/module/newswire/view/46385/](http://lxer.com/module/newswire/view/46385/)

Just make sure you get the ndiswrapper files through synaptic.  Be sure to get ndiswrapper-utils and you can configure the wireless card via the gui.  Just point to the windows xp drivers when you do the config.

-BT

---

### Post by monomaniacpat on 2005-11-04
I'm still having the same problem - even when I have unzipped the files, it refuses to recognise the new file or directory! This applies for ndiswrapper, too. What can I do?

---

### Post by carlos_ on 2005-11-04
Why are you trying to download and compile ndiswrapper as opposed to using synaptic to get it?

I'm pretty sure I got it through synaptic if it wasn't already installed.

I would use synaptic to remove then re-install ndiswrapper (and associated gui if you prefer).

---

### Post by monomaniacpat on 2005-11-04
Once I have installed it, where do I access it from in the GUI?

---

### Post by carlos_ on 2005-11-04
I didn't use the gui myself, but it's a separate package.  You can see the package if you do a search using synaptic for "ndiswrapper".  It should be obvious which package is the ndiswrapper gui.  My guess is that it is a separate gui than the regular network one.  You can read the package description and see if there is any information on the binary to run to pull up the gui.

Sorry, I can't be more helpful... I've only used ndiswrapper from command line.

---

### Post by monomaniacpat on 2005-11-04
Then how do I access it from the command line?

---

### Post by BIGtrouble77 on 2005-11-04
If you read the link I posted you'd see that the gui utility is in:
System-> Administration->Windows Wireless drivers

You need to have ndiswrapper-utils installed.  Either go into synaptic and search for it and install it or type:
```
sudo apt-get install ndiswrapper-utils
```

---

### Post by monomaniacpat on 2005-11-04
I did read the link, but there is no windows wireless drivers utility!?

---

### Post by Vorian on 2005-11-04
[QUOTE=monomaniacpat]I did read the link, but there is no windows wireless drivers utility!?[/QUOTE]

have you tried to config your network ( eth0, eth1 )?

from the terminal try ```
iwlist eth1
```

---

### Post by monomaniacpat on 2005-11-04
eth1 and eth0, for that matter, are both unknown commands...:???:

---

### Post by Vorian on 2005-11-04
[QUOTE=BIGtrouble77]
```
sudo apt-get install ndiswrapper-utils
```[/QUOTE]

> Then how do I access it from the command line?

Try this aptitude or it is in your synaptic package manager

---

### Post by monomaniacpat on 2005-11-04
That doesn't tell me how to actually RUN ndiswrapper, after it is intalled...:(

---

### Post by BIGtrouble77 on 2005-11-05
I'ms sorry, I didn't post all of the files to install.  You need to also install this:

```
sudo apt-get install ndisgtk
```

When it's dones installing run this:

```
killall gnome-panel
```

Run the utility from:

System->Administration->Windows Wireless Drivers

If it still doesn't work make sure this is installed too:
```
sudo apt-get install ndiswrapper-utils
```

---

### Post by monomaniacpat on 2005-11-06
OK, great, I've got Windows Wireless Drivers open now. Having added the relevant driver, it says: 'Hardware Present? No.'

What do I do? - the card's inserted....

HELP!

---

### Post by gw90se on 2005-11-06
I have the same card and just loaded these utilities. It all worked fine for me. I did have to deactivate my eth0 before it would connect with my wlan0. Have you tried rebooting with it installed then running the "Windows Wireless Drivers"?

---

### Post by monomaniacpat on 2005-11-06
Which driver did you use? I'm using LSRTNDS.INF...

Why is it not working for ME?!

---

### Post by gw90se on 2005-11-06
Well, I have shut the laptop off already and am using the desktop, but that seems like the one I chose. As I asked earlier, did you boot up with the card installed? I plugged mine in after booting and then loaded the driver.

---

### Post by Vorian on 2005-11-09
[QUOTE=monomaniacpat]OK, great, I've got Windows Wireless Drivers open now. Having added the relevant driver, it says: 'Hardware Present? No.'

What do I do? - the card's inserted....

HELP![/QUOTE]

Did you boot with the card in?  If so, Try booting without the card in, and insert card after your system is up.

---

