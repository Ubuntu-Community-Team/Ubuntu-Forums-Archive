---
title: "Can totem-xine play Flash files?"
date: 2005-11-27
forum: General Help
---

### Post by Kevinator on 2005-11-27
Since I couldn't get totem-gstreamer to  work properly, I installed totem-xine instead (which seems to be the thing to do according to many other posts on this forum). Had to add a few other packages, but now I've got playback of DVDs (also needed libdvdcss of course), MP3, MPEG and some WMV files working. Currently not working are a few WMVs and all Flash (SWF) files.

Is there a plugin to make totem-xine play Flash files?

I tried libflash, but couldn't get it to play anything at all (neither the command line player or the mozilla plugin), and totem-xine doesn't seem to even attempt to use it.

I see that there's a swf-player in Universe, but it seems to be based on gstreamer, so I don't know if it will work.

---

### Post by aysiu on 2005-11-28
Any reason you want Totem to play Flash and not a web browser like Epiphany or Firefox?

---

### Post by Kevinator on 2005-11-28
Just convenience. I want a browser plugin, too. So far I haven't got either to work with packages available in the Ubuntu repositories.

---

### Post by aysiu on 2005-11-28
[QUOTE=Kevinator]Just convenience. I want a browser plugin, too. So far I haven't got either to work with packages available in the Ubuntu repositories.[/QUOTE] Have you tried 

1. the first link in my sig (to get updated repositories)
2. *sudo apt-get install flashplugin-nonfree*

?

---

### Post by Kevinator on 2005-11-28
For some reason I get errors in Synaptic when I use the repositories listed in the first sig link (I had tried this previously). But after reloading it seems to work. I thought maybe the multiverse repository just wasn't available currently for some reason.

Anyway, I see flashplugin-nonfree in Synaptic now (as well as various other packages that I had previously not been able to access), so I guess I'll try that. Thanks.

---

