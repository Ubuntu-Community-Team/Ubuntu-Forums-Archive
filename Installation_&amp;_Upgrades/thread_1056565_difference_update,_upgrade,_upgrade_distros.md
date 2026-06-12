---
title: "difference update, upgrade, upgrade distros"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by uk2 on 2009-01-31
Hello

I am just wondering what the difference is between them.

When I want to do a update I do this:
sudo apt-get update
Does this download all the latest updates.

And then
sudo apt-get upgrade
Does this install all the updates that have been downloaded.

And this:
sudo apt-get upgrade distros
Does this update to the next available version. For example. I currently have 8.04.2. So I will upgrade to 8.04.3

Many thanks,

---

### Post by Partyboi2 on 2009-01-31
Hi,
You can read more about  apt by checking  out the man pages which can be done by typing
```
man apt-get
``` in a terminal.

>  update
           update is used to resynchronize the package index files from their
           sources. The indexes of available packages are fetched from the
           location(s) specified in /etc/apt/sources.list. For example, when
           using a Debian archive, this command retrieves and scans the
           Packages.gz files, so that information about new and updated
           packages is available. An update should always be performed before
           an upgrade or dist-upgrade. Please be aware that the overall
           progress meter will be incorrect as the size of the package files
           cannot be known in advance.
>  upgrade
           upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new
           versions available are retrieved and upgraded; under no
           circumstances are currently installed packages removed, or packages
           not already installed retrieved and installed. New versions of
           currently installed packages that cannot be upgraded without
           changing the install status of another package will be left at
           their current version. An update must be performed first so that
           apt-get knows that new versions of packages are available.
>   dist-upgrade
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. The
           /etc/apt/sources.list file contains a list of locations from which
           to retrieve desired package files. See also apt_preferences(5) for
           a mechanism for overriding the general settings for individual
           packages.



---

