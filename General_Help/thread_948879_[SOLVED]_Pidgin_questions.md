---
title: "[SOLVED] Pidgin questions"
date: 2008-10-15
forum: General Help
---

### Post by absolutezero1287 on 2008-10-15
Whenever I write a new status message it stays in the list. How do I clear them? I don't mean the SAVED statuses. I'm talking about the ones that you just type in.

Also, is there a way to get Pidgin to recognize what song I'm playing in VLC? I don't use any of the other media players. VLC gets the job done for everything.

---

### Post by khc on 2008-10-16
mouse over the status dropdown and hit delete

---

### Post by absolutezero1287 on 2008-10-16
Thanks very much!

Now does anyone know how to get pidgin to display what songs I'm listening to in VLC?

---

### Post by ryanhaigh on 2008-10-16
[http://m0n5t3r.info/work/pidgin-mpris](http://m0n5t3r.info/work/pidgin-mpris) seems to suggest vlc 0.9+ and the provided pluging might give you what you are after.

---

### Post by absolutezero1287 on 2008-10-17
Got the plugin, but people can't see what I'm playing on VLC. Do I have to make a special status message or is it supposed to do it on its own?

---

### Post by absolutezero1287 on 2008-10-28
Ok, plugin is no longer important.

New issue: I want to purge pidgin's configurations. Can I do this without uninstalling? I figured that if I did uninstall it I would have to: 
```
apt-get --purge remove pidgin
```

---

### Post by hiazle on 2008-10-28
> **absolutezero1287 said:**
> Got the plugin, but people can't see what I'm playing on VLC. Do I have to make a special status message or is it supposed to do it on its own?

Try [MusicTracker]("http://code.google.com/p/pidgin-musictracker/"). Its been under active development and works like a charm.

---

### Post by ryanhaigh on 2008-10-28
> **absolutezero1287 said:**
> Ok, plugin is no longer important.

New issue: I want to purge pidgin's configurations. Can I do this without uninstalling? I figured that if I did uninstall it I would have to: 
```
apt-get --purge remove pidgin
```

I believe your personal configuration is stored in the hidden .purple folder in your home directory.

---

### Post by absolutezero1287 on 2008-10-29
Awesome. Thanks all.

---

