---
title: "How To Install Radeon HD 6290 proprietary drivers in Ubuntu 15.10"
date: 2016-04-02
forum: Hardware
---

### Post by xalerons1 on 2016-04-02
[COLOR=#111111][FONT=Ubuntu]I have been at this for days now. I have followed every guide I can find, purging and repurging to get a clean start to try to reinstall once more but ultimately nothing has worked. I have tried installing from the package on the website as well as using apt to download fglrx. Every time I try to run fglrxinfo, I get the output of:


[/FONT][/COLOR][INDENT]X Error of failed request: BadValue (integer parameter out of range for operation)
Major opcode of failed request: 155 (GLX)
Minor opcode of failed request: 3 (X_GLXCreateContext)
Value in failed request: 0x0 Serial number of failed request: 17
Current serial number in output stream: 18


[/INDENT]
[COLOR=#111111][FONT=Ubuntu]Whenever I run amdcccle, the output says:
[/FONT][/COLOR][INDENT][COLOR=#111111][FONT=Ubuntu]There was a problem initializing Catalyst Control Center Linux edition. It could be caused by the following: [/FONT][/COLOR]No AMD graphics driver is installed, or the AMD driver is not functioning properly. Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig.[/INDENT]
[COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]Once again, the card is an AMD Radeon HD 6290. I have tried to search pieces of this error with no luck of uncovering anything useful. I try very hard never to post anything to forums that is a duplicate of anything but I haven't found anything around that solves the issue I am having. Thanks.[/FONT][/COLOR]

---

### Post by deadflowr on 2016-04-02
Run a full update using Ubuntu's Software Updater.
Click restart when finished.
Then upon the restart open Ubuntu's program called "Software and Updates"
go to the tab marked Additional Drivers.
Select the fglrx driver and click apply.
Let it install.
When finished you can try to iniailize it with;
```
sudo amdconfig --initial
```
then reboot.
See if that helps.

I think the key is part one, full update.
Maybe, maybe not.

---

### Post by xalerons1 on 2016-04-03
Thank you for the reply. I had software updated throughout the process and although I did try again, I had no luck. I keep getting the same errors and I dont even know how many times I have tried reinstalling at this point doing subtle variations of the process. I feel like possibly it has something to do with a few lines that pop up during the install process via apt-get:

```
...
Setting up fglrx-core (2:15.201-0ubuntu2~15.10.2) ...
update-alternatives: using /usr/lib/fglrx-core/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GFXCORE.conf (x86_64-linux-gnu_gfxcore_conf) in auto mode
...
Setting up fglrx (2:15.201-0ubuntu2~15.10.2) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode

```

The warning tag above has definitely given me some pause for a while and when I tried researching it, I was not able to come up with anything concrete about how to remedy i. I came across apt-get logs where people successfully installed the drivers and the logs still had that warning in them. Im still stuck in this whole process.

---

