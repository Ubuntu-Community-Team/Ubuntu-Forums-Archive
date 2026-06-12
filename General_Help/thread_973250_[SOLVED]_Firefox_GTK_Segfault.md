---
title: "[SOLVED] Firefox GTK Segfault"
date: 2008-11-06
forum: General Help
---

### Post by c1rcu17 on 2008-11-06
I'm getting this weird error every time I try to visit my school's online course tools. When I run Firefox from the terminal, I get this output then Firefox crashes. It looks like the GCJ plugin may be the culprit. I have tried purging and reinstalling the plugin via the repositories.

```

GCJ PLUGIN: thread 0x1cd0800: NP_Initialize
GCJ PLUGIN: thread 0x1cd0800: NP_Initialize: using /usr/lib/classpath/gappletviewer.
GCJ PLUGIN: thread 0x1cd0800: NP_Initialize return
GCJ PLUGIN: thread 0x1cd0800: GCJ_New
GCJ PLUGIN: thread 0x1cd0800: plugin_data_new
GCJ PLUGIN: thread 0x1cd0800: plugin_data_new return
GCJ PLUGIN: thread 0x1cd0800: plugin_get_documentbase
GCJ PLUGIN: thread 0x1cd0800: plugin_get_documentbase return
gcjwebplugin.cc:978: thread 0x1cd0800: Error: Failed to read line from whitelist file.

(firefox:7865): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'
GCJ PLUGIN: thread 0x1cd0800: NP_GetValue
GCJ PLUGIN: thread 0x1cd0800: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x1cd0800: NP_GetValue return
GCJ PLUGIN: thread 0x1cd0800: GCJ_GetValue
GCJ PLUGIN: thread 0x1cd0800: GCJ_GetValue: returning TRUE for NeedsXEmbed.
GCJ PLUGIN: thread 0x1cd0800: GCJ_GetValue return

(firefox:7865): Gdk-CRITICAL **: gdk_window_get_user_data: assertion `window != NULL' failed

(firefox:7865): Gtk-CRITICAL **: gtk_container_add: assertion `GTK_IS_CONTAINER (container)' failed

(firefox:7865): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(firefox:7865): Gtk-CRITICAL **: gtk_socket_get_id: assertion `GTK_WIDGET_ANCHORED (socket)' failed
Segmentation fault

```

I couldn't find anything when I searched for for solutions. Any ideas?

---

### Post by c1rcu17 on 2008-11-07
Ok, It seems like I figured it out. For future reference, I purged all things icedtea/GCJ plugin related. I also disabled the GCJ plugin under firefox and removed the actual plugin file. I double checked that my sun java install was working properly. Removing all that stuff seemed to work.

---

