---
title: "Bluetooth keyboard and mouse work best with bluetooth disabled?"
date: 2008-01-21
forum: Hardware &amp; Laptops
---

### Post by Curtisc on 2008-01-21
I got an MX5000 bluetooth keyboard and mouse a few weeks ago.  I plugged it in, and it worked without any issues (although I did have to do some xbindkeys configuration to get all the mouse buttons to work).  Anyway, I just reinstalled Gutsy, and all of a sudden my keyboard and mouse are behaving terribly!  I can't use them at the login screen without disconnecting and reconnecting the dongle, the mouse jitters all over the place, etc.  

Anyway, I realized that before I got the bluetooth combo, I had actually disabled bluetooth services, since I didn't have any use for them.  Then, when I started using bluetooth, I forgot to reenable them.  My question now is what advantage is there to using the bluetooth services if it works without them?

---

### Post by Ravensix on 2008-01-22
i have the same keyboard and mouse but mine does not work.  How do you disable the bluetooth?

---

### Post by Curtisc on 2008-01-23
I think I've answered my own question, but first I'll answer yours...

You can disable bluetooth by going to System > Preferences > Sessions and System > Administration > Services, then unchecking the bluetooth options.  That should prevent bluetooth services from running, which will put the MX5000 combo into legacy mode (the one that lets you use the keyboard in the BIOS).

However, to answer my own question (just figured it out!) - I was having trouble before following the directions in [http://ubuntuforums.org/showthread.php?t=97936](http://ubuntuforums.org/showthread.php?t=97936).  When I tried to change the mouse settings, my keyboard keymap went all over the place, I think because there was only one device ID/controller for both devices.  However, after actually using bluetooth mode (following the tutorial at [http://ubuntuforums.org/showthread.php?t=227057](http://ubuntuforums.org/showthread.php?t=227057)), I found that I could make my many-buttoned mouse function properly.  In fact, my keyboard and mouse are now working better than they do in Windows (less dropouts).

To sum up, if you have bluetooth enabled, you need to do a bit of work to get everything working, but you get a 12-button mouse and a keyboard with fancy keys.  If you disable bluetooth, you get a 3-button mouse and a plain keyboard, but they work without having to do anything.

---

### Post by wasmuthk on 2008-03-01
Thank you, Thank you, Thank you. I have a Logitech MX5000 Keyboard and Mouse and was forced into unplgging the Bluetooth dongle everytime I used my KVM switch. After turning off Bluetooth, it works just fine. 

NOTE: for anyone using a more recent version of Ubuntu, you turn off Bluetooth by choosing System -> Administration -> Services and then uncheck Bluetooth.

---

### Post by sj26 on 2008-03-07
I got mine working (at start-up) while retaining all bluetooth functionality.

Make sure bluetooth services are starting on system start-up. (System -> Administration -> Services, Tick "Bluetooth")

Using a plugged-in keyboard:
```
sudo /etc/init.d/bluetooth start
```
Try and pair your device (hit connect) and while it displays "Connecting..." use:
```
hidd --search
```
To find the address which looks like [FONT="monospace"]12:34:56:78:9A:BC[/FONT] **(1)**. It should also connect the device.

Edit [FONT="monospace"]/etc/default/bluetooth[/FONT]:
[LIST][*]Change [FONT="monospace"]ENABLE_HIDD="0"[/FONT] to [FONT="monospace"]ENABLE_HIDD="1"[/FONT]
[*]To the end of [FONT="monospace"]HIDD_OPTIONS="..."[/FONT], before the end quote ("), add [FONT="monospace"] --connect CODE[/FONT] for every code you identified above **(1)** making sure you have a space before and after each one.[/LIST]

There is probably a more correct and elegant solution, but this works for me.

---

