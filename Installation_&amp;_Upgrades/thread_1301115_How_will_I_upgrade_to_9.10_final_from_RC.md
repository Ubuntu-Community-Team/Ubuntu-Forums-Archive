---
title: "How will I upgrade to 9.10 final from RC?"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by BigG123 on 2009-10-25
If I install RC how will I upgrade to the final edition without reinstalling?

---

### Post by mick222 on 2009-10-25
should be no problem if you do a cleam install . If you upgrade from jaunty you won't get ext4 it will keep your ext3 filesystem and grub legacy.

---

### Post by ibutho on 2009-10-25
Use the update manager or "apt-get dist-upgrade".

---

### Post by BigG123 on 2009-10-25
> **ibutho said:**
> Use the update manager or "apt-get dist-upgrade".
Could I do that from 9.04 to 9.10 RC (current)?

---

### Post by mick222 on 2009-10-25
You could but as I said above it is advisable to do a clean install from te live cd as upgrading wont change your filesystem to the new ext4

---

### Post by coffeecat on 2009-10-25
> **BigG123 said:**
> Could I do that from 9.04 to 9.10 RC (current)?

Yes. Open a terminal, and...

```
sudo apt-get update
```Once that's finished, do..

```
sudo update-manager -d
```The update manager will open, but with a "New Distribution Release 9.10 is available" notice with an "Upgrade" button next to it. Click on the upgrade button and follow the prompts. Be warned - it's a hefty download. Mine was about 800MB with not that many extras apps installed. Once you've installed and rebooted, you're in version 9.10 with a slightly updated RC (if you do this today or tomorrow). If you keep it updated, by Thursday you'll have the final version. In fact you'll have the final version by Wednesday, or even a few hours before because of the necessary package freeze before the release of the final ISOs.

Be aware that your root partition filesystem will remain unchanged. If it's ext3 now, it will stay ext3. And legacy grub will stay as legacy grub booting up Karmic. It won't get upgraded to grub2 automatically. Which some might say is a good thing. :wink:

Good luck!

---

### Post by gnuisancev3 on 2009-10-25
I think everyone one here is confused.  If you install the Karmic RC all you'll have to do is keep doing your regular updates and when the "Final" is released, you'll have it.

I installed the RC earlier this week specifically for this reason so i'd be the rush to grab it from the hammered servers.

---

