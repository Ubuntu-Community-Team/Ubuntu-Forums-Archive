---
title: "connection refused to IMAP server"
date: 2008-11-05
forum: General Help
---

### Post by meles on 2008-11-05
I am suddenly unable to connect by IMAP to my mail server for one of my accounts.
When trying to refresh folders of any of the account associated with this mail server, I get the error:

Error while refreshing folder
Could not connect to mail.jswagner.com: Connection refused

This error and refusal to connect to the server seems to appear only in Ubuntu Intrepid Ibex 8.10. But here it seems to be general in the entire OS when trying to connect by IMAP. The same error in Evolution, Thunderbird, Kmail.

This error, however, doesn't occur in other operating system. I can access the mail server in Ubuntu 8.04, Windows XP using Pegasus Mail, on my PDA with Palm OS and Snapper emailer, etc.

Does anyone have an idea of what might be causing the problem?
Is this a Ubuntu 8.10 specific problem? Or something on the server? Or a combination of both?

I would appreciate any help

Thank you

---

### Post by jrdecastro on 2008-12-18
I have basically the same problem - Evolution throws the same error if I use TLS with a client cert but it does not if I use SSL.
If I use SSL the full header of received messages then says "the client did not present a certificate", but at least it works and I can see the folders.
Will be very interested in the solution

---

