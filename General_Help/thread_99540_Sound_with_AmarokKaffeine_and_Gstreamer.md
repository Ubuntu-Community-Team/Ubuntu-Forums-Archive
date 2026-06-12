---
title: "Sound with Amarok/Kaffeine and Gstreamer"
date: 2005-12-05
forum: General Help
---

### Post by Ruskie on 2005-12-05
Ok, I've messed it all up and I'll have to start from scratch...
At first I didn't get to play DVD on gstreamer, so I installed xine. Kaffeine become instable, but I got video for dvd and divx. Alas, for divx... no sound! And mp3 in Amarok also have no sound...
So my question, put simple, is:

Out of the box, how do you get DVD playback, Divx playback and Mp3 sound, assuming you're using Kaffeine and Gstreamer?

I know some libs have to be installed in /usr/lib/win32, but I'm not sure where to get them and how to instruct gstreamer to look there (I managed for xine, but they didn't play sound...)

Thank you
Marco

---

### Post by Ruskie on 2005-12-06
Gave up on the thing, currently I'm trying to make it work with xine. I've uninstalled everything marked as gstreamer, and installed amarok xine plugin, but it still doesn't work:
I have system sound playing.
Cd playing (but not with amarok: only with Kaffeine or the KsCD)
Dvd  playing (sound and video)
Divx partially playing (video ok but not audio)
Mp3 not playing which is the same as for DivX I believe since Divx audio should be encoded in Mp3....

So, I have xine installed, and /usr/lib/win32 --> essential-20050412 and  xine-lib-1.1.1 installed, taken from xine and mplayer hq.

Questions are:
What should I do to have mp3 played (and thus divx)?
Why amarok won't play cd audio? I can find the tracks with all sort of extensions (.ogg, .wav, .cda etc.) but if I add them to the playlist I get the warning "Some media could not be reproduced" or something like that...

Please help!!!
Thanks
Marco

---

### Post by Ruskie on 2005-12-06
Ok, in case you did, stop worrying for me stupid dumbass. :) I just discovered the Restricted Formats page:
[https://wiki.ubuntu.com/RestrictedFormats?highlight=%28Restricted%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28Restricted%29)

I'll try the lot when I got home from work and I hope I won't have problems anymore. :)

---

### Post by Ruskie on 2005-12-07
I finally managed it all working. Here's the result, I'd be glad if someone could sign the correctness of what I write; To save space, I tried to use kubuntu-desktop programs, without installing cooler one (i.e. Mplayer, etc.):

- For Audio-CD playing I use KsCD (right name?)-Gstreamer. I think this only works after installing gstreamer-plugins, however it works. Note: Amarok cannot play Audio-CD, at least with Gstreamer, because it uses the audiocd:\\ protocol that Gstreamer (and Xine) do not support.

- For Mp3, wav, ogg etc. I use Amarok-Gstreamer. It needs the gstreamer plugins as well. Might use Kaffeine as well.

- For DVD-Divx I use Kaffeine, this time I had been forced to install the Xine engine anyway. Infact, to play DVD you need libdvdcss2 (found in libdvdread3) but even if I install it and launch the appropriate script, Kaffeine can't run DVD when I insert it in the tray or open it from Kaffeine. It works good in Xine. For Divx, using Xine you need Mplayer Xine codec, which I put in /usr/lib/win32, and they played with no sound at first. Things changed when (I think), I installed the gstreamer plugin.

That's it, if you notice errors please do correct me.

Thanks
Marco

---

