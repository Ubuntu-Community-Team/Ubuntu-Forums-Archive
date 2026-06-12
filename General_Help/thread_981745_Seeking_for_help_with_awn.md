---
title: "Seeking for help with awn"
date: 2008-11-14
forum: General Help
---

### Post by youxiang95 on 2008-11-14
When I closed a program, some icons on the awn bar would got a white box,or vertical line which would disappear if I move the mouse on it. And I found that the white box (or line) appeared only on the applet icon that is added from the awn manager. I used awn normally when it run on Ubuntu 8.04 except for 8.10. 
It is said that the problem was because the depandences of the python program, but it still appeared nomatter I install the depandences. I ran the awn in the terminal and I got some messge below:




(awn-applet-activation:12406): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.18.2/gobject/gsignal.c:2346: handler `36' of instance `0x997a010' is not blocked

(avant-window-navigator:12404): Wnck-CRITICAL **: wnck_window_get_actions: assertion `WNCK_IS_WINDOW (window)' failed

(avant-window-navigator:12404): Wnck-CRITICAL **: wnck_window_get_screen: assertion `WNCK_IS_WINDOW (window)' failed

(avant-window-navigator:12404): Wnck-CRITICAL **: wnck_screen_get_workspace_count: assertion `WNCK_IS_SCREEN (screen)' failed

(avant-window-navigator:12404): Wnck-CRITICAL **: wnck_window_is_minimized: assertion `WNCK_IS_WINDOW (window)' failed

(avant-window-navigator:12404): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkBin'

(avant-window-navigator:12404): Gtk-CRITICAL **: gtk_label_set_text: assertion `GTK_IS_LABEL (label)' failed

(avant-window-navigator:12404): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkBin'

(avant-window-navigator:12404): Gtk-CRITICAL **: gtk_label_set_use_underline: assertion `GTK_IS_LABEL (label)' failed

(avant-window-navigator:12404): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkImageMenuItem'

(avant-window-navigator:12404): Gtk-CRITICAL **: gtk_image_menu_item_get_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(avant-window-navigator:12404): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkImageMenuItem'

(avant-window-navigator:12404): Gtk-CRITICAL **: gtk_image_menu_item_set_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(avant-window-navigator:12404): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(avant-window-navigator:12404): Wnck-CRITICAL **: wnck_window_is_maximized: assertion `WNCK_IS_WINDOW (window)' failed

(avant-window-navigator:12404): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkBin'

(avant-window-navigator:12404): Gtk-CRITICAL **: gtk_label_set_text: assertion `GTK_IS_LABEL (label)' failed

(avant-window-navigator:12404): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkBin'

(avant-window-navigator:12404): Gtk-CRITICAL **: gtk_label_set_use_underline: assertion `GTK_IS_LABEL (label)' failed

(avant-window-navigator:12404): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkImageMenuItem'

(avant-window-navigator:12404): Gtk-CRITICAL **: gtk_image_menu_item_get_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(avant-window-navigator:12404): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkImageMenuItem'

(avant-window-navigator:12404): Gtk-CRITICAL **: gtk_image_menu_item_set_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(avant-window-navigator:12404): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(avant-window-navigator:12404): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(avant-window-navigator:12404): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(avant-window-navigator:12404): GLib-GObject-CRITICAL **: g_signal_handlers_block_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(avant-window-navigator:12404): Wnck-CRITICAL **: wnck_window_is_above: assertion `WNCK_IS_WINDOW (window)' failed

(avant-window-navigator:12404): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkCheckMenuItem'

(avant-window-navigator:12404): Gtk-CRITICAL **: gtk_check_menu_item_set_active: assertion `GTK_IS_CHECK_MENU_ITEM (check_menu_item)' failed

(avant-window-navigator:12404): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(avant-window-navigator:12404): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(avant-window-navigator:12404): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(avant-window-navigator:12404): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(avant-window-navigator:12404): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(avant-window-navigator:12404): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(avant-window-navigator:12404): GLib-GObject-CRITICAL **: g_signal_handlers_block_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(avant-window-navigator:12404): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(avant-window-navigator:12404): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(avant-window-navigator:12404): GLib-GObject-CRITICAL **: g_signal_handlers_block_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(avant-window-navigator:12404): Wnck-CRITICAL **: wnck_window_is_pinned: assertion `WNCK_IS_WINDOW (window)' failed

(avant-window-navigator:12404): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkCheckMenuItem'

(avant-window-navigator:12404): Gtk-CRITICAL **: gtk_check_menu_item_set_active: assertion `GTK_IS_CHECK_MENU_ITEM (check_menu_item)' failed

(avant-window-navigator:12404): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(avant-window-navigator:12404): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(avant-window-navigator:12404): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(avant-window-navigator:12404): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(avant-window-navigator:12404): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'






Then how could I solve the problem???

---

### Post by eternalnewbee on 2008-11-14
Press **ALT-F2** enter ```
compiz --replace
``` Then try to run Awn again. Awn needs compiz to be able to run properly.
Hope this helps.

---

### Post by youxiang95 on 2008-11-18
I've allready run the compiz because I added the command "compiz --replace&" to the system->preference->session. Compiz was working well while the awn isn't!!

I installed the awn using deb like this "apt-get install avant-window-navigator". I heared that there's another awn called "awn-bzr". Then what is the difference between then??Shall I install the last one instead of the first one??

---

### Post by eternalnewbee on 2008-11-18
What you could try is go to: Main Menu > System > Administration > Synaptic Package Manager, and type awn in the searchbar and reinstall all the awn packages, and see if that solves it.

---

