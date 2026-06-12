---
title: "Firefox 1.5"
date: 2005-11-08
forum: General Help
---

### Post by canadianwriterman on 2005-11-08
Does anyone know if Firefox 1.5 has been packaged for installation as an upgrade of 1.0.7 in Ubuntu, yet?

---

### Post by 23meg on 2005-11-08
Since it's a new version, not a security update, it won't be packaged; Ubuntu does not provide feature updates after releases to increase stability. You can easily set up 1.5 using this guide: [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by jrib on 2005-11-08
[QUOTE=23meg]Since it's a new version, not a security update...[/QUOTE]

The release notes for RC1 do note "Many security enhancements."  I hope that it does get packaged.  Right now I have to keep 1.0.7 in synaptic, even though I only use 1.5,  because other programs depend on firefox 1.0.7 (like yelp and epiphany).

---

### Post by 23meg on 2005-11-08
It won't get packaged. Instead, all security fixes that were introduced between the 1.0.7 and 1.5 will be made available as security updates to 1.0.7 *when 1.5 is officially out.*

---

### Post by SickTwist on 2005-11-08
[QUOTE=23meg]It won't get packaged. Instead, all security fixes that were introduced between the 1.0.7 and 1.5 will be made available as security updates to 1.0.7 *when 1.5 is officially out.*[/QUOTE]

To add to what 23meg said, it *might* be included in the backports repo if that ever gets up and running for Breezy. However, I'm not sure if backports is officially supported (meaning it will receive security updates). Could anyone clarify?

---

### Post by 23meg on 2005-11-08
Hoary Backports did become official; I'm not sure what the case will be with Breezy, but either way it will be an extra that isn't in the mainline distribution.

---

