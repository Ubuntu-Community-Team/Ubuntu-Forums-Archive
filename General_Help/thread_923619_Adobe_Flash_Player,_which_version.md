---
title: "Adobe Flash Player, which version?"
date: 2008-09-18
forum: General Help
---

### Post by azTom on 2008-09-18
I'm running Firefox 3.0.1 and have been advised that I need Adobe Flash Player to view certain sites.

Adobe lists 3 Linux packages- .tar.gz; .rpm; ans YUM which is recommended to use with Ubuntu 8.04?

Thanks for any and all replies.

---

### Post by mb_webguy on 2008-09-18
*Never* install software from source unless you absolutely have to!  First, look in the Ubuntu repositories (either by using Add/Remove Programs or Synaptic).  Second, look for trusted third-party repositories or PPAs (Personal Package Archives).  Once you add these repositories to your sources, you can install software from them using Add/Remove Programs or Synaptic.  Third, look for deb files.  These are installation files for Debian-based Linux distributions (which includes Ubuntu).  Finally, if you have absolutely no other choice, then -- and only then, and only if you're sure you really, really need this particular software package, and no other alternative will do -- you can install from source code.

The Flash plugin is available in the repositories.  Either open Synaptic and search for "flashplugin-nonfree", or type "sudo apt-get install flashplugin-nonfree" in the terminal.  HOWEVER, this will install Flash 9, and this version of the plugin has known compatibility issues with PulseAudio, and may cause Firefox to crash frequently.  My suggestion is to install the Flash 10 plugin from the backports repository, following the instructions in the "Installing Flash 10 on Hardy Heron" link in my signature.

---

