---
title: "X login hangs, no sound, no network, multiple errors"
date: 2008-08-01
forum: General Help
---

### Post by montgoss on 2008-08-01
I can no longer log into X.  I enter my username then password, the password box grays out, but it doesn't load my desktop environment.  It just sits there.  I can still move the mouse.  It also doesn't make the usual drum sound when presenting the login screen.

I can hit Ctrl+Alt+F1 and log in there.  However, I get a screen full of "-bash: /dev/null: permission denied" errors.  If I try to do tab completion while logged in there, it also throws that error.
I killed the existing X and the tried to run "startx".  I get lots of errors about permission denied.  One of the last and one that sticks out was a "permission denied modifying authority file /home/montgoss.Xauthority".  But I see several other permission denied errors.

So, I ran "sudo startx".  This does bring up an X environment.  But it has no sound or networking.  ifconfig does not list an "eth0" device like I'd expect.

I searched the forums and come up with some other things I tried:
xfix = no effect
new user account = hangs just the same as my original
sudo dpkg-reconfigure -phigh xserver-xorg = no effect

The only thing I did in the session before rebooting was watch a DVD and install some updates through the Update Manager.  I don't remember what they were.  They weren't critical (orange circle, not red arrow).  I haven't installed new software or change any settings in the last several days.

What should I try next?  Is there any additional info you'd like?  I did look through dmesg but didn't see any obvious errors.

---

### Post by montgoss on 2008-08-02
Is there anything I can do besides reinstalling?

---

### Post by montgoss on 2008-08-03
I did a "sudo chmod a+rw /dev/null" and that allows me to log in normally.  But I still don't have sound or network.  I don't think it's a permissions thing for the sound and network since logging in as root also didn't have sound or networking.  What could cause those two things to stop functioning?  It's like the drivers for that hardware has been lost...

---

### Post by montgoss on 2008-08-03
If I run the following commands I can at least access these forums:
```
sudo dhclient -r eth0
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0
```

However, Firefox starts in offline mode because Gnome (I guess) isn't detecting the network card.  The networking icon in the "system tray" has a little orange triangle on it and says "No network connection" if you hover over it.  If I right-click on it, "Enable Networking" is already checked.  If I go to "Administration"->"Network Tools", I can see my eth0 device on the devices tab.  But this is only after I did the above commands. It doesn't list an eth0 if I haven't yet run those commands.  If I select eth0 from the drop-down and click the "Configure" button, I get the following error: ```
The interface does not exist
Check that it is correctly typed and that it is correctly supported by your system.
```

Still no luck on the sound front...  Anyone know what is going on with my system?

---

### Post by montgoss on 2008-08-03
Ok, I can get sounds to play after:
```
sudo modprobe snd-hda-intel
```

But all these commands have to be run at startup every time to get things to work.  Why?  Is there a way to make these fixes permanent?

At startup, I must run:```
sudo chmod a+rw /dev/null
sudo dhclient -r eth0
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0
sudo modprobe snd-hda-intel
```

---

