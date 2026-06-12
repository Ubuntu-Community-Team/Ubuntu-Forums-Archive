---
title: "Running Gnome-do"
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by spursncowboys on 2009-10-04
I installed gnome-do on my xubuntu. 
```
 $gnome-do
[Error 17:33:39.502] Missing login credentials. Please set login information in plugin configuration.

(Do:4599): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.

Microblogging.FriendSource "Microblog friends" encountered an error in Items: Object reference not set to an instance of an object.
Microblogging.FriendSource "Microblog friends" encountered an error in Items: Object reference not set to an instance of an object.
Firefox.PlacesItemSource "Firefox Places" encountered an error in UpdateItems: Object reference not set to an instance of an object.
[Debug 17:33:41.784] Acquiring org.freedesktop.DBus session instance
[Debug 17:33:41.839] Starting org.bansheeproject.CollectionIndexer

Unhandled Exception: System.Exception: org.freedesktop.DBus.Error.ServiceUnknown: The name org.bansheeproject.CollectionIndexer was not provided by any .service files
  at IBusProxy.StartServiceByName (System.String flags, UInt32 ) [0x00000] 
  at NDesk.DBus.Bus.StartServiceByName (System.String name, UInt32 flags) [0x00000] 
  at NDesk.DBus.Bus.StartServiceByName (System.String name) [0x00000] 
  at Banshee.Collection.Indexer.RemoteHelper.IndexerClient.Start () [0x00000] 
  at Banshee.Collection.Indexer.RemoteHelper.SimpleIndexerClient.Start () [0x00000] 

```The gnome-do will pop up and then crash.

---

