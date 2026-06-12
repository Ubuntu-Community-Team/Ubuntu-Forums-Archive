---
title: "[SOLVED] Deluge crashes after Sep16 upgrade"
date: 2008-09-16
forum: General Help
---

### Post by Dr.Ninethousand on 2008-09-16
today I upgraded Deluge at the prompting of update manager..

now Deluge crashes when I start it up, leaving just a gray box..

here is the terminal output, for someone that understands it better than myself:



```
rick@Kutulu:~$ deluge
[INFO    ] 14:45:18 main:93 Deluge ui 0.9.09
[DEBUG   ] 14:45:18 main:94 options: {'config': None, 'logfile': None, 'ui': None}
[DEBUG   ] 14:45:18 main:95 args: []
[DEBUG   ] 14:45:18 configmanager:44 ConfigManager started..
[INFO    ] 14:45:18 main:98 Starting ui..
[DEBUG   ] 14:45:18 ui:44 UI init..
[DEBUG   ] 14:45:18 configmanager:88 Getting config 'ui.conf'
[DEBUG   ] 14:45:18 config:47 Config created with filename: ui.conf
[DEBUG   ] 14:45:18 config:48 Config defaults: {'default_ui': 'gtk'}
[INFO    ] 14:45:18 ui:60 Starting GtkUI..
[DEBUG   ] 14:45:18 client:54 CoreProxy init..
[DEBUG   ] 14:45:18 configmanager:69 get_config_dir: /home/rick/.config/deluge
[DEBUG   ] 14:45:18 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:18 config:47 Config created with filename: gtkui.conf
[DEBUG   ] 14:45:18 config:48 Config defaults: {'autoadd_queued': False, 'close_to_tray': True, 'window_width': 640, 'default_load_path': None, 'window_y_pos': 0, 'classic_mode': True, 'window_pane_position': -1, 'enabled_plugins': [], 'show_connection_manager_on_start': True, 'show_statusbar': True, 'autoadd_enable': False, 'tray_download_speed_list': [5.0, 10.0, 30.0, 80.0, 300.0], 'autoconnect_host_uri': None, 'window_maximized': False, 'enable_system_tray': True, 'show_sidebar': True, 'window_x_pos': 0, 'window_height': 480, 'lock_tray': False, 'connection_limit_list': [50, 100, 200, 300, 500], 'tray_password': '', 'focus_add_dialog': True, 'show_new_releases': True, 'start_in_tray': False, 'autoconnect': False, 'choose_directory_dialog_path': '/home/rick', 'check_new_releases': True, 'autostart_localhost': False, 'show_toolbar': True, 'autoadd_location': '', 'config_location': '/home/rick/.config/deluge', 'tray_upload_speed_list': [5.0, 10.0, 30.0, 80.0, 300.0], 'interactive_add': True, 'signal_port': 40000}
0.9.09
[DEBUG   ] 14:45:18 gtkui:165 retcode: 0
[DEBUG   ] 14:45:18 component:102 Registered QueuedTorrents with ComponentRegistry..
[DEBUG   ] 14:45:18 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:18 component:102 Registered IPCInterface with ComponentRegistry..
[DEBUG   ] 14:45:18 component:102 Registered DbusInterface with ComponentRegistry..
[DEBUG   ] 14:45:18 ipcinterface:83 Processing args from other process: []
[DEBUG   ] 14:45:18 ipcinterface:86 Not connected to host.. Adding to queue.
[INFO    ] 14:45:18 dbusinterface:82 Registering with DBUS..
[DEBUG   ] 14:45:18 component:102 Registered MainWindow with ComponentRegistry..
[DEBUG   ] 14:45:18 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:18 mainwindow:84 Showing window
[DEBUG   ] 14:45:19 menubar:49 MenuBar init..
[DEBUG   ] 14:45:19 component:102 Registered MenuBar with ComponentRegistry..
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:19 component:102 Registered ToolBar with ComponentRegistry..
[DEBUG   ] 14:45:19 toolbar:48 ToolBar Init..
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
/var/lib/python-support/python2.5/deluge/ui/gtkui/toolbar.py:77: GtkWarning: gtk_menu_attach_to_widget(): menu already attached to GtkImageMenuItem
  component.get("MenuBar").torrentmenu_glade.get_widget("remove_torrent_menu"))
[DEBUG   ] 14:45:19 component:102 Registered TorrentView with ComponentRegistry..
[DEBUG   ] 14:45:19 listview:124 ListView initialized..
[DEBUG   ] 14:45:19 torrentview:110 TorrentView Init..
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:19 listview:193 Loading ListView state file: torrentview.state
[WARNING ] 14:45:19 listview:198 Unable to load state file: [Errno 2] No such file or directory: '/home/rick/.config/deluge/torrentview.state'
[DEBUG   ] 14:45:19 component:102 Registered TorrentDetails with ComponentRegistry..
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:19 torrentdetails:384 Loading TorrentDetails state file: tabs.state
[WARNING ] 14:45:19 torrentdetails:389 Unable to load state file: [Errno 2] No such file or directory: '/home/rick/.config/deluge/tabs.state'
[DEBUG   ] 14:45:19 torrentdetails:65 parent: None
[DEBUG   ] 14:45:19 torrentdetails:65 parent: None
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:19 files_tab:216 Loading FilesTab state file: files_tab.state
[WARNING ] 14:45:19 files_tab:221 Unable to load state file: [Errno 2] No such file or directory: '/home/rick/.config/deluge/files_tab.state'
[DEBUG   ] 14:45:19 torrentdetails:65 parent: None
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:19 peers_tab:176 Loading PeersTab state file: peers_tab.state
[WARNING ] 14:45:19 peers_tab:181 Unable to load state file: [Errno 2] No such file or directory: '/home/rick/.config/deluge/peers_tab.state'
[DEBUG   ] 14:45:19 torrentdetails:65 parent: None
[DEBUG   ] 14:45:19 torrentdetails:65 parent: None
[DEBUG   ] 14:45:19 component:102 Registered SideBar with ComponentRegistry..
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:19 component:102 Registered Preferences with ComponentRegistry..
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:19 component:102 Registered SystemTray with ComponentRegistry..
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:19 config:158 Registering function for enable_system_tray key..
[DEBUG   ] 14:45:19 systemtray:76 Enabling the system tray icon..
[DEBUG   ] 14:45:19 component:102 Registered StatusBar with ComponentRegistry..
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:19 component:102 Registered AddTorrentDialog with ComponentRegistry..
[DEBUG   ] 14:45:19 component:102 Registered Signals with ComponentRegistry..
[DEBUG   ] 14:45:19 signalreceiver:52 SignalReceiver init..
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:19 config:117 Setting 'signal_port' to 46718 of <type 'int'>
[DEBUG   ] 14:45:19 coreconfig:40 CoreConfig init..
[DEBUG   ] 14:45:19 component:102 Registered CoreConfig with ComponentRegistry..
[DEBUG   ] 14:45:19 component:102 Registered PluginManager with ComponentRegistry..
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:19 pluginmanagerbase:48 Plugin manager init..
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:19 configmanager:69 get_config_dir: /home/rick/.config/deluge
[DEBUG   ] 14:45:19 pluginmanagerbase:95 Found plugin: Blocklist 1.0
[DEBUG   ] 14:45:19 pluginmanagerbase:95 Found plugin: Label 0.1
[DEBUG   ] 14:45:19 component:102 Registered ConnectionManager with ComponentRegistry..
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'hostlist.conf'
[DEBUG   ] 14:45:19 config:47 Config created with filename: hostlist.conf
[DEBUG   ] 14:45:19 config:48 Config defaults: {'hosts': ['localhost:58846']}
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
Killed
rick@Kutulu:~$ 

```

---

### Post by TNA5000 on 2008-09-16
I am experiencing the same issue on hardy.

Anyone know how to start deluge with debug?

---

### Post by mb_webguy on 2008-09-16
I realize that this doesn't quite address your problem, but I'm using the latest version (1.0.0_RC9 or 0.9.09-1) from the [Deluge website]("http://deluge-torrent.org/") and it's working just fine.  

The only disadvantage I see with the release candidates is that so far they lack the plugin support of the older releases, since version 1.0 will use a different plugin system.  The blocklist plugin is currently the only one available.

---

### Post by kostkon on 2008-09-16
> **Dr.Ninethousand said:**
> today I upgraded Deluge at the prompting of update manager..

now Deluge crashes when I start it up, leaving just a gray box..

here is the terminal output, for someone that understands it better than myself:



```
rick@Kutulu:~$ deluge
[INFO    ] 14:45:18 main:93 Deluge ui 0.9.09
[DEBUG   ] 14:45:18 main:94 options: {'config': None, 'logfile': None, 'ui': None}
[DEBUG   ] 14:45:18 main:95 args: []
[DEBUG   ] 14:45:18 configmanager:44 ConfigManager started..
[INFO    ] 14:45:18 main:98 Starting ui..
[DEBUG   ] 14:45:18 ui:44 UI init..
[DEBUG   ] 14:45:18 configmanager:88 Getting config 'ui.conf'
[DEBUG   ] 14:45:18 config:47 Config created with filename: ui.conf
[DEBUG   ] 14:45:18 config:48 Config defaults: {'default_ui': 'gtk'}
[INFO    ] 14:45:18 ui:60 Starting GtkUI..
[DEBUG   ] 14:45:18 client:54 CoreProxy init..
[DEBUG   ] 14:45:18 configmanager:69 get_config_dir: /home/rick/.config/deluge
[DEBUG   ] 14:45:18 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:18 config:47 Config created with filename: gtkui.conf
[DEBUG   ] 14:45:18 config:48 Config defaults: {'autoadd_queued': False, 'close_to_tray': True, 'window_width': 640, 'default_load_path': None, 'window_y_pos': 0, 'classic_mode': True, 'window_pane_position': -1, 'enabled_plugins': [], 'show_connection_manager_on_start': True, 'show_statusbar': True, 'autoadd_enable': False, 'tray_download_speed_list': [5.0, 10.0, 30.0, 80.0, 300.0], 'autoconnect_host_uri': None, 'window_maximized': False, 'enable_system_tray': True, 'show_sidebar': True, 'window_x_pos': 0, 'window_height': 480, 'lock_tray': False, 'connection_limit_list': [50, 100, 200, 300, 500], 'tray_password': '', 'focus_add_dialog': True, 'show_new_releases': True, 'start_in_tray': False, 'autoconnect': False, 'choose_directory_dialog_path': '/home/rick', 'check_new_releases': True, 'autostart_localhost': False, 'show_toolbar': True, 'autoadd_location': '', 'config_location': '/home/rick/.config/deluge', 'tray_upload_speed_list': [5.0, 10.0, 30.0, 80.0, 300.0], 'interactive_add': True, 'signal_port': 40000}
0.9.09
[DEBUG   ] 14:45:18 gtkui:165 retcode: 0
[DEBUG   ] 14:45:18 component:102 Registered QueuedTorrents with ComponentRegistry..
[DEBUG   ] 14:45:18 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:18 component:102 Registered IPCInterface with ComponentRegistry..
[DEBUG   ] 14:45:18 component:102 Registered DbusInterface with ComponentRegistry..
[DEBUG   ] 14:45:18 ipcinterface:83 Processing args from other process: []
[DEBUG   ] 14:45:18 ipcinterface:86 Not connected to host.. Adding to queue.
[INFO    ] 14:45:18 dbusinterface:82 Registering with DBUS..
[DEBUG   ] 14:45:18 component:102 Registered MainWindow with ComponentRegistry..
[DEBUG   ] 14:45:18 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:18 mainwindow:84 Showing window
[DEBUG   ] 14:45:19 menubar:49 MenuBar init..
[DEBUG   ] 14:45:19 component:102 Registered MenuBar with ComponentRegistry..
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:19 component:102 Registered ToolBar with ComponentRegistry..
[DEBUG   ] 14:45:19 toolbar:48 ToolBar Init..
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
/var/lib/python-support/python2.5/deluge/ui/gtkui/toolbar.py:77: GtkWarning: gtk_menu_attach_to_widget(): menu already attached to GtkImageMenuItem
  component.get("MenuBar").torrentmenu_glade.get_widget("remove_torrent_menu"))
[DEBUG   ] 14:45:19 component:102 Registered TorrentView with ComponentRegistry..
[DEBUG   ] 14:45:19 listview:124 ListView initialized..
[DEBUG   ] 14:45:19 torrentview:110 TorrentView Init..
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:19 listview:193 Loading ListView state file: torrentview.state
[WARNING ] 14:45:19 listview:198 Unable to load state file: [Errno 2] No such file or directory: '/home/rick/.config/deluge/torrentview.state'
[DEBUG   ] 14:45:19 component:102 Registered TorrentDetails with ComponentRegistry..
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:19 torrentdetails:384 Loading TorrentDetails state file: tabs.state
[WARNING ] 14:45:19 torrentdetails:389 Unable to load state file: [Errno 2] No such file or directory: '/home/rick/.config/deluge/tabs.state'
[DEBUG   ] 14:45:19 torrentdetails:65 parent: None
[DEBUG   ] 14:45:19 torrentdetails:65 parent: None
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:19 files_tab:216 Loading FilesTab state file: files_tab.state
[WARNING ] 14:45:19 files_tab:221 Unable to load state file: [Errno 2] No such file or directory: '/home/rick/.config/deluge/files_tab.state'
[DEBUG   ] 14:45:19 torrentdetails:65 parent: None
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:19 peers_tab:176 Loading PeersTab state file: peers_tab.state
[WARNING ] 14:45:19 peers_tab:181 Unable to load state file: [Errno 2] No such file or directory: '/home/rick/.config/deluge/peers_tab.state'
[DEBUG   ] 14:45:19 torrentdetails:65 parent: None
[DEBUG   ] 14:45:19 torrentdetails:65 parent: None
[DEBUG   ] 14:45:19 component:102 Registered SideBar with ComponentRegistry..
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:19 component:102 Registered Preferences with ComponentRegistry..
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:19 component:102 Registered SystemTray with ComponentRegistry..
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:19 config:158 Registering function for enable_system_tray key..
[DEBUG   ] 14:45:19 systemtray:76 Enabling the system tray icon..
[DEBUG   ] 14:45:19 component:102 Registered StatusBar with ComponentRegistry..
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:19 component:102 Registered AddTorrentDialog with ComponentRegistry..
[DEBUG   ] 14:45:19 component:102 Registered Signals with ComponentRegistry..
[DEBUG   ] 14:45:19 signalreceiver:52 SignalReceiver init..
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:19 config:117 Setting 'signal_port' to 46718 of <type 'int'>
[DEBUG   ] 14:45:19 coreconfig:40 CoreConfig init..
[DEBUG   ] 14:45:19 component:102 Registered CoreConfig with ComponentRegistry..
[DEBUG   ] 14:45:19 component:102 Registered PluginManager with ComponentRegistry..
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:19 pluginmanagerbase:48 Plugin manager init..
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 14:45:19 configmanager:69 get_config_dir: /home/rick/.config/deluge
[DEBUG   ] 14:45:19 pluginmanagerbase:95 Found plugin: Blocklist 1.0
[DEBUG   ] 14:45:19 pluginmanagerbase:95 Found plugin: Label 0.1
[DEBUG   ] 14:45:19 component:102 Registered ConnectionManager with ComponentRegistry..
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'hostlist.conf'
[DEBUG   ] 14:45:19 config:47 Config created with filename: hostlist.conf
[DEBUG   ] 14:45:19 config:48 Config defaults: {'hosts': ['localhost:58846']}
[DEBUG   ] 14:45:19 configmanager:88 Getting config 'gtkui.conf'
Killed
rick@Kutulu:~$ 

```

> **TNA5000 said:**
> I am experiencing the same issue on hardy.

Anyone know how to start deluge with debug?
You can find the log of the Deluge daemon in 
```
~/.config/deluge/deluged.log
```

It is better to post here the contents of this file.

---

### Post by Dr.Ninethousand on 2008-09-16
here's my deluged.log


```
[DEBUG   ] 15:21:52 configmanager:44 ConfigManager started..
[INFO    ] 15:21:52 daemon:44 Deluge daemon 0.9.09
[DEBUG   ] 15:21:52 daemon:45 options: {'logfile': None, 'config': None, 'port': 58846, 'donot': False}
[DEBUG   ] 15:21:52 daemon:46 args: []
Traceback (most recent call last):
  File "/usr/bin/deluged", line 8, in <module>
    load_entry_point('deluge==0.9.09', 'console_scripts', 'deluged')()
  File "/var/lib/python-support/python2.5/deluge/main.py", line 169, in start_daemon
    Daemon(options, args)
  File "/var/lib/python-support/python2.5/deluge/core/daemon.py", line 50, in __init__
    from deluge.core.core import Core
  File "/var/lib/python-support/python2.5/deluge/core/core.py", line 49, in <module>
    import deluge.libtorrent as lt
ImportError: libboost_iostreams-gcc42-1_34_1.so.1.34.1: cannot open shared object file: No such file or directory


```

---

### Post by kostkon on 2008-09-16
> **Dr.Ninethousand said:**
> here's my deluged.log


```
[DEBUG   ] 15:21:52 configmanager:44 ConfigManager started..
[INFO    ] 15:21:52 daemon:44 Deluge daemon 0.9.09
[DEBUG   ] 15:21:52 daemon:45 options: {'logfile': None, 'config': None, 'port': 58846, 'donot': False}
[DEBUG   ] 15:21:52 daemon:46 args: []
Traceback (most recent call last):
  File "/usr/bin/deluged", line 8, in <module>
    load_entry_point('deluge==0.9.09', 'console_scripts', 'deluged')()
  File "/var/lib/python-support/python2.5/deluge/main.py", line 169, in start_daemon
    Daemon(options, args)
  File "/var/lib/python-support/python2.5/deluge/core/daemon.py", line 50, in __init__
    from deluge.core.core import Core
  File "/var/lib/python-support/python2.5/deluge/core/core.py", line 49, in <module>
    import deluge.libtorrent as lt
ImportError: libboost_iostreams-gcc42-1_34_1.so.1.34.1: cannot open shared object file: No such file or directory


```
OK, easy solution. You have to install the *libboost-iostreams1.34.1* package (from **Synaptic**). For some reason the packager did not specify this dependency so it is not installed automatically.

---

### Post by Dr.Ninethousand on 2008-09-16
hmm that seems to have changed nothing, including the terminal output and log..   :/

---

### Post by kostkon on 2008-09-16
> **Dr.Ninethousand said:**
> hmm that seems to have changed nothing, including the terminal output and log..   :/
Are you sure? Could you try to run it again and post the new output of the deluged.log log file here?

Before runnning it, it is important to check that the *Deluge* deamon (an old one) is not running already. Go to *System -> Administration -> System Monitor* and kill any *Deluge* related processes you'll see.

Then run it again and check the log.

The new *Deluge* consists of a GUI frontend that connects to a daemon which actually does all the work.

---

### Post by Dr.Ninethousand on 2008-09-16
ok it seems you were close..  I installed libboost-python1.34.1 and now it seems to be working..

I didn't kill any processes so it's possible you were right..  what I did was go and get the .deb from the Deluge site, and when I started to install it it said it needed to also install the libboost-python package..  so I just exited and went to Synaptic for that package instead..

---

### Post by kostkon on 2008-09-16
> **Dr.Ninethousand said:**
> ok it seems you were close..  I installed libboost-python1.34.1 and now it seems to be working..
OK, nice :)
> **Dr.Ninethousand said:**
> I didn't kill any processes so it's possible you were right.. what I did was go and get the .deb from the Deluge site, and when I started to install it it said it needed to also install the libboost-python package.. so I just exited and went to Synaptic for that package instead..
Hmmm, I see. It's clear then that the package offered by the repo fails to fetch some necessary dependencies, I may fill a bug report.

---

### Post by TNA5000 on 2008-09-16
Alright, i can confirm as well, installing libboost-iostreams1.34.1 and libboost-python1.34.1 does fix it.

Thanks a bunch.

---

### Post by itkeepsrepeating on 2008-09-24
I think i'm having a similar problem, however I already have both the libboost packages mentioned installed. I am trying to run deluge v 1.0.0-1. Here are the contents of my ~/.config/deluge/deluged.log:

[DEBUG   ] 16:20:39 configmanager:44 ConfigManager started..
[INFO    ] 16:20:39 daemon:44 Deluge daemon 1.0.0
[DEBUG   ] 16:20:39 daemon:45 options: {'logfile': None, 'config': None, 'port': 58846, 'donot': False}
[DEBUG   ] 16:20:39 daemon:46 args: []
[DEBUG   ] 16:20:40 configmanager:69 get_config_dir: /home/tatertom/.config/deluge
[DEBUG   ] 16:20:40 configmanager:69 get_config_dir: /home/tatertom/.config/deluge
[DEBUG   ] 16:20:40 configmanager:69 get_config_dir: /home/tatertom/.config/deluge
[DEBUG   ] 16:20:40 core:121 Core init..
[DEBUG   ] 16:20:40 component:102 Registered Core with ComponentRegistry..
[DEBUG   ] 16:20:40 configmanager:88 Getting config 'core.conf'
[DEBUG   ] 16:20:40 config:47 Config created with filename: core.conf
[DEBUG   ] 16:20:40 config:48 Config defaults: {'info_sent': 0.0, 'lsd': True, 'max_download_speed': -1.0, 'send_info': False, 'torrentfiles_location': '/home/tatertom', 'state_location': '/home/tatertom/.config/deluge/state', 'stop_seed_at_ratio': False, 'max_active_limit': 8, 'enc_in_policy': 1, 'queue_new_to_top': False, 'ignore_limits_on_local_network': True, 'daemon_port': 58846, 'natpmp': True, 'autoadd_enable': False, 'upnp': True, 'utpex': True, 'max_download_speed_per_torrent': -1, 'max_active_seeding': 5, 'allow_remote': False, 'max_half_open_connections': -1, 'enabled_plugins': [], 'plugins_location': '/home/tatertom/.config/deluge/plugins', 'download_location': '/home/tatertom', 'compact_allocation': False, 'max_upload_speed': -1.0, 'max_connections_global': -1, 'enc_prefer_rc4': True, 'listen_ports': [6881, 6891], 'dht': True, 'move_completed_path': '/home/tatertom', 'stop_seed_ratio': 2.0, 'max_active_downloading': 3, 'prioritize_first_last_pieces': False, 'max_upload_speed_per_torrent': -1, 'auto_managed': True, 'enc_level': 2, 'copy_torrent_file': False, 'max_connections_per_second': -1, 'max_connections_per_torrent': -1, 'move_completed': False, 'dont_count_slow_torrents': False, 'add_paused': False, 'max_upload_slots_per_torrent': -1, 'new_release_check': True, 'enc_out_policy': 1, 'seed_time_ratio_limit': 7.0, 'remove_seed_at_ratio': False, 'autoadd_location': '/home/tatertom', 'max_upload_slots_global': -1, 'config_location': '/home/tatertom/.config/deluge', 'seed_time_limit': 180, 'share_ratio_limit': 2.0, 'random_port': True}
[INFO    ] 16:20:40 core:138 Starting XMLRPC server on port 58846
[DEBUG   ] 16:20:40 core:209 Starting libtorrent session..
[DEBUG   ] 16:20:40 config:158 Registering function for torrentfiles_location key..
[DEBUG   ] 16:20:40 config:158 Registering function for state_location key..
[DEBUG   ] 16:20:40 config:158 Registering function for listen_ports key..
[DEBUG   ] 16:20:40 config:158 Registering function for random_port key..
[DEBUG   ] 16:20:40 core:735 random port value set to True
[DEBUG   ] 16:20:40 core:749 listen port range set to 56579-56589
[DEBUG   ] 16:20:40 config:158 Registering function for dht key..
[DEBUG   ] 16:20:40 core:753 dht value set to True
[DEBUG   ] 16:20:40 config:158 Registering function for upnp key..
[DEBUG   ] 16:20:40 core:763 upnp value set to True
[DEBUG   ] 16:20:40 config:158 Registering function for natpmp key..
[DEBUG   ] 16:20:40 core:770 natpmp value set to True
[DEBUG   ] 16:20:40 config:158 Registering function for utpex key..
[DEBUG   ] 16:20:40 core:784 utpex value set to True
[DEBUG   ] 16:20:40 config:158 Registering function for lsd key..
[DEBUG   ] 16:20:40 core:777 lsd value set to True
[DEBUG   ] 16:20:40 config:158 Registering function for enc_in_policy key..
[DEBUG   ] 16:20:40 core:789 encryption value enc_in_policy set to 1..
[DEBUG   ] 16:20:40 core:803 encryption settings:
			out_policy: enabled
		        in_policy: enabled
			level: both
			prefer_rc4: True
[DEBUG   ] 16:20:40 config:158 Registering function for enc_out_policy key..
[DEBUG   ] 16:20:40 core:789 encryption value enc_out_policy set to 1..
[DEBUG   ] 16:20:40 core:803 encryption settings:
			out_policy: enabled
		        in_policy: enabled
			level: both
			prefer_rc4: True
[DEBUG   ] 16:20:40 config:158 Registering function for enc_level key..
[DEBUG   ] 16:20:40 core:789 encryption value enc_level set to 2..
[DEBUG   ] 16:20:40 core:803 encryption settings:
			out_policy: enabled
		        in_policy: enabled
			level: both
			prefer_rc4: True
[DEBUG   ] 16:20:40 config:158 Registering function for enc_prefer_rc4 key..
[DEBUG   ] 16:20:40 core:789 encryption value enc_prefer_rc4 set to True..
[DEBUG   ] 16:20:40 core:803 encryption settings:
			out_policy: enabled
		        in_policy: enabled
			level: both
			prefer_rc4: True
[DEBUG   ] 16:20:40 config:158 Registering function for max_connections_global key..
[DEBUG   ] 16:20:40 core:806 max_connections_global set to 150.0..
Traceback (most recent call last):
  File "/usr/bin/deluged", line 8, in <module>
    load_entry_point('deluge==1.0.0', 'console_scripts', 'deluged')()
  File "/var/lib/python-support/python2.5/deluge/main.py", line 169, in start_daemon
    Daemon(options, args)
  File "/var/lib/python-support/python2.5/deluge/core/daemon.py", line 52, in __init__
    self.core = Core(options.port).run()
  File "/var/lib/python-support/python2.5/deluge/core/core.py", line 251, in run
    self._on_set_max_connections_global)
  File "/var/lib/python-support/python2.5/deluge/config.py", line 162, in register_set_function
    self.set_functions[key](key, self.config[key])
  File "/var/lib/python-support/python2.5/deluge/core/core.py", line 807, in _on_set_max_connections_global
    self.session.set_max_connections(value)
Boost.Python.ArgumentError: Python argument types in
    session.set_max_connections(session, float)
did not match C++ signature:
    set_max_connections(libtorrent::session {lvalue}, int)


Any help appreciated. 

/Sidenote: If I can, I'd like to run a 9.x version, which is more compatible with the tracker I've registered with. So if anyone has some not-quite n00b instructs to get that running, it would also be appreciated.

---

