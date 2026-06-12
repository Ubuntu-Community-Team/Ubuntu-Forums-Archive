---
title: "Upgrade failed - how to restart?"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by Fatman_UK on 2009-11-03
So far I've done two upgrades from Jaunty, but the second one is causing me stomach ulcers. How do you restart a failed upgrade? 

```
arichardson@vostro-1:~$ sudo do-release-upgrade
Checking for a new ubuntu release
No new release found
```

:x

The upgrade-manager tool doesn't show an upgrade. So it seems I'm stuck somewhere between Jaunty and Karmic. Help!

The failure was in the "installing packages" phase - wine and virtualbox-ose wouldn't upgrade, so I apt-get removed them. If only I could restart the upgrade.

---

### Post by zvacet on 2009-11-03
In synaptic>file tab>history you can see what did you installed if you don't know what is source of your problem.Before upgrade your system heve to be up-to-date.To be sure it is run 

```
sudo apt-get update && sudo apt-get upgrade
```

I'm not on ubuntu right now but in synaptic>preferences or something similar you will find updates window.At the bottom set to normal releases.

---

