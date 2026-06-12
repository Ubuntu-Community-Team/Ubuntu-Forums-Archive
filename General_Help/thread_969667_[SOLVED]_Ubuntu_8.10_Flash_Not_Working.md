---
title: "[SOLVED] Ubuntu 8.10 Flash Not Working"
date: 2008-11-03
forum: General Help
---

### Post by Bradl3yJ on 2008-11-03
I jsut upgraded to 8.10 from 8.04, and synaptic shows that:

firefox (3.0.3+nobinonly-0ubuntu2) is installed.
flashplugin-nonfree (10.0.12.36ubuntu1) is installed.

Flash will not work on any website, firefox attempts to install missing plugins but finds none. When I go to "Tools>Addons" in firefox, Flash is not listed under Plugins.I have tried completely removing flashplugin-nonfree and reinstalling, with the same results.

---

### Post by Game_boy on 2008-11-03
This doesn't solve the specific problem of flashplugin-nonfree, but have you tried gnash as an alternative?

---

### Post by Bradl3yJ on 2008-11-04
Yes i just tried it, however, it seems slow and buggy, many flash files do not work properly.

Apparently even if it is working properly it will not show in Tools>Addons, so where can you check withing firefox to see that the plugin is loaded?

I have tried completely removing flash AND firefox-3.0 using synaptic, then reinstalling both, and still no luck. Interesting thing is that when i choose to "Completely Remove" firefox-3.0 and when i reinstalled it, my bookmarks were still there. That doesn't seem to be completely removing it to me.

I have also tried completely removing the flash-nonfree and downloading the deb from adobe. Same problem.

When i go to a site that requires flash, i click "Install missing plugins" and choose Adobe Flash, it says it is already installed.

---

### Post by Bradl3yJ on 2008-11-04
If i launch FF from terminal, i get these error messages when visiting a site with flash.

> LoadPlugin: failed to initialize shared library /usr/lib/flashplugin-nonfree/libflashplayer.so [libnss3.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /usr/lib/flashplugin-nonfree/libflashplayer.so [libnss3.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /usr/lib/flashplugin-nonfree/libflashplayer.so [libnss3.so: cannot open shared object file: No such file or directory]


I checked and found that /usr/lib/libnss3.so did not exist, but /usr/lib/libnss3.so.1d did exist. I searched synaptic for libnss3, and found that the only package that was installed in the results was libnss3-1d. I created a symbolic link libnss3.so to libnss3.so.1d, and that error was gone (although the same then happened for libsmime3.so, and then one more file, after creating 3 symlinks there, flash now works).

So flash now works, but I am concerned that there is an underlying problem. The "Installed Version" for libnss3-1d is 3.12.1~cvs20080501......hardy, under the properties for the package it shows that it there are two available versions, one is 3.12.0.3-0ubuntu5 (intrepid) which matches someone elses machine. How to i get the proper intrepid version installed? If i choose to uninstall this from synaptic, it wants to uninstall a whole lot of programs that depend on it.

---

### Post by Bradl3yJ on 2008-11-04
To answer my own question, in Synaptic I clicked on the package, went to Package>Force Version and selected the intrepid version. I removed my manual symlinks first, and confirmed that the official intrepid version creates the neccisary links, so this should be all you have to do if you have this problem, install the official version if this lib.

---

### Post by skubler on 2008-11-10
Just want to say that thanks for your post. I had the exact same problem with flash not playing any sound. Once I re-installed libnss3-1d in synaptic and forced the correct version I had sound back while viewing flash content in FF3.

---

### Post by racedog on 2009-01-17
For what it's worth, I had  similar problem because I was working with the Google Web Toolkit (a software development library).  They have their own mozilla browser for debugging and, in order to get that working, I had messed around with some environment variables.  

Specifically, I had changed LD_LIBRARY_PATH to reference the GWT mozilla directory.

So, word to the wise, if Flash isn't working with firefox, make sure it can find this library, and I guess that you have the correct version.  Who knew.

---

### Post by jepperstone on 2009-04-15
I removed flashplugin-nonfree and instead use adobe-flashplugin. Firefox works great except when I watch something on Youtube or Google Video, Firefox goes grey (freezes) and CPU usage goes to 100%. Can someone help me with this? I installed Adobe Flash from the Adobe website (version 10).

Update: I uninstalled Firefox and Flash and reinstalled. I then disabled Shockwave Flash in the add-ons menu. Youtube seems to work fine now except that it tells me I either have JavaScript turned off (I don't think so) or that I don't have Flash installed (but I just installed from the .deb found on the Adobe site). At least Firefox doesn't freeze up anymore, but Flash still doesn't work. I also checked about:plugins and Flash was not listed. Any ideas?

---

