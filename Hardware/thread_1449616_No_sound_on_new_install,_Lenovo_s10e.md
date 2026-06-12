---
title: "No sound on new install, Lenovo s10e"
date: 2010-04-08
forum: Hardware
---

### Post by adpads on 2010-04-08
Hi all!

Perhaps I'm posting prematurely as I am in the first few hours of using my shiny new install of Ubuntu 9.10 on a Lenovo s10e netbook. This computer has had several other distros installed on it before, and has never had a problem with sound.

Oddly, this time, I am unable to get any sound out of any programs (amarok, totem, firefox), though I am able to get system sounds in both KDE and gnome. The 'test' function in the KDE settings window gives me a sound for ALSA analog output, but not for pulse or the others.
In Gnome, under settings > sound preferences > hardware I see no devices listed for me to configure. The same is true of input devices on the following 'input' tab.

I have run through the Ubuntu Sound troubleshooting page and can't see any problems. Intel drivers seem to be installed for the Realtek ALC269, and everything looks ok on the alsa project page with information about my system: [http://www.alsa-project.org/db/?f=8fe45d05c63354cefc2d9264f3a0fda939caa487]("http://www.alsa-project.org/db/?f=8fe45d05c63354cefc2d9264f3a0fda939caa487") - unless any of you can see anything?

I know it's a simple solution I haven't seen yet - what can I do to get the sound working?

Thanks to all!

---

### Post by lidex on 2010-04-09
I'm a little confused, are you using kde or gnome? kubuntu does not use pulseaudio. You do have sound, correct? Just not from the programs you mention? Work through this page for gnome/pulseaudio bugs in karmic:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
This one to configure pulse:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")
And this one to to make sure you have packages you need:
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

---

