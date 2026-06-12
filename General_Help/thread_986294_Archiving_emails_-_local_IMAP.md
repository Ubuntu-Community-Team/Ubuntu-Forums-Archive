---
title: "Archiving emails - local IMAP?"
date: 2008-11-18
forum: General Help
---

### Post by The_Fallen on 2008-11-18
Hi,

I was not sure, where to post this, since it's would probably fit in both the server and the desktop forums, so I ask here...

I'd like to archive my emails on a local IMAP server. Any recommendations? It should be small but secure, since I would like to allow access from the internet. 

Cheers,
fallen

---

### Post by deadowl on 2008-11-18
Well, IMAP, inherently, is not a protocol you use to archive emails. 

Fortunately, if your email provider provides IMAP access, it most likely provides POP access as well. If you'd like to be able to have messages on the server if you need access to them from another computer, but also be able to archive them on your machine, POP is what you want to use.

If this is what you want then you want to start with finding the pop mail server address. 

Some email services (like gmail) require you enable downloading via POP in their options/preferences. Most ISP emails don't require this.

They also frequently offer a walkthrough of how to do this in at least one application, and that will often include the server address (ex. pop.uvm.edu).

Essentially, in Evolution:
1. Select Edit->Preferences from the menu
2. Select "Mail Accounts" from the column on the left.
3. Select the account from which you want to archive email.
4. Click the "Edit" button on the righthand side.
5. Select the "Receiving Email" tab.
6. Type the server address you have found in the Server textbox.
6. From the Server Type box, select POP.
7. Under the "Receiving Options" tab, check off "Leave messages on server."

And that should allow you to archive your email locally, while also leaving it on the server so that you can access it from any computer when you need to.

---

### Post by The_Fallen on 2008-11-19
Thanks, but IMAP is exactly what I want to do. This way I can get the emails off my mail server, but still have access to them from everywhere, as long as my computer is online and I know its IP address.

---

