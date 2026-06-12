---
title: "How to Change Browser Password Masking Character"
date: 2008-09-26
forum: General Help
---

### Post by maw246 on 2008-09-26
This might seem like a pointless question, but I've googled & Yahoo'ed for this and can't seem to find an answer anywhere...

I am running Hardy Heron with Gnome.  When I type into a password textbox within Firefox, my password characters are masked with a large solid circle character.  I'm used to asterisks for masking password characters.  Is this a setting of Firefox?  Or rather, a setting of Gnome?  Can I change it, and if so, how?

Thanks.

---

### Post by anotherdisciple on 2008-09-26
I'll bet you can find it in gconf-editor... I'll search around sometime tonight and get back to you.

---

### Post by Popsicle-Pete on 2009-03-04
I am looking to make the same changes. These black circles are ugly =P

If you found a way please post it here!

Thanks!

---

### Post by frunze on 2009-06-08
I found a way to make those circles look smaller like in Windows XP. Go to synaptic package manager and search for **msttcorefonts** - these are MS Fonts, so you will have Arial, Verdana, Times New Roman and others.
Whatever it tells you agree to it.
Once installed, you can choose these fonts in System--> Preferences --> Appearance. 
I set Desktop, Application and Document font to Arial (see screenshot) and now I have nice little circles (another screenshot).

---

### Post by 8thMP on 2009-08-08
That's great and all, but what if someone wants something else other than the black circles? Maybe we want an asterisk or something of the like.

---

### Post by russellnation on 2009-11-24
I have been lookng for the same thing for a while and found this:

[http://library.gnome.org/devel/gtk/unstable/GtkEntry.html]("http://library.gnome.org/devel/gtk/unstable/GtkEntry.html#gtk-entry-set-invisible-char")

Do a Ctrl+F and search for 'gtk_entry_set_invisible_char'

The file it refers to is at: /usr/include/gtk-2.0/gtk/gtkentry.h

I don't know how to use this, but it seems to be in the right direction.

---

