---
title: "Jaunty Evolution: Problem recovery backup"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by waffen on 2009-04-23
Hello,

I try to recovery my Evolution Backup tar.gz file (file make with Evolution, data Oct 2008) and receipt this error:

```


mario@mario-laptop:~$ evolution --component=mail

(evolution:17555): camel-WARNING **: camel_exception_get_id called with NULL parameter.
em-migrate.c:3033:migrate_to_db: failed to get folder infos 
em-migrate.c:3033:migrate_to_db: failed to get folder infos 
em-migrate.c:3033:migrate_to_db: failed to get folder infos 
em-migrate.c:3033:migrate_to_db: failed to get folder infos 
addressbook_migrate (2.22.0)
** (evolution:17555): DEBUG: mailto URL command: evolution %s
** (evolution:17555): DEBUG: mailto URL program: evolution
** (evolution:17555): DEBUG: EI: SHELL STARTUP
.evolution/
** Message: First result 0
.evolution/backup-restore-gconf.xml
** Message: Second result 0
** Message: Sanity check result 1:0 0
** Message: evolution --force-shutdown
Cerrando evolution-exchange-storage (Backend de Calendario de Exchange / Backend de libreta de direcciones de Exchange de Evolution)
Cerrando evolution-data-server-2.26 (Soporte de calendario y webcal de Evolution / Soporte de libretas de direcciones en archivo local de Evolution)
Cerrando evolution-alarm-notify (Servicio de notificación por alerta del Calendario de Evolution)
** Message: mv /home/mario/.evolution/ /home/mario/.evolution-old/
** Message: mv /home/mario/.camel_certs ~/.camel_certs_old
** Message: cd /home/mario && gzip -cd '/home/mario/Downloads/evolution-backup-20081024.tar.gz'| tar xf -
** Message: gconftool-2 --load /home/mario/.evolution/backup-restore-gconf.xml
** Message: rm -rf /home/mario/.evolution/backup-restore-gconf.xml
** Message: rm -rf /home/mario/.evolution-old/
** Message: rm -rf /home/mario/.camel_certs_old
** Message: rm /home/mario/.evolution/.running
rm: no se puede borrar «/home/mario/.evolution/.running»: No existe el fichero ó directorio
** Message: evolution
mario@mario-laptop:~$ 
(evolution:17888): camel-WARNING **: camel_exception_get_id called with NULL parameter.

(evolution:17888): camel-WARNING **: Cannot load summary file: '/home/mario/.evolution/mail/local/Spe.ev-summary': No existe el fichero ó directorio

GLib-ERROR **: /build/buildd/glib2.0-2.20.1/glib/gmem.c:136: failed to allocate 8084107592 bytes
aborting...
Aborted


```

:confused: any idea? I cant acces my emails... 1.8 GB!

I use Jaunty uptodate...

---

### Post by waffen on 2009-04-25
anybody there have the same problem?? :confused:

---

### Post by waffen on 2009-04-27
I put the solution obtained from the Evolution list:

2009/4/27 Akhil Laddha <lakhil@novell.com>

    Are you trying to move summary from i586 arch to x86_64 arch ?


Uhm... I dont remember because this is an old backup since October 23 2008.. its posible because I start usins Ubuntu 8.10 with 64 bits.

 


    [snip from Thomas's mail]

    Remove the corresponding files with the file ending ".ev-summary" and
    ".ibex.index", in this example you should remove the file
    "~/.evolution/mail/local/Inbox.ev-summary" and
    "~/.evolution/mail/local/Inbox.idex.index".
     * Restart evolution, it will be slow to come up because it recreates
       the indexes.

    Hope it will help you.

    Regards,
    Akhil


YES!! its work perfect!!

Thanks!!

---

### Post by frbe0101 on 2009-05-28
Yeah that fixed the problem for me too, someone at the evolution workgroup should make a script to fix this problem in x32 to x64 conversion.

---

### Post by matt8400 on 2009-09-09
I performed this restore method
(in ~/.evolution )
find . -name "*.ibex.index" -exec rm {} \;
find . -name "*.ev-summary" -exec rm {} \;

Unfortunately now it doesn't work, I get
"""
(evolution:32240): camel-WARNING **: camel_exception_get_id called with NULL parameter.
(evolution:32240): Pango-CRITICAL **: pango_layout_get_line_count: assertion `layout != NULL' failed
Floating point exception
"""

---

### Post by molibdeno on 2011-04-20
I had a similar problem after upgrading from Hardy to Lucid.

Try upgrading/reinstalling libpango and libcamel packages.

---

### Post by fonsi2099 on 2011-07-13
After upgrading from Unity to Gnome3 and back to Unity. I had a similar problem: 
thanks in advance for cour help.

~$ evolution
(evolution:4844): GLib-GObject-CRITICAL **: Object class EMFolderTree doesn't implement property 'paste-target-list' from interface 'ESelectable'
(evolution:4844): GLib-GObject-CRITICAL **: Object class EMFolderTree doesn't implement property 'copy-target-list' from interface 'ESelectable'
e-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
e-data-server-ui-Message: Key file does not have group 'Passwords-Mail'
e-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
e-data-server-ui-Message: Key file does not have group 'Passwords-Mail'

(evolution:4844): camel-local-provider-WARNING **: Summary doesn't match the folder contents!  eek!
  expecting offset 0 got -1, state = 8

(evolution:4844): camel-local-provider-WARNING **: Summary doesn't match the folder contents!  eek!
  expecting offset 0 got -1, state = 8

(evolution:4844): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
**
camel:ERROR:camel-mime-message.c:627:camel_mime_message_get_subject: assertion failed: (mime_message)
Aborted

---

### Post by bart.nicolotti@libero.it on 2011-09-01
I've had a similar problem exporting mail from Ubuntu 8.04 32bit + evolution 2.22 to Ubuntu 10.04 64bit + evolution 2.28.3. We've worked around this problem in 2 step: 1st from Ubuntu 8.04 32bit to Ubuntu 10.04 32bit and then to Ubuntu 10.04 64bit, all went well. I hope this helps :-D

---

