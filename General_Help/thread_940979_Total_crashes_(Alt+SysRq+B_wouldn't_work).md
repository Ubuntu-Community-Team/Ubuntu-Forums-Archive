---
title: "Total crashes (Alt+SysRq+B wouldn't work)"
date: 2008-10-07
forum: General Help
---

### Post by madsporkmurderer on 2008-10-07
Came back to my computer earlier and found it totally locked for the second time this week- a short piece of audio looping and blank screens. Tried various key combinations to no effect- not even with Alt+SysRq+B.

had a look at syslog and it seems to be something to do with samba (I've got my music on an ubuntu media server downstairs). Here is relevant part of syslog:

```
Oct  7 19:39:01 mike /USR/SBIN/CRON[14474]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct  7 19:40:01 mike /USR/SBIN/CRON[14492]: (www-data) CMD ([ -f /usr/share/moodle/admin/cron.php ] && /usr/bin/php -f /usr/share/moodle/admin/cron.php > /dev/null)
Oct  7 19:45:01 mike /USR/SBIN/CRON[14540]: (www-data) CMD ([ -f /usr/share/moodle/admin/cron.php ] && /usr/bin/php -f /usr/share/moodle/admin/cron.php > /dev/null)
Oct  7 19:50:01 mike /USR/SBIN/CRON[14589]: (www-data) CMD ([ -f /usr/share/moodle/admin/cron.php ] && /usr/bin/php -f /usr/share/moodle/admin/cron.php > /dev/null)
Oct  7 19:55:01 mike /USR/SBIN/CRON[14637]: (www-data) CMD ([ -f /usr/share/moodle/admin/cron.php ] && /usr/bin/php -f /usr/share/moodle/admin/cron.php > /dev/null)
Oct  7 19:55:29 mike kernel: [269418.463652]  CIFS VFS: server not responding
Oct  7 19:55:29 mike kernel: [269418.463658]  CIFS VFS: No response for cmd 50 mid 582
Oct  7 19:55:49 mike kernel: [269438.425779]  CIFS VFS: Error 0xffffff90 on cifs_get_inode_info in lookup of /foreigner/Permission To Rock (Disc 1)
Oct  7 19:56:09 mike kernel: [269458.388031]  CIFS VFS: Error 0xffffff90 on cifs_get_inode_info in lookup of /Funeral for a Friend
Oct  7 19:56:19 mike kernel: [269468.369804]  CIFS VFS: Error 0xffffff90 on cifs_get_inode_info in lookup of /Funeral for a Friend
Oct  7 19:56:39 mike kernel: [269488.331456]  CIFS VFS: Error 0xffffff90 on cifs_get_inode_info in lookup of /Prodigy - Their Law - The Singles 1990-2005 [2CD Edition]
Oct  7 19:56:49 mike kernel: [269498.312517]  CIFS VFS: Error 0xffffff90 on cifs_get_inode_info in lookup of /Prodigy - Their Law - The Singles 1990-2005 [2CD Edition]
Oct  7 19:56:59 mike kernel: [269508.293689]  CIFS VFS: Error 0xffffff90 on cifs_get_inode_info in lookup of /Prodigy - Their Law - The Singles 1990-2005 [2CD Edition]
Oct  7 19:57:19 mike kernel: [269528.255815]  CIFS VFS: Error 0xffffff90 on cifs_get_inode_info in lookup of /Splended Eddie
Oct  7 19:57:39 mike kernel: [269548.218077]  CIFS VFS: Error 0xffffff90 on cifs_get_inode_info in lookup of /Sex Pistols, The
Oct  7 19:57:49 mike kernel: [269558.201725]  CIFS VFS: Error 0xffffff90 on cifs_get_inode_info in lookup of /Sex Pistols, The
Oct  7 19:57:59 mike kernel: [269568.180369]  CIFS VFS: Error 0xffffff90 on cifs_get_inode_info in lookup of /Sex Pistols, The
Oct  7 19:58:19 mike kernel: [269588.142597]  CIFS VFS: Error 0xffffff90 on cifs_get_inode_info in lookup of /Funny songs
Oct  7 19:58:39 mike kernel: [269608.104734]  CIFS VFS: Error 0xffffff90 on cifs_get_inode_info in lookup of /AC-DC
Oct  7 19:58:49 mike kernel: [269618.085849]  CIFS VFS: Error 0xffffff90 on cifs_get_inode_info in lookup of /AC-DC
Oct  7 19:58:59 mike kernel: [269628.066977]  CIFS VFS: Error 0xffffff90 on cifs_get_inode_info in lookup of /AC-DC
Oct  7 19:59:09 mike kernel: [269638.048082]  CIFS VFS: Error 0xffffff90 on cifs_get_inode_info in lookup of /AC-DC
Oct  7 19:59:19 mike kernel: [269648.029194]  CIFS VFS: Error 0xffffff90 on cifs_get_inode_info in lookup of /AC-DC
Oct  7 19:59:29 mike kernel: [269658.010311]  CIFS VFS: Error 0xffffff90 on cifs_get_inode_info in lookup of /AC-DC
Oct  7 19:59:39 mike kernel: [269667.991486]  CIFS VFS: Error 0xffffff90 on cifs_get_inode_info in lookup of /AC-DC
Oct  7 19:59:49 mike kernel: [269677.972538]  CIFS VFS: Error 0xffffff90 on cifs_get_inode_info in lookup of /AC-DC
Oct  7 20:58:43 mike syslogd 1.5.0#1ubuntu1: restart.
Oct  7 20:58:43 mike kernel: Inspecting /boot/System.map-2.6.24-19-generic
Oct  7 20:58:43 mike kernel: Loaded 28491 symbols from /boot/System.map-2.6.24-19-generic.
```

Anyone got any ideas?

Thanks,
Mike

---

