---
title: "Ubuntu noob in need of support"
date: 2009-01-27
forum: Hardware
---

### Post by bicparker on 2009-01-27
This is the first time I've worked with linux and I've been doing so for about a week.  But in this small amount of time, I have amassed two big problems.  The first problem is the most ominous.  Whenever I am working in the terminal and accidentally press the backspace button while nothing that I've typed exists in the command line; the computer logs itself off.  This also happens when I type in a word that returns no results in the find function on firefox.  The second problem is the fact that my sound card does not want to work no matter what I do.  I have a CreativeLabs X-fi Extreme audio sound card that has worked when I was running XP.  I have scoured the internet for solutions to this problem and have had little luck.  So far, I have switched from alsa to OSS because I read that it would help.  But now, I don't know how to get back (if I really need to).  Please help!  It would be greatly appreciated!

---

### Post by Coreigh on 2009-01-27
RE X-fi card, have you seen these?:
[LIST=1]
[*][http://ubuntu-utah.ubuntuforums.org/showthread.php?t=571656](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=571656)
[*][http://connect.creativelabs.com/opensource/Wiki/SoundCard%20Support.aspx](http://connect.creativelabs.com/opensource/Wiki/SoundCard%20Support.aspx)
[*][http://support.creative.com/kb/ShowArticle.aspx?url=http://203.211.142.198:80/srvs/cgi-bin/webcgi.exe](http://support.creative.com/kb/ShowArticle.aspx?url=http://203.211.142.198:80/srvs/cgi-bin/webcgi.exe)
[*][http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675)
[/LIST]

Regarding the log off, it sounds like the same as hitting Ctrl+Alt+BkSP to kill the GUI. Is it possible you have somehow edited the keymap or created a short cut key accidentally that does this? YOu can see the keyboard short cuts in System >> Preferences >> Keyboard Shortcuts. Or is it possible to create a bash alias that does this?

Anyone else got any ideas?

---

### Post by Squid Spectre on 2009-01-27
I think you might be hitting ctrl+alt+backspace and ending the x session. I've never heard of backspace alone restarting the x server.

To change back to ALSA just go to the Administration (may be Preferences, I'm not near my Ubuntu PC) menu and go to the Sound entry, theres a dropdown there to toggle sound device and sound archetecture.

EDIT:
Coreigh also has a point, check your keyboard aliases.

---

### Post by bicparker on 2009-01-27
For my sound, I tried all four of your suggestions.
1. I went to the end of the thread and they all came to the conclusion that the sound card doesn't work with Hardy.

2. This requires me to download the driver from the link on suggestion #3 

3. The link doesn't work.  (this rules out suggestion #2 and #3)

4. I hit a bump in the road when I punched in 

[SIZE="1"]"make menuconfig"  [/SIZE]

the terminal responded with 

[SIZE="1"]"No rule to make target `menuconfig'.  Stop."[/SIZE]

On the note of the log off thing, I checked my shortcuts and couldn't find one that was responsible.  I'm no expert, but when my computer DOES log off it makes a little error beep so I don't think it's a shortcut it's acting a little more like a glitch.

---

### Post by Squid Spectre on 2009-01-28
Could you elaborate on what you mean by "log off?" Describe what the computer does. Is it a complete reboot, or just kicking you to the login screen for Ubuntu?

---

### Post by bicparker on 2009-01-28
it kicks me back to the login screen.  But on the note of the audio card, I think that it just isn't compatible with hardy heron.  Correct me if I'm wrong.

---

