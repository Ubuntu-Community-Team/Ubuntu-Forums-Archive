---
title: "Thunderbird Auto-forwarding?"
date: 2008-10-06
forum: General Help
---

### Post by 71CH on 2008-10-06
Hi all
I did a few searches for this but couldn't find a satisfactory answer.  I just installed Thunderbird and really love it.  I think it's much better than Evolution.  Anyway, I was wondering if there was a way to auto-forward my emails to my gmail account.  If there's a way to do this without even having to open up Thunderbird that would be even better (though I don't really think this is possible).  Thanks.

---

### Post by pdwerryhouse on 2008-10-06
Where is Thunderbird fetching your mail from? If it's an ISP, they may already have a service to forward your email to another address.

If not, then you could just use fetchmail on your Linux box to retrieve the mail, and then create a .forward file in your home directory, with your gmail address in it.

You will need to have a mail transport agent (eg, postfix) configured for this to work.

---

### Post by 71CH on 2008-10-06
Can you please explain this fetchmail and mail transport agent thing in more detail please.  Thanks.

---

### Post by 71CH on 2008-10-07
bump

---

### Post by 71CH on 2008-10-07
I tried using message filters but its really buggy.  Please help.

---

### Post by 71CH on 2008-10-07
I saw somewhere that this can be done in Thunderbird with a rule.  Anyone know what that is?

---

### Post by lisati on 2008-10-07
> **71CH said:**
> Hi all
I did a few searches for this but couldn't find a satisfactory answer.  I just installed Thunderbird and really love it.  I think it's much better than Evolution.  Anyway, I was wondering if there was a way to auto-forward my emails to my gmail account.  If there's a way to do this without even having to open up Thunderbird that would be even better (though I don't really think this is possible).  Thanks.

It's in the "message filters" department. You can either choose a particular messgae and choose the Message->Create Fileter from message item, and edit the specified filter, or choose the Tools->message Filters option, create a new filter, choose the filter to edit, and set it from there. The required "action" is listed on my copy of thunderbird as "Forward Message To"

---

### Post by 71CH on 2008-10-07
> **lisati said:**
> It's in the "message filters" department. You can either choose a particular messgae and choose the Message->Create Fileter from message item, and edit the specified filter, or choose the Tools->message Filters option, create a new filter, choose the filter to edit, and set it from there. The required "action" is listed on my copy of thunderbird as "Forward Message To"

Thanks for your reply.  I actually tried to do this and it wouldn't work.  I think it has something to do with using the webmail and hotmail plugin for Thunderbird.  Is there a different way to do this?

---

### Post by lisati on 2008-10-07
[QUOTE=71CH;5924510]Thanks for your reply.  I actually tried to do this and it wouldn't work.  I think it has something to do with using the webmail and hotmail plugin for Thunderbird.  Is there a different way to do

I haven't used hotmail with an email client since they started expecting me to pay to be able to do that, so I'm not sure.....

Anyone else?

---

### Post by 71CH on 2008-10-07
> **lisati said:**
> [QUOTE=71CH;5924510]Thanks for your reply.  I actually tried to do this and it wouldn't work.  I think it has something to do with using the webmail and hotmail plugin for Thunderbird.  Is there a different way to do

I haven't used hotmail with an email client since they started expecting me to pay to be able to do that, so I'm not sure.....

Anyone else?

Actually if you use Thunderbird's hotmail plugin you don't have to pay...

---

### Post by 71CH on 2008-10-07
bump

---

### Post by pdwerryhouse on 2008-10-08
postfix is a mail transport agent - ie, a mail server. There's a ton of documentation available for it, and I strongly recommend that you read through it before proceeding with it.

fetchmail is a command line implementation of the POP and IMAP client protocols; it will fetch your email from your ISP and then deliver it to your local system.

Setting up both of these will probably require a bit of reading to get right. That said, it's a much better solution than running Thunderbird purely to pop and forward your mail to a different address.

---

