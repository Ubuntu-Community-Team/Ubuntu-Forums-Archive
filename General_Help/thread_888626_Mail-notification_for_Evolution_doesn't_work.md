---
title: "Mail-notification for Evolution doesn't work"
date: 2008-08-13
forum: General Help
---

### Post by anlag on 2008-08-13
Having been a Thunderbird user for some time, I thought after a reinstall that I should try the built-in mail client, Evolution. It seems fair enough, apart from one or two things that are not related to this thread.

But a necessity for me to be able to use it, is that I have a proper notification utility that alerts me to new mail, and without me having to have the whole program window open. This isn't working at the moment.

I've installed the mail-notification package, as well as mail-notification-evolution. I've also gone to Jean-Yves Lefort's site and got the latest version of it there, as well as making sure his own mail-notification plugin is installed in Evolution. It's a no-go. First, before I moved on to Lefort's stuff, I'd simply not get any tray notifications unless Evolution was already open. Not too useful. And with Lefort's latest version, when I set mailbox type to Evolution, it simply says: "Mail Notification can not contact Evolution", referring to the mentioned plugin and that the program should be running. Both seen to.

Actually, at the moment, although I thought I had uninstalled Lefort's latest version as well as the repository ones before reinstalling the latter, it still looks like the configuration utility is that of the latest version (from Lefort's site.) It also won't open a window unless I run it with sudo.

Any ideas or suggestions? I'm a bit stumped, but really would like to get this working. I know about Alltry as I used that with Thunderbird earlier, but for one its functionality was limited (would only pop up an alert on the first new mail, among other things) and for another, if I can avoid having the whole mail client open all the time, I'd prefer that.

I'm running Ubuntu 8.04 and using Gnome.

Thanks in advance.

---

### Post by Sand Lee on 2008-10-07
I've got the same problem. I've had to use the mail-notification plugin (synaptic) to access the IMAP server directly as a workaround. Does anyone know how to actually make Evolution's default plugin actually work?

---

### Post by maks_zbogar on 2008-12-16
Same here... Sorry, no solution.
Have been looking for any solution since I installed Intrepid in November 2008, but no result. As I was told, Evolution 2.24.2 use mysql so it can't be read with Mail notification and also can't be indexed with Tracker or Beagle. All these programs read only old Evolution plain text format. I hope there will soon be any update, or I will have to switch to Thunderbird.

---

### Post by webdebbyjoss on 2009-04-07
same problem, where can I found the detailed information about Evolution+MySQL mentioned in previous post?? It looks like a great news, but I can't find any information about this on the web.

---

### Post by andrewski on 2009-05-29
Yup, seems like a bug: [https://bugs.launchpad.net/mail-notification/+bug/376812](https://bugs.launchpad.net/mail-notification/+bug/376812)

---

