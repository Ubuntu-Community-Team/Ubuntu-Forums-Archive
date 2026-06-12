---
title: "[SOLVED] Firefox printing closes window- help!"
date: 2008-10-26
forum: General Help
---

### Post by FokkerCharlie on 2008-10-26
Hi!

Recently, I have noticed a problem when trying to print in Firefox.  Whenever I select File > Print Preview, or File > Print > Print, all open FF windows close.

When launching FF from a terminal, this is the output:
```

~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
/usr/lib/firefox-3.0.3/firefox: symbol lookup error: /usr/lib/xulrunner-1.9.0.3/libxul.so: undefined symbol: cairo_ps_surface_restrict_to_level
```

the ** Message line appear at start, but the /usr/lib etc part appears when the program closes itself.

I think that the problem may have started when I installed Cairo-dock and had a fiddle with it.  I have since uninstalled this.  The problem manifests with all users on my machine, whether printing to the HP printer that I have or to PDF.

Any ideas?

Cheers
Charlie

---

### Post by FokkerCharlie on 2008-10-27
OK- solved this.

Was to do with a svn installation of Cario-dock.  Needed to install with glitz, then uninstall with Glitz.

Charlie

---

