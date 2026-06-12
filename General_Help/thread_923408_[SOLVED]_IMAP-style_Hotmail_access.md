---
title: "[SOLVED] IMAP-style Hotmail access?"
date: 2008-09-18
forum: General Help
---

### Post by BenWT on 2008-09-18
I know there are a few threads on these issues, but I haven't been able to resolve this from them. Apologies if I've missed one that did answer the question!

I've had a hotmail account for a very long time (**i.e. old enough that webDAV should be available, according to the wikipedia article**) and have just gotten ubuntu (hardy). I also have a university email account. In windows outlook, I was able to access hotmail in the same way as my imap university email, so that everything remained on the server, and deletions and read/unread markings were synchronised between outlook and the website access. I'm looking for a way to recreate this in ubuntu. I've tried both evolution with hotwayd and thunderbird with the webmail extension - both worked great with my uni email, but not with hotmail. While I can download and send messages (and managed to get thunderbird to work with 2 separate smtp's) neither client will synch properly with hotmail. Thunderbird just downloaded all my messages, marked them as "unread" on my computer and "read" on the server.

Hotmail won't forward to anything that doesn't belong to microsoft, so I can't just forward to a googlemail or to my university email and access that via IMAP. I know hotmail is an awful choice, but the hassle of changing email addresses is even worse than just giving up and logging into the windows live mail website all the time!



Oh, and how I do I make thunderbird the default email application?

Many thanks!

---

### Post by salukibob on 2008-09-28
Hi There,

I have been having exactly the same problem as you for god knows how long. Sadly, as all the available options are POP3 based, it pretty much useless for my need (accessing folders other than INBOX).

Until now... I came across a service called IzyMail ([http://v3.izymail.com/](http://v3.izymail.com/)) that properly support HTTPMail to IMAP. You have to register with them, and direct your email client to their servers. Your emails are read from Hotmail/Yahoo/etc, and sent to you via IMAP. They effectively translate at the server end. It has proper folder and sync support. I've signed up, and been very impressed so far. The service is free for a set of fixed options, or to allow full control, you pay about $1.50 a month. 

So far, its the ONLY option i've found that allows proper sync and folder access, which I find quite unbelievable really, as POP3 is so unbelievably restrictive. But there you go.

To answer your other question, if you use the ubuntu menu and go to System->Preferences->Preferred Applications, you should be able to select thunbderbird as your default email client.

Hope that helps
Cheers
Rob

---

### Post by BenWT on 2008-09-28
Cheers - I'll check that out!

---

