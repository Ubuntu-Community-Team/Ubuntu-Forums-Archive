---
title: "HP6715b Hardy Survival Tips / Open Issues"
date: 2008-05-04
forum: Hardware
---

### Post by drplix on 2008-05-04
After a year of running Feisty 64-bit on my HP 6715b laptop I took the plunge to update to Hardy 64-bit.  These were my tips/experience installing Feisty last time around...

[http://ubuntuforums.org/showthread.php?t=488406](http://ubuntuforums.org/showthread.php?t=488406)

With these issues dealt with its been very stable. This is my primary work machine so I couldn't face the risk of down time when Gutsy came out so I hedged on updating.

So now to Hardy.  Fingers crossed...

Install
-------
I did a full backup and a clean install with reformat of the disk.  I used the Kubuntu AMD64 Alternate image to install.  System booted after install.

Video
-----
Didn't detect my ATI x1250 GPU.  Video came out in Vesa and at less than the full resolution (1680x1050).  I tried installing ATI fglrx drivers using adept.  I forget exactly what happened but this didn't help.  So I then decided to use the latest ATI drivers using their installer.  This worked. But no go with compiz/3D.  All in all a complete pain just like last time. However after a lot of fiddling I now have full resolution but no desktop 3D.

(This ATI experience is lamentable - it is in dramatic contrast to what I found with a Hardy server I built last week with a NVidia GeForce 7200 GPU.  Installed no problem, display resolution correct, card detected, proprietary drivers detected and easily installed through driver manager.  Compiz 3D effects up and working not a single issue.  Come on ATI get your act together!  I certainly will look to buy a laptop with NVidia GPU next time!)

Network
-------
Built in wired NIC detected and working no problems.

WiFi
----
Chipset is Broadcom BCM4312 - was really hoping this would work now (previously I had to use ndiswrapper and would periodically find the card locked up requiring several reboots to get it out of its weird state).

The b43xx drivers don't work.  So back to ndiswrapper - installed through adept.  Used the HP XP drivers downloaded from their site.  (I know this works as its what I had on Feisty for over a year).  Nothing. Broken.  Aaaagh.  After a lot of time searching around I can't remember how I figured out that there's now a clash between ndiswrapper and ssb. Solution blacklist ssb.  Edit /etc/modprobe.d/blacklist and add a line...

#removed this to make ndiswrapper work
blacklist ssb

(I have no idea what ssb is but its no good with ndiswrapper) WiFi now working.  Seems like this version of ndiswrapper doesn't have the pathological card lock up problem too - so we've moved forward a step in the process.

Firewall
--------
Discovered the new ufw tool with Hardy.  Very nice really easy to set up a proper firewall now.   Here's how to set up a very basic firewall that lets you ssh into the box...

sudo ufw allow proto tcp from any to any port 22
sudo ufw enable
sudo ufw default deny

Still need to see if it will let me redirect ports (eg port 80 to 8080 for my NetKernel application server).

Suspend / Resume  (S To RAM).
----------------
This worked perfectly on Feisty.  Was not expecting any problems.  Wrong.

Suspend works every time. Resume is 'intermittent'.  1 out 3 times resume will come back to a blank screen and there's nothing you can do to get in.  Sometimes you can see that the kernel is alive (caps-lock light toggles etc), sometimes it looks just dead.  Only solution is a hard reset - CTL-ALT-BKSPC doesn't work, nor does CTL-ALT-DEL.

I'd love some help figuring this out - I really really really need suspend- this is a work laptop and I travel to/from home and also often on the road.  Suspend/Resume is a minimum requirement for a laptop OS.

I don't even know how to start diagnosing this one.  Looks like I could start hacking at the /etc/acpi.d/suspend  scripts but where to start?

In the past I've seen shutdown issues with ATI fglrx proprietary drivers but in the last few months these had gone away on Feisty some time ago.  Another pointer may be the USB stack which leads to another fix...

USB breaks on resume (FIX)
--------------------

When resume does work I find that my USB mouse is dead (no light nothing).  Weirdly keyboard works. Anyway here's the fix.  Run this script as root (sudo)...

#!/bin/bash
modprobe -r ohci_hcd
modprobe -r ehci_hcd
modprobe -r hci_usb
modprobe -r usbhid
modprobe usbhid
modprobe hci_usb
modprobe ehci_hcd
modprobe ohci_hcd

All the USB devices start working again.

Other Items
-----------

As I said I installed Kubuntu (I need the power features of KDE for my day job).  However, as I mentioned, I installed a standard Ubuntu AMD64 home media server last week.  It worked great out of the box.  Detected video, detected sound, could have provided a tool to set up RAID but it was pretty painless.  So this made me wonder if all the polish is going into the Gnome distro?

So I thought, I know I'll install Gnome on the 6715b and see if this can give me a more stable hardware management.  No chance. Tried installing gnome with adept.  Get broken package dependencies - there is a legacy package that is no longer shipped in gnome that is marked as a dependent in the Hardy repositories (I forget what it is, something like a key manager or something).  Anyway bottom line the packages are all there but you can't install them because of a metadata bug.  Please someone can you fix this. Having dual gnome/kde environments is a pretty standard use-case.

Compiz 3D
---------
Having seen this working perfectly on my server install it is massively disappointing that the ATI world is letting us down.

I can get 3D effects if I install GLX but it feels horribly slow.  I know the ATI fglrx drivers support AIGLX but the compiz install has fglrx blacklisted.  I haven't had time to hack this stuff.  I can't see why ATI is having such a problem - my 6 year old laptop with NVideo GeForce Go runs compiz super fast on a Suse distro.  This x1250 chipset is up-to-date and runs Vista (spit) Aero with no problems.

All I can say is the contrast in experience between ATI and Nvidia is night (dark dark cloudy stormy night) and day (mostly sunny, intermittent light cloud).

Hope this helps somebody. And if anyone knows how to start solving the suspend/resume all help appreciated.

---

### Post by drplix on 2008-05-04
Forgot something...

Sound
-----

This laptop has the AD1981 audio chipset.  Last time on Feisty I had audio out but no input.  I had to build the Alsa drivers by hand.  Guess what. Same problem.  I was really surprised.  I have no idea what's going on with this pulse audio stuff in Hardy but I decided I'd try the old fix.

Downloaded latest Alsa drivers.  make, make install then use alsaconf which detects the card no problem (note: first get rid of all the sound files in /etc/modprobe.d/  first. alsaconf creates a file '/etc/modprobe.d/sound'). 

Sound is fixed again.

---

### Post by drplix on 2008-05-04
Update:

So I reverted to the non-proprietary drivers.  (Hardware Drivers Manager - uncheck the ATI driver).  Suspend/Resume is working.  I've not tested USB after resume yet.

So the ATI drivers are the problem (who'd have thought it eh?).

So s/r works but now there's another fix/hack needed. When you boot with the default drivers you get a garbage display (looks like frequency wrong or something).  CTL-ALT-BACKSPC to restart X and you're looking at the login.  From then on its ok.

I now have no Open-GL so my plans to use my laptop as a front-end to my shiny new MythTV media server are out the window.  Might try one more go with the latest proprietary using Envy but I don't expect anything since I already did a hand install of the very latest ATI downloaded driver.

Repeat after me. "What do we want basic ATI driver support, when do we want it now."  Let's organize a sit-in at the AMD headquarters.

---

