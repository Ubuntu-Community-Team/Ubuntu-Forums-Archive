---
title: "[SOLVED] Mail notification icon-click actions"
date: 2008-07-28
forum: General Help
---

### Post by the real omni on 2008-07-28
Hi,

Using Ubuntu 8.04 and mail-notification 5.4

I'm wondering how I can set Mail Notification do perform two actions when I click the tray icon.

In the preferences I only see four either-or options: launch mail reader, open latest message, consider new mail as read, and update the mail status. No way to combine them, which is odd as every other major POP3/TLS scanner I've ever used does ALL of those with a single click on the tray icon.

What I want is specifically to open the mail reader and then consider the new messages as read and hide the tray icon until there's more new mail.

Right now, I have mail-notification set to launch the mail reader when I click on the tray app. That means I also have to go back to the system tray, right-click the icon, and select "consider new mail as read."

Is there a way to do this?

Thanks

---

### Post by the real omni on 2008-08-09
Still trying to get this one figured out...

---

### Post by the real omni on 2008-09-28
SOLVED: 

ALT+F2 to bring up the run dialog, and run 

gconf-editor

In gconf-editor, navigate to

apps -> mail-notification -> commands -> new-mail

Enter the command you'd like to run in the 'command' field.

Simple as that! :)

---

