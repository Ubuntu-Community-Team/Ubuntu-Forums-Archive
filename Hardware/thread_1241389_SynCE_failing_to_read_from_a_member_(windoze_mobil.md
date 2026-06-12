---
title: "SynCE failing to read from a member (windoze mobile 6.1)"
date: 2009-08-15
forum: Hardware
---

### Post by mandarb777 on 2009-08-15
Edit: I have gotten the computer side to work.  However, it is not actually syncing the data to the phone.

Hello All,
I recently got a Samsung BlackJack II with Windows Mobile 6.1 and really like the phone.  However, a major reason why I got it was to sync my Evolution data with it, but the SynCE is paging out the following error and not syncing any data.  I am using ubuntu gnome 9.04 amd64.

```
:~$ msynctool --sync synce-sync
Synchronizing group "synce-sync" 
The previous synchronization was unclean. Slow-syncing
DEBUG:SynCE:Connect() called
Member 1 of type synce-opensync-plugin just connected
Member 2 of type evo2-sync just connected
All clients connected or error
DEBUG:SynCE:get_changeinfo() called
DEBUG:SynCE:slow sync requested for Contacts
DEBUG:SynCE:slow sync requested for Calendar
DEBUG:SynCE:slow sync requested for Tasks
INFO:SynCE:initiating device synchronization
Received an entry pas-id-4A7B3A4A00000000 with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A00000002 with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A00000004 with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Traceback (most recent call last):
  File "/usr/lib/opensync/python-plugins/synce-opensync-plugin-2x.py", line 152, in get_changeinfo
    self._TriggerSync()
  File "/usr/lib/opensync/python-plugins/synce-opensync-plugin-2x.py", line 117, in _TriggerSync
    self.engine.Synchronize()
  File "/var/lib/python-support/python2.6/dbus/proxies.py", line 140, in __call__
Received an entry pas-id-4A7B3A4A00000006 with data of size 8 from member 2 (evo2-sync). Changetype ADDED
    **keywords)
  File "/var/lib/python-support/python2.6/dbus/connection.py", line 622, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.synce.SyncEngine.Error.NoBoundPartnership: 
Received an entry pas-id-4A7B3A4A00000008 with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A0000000B with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A0000000D with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A0000000F with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A00000011 with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A00000013 with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A00000015 with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A00000017 with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A00000019 with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A0000001A with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A0000001C with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A0000001E with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A00000001 with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A00000003 with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A00000005 with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A00000007 with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A00000009 with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A0000000A with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A0000000C with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A0000000E with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A00000010 with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A00000012 with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A00000014 with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A00000016 with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A00000018 with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A0000001B with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7B3A4A0000001D with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Received an entry pas-id-4A7C45D400000000 with data of size 8 from member 2 (evo2-sync). Changetype ADDED
Member 2 of type evo2-sync just sent all changes
Member 1 of type synce-opensync-plugin had an error while getting changes: Error during get_changeinfo() method
DEBUG:SynCE:disconnect() called
Member 1 of type synce-opensync-plugin just disconnected
Member 2 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to read from one of the members
DEBUG:SynCE:finalize() called
Error while synchronizing: Unable to read from one of the members

```

Does anyone know how to solve this?
Mandarb

---

