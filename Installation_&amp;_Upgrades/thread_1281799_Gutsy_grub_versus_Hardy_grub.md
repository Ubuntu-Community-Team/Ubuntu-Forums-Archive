---
title: "Gutsy grub versus Hardy grub"
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by gmoore777 on 2009-10-03
Does the grub that gets installed in the MBR from Gutsy different
than the grub that gets installed in the MBR from Hardy?

Meaning, would the grub in the MBR have a different set of
files that it will be looking for when it goes to the bootable partition?

Reason I ask is that, I had a Dell laptop. 
Installed Hardy.
Then installed Gutsy. (dual boot)
Then deleted the Gutsy partition.
Then booted up a live Hardy CD, and ran `cfdisk` to make my first partition (Hardy) bootable.
Rebooted.
  "Grub Error 22."

Booted up live Hardy CD, ran:
  sudo grub
  root  (hd0,0)
  setup (hd0,0)
Rebooted. Still got "Grub Error 22."

Booted up live Hardy CD, ran:
  sudo grub
  root  (hd0,0)
  setup (hd0)  <-- slight change
Rebooted and my original HardyHeron rebooted.

So I feel that those 446 some odd bytes that the Gutsy Gibbon
lays down in the MBR isn't good enough (not forward compatible) to load a Hardy partition.

Comments?

---

### Post by presence1960 on 2009-10-03
you installed Gutsy after Hardy so the GRUB on MBR was looking to Gutsy. When you deleted Gutsy's partitions GRUB was looking for non-existant files that you deleted. When you install GRUB it "points" or "hands off" to menu.lst. You deleted that when you removed Gutsy's partitions.

When you restored GRUB you directed it to poiint to hardy's menu.lst

It isn't that Gutsy's or hardy's GRUB isn't good enough to boot the other version of Ubuntu.

Look [here]("http://www.gnu.org/software/grub/manual/grub.html") to learn about GRUB

---

