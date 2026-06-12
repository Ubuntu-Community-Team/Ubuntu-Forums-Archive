---
title: "Evince crashing bug"
date: 2008-11-25
forum: General Help
---

### Post by Orionriver on 2008-11-25
As a disclaimer, I am a newbie to these forums, so if I am posting in the wrong forum, or breaching some other etiquette, please tell me. 

I have recently experienced a bug in Evince that caused it to crash immediately after opening any .pdf. I ran it in terminal and got this output:

(evince:6005): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.16.6/gobject/gtype.c:3362: type id `0' is invalid

(evince:6005): GLib-GObject-WARNING **: can't peek value table for type `<invalid>' which is not currently referenced

(evince:6005): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.16.6/gobject/gvalue.c:96: cannot initialize GValue with type `(null)', this type has no GTypeValueTable implementation

(evince:6005): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.16.6/gobject/gtype.c:3362: type id `0' is invalid

(evince:6005): GLib-GObject-WARNING **: can't peek value table for type `<invalid>' which is not currently referenced

(evince:6005): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.16.6/gobject/gvalue.c:96: cannot initialize GValue with type `(null)', this type has no GTypeValueTable implementation
**
** ERROR:(/build/buildd/evince-2.22.2/./shell/ev-metadata-manager.c:574):save_values: code should not be reached
Aborted

I can use other programs to run the .pdfs, so I know it isn't a problem with them, and I had been runnning these pdfs in evince up until my computer hung a few minutes ago. A casual google search of the bug yielded no useful results.

---

