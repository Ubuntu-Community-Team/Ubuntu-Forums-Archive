---
title: "USB corrupted and reduced in size?"
date: 2011-01-20
forum: Hardware
---

### Post by shadarack on 2011-01-20
So, today it was announced to me that my filthy Linux computer corrupted my mother-in-law's USB flash drive and reduced it's capacity. Immediately I decried this as ignorant and impossible, but on further thought, this is the third drive that has suffered malfunction after being plugged into my computer over a couple of years, and I'm starting to wonder. My USB plugs are in the back of my computer, so I use a USB extension cord to plug the drives into to read and write. The first drive to suffer was a cheap thing I got shipped to me from China, so I thought nothing of it dying. I'm not sure where the second came from, but the case declares it is an 8 gig drive. It can no longer be mounted on Linux or Windows. LSUSB says it is a 2 gig drive, and fstab -l won't list it. The mother in law's drive was also 8 gigs(although a different model then the second drive) before it was "corrupted" when I returned it to her, so she ran a quick format through Windows 7 on it. Now it shows as 2 gigs. Windows disk manager says it's 2 gigs, but refuses to delete the partition table when I tried to resize it as some tutorials have suggested. Gparted won't delete the partition table either. Is it possible Ubuntu is, for some reason, eating USB drives? Could there be something wrong with my USB ports or my USB extension cable or the combination of the two? Am I just a victim of bad circumstances? Does anyone have any suggestions for possibly recovering her drive other then just buying her a new one?

---

