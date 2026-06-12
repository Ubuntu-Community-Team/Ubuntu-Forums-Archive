---
title: "Reversing distro updates?"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by phobophilia on 2009-01-04
Pardon my inexperience, but I need help.

8.10 and my computer do not play well together. I walk on eggshells; adjusting screen brightness freezes it. Clicking on menus freezes it. Being on it for more than 30 minutes renders the keyboard input useless. By upgrading the distro version, I've turned a reasonably functional computer into a (metaphorically) slumping, half-paralyzed stroke victim. 

This has happened before- I've tried upgrading from 8.04 twice before, with the same results. Not knowing how to fix it, I wipe the partition and reinstall 8.04 from a disc. I'd like to not do that anymore.

Is there any function/terminal command to revert the system to 8.04?
Many thanks, P.

---

### Post by pytheas22 on 2009-01-04
I don't know of any way to reverse a dist-upgrade over the Internet, but if you burn an Ubuntu 8.04 [alternate CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") and boot to it, you'd have a dist-upgrade option.  I'm not positive, but if you tell it to 'upgrade' your 8.10 system, it should turn it back into an 8.04 system, barring any weird problems.

It might also work to edit your /etc/apt/sources.list file so that you replace the 8.10 repositories with those for 8.04, then run 'sudo apt-get update; sudo apt-get upgrade'.  But this would probably be a messier solution and I doubt it would actually succeed, although in principle it would.

---

