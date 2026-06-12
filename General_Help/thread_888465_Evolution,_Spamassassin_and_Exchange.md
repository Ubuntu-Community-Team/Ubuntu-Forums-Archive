---
title: "Evolution, Spamassassin and Exchange"
date: 2008-08-13
forum: General Help
---

### Post by Edricson on 2008-08-13
Hi,

I'm using Evolution to read my mail on an Exchange server. I am also using Spamassassin to fight junk. My problem is that I cannot find where Evolution puts the junk. If a junk post slips into the Inbox, I mark it as spam, it disappears from view but it does not go to the junk folder either on the Exchange server or on the machine. Moreover, if I check the web interface for the account, the spam is still there. On the other hand, I cannot find the false positives to mark them as not spam (thankfully, they are also available through the web interface, but this is annoying).

Can anyone help me with this?

Thanks!

---

### Post by bmac on 2008-08-13
I believe the junk mail info is in /evolution/mail/vfolder. Evolution is probably a hidden folder on your account...

---

### Post by Edricson on 2008-08-14
Umm, no, ~/.evolution/mail/vfolder contains just a file UNMATCHED.cmeta which as far as I can see contains nothing useful.

---

