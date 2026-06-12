---
title: "Help with mail server - no connection"
date: 2008-10-29
forum: General Help
---

### Post by joel@parke.ods.org on 2008-10-29
Hi all,

I have been working on this for a few days and thus far no go.
The problem seems to be that many sites which used to send me email (until Friday) no longer are able to reach my Ubuntu server.  

I can send email to myself using gmail, but nothing else seems to arrive.  I have a dynamic IP address with comcast - is that an issue?  Please help as this is making me crazy.  

NOTE I have tried to test my smtp sever with [http://www.wormly.com/test_smtp_server](http://www.wormly.com/test_smtp_server), but this says 
Resolving hostname...
Connecting...
SMTP -> ERROR: Failed to connect to server: Connection timed out (110)
Message sending failed.

I have tested using telnet ministrynewengland.org 25 and that all works.  but emails to [email]joel@ministrynewengland.org[/email] seemingly go no where.  An alias for this sever is also parke.ods.org and emails to [email]joel@parke.ods.org[/email] are missing as well.  Could these be blocked because the site is a dynamic ip address? 

I am using ods.org as my NS and I do have an MX record for ministrynewengland.org.   

Any ideas would be greatly appreciated! 

Thanks!!!!

---

### Post by joel@parke.ods.org on 2008-10-29
I believe port 25 from comcast is not blocked and that seems to be the problem!  YUCK

So How can I tell smtp to use a different port?  What is the setting in main.cf - does anyone know?

Thanks,
Joel

---

