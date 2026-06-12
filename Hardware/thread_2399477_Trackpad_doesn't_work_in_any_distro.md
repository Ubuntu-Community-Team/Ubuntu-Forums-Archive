---
title: "Trackpad doesn't work in any distro"
date: 2018-08-25
forum: Hardware
---

### Post by xyzdig on 2018-08-25
Hello, this beginner needs some help here. A few months go I had a fully functioning trackpad, but ever since I had to format my HDD, there's no way to make it work in any distro. I used to dual boot and it worked on Windows 10, but not on Solus (which is the one I used before) or Ubuntu (current one). I'm currently using a mouse, but it's not always convenient. I remember while I was trying to make dual booting work, the trackpad would sometime not work on live USB's. After a while, it didn't work in installed systems or Live USB.. I already tried a lot of the things I found online but they haven't worked. It doesn't help that I still don't quite understand Linux so I'm really lost. One thing I did was use the "xinput" command on the terminal and the trackpad does seem to appear. It seems to be the "Virtual core XTEST pointer". Can anyone help me? Thanks in advance.

---

### Post by xyzdig on 2018-08-27
up

---

### Post by coralof on 2018-08-27
Try inputting the following into terminal

[COLOR=#000000]sudo apt-get install xserver-xorg-input-synaptics


[/COLOR]

---

### Post by xyzdig on 2018-08-29
It seems it got installed it,but it's still not working

---

### Post by coralof on 2018-08-29
And you've restarted and everything? Hmm... What brand / model of laptop is it?

---

### Post by xyzdig on 2018-08-29
It's a brand from my country, and unfortunately there's little to no info of it online. I couldn't even find a manual or the touchpad drivers. It's weird because it used to work. I was distro hopping a lot a few months ago and I didn't have to do anything to make it work. It started failing and eventually stopped working when I had to format my drive and reinstall everything.

---

### Post by coralof on 2018-08-30
Perhaps its a hardware issue, then. Maybe you could try opening up the bottom and checking the connections on the motherboard? Or if it used to work, have you tried re-installing the main system?

---

### Post by xyzdig on 2018-09-07
> **coralof said:**
> Perhaps its a hardware issue, then. Maybe you could try opening up the bottom and checking the connections on the motherboard? Or if it used to work, have you tried re-installing the main system?

So I had to replace my HDD because it was dying, told the guy to see if he could fix the touchpad while he was at it, and he said it started working after the installation. Not sure what happened there, but at least it works now.

---

