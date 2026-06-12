---
title: "Can't start gnome-app-install"
date: 2005-11-22
forum: General Help
---

### Post by FiVAL on 2005-11-22
Hello everyone!

I'm still a N00B in the Unix world and I tried, also suceed,
to install the new 1.5rc3 of FireFox. But I guess I also did
something wrong...

At the moment gnome-app-install won't start anymore!

```

root@ubuntu76:/home/evwielinga# gnome-app-install
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 41, in ?
    from AppInstall import AppInstall
  File "/usr/lib/gnome-app-install/AppInstall.py", line 30, in ?
    import gtkmozembed
ImportError: /usr/lib/mozilla-firefox/libgtkembedmoz.so: undefined symbol: _ZTV24nsGetServiceByContractID

```

Is there someone who can help me?

ThX in advance!

Edgar

---

### Post by frodon on 2005-11-22
I advice you to follow these instructions : [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion).

---

### Post by FiVAL on 2005-11-22
I did find that article in the end.
And that's also the reason new FireFox works!

Only now won't "Gnome-app-install" work anymore ;-(

---

### Post by FiVAL on 2005-11-23
Is there a Way to install -> gnome-app-install again?

---

### Post by jrib on 2005-11-23
[QUOTE=FiVAL]Is there a Way to install -> gnome-app-install again?[/QUOTE]

Yes, in synaptic.  gnome-app-install depends on the firefox package.  Did you remove the old package when you installed the new firefox version?  You should keep the old firefox package installed even though you have 1.5RC3 installed as well.

---

