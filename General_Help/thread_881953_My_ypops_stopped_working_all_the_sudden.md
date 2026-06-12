---
title: "My ypops stopped working all the sudden"
date: 2008-08-06
forum: General Help
---

### Post by puifais on 2008-08-06
I have been using ypops to check my free yahoo account.  It's worked fine until it stopped ](*,)...  Now it says, "Error while performing operation.  DATA command failed:  Mailbox unavailable" when I'm trying to send.  For checking emails, it doesn't give any errors, but it keeps "waiting" and never finishes checking emails.

I looked around and try to find out if I just need to change the configuration of Evolution or ypops itself.  Everyone seems to set up ypops the same way.  Evolution settings, however, seem to vary a little bit:  some people do SSL encryption, some don't.  Some put [email]username@yahoo.com[/email] instead of just username in email receiving option, etc, etc.

Any ideas?  I'm posting my ypops log below just incase it helps:

> [ Wed Aug  6 13:39:22 2008 ] YPOPs! Version 0.9.5.1
[ Wed Aug  6 13:39:22 2008 ] Configuration:
[ Wed Aug  6 13:39:22 2008 ]  Log Mode = Advanced (1)
[ Wed Aug  6 13:39:22 2008 ]  Use Proxy = 0, NTLM=0, HTTP Proxy = -:80, HTTPS Proxy = -:80
[ Wed Aug  6 13:39:22 2008 ]  Max Emails = 40, Leave as unread = 1
[ Wed Aug  6 13:39:22 2008 ]  Empty Trash = 0, Empty Bulk = 1
[ Wed Aug  6 13:39:22 2008 ]  Download Inbox = 1, Download BulkMail = 0
[ Wed Aug  6 13:39:22 2008 ]  Email Category = All
[ Wed Aug  6 13:39:22 2008 ]  Proxy Auth = 0, NTLM=0, Username = -, Password = -
[ Wed Aug  6 13:39:22 2008 ]  Quiet Mode = 1, Autostart = 0, Always on Top = 0
[ Wed Aug  6 13:39:22 2008 ]  Network IP = 127.0.0.1, POP3 Port = 5110, SMTP Enable = 1, SMTP Port = 5025
[ Wed Aug  6 13:39:22 2008 ]  Save Sent Email = 1, Enable UIDL = 1, Ignore Exact Size = 1, Hide Tray Icon = 0
[ Wed Aug  6 13:39:22 2008 ]  Apply Limit to Message List = 1, Cookie Timeout = 12000
[ Wed Aug  6 13:39:22 2008 ]  User Agent = Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0)
[ Wed Aug  6 13:39:22 2008 ] =========================================================================
[ Wed Aug  6 13:39:22 2008 ] <> Sending POP3 response to socket 7: +OK POP3 YPOPs! proxy ready
[ Wed Aug  6 13:39:22 2008 ] <> POP3 response sent: +OK POP3 YPOPs! proxy ready
[ Wed Aug  6 13:39:22 2008 ] Unknown AUTHORIZATION state command: CAPA
[ Wed Aug  6 13:39:22 2008 ] <> Sending POP3 response to socket 7: -ERR Unknown AUTHORIZATION state command
[ Wed Aug  6 13:39:22 2008 ] <> POP3 response sent: -ERR Unknown AUTHORIZATION state command
[ Wed Aug  6 13:39:22 2008 ] <puifais> Sending POP3 response to socket 7: +OK User name accepted, password please
[ Wed Aug  6 13:39:22 2008 ] <puifais> POP3 response sent: +OK User name accepted, password please
[ Wed Aug  6 13:39:22 2008 ] Starting POP3 session for "puifais".
[ Wed Aug  6 13:39:22 2008 ] <puifais> Password received from client.
[ Wed Aug  6 13:39:22 2008 ] <puifais> Previous session recycled
[ Wed Aug  6 13:39:22 2008 ] CookieJar set to = cookies-puifais.txt
[ Wed Aug  6 13:39:22 2008 ] <puifais> Previous session recycled, newapi=0
[ Wed Aug  6 13:39:22 2008 ] <puifais> Analyzing the INBOX folder
[ Wed Aug  6 13:39:22 2008 ] <puifais> inbox URL=http://us.mc569.mail.yahoo.com/ym/ShowFolder?box=Inbox&Npos=0&Nview=a&Norder=down&warnondelete=0
[ Wed Aug  6 13:39:22 2008 ] Content-Type = text/html; charset=iso-8859-1
[ Wed Aug  6 13:39:22 2008 ] <puifais> Page has been dumped to '/var/log/ypops/puifais.Inbox_page0.html' for analysis
[ Wed Aug  6 13:39:22 2008 ] <puifais> Page has been dumped to '/var/log/ypops/puifais.checkerror.html' for analysis
[ Wed Aug  6 13:39:22 2008 ] <puifais> You use 0% of your Yahoo! mailbox
[ Wed Aug  6 13:39:22 2008 ] <puifais> Extracted 0 message Id's from mailbox Inbox
[ Wed Aug  6 13:39:22 2008 ] <puifais> No messages were found. Folder probably empty
[ Wed Aug  6 13:39:22 2008 ] <puifais> Page has been dumped to '/var/log/ypops/puifais.Inbox_0msgs.html' for analysis
[ Wed Aug  6 13:39:22 2008 ] <puifais> INBOX folder analyzed
[ Wed Aug  6 13:39:22 2008 ] <puifais> Sending POP3 response to socket 7: +OK Mailbox open and analyzed
[ Wed Aug  6 13:39:22 2008 ] <puifais> POP3 response sent: +OK Mailbox open and analyzed
[ Wed Aug  6 13:39:22 2008 ] <puifais> Command received from email client: CAPA
[ Wed Aug  6 13:39:22 2008 ] <puifais> Sending POP3 response to socket 7: -ERR Unknown command
[ Wed Aug  6 13:39:22 2008 ] <puifais> POP3 response sent: -ERR Unknown command
[ Wed Aug  6 13:39:22 2008 ] <puifais> Command received from email client: UIDL 1
[ Wed Aug  6 13:39:22 2008 ] <puifais> Sending POP3 response to socket 7: -ERR no such message OR message marked as deleted OR message not downloaded
[ Wed Aug  6 13:39:22 2008 ] <puifais> POP3 response sent: -ERR no such message OR message marked as deleted OR message not downloaded
[ Wed Aug  6 13:39:22 2008 ] <puifais> Command received from email client: LIST
[ Wed Aug  6 13:39:22 2008 ] <puifais> Sending POP3 response to socket 7: +OK scan listing follows
[ Wed Aug  6 13:39:22 2008 ] <puifais> POP3 response sent: +OK scan listing follows
[ Wed Aug  6 13:39:22 2008 ] <puifais> Sending POP3 response to socket 7: .
[ Wed Aug  6 13:39:22 2008 ] <puifais> POP3 response sent: .
[ Wed Aug  6 13:39:22 2008 ] <puifais> Command received from email client: QUIT
[ Wed Aug  6 13:39:22 2008 ] <puifais> Sending POP3 response to socket 7: +OK YPOPs! signing off. Hope you enjoyed this program.
[ Wed Aug  6 13:39:22 2008 ] <puifais> POP3 response sent: +OK YPOPs! signing off. Hope you enjoyed this program.
[ Wed Aug  6 13:39:22 2008 ] <puifais> Emptying bulk mail folder
[ Wed Aug  6 13:39:22 2008 ] <puifais> URL: [http://us.mc569.mail.yahoo.com/ym/ShowFolder?EB=1&.crumb=&reset=1](http://us.mc569.mail.yahoo.com/ym/ShowFolder?EB=1&.crumb=&reset=1)
[ Wed Aug  6 13:39:23 2008 ] Content-Type = text/html; charset=iso-8859-1
[ Wed Aug  6 13:39:23 2008 ] <puifais> closing POP3 socket 7

---

### Post by Huggy on 2008-10-29
I am having the same issue as well. I thought it may be tied to the firewall so I turned it off, and I tried forwarding ports on my router as well with no luck. So I am out of ideas. It affects both the mail classic and mail beta. Your configuration looks the same as mine, but I can;t send anything due to the same error message. I can recieve all day though.

---

