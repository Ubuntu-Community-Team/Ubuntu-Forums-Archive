---
title: "Ubuntu GMail Notifier"
date: 2008-11-18
forum: General Help
---

### Post by planetzpmq on 2008-11-18
Is there such thing as a simple GMail notifier for Ubuntu?  One where I can just open a package and install?  I don't need an actual mail app because I want to use the GMail interface online.  I just need a notifier.

---

### Post by Simian Man on 2008-11-18
There is a [screenlet]("http://www.screenlets.org/index.php/Gmail") that will show your unread message count on your desktop.  I believe it is included in the screenlets package so:

> sudo apt-get install screenlets

Should get you started.

---

### Post by planetzpmq on 2008-11-18
I'm brand new to Ubuntu.  Is that a command line or something?

---

### Post by edu1962 on 2008-11-18
You can use mail notification in system tray
mail-notification works with system trays implementing the
freedesktop.org System Tray Specification, such as the GNOME Panel
Notification Area, the xfce4 Notification Area and the KDE System Tray.

 Mail Notification features include:
  * multiple mailbox support
  * mbox, MH, Maildir, Sylpheed, POP3, IMAP, Gmail and Evolution support
  * Mozilla products (Mozilla, SeaMonkey, Thunderbird, ...) mailbox support
  * SASL authentication support
  * APOP authentication support
  * SSL/TLS support (disabled, see README.Debian)
  * automatic detection of mailbox format
  * immediate notification (depends on your settings)
  * HIG 2.0 compliance

 Note: Evolution support is available with mail-notification-evolution.

 Homepage: [http://www.nongnu.org/mailnotify/](http://www.nongnu.org/mailnotify/)

---

### Post by whitethorn on 2008-11-18
> **edu1962 said:**
> You can use mail notification in system tray
mail-notification works with system trays implementing the
freedesktop.org System Tray Specification, such as the GNOME Panel
Notification Area, the xfce4 Notification Area and the KDE System Tray.

 Mail Notification features include:
  * multiple mailbox support
  * mbox, MH, Maildir, Sylpheed, POP3, IMAP, Gmail and Evolution support
  * Mozilla products (Mozilla, SeaMonkey, Thunderbird, ...) mailbox support
  * SASL authentication support
  * APOP authentication support
  * SSL/TLS support (disabled, see README.Debian)
  * automatic detection of mailbox format
  * immediate notification (depends on your settings)
  * HIG 2.0 compliance

 Note: Evolution support is available with mail-notification-evolution.

 Homepage: [http://www.nongnu.org/mailnotify/](http://www.nongnu.org/mailnotify/)

+1 works with popmail at gmail. Just don't forget to activate pop mail in the settings menu in gmail.

---

### Post by oldos2er on 2008-11-18
Checkgmail, and gmail-notify are a couple I've used.

---

