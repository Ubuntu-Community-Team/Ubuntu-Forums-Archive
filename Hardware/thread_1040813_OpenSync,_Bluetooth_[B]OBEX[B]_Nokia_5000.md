---
title: "OpenSync, Bluetooth [B]OBEX[/B] Nokia 5000"
date: 2009-01-15
forum: Hardware
---

### Post by obsrv on 2009-01-15
Hello,
My target is to sync my cell phone Nokia 5000 with PIRATE Workstation which uses Ubuntu 9.04 A3 Jaunty. As default settings I can't browse files on I get this error:

```
Error: Connection refused
Please select another viewer and try again.
```

Is this misconfiguration or OBEX problems? Maybe I should report a bug?

---

### Post by obsrv on 2009-01-18
BUMP! I really need to back up whole my cell phones data.

---

### Post by obsrv on 2009-02-08
BUMP. I need this thing very much :( :( :(

---

### Post by sanderj on 2009-08-09
I get the same message om my "Ubuntu 9.04" 64-bit, trying to connect to my Nokia N95:

> Could not display "obex://[00:1F:00:B0:00:34]/".

Error: Connection refused
Please select another viewer and try again.


And (nothing relevant in) /var/log/syslog

```
Aug  9 14:08:24 athlon64 kernel: [ 1113.308689] usb 4-1: new full speed USB device using ohci_hcd and address 4
Aug  9 14:08:24 athlon64 kernel: [ 1113.475249] usb 4-1: configuration #1 chosen from 1 choice
Aug  9 14:08:24 athlon64 bluetoothd[2920]: HCI dev 0 registered
Aug  9 14:08:24 athlon64 bluetoothd[2920]: HCI dev 0 up
Aug  9 14:08:24 athlon64 bluetoothd[2920]: Starting security manager 0
Aug  9 14:08:24 athlon64 bluetoothd[2920]: Registered interface org.bluez.Service on path /org/bluez/2920/hci0
Aug  9 14:08:24 athlon64 bluetoothd[2920]: Registered interface org.bluez.SerialProxyManager on path /org/bluez/2920/hci0
Aug  9 14:08:24 athlon64 bluetoothd[2920]: rfcomm_bind: Address already in use (98)
Aug  9 14:08:24 athlon64 bluetoothd[2920]: audio-headset: Operation not permitted (1)
Aug  9 14:08:24 athlon64 bluetoothd[2920]: l2cap_bind: Address already in use (98)
Aug  9 14:08:24 athlon64 bluetoothd[2920]: audio-a2dp: Operation not permitted (1)
Aug  9 14:08:24 athlon64 bluetoothd[2920]: Registered interface org.bluez.NetworkPeer on path /org/bluez/2920/hci0
Aug  9 14:08:24 athlon64 bluetoothd[2920]: Registered interface org.bluez.NetworkHub on path /org/bluez/2920/hci0
Aug  9 14:08:24 athlon64 bluetoothd[2920]: Registered interface org.bluez.NetworkRouter on path /org/bluez/2920/hci0
Aug  9 14:08:24 athlon64 bluetoothd[2920]: probe failed with driver input-headset for device /org/bluez/2920/hci0/dev_00_1F_00_B0_00_34
Aug  9 14:08:24 athlon64 bluetoothd[2920]: Registered interface org.bluez.Serial on path /org/bluez/2920/hci0/dev_00_1F_00_B0_00_34
Aug  9 14:08:24 athlon64 bluetoothd[2920]: Registered interface org.bluez.Control on path /org/bluez/2920/hci0/dev_00_1F_00_B0_00_34
Aug  9 14:08:24 athlon64 bluetoothd[2920]: Adapter /org/bluez/2920/hci0 has been enabled

Aug  9 14:08:43 athlon64 bluetoothd[2920]: Discovery session 0x7f71e5519940 with :1.69 activated
Aug  9 14:08:50 athlon64 bluetoothd[2920]: link_key_request (sba=00:1F:81:00:02:00, dba=00:1F:00:B0:00:34)

Aug  9 14:09:53 athlon64 bluetoothd[2920]: Discovery session 0x7f71e5519940 with :1.72 activated
Aug  9 14:09:58 athlon64 bluetoothd[2920]: link_key_request (sba=00:1F:81:00:02:00, dba=00:1F:00:B0:00:34)

```

---

### Post by lobner on 2009-09-07
Hello sirs,

Dig anyone figure this out? I am having the same problem.

/regards

-------------------
### EDIT ###

Nevermind, I solved it by connecting the phone to the computer, instead of the other way around.
Then it went through all the authentication procedures, and gave access through Nautilus.

---

### Post by brunzibrunz on 2011-02-11
[SIZE=1]Hello,

I finally managed to sync my calendar over Bluetooth with my NOKIA 5000. I want to share how I got it working.[/SIZE]

[LIST=1]
[*][SIZE=4][SIZE=1]Download libsyncml from[/SIZE] [/SIZE][URL="http://sourceforge.net/projects/libsyncml/files/libsyncml/0.5.4/libsyncml-0.5.4.tar.bz2/download"]http://sourceforge.net/projects/libsyncml/files/libsyncml/0.5.4/libsyncml-0.5.4.tar.bz2/download

[/URL]
[*]extract the files using your favourite tool - e.g. ```
tar -jxvf libsyncml-0.5.4.tar.bz2
```
[*]So far, so good. Open CMakeLists.txt and delete the paragraph starting with *"# ensure out od source build"* - leave the next comment intact!!
[*]Then open data_sync_callbacks.c (It's in libsyncml/datasync_api) and delete the part of code from line 653 *smlAssert(datastore->dsObject->mappingCallback);* to 672 be sure to leave the** }** intact.
[*]You have to check if you fulfill all dependencies of libsyncml in the INSTALL file
[*]Then go back to the base dir of libsyncml-0.5.4 and type ```
cmake .
``` (You might have to install it first)
[*]Next type ```
make
``` and then ```
sudo checkinstall
```
[*]Now you should be able to start "syncml-ds-tool"
[*]Switch on bluetooth both on your mobile and PC: type ```
hcitool scan
``` and with your MAC ```
sdptool browse <MAC>
``` to find out which channel SyncML is!!!
[*]create a folder for your files and you're ready to go
[*]launch ```
syncml-ds-tool -b <MAC> <channel> --slow-sync text/x-vcalendar calendar <absolute path to your sync dir> --wbxml --identifier "PC Suite"
``` The syncing process should start and your calendar files from your mobile should be transmitted to your folder.
 Using the repository package I got the error message *Assertion datastore->dsObject->mappingCallback failed* and therefore I did step 4. It seems to have solved the problem.
[/LIST]
Greez

Probably syncml-ds-tool can't find libsyncml.so.2 - If so create a symbolic link in /usr/lib  ```
sudo ln -s /usr/local/lib/libsyncml.so.2 /usr/lib/libsyncml.so.2
```[SIZE=4]
[/SIZE]

---

