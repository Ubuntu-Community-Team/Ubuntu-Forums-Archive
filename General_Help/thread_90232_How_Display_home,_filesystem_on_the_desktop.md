---
title: "How: Display home, filesystem on the desktop"
date: 2005-11-14
forum: General Help
---

### Post by tig4 on 2005-11-14
Was wondering how to display my home dir and filesystem on the desktop not as a softlink. I dont want the little link icon on them. Is there a way to do this?

Thanks,

Tig

---

### Post by MichaelM on 2005-11-14
This might help:[QUOTE=ubuntuguide.org]How can I show the Computer, Home, and Trash desktop icons in GNOME?

       1.
          Make sure the universe and multiverse repositories are enabled. (See How do I add Universe and Multiverse?)

       2.
          Install the gtweakui package with Synaptic (See How do I use Synaptic to install packages?)

          Gnome (universe) > gtweakui

       3.
          After gTweakUI is installed, choose System &#8594; Preferences &#8594; gTweakUI - Nautilus.

       4.
          Select the Show computer icon, Show home icon, and Show trash icon check boxes. The changes take effect immediately.[/QUOTE]

---

### Post by tig4 on 2005-11-14
Thanks!

---

### Post by mcduck on 2005-11-14
or same without installing anything:

1.Open Applications/System Tools/Configuration Editor.
2. Go to apps/nautilus/desktop.
3. Select computer_icon_visible and home_icon_visible (and documents and trash icons too, if you wish. Note, that for Documents icon you must have a 'Documents' directory in your home.)

---

### Post by tig4 on 2005-11-14
[QUOTE=mcduck]or same without installing anything:

1.Open Applications/System Tools/Configuration Editor.
2. Go to apps/nautilus/desktop.
3. Select computer_icon_visible and home_icon_visible (and documents and trash icons too, if you wish. Note, that for Documents icon you must have a 'Documents' directory in your home.)[/QUOTE]

Even better! :)

---

### Post by MichaelM on 2005-11-14
[QUOTE=mcduck]or same without installing anything:

1.Open Applications/System Tools/Configuration Editor.
2. Go to apps/nautilus/desktop.
3. Select computer_icon_visible and home_icon_visible (and documents and trash icons too, if you wish. Note, that for Documents icon you must have a 'Documents' directory in your home.)[/QUOTE]
That should be in the guide instead (or also). :)

---

