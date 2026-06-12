---
title: "Trouble with FireFox"
date: 2008-08-03
forum: General Help
---

### Post by nadimRafehi on 2008-08-03
All of a sudden my Firefox stopped working. It'll open and after a few seconds automatically close.

I ran Firefox from the terminal and here is what I came up with:

> $ ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
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
GCJ PLUGIN: thread 0x622920: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x622920: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x622920: NP_GetValue
GCJ PLUGIN: thread 0x622920: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x622920: NP_GetValue return
GCJ PLUGIN: thread 0x622920: NP_GetValue
GCJ PLUGIN: thread 0x622920: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x622920: NP_GetValue return
/usr/lib/firefox-3.0.1/firefox: symbol lookup error: /usr/lib/libcairo.so.2: undefined symbol: pixman_format_supported_destination


Any ideas?

---

### Post by nadimRafehi on 2008-08-03
Anyone? :(

---

### Post by jimv on 2008-08-03
hmmm...you could try reinstalling.  This command will do that and leave your profile intact:


sudo apt-get remove --purge firefox-3.0
sudo apt-get install firefox-3.0

---

### Post by nadimRafehi on 2008-08-03
Nope, no changes. I think it may have something to do with libcairo as can be seen in the error message:

> /usr/lib/firefox-3.0.1/firefox: symbol lookup error: /usr/lib/libcairo.so.2: undefined symbol: pixman_format_supported_destination


---

### Post by tamoneya on 2008-08-03
what is the output of:```
ls -l ~/.mozilla/firefox
```

---

### Post by nadimRafehi on 2008-08-03
That gives me:

> total 8
drwx------ 7 nadim nadim 4096 2008-08-03 17:10 3me4i383.default
-rw-r--r-- 1 nadim nadim   94 2008-07-23 09:00 profiles.ini


---

### Post by tamoneya on 2008-08-03
> **nadimRafehi said:**
> That gives me:

everything looks fine there.  Try this:```
sudo apt-get install libcairo2
```

---

### Post by nadimRafehi on 2008-08-03
Hmm, it seems to be working a bit better now. It closes when I visit certain pages though. For example, if I try to log into gmail it'll close once the loading bar has filled.

---

### Post by nadimRafehi on 2008-08-03
> **tamoneya said:**
> everything looks fine there.  Try this:```
sudo apt-get install libcairo2
```

No, that's already installed.

Maybe Cairo-Dock may have something to do with it. I couldn't get it to work with Glitz using the SVN version (French error messages  are painful) so I ended up using the --remove command on the SVN file. Could that have something to do with it?

---

### Post by nadimRafehi on 2008-08-03
Any ideas on where I can go from here?

---

### Post by nadimRafehi on 2008-08-03
I've established the problem is related to FireFox.

When I tried to open xampp panel (sudo ./lampp panel) I got a similar error message:

> Traceback (most recent call last):
  File "xampp-control-panel.py", line 21, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
ImportError: /usr/lib/libcairo.so.2: undefined symbol: pixman_format_supported_destination


---

