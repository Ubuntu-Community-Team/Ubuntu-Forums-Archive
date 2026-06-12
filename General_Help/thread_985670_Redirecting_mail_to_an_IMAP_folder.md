---
title: "Redirecting mail to an IMAP folder"
date: 2008-11-17
forum: General Help
---

### Post by xerxesdaphat on 2008-11-17
Hi,

Apologies if this is the wrong forum, it didn't really seem to belong in Networking/Wireless though, so I popped it in here.

I'm attempting to redirect mail from Hotmail to GMail. Harder than you'd think. The `hard' part is done -- freepops takes care of making the Hotmail mail available as a POP3 server, no issue there. GMail is accessible via IMAP. I don't want to send the mails to GMail via normal SMTP (sendmail or similar) -- it works at first, but eventually one gets a reply message about my IP not being authorised to send mail to GMail (apparently quite common).

So now I have the general problem of automatically taking mail from a POP3 server, and putting it into an IMAP folder. Fairly simple using Evolution or similar, but I'm not interested in a graphical program; this will be running on a headless server. I'm not familiar with Fetchmail/procmail etc.; have spent most of the afternoon googling to find information on this.

What's a good method of moving mail to an IMAP folder based on rules? It would seem fetchmail/getmail don't let me forward mail to an IMAP folder, only download the mail. Is there an MTA that does IMAP? If possible, I'd like to not even have the mail stored locally at all.

Thanks for helping me out with this, I'm a bit stuck -- I'm hoping I don't have to whip out the Perl and hack something up myself :)

---

