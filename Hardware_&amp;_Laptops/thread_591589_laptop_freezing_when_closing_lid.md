---
title: "laptop freezing when closing lid"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by invictus on 2007-10-25
Hi

After installing gutsy I got a problem with my laptop: Every time I close the lid, the computer freezes and the only way to get it to react again is to use the shutdown button. The screen goes black (but not off) and the cursor freezes on top of this black screen.

I know for sure I didnt have this problem with earlier releases.

I have a Dell inspiron 510m.

---

### Post by pelo8280 on 2007-10-25
I have a similar problem.  My screen randomly goes blank after shutting the lid while running gutsy.  The screen goes completely off.  I believe X Windows is crashing, because some other times I get sent back to the logon screen (X Windows restarts).

I have a compaq c306us.

---

### Post by invictus on 2007-10-28
What I am most interested in is why it worked in previous releases and not this one? Should I hold my breath waiting for an update in gutsy or should I just use feisty/windows?

---

### Post by pelo8280 on 2007-10-28
> **invictus said:**
> What I am most interested in is why it worked in previous releases and not this one? Should I hold my breath waiting for an update in gutsy or should I just use feisty/windows?

It has been reported as a bug: [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/44393](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/44393)

The fix will come eventually, but we just might have to wait for 8.04. :(

---

### Post by cow_racer on 2007-10-28
I think when you close the lid, the laptop goes into suspend mode.  And if your latop is like mine with ati video card and using the fglrx driver, it will get stuck.

---

### Post by pelo8280 on 2007-10-28
I set my laptop to blank the screen when I shut the lid, and it certainly does blank the screen - but x windows crashes on a purely selective basis.  Sometimes it does, sometimes it doesn't.

BTW, my laptop has intel graphics, and When I go into standby, I can't resume.  I get a black screen with "[FONT="Fixedsys"]      LINU[/FONT]" in yellow at the top (yes, it is missing the x)

---

### Post by invictus on 2007-10-29
I too have intel GMA and not ATI/Nvidia.

However, I get this problem whenever I close the lid. It is not dependent on being at the login screen.

---

### Post by mysurface on 2007-10-29
> **pelo8280 said:**
> It has been reported as a bug: [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/44393](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/44393)

The fix will come eventually, but we just might have to wait for 8.04. :(

No way, that is too long to wait!

7.04 have no such problems!

---

### Post by mysurface on 2007-10-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bug/135181](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bug/135181) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **invictus said:**
> Hi

After installing gutsy I got a problem with my laptop: Every time I close the lid, the computer freezes and the only way to get it to react again is to use the shutdown button. The screen goes black (but not off) and the cursor freezes on top of this black screen.

I know for sure I didnt have this problem with earlier releases.

I have a Dell inspiron 510m.

Finally I found a so call solution to solve this critical *** crash! freeze! hang! blank screen! or whatever you called. You can't press ctrl-alt-F1, it will crash! You can't  ctrl-alt-backspace, sometimes it goes blank screen. You can't close your lid, else it freeze! 

The cause of problem is the intel video driver is not suitable for Dell inspiron 510m, I donno why, it just don't cope well. So, lets change it to older driver, i810

```
sudo gedit /etc/X11/xorg.org
```

search the word 'intel' and replace it will i810. Ya make sure you have install that i810 driver.
```
dpkg -l | grep i810
```

xorg.conf will looks like below, after modified.
```
Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

```

Did anyone mention about bullet proof X?
[http://arstechnica.com/journals/linux.ars/2007/08/29/ubuntu-xorg-maintainer-demonstrates-bulletproof-x](http://arstechnica.com/journals/linux.ars/2007/08/29/ubuntu-xorg-maintainer-demonstrates-bulletproof-x)

I doubt will it still works after you downgrades the driver to i810, if you guys dare to try, please let us knows the result.

> xserver-xorg-video-intel is going to supersede xserver-xorg-video-i810 very soon.
by Alex Muntada

---

### Post by Paul Dufresne on 2007-11-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/65027](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/65027) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Are you all using AMD64 ?
You should subscribe to bug #44393 and bug #65027 if you have a Launchpad account.
Here the links:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/65027](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/65027)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/44393](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/44393)

---

### Post by pelo8280 on 2007-12-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/152200](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/152200) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I found my problem.  X server crashes when totem is running.  It's only totem, not xine because Amarok is fine.  Oh well.

---

### Post by baxterdog on 2007-12-02
I had a similar problem when plugged into a switched outlet that was off. Didn't have the power settings properly configured. The laptop wouldn't turn back on until I plugged into a powered outlet and let the battery charge. Just plugging into a powered outlet right away didn't work until the battery was charged. Then I was able to boot up and change the power settings. Haven't had problems since.

---

### Post by baxterdog on 2007-12-02
Have done some more tests and sure enough the power settings are very important in whether or not a laptop acts up with the lid closing. Make sure that the setting for laptop lid closing is not set to hibernate or shutdown. I have it set to blank screen and I can remove from AC power, wait, bring back up with just battery (or AC) and it works fine.

Using an Acer travelmate 2480 from newegg.

---

### Post by pelo8280 on 2007-12-02
My laptop is set to "Do Nothing" when the lid is closed on AC Power and "Blank Screen" on battery power.  It's either an issue with xserver or totem.  I'm on an intel 945 graphics card using the Experimental Modesetting driver.  What is everybody else using?

---

### Post by josteinaj on 2008-03-19
Thanks a lot mysurface! :)

I got it working now. I also had a similar problem when running wings3d and ctrl+alt+shift moving it from one desktop to another. A lot of vertical color lines appeared with the cursor on top, as it freezed just like earlier with the black screen + cursor and lid closing. I tried the same with glxgears and the same thing happened.

After applying your fix mysurface, what happened when I ctrl+alt+shift moved the glxgears window between desktops was that gnome(?) shut down and I was returned to the login screen. After disabling compiz it's working fine.

(using a Dell Inspiron 510m and Ubuntu 7.10 Gutsy Gibbon)

---

### Post by bzzzzz on 2008-03-26
I am using a dell d505 latitude.  I have feisty fawn installed using wubi.

when i close the computer turns to a black screen and a white mouse pointer.  It is impossible to move the white mouse pointer and I have yet to discover any key that will wake the machine and so resort to pressing the off button for several seconds.

I have only just replaced my i810 driver with the intel driver as I used to have my screen vertically displaced by an inch and so was unable to see the whole screen.  However with this new driver things seem to be working better, but I just can't close the lid.

---

### Post by crawall on 2008-05-11
> **invictus said:**
> Hi

After installing gutsy I got a problem with my laptop: Every time I close the lid, the computer freezes and the only way to get it to react again is to use the shutdown button. The screen goes black (but not off) and the cursor freezes on top of this black screen.

I know for sure I didnt have this problem with earlier releases.

I have a Dell inspiron 510m.
The same issue with my Dell Latitude D505.
I've tried  - Option "ForceEnablePipeA" "true" and other suggestions but none of all are working. Waiting for Hardy doesn't change anything since i've already installed it and my laptop doesn't respond any different.
I keep trying your suggestions and stay hopefull to find a solution

---

