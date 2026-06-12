---
title: "Pidgin closes with no error"
date: 2008-08-31
forum: General Help
---

### Post by reets on 2008-08-31
When I run Pidgin it will randomly close (usually when I am not even doing anything with it at the time) and no error message comes up. I did a back trace, hopefully that helps. It's v2.5.0 from getdeb.net and I did remove Pidgin from Synaptic first before installing.

---

### Post by Ryadt on 2008-08-31
Try starting pidgin in the terminal```
pidgin -d
```
Post any output errors.

---

### Post by reets on 2008-08-31
Thanks for the info, I think it may be the Guification plugin that is causing the crash. Anyone experience that before? I installed the one from their site or is there a special one needed?

There was no actual error in the debug info, just a lines showing my friend sign off and then Segmentation Fault and then closed. I disabled Guification plugin and next time someone signed off/on it didn't crash.

Update:

It did eventually crash again, seems to maybe not be Guification since it's disabled now but still crashed when someone signed off/on. Here is the last few lines before it crashed:

```

(12:11:21) msn: Queueing buddy icon request for email@hotmail.com (buddy_icon_window = 1)
(12:11:21) msn: Releasing buddy icon request
(12:11:21) msn: new httpconn (0x86a3860)
(12:11:21) msn: C: NS 000: XFR 16 SB
(12:11:21) msn: switchboard send msg..
(12:11:21) msn: Appending message to queue.
(12:11:21) msn: msn_release_buddy_icon_request(): buddy_icon_window-- yields =0
(12:11:21) blist: Updating buddy status for email@hotmail.com (MSN)
(12:11:21) msn: S: NS 000: UBX email@hotmail.com 1 0
(12:11:21) msn: UBX received.
(12:11:21) msn: S: NS 000: UBX email@hotmail.com 1 80
(12:11:21) msn: UBX received.
(12:11:21) msn: msn get PSM
(12:11:21) msn: Get CurrentMedia
(12:11:21) msn: No currentmedia string
(12:11:21) blist: Updating buddy status for email@hotmail.com (MSN)
Segmentation fault

```

---

### Post by Sycron on 2008-08-31
I'm using pidgin 2.5.0 for no less than 1 week and no problems. Try disabling the plugins.

---

### Post by reets on 2008-08-31
Disabled all plugins except the Nautilus integration (which is enabled by default). Running a new test now and waiting to see if it dies again. If it doesn't after a while I'll have to enable 1 plugin at a time and see what makes it crash. 

I only had Buddy Notification and Marker Line turned on so those only do things inside IM windows anyways but who knows.

Update (these lines came up when loading the plugins window, any issues in these lines?):
```

(12:58:51) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(12:58:51) plugins: probing /usr/lib/purple-2/liboscar.so
(12:58:51) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(12:58:51) plugins: probing /usr/lib/purple-2/tcl.so
(12:58:51) plugins: /usr/lib/purple-2/tcl.so is not loadable: libtk8.4.so.0: cannot open shared object file: No such file or directory

```

---

### Post by Sycron on 2008-08-31
Is the plugin compatible with the latest 2.5.0 pidgin ?

---

### Post by reets on 2008-08-31
The only plugin I actually installed was Guification, everything else was there when Pidgin was installed. Should the guification plugin work just fine though in 8.04 with Pidgin 2.5.0?

Also, if it is Guification causing the problem, does that plugin work properly with dual monitors?

UPDATE: 
Pidgin 2.5.0 crashed after a few hours again so i just installed Pidgin 2.5.1 and only libnotify enabled, we shall see what happens.

---

### Post by reets on 2008-08-31
Tried GDB again and it ended with this:

```

(no debugging symbols found)

Program exited with code 01.

```

Fresh install, did complete removal of 2.5.0 and this one is 2.5.1 with no plugins enabled at all.

---

### Post by reets on 2008-09-01
Fixed, it was some kind of sound conflict and had nothing to do with Pidgin. Had to fix it in Ubuntu. Thanks for all the suggestions!

---

### Post by pigphish on 2008-10-28
Had the same issue and was getting an abrupt crash from pidgin. Took advice and went to System-> preference -> sound. 

Set everything to automatic and doesn't crash any more.

---

