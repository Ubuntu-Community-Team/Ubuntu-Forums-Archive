---
title: "Designating laptop as desktop monitor"
date: 2013-07-13
forum: Hardware
---

### Post by eamonster on 2013-07-13
I searched the forums (and internet) for awhile and didn't see anything that would cover my question.  I have a really nice desktop that I current run Ubuntu 13.04 on but I never seem to use it because I prefer using a laptop.  I currently have a MacBook Pro running OSX and would like to keep it on there BUT I would like to use the laptop of a monitor for my desktop as well.  Is there something that I can do where I can switch from using the OS on my laptop and when I want to use linux, be able to switch to using my laptop as the designated keyboard/monitor for my desktop?  Maybe some sort of boot-up option.  I also don't want to have to have a cord hooked up from my laptop to my desktop.  So, wireless would be preferred.  

If this is not possible, I did manage to see that there were people on the forums that were trying out wireless monitors but that was over a year ago.  If anyone has had luck with these then this would be a nice option to be able to use it in another room if need be.  

Thanks!

---

### Post by Cheesehead on 2013-07-13
Using a direct physical connection (null-modem cable), you can use a laptop as a text-only console. Your laptop's hardware is simply not configured to export your keyboard and monitor to another system in that way.

Instead, use ssh to login remotely to the desktop.
See [https://help.ubuntu.com/community/AppleRemoteDesktop](https://help.ubuntu.com/community/AppleRemoteDesktop) for one good way to set up the Mac and the Laptop.

---

### Post by eamonster on 2013-07-13
> **Cheesehead said:**
> Using a direct physical connection (null-modem cable), you can use a laptop as a text-only console. Your laptop's hardware is simply not configured to export your keyboard and monitor to another system in that way.

Instead, use ssh to login remotely to the desktop.
See [https://help.ubuntu.com/community/AppleRemoteDesktop](https://help.ubuntu.com/community/AppleRemoteDesktop) for one good way to set up the Mac and the Laptop.


Thank you for the reply but wouldn't that do exactly the opposite of what I want?  I would like the laptop to show my desktop not have my desktop now have my macbooks desktop.

---

### Post by Cheesehead on 2013-07-14
You're right. Look at SSH with X-forwarding.
One good set of instructions for an OSX laptop is at [http://narnia.cs.ttu.edu/drupal/node/132](http://narnia.cs.ttu.edu/drupal/node/132)

---

