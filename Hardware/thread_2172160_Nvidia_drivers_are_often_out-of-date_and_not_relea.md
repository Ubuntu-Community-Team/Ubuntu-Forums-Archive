---
title: "Nvidia drivers are often out-of-date and not released fast enough..."
date: 2013-09-03
forum: Hardware
---

### Post by agrestringere on 2013-09-03
[FONT=arial]Background: coming from Windows 7 and XP I'm used to my Nvidia drivers being in sync with the official Nvidia release cycle and always having extremely fresh drivers available. However with Ubuntu it seems that new upstream Nvidia releases are delayed for way too long before being released to the main repositories.  Nvidia Ubuntu drivers should always be at the most recent version officially endorsed by Nvidia themselves as STABLE. This affects the quality of the experience I have with Nvidia on Ubuntu because newer drivers mean greater performance/stability, new features and added support for new Nvidia cards.  Ubuntu needs to embrace a rapid-release cycle where new drivers are quickly put into production and release it to the main repository where all Ubuntu can update to it especially for LTS users.[/FONT][SIZE=3][FONT=arial][SIZE=2]

Just filed a bug Bug #1219908 [[goo.gl/cjtw8N]("http://goo.gl/cjtw8N")] about my frustration with the slow-release cycle of the Nvidia drivers in the main Ubuntu repositories and it got upgraded to Wishlist.  If this problem affects you too you can log into [www.launchpad.net]("http://www.launchpad.net/") and click the “this affects me too” button the bug report and let the package maintainers know that you would like a faster release cycle so you can have access to fresh drivers in sync with official Nvidia releases.
[/SIZE][/FONT][FONT=arial][SIZE=2]
Nvidia Official Linux Drivers List [[goo.gl/sXQvOh]("http://goo.gl/sXQvOh")]
My Launchpad.net Bug #1219908 [[goo.gl/cjtw8N]("http://goo.gl/cjtw8N")] [/SIZE][/FONT][/SIZE]

---

### Post by Yellow Pasque on 2013-09-03
Well, Ubuntu's not a rolling release. For non-LTS releases, they generally test the most recent version in the testing phase, and once the release date passes, that's it. Most people are happy with that, and if not, they use xorg-edgers or another distro. Maybe a rolling release would be more appropriate for you. I'm using Debian sid(uction) and nvidia 325.15 right now ;)

---

### Post by CatKiller on 2013-09-04
Take it up with Nvidia. The nouveau drivers are always up to date.

---

### Post by monkeybrain20122 on 2013-09-04
Get the up to date driver from xorg-edgers 
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

BTW, I don't believe you get up to date driver automatically from Windows, you have to update manually by downloading the driver from Nvidia. You can also do that in Ubuntu or any Linux, though it is complicated. So use xorg-edgers, install the driver and disable the repository (since you don't want the frequent updates for other things) and re-enable it when you need the next update.

---

### Post by monkeybrain20122 on 2013-09-04
> **CatKiller said:**
> Take it up with Nvidia. The nouveau drivers are always up to date.

Well not really, nouveau that comes with Ubuntu is pretty old as well, it  will be up to date if you get it from xorg-edgers. And the Nvidia driver in the repo not being up to date has nothing to do with Nvidia, It releases its Linux and Windows drivers at the same time. it is Ubuntu's packaging policy. In other distros like Arch or Fedora you will get the update driver, or you can download from Nvidia.

---

### Post by agrestringere on 2013-09-05
monkeybrain20122: 

The problem is that x-org-edgers contains other bleeding edge packages like 'xorg' and many others straight from git repos that may cause stability problems. Running the official BETA Nvidia driver - like the 325.15 - alone on a stable system is better and I haven't had problems with that.  The problem is that the actual real STABLE driver from Nvidia is 319.49 right now which I would prefer to use on a production system.  Currently on Ubuntu 12.04 the STABLE driver is 304.88, it's deprecated and out of date.  Even the official Nvidia LEGACY driver is at 304.108, unbelievably it's farther ahead.  By now all Nvidia users should be on the STABLE 319.49 version, regardless of Ubuntu version, whether 12.04 through 13.04 and 13.10.  There's no real good reason to hold drivers back that long if Nvidia themselves have certified and recommended the 319.49 driver as STABLE for use in Linux systems.

The immediate problem presented by this is that it's going to take up to month if not longer for Ubuntu to get the 319.49 packaged, tested and released and by that time Nvidia will already nominate a future driver like the 325 release as the STABLE official release and we will still be far behind the curve. Users who are having problems that are fixed by the newer STABLE Nvidia releases will have to wait a month with a broken or poorly performing system.  People who use multiple monitors and those with new cards that are not well supported by the current Ubuntu drivers are also going to have a poor experience with the Ubuntu distribution. Those worst affected are those who have hybrid graphics "Optimus" and they'll have to wait longer to get newer versions that have improved support for that.  System downtime for even a few days is serious.  For businesses downtime means money down the drain. 

Then there's the number of drivers currently available in the Nvidia repositories.  There are nvidia-304, nvidia-310, nvidia-313 and so forth. Why so many different versions of drivers that are all deprecated and out of date?  We only need a nvidia-stable, nvidia-beta and nvidia-legacy driver that mirrors the current official Nvidia releases.  If those drivers were available to all versions of Ubuntu we wouldn't need so many PPA's or workarounds to obtain them.  Those PPA's aren't well maintained and none of them are in sync with the Nvidia release schedule and many are incomplete. 

The actual driver versions should be like this right now for 12.04, 12.10, 13.04 and 13.10:
+ nvidia-stable: 319.49
+ nvidia-beta: 325.15
+ nvidia-legacy: 310.108

Simple right?

Ubuntu needs to change it's packaging policies regarding Nvidia drivers, it's really frustrating.

tl;dr - There's no real good reason to hold drivers back that long if Nvidia themselves have certified and recommended their own drivers as STABLE, BETA and LEGACY for use in Linux systems.

---

### Post by Linuxisfast on 2013-09-06
If you install post-release updates then you get the latest stable long term from Nvidia. Ubuntu 12.04.3 latest installs Optimus support right out of the box with nvidia prime on hybrid laptops. If you want latest drivers, there is always xorg-edgers ppa. Btw, if you go to the nvidia dev forum, you will see that even with their long term drivers there are issues so Canonical is doing right in being conservative in this regard. No one wishes to boot up to a blank screen after installing new drivers.

---

