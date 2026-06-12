---
title: "moving kontact to other computer"
date: 2005-11-04
forum: General Help
---

### Post by Joenco on 2005-11-04
Hello,

I have two computers with kubuntu breezy.
Is it possible to move all kontact files from one to the other in a simple way?

Thank you,

---

### Post by lerrup on 2005-11-08
A usb stick?

They are located under /home/.kde/ somewhere.  You should be able to just copy and paste across to the other /home directory (just make sure the path is the same from /.kde in).

---

### Post by jeremy on 2005-11-08
You will need the relevant folders from
.kde/share/apps 
and the relevant files from
.kde/share/config
and std.vcf from .kde/share/apps/kabc
As far as I remember that is all.

---

### Post by asimon on 2005-11-08
If "all kontact files" includes your mail then I think kmail also uses ~/Mail.

BTW the Contacts, Calendar, To-do List, Journal, and Feeds parts have an export and import functionality, have a look at the File menu. But kontact and especially kmail is missing some easy 'catch-all' import/export.

---

### Post by daller on 2005-11-08
[QUOTE=asimon]If "all kontact files" includes your mail then I think kmail also uses ~/Mail.

BTW the Contacts, Calendar, To-do List, Journal, and Feeds parts have an export and import functionality, have a look at the File menu. But kontact and especially kmail is missing some easy 'catch-all' import/export.[/QUOTE]

If we are talking Breezy, it's this dir:

~/.kde/share/apps/kmail/mail

---

### Post by asimon on 2005-11-08
[QUOTE=daller]If we are talking Breezy, it's this dir:
~/.kde/share/apps/kmail/mail[/QUOTE]
You're right for most settings. From the Kmail FAQ:
> 6.4.  Where does KMail save my settings and my mail?
  Most KMail settings are stored in $KDEHOME/share/config/kmailrc, where $KDEHOME is typically ~/.kde; the identities are stored in $KDEHOME/share/config/emailidentities and your mail is saved in $KDEHOME/share/apps/kmail (or ~/Mail if you upgraded from a previous KMail version that used this location.) Note that some of the files are hidden: remember to also copy those if you want to backup or archive your mails.
So better check out both locations.

---

