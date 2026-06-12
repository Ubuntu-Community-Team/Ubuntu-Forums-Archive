---
title: "Maildir mail not seen by Evolution"
date: 2008-09-13
forum: General Help
---

### Post by ubunteduser on 2008-09-13
I am trying to recover email from another computer. I copied the Maildir files over and opened an account under Evolution to point to the Maildir where my messages are. 

Evolution does not see the messages even though there are plenty of messages under the cur directory. Evolution does recognize how many messages are suppose to be in there, since when I right click on the inbox of the account and look at properties, it reports the number of messages. But they do not appear in the inbox.

Can anyone help me with recovering those messages? Thanks.

---

### Post by noobissima on 2008-10-31
I have the same problem, my mail are located on ~/Mail.

Using evolution and imap, how to change the server directory of the mail?

---

### Post by nnahler on 2008-12-10
Edit -> Preferences -- Choose your account to edit -- Account Editor -> Choose Tab: Receiving Options -> Under 'Folders' tick the box 'Override server-supplied namespace' and  in the field below fill in your directory.

I find this option a bit disappointing though as the folder structure in evolution ends up as:

INBOX
Junk
~.mail.directory
-- 1st folder
-- 2nd folder
-- ...

Where I would prefer:

INBOX
Junk
1st folder
2nd folder
...

But I did not figure out yet how to achieve this. Anybody an idea?

This works in Thunderbird very nicely :-(

---

