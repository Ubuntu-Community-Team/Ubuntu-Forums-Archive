---
title: "[SOLVED] compiz cube issues"
date: 2008-11-07
forum: General Help
---

### Post by dondad on 2008-11-07
Running intrepid with nvidia 8600 card. Compiz  works, but I cannot get the cube transparency, skydome, or cube caps to work. I am trying to use the same skydome that I used in my hardy install, but it is just black, no matter what I do with the image or colors gradient. The transparency does not work at all, and although I have no images selected for the cube caps, it has a "freedesktop.org" image on the top and a blank on the bottom that will not change.

Right now, I am running metacity as the decorator because emerald seems to crash often and I lose the bars at the top of the windows.

I have tried totally uninstalling and reinstalling, but no change. Any idea where to look next?

Update:

I finally fixed it. When I installed Intrepid, I had my home directory on a separate partition in a Gutsy install so I didn't format it. The problem was that the old configuration file from Gutsy was interfering with the newer compiz. Doing a complete removal and reinstall of compiz apparently didn't get rid of this file. Once I found it, I removed compiz and emerald again, deleted the configuration files manually, then reinstalled them. That fixed the problem. Having the /home on a separate partition is a good idea for data retention, but the invisible files, especially configurations, probably should be removed (or copied somewhere else) before doing an upgrade to a new version. After the upgrade, you can try putting them back one at a time and look for problems.

---

### Post by dondad on 2008-11-13
> **dondad said:**
> Running intrepid with nvidia 8600 card. Compiz  works, but I cannot get the cube transparency, skydome, or cube caps to work. I am trying to use the same skydome that I used in my hardy install, but it is just black, no matter what I do with the image or colors gradient. The transparency does not work at all, and although I have no images selected for the cube caps, it has a "freedesktop.org" image on the top and a blank on the bottom that will not change.

Right now, I am running metacity as the decorator because emerald seems to crash often and I lose the bars at the top of the windows.

I have tried totally uninstalling and reinstalling, but no change. Any idea where to look next?

bump

Still no transparency, 3D windows do not work, I cannot change the cube caps and the skydome does not work. Any ideas?

---

### Post by eternalnewbee on 2008-11-13
> 
Running intrepid with nvidia 8600 card. Compiz works, but I cannot get the cube transparency, skydome, or cube caps to work. I am trying to use the same skydome that I used in my hardy install, but it is just black, no matter what I do with the image or colors gradient. The transparency does not work at all, and although I have no images selected for the cube caps, it has a "freedesktop.org" image on the top and a blank on the bottom that will not change.
Hi there. Could you post some screenshots?
Just a thought: Is your **Horizontal Virtual Size** set to 4?

---

