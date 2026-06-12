---
title: "barry-sync had an error while getting changes: Desktop: unexpected command of 0x41 in"
date: 2011-06-11
forum: Hardware
---

### Post by kouhinn on 2011-06-11
Hi,all

When I use barry with opensync to do synchronization with evolution, the barry-sync failed:
```
unexpected command of 0x41 instead of expected 0x40
```

The bcharge and barrybackup is worked fine, and I believe I did the right configuration for opensync and evolution.

Could anyone give me some help about this?

Here is the details:
```

beffery@beffery-laptop:~$ !217
msynctool --showgroup BlackBerry
Groupname: BlackBerry
Member 2: barry-sync
	Configuration : #
# This is the default configuration file for the barry-sync opensync plugin.
# Comments are preceded by a '#' mark at the beginning of a line.
# The config format is a set of lines of <keyword> <values>.
#
# Keywords available:
#
# DebugMode        - If present, verbose USB debug output will be enabled
#
# Device           - If present, it is followed by the following values:
#      PIN number    - PIN number of the device to sync with (in hex)
#      sync calendar - 1 to sync calendar, 0 to skip
#      sync contacts - 1 to sync contacts, 0 to skip
#
# Password secret  - If present, specifies the device's password in plaintext
#

#DebugMode

Device 2535428E 1 1

#Password secret


Member 1: evo2-sync
	Configuration : <config>
  <address_path>file:///home/beffery/.evolution/addressbook/local/system</address_path>
  <calendar_path>file:///home/beffery/.evolution/calendar/local/system</calendar_path>
  <tasks_path>file:///home/beffery/.evolution/tasks/local/system</tasks_path>
</config>

beffery@beffery-laptop:~$ history|grep BlackBerry
  199  msynctool --configure BlackBerry 1
  202  msynctool --configure BlackBerry 1
  203  msynctool --addgroup BlackBerry
  204  msynctool --configure BlackBerry 1
  205  msynctool --addmember BlackBerry evo2-sync 
  206  msynctool --addmember BlackBerry evolution-sync 
  207  msynctool --addmember BlackBerry evo2-sync 
  208  msynctool --addmember BlackBerry barry-sync
  209  msynctool --configure BlackBerry 1
  210  msynctool --configure BlackBerry 2
  211  msynctool --sync BlackBerry
  213  msynctool --sync BlackBerry
  216  msynctool --configure BlackBerry 2
  217  msynctool --showgroup BlackBerry
  219  msynctool --sync BlackBerry
  235  history|grep BlackBerry
  238  history|grep BlackBerry
  239  msynctool --showgroup BlackBerry
  240  history|grep BlackBerry
beffery@beffery-laptop:~$ !219
msynctool --sync BlackBerry
Synchronizing group "BlackBerry" 
Member 1 of type evo2-sync just connected
Member 2 of type barry-sync just connected
All clients connected or error
Member 1 of type evo2-sync just sent all changes
Sent packet:
    00000000: 07 01 0b 00 40 02 46 2e 00 02 00                 ....@.F....

Response packet:
    00000000: 07 00 07 00 41 00 02                             ....A..

Desktop: unexpected command of 0x41 instead of expected 0x40
Received an entry contacts-1771111419 with data of size 4 from member 2 (barry-sync). Changetype ADDED
]Member 2 of type barry-sync had an error while getting changes: Desktop: unexpected command of 0x41 instead of expected 0x40
Member 1 of type evo2-sync just disconnected
Member 2 of type barry-sync just disconnected
All clients have disconnected
The sync failed: Unable to read from one of the members
Error while synchronizing: Unable to read from one of the members

```

---

### Post by kouhinn on 2011-06-13
Is there anyone could help me ?

---

### Post by kouhinn on 2011-06-14
Is there anyone encountered the same difficulty?

---

### Post by SoFl W on 2011-06-14
I would have to look through some old notes so give me a while.  I tried the Barry sinc but not with evolution, just used it for backup.  I remember I had to change some config around.

I eventually just installed Windows in a Virtual machines and fire that up to backup my Blackberry.


EDIT:

See if these threads help:
[http://ubuntuforums.org/showthread.php?t=190938](http://ubuntuforums.org/showthread.php?t=190938)
[http://ubuntuforums.org/showthread.php?t=1145846](http://ubuntuforums.org/showthread.php?t=1145846)  (<- this is more for usb storage)
[http://ubuntuforums.org/showthread.php?t=1112790](http://ubuntuforums.org/showthread.php?t=1112790)

---

### Post by kouhinn on 2011-06-15
Thank you for your kind reply. I can't still found any solution to my problem.
I think I should give up. I'll sync my blackberry in windows.

---

