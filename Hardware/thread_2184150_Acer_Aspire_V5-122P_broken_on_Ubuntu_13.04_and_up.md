---
title: "Acer Aspire V5-122P broken on Ubuntu 13.04 and up"
date: 2013-10-27
forum: Hardware
---

### Post by degrace on 2013-10-27
I just obtained an Acer Aspire V5-122P and I am trying to install Ubuntu on it. My experience so far:

Knock on wood, but 12.04 LTS work perfectly, and in an expected fashion. Thart was *not *my first choice or first attempt.

13.04 work, sort of. There's a problem with the ATI drivers, but it's fixable. You can get through the installation, but the system fails to boot into Unity on reboot and instead faults to a command prompt. Using the instructions obtained here:

[http://justanyone.blogspot.ca/2013/08/solved-installing-linux-on-acer-aspire.html](http://justanyone.blogspot.ca/2013/08/solved-installing-linux-on-acer-aspire.html)

It was possible to get 13.04 working. But, if you install the available updates, it kills Ububtu. On future reboots it gets through the purple splash screen, goes to a black screen and just freezes. Nothing informative at all appears.

13.10 is worse. It is possible to upgrade from 13.04 to 13.10, but the above issue is then introduced. It is not possible to directly install 13.10. You get the initial option list to installl or boot to live desktop, but whichever option you select, you get the purple splash screen then freeze to black.

I suppose that I can keep going with 12.04 and pray that some future update doesn't screw me, but 12.04 won't be supported forever. This issue is frankly shaking my confidence in Ubuntu. My fear is that if I trust this system, I'm one update away from being frozen out of it. I hate that I can't update to take advantage of new features.

Does anyone have any clue what is going on and if there's a fix?

---

### Post by NoBugs! on 2013-10-27
I don't know if any Acer laptops are Linux certified. I know a good number of Dells are, and Dell even preinstalls it sometimes. You can find certified Ubuntu systems here: [http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/)

I've heard the reverse can be true too - installing Windows on a computer requires tracking all over for drivers and stuff.

---

### Post by degrace on 2013-10-29
OK, well, I solved it but it's not pretty. At least, it's working in what appears to be a normal fashion so far. I really wish I'd been taking notes, but for the benefit of anyone else trying to get this system to work, here's basically what I did:

1. Install version 12.04. This version correctly handles the proprietary ATI graphic drivers needed. Later versions of Ubuntu *do not*. Make sure you *fully* update the distro, and make *sure* you have all available proprietary drivers installed through the update manager before proceeding. The system will automatically detect what's needed and offer them up to you - Ubuntu works much better on this system in the LTS version.
2. Upgrade to 12.10. Everything works, but, you will have no touchpad. A mouse will still work and the touch screen works.
3. Upgrade to 13.04. Now all input devices (keyboard, touchscreen, touchpad, mouse) do not work, but it boot normally otherwise.
4. Get into recovery mode. This is an entertaining exercise. Ubuntu does *not* make this easy. Basically, while booting, even before the Acer splash screen comes up, start rapidly and repeatedly pressing both shift keys. Cross your toes, because your fingers will be busy. It may take a couple of attempts, but you'll get into the GRUB menu, Select recovery move for the later version of the Linux kernel.
5. Go to Network.
6. Once back to the menu, go dpkg. This will install a bunch of missing drivers for input devices.
7. You can do a bunch of apt-get steps from a root shell here if you want to clean stuff up. I did but I think I may have just made things worse. I really think you're done after the dpkg step.
8. Continue to boot into Ubuntu - everything should now be working.
9. Try to get updated. You'll notice if you are now at the same place as me that you're always being hounded for partial upgrades if you try to use the software updated, and these always fail.
10. Try from a terminal:
sudo apt-get install -f
You will see the name of the file that's causing the trouble.
11. See this post:

[http://ubuntuforums.org/showthread.php?t=2172620](http://ubuntuforums.org/showthread.php?t=2172620)

This gives you the answer, although note the path to the file is wrong, it's /var/lib not /var/usr. Edit the file:

sudo nano /var/lib/dpkg/info/xserver-common-lts-raring.postrm

Remove the whole if block containing the dpkg-divert command.

12. Do *sudo apt-get install -f* again, this time you'll have better luck.\
13. Try the software updater again, this time it will say you're up to date but offer to let you upgrade to 13.10.
14. Upgrade to 13.10.

Now you have a working Ubuntu 13.10. Sound, video, network, input devices including touchpad and touchscreen, all working so far, and reboots successfully.

---

