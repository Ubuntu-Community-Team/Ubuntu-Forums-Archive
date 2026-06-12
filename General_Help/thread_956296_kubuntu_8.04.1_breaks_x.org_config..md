---
title: "kubuntu 8.04.1 breaks x.org config."
date: 2008-10-23
forum: General Help
---

### Post by kesuki on 2008-10-23
okay, updating to 8.04.1 breaks my x.org config. 8.04 works fine, i switched to kubuntu, when i realized kubuntu worked with my graphic card i switched (i had been booting ubuntu with gnome failsafe, manually had to set it each login) oh as a side note, kubuntu 8.10 beta works great with my gpu, but i can't stand adept as an installer.  it doesn't sort things alphabetically, has no way to force alphabetic sorting, and worst of all the search is broken. a search for an application by name only works if the long description includes the application name. about 90% of the repository avoids the redundant name of application in the description, because it's in the name of the program... which adept can't search. besides, i don't like using beta software.  

okay it's really integrated motherboard graphic, but i don't have a single working pci-express graphic card, none of my legacy pci (yes legacy pci)  graphic cards work really well with ubuntu or kubuntu, and the integrated grapics is better than the legacy pci cards anyways.   bedsides, i dual boot to windows, and it's a real pain to switch the gpu in bios every time i reboot.  no i don't have money to buy a pci express card either. 

i confirmed that it was the 8.04.1 upgrade that broke my x.org config, because trying to boot from an 8.04.1 cdrom does the same thing my upgraded hard drive does, it endlessly fails to launch kdm, and keeps trying and failing.  over, and over.  doesn't matter if i install the closed source drivers from ati, it still does the same.  

so how do i revert the upgrade, or fix the x.org config? how do i downgrade to the working 8.04 version? i have command line access only(to my hd install), reformatting  would take me about 6 hours of copying files over, it would be nice to just have an apt-get command or series of commands. 

it would be a real pain to have to download a 8.04 cd and then copy over the x.org config files, and i'm not even sure that would work... i might have to take the working version of kdm, from 8.04 and not the broken 8.04.1

---

### Post by kesuki on 2008-10-23
okay, i admit that the search might not be as bad as i thought in adept, because i was misspelling the name of the application in question.  but the search can't be tweaked, dolphin can't be tweaked, tons of tweaking tools for kde are missing... it's like some authoritatian gods at kde decided single clicks must be universal, and the features they want must be default, etc etc. making customization as difficult as possible... 

i've never liked dolphin, and if gnome worked on my gpu i would probably use ubuntu instead, but it doesn't.  in kde 3 it was easy to set nautilus as my file manager, and it worked fine.

---

