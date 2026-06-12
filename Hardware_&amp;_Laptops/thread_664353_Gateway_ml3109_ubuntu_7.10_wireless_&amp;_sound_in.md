---
title: "Gateway ml3109 ubuntu 7.10 wireless &amp; sound instructions"
date: 2008-01-11
forum: Hardware &amp; Laptops
---

### Post by ICouldBeatSimon on 2008-01-11
Hey everyone, I'm a new ubuntuforum user.  I got an ml3109 for xmas and decided to load the best OS EVER.  There were two common problems with this laptop.  One couldn't connect to security-encrypted wifi networks and there was no sound.  After reading the 16 page thread, I decided to start a new one so people wouldn't have to search through the long one to figure out what to do.

I'm assuming your system was connected to the internet while installing and you received all possible updates.  To update your machine, use System->Administration->Update Manager.  Note: when I first installed a few days ago, I had around 158 updates.

I don't know if this helped, but I'm a coder, so I also downloaded the most recent version of g++ and its lib package(search in System->Administration->Synaptic Package Managerr for g++-4.2 and g++-4.2-multilib).

Also, make sure you run 'sudo apt-get install build-essential' 

If you haven't done any of this, do so and restart your laptop.

Here's a complete setup for wireless:

Run this command:

```
sudo gedit /etc/modprobe.d/blacklist
```

Add the following lines to the end of that file:

blacklist r818x
blacklist r8180
blacklist r8187

Restart the laptop.

If you click on the network manager applet, you should see practically nothing.

NOW. Download and install the latest ndiswrapper here:

[ndiswrapper]("http://sourceforge.net/project/showf...ease_id=537654")

Extract and terminal into that directory.

Run the following commands:
```

sudo make uninstall
make
sudo make install
```

You should see little or no errors/warnings. I saw one about not using a variable (can't remember name).

Then download the latest realtek drivers here:

[realtek]("ftp://152.104.238.19/cn/wlan/RTL8185_6.1102.0702,UI_1.00.0006.zip")

Extract and navigate through the folders until you see a bunch of windows OS folders.  I personally used WIN2000, but other instructions I've read ask for WINXP. 

Move those to the Desktop. Navigate to either one, and run the following commands (pay attention to output):

```
sudo bash
ndiswrapper -i net8185.inf
ndiswrapper -l
modprobe ndiswrapper
```

After that last command, you should see a signal coming from your secured network.  If not, restart. Also, I don't know if this is needed, but I did it anyway just in case:

```
sudo gedit /etc/modules
```

Add 'ndiswrapper' to the end of the file.

Restart laptop.



For sound, I followed Donnie's instructions here:

[URL="http://donnieknows.com/bin/view/Main///GatewayML3109#Wireless"]Donnie's Instructions
[/URL]

Then, I removed the snd-hda-intel.ko file using this command:

```
sudo rm /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
```

Then I redid Donnie's instructions and presto! it worked!

I suppose one doesn't have to install, remove the file, then REinstall, but this method worked!  If you have an easier method, post it!  I'd love to know as much as the next ubuntu lover.

\\:D/Many thanks to Yoblin, lvleph, and pablodavid.=D> ):P

---

### Post by eltorodeoro on 2008-01-11
awesome!  great how-to for the wireless card.  as of this post, tho, the link to donnie's sound tutorial seems to be broken.

thanks!

jeremy

---

### Post by ICouldBeatSimon on 2008-01-15
I do apologize for the broken link.  I double checked it and it should work now.

---

### Post by thebigeis on 2008-02-04
Could you write a more detailed instruction on how to make the sound work? I tried following yours/donnie/another thread linked to it, and now kmix is always muted and shows no mixers. I'm very new to kubuntu and need step-by-step instructions. Please, help!

---

### Post by thebigeis on 2008-02-04
ALSO, after doing bash enable_sound.sh I get this at the end:
sudo: alsaconf: command not found
alsactl: save_state:1253: No soundcards found...

Should that be right? Anyway, I need a solution!

---

### Post by ICouldBeatSimon on 2008-02-08
I'm sorry, but these these instructions are for Ubuntu Gutsy.  I'm not familiar with Kubuntu at all.

---

### Post by nmosterhaus on 2008-02-18
thebigeis, the alsa-utils package needs to have ncurses-dev installed to be able to compile. 

Try:

sudo apt-get install libncurses-dev

run the script again and then it should compile.

---

