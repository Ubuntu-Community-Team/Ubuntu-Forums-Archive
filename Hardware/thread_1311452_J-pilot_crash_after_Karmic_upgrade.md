---
title: "J-pilot crash after Karmic upgrade"
date: 2009-11-02
forum: Hardware
---

### Post by barney_1 on 2009-11-02
After upgrading to 9.10 Karmic Koala I encountered segfaults in Jpilot.  I could launch the program but when I tried to switch to Calendar view or others the program would segfault.

To fix this I move the .jpilot directory:
```
mv ~/.jpilot ~/jpilot_backup
```
I then launched JPilot and did a complete backup from the device.

I'm getting errors when I sync and I think it may be a permissions problem.  Here's the sync log:
```
Doing a fast sync.
Syncing DatebookDB
Syncing AddressDB
sync.c:1567 Error getting app info /home/mike/.jpilot/ToDoDB.pdb
Syncing ToDoDB
Fetching 'ToDoDB' (Creator ID 'todo')... OK
Syncing MemoDB
Fetching 'MemoDB' (Creator ID 'memo')... OK
sync.c:1567 Error getting app info /home/mike/.jpilot/ExpenseDB.pdb
Syncing ExpenseDB
Fetching 'ExpenseDB' (Creator ID 'exps')... OK
sync.c:1562 Error reading file: /home/mike/.jpilot/Keys-Gtkr.pdb
Syncing Keys-Gtkr
fast_sync_application: Unable to open file: Keys-Gtkr
synctime: Palm OS version 5.40
synctime: Setting the time on the pilot... Done
Fetching 'Saved Preferences' (Creator ID 'psys')... OK
Finished.
```

Here's my directory info:
```
drwx------   3 mike mike   4096 2009-11-02 12:49 .
drwxr-xr-x 128 mike mike  12288 2009-11-02 12:47 ..
-rw-------   1 mike mike      0 2009-11-02 12:38 AddressDB.pc3
-rw-------   1 mike mike  17656 2009-11-02 12:42 AddressDB.pdb
lrwxrwxrwx   1 mike mike     14 2009-11-02 12:42 backup -> backup11021242
drwx------   2 mike mike   4096 2009-11-02 12:45 backup11021242
-rw-------   1 mike mike    378 1969-12-31 18:00 CalendarDB-PDat.pdb
-rw-------   1 mike mike   1172 1969-12-31 18:00 ContactsDB-PAdd.pdb
-rw-------   1 mike mike      0 2009-11-02 12:38 DatebookDB.pc3
-rw-------   1 mike mike 196527 1969-12-31 18:00 DatebookDB.pdb
-rw-------   1 mike mike      0 2009-11-02 12:39 ExpenseDB.pc3
-rw-------   1 mike mike    495 2009-11-02 12:42 ExpenseDB.pdb
-rw-------   1 mike mike    127 2009-11-02 12:48 jpilot.alarms
-rw-------   1 mike mike      0 2009-11-02 12:49 jpilot.install
-rw-------   1 mike mike   7425 2009-11-02 12:49 jpilot.log
-rw-------   1 mike mike     11 2009-11-02 12:49 jpilot.next_id
-rw-------   1 mike mike      5 2009-11-02 12:48 jpilot.pid
-rw-------   1 mike mike      0 2009-11-02 12:38 jpilot.plugins
-rw-------   1 mike mike   1868 2009-11-02 12:49 jpilot.rc
-rw-------   1 mike mike      0 2009-11-02 12:39 Keys-Gtkr.pc3
-rw-------   1 mike mike    363 1969-12-31 18:00 Memo32DB.pdb
-rw-------   1 mike mike      0 2009-11-02 12:38 MemoDB.pc3
-rw-------   1 mike mike  67040 2009-11-02 12:49 MemoDB.pdb
-rw-------   1 mike mike    380 1969-12-31 18:00 MemosDB-PMem.pdb
-rw-------   1 mike mike  22115 2009-11-02 12:49 Saved Preferences.prc
-rw-------   1 mike mike      0 2009-11-02 12:49 sync_pid
-rw-------   1 mike mike    380 1969-12-31 18:00 TasksDB-PTod.pdb
-rw-------   1 mike mike      0 2009-11-02 12:49 ToDoDB.pc3
-rw-------   1 mike mike    541 2009-11-02 12:49 ToDoDB.pdb

```

Any thoughts on these errors? Thanks for the help!

---

### Post by barney_1 on 2009-11-02
I've tried reasserting ownership of the .jpilot files with this:
```
cd ~/.jpilot
sudo chown mike:mike *
```
Which seems to take care of the syncing errors (I disabled the keyring conduit).

I'm still getting persistent crashes when clicking back to the todo list, this comes up in dmesg:
```
jpilot[3730]: segfault at 68746f49 ip 00e2c761 sp bfc77368 error 4 in libc-2.10.1.so[dbd000+13e000]
```

---

### Post by Reteip on 2010-02-26
Hi Barney

I think I am having a similar problem.
Jpilot does not crash on me but my output says:
[INDENT]sync.c:1562 Error reading file: /home/xxxxx/.jpilot/Keys-Gtkr.pdb
Syncing Keys-Gtkr
fast_sync_application: Unable to open file: Keys-Gtkr[/INDENT]

When you said:
(I disabled the keyring conduit)
How did you do that?
Please be mindful that I am the sort of person that is more comfortable with GUI interfaces. I need a lot of guidance when doing stuff using a terminal.

I would appreciate your reply.
Thanks

---

### Post by katosheen on 2010-09-07
> 
[INDENT]Jpilot does not crash on me but my output says:[/INDENT][INDENT]sync.c:1562 Error reading file: /home/xxxxx/.jpilot/Keys-Gtkr.pdb
Syncing Keys-Gtkr
fast_sync_application: Unable to open file: Keys-Gtkr[/INDENT]

If you uncheck ''Sync KeyRing 1.1 (/usr/lib/jpilot/plugins/libkeyring.so)'' option in j-pilot File->Preferences->TAB:Conduits , you get rid of this error.

---

