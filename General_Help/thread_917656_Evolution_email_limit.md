---
title: "Evolution email limit?"
date: 2008-09-12
forum: General Help
---

### Post by krusty_ on 2008-09-12
Hi All,  (I hope this is in the right section... I can't find a better place to put it.)

I recently installed HH and am in the process of migrating about 120K emails across from my Windows environment.

First I'll explain what I've done and then what the problem is.

I installed an IMAP server (Macallen Mail Solution) on my Windows box and then using Outlook I dragged all my email across to the IMAP account in order to get them all onto the server.  These emails came from about 9 different PST files totalling about 11Gb of email.  This process worked fine and allowed me to access the email in the IMAP account perfectly.

On my other machine, I installed HH and configured Evolution to connect to the IMAP server and synchronize.  This was incredibly slow and effectively was useless.

So, I thought I'd use POP instead.  Deleted the IMAP account in Evo and created a POP account.  Set it to download and all was well... for a while.

I've noticed that Evo downloads about 100 - 200 messages before it errors out.  That's fine, I just set the download interval to every one minute and then it keeps trying.  So far, it's managed to bring down about 13000 emails and now I'm screwed.

I don't have my laptop here with me, but basically my inbox appears empty (although the message counter is still there).  Evo is not hung and I can send messages, change settings etc, but when I try to download I get a message in the status bar telling me that my inbox is full.

I navigated across to ~/.evolution/ blah blah and my inbox is 724Mb at the moment.

Google found me a reference that says Evo doesn't like mailboxes over 700Mb.  I can't believe that's true?

Does anybody have any suggestions:
1.  How do I get back those 13K messages which have been downloaded.  I assume they're in MBOX format so I can probably make a plan with installed T-Bird and bringing them across.
2.  More importantly, what I need is 1 email client that is going to just work.

My requirements aren't all that extensive, are they?:

120K emails need to be downloaded into one email account.  I have about 15 folders which contain certain emails based on automated rules.  The actual number of the messages in the INBOX will be relatively low.  I'm perfectly happy (and would like) to have archive folders as well.  This should allow me to spread the bulk of messages into folders that are used less frequently.

Can I do this with Evo?  If not, what do you recommend?  I can use T-Bird if I have to, but I'm not a huge fan, I should admit.

Any suggestions?

---

### Post by krusty_ on 2008-09-15
Nobody got any ideas for me?

---

