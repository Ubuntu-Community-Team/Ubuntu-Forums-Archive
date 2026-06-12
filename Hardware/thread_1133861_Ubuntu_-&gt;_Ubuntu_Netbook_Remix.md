---
title: "Ubuntu -&gt; Ubuntu Netbook Remix"
date: 2009-04-23
forum: Hardware
---

### Post by qrwe on 2009-04-23
Hi,

I've installed Ubuntu 8.10 at my Asus EeePC 901. Now when there's a Netbook Remix release available ät 9.04, I would like to upgrade to that Ubuntu branch instead. Is that possible? Is it risky to just switch the repositories?

---

### Post by Tobi-fp on 2009-04-23
You dont have to switch the repositories?
You just do System -> Administration -> update***** (cant remember what its called in english) and at the top of the screen you can update it. Afterwards you can add the repositories for netbook remix

---

### Post by HankB on 2009-04-23
> **qrwe said:**
> Hi,

I've installed Ubuntu 8.10 at my Asus EeePC 901. Now when there's a Netbook Remix release available ät 9.04, I would like to upgrade to that Ubuntu branch instead. Is that possible? Is it risky to just switch the repositories?

There are instructions here [https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR) for installing UNR features on a regular install. If you do the upgrade from what you have, that is what you will need to do to match UNR features.

If you install the UNR flavor of 9.04 over what you have, you have the opportunity to use EXT4 for your root partition (presuming the 4GB SSD) and continue to use your /home (8 or 16GB SSD) as is. Select manual partitioning of the drive to specify what you want. If you decide you don't like the UNR desktop, you can switch back to the standard Gnome desktop.

This morning I installed 9.04 release over 9.04RC on ,y 901, leaving the 16GB SSD alone (and specifing it be used as /home) and reformatting the 4GB SSD for /.

It might be faster to reinstall rather than upgrade.

HTH,
hank

---

