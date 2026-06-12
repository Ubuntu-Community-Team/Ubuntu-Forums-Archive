---
title: "Pop3 client for simple download"
date: 2008-09-05
forum: General Help
---

### Post by Ole Juul on 2008-09-05
I wish to simply download mail from various accounts and put them in the current (or specified) directory. There does not seem to be a lot of choice in POP3 clients so I am trying fetchmail as a start - unfortunately it is very slow and does not work for me yet. I did not set up a configuration file as I understand that fetchmail will work entirely from the command line.

Can someone give me a working command line?

Here is what I'm using and the output:

ole@SCO:~/DOWN$ fetchmail -v -u test mail.coalmont.net
Enter password for [email]test@mail.coalmont.net[/email]:
fetchmail: 6.3.2 querying mail.coalmont.net (protocol auto) at Fri 05 Sep 2008 04:48:30 PM PDT: poll started
fetchmail: 6.3.2 querying mail.coalmont.net (protocol IMAP) at Fri 05 Sep 2008 04:48:30 PM PDT: poll started
fetchmail: IMAP< * OK mail-pop3 ready.
fetchmail: IMAP> A0001 CAPABILITY
fetchmail: IMAP< * CAPABILITY IMAP4rev1 SASL-IR SORT THREAD=REFERENCES MULTIAPPEND UNSELECT LITERAL+ IDLE CHILDREN NAMESPACE LOGIN-REFERRALS UIDPLUS LIST-EXTENDED I18NLEVEL=1 STARTTLS AUTH=PLAIN AUTH=LOGIN
fetchmail: IMAP< A0001 OK Capability completed.
fetchmail: IMAP> A0002 STARTTLS
fetchmail: IMAP< A0002 OK Begin TLS negotiation now.
fetchmail: Issuer Organization: GlobalSign nv-sa
fetchmail: Issuer CommonName: GlobalSign Domain Validation CA
fetchmail: Server CommonName: *.superb.net
fetchmail: Server CommonName mismatch: *.superb.net != mail.coalmont.net
fetchmail: mail.coalmont.net key fingerprint: 53:21:1C:EF:48:10:98:22:0B:47:7E:F7:41:3F:DE:FA
fetchmail: IMAP> A0003 CAPABILITY
fetchmail: IMAP< * CAPABILITY IMAP4rev1 SASL-IR SORT THREAD=REFERENCES MULTIAPPEND UNSELECT LITERAL+ IDLE CHILDREN NAMESPACE LOGIN-REFERRALS UIDPLUS LIST-EXTENDED I18NLEVEL=1 AUTH=PLAIN AUTH=LOGIN
fetchmail: IMAP< A0003 OK Capability completed.
fetchmail: mail.coalmont.net: upgrade to TLS succeeded.
fetchmail: IMAP> A0004 LOGIN "test" *
fetchmail: IMAP< A0004 NO Authentication failed.
fetchmail: IMAP> A0005 *
fetchmail: Authorization failure on [email]test@mail.superb.net[/email]
fetchmail: IMAP> A0006 LOGOUT
fetchmail: IMAP< A0005 BAD Error in IMAP command received by server.
fetchmail: IMAP< * BYE Logging out
fetchmail: IMAP< A0006 OK Logout completed.
fetchmail: 6.3.2 querying mail.coalmont.net (protocol IMAP) at Fri 05 Sep 2008 04:48:35 PM PDT: poll completed
fetchmail: 6.3.2 querying mail.coalmont.net (protocol auto) at Fri 05 Sep 2008 04:48:35 PM PDT: poll completed
fetchmail: Query status=3 (AUTHFAIL)
fetchmail: normal termination, status 3
ole@SCO:~/DOWN$

---

### Post by wolfen69 on 2008-09-05
i find Thunderbird to be a great mail client.

---

### Post by Ole Juul on 2008-09-05
Thanks, but Thunderbird is not going to work for me. I just looked at it and to make it work on a console is probably way beyond my skills. :)

fetchmail, getmail, or maybe mpop, are better choices. I'm trying fetchmail first but just need a little help getting started.

---

