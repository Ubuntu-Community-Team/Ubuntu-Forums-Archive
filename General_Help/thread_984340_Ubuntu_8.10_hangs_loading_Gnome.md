---
title: "Ubuntu 8.10 hangs loading Gnome"
date: 2008-11-16
forum: General Help
---

### Post by LDRoamer on 2008-11-16
I had Ubuntu 8.04 running (started out as an installation of Feisty and just did distribution upgrades). I decided that it was time to do a complete reinstall and so I opted to install 8.10. Install seemed to go fine but the system hangs loading Gnome. I get to the log in screen fine but as soon as the user name and password are entered the screen goes black and that is the end of it. No hard disk activity. Left it for a long time and it stayed that way. 

I tried booting the live CD and that also hung loading Gnome.

My machine is an old compaq with 512mb ram,1.9ghz Pentium IV processor and on board intel graphics. It has two hard disks (120 and 200 gb) but I am booting ubuntu from an external usb disk.

Any suggestions would be appreciated.

---

### Post by darcyk on 2008-11-27
Hi,

Any update on this issue? I'm having the exact same problem with a fresh install of 8.10 on a Dell Optiplex GX260: I get past the login screen but then Gnome hangs on the following brown screen (sometimes I'm treated to a black screen too!). I can log in successfully via the console. I thought it might be a problem that an update might fix, but I can't run apt-get from the terminal as I can in the server edition.

Any ideas anyone?

---

### Post by hydratic on 2009-01-01
I have the exact same problem.

I have a dell gx 260. Install goes flawless. It logs in well and halts on loading gnome.

I have checked the logs, something about unable to connect to x server.
I ll post the exact logs tommorow. The machine is somewhere else.

Tommorow i ll use a different graphical card to see if it makes any difference.

I ll keep you posted

Hydratic

---

### Post by drdenim on 2009-01-08
I too am having a similar problem.  I haven't gotten a black screen yet, but when I choose any session other than 'failsafe terminal' it freezes with an empty brown login screen after I enter my password.  I've been having graphics card issues and this started after I removed my graphics card and tried to go back to onboard graphics.

I don't really know if this will help or not, but have you guys tried starting it in a KDE session? (Which now that I think of it, I haven't tried myself...)

EDIT: Okay, it lets me in if I use KDE and it's letting me in with failsafe GNOME now. still not sure how to fix the problem though...

---

