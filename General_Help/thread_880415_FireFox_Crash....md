---
title: "FireFox Crash..."
date: 2008-08-05
forum: General Help
---

### Post by DivinityX on 2008-08-05
When on FireFox, i'll be surfing the web, and it just disappears (crash)...I realized it's usually when i'm loading youtube, a myspace profile, Facebook, or any other site that calls for a lot of memory, after i reload FireFox, i click the same link i just clicked, and it works fine. I'm figuring it crashes because of pull so much memory at once, but when i use firefox on windows, i don't get that...is there some way to make it stop crashing?

---

### Post by mb_webguy on 2008-08-05
It's not a memory problem.  It's Flash.  The current Flash plugin doesn't work perfectly with PulseAudio, and when Flash has a problem it causes Firefox to crash.

If you type "sudo apt-get install libflashsupport" in the terminal, it should fix it.  If not, follow the instructions on [this page]("http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html").  The nspluginwrapper causes Flash to show a gray box in Firefox when it fails, instead of crashing the browser.  Some people have reported that running Flash in nspluginwrapper uses considerably more memory, but I haven't noticed any significant difference.

---

### Post by DivinityX on 2008-08-05
i...think it worked, i installed it, restared firefox, went to myspace, and youtube...and no crash!!! HAHA!!! AMAZING!!! THANK YOU!!!

---

