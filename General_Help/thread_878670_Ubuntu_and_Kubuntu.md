---
title: "Ubuntu and Kubuntu"
date: 2008-08-03
forum: General Help
---

### Post by Graham1 on 2008-08-03
Hi

Currently running Ubuntu 8.04 but would now like to try Kubuntu 8.04 (KDE 3.59 and 4.1). Will I run into any problems installing Kubuntu 8.04 onto my Ubuntu 8.04 partition? On Kubuntu's site, it suggests using kubuntu-desktop within Synaptic. Is this the prefered/safest method?

:)

---

### Post by Elfy on 2008-08-03
I've always installed the desktop's with aptitude myself

```
sudo aptitude install kubuntu-desktop
```

Be aware that you will end up with both gnome and kde apps in your menu and will need to edit them if you only want kde in kubuntu and gnome in ubuntu.

Check out the psychocats pages for more info

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by coffeecat on 2008-08-03
> **Graham1 said:**
> On Kubuntu's site, it suggests using kubuntu-desktop within Synaptic. Is this the prefered/safest method?

Yes. Install kubuntu-desktop and dozens of packages will be pulled in with it, making up your Kubuntu experience. :) When you boot up and get to the login manager, you can choose whether to log into gnome or kde there. It's under options (or something like that). Choose which desktop you want before you enter your password, otherwise you'll go into the default desktop.

You may find that the orange Ubuntu usplash will be replaced by the blue Kubuntu one. If you want to change it back, post back and I (or someone) can post a link.

---

### Post by Graham1 on 2008-08-03
Thanks for the replies guys :). Until now, I wasn't sure you could mix the two (having come on seperate cd's) unlike openSUSE and Fedora which lets you choose, during install. 

Btw, is it easy to uninstall Kubuntu? (should I come across problems). Would it be a case of deselecting kubuntu-desktop which would then deselect the appropriate dependencies?

:)

---

### Post by Elfy on 2008-08-03
I'm not sure about with sysnaptic but if you use aptitude to install in a terminal it should remove everything through a terminal

```
sudo aptitude install kubuntu-desktop
sudo aptitude remove kubuntu-desktop
```

If not then there is a long command on one of the psychocats pages which gives a suitable apt-get command.

---

### Post by coffeecat on 2008-08-03
If you do decide you don't want kde, before you start uninstalling everything, can I tell you about two kde packages? They don't come with a default install of Ubuntu and they can be very useful on the Gnome desktop, even if their kde theming makes them look a little out of place.

**K3b** - an all-purpose optical media burning/ripping/formatting app. I use it less now that Gnome has Brasero, but it's probably more powerful/flexible and is highly regarded.

**Konqueror** - the kde web/file browser. The reason I use it in Gnome is that it is a very good way of viewing man pages. I think it's worth installing in Gnome for this reason alone. Once you've installed it, type 'man:appname' in the address bar (no quotes) and compare that with 'man appname' from the terminal (note the colon). Much easier to read, isn't it?

If you do decide to keep these apps, they'll keep a load of dependencies with them.

---

### Post by castor_troy on 2008-08-03
Installing Kubuntu Desktop through Synaptic is a breeze.

Dont know about uninstalling through synaptic. Guess the terminal way would be better.

I am myself now using both kde and gnome. i installed kubuntu-desktop over Ubuntu.

The cluttered menu's are a huge turn-off. But i'm still not able to make up my mind as to which one to keep. So i'm using both.

I liked amarok the moment i used it. Rythmbox just does not feel the same.\

So now i use amarok in gnome.

---

### Post by Graham1 on 2008-08-03
Once again, thanks for the replies :D. Installing Kubuntu 8.04 as we speak (using aptitude). I'm mostly a Gnome guy (hence Ubuntu) but KDE 4.1 is beginning to look nice and more functional now (well, in openSUSE 11.0). Will Kubuntu include 3.59 or/and 4.1? K3B is an excellent tool (which I've used most of the time (in other distro's) but I tend to use Brasero more now (simpler and does the job). Will let you know how it goes.

:)

---

### Post by Graham1 on 2008-08-03
Kubuntu up and running now :). Is it possible to install KDE 4.1 along side 3.59?

:)

---

### Post by Graham1 on 2008-08-07
LOL, see what you mean about the messy menus. Unfortunately, it didn't install the latest KDE 4.1 but 4.0.x instead. Removing KDE4 then caused other problems which I couldn't figure out (or had time to) so I re-installed Ubuntu again.

:)

---

### Post by Elfy on 2008-08-07
Oh what fun we can have with reinstalling - I tell you what I did after the first run of massive menu attack.

I made a small 6Gb partition in which to install other types - I tried kub* and Xub* - I then used supergrub (because I can do it that way :) ) to point grub at the ubuntu install again and just add kubuntu or xubuntu to the ubuntu menu list.

There is probably an easier way but I haven't bothered to find it :D

---

