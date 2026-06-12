---
title: "Pidgin 2.5.0 Several XMPP accounts (certificate problem)"
date: 2008-08-25
forum: General Help
---

### Post by lunatico on 2008-08-25
Hello!

The good news is that Pidgin 2.5.0 has been released and it works in Hardy. I installed the deb package from [getdeb]("http://www.getdeb.net/release.php?id=3100").

I do have a small weird problem.

I have two XMPP accounts configured. One @gmail.com and the other one @tcd.ie which is my college email server. They use google services.
On previous Pidgin versions it worked with no problem. After I installed 2.5 and logged in the first time it asked me to accept certificates, 3 for my MSN account and then two for talk.google.com.
The talk.google.com was asked twice actually, I suppose one per each XMPP account.
The problem is that each time I open Pidgin it will ask me to accept a talk.google.com certificate again.

Basically what I think it's happening is that it can't handle two certificates with the same name (talk.google.com) for different accounts, or in different servers.

Is this only me? Any ideas?

I already sent an email to [email]support@pidgin.im[/email]. If they provide any feedback I'll post it here.

If anyone knows how to fix this or anything please post.

Thank you!

---

### Post by lunatico on 2008-08-25
Right! I figured this myself.

Basically both XMPP accounts where using talk.google.com as the server, but it could not handle two certificates for different account on the same server.
So what I did was to use talk.google.com on my @gmail account and talk.l.google.com on the other @tcd.ie account.
Both names resolve to the same server after DNS but for Pidgin they are different servers.
This is a bug I think. Not sure if I can be bothered to file it...

---

