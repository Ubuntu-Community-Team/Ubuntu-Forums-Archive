---
title: "Headphones not working?...."
date: 2010-05-05
forum: Hardware
---

### Post by Corinthe on 2010-05-05
I've used Ubuntu for a fair while (not that I'm a Linux genius or anything, obviously...) and like it a lot. A few days ago I installed Lucid on my laptop, and it works great- aside from the fact that my headphones don't work. I've never had this problem in any of the other releases, or on my computer at all. Sound comes out of the speakers just fine, but not the headphones. I know the headphones (and the headphone jacks) aren't broken, because they both work fine in Windows. If it helps, I'm running an HP Pavilion laptop, and I have standard iPod headphones...

---

### Post by lidex on 2010-05-05
Have you checked alsamixer: ```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

And what about settings in 'system>preferences>sound'?

---

### Post by solri on 2010-05-07
> **lidex said:**
> Have you checked alsamixer: ```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

And what about settings in 'system>preferences>sound'?
I have the same problem - headphones worked fine in karmic, but now nothing. When I try to open alsamixer, I get 
[COLOR=Blue]
cannot load mixer controls: Invalid argument[/COLOR]

---

### Post by lidex on 2010-05-08
> **solri said:**
> I have the same problem - headphones worked fine in karmic, but now nothing. When I try to open alsamixer, I get 
[COLOR=Blue]
cannot load mixer controls: Invalid argument[/COLOR]

Your alsa install is likely borked. Try the link in my sig for alsa-upgrade-script.

---

### Post by cub on 2010-05-08
It's not exactly the same problem, but to get sound out of my Sony Vaio I had to install alsa 1.0.23. Description can be found in the Vaio-thread: [http://ubuntuforums.org/showpost.php?p=9178261&postcount=23](http://ubuntuforums.org/showpost.php?p=9178261&postcount=23)

---

### Post by JackFlash79 on 2010-05-14
Try this post instructions by [Unreal223linux]("http://www.backports.ubuntuforums.org/member.php?u=321904"): [http://www.backports.ubuntuforums.org/showthread.php?t=473425](http://www.backports.ubuntuforums.org/showthread.php?t=473425)

I had the exact same problem and this  instructions worked perfectly form me, for both 9.10 Karmic Koala and 10.04 LTS Lucid Lynxs
By the way I'm a noob.

This is my adaptation to the new alsa driver, all credits should go to [Unreal223linux]("http://www.backports.ubuntuforums.org/member.php?u=321904"):

Step one is you need the newest version of the alsa sound drivers. To do that cut and paste each line of the below code box into the terminal one at a time. Wait untill one function is done before pasting in the next. The terminal is located in applications> accessories>terminal.

```
sudo apt-get install build-essential linux-headers-$(uname -r)

wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2

tar -xjf alsa-driver-1.0.23.tar.bz2

cd alsa-driver-1.0.23

./configure

sudo make

sudo make install

```


Once through all of the commands reboot your computer.

-------------------

Once the computer is back up go back into the terminal and enter this:

```
 sudo gedit /etc/modprobe.conf 
```

You will be prompted for your user account password. When you type it will look like nothing is happening but thats just a security feature.

In the text file that pops up enter this and save it:

 ```
options snd-hda-intel model=6stack-digout 
```


Once saved reboot your computer

---------------------

Once your computer is back up go back into the terminal and enter

```
alsamixer
```

Use the arrow keys to move around on this screen. On anything you see double MM on press the M key and maximize the volume. Do this to anything with the double MM.

Once you do your headphones should be working! Go to the volume control panel and go to edit>preferences> and enable surround. From what I have seen that is the one that adjusts your headphones.

Good luck!

---

### Post by martine4161 on 2010-05-14
Your head phone is working fine in the speakers but not in head phone mode so basically you have a setting for the head phones in your OS , may be that can be disabled or the volume is less so check that and you can hear the voice.

---

### Post by atyankov on 2010-06-30
Worked for me on ASUS A6000! Big thanks! :D

---

### Post by Rig'dzin Dorje on 2011-01-23
[FONT=Times New Roman][SIZE=4]I had this problem (*Fujitsu Siemens Amilo laptop, Ubuntu 10.10*). Thanks for the reference to ALSAMIXER (I'm on my second Ubuntu distro but I'm still very new.). 
What I found in ALSAMIXER was that the MASTER and HEADPHONE controls seemed to be the wrong way round. If I reduced the MASTER setting it affected the headphones, whereas the HEADPHONE setting affected the laptop speakers. The laptop hardware Fn keys for audio, and the Ubuntu volume control indicator widget, both move the MASTER control - but it's the headphones that respond.
To use the headphones and cut out the laptop speakers I have to *zero the HEADPHONE setting*, and if I ever want to use the laptop speakers I have to go back into ALSAMIXER and increase the HEADPHONE setting again.
What I still can't do is insert and withdraw the headphones and have the laptop speakers cut out and in automatically.[/SIZE][/FONT]

---

