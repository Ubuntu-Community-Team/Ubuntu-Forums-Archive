---
title: "Evolution downloads but does not display new messages for ONE account"
date: 2008-10-26
forum: General Help
---

### Post by gadgetgirl02 on 2008-10-26
I've been using Evolution for a couple of years now, but this one is new to me. It downloads the email messages from all of the accounts I have it set up for (there are three in total), but for my main Gmail account, it downloads the messages but won't display them. I've tried to fix this through the front-end software, but nothing works. If I tell Evolution to display unread messages only, it shows a blank inbox. If I search for a message that I know the text of because I read it in the web client, it again will show blank results. The other email accounts are all fine, though.

The kicker is that sometimes things sort of work. Sometimes I will get the new email notification, but not be able to see the messages. Other times everything will work perfectly, but it seems very fragile -- if I so much as change folders within Evolution, the messages are not visible again.

The weirdest part is, Evolution will always display messages from this one newsletter I get about once every two weeks or so. Messages from that one address will continue to display, even when all the messages in between one newsletter and the previous one will not.

It seems to me that I have some table corruption, but I'm not sure. Anyone know what needs to be fixed?

I'm running Hardy Heron on a Dell Inspiron 1521.

---

### Post by gadgetgirl02 on 2008-11-02
Yesterday I got a full, complete, correct load of my inbox again, for the second time in six days. For the problem I described in the previous post, that was very quick -- often I can go two weeks without that happening. So, just for fun, I tried doing a search... and found that there was already a search there (for the newsletter I mentioned always show up).

Now, before you get to laughing so hard you can't read the rest of this: believe me, I *checked* the filter box to ensure it was empty, LOTS of times. Also, if the problem was I was being an idiot and not turning off the filter, why did all of my e-mail show up on some loads?

For now, I'm going to file this in my ever-growing Ubuntu pile of "It fixed itself" issues, but I'd still like to know how the behaviour reconciles with the features.

---

### Post by alfh on 2009-09-14
I have the same problem. Ubuntu 8.0.4, Evolution 2.22.3.1

After a search, the inbox on my main account refuses to show some of the unread messages. I sent myself a test message, this shows up.

The message count of the inbox shows 575 messages, which correspond to the number of read messages. However right-clicking the folder and selecting properties says 601 messages. So obviously Evolution knows these messages exists, but for some reason thinks I'm not entitled to see them.

So, for now, back to the webmail.

---

### Post by alfh on 2009-09-14
Eventually I found all the missing messages in the local trash folder. Unread messages from my secondary account also was moved to the trash folder of that account. Even if I accidentally should have touched 'delete' on the keyboard or clicked the delete button, I have no idea how this would move all of my unread messages, in two different accounts, to the trash?

I will proceed with the utmost caution!

---

