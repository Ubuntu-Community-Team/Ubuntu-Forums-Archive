---
title: "Cannot sync Samsung Omnia i910 with Evolution"
date: 2010-05-12
forum: Hardware
---

### Post by Robertjm on 2010-05-12
Hi all,

I've been trying to get my Samsung Omnia i910 to sync using Evolution. I have Multisync installed. A partnership is created and the desktop does seem to make a communication attempt with the phone.

However, nothing syncs, and there seems to be an error as well.

Here's what I get when I try and sync from the command line:

[COLOR="Blue"][B]robertjm@robertjm-laptop:~$ msynctool --sync UbuntuDesktop
Synchronizing group "UbuntuDesktop" 
DEBUG:SynCE:Connect() called
Member 1 of type synce-opensync-plugin just connected
Member 2 of type evo2-sync just connected
All clients connected or error
DEBUG:SynCE:get_changeinfo() called
DEBUG:SynCE:slow sync requested for Contacts
DEBUG:SynCE:slow sync requested for Calendar
DEBUG:SynCE:slow sync requested for Tasks
INFO:SynCE:initiating device synchronization
Received an entry pas-id-4B8B7AF800000000 with data of size 4 from member 2 (evo2-sync). Changetype ADDED
Member 2 of type evo2-sync just sent all changes
INFO:SynCE:waiting for engine to complete sync
INFO:SynCE:device synchronization complete
INFO:SynCE:initiating prefill
INFO:SynCE: prefill complete
DEBUG:SynCE:requesting remote changes
DEBUG:SynCE:got 4 changesets
DEBUG:SynCE:no changes for item type 0
DEBUG:SynCE: processing changes for 4 items of item type 1
Traceback (most recent call last):
  File "/usr/lib/opensync/python-plugins/synce-opensync-plugin-2x.py", line 174, in get_changeinfo
    change.uid = array.array('B',guid).tostring() 
  File "/usr/lib/pymodules/python2.6/opensync.py", line 192, in set_uid
    def set_uid(self, *args): return _opensync.OSyncChange_set_uid(self, *args)
TypeError: in method 'OSyncChange_set_uid', argument 1 of type 'OSyncChange *'
Member 1 of type synce-opensync-plugin had an error while getting changes: Error during get_changeinfo() method
DEBUG:SynCE:disconnect() called
Member 1 of type synce-opensync-plugin just disconnected
Member 2 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to read from one of the members
DEBUG:SynCE:finalize() called
Error while synchronizing: Unable to read from one of the members
robertjm@robertjm-laptop:~$ 
[/B][/COLOR]

When I go into the Multisync0.90 gui, select edit and then hi light synce-opensync-plugin it seems to be pretty sparten:

[COLOR="Blue"][B]<?xml version="1.0"?>
<filter/>
[/B][/COLOR]

Should there be more stuff in there regarding syncing?

In the evo2-sync the options are set to Addressbook: Ubuntu One, Calendar: Personal, Tasks: Personal

Using the gui I get a msg about not being able to communicate with one of its members. I still get the same msg if I change Addressbook to Personal.

Using Lucid Lynx 32bit version

---

### Post by coqboricua on 2010-06-05
I wish somebody could help with this...I have exactly the same problem.

---

### Post by Vjetar on 2010-06-17
You can find patch at [http://www.opensync.org/ticket/1131](http://www.opensync.org/ticket/1131)

---

