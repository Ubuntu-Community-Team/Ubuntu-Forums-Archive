---
title: "Can't install on HP Pavillion ZE4420"
date: 2006-09-21
forum: Hardware &amp; Laptops
---

### Post by ronourse on 2006-09-21
I have tried installing the latest Ubuntu distribution on my HP Pavillion ZE4420 laptop. The laptop has an AMD Athlon XP 2200+ processor with 256 meg of ram, of which 64 meg is dedicated to video. I have XP on it and it runs fine other than taking forever to finish booting and some apps do run slow. I know the amount of ram is marginal (it uses PC100 ram), but that is what it came with.

It boots fine from the Ubuntu CD but is VERY slow when running any apps from the CD (again, is ram size the culprit?). I went to install Ubuntu on the hard drive (30 gig with 20+ free), but the system locks up tight after many minutes of just trying to open the Installer. The Installer window never opens completely and is blank when it locks up. I have used the same CD to install on two other desktop (intel) systems.

Is this laptop as configured capable of running Ubuntu? Am I using the correct Ubuntu distribution? What else could be causing this? Is there another distribution (sorry Ubuntu) that would install properly?

Any help or suggestions would be appreciated. Thanks.

---

### Post by Mor Hedroom on 2007-02-02
Hi ronourse!

I hope I have some good news for you.  I too have an HP Pavilion ze4420us, and was going to try it out as my first experience with 6.10 Edgy.  I've never done anything with Linux before, but after about 6 months of hemming and hawing, I took the plunge.

It sounds like your CD may be fine, and I see that you've been a little ignored on this forum as as well as another, so when I was experiencing the same symptoms as you, I was quite discouraged.

Happily, in the shower this morning, it came to me that if the Live CD is having problems with the memory, it would certainly slow things down.  I thought of trying Xubuntu, or downloading the alternate install ISO and try going from the text interface, but our computer should have just enough memory not to be a total downer like it was being!

I then remembered that in the BIOS setup there is an option to play with how much memory is allocated as video buffer.  Looking there, I found it was set to "Auto", so I set it to 8MB (the lowest setting), since I don't need serious fast video just to install an OS.  Sure enough!  Nice, pleasant, quick and easy.

Oh, and don't forget to disable USB legacy support in the BIOS as well.  Also, you may want to hit the <escape> key at the initial boot screen, to get the boot: prompt and tell the installer to ignore the PCMCIA slot for now.  You can do this by typing the following:  (I'll include the prompt, so just make the input look exactly like this...

boot: live hw-detect/start_pcmcia=false

Then hit enter, and your system will boot up much faster an easier, and you can actually look around at some of the apps!  I played a couple of games, and ran the calculator to make sure...feats that were impossible before specifying small video memory!

I hope this isn't too late, and that it works for you.  Good luck!

-Mor Hedroom

---

### Post by mikewhatever on 2007-02-02
I was wondering, if there was an option of disabling PCMCIA after the installation.

---

### Post by Mor Hedroom on 2007-02-06
Hi Mike.

I would think that there is, but I'm just beginning with Linux.  I remember finding somewhere that there is a file that controls the boot configuration, but I can't recall what it is.  If you put the same command I wrote above (hw-detect/start_pcmcia=false) within that file, it should work.

However, I have not yet had any problems with the PCMCIA slot after installing.  The only issue I'm working around right now with the help of the folks around here is getting a WiFi PCMCIA card to work.

I did find this, though.  Hope it helps.  (Found at [the desktop guide]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s04.html"))

Run a system command automatically at startup

Sometimes it can be useful to run a custom command whenever your computer starts up. To do this:

   1.  Edit the crontab with administrative privileges (see Chapter 2, Administrative Tasks):  sudo crontab -e

   2.  Insert the following line:

      @reboot /home/user/command

      [Note]:  Replace /home/user/command with the full address to your command.

   3.  Save the file and exit.

Good luck!

-Mor Hedroom

---

