---
title: "[SOLVED] Graphics not working since upgrade to Intrepid"
date: 2008-11-16
forum: Hardware
---

### Post by timswait on 2008-11-16
I've just upgraded from Hardy Heron to Interpid Ibex, but my graphics have been in low graphics mode since. I get the following message when I start up:
> Ubuntu is running in low graphics mode
The following error was encountered. You may need to update your configuration to solve this.
(EE) fglrx (0): atiDriScreenInit failed. GPS not been initialised.
(EE) fglrx (0): FB pci_device_map_range error! (EE) fglrx (0): Failed to map FB memory.
(EE) fglrx (0): firegl_SetSuspendResumeState FAILED -9

Under Hardy I was running the ATi restricted driver. Now when I go to System>Admin>Hardware there is a "ATI/AMD proprietary FGLRX driver listed but it is not activated. When I click "activate" I am prompted to enter my password, which I do, but then nothing happens. A window with a progress bar at 0% briefly flashes up then vanishes, but nothing more happens.
What do I need to do to sort this out?
Cheers

---

### Post by timswait on 2008-11-17
Solved it myself. I had my ATi drivers installed with "Envy". When I uninstalled the driver with Envy then I could install the one Ubuntu listed as a restricted driver and now it works :)

---

