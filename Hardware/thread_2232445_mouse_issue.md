---
title: "mouse issue"
date: 2014-07-02
forum: Hardware
---

### Post by freewarelover on 2014-07-02
Hey so I have Lubuntu on my netbook and after making the adjustment to having it suspend when I close it, when I open it back up the touchpad mouse isn't really responsive. Has anyone else noticed this issue? I tried looking to see if it was listed under known issues on the main site butr didn't see it.  Any advice would be great.

---

### Post by bapoumba on 2014-07-02
To come out of suspend, you need to hit the space bar first, then touchpad and mouse work, at least here.

---

### Post by freewarelover on 2014-07-03
hmm doesn't work for me I still had to force shutdown with power button. Also the issue only occurs if it's put into suspension for like an hour or more.

---

### Post by bapoumba on 2014-07-03
You may want to have a look here, just posted screenshots for some other issue. you'll have my settings that work here.
[http://ubuntuforums.org/showthread.php?t=2225413&p=13064791#post13064791](http://ubuntuforums.org/showthread.php?t=2225413&p=13064791#post13064791)

---

### Post by freewarelover on 2014-07-14
Sorry for the prolonged response I thought I responded to that a while ago, came back to realize I never did lol. I tried those settings but they didn't make a difference to the issue.

---

### Post by bapoumba on 2014-07-15
Hmm, having light-locker running is the step that go it working for me. Here is where I found out : [http://ubuntuforums.org/showthread.php?t=2224690](http://ubuntuforums.org/showthread.php?t=2224690)
Will need to look for a specific bug with touchpad functionality upon resume from suspend.
What are your hardware specs again ?

---

### Post by WinEunuchs2Unix on 2014-07-15
Since it only happens when suspending for more than an hour and not less than an hour could it be battery related?

Does your Netbook BIOS wake itself up after a period of time via WLAN or some other funky option?

---

### Post by bapoumba on 2014-07-16
I'm not sure..

---

### Post by freewarelover on 2014-07-23
Hey again sorry for the delayed response. I've applied all the settings you posted but still no luck. It's a HP netbook. (once I login and move the touchpad while at the desktop it switches between the two desktops Lubuntu provides and barely moves curser which therefore forces me to shutdown via power button)

---

### Post by bapoumba on 2014-07-23
OK. These are a few threads where you may get relevant info.

First, from older forums post, these still work on lubuntu 14.04. First one should show your touchpad, second the settings you have :
```
xinput --list
synclient -l
```

[http://ubuntuforums.org/showthread.php?t=2217553](http://ubuntuforums.org/showthread.php?t=2217553) ; [http://forums.linuxmint.com/viewtopic.php?f=49&t=157115&p=813402&hilit=thinkpad+twist+touchpad#p813402](http://forums.linuxmint.com/viewtopic.php?f=49&t=157115&p=813402&hilit=thinkpad+twist+touchpad#p813402) < may not be relevant to you
[http://ubuntuforums.org/showthread.php?t=2217808](http://ubuntuforums.org/showthread.php?t=2217808)
[http://ubuntuforums.org/showthread.php?t=1858855](http://ubuntuforums.org/showthread.php?t=1858855)

What is you netbook model ?

---

### Post by freewarelover on 2014-07-23
I tried following those links but my install of Lubuntu doesn't recognize gedit as a command. Also not sure about the model. Maybe this? 311-1025NR

---

### Post by bapoumba on 2014-07-23
oh, lubuntu uses leafpad, not gedit :)

---

### Post by freewarelover on 2014-07-24
Well I got good news and bad news.

Good news: got into the grub file via leafpad.
Bad news: it says to locate a line of text as if the file as is filled with text but for me it's blank. (yes the whole file is blank) What should I do? Could you maybe give the text that's supposed to be there?

I'm following the instructions here [http://forums.linuxmint.com/viewtopic.php?f=49&t=157115&p=813402&hilit=thinkpad+twist+touchpad#p813402](http://forums.linuxmint.com/viewtopic.php?f=49&t=157115&p=813402&hilit=thinkpad+twist+touchpad#p813402)

> [COLOR=#333333][FONT=Lucida Grande]2. The GRUB configuration file should open. Locate the following line:[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]GRUB_CMDLINE_LINUX=" "

^^^ No such line exists. No line of anything does.[/FONT][/COLOR]

---

### Post by bapoumba on 2014-07-24
I do have that line in /etc/default/grub
```
GRUB_CMDLINE_LINUX=""
```

How are you booting in the computer ? In UEFI mode with grub2 ?

---

### Post by freewarelover on 2014-07-24
I don't know how do I tell?

Edit: a friend showed me how to tell. I'm running BIOS not UEFI

Edit2: nevermind. Was going to add the text from a grub file in VM of Lubuntu that I'm running but didn't have to because text appear there today so I made the modification. Fingers crossed.

Edit3: It didn't do the trick.

---

### Post by bapoumba on 2014-07-26
I have no real idea.. 
Please have a look at /var/log/dmesg right after trying to wake up from suspend.
If you are stuck and cannot get back to a graphical session, <ctrl><alt><f2> will get you to a tty, enter your login/password and run :
```
dmesg > my_dmsg_log
```
That will create a file my_dmsg_log in your /home file that you can read later after a reboot. The file can be quite long, have look at the bottom first. If you need to do that several times in the future, use a different file name each time. 
To reboot, please run from the tty (always better than a hard shutdown) :
[code]sudo reboot/code]
Or remember that "Raising Elephants Is So Utterly Boring" or "Reboot Even If System Utterly Broken" and use the Magic SysRq key combo : <alt><PrinScreen>reisub (do not release <alt><PrintScreen> between letters) if the sudo reboot does not work.

---

### Post by freewarelover on 2014-08-02
When I did crtl+alt+F2 it took me to tty2 (yes "tty2" not tty) which didn't recognize my login pass. I had to shutdown with power button. Rebooted hoping it wouldn't go back to that screen. It didn't thank god.

Also now ever since I went through that booting looks a little different. There's a line of yellow text that appears and goes away during boot.

Edit: the yellow text happens a random boots.

---

