---
title: "Wrong permissions on delivered mail"
date: 2008-09-14
forum: General Help
---

### Post by MadEgg on 2008-09-14
I have a mail server using fetchmail, postfix, procmail, dovecot, using maildir, not mbox.

I use procmail for delivering mail with a certain subject to different mailfolders. This used to work on my old server running Gentoo, but I recently switched to Ubuntu Server. After some hassle I got it all to work with maildir since Ubuntu uses mbox by default, but a problem I now run into is that filtered mail gets the wrong permissions.

Normal mail, delivered to INBOX, is fine. But when a mail has a '[All]' in the subject, which should trigger it to move to the .AI box, it gets the wrong permissions: 'root:root' instead off 'eggie:users', which would be appropriate for my account, just like all the other mails.

Can anyone tell me what could be causing this?

Thanks!

---

### Post by Sycron on 2008-09-14
I've had this problem 1 year ago... I've fixed it somehow. I was edited a file with permissions. It's easy if you have gnome. System-administratuion-userandgroups-permissions

---

### Post by MadEgg on 2008-09-14
Could you be a bit more specific? 

I mean 'System-administratuion-userandgroups-permissions', where do I do that? 

What users and permissions need to be changed?

---

### Post by Sycron on 2008-09-14
It doesn't work if you don't have GNOME...

---

### Post by MadEgg on 2008-09-14
I don't really see the link between Procmail and GNOME, but I want this fixed so if I need to use any gnomish something I can always install it...

---

### Post by Sycron on 2008-09-15
Don't install GNOME. It's not worthy.

---

### Post by MadEgg on 2008-09-15
Right, I (kind of) figured it out.

This was my /etc/procmailrc
```

# Use maildir-style mailbox in user's home directory
DEFAULT=$HOME/.maildir/
SHELL=/bin/sh
PMDIR=$HOME/.Procmail
LOGFILE=$PMDIR/pmlog
MAILDIR=$HOME/.maildir/
INCLUDERC=$PMDIR/rc.subscriptions

```

I created this to make sure the maildir format was used instead of mbox, since without this file, even though the ~/.procmailrc said otherwise, procmail would deliver to /var/spool/mail/$USER. Removing most of the lines from /etc/procmailrc fixed it. It now is:

```

# Use maildir-style mailbox in user's home directory
DEFAULT=$HOME/.maildir/

```

This gives proper permissions on newly created files and also filters mail correctly.

---

### Post by Sycron on 2008-09-15
Good job! :D

---

