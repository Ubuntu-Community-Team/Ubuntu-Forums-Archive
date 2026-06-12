---
title: "Audio device missing after latest update"
date: 2008-05-29
forum: Hardware
---

### Post by jmac327 on 2008-05-29
Last night I updated all the recommended and urgent packages listed by the Update Manager.  Today, I find that my Nvidia Soundstorm audio devices are missing resulting in no sound in any application.  Attempting to use the volume control gives the following message:  "No volume control GStreamer plugins and/or devices found."

I had originally followed the instructions [found here]("http://ubuntuforums.org/showthread.php?t=253725") to get the digital output Soundstorm provides and it had been working well for the last month.  I found the list of packages that were updated last night, but none of them seem related to audio.  If necessary I can post the log, but I'm wondering if something broke compatibility with the patch file I ran with the above instructions.  Any help or advice would be welcome.

---

### Post by ajgreeny on 2008-05-29
There was a kernel upgrade to 2.6.24-17-generic which may be the problem.  I think you will need to reinstall the closed source nvidia driver again for the kernel.

---

### Post by jmac327 on 2008-05-29
Thanks a lot!  This was indeed the problem, it seems I had not noticed the kernel update.  Running the installer and restarting nvsound did the trick.  I'll have to pay closer attention to the updates from now on.

---

