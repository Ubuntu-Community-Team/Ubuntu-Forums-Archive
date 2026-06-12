---
title: "Updating packages"
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by GSam on 2009-07-21
When I check my Update Manager it says "the package information was last updated 92 days ago". How can I update the package information without doing an upgrade or changing any of the rest of my system? I'm running 8.04 and only have a couple of complaints (like having to click Rhythmbox 2-3 times to get it to open, Just a trifle irritation), otherwise it runs smoothly. I would like to upgrade Rhythmbox (I have 0.11.5), but that seems to be all I can get for 8.04. Maybe if I could update the package information a later version might be available???

---

### Post by mikewhatever on 2009-07-21
While it's not going to bring in newer package versions, you can reload the package information with the following command:

sudo apt-get update

---

### Post by Rocket2DMn on 2009-07-21
In the Update Manager window, you can just click the Check button and it will check for updates (same as running "sudo apt-get update").

---

