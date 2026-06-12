---
title: "App Upgrade Question"
date: 2008-09-22
forum: General Help
---

### Post by smith_fan on 2008-09-22
I am wanting to upgrade my Deluge client to a Release Version, but am not sure how to do so.  The version of the currently running one on here is Deluge 0.5.8.9.  I downloaded v0.9.09-1_i386.hardy.deb, but I got an error message when I tried to install it.

I am still pretty green when it comes to his linux stuff and I'm unsure what the problem is.

“Marking Upgrades” in Synaptic didn't get me anywhere when I tried that first and I don't want to lose what it's already got in a HUGE download by uninstalling.

Will someone please give me an idea of what I need to do to get it upgraded successfully?

Thanks!,
~D~

---

### Post by kostkon on 2008-09-22
> **smith_fan said:**
> I am wanting to upgrade my Deluge client to a Release Version, but am not sure how to do so.  The version of the currently running one on here is Deluge 0.5.8.9.  I downloaded v0.9.09-1_i386.hardy.deb, but I got an error message when I tried to install it.

I am still pretty green when it comes to his linux stuff and I'm unsure what the problem is.

“Marking Upgrades” in Synaptic didn't get me anywhere when I tried that first and I don't want to lose what it's already got in a HUGE download by uninstalling.

Will someone please give me an idea of what I need to do to get it upgraded successfully?

Thanks!,
~D~
Assuming that you use 8.04 then you can use the [*PPA* for *Deluge*]("https://launchpad.net/~deluge-team/+archive"). It will allow you to install the latest version (1.0.0) and you will get update notifications in *Ubuntu* every time there is a new version.

You have to add *Deluge*'s repository to your software sources list. Thus, go to *System -> Administration -> Software Sources* and in the *Third Party Software* tab press the *Add* button and put the following line
```
deb http://ppa.launchpad.net/deluge-team/ubuntu hardy main
```
After doing this you will get an update notification in *Ubuntu* to install the latest version. And from now on, you will get a notification every time there is a new version of *Deluge*.

---

### Post by smith_fan on 2008-09-22
Beautiful! :-D  Sank you very much!:)

---

### Post by smith_fan on 2008-09-22
Unfortunately, I've hit a snag. :icon_frown:   (It seems as though that is always the case, in my experience with linux) :-x

Per your instruction, I added to my repositories.  It all went smoothly until the next time I tried to open Deluge.  Now, it's window *greys-out* like it's trying to finish-up doing something.

Fixing broken packages via Synaptic hasn't helped any.

It never indicated any problems.  It just stopped working following a reboot.

Got any ideas?:confused:

Thanks!,
~D~

---

### Post by mb_webguy on 2008-09-22
I just upgraded to Deluge 1.0.0 using the deb from the Deluge website, and everything worked fine.  Make sure you don't have Deluge running when you try to install.  It technically shouldn't matter, but sometimes it seems to.

---

### Post by kostkon on 2008-09-22
> **smith_fan said:**
> Unfortunately, I've hit a snag. :icon_frown:   (It seems as though that is always the case, in my experience with linux) :-x

Per your instruction, I added to my repositories.  It all went smoothly until the next time I tried to open Deluge.  Now, it's window *greys-out* like it's trying to finish-up doing something.

Fixing broken packages via Synaptic hasn't helped any.

It never indicated any problems.  It just stopped working following a reboot.

Got any ideas?:confused:

Thanks!,
~D~
Assuming that you updated to version 1.0.0 just fine, could you please post here the output of the following file?:
```
~/.config/deluge/deluged.log
```

To access this file, go to your home folder and select the *View -> Show Hidden Files* menu option. After doing this, you will be able to see the *.config* hidden folder. Go inside this folder, and then in the *deluge* folder. There you will find the *deluged.log* text file. Open it and post here its contents.

---

### Post by smith_fan on 2008-09-22
It *was* running when I performed the upgrade. Doh! #-o  And it was halfway through a trickling 4.4 GB download.  Is there a way to not lose all that information while still correcting the problem?

---

### Post by mb_webguy on 2008-09-22
> **smith_fan said:**
> It *was* running when I performed the upgrade. Doh! #-o  And it was halfway through a trickling 4.4 GB download.  Is there a way to not lose all that information while still correcting the problem?

Upgrading doesn't alter your configuration files or torrents.  When you open up the new version of Deluge, your torrents will still be there, at the same level of completion.  Close Deluge and try reinstalling.

---

### Post by kostkon on 2008-09-22
> **mb_webguy said:**
> Upgrading doesn't alter your configuration files or torrents.  When you open up the new version of Deluge, your torrents will still be there, at the same level of completion.  Close Deluge and try reinstalling.
Indeed. You'll only lose your preferences, thus don't forget the first time your run it to apply your previous preferences again.

---

### Post by mb_webguy on 2008-09-22
> **kostkon said:**
> Indeed. You'll only lose your preferences, thus don't forget the first time your run it to apply your previous preferences again.

I didn't lose my preferences, either.  Of course, I was upgrading from 0.9.8, which was a v1.0 release candidate.  It may be different if you're upgrading from 0.5.

---

### Post by kostkon on 2008-09-22
> **mb_webguy said:**
> I didn't lose my preferences, either.  Of course, I was upgrading from 0.9.8, which was a v1.0 release candidate.  It may be different if you're upgrading from 0.5.
Yes, I think if you upgrade from the 0.5.x.x branch you lose your preferences.

---

### Post by smith_fan on 2008-09-23
Here are the contents of that log:
"
[DEBUG   ] 18:58:48 configmanager:44 ConfigManager started..
[INFO    ] 18:58:48 daemon:44 Deluge daemon 1.0.0
[DEBUG   ] 18:58:48 daemon:45 options: {'logfile': None, 'config': None, 'port': 58846, 'donot': False}
[DEBUG   ] 18:58:48 daemon:46 args: []
[DEBUG   ] 18:58:49 configmanager:69 get_config_dir: /home/darin/.config/deluge
[DEBUG   ] 18:58:49 configmanager:69 get_config_dir: /home/darin/.config/deluge
[DEBUG   ] 18:58:49 configmanager:69 get_config_dir: /home/darin/.config/deluge
[DEBUG   ] 18:58:49 core:121 Core init..
[DEBUG   ] 18:58:49 component:102 Registered Core with ComponentRegistry..
[DEBUG   ] 18:58:49 configmanager:88 Getting config 'core.conf'
[DEBUG   ] 18:58:49 config:47 Config created with filename: core.conf
[DEBUG   ] 18:58:49 config:48 Config defaults: {'info_sent': 0.0, 'lsd': True, 'max_download_speed': -1.0, 'send_info': False, 'torrentfiles_location': '/home/darin', 'state_location': '/home/darin/.config/deluge/state', 'stop_seed_at_ratio': False, 'max_active_limit': 8, 'enc_in_policy': 1, 'queue_new_to_top': False, 'ignore_limits_on_local_network': True, 'daemon_port': 58846, 'natpmp': True, 'autoadd_enable': False, 'upnp': True, 'utpex': True, 'max_download_speed_per_torrent': -1, 'max_active_seeding': 5, 'allow_remote': False, 'max_half_open_connections': -1, 'enabled_plugins': [], 'plugins_location': '/home/darin/.config/deluge/plugins', 'download_location': '/home/darin', 'compact_allocation': False, 'max_upload_speed': -1.0, 'max_connections_global': -1, 'enc_prefer_rc4': True, 'listen_ports': [6881, 6891], 'dht': True, 'move_completed_path': '/home/darin', 'stop_seed_ratio': 2.0, 'max_active_downloading': 3, 'prioritize_first_last_pieces': False, 'max_upload_speed_per_torrent': -1, 'auto_managed': True, 'enc_level': 2, 'copy_torrent_file': False, 'max_connections_per_second': -1, 'max_connections_per_torrent': -1, 'move_completed': False, 'dont_count_slow_torrents': False, 'add_paused': False, 'max_upload_slots_per_torrent': -1, 'new_release_check': True, 'enc_out_policy': 1, 'seed_time_ratio_limit': 7.0, 'remove_seed_at_ratio': False, 'autoadd_location': '/home/darin', 'max_upload_slots_global': -1, 'config_location': '/home/darin/.config/deluge', 'seed_time_limit': 180, 'share_ratio_limit': 2.0, 'random_port': True}
[INFO    ] 18:58:49 core:138 Starting XMLRPC server on port 58846
[DEBUG   ] 18:58:49 core:209 Starting libtorrent session..
[DEBUG   ] 18:58:49 config:158 Registering function for torrentfiles_location key..
[DEBUG   ] 18:58:49 config:158 Registering function for state_location key..
[DEBUG   ] 18:58:49 config:158 Registering function for listen_ports key..
[DEBUG   ] 18:58:49 config:158 Registering function for random_port key..
[DEBUG   ] 18:58:49 core:735 random port value set to True
[DEBUG   ] 18:58:49 core:749 listen port range set to 65400-65410
[DEBUG   ] 18:58:49 config:158 Registering function for dht key..
[DEBUG   ] 18:58:49 core:753 dht value set to True
[DEBUG   ] 18:58:49 config:158 Registering function for upnp key..
[DEBUG   ] 18:58:49 core:763 upnp value set to True
[DEBUG   ] 18:58:49 config:158 Registering function for natpmp key..
[DEBUG   ] 18:58:49 core:770 natpmp value set to True
[DEBUG   ] 18:58:49 config:158 Registering function for utpex key..
[DEBUG   ] 18:58:49 core:784 utpex value set to True
[DEBUG   ] 18:58:49 config:158 Registering function for lsd key..
[DEBUG   ] 18:58:49 core:777 lsd value set to True
[DEBUG   ] 18:58:49 config:158 Registering function for enc_in_policy key..
[DEBUG   ] 18:58:49 core:789 encryption value enc_in_policy set to 1..
[DEBUG   ] 18:58:49 core:803 encryption settings:
			out_policy: enabled
		        in_policy: enabled
			level: both
			prefer_rc4: True
[DEBUG   ] 18:58:49 config:158 Registering function for enc_out_policy key..
[DEBUG   ] 18:58:49 core:789 encryption value enc_out_policy set to 1..
[DEBUG   ] 18:58:49 core:803 encryption settings:
			out_policy: enabled
		        in_policy: enabled
			level: both
			prefer_rc4: True
[DEBUG   ] 18:58:49 config:158 Registering function for enc_level key..
[DEBUG   ] 18:58:49 core:789 encryption value enc_level set to 2..
[DEBUG   ] 18:58:49 core:803 encryption settings:
			out_policy: enabled
		        in_policy: enabled
			level: both
			prefer_rc4: True
[DEBUG   ] 18:58:49 config:158 Registering function for enc_prefer_rc4 key..
[DEBUG   ] 18:58:49 core:789 encryption value enc_prefer_rc4 set to True..
[DEBUG   ] 18:58:49 core:803 encryption settings:
			out_policy: enabled
		        in_policy: enabled
			level: both
			prefer_rc4: True
[DEBUG   ] 18:58:49 config:158 Registering function for max_connections_global key..
[DEBUG   ] 18:58:49 core:806 max_connections_global set to -1..
[DEBUG   ] 18:58:49 config:158 Registering function for max_upload_speed key..
[DEBUG   ] 18:58:49 core:810 max_upload_speed set to -1.0..
[DEBUG   ] 18:58:49 config:158 Registering function for max_download_speed key..
[DEBUG   ] 18:58:49 core:815 max_download_speed set to -1.0..
[DEBUG   ] 18:58:49 config:158 Registering function for max_upload_slots_global key..
[DEBUG   ] 18:58:49 core:820 max_upload_slots_global set to -1..
[DEBUG   ] 18:58:49 config:158 Registering function for max_half_open_connections key..
[DEBUG   ] 18:58:49 config:158 Registering function for max_connections_per_second key..
[DEBUG   ] 18:58:49 config:158 Registering function for ignore_limits_on_local_network key..
[DEBUG   ] 18:58:49 config:158 Registering function for share_ratio_limit key..
[DEBUG   ] 18:58:49 core:835 share_ratio_limit set to 2.0..
[DEBUG   ] 18:58:49 config:158 Registering function for seed_time_ratio_limit key..
[DEBUG   ] 18:58:49 core:840 seed_time_ratio_limit set to 7.0..
[DEBUG   ] 18:58:49 config:158 Registering function for seed_time_limit key..
[DEBUG   ] 18:58:49 core:845 seed_time_limit set to 180..
[DEBUG   ] 18:58:49 config:158 Registering function for max_active_downloading key..
[DEBUG   ] 18:58:49 core:851 max_active_downloading set to 3..
[DEBUG   ] 18:58:49 core:852 active_downloads: 8
[DEBUG   ] 18:58:49 config:158 Registering function for max_active_seeding key..
[DEBUG   ] 18:58:49 core:857 max_active_seeding set to 5..
[DEBUG   ] 18:58:49 core:858 active_seeds: 5
[DEBUG   ] 18:58:49 config:158 Registering function for max_active_limit key..
[DEBUG   ] 18:58:49 core:863 max_active_limit set to 8..
[DEBUG   ] 18:58:49 core:864 active_limit: 15
[DEBUG   ] 18:58:49 config:158 Registering function for dont_count_slow_torrents key..
[DEBUG   ] 18:58:49 core:869 dont_count_slow_torrents set to False..
[DEBUG   ] 18:58:49 config:158 Registering function for send_info key..
[DEBUG   ] 18:58:49 core:874 Sending anonymous stats..
[DEBUG   ] 18:58:49 config:158 Registering function for new_release_check key..
[DEBUG   ] 18:58:49 core:924 Checking for new release..
[DEBUG   ] 18:58:49 alertmanager:44 AlertManager initialized..
[DEBUG   ] 18:58:49 core:904 get_new_release
[DEBUG   ] 18:58:49 component:102 Registered AlertManager with ComponentRegistry..
[DEBUG   ] 18:58:49 component:102 Registered SignalManager with ComponentRegistry..
[DEBUG   ] 18:58:49 component:102 Registered PluginManager with ComponentRegistry..
[DEBUG   ] 18:58:49 pluginmanagerbase:48 Plugin manager init..
[DEBUG   ] 18:58:49 configmanager:88 Getting config 'core.conf'
[DEBUG   ] 18:58:49 configmanager:69 get_config_dir: /home/darin/.config/deluge
[DEBUG   ] 18:58:49 pluginmanagerbase:95 Found plugin: Blocklist 1.0
[DEBUG   ] 18:58:49 pluginmanagerbase:95 Found plugin: Label 0.1
[DEBUG   ] 18:58:49 component:102 Registered TorrentManager with ComponentRegistry..
[DEBUG   ] 18:58:49 torrentmanager:108 TorrentManager init..
[DEBUG   ] 18:58:49 configmanager:88 Getting config 'core.conf'
[DEBUG   ] 18:58:49 config:158 Registering function for max_connections_per_torrent key..
[DEBUG   ] 18:58:49 torrentmanager:602 max_connections_per_torrent set to -1..
[DEBUG   ] 18:58:49 config:158 Registering function for max_upload_slots_per_torrent key..
[DEBUG   ] 18:58:49 torrentmanager:608 max_upload_slots_per_torrent set to -1..
[DEBUG   ] 18:58:49 config:158 Registering function for max_upload_speed_per_torrent key..
[DEBUG   ] 18:58:49 torrentmanager:613 max_upload_speed_per_torrent set to -1..
[DEBUG   ] 18:58:49 config:158 Registering function for max_download_speed_per_torrent key..
[DEBUG   ] 18:58:49 torrentmanager:618 max_download_speed_per_torrent set to -1..
[DEBUG   ] 18:58:49 alertmanager:78 Registered handler for alert torrent_finished_alert
[DEBUG   ] 18:58:49 alertmanager:78 Registered handler for alert torrent_paused_alert
[DEBUG   ] 18:58:49 alertmanager:78 Registered handler for alert torrent_checked_alert
[DEBUG   ] 18:58:49 alertmanager:78 Registered handler for alert tracker_reply_alert
[DEBUG   ] 18:58:49 alertmanager:78 Registered handler for alert tracker_announce_alert
[DEBUG   ] 18:58:49 alertmanager:78 Registered handler for alert tracker_alert
[DEBUG   ] 18:58:49 alertmanager:78 Registered handler for alert tracker_warning_alert
[DEBUG   ] 18:58:49 alertmanager:78 Registered handler for alert tracker_error_alert
[DEBUG   ] 18:58:49 alertmanager:78 Registered handler for alert storage_moved_alert
[DEBUG   ] 18:58:49 alertmanager:78 Registered handler for alert torrent_resumed_alert
[DEBUG   ] 18:58:49 alertmanager:78 Registered handler for alert state_changed_alert
[DEBUG   ] 18:58:49 component:102 Registered AutoAdd with ComponentRegistry..
[DEBUG   ] 18:58:49 configmanager:88 Getting config 'core.conf'
[DEBUG   ] 18:58:49 config:158 Registering function for autoadd_enable key..
[DEBUG   ] 18:58:49 autoadd:116 _on_autoadd_enable
[DEBUG   ] 18:58:49 config:158 Registering function for autoadd_location key..
[DEBUG   ] 18:58:49 autoadd:123 _on_autoadd_location
[DEBUG   ] 18:58:49 component:125 Starting component PluginManager..
[DEBUG   ] 18:58:49 component:125 Starting component TorrentManager..
[DEBUG   ] 18:58:49 configmanager:88 Getting config 'core.conf'
[DEBUG   ] 18:58:49 oldstateupgrader:86 Attempting to create torrent_info from /home/darin/.config/deluge/torrentfiles/Windows_XP_Pro_SP3_VLK_MSDN.4171064.TPB.torrent
Traceback (most recent call last):
  File "/usr/bin/deluged", line 8, in <module>
    load_entry_point('deluge==1.0.0', 'console_scripts', 'deluged')()
  File "/var/lib/python-support/python2.5/deluge/main.py", line 169, in start_daemon
    Daemon(options, args)
  File "/var/lib/python-support/python2.5/deluge/core/daemon.py", line 52, in __init__
    self.core = Core(options.port).run()
  File "/var/lib/python-support/python2.5/deluge/core/core.py", line 301, in run
    component.start()
  File "/var/lib/python-support/python2.5/deluge/component.py", line 194, in start
    _ComponentRegistry.start()
  File "/var/lib/python-support/python2.5/deluge/component.py", line 114, in start
    self.start_component(component)
  File "/var/lib/python-support/python2.5/deluge/component.py", line 121, in start_component
    self.start_component(depend)
  File "/var/lib/python-support/python2.5/deluge/component.py", line 126, in start_component
    self.components[name].start()
  File "/var/lib/python-support/python2.5/deluge/core/torrentmanager.py", line 164, in start
    deluge.core.oldstateupgrader.OldStateUpgrader()
  File "/var/lib/python-support/python2.5/deluge/core/oldstateupgrader.py", line 72, in __init__
    self.upgrade05()
  File "/var/lib/python-support/python2.5/deluge/core/oldstateupgrader.py", line 109, in upgrade05
    max_upload_speed=ti.upload_rate_limit,
AttributeError: 'torrent_info' object has no attribute 'upload_rate_limit'
[DEBUG   ] 18:58:49 core:916 new_release: 1.0.0
"
Am I hosed regarding the in-progress download?

How would you propose I proceed?  Should I just remove it using Synaptic??

Thanks!,
~D~

---

### Post by mb_webguy on 2008-09-23
As long as you don't do anything with the contents of your ~/.config/deluge directory, you shouldn't have to worry about your in-progress download.  Uninstall the app using Synaptic, but don't select the "Mark for complete removal" option, just "Mark for removal".  Then try to reinstall using the deb from the Deluge website.

---

### Post by smith_fan on 2008-09-23
After having done that, Deluge's window still opens to a *greyed-out* condition.  Should I try again using the 'mark for complete removal' choice instead?

---

### Post by smith_fan on 2008-09-23
I noticed that in Synaptic when I removed it, I removed the packages "deluge-torrent" and "deluge-torrent-common".  Installing the DEB from the site appears to only install "deluge-torrent".  When I search for and try to install "deluge-torrent-common", Synaptic marks "deluge-torrent" for removal.  I'm unable to get 'em both installed simultaneously.

I'm thoroughly confused! *but what else is new, I suppose?*

Can anybody please explain to me what is happening here?:confused:

Thanks!,
~D~

---

### Post by smith_fan on 2008-09-25
Anybody?  Anybody at all?! :confused:

---

