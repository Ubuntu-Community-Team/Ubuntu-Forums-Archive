---
title: "Help! Font error"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by JustGus on 2008-12-07
Hi,  I tried out, then uninstalled a MythTV app and since then I'm getting error messages when I attempt to install any other software. I've tried uninstalling and reinstalling and still have problems, with the error messages pointing to the fontconfig and ttf-liberation typeface files.
When I try to reinstall these files through Synaptic I get:
[i]E: fontconfig: subprocess post-installation script returned error exit status 1
E: ttf-liberation: subprocess post-installation script returned error exit status 1[/i] 

Synaptic Package Manager on the other hand is indicating "0 [applications] broken"

Does anyone out there know of a solution?  Thanks in advance!

---

### Post by JustGus on 2008-12-20
Replying to my own request (Newbie, [s]Doctor,[/s] heal thyself!"), I found the following solution, which was to open the Terminal and run *defoma-reconfigure -f*  
 This went through and cleaned up both fontconfig and the offending liberation font.

---

