---
title: "Can't print to SMB printer"
date: 2010-03-18
forum: Hardware
---

### Post by bleeblee on 2010-03-18
I can't connect to a Windows network shared printer, although the  CUPS output below seems to indicate it can be seen by my ubuntu laptop:

'remote_server_smb_shares': <smbc.Dirent object "SamsungM" (Printer share) at 0xa435e00>
(full output at the bottom of this post)

Using the Gnome Desktop, I navigate to:

System > Administration > Printing
  then
Server > Settings > "show printers shared by other systems" > Problems?

I get a message "I have not been able to work out the problem but here is some useful info for a bug report."

Is this likely a bug or is it user error?

Thanks for any feedback.

===full output below===

Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Is local server publishing?):
{'local_server_exporting_printers': False}
Page 3 (Choose printer):
{'cups_dests_available': [('Dell-1700', None)], 'cups_queue_listed': False}
Page 4 (Local or remote?):
{'printer_is_remote': True}
Page 5 (Remote address):
{'remote_server_ip_address': '192.168.2.7', 'remote_server_name': ''}
Page 6 (Check network server sanity):
{'remote_server_connect_ipp': False,
 'remote_server_name_resolves': ['192.168.2.7', '192.168.2.7', '192.168.2.7'],
 'remote_server_smb': True,
 'remote_server_smb_shares': [<smbc.Dirent object "IPC$" (IPC share) at 0xa435db8>,
                              <smbc.Dirent object "Documents" (File share) at 0xa435d58>,
                              <smbc.Dirent object "print$" (File share) at 0xa435dd0>,
                              <smbc.Dirent object "share1" (File share) at 0xa435de8>,
                              <smbc.Dirent object "SamsungM" (Printer share) at 0xa435e00>,
                              <smbc.Dirent object "ADMIN$" (File share) at 0xa435e18>,
                              <smbc.Dirent object "H$" (File share) at 0xa435e30>,
                              <smbc.Dirent object "C$" (File share) at 0xa435e48>],
 'remote_server_try_connect': '192.168.2.7'}
Page 7 (Locale issues):
{'printer_page_size': None,
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}

---

