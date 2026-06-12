---
title: "Reinstalling software after messing it up"
date: 2008-11-07
forum: General Help
---

### Post by ykcirt on 2008-11-07
Hi there.

I messed up two software installations, those of the VLC and Audacious media players. I'm a little beyond fixing things. In the case of Audacious there could be an external factor that I don't know of, but as far as VLC is concerned, I am 100% certain that I did the damage directly to the program. I installed a VLC skin that I can't remove and only has limited functionality (can't access the detailed program options menu). VLC thinks these settings, this skin and the location of the skin file, which is annoyingly enough on the desktop, are defaults and can't be changed or replaced.

-> If I completely remove VLC via the synaptic package manager, it's not entirely gone. I know this because once I reinstall it, all the default settings and the malfunctioning skin are right back where I left them. I know what to do had this been Windows. I'd just remove every trace of it, registry entries included. But this is not Windows, so I am a little unsure how to proceed. If I do a file search after removing VLC with the synaptic package manager, there are still related files in the following places:

/usr/share/app-install/desktop
/var/cache/apt/archives (many files here)
/var/lib/dpkg/info

Can I safely remove these files *and* expect that this will help me do a completely fresh re-installation afterward?

---

### Post by hyper_ch on 2008-11-07
user settings are stored in your homefolder... check there for hidden directories.

Otherwise "purge" an installed application:

```

sudo apt-get purge vlc

```

---

### Post by mtausig on 2008-11-07
To completely remove a package open a console and type
sudo apt-get purge audacious

Then look in your home directory for config files named probably something like .audacious, audacious or .audious.rc and remove them.

Actually, try deleting your configuration directories before removing the whole program, it is more likely that the error is somewhere there.

Edit: Too slow ...

---

### Post by ykcirt on 2008-11-07
Well, thanks for those tips but they didn't work. After reinstalling VLC still errors out on starting up (asking again for the location of the 'bad' default skin file, which I removed from the desktop). And while there was one for VLC, I couldn't find an audacious folder in Home. I looked around for related names (AMP, XMMS, Beep), but I found nothing.

So. What's next?

---

### Post by mtausig on 2008-11-07
> **ykcirt said:**
> And while there was one for VLC, I couldn't find an audacious folder in Home. 

I haven't got audacious installed here, so I can't check myself. But you can try
find ~ -name '*audacious*' 2>/dev/null
and see if that finds anything. If not, try extending the search (to '*aud*')

---

### Post by mkvnmtr on 2008-11-07
Do you know how to find hidden files? Just go to View and enable hidden files. Be sure to hide them again when yu are through.

---

### Post by ykcirt on 2008-11-07
> **mkvnmtr said:**
> Do you know how to find hidden files? Just go to View and enable hidden files. Be sure to hide them again when yu are through.

I wouldn't have been able to find the .vlc folder otherwise. ;)

I'll look into the other thing, mtausig, but I have to leave the computer for a bit. I'll reply again later.

---

