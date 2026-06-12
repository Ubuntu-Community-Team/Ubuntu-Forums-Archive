---
title: "Few issues with Ubuntu especially with 5.1 system"
date: 2013-01-10
forum: Hardware
---

### Post by Yowan on 2013-01-10
I've been using Ubuntu in VMs for the past 3 years and finally decided to give the 64-bit version a try on a physical install, however I've been running into few issues:

1. My audio is missing the center channel of my 5.1 speakers, and  therefore most of my HD movies have no dialog, and the subwoofer doesn't  work either. The default 5.1 sound setting is a total joke and doesn't even work properly. The system software doesn't even have additional audio tuning options for speaker-specific configuration like on Windows. On Windows the driver software automatically adjusted all sound channels  as they should be but can't find anything on Ubuntu - the options are  simply not there, the settings are barely even comparable to Windows.

2.I've typed my password about a thousand times already to install software,  which makes me wish that things should be simple as in Windows (Can't there be some UAC-alike thing in Ubuntu). How can I once for all avoid typing my password each time I want to install something? 

Where can I obtain a decent driver for my sound card (SoundMAX ADI 1988B)?

3. I've no resolution to  the mouse scroll speed issue, there simply isn't any option in settings to adjust the mouse scroll speed, what kind of modern OS doesn't have this? How can I have this settings without installing any additional software? Add to this a ridiculous default mouse scrolling speed with no option to  change it in the OS, and you're left with a rather unpleasant  experience.

4. Why can't there be a simple user friendly GUI for Linux software installers? why do I have to mess up with tar.gz files? Why not simply some .exe-alike installers? (.deb is not even close) - Why does this have to be so complicated?

5. I figured I'd update my nVidia drivers. Now every time I've used Linux,  I've been scared of this step, as it more often than not, fails. Using  the Ubuntu Software Centre, I selected the "tested" nvidia current  drivers, and then restarted X to load the new drivers. This as always  was a disaster. Upon logging in to the desktop, I no longer had Unity, I  recall this happening in 12.04 also, but hoped it'd be fixed by now.  Needless to say fixing this involved loading a terminal, removing the  drivers, downloading the kernel source and the headers and trying again.  This did work, but what a massive pain in the *** which shows that no  matter how pretty they make the OS, it's just a clusterbomb of not quite  right. I found out that it was some kinda of unfixed bug in Ubuntu itself.

Why do such things have to be so complicated? On Windows you just have to click on a setup file, sit tight and everything is done perfectly without even having to mess up with terminal windows etc.. Needless to say the Nvidia driver feels half baked, not even comparably to first grade Nvidia quality drivers for Windows.

6. How can I move the Unity Launcher to the bottom - they say Ubuntu is so customizable but I didn't find anything about that, nothing except a thread from the 11.xx days with steps that don't even work with 12.10.

7. The default fonts are horrible for the most part, especially distorted and washed out in Chrome. Has something to do with rendering but it occurs even with the default display driver. I have no clue why. I'm using a GTX460 if that matters.

I'm so disappointed in this release as I was expecting a perfect out of the box experience but as of yet, it's still just too much hassle, especially when you have to use the terminal to do almost everything. I almost never used CMD on Windows for basic stuff like installing drivers, configuring the system or doing any complex things. The issue with Ubuntu is with the ease of use and proper software, it's too complex for the average user.

---

### Post by ahallubuntu on 2013-01-10
I'm very happy with Ubuntu 12.04 LTS myself.

You can use the Ubuntu software center to install software without tar.gz files most of the time.  There are a few special cases where you do have to tweak things in more advanced ways, but these are the exception, not the rule.  And once you do them, generally you don't have to keep doing them.

It is not recommended to remove the admin (sudo) password to install software, just like it's not recommend in Windows.  (it's REALLY not recommended in Windows, as you make yourself much more secure and vulnerable to infections there.)  If you really want to get rid of the password, try here:

[http://www.howtogeek.com/116757/8-ways-to-tweak-and-configure-sudo-on-ubuntu/](http://www.howtogeek.com/116757/8-ways-to-tweak-and-configure-sudo-on-ubuntu/)

It is recommended instead that you make the timeout longer so you can go longer between needing to type it from the last time.

Otherwise, your post seems as much about complaining than asking for help, and I can't help you with the attitude except suggesting you try another Linux distro or stick with Windows if you are unhappy with Ubuntu.  Ubuntu is far from perfect, but for what it is, it's quite amazing.  I just started playing with Windows 8 and it gave me quite a headache - but if you'd prefer that, have fun.  If you really want help with Ubuntu here, stick to constructive questions and get rid of the attitude.

---

### Post by Yowan on 2013-01-10
Sorry for being like this but Ubuntu really drives me nuts sometimes. :P

I'll manage but is there anything I can do about issues 1,3 & 6? Those are my primary annoyances. Can't use Ubuntu without proper Audio drivers.

---

### Post by tlhIngan on 2013-01-10
> **Yowan said:**
> Sorry for being like this but Ubuntu really drives me nuts sometimes. :P

I'll manage but is there anything I can do about issues 1,3 & 6? Those are my primary annoyances. Can't use Ubuntu without proper Audio drivers.

Have a search in the Synaptic Package Manager
This is the recommended way to install software and drivers, you might find a driver package for your issues.

---

### Post by ahallubuntu on 2013-01-10
> **tlhIngan said:**
> Have a search in the Synaptic Package Manager
This is the recommended way to install software and drivers, you might find a driver package for your issues.

FYI, Synaptic is not even installed by default in 12.04 LTS any longer.  Ubuntu Software Center is the preferred way to install stuff now.  Personally, I always install Synaptic myself (very easy) but the average new user wouldn't have it installed.

---

### Post by ahallubuntu on 2013-01-10
> **Yowan said:**
> Sorry for being like this but Ubuntu really drives me nuts sometimes. :P

I'll manage but is there anything I can do about issues 1,3 & 6? Those are my primary annoyances. Can't use Ubuntu without proper Audio drivers.

You should install your Nvidia drivers using "Additional Drivers" in the "System Settings" window in Ubuntu 12.04 .  Always try the easy way, using a mouse and the Gui, before resorting to terminal work.  I know I've installed such drivers for both NVidia and AMD/ATI cards in Ubuntu this way without needing to do anything in the terminal or having any problems.  Just try it.  As a last resort, go to NVidia's website and look for a driver.

Can't help you with the mouse scroll issue.

Can't help you with the fonts issue - I have no issue with the fonts in Chrome; they are different from the ones in Windows.  I got used to them.  Windows fonts look funny to me now when I go back.

---

### Post by Hugh Mulqueen on 2013-01-10
I think you just described alot of whats wrong with the open-source world right there...
Hardware support has always been linux's achilies heel. For example sound supriseing as it may seem is one of the big issues, PulseAudio is the underlieing problem there. 5.1 isn't supported that well. what sound card do you have?

try running in the terminal:
**arecord -l**

If you can try to give as much info about your problem people might be able to fix it then.

Your experience was alot like mine when I was starting out I couldn't break away from windows for along time. Until ubuntu got its act together ubuntu 8.10, yes!!! always had trouble with NVIDIA graphics drivers. the problem with NVIDIA is that their drivers are propietary drivers. So ubuntu can't fix any bugs or do anything with them. If you have a serious bug with them you have to wait for the company to fix it. Linus Torvalds said "F**k NVIDIA there last year. Just tell you how frustrating it is for even the most profecant hackers.

You also want to move the launch bar to the bottom. Now theres a few options here:
Cairo dock:
Pros:
Easy enough to set up and alot of customization options.
Cons:
Too much customisation?
I don't know whatever floats your boat. 

I hate unity I use the old reliable linux mint desktop Cinnamon desktop or Mate. You can get the installation notes here:
[http://wiki.mate-desktop.org/download]("http://wiki.mate-desktop.org/download")

Or Cinnamon here:
[https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable]("https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable")

As for entering in your password a zillion times. Thats what makes linux OS's more secure (than the rest Windows/MacOS). Programs can't sneak by you and cause problems (like viruses, worms, trojens and rootkits).

If your on the terminal you can use:

**sudo -i**

For temporary root access. Make sure you use the exit command after and close the session.

---

### Post by Yowan on 2013-01-11
> **Hugh Mulqueen said:**
> I think you just described alot of whats wrong with the open-source world right there...
Hardware support has always been linux's achilies heel. For example sound supriseing as it may seem is one of the big issues, PulseAudio is the underlieing problem there. 5.1 isn't supported that well. what sound card do you have?

try running in the terminal:
**arecord -l**

If you can try to give as much info about your problem people might be able to fix it then.

Your experience was alot like mine when I was starting out I couldn't break away from windows for along time. Until ubuntu got its act together ubuntu 8.10, yes!!! always had trouble with NVIDIA graphics drivers. the problem with NVIDIA is that their drivers are propietary drivers. So ubuntu can't fix any bugs or do anything with them. If you have a serious bug with them you have to wait for the company to fix it. Linus Torvalds said "F**k NVIDIA there last year. Just tell you how frustrating it is for even the most profecant hackers.

You also want to move the launch bar to the bottom. Now theres a few options here:
Cairo dock:
Pros:
Easy enough to set up and alot of customization options.
Cons:
Too much customisation?
I don't know whatever floats your boat. 

I hate unity I use the old reliable linux mint desktop Cinnamon desktop or Mate. You can get the installation notes here:
[http://wiki.mate-desktop.org/download](http://wiki.mate-desktop.org/download)

Or Cinnamon here:
[https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable](https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable)

As for entering in your password a zillion times. Thats what makes linux OS's more secure (than the rest Windows/MacOS). Programs can't sneak by you and cause problems (like viruses, worms, trojens and rootkits).

If your on the terminal you can use:

**sudo -i**

For temporary root access. Make sure you use the exit command after and close the session.
Thanks for your reply, here is the information:
```

card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by Hugh Mulqueen on 2013-01-13
I have good news just found a fella with the same problem as yourself with the same audio chip. 

[http://ckozler.net/?p=70]("http://ckozler.net/?p=70")

It looks like your surround sound speakers might be turned down. All you need to do is turn them up!

This post is a little bit old it dates back to ubuntu 9.10 or earlier. 

Skip down to the alsa bit and run this command:

**alsamixer -c 0**

ALSA is very easy to use all you have to do is select the "surround", "Centre", LFE and "Side" with the left/right directon keys and use the up/down to turn the sound up. And it should work after that.
Enjoy your movies!!!):P

---

### Post by Yowan on 2013-01-25
> **Hugh Mulqueen said:**
> I have good news just found a fella with the same problem as yourself with the same audio chip. 

[http://ckozler.net/?p=70](http://ckozler.net/?p=70)

It looks like your surround sound speakers might be turned down. All you need to do is turn them up!

This post is a little bit old it dates back to ubuntu 9.10 or earlier. 

Skip down to the alsa bit and run this command:

**alsamixer -c 0**

ALSA is very easy to use all you have to do is select the "surround", "Centre", LFE and "Side" with the left/right directon keys and use the up/down to turn the sound up. And it should work after that.
Enjoy your movies!!!):P
Still doesn't work, no surround sound either.  I found out that I have to frequently switch between Sound Modes during playback until I get sound fro my subwoofer. But for some reason after few minutes it reverts back to the previous situation, i.e no surround, playback only through 4 speakers without the anything from the subwoofer. Also the sound quality is terrible compared to what I had on Windows.

---

### Post by furything on 2013-01-25
Just a quick note.
Earlier in the thread you mention your sound max chip but as I understand it you are using a vm.

You need to check the vm sound emulator (there are normally a couple of choices) and make sure that the driver you have installed is the emulated one and _NOT_ the host one.

Also the chosen emulated sound card has to be of course 5.1 compatible

Should also say that I have found that the intel 'HD' sound driver can be a pain. Every time I have to rebuild something with Intel sound I go weak at the knees. HDMI out through nVidia by far easier and always seems to just work.

In general I find the live cds very good at finding device drivers. In fact with servers ubuntu is easier to use than windows so keep persevering.

---

### Post by Yowan on 2013-01-27
> **furything said:**
> Just a quick note.
Earlier in the thread you mention your sound max chip but as I understand it you are using a vm.

You need to check the vm sound emulator (there are normally a couple of choices) and make sure that the driver you have installed is the emulated one and _NOT_ the host one.

Also the chosen emulated sound card has to be of course 5.1 compatible

Should also say that I have found that the intel 'HD' sound driver can be a pain. Every time I have to rebuild something with Intel sound I go weak at the knees. HDMI out through nVidia by far easier and always seems to just work.

In general I find the live cds very good at finding device drivers. In fact with servers ubuntu is easier to use than windows so keep persevering.
I'm actually running Ubuntu on a second HDD, the sound is the only thing which is keeping me from using it on a daily basis. Why has the Ubuntu sound stack not been fixed/made to work properly on my sound card. Is there something wrong with Ubuntu or is it just some kind of bug that will be fixed in the next release?

---

### Post by Yellow Pasque on 2013-01-27
> **Yowan said:**
> Why has the Ubuntu sound stack not been fixed/made to work properly on my sound card? Is there something wrong with Ubuntu or is it just some kind of bug that will be fixed in the next release?

The bug has 0% chance of being fixed if you (or someone with your laptop) don't report it. You can't just assume that a very hardware-specific bug like that will be reported and fixed. BTW, what is your laptop model?

---

### Post by furything on 2013-01-28
looks like there was a bug report and work being done to fix it.
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/213206](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/213206)
Have not read this to see if fixed or if there is a description of a process to get surround sound to work now. I will leave that to you to read ;)

---

### Post by Yellow Pasque on 2013-01-28
> **furything said:**
> Have not read this to see if fixed or if there is a description of a process to get surround sound to work now. I will leave that to you to read ;)
Maybe you should read it ( ;) ) since the bug is about the digital output and not missing center/subwoofer on analog 5.1

---

### Post by furything on 2013-01-28
:redface: Sorry[SIZE=2] Temüjin yes I probably [SIZE=2]should. 

[SIZE=2]This will t[/SIZE]each me to take time and read threads[SIZE=2] [SIZE=2]rather than [/SIZE][/SIZE]GLANCE. 
[SIZE=2][SIZE=2]
I[SIZE=2]nstalling win 2008 r2 on a sunfire [/SIZE][/SIZE][/SIZE]box which is far more frustrating than run[SIZE=2]ning ubuntu server 12:10 on [SIZE=2]one.[/SIZE][/SIZE]
[/SIZE][/SIZE]

---

### Post by Yowan on 2013-01-30
> **Temüjin said:**
> The bug has 0% chance of being fixed if you (or someone with your laptop) don't report it. You can't just assume that a very hardware-specific bug like that will be reported and fixed. BTW, what is your laptop model?
I'll look into it, where exactly should I report hardware-specific problems? I'm using a PC btw, the sound card is an Asus Supreme FXII which is not completely a standalone card as it is plugged in the audio riser slot of my board). On Windows it required a driver which automatically adjusted the speaker setup. I couldn't find the Linux version of that thing on Asus's website. It seems that they never provided any linux drivers. :(

---

### Post by Hugh Mulqueen on 2013-02-09
Really I'd like to try to fix something there if you could post as much as you can and anyone else that has the same hardware. Link the info to launchpad and we'll try to get this thing up to speed. 

I was looking to do some sound hardware hacking so give us a hand there with the post above:
[https://bugs.launchpad.net/ubuntu/+s...er/+bug/213206]("https://bugs.launchpad.net/ubuntu/+s...er/+bug/213206")

Or not 505 error there... so close. 
Please post in new bug report:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1120853]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1120853")

Could someone give me a more verbose output of the above driver for development purposes?

[https://wiki.ubuntu.com/DebuggingSoundProblems]("https://wiki.ubuntu.com/DebuggingSoundProblems")

**wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh**
It will run automatically and then file it in my new bug report:

Thanks.

---

