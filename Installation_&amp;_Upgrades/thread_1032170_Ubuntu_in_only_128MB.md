---
title: "Ubuntu in only 128MB"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by Yako no Kai on 2009-01-06
Here's a beginner's guide to ubuntu in only 128MB, by a beginner.  Mostly, this post is to give information.  I would also like to hear any ideas for ways to add to usability without sacfificing performance. This is my first posting, so please let me know if I make any wrong moves in the below.

(I'm not saying that I'm without any problems to be solved.  I have one, there is already a [thread](http://ubuntuforums.org/showthread.php?t=122402) about it, it doesn't have much to do with this post, and it's a mess.)

-

When you look at the requirements for Ubuntu, they say that even for Xubuntu, 128MB is too little.  But I've found that with LXDE, the light X desktop environment, everything is darn snappy with 50MB to spare.  Of course, it'll go to swap if you try to do anything, but with that RAM, so will Windows.

(My other specs: Duron 1300, Matrox video card, SBLive ... this is an old PC that I ended up with and decided to why not give it a try. It currently lives under my desk, but if remote access had worked, I would have been using Ubuntu more than when dual-booting the PC I'm typing on.)

My main resource: [http://wiki.dennyhalim.com/ubuntu-minimal-desktop](http://wiki.dennyhalim.com/ubuntu-minimal-desktop) 
(Ignore where denny says "don't install the base system.")

-

Here are the steps I followed:
0-a. I shrank a partition, leaving 4GB empty space.

0-b. Using UNetbootin, I attempted to boot the intrepid mini iso from hard disk. This turned out to be a mistake. Just to warn anyone thinking about this: the C: drive must be Win2k/XP. If C: is, for example, Windows 98, you'll get something like this: "Windows could not start because the following file is missing or corrupt: winnt_root\System32\Ntoskrnl.exe."  I think there is a way around this, but it's offtopic for this post.

1. Continuing with the mini iso, partition and install the base system.  Select the linux-generic kernel metapackage when prompted.

2. Finish setup and reboot.  Log in to your command line system.

3. ```
sudo aptitude install xserver-xorg-core xinit menu menu-xdg alsa-utils gdebi-core synaptic logrotate
```

```
sudo aptitude install --without-recommends lxde gnome-icon-theme openbox-themes xdg-utils libjpeg-progs
```

```
sudo aptitude install thunar x11-xserver-utils tango-icon-theme thunar-volman lxrandr roxterm catfish slim lxnm obconf miscfiles alsamixergui
```

3 Notes.
LXDE recommends GDM. If you want to use something smaller, like slim or XDM, you'll need to use the without-recommends flag. GDM is necessary for setting up VNC server, but it didn't help me any.

For some reason, alsamixergui made the difference between sound and error-free silence.  I didn't change a single setting to get sound to work.  Installing it seemed to be enough.

Roxterm is my current favorite light xterm.

Not everything needed by LXDE gets installed by default.  The next 3 notes deal with this.

[list]
[*] I don't particularly care for the Tango theme, but if you follow only the instructions above, PCManFM will give you a message, on every login, telling you to create the file .gtkrc-2.0 and add 
```
gtk-icon-theme-name="Tango"
```
to it. I've found that, of the gnome themes, only Tango makes the error go away.

[*] You need to have a directory named Desktop in your home dir, so add one.  It is not created by default, and without one, you get an error if you try to add any icons to your desktop.

[*] You will get an error when you edit your LXDE screensave prefs.  The cause is this directory in the advanced tab: /usr/share/backgrounds.  You can clear it or run the following command:
```
sudo mkdir /usr/share/backgrounds
```
[/list]

4. For apps, I went with Opera (slim on any OS) and audacious as a slim mp3 player.  Other apps are probably offtopic for this post. Aren't there enough 'light app' threads?

---

### Post by mpsii on 2009-01-29
Very good write-up.

---

