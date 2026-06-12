---
title: "base-config base-config/package-selection - bug? feature? borked?"
date: 2006-01-11
forum: Installation &amp; Upgrades
---

### Post by Red_Phoenix on 2006-01-11
Hi,

I'm attempting to come up with a 'extremely customised' set of packages, to be installed via a preseed file.

Rather than using the traditional:

base-config  base-config/package-selection      string ~tubuntu-standard|~tubuntu-desktop

I need to specify each and every package to be installed, individually. (Note: All the packages that make up minimal & standard will be included, and about 60% of desktop).

I've tried the following syntax:
string ~tadduser|alsa-base|alsa-utils|anacron|apache2-common ...
string ~t^adduser$|!t^alsa-base$|~t^alsa-utils$|~t^anacron$ ...
string ~n^adduser$|!n^alsa-base$|~n^alsa-utils$|~n^anacron$ ...
string ~n^(adduser|alsa-base|alsa-utils|anacron| ... )$

None of which seem to work correctly.

I do, however, get a few complaints in the /var/log/* files, about packages that cannot be authenticated - does anyone have any idea what is going wrong?

For the moment, I've added a:
base-config base-config/late_command   string apt-get -yu --allow-unauthenticated install adduser alsa-base alsa-utils anacron apache2-common ...
.. which will probably work ok, but it is nowhere near as elegant.

Any help would be appreciated.

Regards,

Leigh.

---

