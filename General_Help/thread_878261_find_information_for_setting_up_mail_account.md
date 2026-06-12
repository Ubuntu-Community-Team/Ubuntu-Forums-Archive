---
title: "find information for setting up mail account"
date: 2008-08-02
forum: General Help
---

### Post by pytheas22 on 2008-08-02
I have a user who has a corporate email account.  At work, she uses Outlook for mail (there is no webmail), and it's configured by the IT people there, who provide no public documentation on how their mail system works.  The user wants to configure Evolution for the mail account so that she can check her mail at home.

The only information I know is her username, password and mail server address (which I figured out by knowing the corporate domain and using "host").  I have no idea whether the mail server uses IMAP, POP, Exchange or what.  I could try to get it working in Evolution through trial and error, but I was wondering if there's any easy way to figure out the mail server's configuration.  The user claims that when she tries to view configuration information for her account in Outlook, she's denied access.

I was thinking that maybe I could portscan the mail server to figure out some information, but I would like to use a friendlier approach if possible.  Are there any Linux utilities that can connect to a mail server and figure out which protocols it uses, what kind of encryption is necessary and so on?

Or if I do go with the portscanning approach, does anyone happen to know what exactly I should be looking for (e.g., would it be possible to distinguish an IMAP server from a POP server based on which ports are open)?

Thanks in advance for any help.

---

