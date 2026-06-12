---
title: "Exim problems?  Open Ports I wish to close!"
date: 2008-12-25
forum: Installation &amp; Upgrades
---

### Post by theravenproject on 2008-12-25
Having recently wiped Hardy and Done a clean full (Not the live CD) alternate install on my Hardcore Gamer---I even installed the complete way and set up LVM etc--I decided to use UMIT (NMAP Powered) to scan LOCALHOST and see if there were any open ports that shouldn't be.  There were.  Port 25 was open and I have never done that so it was done automatically and also another port- 631 is open.  I need to know how to protect/close these ports off somehow.  I prefer to close them but if someone tells me how to protect them then perhaps I can leave them be.  Thanks People...

---

### Post by albinootje on 2008-12-25
> **theravenproject said:**
> Having recently wiped Hardy and Done a clean full (Not the live CD) alternate install on my Hardcore Gamer---I even installed the complete way and set up LVM etc--I decided to use UMIT (NMAP Powered) to scan LOCALHOST and see if there were any open ports that shouldn't be.  There were.  Port 25 was open and I have never done that so it was done automatically and also another port- 631 is open.  I need to know how to protect/close these ports off somehow.  I prefer to close them but if someone tells me how to protect them then perhaps I can leave them be.  Thanks People...

25 is for smtp software, like exim or postfix.
631 is Cups printing software.

If you want to close those ports, use firewall software to do this.
The more recent Ubuntu releases come with ufw by default.
See here for more info on ufw (scroll down to section "command line") :
[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

If you prefer a GUI for ufw, see :
[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

---

### Post by Aearenda on 2008-12-25
I noticed that Exim gets installed as a dependency of smartmontools - and of course 631 is CUPS. If you don't want to use a firewall, you could just prevent Exim from starting in system->administration->services. CUPS is a bit harder - if you go to [http://localhost:631/admin/](http://localhost:631/admin/) you can turn off sharing and remote administration, but you probably need to have CUPS running to use your printer.

---

### Post by theravenproject on 2008-12-25
OK, can you tell me how I can reset exim to it's defaults 'cos I went and screwed with it before I got an answer. Currently I entered 

sudo dpkg-reconfigure exim4-config

and then I selected the "No configuration at this time"--I know in order to reset it I use the same command but what option do I set it as?  There are five different options,,,

---

### Post by albinootje on 2008-12-25
> **theravenproject said:**
> OK, can you tell me how I can reset exim to it's defaults 'cos I went and screwed with it before I got an answer. Currently I entered 

sudo dpkg-reconfigure exim4-config

and then I selected the "No configuration at this time"--I know in order to reset it I use the same command but what option do I set it as?  There are five different options,,,

Do you really want to use Exim ? I find Exim almost as hard as Sendmail (cough,cough :( ) to use :(
Postfix is soooooooooooo easy compared to that. It's a breeze!

If you want to start from scratch with exim, you can do this :
```

sudo apt-get remove --purge exim4-*
sudo apt-get install exim4

```
And reinstall smartmontools if exim wants to remove that.
Wanna try postfix instead of exim ? Do this :
```

sudo apt-get install postfix

```
And tweak /etc/postfix/main.cf later on if needed.

---

### Post by theravenproject on 2008-12-25
Okay but what exactly does Exim-4 or Sendmail or the one you suggested do?  Is what it does necessary to the usefulness of my professional Home Computer.  I use my Home Desktop (A Coolermaster Full CM STACKER Tower with a Gigabyte GA-X48T-DQ6 DDR3 1600 Mhz FSB mobo and 4 Gb of OCZ Platinum 1800 Mhz DDR3 Ram and an Intel Q9300 Quadcore Processor.  Nvidia GRFX Card, Zalman 1000 Watt Power and Zalman Large Proc Cooler, 500 GB WD HDD SATA II 3.5/mbs and Ubuntu Intrepid Ibex (Tweaked)) as my college Computer-I am an Undergrad at Baker College in Computer Science/IT-Network+ Security minor.  Are these programs necessary for the well-being of my day to day School and burgeoning professional life?

---

### Post by albinootje on 2008-12-25
> **theravenproject said:**
> Okay but what exactly does Exim-4 or Sendmail or the one you suggested do?  Is what it does necessary to the usefulness of my professional Home Computer.  I use my Home Desktop (A Coolermaster Full CM STACKER Tower with a Gigabyte GA-X48T-DQ6 DDR3 1600 Mhz FSB mobo and 4 Gb of OCZ Platinum 1800 Mhz DDR3 Ram and an Intel Q9300 Quadcore Processor.  Nvidia GRFX Card, Zalman 1000 Watt Power and Zalman Large Proc Cooler, 500 GB WD HDD SATA II 3.5/mbs and Ubuntu Intrepid Ibex (Tweaked)) as my college Computer-I am an Undergrad at Baker College in Computer Science/IT-Network+ Security minor.  Are these programs necessary for the well-being of my day to day School and burgeoning professional life?

Okay, thanks for the info, it's obvious now. :)

Exim and Sendmail are Mail Transfer Agents, and usually only installed on servers.
[https://help.ubuntu.com/community/Exim4](https://help.ubuntu.com/community/Exim4)

Exim *probably* was installed as a dependency of smartmontools.
Because with smartmontools you can configure that e.g. every night your hard disk is checked for errors, and if errors are found, then you will receive an email, and exim was added to enable sending out those emails.

Try this in a terminal :
```

apt-get remove --purge exim4

```
I have smartmontools installed, and got exim4 with it for free, but I don't use exim at all.
Here it looks like this if I type in the above command.

The following packages will be REMOVED:
  bsd-mailx* exim4* exim4-base* exim4-config* exim4-daemon-light* mailx*
0 upgraded, 0 newly installed, 6 to remove and 1 not upgraded.
After this operation, 4076kB disk space will be freed.
Do you want to continue [Y/n]? 

So, it won't remove smartmontools, which is good. Go ahead.

---

### Post by theravenproject on 2008-12-25
Yeah,  Actually I think that in Intrepid Ibex, Exim is hooked up with the cups packages and so I wonder if deleting Exim is the thing to do even if I don't use it.  As far as Deleting it I started to do that with Synaptic (I like to use Synaptic to delete things because it can warn me if I am running the risk of breaking anything or creating unmet dependencies etc...So I ran Synaptic on Exim and it's related packages and it is obviously a prime component welded into the Ubuntu framework because it is hooked up with cups and because when you try and delete it in Synaptic it says you also must delete the Ubuntu Desktop Meta-Package, and some other mission critical Framework applications.  Perhaps I could incorporate a WM now instead of Gnome and thus create my own Custom Framework...It'll take some hard work, grueling research and support from your best at these forums but when it's done it could even resemble a distro of it's own!

PLEASE WRITE ME BACK AND INFORM ME OF WHAT YOU THINK I SHOULD DO IN DETAIL IF YOU'VE READ AND HAVE CONSIDERED THE INFO WRITTEN ABOVE!

---

### Post by albinootje on 2008-12-25
> **theravenproject said:**
> So I ran Synaptic on Exim and it's related packages and it is obviously a prime component welded into the Ubuntu framework because it is hooked up with cups and because when you try and delete it in Synaptic it says you also must delete the Ubuntu Desktop Meta-Package, and some other mission critical Framework applications.

Okay, if you don't want to use a firewall, then the easiest thing is the stop exim from working.

Please do this in a terminal :
```

sudo /etc/init.d/exim4 stop
sudo update-rc.d exim4 remove

```
That should result in the following, which is okay to ignore :
update-rc.d: /etc/init.d/exim4 exists during rc.d purge (use -f to force)

After that scan your computer again with the nmap-based UMIT to see the difference.

---

### Post by theravenproject on 2008-12-26
Is this what you truly reccomend for my computer?  I mean as a home Business/College Desktop-that I will not need Exim and it won't break anything or cause any unmet dependencies.  I never had smartmon tools either-I just got and installed them because I have a SMART enabled HDD and want to use the advanced features (I don't even know what they do!  What if I just use the Stop command without removing exim-every time I restart/boot my computer as soon as I get to my desktop I just pull up Terminator and run the exim/initd stop command?  Lastly, what about the other port I had running open-port 631?  I read somewhere that you have to go to the config file for cups I believe it was and make sure that you bind it to localhost but I haveno idea how to do so or whether doing so is the answer for my personal computer/situation.  I did uninstall UFW becuase I never even knew it existed let alone how to use it and so all along I have been using FIRESTARTER firewall instead.

---

### Post by albinootje on 2008-12-26
> **theravenproject said:**
>   What if I just use the Stop command without removing exim-every time I restart/boot my computer as soon as I get to my desktop I just pull up Terminator and run the exim/initd stop command?  Lastly, what about the other port I had running open-port 631?  I read somewhere that you have to go to the config file for cups I believe it was and make sure that you bind it to localhost but I haveno idea how to do so or whether doing so is the answer for my personal computer/situation.  I did uninstall UFW becuase I never even knew it existed let alone how to use it and so all along I have been using FIRESTARTER firewall instead.

Yes. To prevent exim from starting, you would only have to type this once in a terminal :
```

sudo /etc/init.d/exim4 stop
sudo update-rc.d exim4 remove

```
Good that you started with FireStarter firewall!

---

