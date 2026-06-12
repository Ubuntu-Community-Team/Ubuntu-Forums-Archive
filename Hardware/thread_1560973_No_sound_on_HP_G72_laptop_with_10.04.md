---
title: "No sound on HP G72 laptop with 10.04"
date: 2010-08-25
forum: Hardware
---

### Post by Cactusm123 on 2010-08-25
I've looked at the various posts about this problem, but none of the solutions I've found have worked.

I've tried:

Adding the line "options snd-hda-intel model=g71v" to alsa-base.conf, with variations on the model.

Running sudo apt-get install linux-alsa-driver-modules-`uname -r`, which returned a package not found error for a generic driver.

aplay -l returns:

card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

The speaker is labeled Altec Lansing, but the computer doesn't show any proprietary drivers for it when I search for them.

Any help would be much appreciated.

EDIT:
Fixed it. There's a Linux driver at [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=24&Level=4&Conn=3&DownTypeID=3](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=24&Level=4&Conn=3&DownTypeID=3) that includes steps to make it work.

Worked like a charm.

Hope this helps anyone with the same problem.

---

### Post by MachoMan1350 on 2010-09-15
hey, i'm having the same problem with the same laptop. i have downloaded the Linux driver from the link you provided, but how do i install it? i read the instructions it came with, but i didn't understand them.....

---

### Post by Cactusm123 on 2010-09-15
These are the instructions I used. I'll see if I can help clarify them. My comment's will be in []'s.

Note: Ubuntu OS, please use manual install.
      Run commands need to add sudo at first words. [at the terminal, enter 'sudo su' at the prompt, no quotes, and press enter. That elevates you to root privileges.]

Manual install:
Step 1. unzip source code 

[You need to be in the directory you downloaded the file to. I DL'd it to ~/Downloads, so the first thing I would do is 'cd ~/Downloads' w/out quotes to be in the right spot. Then you copy the next line, but you have to replace the .xx. with the version number, so erase the line to that point and press TAB to autocomplete.]

        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Complied source code [TAB completion also applies to this one - copy 'cd alsa-driver-1.0.' into the terminal, press TAB, then press enter. The rest of the commands can be copy-pasted into the terminal as is.]

	a. cd alsa-driver-1.0.xx
	b. ./configure --with-cards=hda-intel
	c. make
	d. make install

Step 3. reboot your machine

[I didn't have to do step 4]

Step 4. Use the alsamixer the disable mute (All audio line default is mute)
        Must to compile and to install the ALSA library and utility. (Use automatic install is already install)
        excute alsamixer

Hope that helped! Any other questions, feel free to ask.

---

### Post by Tootler on 2010-09-17
I have the same problem but I have external speakers connected via the headphone O/P and they work fine. Also I do not wish to get into the business of downloading and compiling source code if I can possibly avoid it. 

I have also noticed on reviews of HP laptops in online retailers sites, there is a general complaint about the internal speakers being very quiet so there may be a hardware issue.

---

### Post by Cactusm123 on 2010-09-17
As far as I'm aware, no way to do it without the driver. Compiling isn't difficult - sudo make, then sudo make install. I've never had any trouble with he speaker volume, and it seems about the same in Linux and Windows.

---

### Post by lidex on 2010-09-17
> **Tootler said:**
> I have the same problem but I have external speakers connected via the headphone O/P and they work fine. Also I do not wish to get into the business of downloading and compiling source code if I can possibly avoid it. 

I have also noticed on reviews of HP laptops in online retailers sites, there is a general complaint about the internal speakers being very quiet so there may be a hardware issue.

The problem may be fixed in the next ubuntu release so you may only need the work-around until then. I'd like to have a look at it if you wouldn't mind.

Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```

---

### Post by Tootler on 2010-09-18
I installed the driver following the instructions given and now I am worse off. I have no sound at all. The speaker icon in the upper taskbar now instead of having a spreading sound symbol just has a double dash (--) after it.

From the previous post 

> Can you post the output of these terminal commands for me please:

```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#*
```

Here is the output

```

geoff@Ptera:~$ aplay -l
aplay: device_list:223: no soundcards found...
geoff@Ptera:~$ dpkg -l | grep "alsa"
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  alsamixergui                          0.9.0rc2-1-9                                    graphical soundcard mixer for ALSA soundcard
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                       0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA
geoff@Ptera:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

```

The output is worrying to say the least. Something is clearly missing.

---

### Post by Tootler on 2010-09-18
I recompiled and reinstalled the drivers and it is now working OK including sound on the internal speakers.

I don't know what went wrong with the original install.

Whole morning wasted! Now to go and cut the grass.

---

### Post by felipemartim on 2010-10-07
[Cactusm123]("http://ubuntuforums.org/member.php?u=942239") workaround solved my problem. Thanks a lot!

---

### Post by kle on 2010-10-24
Thank you, Cactusm123 - !!!

Perfect, and gosh am I ever glad to get my sound back!

By the way, I would mark your issue as solved so that people googling the issue will see at once that here they might find the solution.

---

### Post by Dngrsone on 2011-07-24
[Updating ALSA](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/) worked for me.

---

### Post by Dngrsone on 2011-12-08
> **Dngrsone said:**
> [Updating ALSA](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/) worked for me.

What sucks is that I have to reinstall it every time the kernel updates.  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/argh.gif[/IMG]

---

