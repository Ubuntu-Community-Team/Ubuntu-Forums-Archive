---
title: "Problem with email file"
date: 2008-10-14
forum: General Help
---

### Post by RandomActs on 2008-10-14
All, in /var/spool/mail  I have several large user email files. If I look at the contents I can in fact see there are valid emails contained within. However, when I login as that user and use mail or mutt it tells me I have no mail. 

Any idea what is happening? and how I can get at them?

---

### Post by RandomActs on 2008-10-14
I fixed my own problem. I need to specify a -f option with mutt or mail. 

Thanks.

---

### Post by andrew.46 on 2008-10-30
Hi Random:

> **RandomActs said:**
> I fixed my own problem. I need to specify a -f option with mutt or mail. 

The -f option allows you to specify mailboxes other than your default one. Does this mean you have several different mailboxes, or have you not specified a default?

  Andrew

---

