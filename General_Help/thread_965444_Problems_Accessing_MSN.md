---
title: "Problems Accessing MSN"
date: 2008-10-31
forum: General Help
---

### Post by Silvernotex on 2008-10-31
Having a look around a few people seem to be having this problem, using the applications so far (pidgin, emesene and amsn), I have been completely unable to access msn. However, back in the time I was running windows id been experiencing a similar problem using the official client? (fully updated Windows Live messenger). Is it possible they've moved the server? if so where to and if not, what can I do to get back to msn. At the moment im using [www.messengerfx.com](www.messengerfx.com) to talk to people, as you might imagine it doesn't have the capabilities of the proper IM's though

---

### Post by Ric_ on 2008-10-31
I don't think its MSN as my hotmail account connects fine. However I have the same problem with gtalk. It just sits there trying to connect and eventually (we are talking 5 mins plus) it time sout. 5 mins seems far too long to be a DNS time out which is what would happen if they'd tweaked stuff.

Its very odd. Seems to be lots of people having gremlins in pidgin, as of yet i haven't spotted a pattern. I'll dig around and see whats happening and run a few tcpdumps. I'll let you know if i find anything.

Ric_

:confused:

---

### Post by Ric_ on 2008-10-31
In regards gtalk there seems to be a problem with the template in pidgin 2.5.2 on ubuntu.

I had to modify the account and go into advanced settings.

Tick "Require SSL/TLS" and Tick "Force old (port 5223) SSL"

Set the "connect port:" to 443
and set the "Connect server:" talk.google.com

It should now connect and be fine :)

---

### Post by Hubris2 on 2008-11-02
From what I've been able to gather so far (the Pidgin SSL FAQ) Pidgin isn't allowing OpenSSL as a valid library because of a licensing issue.  It suggests recompiling after installing an alternate SSL library.

If this is a correct synopsis, unless we want to uninstall and compile ourselves, we're stuck waiting for an updated version of the binary.

---

### Post by Doug77 on 2008-11-03
I can rarely access msn through Pidgin (2.5.2), amsn, or kopete.  Emesene works in HTTP mode, but often appears to drop messages.

---

### Post by jesuisbenjamin on 2008-11-17
Hi,

After an fresh install of 8.10 it seems i am unable to connect to MSN through Pidgin. However i can connect to MSN via the web browser.
Could anyone help figure out why connection fails on Pidgin?

Here attached are my settings.

---

### Post by jesuisbenjamin on 2008-11-18
bump!

---

### Post by 3rdalbum on 2008-11-18
MSN has been taking longer to load up for me, and it seems to be putting some heavy amounts of data through my internet connection while doing so. It works fine once connected though. I don't know if this information will help you?

---

### Post by scouser73 on 2008-11-18
I can access MSN through pidgin with no problems and I use a Gmail account for my MSN.

---

### Post by jesuisbenjamin on 2008-11-18
> **scouser73 said:**
> I can access MSN through pidgin with no problems and I use a Gmail account for my MSN.

Do you mean that your msn buddies are listed in your gmail account? So you actually don't use your hotmail account to log onto the msn network?
If so how could i do that as well?

My msn simply for ever tries to connect, while my gmail account is running without problem...

---

### Post by scouser73 on 2008-11-18
My MSN contacts are all in Pidgin, so if you wanted to have the same set up as me, then set up a Gmail account, and then associate it with Microsoft Passport. [https://accountservices.passport.net/ppnetworkhome.srf?vv=600&lc=2057]("https://accountservices.passport.net/ppnetworkhome.srf?vv=600&lc=2057")

---

