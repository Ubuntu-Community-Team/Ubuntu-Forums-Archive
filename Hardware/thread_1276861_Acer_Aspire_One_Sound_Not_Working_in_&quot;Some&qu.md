---
title: "Acer Aspire One Sound Not Working in &quot;Some&quot; Programs."
date: 2009-09-27
forum: Hardware
---

### Post by Vapourstreak on 2009-09-27
Hello,

I have an Acer Aspire One AOA-150 (8.9", 160GB HDD), and I just installed Ubuntu Netbook Remix on it.  I went on YouTube, and found out sound didn't work.  I changed the sound drivers and stuff in the sound options, and clicked test.  Two of the OSS options worked when I pressed 'Test', but it wouldn't work on YouTube.  Then I installed Exaile, and played some music, and found out sounds worked there, and worked on the login screen, but in every other program, sound didn't work.  Is there any way to fix this?  If I fix this issue, Ubuntu would be perfect for me, and that would be the end of my plans to buy Windows 7. 

Thank you,
Vapour. (:

---

### Post by nixscripter on 2009-10-03
The problem might be related to ALSA vs. OSS. IIRC, the flash player (used by YouTube) is hooked into ALSA.

Go to System -> Administration -> Preferences -> Sound. What are your output devices set to, ALSA, OSS, or another option? If they are alsa, you might want to try quitting the browser, and restarting ALSA. I have written a little script to reload it, due to an unrelated problem:

```

#!/bin/sh
# by nixscripter, Ubuntu Forums
# works around a bug which causes no sound after hibernate resume

if [ `whoami` != root ]; then
    echo "You must be root to run this script." >&2
    exit 2
fi
/etc/init.d/alsa-utils restart # save and reload alsa mixer settings
/etc/init.d/alsasound restart # kill processes using it

```

You will have to run this script as root.

---

