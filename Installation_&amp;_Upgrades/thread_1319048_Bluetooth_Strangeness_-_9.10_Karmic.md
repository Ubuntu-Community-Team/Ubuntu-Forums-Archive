---
title: "Bluetooth Strangeness - 9.10 Karmic"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by TheOldFellow on 2009-11-08
Dongle fitted, worked fine with Jaunty.  Upgrade to Karmic.  Now no Applet, so start applet manually with /usr/bin/bluetooth-applet.  Applet runs but has Red-X.  Right clicl applet, says (Grey) bluetooth on, Turn off Bluetooth. Click Preferences, displays big button 'Turn on Bluetooth', press it, nothing happens.

Now, unplug dongle, replug dongle - everything works!

What have I got wrong?  Some kernel module not being loaded maybe?  udev broken?

I suspect that no-one at Canonical knows diddly about bluetooth, because no forum posts are ever responded to, but hell, we can but try.

R.

---

### Post by zoggerman on 2009-11-29
I have been trying to get a single reply from *anyone* for recommendations of a bluetooth dongle that worked out of the box with no hoop jumping in Karmic. Apparently it doesn't exist.

At least yours sort of works, what are you using?

I think six month carved in stone to the date release cycles are breaking more stuff than they fix. It's a marketing decision not an engineering decision and it is retarded because of that. I wish they skipped long term and six months versions and went to an integrated one year release cycle with a six month beta testing period to fix bugs, insist on that, then just one year back porting security and functionality fixes. That would give people at least two years to run something that worked. What we have now is perpetual alpha ware. I jumped from fedora because it is the same thing there, every release breaks stuff that was working fine, including critical things like sound and video/monitor stuff, I thought ubuntu would be smarter and better because of all the interest, but nope, same junk. I can't see much of any difference using the same gnome desktop.

And ya know what? I would be perfectly willing to pay like ten bucks to have a disk shipped once a year if it wasn't broken, and I bet tens of thousands maybe hundreds of thousands of people would be too. People don't care about paying for software *if it works*.

---

### Post by gdesilva on 2009-11-30
Not sure whether you have the same problem as I did. I had a Dell (Broadcom) bluetooth dongle working in 9.04 but in 9.10 kept getting the message that bluetooth device is not found. Spent weeks trying various things without success until I came across the following post;

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8298037](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8298037)

Thanks to niteshifter, I followed the advice and lo and behold 9.10 found the device.

It appears the problem is at boot time device is set to HID Proxy mode but never gets reset to HCI after boot up. Obviously, a bug with 9.10 but at least this is a reasonable work around.

This solution only works if your bluetooth device is stuck in HID Proxy mode.

Hope this will help someone.

---

