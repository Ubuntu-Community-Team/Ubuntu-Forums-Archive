---
title: "Custom Program Launcher Not Launching"
date: 2008-09-05
forum: General Help
---

### Post by kuloch on 2008-09-05
I created a custom program launcher for the Xfce panel, which launches a bash script I made for firing up the Cisco VPN client when I'm at my university.  The script works just fine when I run it from a terminal.  Here are the script's contents:
```
sudo /etc/init.d/vpnclient_init start
sudo vpnclient connect MUOnCampus
```
However, when I click on it, nothing happens.  Calling '/etc/init.d/vpnclient_init stop' confirms that it wasn't fired up (where manually calling the script does start it).  If I click the "Run in terminal" option for the Launcher, then a Terminal window pops up in the bin folder where the script is located, but the script isn't run.  I can type it in, but that's the purpose of the launcher...

The same happens for the other startup script (for a different profile) and the stop script.  And selecting "Use startup notification" doesn't seem to make any difference.

**EDIT** It's worth mentioning that the VPN client's login process requires agreement to a ToS by hitting 'y' and RETURN.  But that's run after the *_init start, so I don't think it's affecting anything.

Another couple convenience questions:  The VPN client keeps control of the thread on which it's running, which requires hitting CTRL-Z and entering 'bg' if the script was run directly via terminal.  Is there a way to have my script send it to background without needing my input?  Similarly, is there a way (maybe via pipes? I don't remember their details) to have the script provide the 'y' input needed for the ToS agreement?

**EDIT 2**
Apparently the launcher dislikes running scripts that were originally text files but have been 'chmod +x'ed, even if they run fine via terminal.  I added a bash before it (actually, just changed it to gksudo, so that I can make sure everything has root access), and it works great now.  Hopefully the bash man page will be enough to get me through having it automatically respond 'y' to that agreement.

---

