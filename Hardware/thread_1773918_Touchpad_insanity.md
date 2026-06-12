---
title: "Touchpad insanity"
date: 2011-06-02
forum: Hardware
---

### Post by colordrops on 2011-06-02
Hello,

I'm trying to get the Synaptics touchpad working on my HP DV4-3011.  It works in Windows 7, but doesn't work in Ubuntu Natty, even at the log in screen.  It appears that the driver is installed correctly, and the system detects the touchpad, as I see it in GPointing and **System > Preferences > Mouse** settings.  But nothing happens when I try to use it:

root@snagglepuss:~# synclient -m 100
    time     x    y   z f  w  l r u d m     multi  gl gm gr gdx gdy
   0.000     0    0   0 0  0  0 0 0 0 0  00000000

synclient stays like this with no response from the touch pad.

I've searched all the forums, and tried the following solutions, with no luck.  I've tried everything on [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

Here's everything else I've tried:

1.  Make sure the touchpad is enabled (GPointing app, fn-f9, etc).  It appears to be enabled

2. gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true
3. adding SHMConfig options to /usr/share/X11/xorg.conf.d/50-synaptics.conf

4. installing synaptics-dkms from the utouch ppa

5. installing hid-multitouch-dkms from the utouch ppa

6. modifying the module params:
sudo -i
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.conf

I'm at the end of my rope.  Does anyone have any advice?

thank you

---

### Post by belltown on 2011-06-02
> **colordrops said:**
> Hello,

I'm trying to get the Synaptics touchpad working on my HP DV4-3011.  It works in Windows 7, but doesn't work in Ubuntu Natty, even at the log in screen.  It appears that the driver is installed correctly, and the system detects the touchpad, as I see it in GPointing and **System > Preferences > Mouse** settings.  But nothing happens when I try to use it:

root@snagglepuss:~# synclient -m 100
    time     x    y   z f  w  l r u d m     multi  gl gm gr gdx gdy
   0.000     0    0   0 0  0  0 0 0 0 0  00000000

synclient stays like this with no response from the touch pad.

I've searched all the forums, and tried the following solutions, with no luck.  I've tried everything on [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

Here's everything else I've tried:

1.  Make sure the touchpad is enabled (GPointing app, fn-f9, etc).  It appears to be enabled

2. gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true
3. adding SHMConfig options to /usr/share/X11/xorg.conf.d/50-synaptics.conf

4. installing synaptics-dkms from the utouch ppa

5. installing hid-multitouch-dkms from the utouch ppa

6. modifying the module params:
sudo -i
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.conf

I'm at the end of my rope.  Does anyone have any advice?

thank you
What touchpad model, configuration and driver version do you have? Post the output of:

```

grep -im 1 touchpad /var/log/kern.log

```and
```

grep -i touchpad /var/log/Xorg.0.log

```and
```

grep -iA 3 'module synaptics' /var/log/Xorg.0.log

```

---

### Post by colordrops on 2011-06-06
Sorry for the late reply.  I was at a wedding in northwestern China...

So here's the info you requested.

Touchpad model:

```
May 29 21:13:09 snagglepuss kernel: [   21.339726] Synaptics Touchpad, model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400
```

Configuration:

```
[    15.191] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event13)
[    15.191] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    15.191] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    15.192] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    15.192] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    15.332] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5776
[    15.332] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 5012
[    15.332] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    15.332] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    15.332] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    15.464] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    15.464] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    15.496] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    15.496] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    15.496] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    15.496] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.036
[    15.496] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    15.496] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    15.496] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    15.496] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    15.548] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    15.548] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
```

Driver version:

```
[    15.192] (II) Module synaptics: vendor="X.Org Foundation"
[    15.192] 	compiled for 1.10.1, module version = 1.3.99
[    15.192] 	Module class: X.Org XInput Driver
[    15.192] 	ABI class: X.Org XInput driver, version 12.3

```

---

### Post by belltown on 2011-06-07
There are some patches described in this [bug report]("https://bugs.launchpad.net/ubuntu-release-notes/+bug/582809?comments=all") that may fix your touchpad problems. I have a similar touchpad (mine is a synaptics 7.4 clickpad, versus your 7.5 version). I'm also running Ubuntu 11.04 with the synaptics module 1.3.99.

You can follow the instructions in [comment #144]("https://bugs.launchpad.net/ubuntu-release-notes/+bug/582809/comments/144") to build a patched synaptics driver. Alternatively, you might want to try installing a deb file I built to run on an x64-based 11.04 system. Download it from [http://ubuntuone.com/p/w2H/](http://ubuntuone.com/p/w2H/) To install it, go to the folder where you downloaded it and type: sudo dpkg -i synaptics-patch-amd64.deb

I'm not sure if you'll have to undo any of the other steps you've taken so far before installing the patch. I'm fairly sure you'll have to undo step 6, "echo options psmouse proto=exps > /etc/modprobe.d/psmouse.conf" as that has configured the touchpad to work as a psmouse, a solution that others have found very problematic, versus leaving it configured as a synaptics touchpad. You may also need to uninstall the packages you installed in #4 and #5. In my case, I just used the latest Xorg synaptics driver with the patch applied; I didn't need to install any other packages.

---

### Post by colordrops on 2011-06-08
> **belltown said:**
> There are some patches described in this [bug report]("https://bugs.launchpad.net/ubuntu-release-notes/+bug/582809?comments=all") that may fix your touchpad problems. I have a similar touchpad (mine is a synaptics 7.4 clickpad, versus your 7.5 version). I'm also running Ubuntu 11.04 with the synaptics module 1.3.99.

You can follow the instructions in [comment #144]("https://bugs.launchpad.net/ubuntu-release-notes/+bug/582809/comments/144") to build a patched synaptics driver. Alternatively, you might want to try installing a deb file I built to run on an x64-based 11.04 system. Download it from [http://ubuntuone.com/p/w2H/](http://ubuntuone.com/p/w2H/) To install it, go to the folder where you downloaded it and type: sudo dpkg -i synaptics-patch-amd64.deb

I'm not sure if you'll have to undo any of the other steps you've taken so far before installing the patch. I'm fairly sure you'll have to undo step 6, "echo options psmouse proto=exps > /etc/modprobe.d/psmouse.conf" as that has configured the touchpad to work as a psmouse, a solution that others have found very problematic, versus leaving it configured as a synaptics touchpad. You may also need to uninstall the packages you installed in #4 and #5. In my case, I just used the latest Xorg synaptics driver with the patch applied; I didn't need to install any other packages.

Thanks for the tip.

For each of the steps above, I tried them all individually and in combination.  Before trying the patch you've described, I made sure all the changes were reverted.  So I followed the instructions in #190, which is based on #144 as well as other patches.  Also applied the change in #208.  Still nothing.

---

### Post by belltown on 2011-06-09
> **colordrops said:**
> Thanks for the tip.

For each of the steps above, I tried them all individually and in combination.  Before trying the patch you've described, I made sure all the changes were reverted.  So I followed the instructions in #190, which is based on #144 as well as other patches.  Also applied the change in #208.  Still nothing.

So have you deleted /etc/modprobe.d/psmouse.conf ?

And have you purged synaptics-dkms and hid-multitouch-dkms ? Type: dpkg -l | egrep '(synaptics|dkms)' to see if they're still there.

---

### Post by colordrops on 2011-06-09
> **belltown said:**
> So have you deleted /etc/modprobe.d/psmouse.conf ?

And have you purged synaptics-dkms and hid-multitouch-dkms ? Type: dpkg -l | egrep '(synaptics|dkms)' to see if they're still there.

psmouse.conf is indeed gone.  I had uninstalled the two utouch packages, but you guessed correctly that they had not been purged.  I removed the repos from the package manager,  purged the two packages, and rebooted.

The touchpad is still not working.

I really appreciate your help with this!

---

### Post by belltown on 2011-06-09
> **colordrops said:**
> psmouse.conf is indeed gone.  I had uninstalled the two utouch packages, but you guessed correctly that they had not been purged.  I removed the repos from the package manager,  purged the two packages, and rebooted.

The touchpad is still not working.

I really appreciate your help with this!

Sorry it's not working. All I can suggest now is that you try reinstalling the synaptics driver. Before you do that make sure you don't have any non-standard repositories enabled (i.e. just use main, universe, restricted and multiverse). Make sure the only updates you have checked in Synaptics Package Manager are natty-security and natty-upgrades. Make a copy of your /usr/share/X11/xorg.conf.d/50-synaptics.conf file in your home directory.

Then try the following:

```

sudo su
apt-get purge xserver-xorg-input-synaptics
apt-get update
apt-get install xserver-xorg-input-synaptics
reboot

```After you reboot, run a terminal window. Try using your touchpad again. You should at least get some functionality at this point. synclient should show your configured settings. synclient -m won't work until you re-edit the 50-synaptics.conf file to put back the                       Option "SHMConfig" "on" statement.     

If your touchpad is not working at all at this point then I'm at a loss for what to do, other that re-install the OS. If it works but not 100% then you can try the patches I told you about earlier. I suppose it is possible that the your synaptics 7.5 touchpad is not correctly supported by the kernel/Xorg, unlike my 7.4 touchpad, in which case you'd need to raise a bug report through bugs.launchpad.net.

Good luck.

---

### Post by belltown on 2011-06-09
One more thing: Make sure you don't have any other Xorg config files lying around that could get picked up.

```
find / -name '*-synaptics.conf' 2>/dev/null
```The only one you should see, apart from any you have saved in your home directory, for example, is: /usr/share/X11/xorg.conf.d/50-synaptics.conf

You should also make sure you don't have a file named xorg.conf anywhere on your system, or if you do it doesn't contain any touchpad-related directives.

---

### Post by colordrops on 2011-06-13
I verified that there are no additional configuration files as you mentioned.  A couple new things I found:

Adding acpi=off to the kernel params finally got the touchpad to work, but broke half a dozen other things.  I tried 6 or 7 other kernel params to no avail. 

Also, found that dmesg is occasionally reporting errors when I touch the touchpad:

psmouse.c bad data from KBC - timeout

In the end I filed a bug:

[Link: Bug 796469]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/796469")

Thanks for all your advice.

-- Colordrops

---

