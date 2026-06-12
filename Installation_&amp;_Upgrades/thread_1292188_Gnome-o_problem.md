---
title: "Gnome-o problem"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by hariks0 on 2009-10-15
I am not able to use Gnome-Do. It appears after 5 seconds of click and disappears. The terminal out put is as follows:-

hari@Indira:~$ gnome-do
Could not read MPD database file: ApplicationName='/usr/bin/mpc', CommandLine='playlist --format ":%title%:%artist%:%album%:%file%"', CurrentDirectory=''
SqueezeCenter: Error connecting to server localhost:9090. Retrying in 30 seconds.You may want to adjust the settings in the SqueezeCenter configuration dialog.
Cannot index Thunderbird contacts because a System.ArgumentNullException was thrown: Argument cannot be null.
Parameter name: path
Could not read Bibtex file: Could not find file "/home/hari/bibtex.bib".
[Error 00:47:01.997] Missing login credentials. Please set login information in plugin configuration.
Could not locate Skype on D-Bus. Make sure Skype is running
Could not locate Skype on D-Bus. Make sure Skype is running
Could not locate Skype on D-Bus. Make sure Skype is running
[Info 00:47:02.092] [JIRA] Configuration for JIRA is not valid, see the plugin settings page

(Do:2484): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.

Could not read MPD database file: ApplicationName='/usr/bin/mpc', CommandLine='playlist --format ":%title%:%artist%:%album%:%file%"', CurrentDirectory=''
[Error 00:47:02.613] [Youtube] Missing login credentials. Please set login information in YouTube plugin configuration.
[Error 00:47:02.623] [Youtube] Error getting favorites videos - Object reference not set to an instance of an object
[Error 00:47:02.630] [Youtube] Error getting subscriptions - Object reference not set to an instance of an object
[Error 00:47:02.630] [Youtube] Error getting own videos - Object reference not set to an instance of an object
Could not locate Tomboy on D-Bus. Perhaps it's not running?
Cannot index Thunderbird contacts because a System.ArgumentNullException was thrown: Argument cannot be null.
Parameter name: path
Could not read Bibtex file: Could not find file "/home/hari/bibtex.bib".
[Error 00:47:02.853] [RTM] Not authorized to use a Remember The Milk account.
[Error 00:47:02.864] [RTM] Not authorized to use a Remember The Milk account.
[Error 00:47:02.865] [RTM] Not authorized to use a Remember The Milk account.
[Error 00:47:02.866] [RTM] Not authorized to use a Remember The Milk account.
Microblogging.FriendSource "Microblog friends" encountered an error in Items: Object reference not set to an instance of an object.
Microblogging.FriendSource "Microblog friends" encountered an error in Items: Object reference not set to an instance of an object.
[Error 00:47:02.899] [PidginContactItemSource] Error reading Pidgin buddy list file: Could not find a part of the path "/home/hari/.purple/blist.xml".
[Error 00:47:03.059] [TSClientItemSource] Could not open directory '/home/hari/.tsclient'
[Debug 00:47:03.076] Acquiring org.freedesktop.DBus session instance
[Debug 00:47:03.077] Starting org.bansheeproject.CollectionIndexer

Unhandled Exception: System.Exception: org.freedesktop.DBus.Error.ServiceUnknown: The name org.bansheeproject.CollectionIndexer was not provided by any .service files
  at IBusProxy.StartServiceByName (System.String flags, UInt32 ) [0x00000] 
  at NDesk.DBus.Bus.StartServiceByName (System.String name, UInt32 flags) [0x00000] 
  at NDesk.DBus.Bus.StartServiceByName (System.String name) [0x00000] 
  at Banshee.Collection.Indexer.RemoteHelper.IndexerClient.Start () [0x00000] 
  at Banshee.Collection.Indexer.RemoteHelper.SimpleIndexerClient.Start () [0x00000] 
hari@Indira:~$ 

Other users of the PC are able to use Gnome-Do. Any help will be highly appreciated.

---

### Post by afrodeity on 2010-05-25
apparently something to do with weather and gmail plugins. upgrade to gnome-do 2

---

