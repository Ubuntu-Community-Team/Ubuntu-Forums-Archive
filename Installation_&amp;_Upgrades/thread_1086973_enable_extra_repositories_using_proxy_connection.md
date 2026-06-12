---
title: "enable extra repositories using proxy connection"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by sramanujam on 2009-03-04
i've installed ubuntu 8.10 in x86_64 based system using live cd which contains only the operating system, but no softwares preinstalled with it. i followed the tutorial [http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php) to enable extra repositories, however since my computer is behind a proxy which needs authorization, i couldn't complete the first step of adding third party software source. every time i try, i'm getting an error which says 

[I]"Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct."[/I]


how to go about with this problem so that i can download the missing softwares?

i've actually set the proxy, port, username and password in System-Preferences-Network proxy. still it doesn't work :(

jam, india.

---

### Post by DarkFire82_L33T on 2009-10-05
Ran the same thing, on Karmic. Heres my process and results:

Software Sources > Other Software tab > Add button > Imput "[SIZE=2][COLOR=Red]deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) *jaunty* free non-free[/COLOR][/SIZE]" without quotes > replaced "[SIZE=2][COLOR=Red]jaunty[/COLOR][/SIZE]" with "[SIZE=2][COLOR=Red]karmic[/COLOR][/SIZE]" > Add Source button > Close button > Reload button.

Resulted in an error saying:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

---

