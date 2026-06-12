---
title: "Very strange ACPI problems with Toshiba Satellite 1135-S155"
date: 2009-03-03
forum: Hardware
---

### Post by chris_acheson on 2009-03-03
I have a Toshiba Satellite 1135-S155 that has run several versions of Kubuntu (started with 7.04, currently has 8.04).  It has always had this weird problem where it will shut off randomly while I'm using it.  For a while I thought it was overheating, but after an accidental discovery and some further experimentation, I determined that it was actually a power problem.

The battery is old and worn out, so it's typically fully discharged when I start the machine up.  While the battery charges, everything is fine.  Once it finishes charging, it'll run for a little while longer (from a few seconds to a minute or so) and then shut off without warning.  If I disconnect the AC adapter before it finishes charging, it can run off of battery power until that runs out.  If I reconnect the AC before the juice is gone, it can run until it's fully charged again.  It can run indefinitely like this, as long as I disconnect and reconnect the AC at the right times.

If I remove the battery and run straight off the AC, the machine will shut off very quickly, typically before reaching the KDM login screen.  On a friend's suggestion, I tried entering the BIOS setup and letting it run for a while -- no shutoff problems.  It also seems to run just fine if I let it sit at the LUKS passphrase prompt (I set up full disk encryption through the alternate installer).

I tried playing with boot parameters: "acpi=off" has no effect when booting normally, but allows recovery mode to run just fine.  On the other hand, booting in recovery mode with "noacpi" or "pci=noacpi" seems to make it shut off even sooner, before I'm able to type my encryption passphrase (or sometimes before reaching the prompt).

Any ideas on how to narrow this problem down further?  Is there some sort of daemon that might be overriding the "acpi=off" parameter?

---

