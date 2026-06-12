---
title: "Sound issue: higher pitch - Ubuntu 12.04"
date: 2013-06-11
forum: Hardware
---

### Post by chicknmuncher on 2013-06-11
I'm having a strange issue with my sound. I have no problems hearing anything, but it's all pitched up a noticeable amount. Like a chipmunk effect. I've checked the forums as well as various google searches and I'm having no luck at all.

Ubuntu 12.04 (fresh install)
Unity desktop
Acer Aspire 3620 Laptop

I'm am fairly new with Linux but I know my way around enough. Any help is much appreciated.

---

### Post by GrimReaperAxeKick on 2013-06-11
[COLOR=#000000]Right click on the volume icon (speaker, usually top-right of screen)-[/COLOR]
[COLOR=#000000]click on "open volume control", the alsa-mixer control panel opens.[/COLOR]
[COLOR=#000000]Then edit, preferences, and in the list;[/COLOR]
[COLOR=#000000]scroll down to "clock internal rate" and check it (make it visible).[/COLOR]
[COLOR=#000000]Close the preferences and return to the alsa-mixer control panel,[/COLOR]
[COLOR=#000000]Click the options tab, the box "internal clock rate" needs setting to 44100[/COLOR]

---

### Post by chicknmuncher on 2013-06-11
Thanks for the reply,

I must not know as much as I think, or we have some sort of miscommunication because I'm not finding either of those menus.

*UPDATE* While troubleshooting I decided to find a movie file and give it a try. No issues.The only thing I was using before was Google Chrome browser. Opened up YouTube in Firefox and sure enough no problems. I'm gonna take the easy way out here and get rid of Chrome. Save a lot of hassle.

Thank you again though

---

### Post by GrimReaperAxeKick on 2013-06-11
If that's the case, then that would render my solution irrelevant. And on that note, I'm not too sure about the Chromium issue. Chromium doesn't have any equalizer, and it has no sound setting per se, so it's probably a coding issue - something of which I'm not too learned in (at least at the moment), or it could be a driver issue.

---

