---
title: "Evolution filter based on adressbook"
date: 2005-11-16
forum: General Help
---

### Post by Matyy on 2005-11-16
Hi,
i'm quite happy with Evolution. But not with spamassasin. I would love to have a filter, that moves all mails that have a known sender (adress is in the adressbook) in an other folder. (like in Thunderbird)

Does someone know a way how to accomplish this?

thx, matyy

---

### Post by mirons on 2005-11-16
If I've understood the problem it's very easy:
Message menu ---> Create rule ---> Filter on sender
(or something like that, my menus are in Italian).

---

### Post by gapplewagen on 2005-11-16
If you right-click on a message from who you want to filter for, you should see an option that says "Create Rule From Message".  From there you can create a rule to filter on Sender, Recipient, or Subject.  In the bottom of the box that comes up you can apply many rules for the message.  The default should be to move it to a specified folder.

More advanced filter options are available in "Edit --> Message Filters".

---

### Post by Matyy on 2005-11-16
yeah, I got that :) But so I have to create a filter for every single friend. What I'd like is a single filter that checks if the mail's sender is in my adressbook. (It'd be even better if it could differ between the different adressbooks, but that's not necessary)

---

### Post by Matyy on 2005-11-16
Hmm, perhaps it'd be possible to send the mail to a script that checks if the sender's adress is in the adressbooks and if yes sends "1" back to evolution. But I have no idea how this script be written. If someone knows a way, please post it!

---

### Post by Stormspace on 2005-11-16
How about a filter on which account the mail comes from. I have serveral accounts and need for the mail to be moved into a folder based on the account the mail came from. Currently I'm stuck with message filters, but I'm looking for a way to do it.

---

