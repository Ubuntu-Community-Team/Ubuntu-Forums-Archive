---
title: "Mutt Configuration- History Question - Save To Mailbox/Open Mailbox"
date: 2008-11-25
forum: General Help
---

### Post by davewmerrill on 2008-11-25
Hi All,

I had an instance of Mutt on an old machine where I could:

[LIST]
[*]Type "s" to save a message to a Mailbox (say foobox).
[*]Then type "o" and be able to use the arrow keys to up-arrow to foobox and change to that folder
[/LIST]
I had no particular configuration settings in my .muttrc so I assume this was the default behavior for Mutt. I.E. the "history" for "saving to" and "opening" mailboxes was stored in the same place.

On a new instance of Mutt the default is just the opposite, the histories for opening mailboxes and saving to mailboxes seems to be different, I can't do what I used to be able to do.

I have not yet found anyone else discussing this issue, nor can I find what seems to be the right settings in .muttrc.

Anyone else have this problem? Or a lead on making Mutt do my bidding?

Thanks in advance!
Dave

---

### Post by andrew.46 on 2008-12-01
Hi,

I also only use the defaults and the letter 's' should still save your message. To open a mailbox the default is 'c'. This is with:

```
andrew@skamandros:~$ mutt -v | head -n1
Mutt 1.5.18 (2008-05-17)
```

from the intrepid ibex repositories.

  Andrew

---

### Post by sdennie on 2008-12-01
Try adding the following to ~/.muttrc:

```

bind index s save-message
bind pager s save-message
bind index o change-folder

```

---

