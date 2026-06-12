---
title: "sync failure usb device not recognized?"
date: 2008-05-22
forum: Hardware
---

### Post by intruderukr on 2008-05-22
I have upgraded to Hardy Heron and would like to sync my mobile 5 ipaq; I followed the good instructions [here]("http://www.synce.org/moin/SynceWithUbuntu"), but at the last step I get this message: synce-pls
synce-pls: symbol lookup error: synce-pls: undefined symbol: rapi_connection_from_name
I have tried a few other things like typing "dmesg", but my ipaq which is connected to the usb port is not detected...is there any help???:confused:thanks!

---

### Post by intruderukr on 2008-05-22
After some more work I can see that the ipaq is there, but I'm not able to sync...any one out there have the solution?
here is my shell:
 
trude@ubuntu:~$ sudo synce-serial-config ttyUSB0

  ERROR:
  
  synce-serial-config was unable to find a character device named "ttyUSB0"
  
  
trude@ubuntu:~$ librra0 librra0-tools librapi2-tools libsynce0 synce-dccm synce-multisync-plugin synce-serial
bash: librra0: command not found
trude@ubuntu:~$ sudo apt-get install librra0 librra0-tools librapi2-tools libsynce0 synce-dccm synce-multisy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
librra0 is already the newest version.
librra0-tools is already the newest version.
librapi2-tools is already the newest version.
libsynce0 is already the newest version.
synce-dccm is already the newest version.
E: Couldn't find package synce-multisy
trude@ubuntu:~$ sudo apt-get install libmultisync-plugin-all multisync
Reading package lists... Done
Building dependency tree       
Reading state information... Done
multisync is already the newest version.
The following packages were automatically installed and are no longer required:
  libdynamite0 libunshield0 liborange0 libnss3-0d agsync
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libmultisync-plugin-backup libmultisync-plugin-evolution libmultisync-plugin-irmc
  libmultisync-plugin-irmc-bluetooth libmultisync-plugin-opie
The following NEW packages will be installed:
  libmultisync-plugin-all libmultisync-plugin-backup libmultisync-plugin-evolution
  libmultisync-plugin-irmc libmultisync-plugin-irmc-bluetooth
  libmultisync-plugin-opie
0 upgraded, 6 newly installed, 0 to remove and 2 not upgraded.
Need to get 269kB of archives.
After this operation, 954kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libmultisync-plugin-evolution 0.82-8build1 [31.6kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libmultisync-plugin-backup 0.82-8build1 [33.5kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libmultisync-plugin-irmc 0.82-8build1 [82.0kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libmultisync-plugin-irmc-bluetooth 0.82-8build1 [13.4kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libmultisync-plugin-opie 0.82-8build1 [101kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libmultisync-plugin-all 0.82-8build1 [6932B]
Fetched 269kB in 1s (155kB/s)                  
Selecting previously deselected package libmultisync-plugin-evolution.
(Reading database ... 121926 files and directories currently installed.)
Unpacking libmultisync-plugin-evolution (from .../libmultisync-plugin-evolution_0.82-8build1_i386.deb) ...
Selecting previously deselected package libmultisync-plugin-backup.
Unpacking libmultisync-plugin-backup (from .../libmultisync-plugin-backup_0.82-8build1_i386.deb) ...
Selecting previously deselected package libmultisync-plugin-irmc.
Unpacking libmultisync-plugin-irmc (from .../libmultisync-plugin-irmc_0.82-8build1_i386.deb) ...
Selecting previously deselected package libmultisync-plugin-irmc-bluetooth.
Unpacking libmultisync-plugin-irmc-bluetooth (from .../libmultisync-plugin-irmc-bluetooth_0.82-8build1_i386.deb) ...
Selecting previously deselected package libmultisync-plugin-opie.
Unpacking libmultisync-plugin-opie (from .../libmultisync-plugin-opie_0.82-8build1_i386.deb) ...
Selecting previously deselected package libmultisync-plugin-all.
Unpacking libmultisync-plugin-all (from .../libmultisync-plugin-all_0.82-8build1_all.deb) ...
Setting up libmultisync-plugin-evolution (0.82-8build1) ...
Setting up libmultisync-plugin-backup (0.82-8build1) ...
Setting up libmultisync-plugin-irmc (0.82-8build1) ...
Setting up libmultisync-plugin-irmc-bluetooth (0.82-8build1) ...
Setting up libmultisync-plugin-opie (0.82-8build1) ...
Setting up libmultisync-plugin-all (0.82-8build1) ...
trude@ubuntu:~$ multisync
plugin_API_version
short_name
long_name
plugin_init

** (multisync:14149): CRITICAL **: synce_info_from_hal: Failed to initialise hal context: org.freedesktop.DBus.Error.NoMemory: Not enough memory
** Message: Hal reports no devices connected
process 14149: Attempt to remove filter function 0xb666fcd0 user data 0x80cefe8, but no such filter has been added

** (multisync:14149): WARNING **: No devices connected to odccm

** (multisync:14149): WARNING **: No devices connected to odccm
[synce_info_from_file:69] unable to open file: /home/trude/.synce/active_connection
[rapi_context_connect:100] Failed to get connection info
[synce_connect:291] Failed to initialize RAPI
[synce_info_from_file:69] unable to open file: /home/trude/.synce/active_connection
[rapi_context_connect:100] Failed to get connection info
[synce_connect:291] Failed to initialize RAPI
** Message: Hal reports no devices connected
** Message: Hal reports no devices connected

** (multisync:14149): WARNING **: No devices connected to odccm
[synce_info_from_file:69] unable to open file: /home/trude/.synce/active_connection
[rapi_context_connect:100] Failed to get connection info
[synce_connect:291] Failed to initialize RAPI
[synce_join_thread:260] synce_join_thread called when no thread is running
[synce_join_thread:260] synce_join_thread called when no thread is running

(multisync:14149): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(multisync:14149): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'
Segmentation fault
trude@ubuntu:~$ synce-matchmaker create INDEX
** Message: Hal reports no devices connected

** (process:26477): WARNING **: No devices connected to odccm
[synce_info_from_file:69] unable to open file: /home/trude/.synce/active_connection
[rapi_context_connect:100] Failed to get connection info
[main:66] Failed to initialize RAPI
trude@ubuntu:~$ /dev/ttyUSB0
bash: /dev/ttyUSB0: No such file or directory
trude@ubuntu:~$

---

### Post by jamorod on 2010-01-03
Hi there,

Were you able to find a solution to this?

I have a Palm Treo 750 with Windows Mobile 6. At times, I can sync, other times, I plug it and the device is not found. The only solution seems to be to restart the computer and hope that the device will be detected.

---

