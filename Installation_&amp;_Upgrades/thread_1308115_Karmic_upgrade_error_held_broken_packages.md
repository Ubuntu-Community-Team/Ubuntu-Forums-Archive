---
title: "Karmic upgrade error held broken packages"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by ENOTTY on 2009-10-31
Hi, I am trying to upgrade from Januty to Karmic using the alternate install ISO, but I get this error "E:Unable to correct problems, you have held broken packages."

I checked Synaptic and there's nothing pinned. I had gears and unison-gtk installed from .debs, but I removed them. Error still occurs.

I ran "Fix broken packages" in Synaptic. It found nothing to fix. Then I removed all my .list files that referenced non-official Ubuntu repositories, and then ran apt-get update and apt-get upgrade. Nothing was installed or removed. Same error occurs.

I do have a lot of packages installed from PPAs, like chromium-browser, smplayer, pidgin, vlc, subversion, and probably others. Are these causing the problems? I guess I would have to manually downgrade each of these packages to the versions distributed in jaunty or jaunty-updates? Is there a command to do this without having to manually select "Force version" on each one in Synaptic?

Attached are the logs from the latest run from the /var/log/dist-upgrade directory. (Had to change the filenames to .txt because the forum wouldn't accept them otherwise, and term.log was 0 bytes.)

Thanks in advance!

---

### Post by ENOTTY on 2009-11-01
I removed every non-Canonical supported package. (Literally, Synaptic only shows the packages with the little Ubuntu symbol in the Installed section.) Still didn't work.

Took a look at the apt.log and the last couple messages reference a package called mountall, which does not exist in Jaunty. But the upgrader says it found solutions to the broken dependencies. Blah

---

