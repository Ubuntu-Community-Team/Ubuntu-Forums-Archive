---
title: "Hardy -&gt; Jaunty upgrade survival story"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by juise- on 2009-04-29
I encountered some problems upgrading from Hardy to Jaunty, but finally got everything working, so I thought I'd share my story here. It's been a few days already, so I might not remember all the details accurately anymore.

The start was a smooth, I just started the upgrade from adept manager, and let it finish downloading overnight.

The upgrade finishes, and reboots into kdm prompt. When I log in, I get the KDE4 desktop with a twist: The windows I manage to open won't have any edges on them, and I seem to be unable to move or close them. Seems like a window manager problem. I've encountered these things before doing ubuntu upgrades, usually they're because some needed packages actually won't get installed (was the case here also).

I get a shell, and try 'apt-get update'. The response is that some of the packages have not been installed correctly, and I should run dpkg-reconfigure on them. As it's been a while since I have looked at the configuration of my system, I just decide to do 'dpkg-reconfigure -a' (which turns out to be a mistake). I go through the configuration for all the packages. After that I decide to try if my X desktop has gotten any better, and do '/etc/init.d/kdm restart'.

Now the problems start. X starts up in 'low resolution mode', and I'm greeted with an error about missing freetype library. Neither my mouse nor keyboard is responding, so the option I have left is to reboot.

Unfortunately, after rebooting I get back to exact same situation. I figure I should go and edit my xorg.conf to remove the freetype library loading, but I have no way to escape the X nag screen. I reboot again, and boot to single user mode, only to find out that I'm not able to use the menu (I later found out why: [http://ubuntuforums.org/showthread.php?t=1135146]("http://ubuntuforums.org/showthread.php?t=1135146")). So I'm off to boot from a [CD]("http://www.sysresccd.org/") to fix my xorg.conf and then try again.

After removing the freetype library from the xorg.conf I try booting Jaunty again. This time I get an X nag screen about that it's unable to find the input devices. (I think this was the real problem all the time, and the error screen tool just picked up the freetype error because it was first error in the logs). As before, I'm stuck as X eats all my input and doesn't let me to go to console with the usual Ctrl-Alt-F1. I figure it's easier to try to solve this inside Jaunty, so I boot up from the CD again and stop kdm from starting on runlevel 2 by renaming the symlink in '/etc/rc2.d'. Then I reboot Jaunty.

Now I finally get a login prompt at console. I immediately notice something wrong after login: When I try to use autocomplete I get a load of '/dev/null: permission denied' messages. After a few moments of wondering, an educated guess points the problem to udev configuration. It turns out that in '/etc/udev/rules.d' there is a rule file '40-permissions.rules.dpkg-old', but nothing that would be replacing it. Quick look inside the file makes me confident that this file should still be part of the configuration, so I think that dpkg has somehow gotten it wrong. I try 'dpkg-reconfigure udev' and 'apt-get --reinstall install udev' in different orders. I find out that dpkg-reconfigure actually breaks some udev-related stuff (I get complaints about missing 'udevadm' during post-configuration when a new initramfs is generated after dpkg-reconfigure, and sure enough, there is no such executable on my system. apt-get --reinstall fixes that missing executable). Neither of the commands actually substitute anything for the now-missing permissions.rules file, so I just rename that not to include the dpkg-old - suffix and do '/etc/init.d/udev restart'.

Now when I start X again with '/etc/init.d/kdm start' and I find myself back where I started from. X works, but the KDE desktop is broken. But at least I now have the apt working. I try 'apt-get install kde'. Whoa, there's a whole lot of packages missing, including some important-looking (ahem, kde-core). No wonder it didn't work.

After the install is complete, I enable the kdm in rc2 start scripts again and reboot. And what do you know, everything seems to work.

As a conclusion, it took me about one work day to solve the problems caused by the upgrade, and I consider myself quite experienced Linux user. Based on my experiences and problems I run into, I cannot recommend taking this upgrade path unless you're feeling confident with your Ubuntu skills.


If you happen to know how I could have avoided going through all this trouble (except for clean install, I didn't want to do that), please comment. I'll be smarter next time. ;-)

---

