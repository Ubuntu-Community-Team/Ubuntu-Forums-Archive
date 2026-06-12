---
title: "why was nail dropped from hardy?"
date: 2008-07-25
forum: General Help
---

### Post by r.stiltskin on 2008-07-25
I used to use nail with msmtp to send a simple email from a perl script.  Just upgraded to Hardy and found that nail is no longer in the repositories.  I'm trying to use mailx instead of nail, but I haven't figured out how to configure it to work with msmtp.   Instead it seems to go directly to my isp's server & I don't see how to get it to login.  So the server is rejecting my messages: 
```
SMTP<< 550 5.7.1 Authentication Required
  SMTP<< 503 5.5.0 No MAIL FROM command has been issued.
  SMTP<< 503 5.5.0 No MAIL FROM command has been issued.
  SMTP>> QUIT
```

I have no problem configuring msmtp -- I've already done that & tested it & I can send emails from the command line using msmtp alone.  I can also send regular emails using evolution.  So my problem is just with mailx.  Is there an easier replacement for nail?  Or can mailx be configured to serve this purpose?


Edit: I just found & installed smail.  I'll see if that will serve the purpose.

---

