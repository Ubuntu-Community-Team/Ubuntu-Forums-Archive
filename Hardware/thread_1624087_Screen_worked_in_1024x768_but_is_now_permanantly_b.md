---
title: "Screen worked in 1024x768 but is now permanantly black at 800x600"
date: 2010-11-17
forum: Hardware
---

### Post by deadalus.globalnode on 2010-11-17
I have installed ubuntu 10.04 and it was working just fine until I tried to change the resolution. It was running in 1600x1200 by default and it worked great in 1024x768 the few times that I switched to that. 

Then I downloaded and installed Wolfenstein ET. After running the installer successfully as root I went to run it and the screen blanked out while the background music played. I knew that the default resolution for Wolf ET was 800x600 so I switched over into TTY1, did a soft restart. I then logged in and set the monitor res to 800x600 and hit apply. At that point the entire screen went black. I waited for a minute hopping that the screen would "revert" but it didn't, and now I am stuck with windows (which I rarely use, and quite frankly want to get rid of). I wouldn't mind doing a fresh install but I have some code that I have been working on for awhile now and don't want to loose. I also can't retrieve the files via live cd because the home dir is encrypted, and I didn't write down my key. ](*,)

I am hopping that there is something that I can do maybe in the xorg.conf file that will allow me to change the resolution back to a supported one. Also an added bonus would be if anyone knows how to change the default res of Wolf ET that would be great.

Thanks in advance.

Deadalus.globalnode

---

### Post by sikander3786 on 2010-11-17
First of all boot into Recovery Mode, 2nd option on the Grub menu and you'll see an option like reconfigure graphics. Try that and reboot. Does that help?

---

### Post by deadalus.globalnode on 2010-11-17
Thank you for the fast reply.

I do not seem to be able to find that option, the options that I do have are:
[INDENT]- Resume normal boot
- Clean
- dpkg (Repair broken packages)
- failsafeX
- Grub
- netroot 
- root
[/INDENT]
Failsafex is the closest thing that I see, but I don't feel that will help me much. I can get to the login screen, and I do have an alternative wm (e16), but I am more familiar with gnome at the moment.

---

### Post by sikander3786 on 2010-11-17
Hmmm. I don't know if it has been replaced in 10.10... Which version are you using? And which graphics card is it?

Try failsafe mode. It might let you boot to the desktop and you might be able to change resolution there.

If that doesn't help, boot back to recovery mode and select 'root'.

Try this command to reconfigure graphics.

```
dpkg-reconfigure -phigh xserver-xorg
```

Continue boot and see if it worked.

---

### Post by deadalus.globalnode on 2010-11-17
The version of Ubuntu is 10.04, My graphics card is an ati firegl 9000 something or other. The card is horrible quite frankly as I had to literally hack windows to install the windows based graphics drivers. In fact for the most part Linux has supported the card better than windows by a long shot.

I will let you know the results after I try failsafe mode.

once again thanks.

---

### Post by deadalus.globalnode on 2010-11-17
Ok,
I booted into recovery mode, selected failsafeX and it popped up with a dialog box. One of the options was to reconfigure the display, but the only option that worked at all for me was "run in low graphics mode for this session only". when I log in I get a usual 1600x1200 res, but if I restart it doesn't persist. At least I can get my important files off now in case I do end up doing a fresh install.:smile:

---

### Post by sikander3786 on 2010-11-17
Boot into low graphics mode and see if there is an xorg.conf file, backup and delete it by,

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bad
```

```
sudo rm /etc/X11/xorg.conf
```

If it isn't there no problem. Carry on with the next command,

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot.

---

### Post by deadalus.globalnode on 2010-11-17
Great, that fixed it. Thank you for your time. I really appreciate it.

---

