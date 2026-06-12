---
title: "No sound in FF when playing flash"
date: 2008-09-01
forum: General Help
---

### Post by PC_load_letter on 2008-09-01
Hi all,
   I am running Xubuntu 8.04 32bit and the sound was working perfectly. Today I wanted to watch an FLV file that I downloaded, MoviePlayer couldn't play it at first, so it searched for the gstreamer plugins and installed them.

Now there is no sound when I try to play flash movies, youtube or anything flash on FF. I installed "libflashsupport" but in vain.

When I run FF from terminal here is the error that I get when trying to watch a youtube video:

```
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
```

Any idea how this could be fixed?

Thanks.

---

### Post by quibbler on 2008-09-01
> **PC_load_letter said:**
> Hi all,
   I am running Xubuntu 8.04 32bit and the sound was working perfectly. Today I wanted to watch an FLV file that I downloaded, MoviePlayer couldn't play it at first, so it searched for the gstreamer plugins and installed them.

Now there is no sound when I try to play flash movies, youtube or anything flash on FF. I installed "libflashsupport" but in vain.

When I run FF from terminal here is the error that I get when trying to watch a youtube video:

```
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
```

Any idea how this could be fixed?

Thanks.
Download Adobe flash here:
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

Install vlc and the vlc plugin for firefox from the package manager.

Regards quibbler

---

### Post by PC_load_letter on 2008-09-01
I don't get it, I already have the flash plugin installed from Synaptic, so does the link provide a new version that will fix my problem? 
I heard people recommending the Flash 10 but it still in beta, I'll wait for the official release.

---

