---
title: "Setting up Email: postfix AND courier! why?"
date: 2008-09-02
forum: General Help
---

### Post by bb002 on 2008-09-02
Every email server setup guide I look at tells you how to setup both postfix and courier. Why not just one or the other?

Let's just take this guide for instance: 
[https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto)

In the **big picture** section it has
> 
]Postfix Mail Transfer Agent receives emails via the SMTP protocol and delivers them to different places on your hard disk.

]Courier is a standalone mail server just like Postfix but we just use its POP3/IMAP server component to let users access the mailboxes.

Is there some particular reason I must use parts from both mtas if they are the "same"? Is there some technical reason that forces this setup that I don't know of? I just want one or the other. I'm in need of all the listed features offered by that guide even if it is incomplete. Do some of them only work with one or the other? If so which goes where?

Sorry for asking so many questions just that setting up a mail server seems far more complicated than I think it should be. Making me want to ask more questions that I probably could answer with an easy web search. :/

---

