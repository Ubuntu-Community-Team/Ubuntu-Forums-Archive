---
title: "Firefox crashes a lot"
date: 2008-09-18
forum: General Help
---

### Post by phil81uk on 2008-09-18
I am running a standard install of Hardy that I installed the previous week. It auto-updated itself to Firefox 3.

However FF3 seems to crash all the time. Sometimes when I click Javascript commands, other times completely randomly.

Should I try an alternative browser?
Or is there an error log where I can identify what casues it? I'd like to keep Firefox as I am used to it.

Thank.

---

### Post by prshah on 2008-09-18
> **phil81uk said:**
> 
Or is there an error log where I can identify what casues it? I'd like to keep Firefox as I am used to it.

Open a terminal (Applications-Accessories-Terminal) and give the command ```
/usr/bin/firefox
``` Now any errors (and a lot more diagnostic output) will be displayed on the terminal; you can copy and paste it here for a more accurate diagnosis.

Remember; closing the terminal will (insta)close firefox.

---

### Post by mb_webguy on 2008-09-18
It could be several things, but it's probably either corrupted configuration files or the Flash plugin.

To fix the former, either delete the .mozilla folder (after backing up your bookmarks and passwords, of course), or create a new profile using the command "firefox -profilemanager" in the terminal.  If you delete your .mozilla folder, make sure you shut down Firefox first.  You may also want to reinstall Firefox after you delete the .mozilla folder, just to make sure there isn't anything wrong with the installation.

To fix the Flash plugin, try installing the Flash 10 plugin from the backports repository.  This will fix some incompatibilities between the Flash plugin and PulseAudio that cause Flash to crash and take down Firefox with it.  Check the "Installing Flash 10 in Hardy Heron" link in my signature for instructions on how to do this.

---

### Post by phil81uk on 2008-09-20
Hello,

Opening Firefox from the command prompt gives me the following errors (and eventually it crashed:

> 
(npviewer.bin:15352): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:15352): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:15352): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:15352): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:15352): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:15352): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:15352): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:15352): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed


---

### Post by prshah on 2008-09-21
> **phil81uk said:**
> 
(npviewer.bin:15352): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:15352): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

These messages are from the (Adobe) flash plugin; they are probably not what is causing the crash. Do you have any other messages?

---

### Post by dslachut on 2008-10-01
```
GCJ PLUGIN: thread 0x622930: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x622930: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x622930: NP_GetValue
GCJ PLUGIN: thread 0x622930: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x622930: NP_GetValue return
GCJ PLUGIN: thread 0x622930: NP_GetValue
GCJ PLUGIN: thread 0x622930: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x622930: NP_GetValue return

(npviewer.bin:24043): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:24043): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:24043): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:24043): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:24043): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:24043): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed
Segmentation fault

```

Whether there is or is not a segfault is really 50-50, in other cases it just hangs in the middle of another "gtk_widget_destroy" notification.

As for when: it happens when I'm viewing Facebook photos.

---

