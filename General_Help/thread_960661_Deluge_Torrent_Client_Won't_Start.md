---
title: "Deluge Torrent Client Won't Start"
date: 2008-10-27
forum: General Help
---

### Post by EnigMattic on 2008-10-27
I'm running Ubuntu Intrepid (Release Candidate) amd64 and Deluge (version 1.0.3 from getdeb.net and the version from the repo) won't start at all.

Here's the terminal output:
```
:~$ deluge
[INFO    ] 20:23:33 main:93 Deluge ui 1.0.3
[DEBUG   ] 20:23:33 main:94 options: {'config': None, 'logfile': None, 'ui': None}
[DEBUG   ] 20:23:33 main:95 args: []
[DEBUG   ] 20:23:33 configmanager:44 ConfigManager started..
[INFO    ] 20:23:33 main:98 Starting ui..
[DEBUG   ] 20:23:33 ui:44 UI init..
[DEBUG   ] 20:23:33 configmanager:88 Getting config 'ui.conf'
[DEBUG   ] 20:23:33 config:47 Config created with filename: ui.conf
[DEBUG   ] 20:23:33 config:48 Config defaults: {'default_ui': 'gtk'}
[INFO    ] 20:23:33 ui:60 Starting GtkUI..
[DEBUG   ] 20:23:33 client:54 CoreProxy init..
[DEBUG   ] 20:23:33 configmanager:69 get_config_dir: /home/matthew/.config/deluge
[DEBUG   ] 20:23:33 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 20:23:33 config:47 Config created with filename: gtkui.conf
[DEBUG   ] 20:23:33 config:48 Config defaults: {'autoadd_queued': False, 'close_to_tray': True, 'window_width': 640, 'default_load_path': None, 'window_y_pos': 0, 'classic_mode': True, 'window_pane_position': -1, 'enabled_plugins': [], 'show_connection_manager_on_start': True, 'show_statusbar': True, 'autoadd_enable': False, 'tray_download_speed_list': [5.0, 10.0, 30.0, 80.0, 300.0], 'autoconnect_host_uri': None, 'window_maximized': False, 'enable_system_tray': True, 'show_sidebar': True, 'window_x_pos': 0, 'window_height': 480, 'lock_tray': False, 'connection_limit_list': [50, 100, 200, 300, 500], 'tray_password': '', 'focus_add_dialog': True, 'show_new_releases': True, 'start_in_tray': False, 'autoconnect': False, 'choose_directory_dialog_path': '/home/matthew', 'check_new_releases': True, 'autostart_localhost': False, 'show_toolbar': True, 'autoadd_location': '', 'config_location': '/home/matthew/.config/deluge', 'tray_upload_speed_list': [5.0, 10.0, 30.0, 80.0, 300.0], 'interactive_add': True, 'signal_port': 40000}
1.0.3
[DEBUG   ] 20:23:33 gtkui:165 retcode: 0
[DEBUG   ] 20:23:33 component:102 Registered QueuedTorrents with ComponentRegistry..
[DEBUG   ] 20:23:33 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 20:23:33 component:102 Registered IPCInterface with ComponentRegistry..
[DEBUG   ] 20:23:33 component:102 Registered DbusInterface with ComponentRegistry..
[INFO    ] 20:23:33 dbusinterface:59 Deluge already running..
[DEBUG   ] 20:23:33 dbusinterface:60 args: []
[DEBUG   ] 20:23:33 dbusinterface:76 Exiting..
```

Any help appreciated! Thanks!

---

