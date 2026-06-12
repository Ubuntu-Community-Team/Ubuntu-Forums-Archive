---
title: "Can someone recommend a low end graphics card please?"
date: 2008-05-03
forum: Hardware
---

### Post by starbase1 on 2008-05-03
I've had various issues with graphics cards, and this time I am determined to get a graphics card that works well with the latest Ubuntu, including the desktop effects.

So can someone recommend a card? I'm hoping to get something round about 50 UK pounds / 100 US dollar level.

Failing that, are there any guidelines on what to look for?

I currently have an NVidia geForce 8400 GS installed, but it does not recognise the full resolution of my monitor under Ubuntu, and I can't enable desktop effects...

Clues for the clueless gratefully received...

Nick

---

### Post by CREEPING DEATH on 2008-05-03
That's a great graphics card, the problem is an Ubuntu issue that is being resolved.  Check the forums for help!

CD

---

### Post by starbase1 on 2008-05-03
> **CREEPING DEATH said:**
> That's a great graphics card, the problem is an Ubuntu issue that is being resolved.  Check the forums for help!

CD

Thanks Creeping Death - I tried searching on a several terms that seemed good to me, but could not find a thread with an answer, could you help point me the right way please?

Thanks, Nick

---

### Post by |{urse on 2008-05-03
i've seen lots of ubuntu video weirdness in my day and it seems the problem is a lot of the times the monitor you are using and not the card/chipset. I have this cheapie X2gen flat panel that does nice hi-res on any os except ubuntu, on ubuntu it wont even display under vesa. framebuffer or not. Save yourself some trouble and make sure your monitor is supported as well. So you don't end up with kikbutt 3d on an 800x600 screen

---

### Post by starcannon on 2008-05-03
Starbase1 I use that card, it works great. Heres how:

1) Download the driver from here [http://www.nvidia.com/object/linux_display_ia32_169.12.html]("http://www.nvidia.com/object/linux_display_ia32_169.12.html")

2) Print out these directions, your going to be in pure CLI for most of this.

3)CTRL-ALT-F1

4)```

login:
Password:
cp /etc/X11/xorg.conf /home/yourhome/xorg.conf.backup
sudo rm /etc/X11/xorg.conf #just deleting the xorg.conf, we backed it up.
sudo /etc/init.d/gdm stop
sudo apt-get install build-essential
cd /home/yourhome/nvidia_driver_location 
sudo chmod a+x ./NVIDIA*.run
sudo ./NVIDIA*.run
#Answer affirmative to all questions in the wizard.
#Driver is installed now to make sure it works on reboots

sudo nano /etc/modules
#add nvidia to the list.
ctrl-x
y and enter
sudo nano /etc/default/linux-restricted-modules-common
#add nv to the restricted list
ctrl-x
y and enter
#Driver should now be loaded on reboots, and old driver should not.
#Lets restart the X-server and the Gnome Desktop Manager

sudo /etc/init.d/gdm start 

```
Okay, if I didn't forget anything that should do it. If you find you have problems and get dumped to a Command Line Interface then restore the xorg.conf.backup we made
```
sudo cp /home/yourhome/xorg.conf.backup /etc/X11/xorg.conf
sudo nano /etc/modules
#remove nvidia from list
sudo nano /etc/default/linux-restricted-modules-common
#remove nv from restricted list
sudo /etc/init.d/gdm restart 
#come back here and report what went wrong, I'll help you figure it out if possible, though this method works great on getting the Nvidia 8400m gs fully functional on an HP Pavilion dv2600 using Feisty, Gutsy, and Hardy.
```
If this fixed your problem let us know.
GL and have fun.
~starcannon

---

### Post by starbase1 on 2008-05-03
Starcannon, thanks for the suggestion. I don;t have a working internet connection on my Ubuntu box unfortunately, and from my very limited understanding, that sudo apt get is going to try and fetch files over the internet connection?

Nick

---

### Post by starcannon on 2008-05-03
> **starbase1 said:**
> Starcannon, thanks for the suggestion. I don;t have a working internet connection on my Ubuntu box unfortunately, and from my very limited understanding, that sudo apt get is going to try and fetch files over the internet connection?

Nick

That is correct, though you may be able to get the build-essential package from the cd, from the Desktop in gui mode go to:

 insert livecd that you installed with in the cd tray

 system-->administration-->software sources

enable cdrom with ubuntu support in the box on the first tab, choose reload when the popup window gives you the choice, you may get an error about some of the options because of your lack of an internet connection (no cat5 cable handy?)

Now go to:
system-->administration-->synaptic package manager

search for build-essential

put a check mark on it and Apply, and Apply again.

You will need to use the computer your on to post here to download the nvidia drivers and move them using a thumbdrive or whatever media you have available.

That should allow you to continue the install process.

GL I'll keep checking back

---

### Post by starbase1 on 2008-05-03
Thanks again starcannon, I'll give that a god tomorrow.

I might have another crack at installing my wireless internet thingy first...

How does cat 5 cable help?!?!

Nick

---

### Post by starcannon on 2008-05-03
Guess a piece of cat5 would only help if you had a router to plug it into, made assumptions about your internet connection, but didn't consider you maybe getting your access soley through wireless.

I think your wise to get your internet access rolling first, makes everything else so much easier.

---

