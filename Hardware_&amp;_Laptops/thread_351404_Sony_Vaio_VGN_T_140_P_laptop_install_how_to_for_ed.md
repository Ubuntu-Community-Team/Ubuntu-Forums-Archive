---
title: "Sony Vaio VGN T 140 P laptop install how to for edgy 6.10 and feisty 7.04"
date: 2007-02-01
forum: Hardware &amp; Laptops
---

### Post by whiterabbitwonder on 2007-02-01
#Hello All.  I figured I would share the fruits of my 2 days spent ](*,) trying to install Edgy and then Feisty and now Gutsy Tribe 5 on my Sony Vaio T140P laptop.
# NOTE, I only use Kubuntu.  Frankly gnome sucks the big one.  KDE when I finally tried it was the reason I felt like making the jump from XP.  They have actually put some time into basic usability, which is important (how many millions has Apple and MS put into usability alone...)
# Also in case i every bork my install, I will have a nice script to repave with...

#BTW Feisty has some really nifty battery and wireless utilities that are a must have.

#These instructions came from about 20 diff sources on the net.  Thank you to everyone who made this easier.

**#First lets get updated and get feisty:**
sudo su
#make sure you are up to date as upgrades can only be done one release at a time.
apt-get update && apt-get upgrade && apt-get dist-upgrade && apt-get autoclean
nano /etc/apt/sources.list 

# and replace anything that says edgy with feisty
# the next step will take a few hours unless you are on a fat pipe
apt-get update && apt-get upgrade && apt-get dist-upgrade && apt-get autoclean
#you should now have feisty if that went well

[B]# next we will fix the video resolution
sudo apt-get 855resolution
#this will actually get the 915resolution as it seems some kickass hacker fixed the 915 to work with the vbios on this machine.  so it remembers the resolution even when hibernating! (although it is slow as hell to hibernate and since it remembers most of the apps from your last session, i wonder whether hibernate is really useful)

**# voila, you should have nice 1280 x 768 resolution now.  **

######################
**# Audio silence?  try this**
# simple.  in the mixer, go to Switches tab, turn off external amplifier. 

Most everything else works. except the volume buttons on the front.
[B]
# MP3 Playback ####################[/B]
#So, playing mp3 with Amarok.  It will complain about codecs, so do this:
sudo apt-get libxine1-ffmpeg libxine-extracodecs

**#do you get a "demux" error when trying to play a shoutcast etc. stream?**
# (note their is probably a better way to do this, but this works and i am lazy so...
top
# look for the PID of "artsd".  assuming the PID is for example 9999, type
kill 9999
# now quit and reopen Amarok and play a stream.

**# Installing a Firewall**
apt-get install kmyfirewall
# it is kind've annoying that when installing itself it does not add an entry to the start menu.  Even Katapult does not see it :( so we have to make our own shortcut.
# click KDE menu, then right click System and choose Edit.  Click New Item, Put KMyFirewall in the name, and in the command put kmyfirewall (if you always want to run it as root, which you have to anyway to make any changes, then put     kdesu kmyfirewall    in the command box.  Then click the icon, and choose the flame icon for this app.

---

### Post by ebeyer on 2007-09-30
Thanks for the instructions.  I look forward to trying this
with my Vaio.

Do you have any information or advice on partitioning
the hard drive and setting up a dual boot with Win-doze?
I may want to cross over, from time to time.

EB

---

### Post by whiterabbitwonder on 2007-10-10
when you install kubuntu (or ubuntu) it will offer to make your computer dual boot.  You could use that option.  But make sure you BACK UP your stuff.  I don't dual boot as I have another computer I use for windows.  Also, on the laptop i use vmware server with a windows xp virtual machine for when i need that OS.  It is much easier than dual booting.  For backup, i recommend [www.mozy.com]("http://www.mozy.com")

---

