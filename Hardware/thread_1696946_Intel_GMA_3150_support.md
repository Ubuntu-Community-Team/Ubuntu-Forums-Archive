---
title: "Intel GMA 3150 support?"
date: 2011-02-28
forum: Hardware
---

### Post by ojdon on 2011-02-28
Hi there,

I'm just wondering what the support is like for the Intel GMA 3150 chipset? I've got one for my Viewpad and once I first installed it, it was using "Normal" Visual Effects settings but I changed to "None" but now if I want to go back to "Normal" settings it keeps reverting me back to normal. 

How do I fix this issue?

---

### Post by ojdon on 2011-03-10
Bump! Anyone have any guidance?

---

### Post by Yellow Pasque on 2011-03-10
what is the output of:
```
sudo apt-get install mesa-utils
glxinfo
compiz --replace
```

---

### Post by easybuckroo on 2011-07-18
compiz --replace
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing scale options...done
Initializing session options...done
** (<unknown>:1871): DEBUG: Unity accessibility initialization
** (<unknown>:1871): DEBUG: Shows on edge: 1

Screen geometry changed:
  Monitor 0(primary)
   0x0x800x600

** (<unknown>:1871): DEBUG: PanelController:: Added Panel for Monitor 0
Initializing unityshell options...done
** (<unknown>:1871): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (<unknown>:1871): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (<unknown>:1871): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (<unknown>:1871): DEBUG: PlaceEntry: Applications
** (<unknown>:1871): DEBUG: PlaceEntry: Commands
** (<unknown>:1871): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:1871): DEBUG: /com/canonical/unity/applicationsplace
** (<unknown>:1871): DEBUG: /com/canonical/unity/filesplace
** (<unknown>:1871): DEBUG: Setting to primary screen rect: x=0 y=0 w=800 h=600

** (<unknown>:1871): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window58720917: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

** (<unknown>:1871): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus


** (<unknown>:1871): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window58721334: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:1871): WARNING **: Failed to fetch view type at /org/ayatana/bamf/application0xa0ff6c0: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:1871): WARNING **: Failed to fetch view type at /org/ayatana/bamf/application0xa0ff6c0: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


(<unknown>:1871): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (<unknown>:1871): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:1871): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:1871): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:1871): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:1871): DEBUG: IndicatorAdded: libme.so
** (<unknown>:1871): DEBUG: IndicatorAdded: libsession.so
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
** (<unknown>:1871): DEBUG: MaximizeIfBigEnough: Firefox window size doesn't fit
** (<unknown>:1871): DEBUG: Connected to proxy
** (<unknown>:1871): DEBUG: Connected to proxy
** (<unknown>:1871): DEBUG: Connected to proxy

(<unknown>:1871): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:1871): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:1871): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:1871): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:1871): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed

(<unknown>:1871): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed

---

