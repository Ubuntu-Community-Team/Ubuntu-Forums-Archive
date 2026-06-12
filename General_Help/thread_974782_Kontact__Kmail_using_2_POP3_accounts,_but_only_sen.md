---
title: "Kontact / Kmail using 2 POP3 accounts, but only sends through the Default..."
date: 2008-11-07
forum: General Help
---

### Post by stir-crazy on 2008-11-07
I had just a gmail account for some time, and Kontact worked fine.  Today I added my school account, which for the most part works.

However, if I try to send mail from my school account, the "from" field is actually my gmail (though the reply-to is correctly listed as my school account.)

I have looked through my "Identities", "SMTP" and "POP" settings for each account, don't see any instances where there's any cross reference that explains this.

Anybody know how to correct this or have any ideas on what I might be overlooking?  Thanks!

EDIT:  Regardless of whether I select my school identity, or manually input the (school) email address, the receiver always sees my gmail (default) address.

---

### Post by stir-crazy on 2008-11-08
Likely figure this out, posting should anybody else have a similar issue.  Per the Kontact help pages:

"The way of sending messages configured here will be used for your default identity a**nd for all other identities that have no own way of sending messages**. You can use different ways of sending messages for different identities by selecting the Special transport checkbox in the Advanced tab of the Identities section."

Checking in closer detail with the Fresno State campus, they say I need to check with my ISP to get smtp server to work...that sounds odd.  Somehow I don't think Comcast will have much to say there, but that at least explains what's going on, and that it isn't really a Kontact issue at all.

Thanks for listening, I feel much better now.

---

