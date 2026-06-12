---
title: "Creative Audigy or SB X-Fi &lt;No Sound&gt;"
date: 2007-10-01
forum: Hardware &amp; Laptops
---

### Post by iheartubuntu on 2007-10-01
In windows, my device manager says I have a "Creative Labs SB X-Fi" sound card. In another diagnostic software program I have in windows called Everest, it tells me the card is a "Creative Labs Audigy 4" card.

In Ubuntu, when I search for the card in the terminal it says I have "Creative SB X-Fi".

This system is a P4-3ghtz dual core and its over a year old now. Today, I decided to install Ubuntu on it (dual boot using wubi) and it has worked fine so far, minus any sound.

I have no sound. Im fairly new to Ubuntu, but can get around if someone is nice enough to guide me through any commands to get the sound working.

Any help would seriously be appreciated! Thanks!

---

### Post by aldeby on 2007-10-02
just try installing the latest drivers from alsa, unfortunately they focus more on quality than on time so currently there are lots of devices supported only by beta drivers (which anyway would be hopefully released on time for 7.10 ubuntu gutsy release)

follow these steps:
```

# apt-get update && apt-get install mercurial build-essential libncurses5 automake autoconf

$ hg clone http://hg.alsa-project.org/alsa-driver alsa-driver
$ hg clone http://hg.alsa-project.org/alsa-kernel alsa-kernel

$ cd alsa-driver
$ ./hgcompile

# make install-modules
# alsaconf
# depmod -a

reboot

```

---

### Post by ubundude on 2007-10-02
It took me a few hours trying different things and asking different people till we tried turning off the Analog/Digital Output Jack. Hopefully it is this simple for you. Doubble click the speaker in the tray, then the "switches" tab and un-check the box.  Test the sound.  Good luck.

---

### Post by BulletzBill on 2007-10-03
Hello,

I also am using a Creative X-Fi sound card and just installed Ubuntu as a dual-boot (I am a novice user) and am having trouble getting sound.

First of all, when I click the speaker icon I get the following error message:
"No volume control GStreamer plugins and/or devices found."

When I go into the device manager, I do see the card, listed as "SB X-Fi" but with Device Type and Capabilities listed as unknown.

I tried executing the commands you posted, but after entering:
```
sudo apt-get update && apt-get install mercurial build-essential libncurses5 automake autoconf
```
I get the following errors:
"E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?"

What am I doing wrong?

---

### Post by Perfect Storm on 2007-10-03
Here's the driver: [http://opensource.creative.com/soundcard.html#X-FI](http://opensource.creative.com/soundcard.html#X-FI) it's still in beta and only for 64bit

---

### Post by BulletzBill on 2007-10-03
> **Artificial Intelligence said:**
> Here's the driver: [http://opensource.creative.com/soundcard.html#X-FI](http://opensource.creative.com/soundcard.html#X-FI) it's still in beta and only for 64bit

Thank you very much. :) But, I am having trouble installing it. I am using the 64-bit version of 7.10 Beta on an athlon X2 but I get this error when I attempt to run the install:
"This product only support 64-bit Operating Systems
Setup will now exit"

any ideas?

---

### Post by Perfect Storm on 2007-10-03
No sorry, it could be a glitch in either the beta driver and/or a glitch in ubuntu beta.

---

### Post by BulletzBill on 2007-10-03
For anyone out there with this same problem, I've found a fix on creative's site. However I have not yet tested this:

[http://connect.creativelabs.com/linux/Lists/Driver%20Issues/DispForm.aspx?ID=18](http://connect.creativelabs.com/linux/Lists/Driver%20Issues/DispForm.aspx?ID=18)

---

### Post by iheartubuntu on 2007-10-03
Thanks for the tips, but ive still failed to get any sound also.

After I download the "tar.gz", I have no clue what to do with it. Its not like a typical deb file that just installs on its own.

---

### Post by Perfect Storm on 2007-10-03
I have no way to test this but try;

```
sudo aptitude install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
```
You properly also need libasound-dev and other -dev/headers


```
cd ~/Desktop
tar zxfv XFiDrv_Linux_US-1.04.tar.gz
cd XFiDrv_Linux_US-1.04
chmod +x installer
sudo sh installer

```

---

### Post by iheartubuntu on 2008-02-21
Just an update for people with the Creative SB X-Fi sound cards...

I found this topic here...

[http://4front-tech.com/forum/viewtopic.php?p=7485#7485](http://4front-tech.com/forum/viewtopic.php?p=7485#7485)

which brought me here...

[http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi)

where I downloaded the x86 deb file for my sound card.

Right now I have some tentative beeping through my speakers when I test them in the system>preferences>sound option. But the speaker icon in the top right is still X'ed out. I'll reboot and see if it helps.

---

### Post by Yellow Pasque on 2008-02-21
> But the speaker icon in the top right is still X'ed out. I'll reboot and see if it helps.
The gstreamer volume control is not compatible with OSS4. Thankfully, someone named Clive Wright (known as seawright on the 4front and Ubuntu forums) wrote a patch and built it so that it's a simple drop-in replacement. Check out the OSS4 link in my signature for a link to that patch (32-bit), and I have the 64-bit version attached to that post as well.
Also, see my directions for adding a panel launcher for the ossxmix program. That will give you much better control of your sound.

If you have any further questions, don't hesitate to ask here or on the 4front forums.

---

### Post by iheartubuntu on 2008-02-21
> **Temüjin said:**
> The gstreamer volume control is not compatible with OSS4. Thankfully, someone named Clive Wright (known as seawright on the 4front and Ubuntu forums) wrote a patch and built it so that it's a simple drop-in replacement. Check out the OSS4 link in my signature for a link to that patch (32-bit), and I have the 64-bit version attached to that post as well.
Also, see my directions for adding a panel launcher for the ossxmix program. That will give you much better control of your sound.

If you have any further questions, don't hesitate to ask here or on the 4front forums.

Thanks. I got the ossxmix panel launcher working, but still no sound.

I dont know what to do with the tar.gz file once I download it. Sorry! It has been a while since I used ubuntu and forgot how to install tar files. Uggh.

---

### Post by Yellow Pasque on 2008-02-21
You should be able to open and extract through the GUI or:
```
tar xzf filename
```
Then, you can follow the directions in the readme/install file.

---

### Post by iheartubuntu on 2008-02-21
OK, I did the tar xzf command in the terminal, switched to the "gstreamer-ossv4" directory and then did what the readme said....

> gzip /usr/lib/gstreamer-0.10/libgstossaudio.so
mv libgstossaudio.so /usr/lib/gstreamer-0.10/

This is what I get...

dave@dave-desktop:~/gstreamer-ossv4$ gzip /usr/lib/gstreamer-0.10/libgstossaudio.so
gzip: /usr/lib/gstreamer-0.10/libgstossaudio.so: No such file or directory

dave@dave-desktop:~/gstreamer-ossv4$ mv libgstossaudio.so /usr/lib/gstreamer-0.10/
mv: cannot move `libgstossaudio.so' to `/usr/lib/gstreamer-0.10/libgstossaudio.so': Permission denied

---

### Post by Yellow Pasque on 2008-02-21
you have to use 'sudo' in front of the command because root is the owner of /usr/lib

Are you using 64-bit Ubuntu?

---

### Post by iheartubuntu on 2008-02-21
no its 32 bit.

I get the same message even with sudo in front of it.

In  the terminal maybe i should be in a different directory? Right now I am at :

> dave@dave-desktop:~/gstreamer-ossv4$

---

### Post by iheartubuntu on 2008-02-21
I rebooted the computer and I have some sound working. Amarok plays MP3 files no prob and I get some audio in a few games too. But generally I get no other audio. No Youtube audio. No Most games dont have audio. Any video files like AVI dont have audio.

Any tips? Its got to be something to do with gstreamer I cant seem to get working.

---

### Post by iheartubuntu on 2008-02-21
Maybe there are some updated gstreamer files out there I should load?

---

### Post by iheartubuntu on 2008-02-22
Hi all. Still no sound from most programs. Any suggestions? Many thanks.

---

### Post by iheartubuntu on 2008-02-22
An update... I do have sound in sopcast and amorak and even VLC, but not in mplayer or nothing from the internet like youtube. Any tips?

---

### Post by iheartubuntu on 2008-02-22
I believe this is the part Im stuck on. If I could get these commands working, I think I can get all sound to work.

> **shirteesdotnet said:**
> OK, I did the tar xzf command in the terminal, switched to the "gstreamer-ossv4" directory and then did what the readme said....



This is what I get...

dave@dave-desktop:~/gstreamer-ossv4$ gzip /usr/lib/gstreamer-0.10/libgstossaudio.so
gzip: /usr/lib/gstreamer-0.10/libgstossaudio.so: No such file or directory

dave@dave-desktop:~/gstreamer-ossv4$ mv libgstossaudio.so /usr/lib/gstreamer-0.10/
mv: cannot move `libgstossaudio.so' to `/usr/lib/gstreamer-0.10/libgstossaudio.so': Permission denied

---

### Post by iheartubuntu on 2008-02-25
*BUMP*

Please anyone. Im desperate to get the rest of my sound working properly. Thanks. :)

---

### Post by Yellow Pasque on 2008-02-25
Sorry to leave you hanging.

Go to the terminal and enter this:
```
sudo nautilus
```
Now go to /usr/lib/gstreamer-0.10
This should bring up a GUI that has root permissions. Now you can move the copy of libgstossaudio.so that came with the patch into usr/lib/gstreamer-0.10

Also, in the terminal you can use this command to control the OSS mixer:
```
ossxmix
```

---

### Post by iheartubuntu on 2008-02-25
For now Im going to use an older sound card, which works great. I'll come back to this problem in the future and retest the sound card from time to time, but for now I want to get my machine up and running. My alt sound card works fine and Ubuntu found it right away.

---

### Post by iheartubuntu on 2008-05-19
Since I never did figure this out, and reverted to an old sound card on that computer... Ive installed Hardy Heron on my laptop here at home and it found everything perfectly out of the box and I find it to be more stable than any release Ive tried so far. I like 8.04 quite a lot!

Does anyone know if Ubuntu 8.04 has drivers that can detect the Creative Audigy - SB X-Fi sound card? Im considering backing up my data and doing a fresh install of 8.04 on my system at work with the x-Fi sound card back inside of it if there is a chance it will work fine.

---

### Post by dtrot55 on 2008-05-19
Check out this link and follow the instructions on post 1....I use the X-Fi and the OSS drivers work fine...though the only thing  i have seen is soem linux games dont have sound..but other than that everything else has worked...but dont expect the functionality you get in windows...these drivers are basic..as in no 24 bit crystalizer and stuff like that...sound blaster for some reason has released a crappy beta driver and is taking forever to get to a final version

[http://ubuntuforums.org/showthread.php?t=571656](http://ubuntuforums.org/showthread.php?t=571656)

---

