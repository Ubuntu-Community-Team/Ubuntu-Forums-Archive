---
title: "Basic SMTP"
date: 2008-09-02
forum: General Help
---

### Post by envygeeks on 2008-09-02
Is there an application that is built specifically to create a sendmail for scripts and scripts only.  No relay, well, I assume it would be relay all points considering, but not external relay, not external SMTP, I just simply want it to send mail from scripts.  And only scripts.  It would be a huge waste of resources to full blast an SMTP server simply for application mail.


Thanks.

---

### Post by koenn on 2008-09-02
I don't quite understand what it is you're trying to do :
If you're sending mail (from scripts), you obviously want them sent to somebody, and I don't see how that's going to work without an SMTP ('mail') server taking care of the transport.

but for mail from scripts you could look in to the 'mail' command (might require the mailx package to be installed), or nullmailer (google, man)

---

### Post by monkeyking on 2008-09-02
I think mail is set up per install default on ubuntu.

Try typing mail,
and see what happens.

if it works then make you scripts send email to loginname@localhost

Then you will recieve all your mails in your local mailbox.

But I would rather use ssmtp, and then create an external mail,
like gmail that support remote smptp access, and then use your gmail as forwarding mailserver.

I've set it up, so I from the command line can send email like.

```
echo "emailtextbody"|mutt -s "subject" my@email.com 
```
Mutt is just emailclient. mutt also supports attachments.
you just add -a file.txt

---

