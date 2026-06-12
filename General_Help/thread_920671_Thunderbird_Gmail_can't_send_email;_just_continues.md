---
title: "Thunderbird: Gmail can't send email; just continues to ask for password"
date: 2008-09-15
forum: General Help
---

### Post by xalent on 2008-09-15
I've looked around and haven't seen this exact problem. I found another thread where Thunderbird wasn't working with POP3/IMAP, but for me, I can receive messages and I'm using IMAP. I just can't send any emails. Thunderbird just keeps on asking for a password. I have the outgoing server set up as:

server: smtp.gmail.com
port: 587
security: TLS

These same settings work when I'm using Evolution Mail (meaning I can send email) and these are the exact settings to have Thunderbird running.

---

### Post by nikgare on 2008-09-15
Are you sure that the **outgoing** username is correct?

---

### Post by xalent on 2008-09-15
Yeah, that was the problem. Thanks. I can't believe I missed that.

---

### Post by 71CH on 2008-10-09
> **xalent said:**
> Yeah, that was the problem. Thanks. I can't believe I missed that.

I have the same problem as well.  What do you mean by outgoing username?  Mine is set up as my email address.  Should I remove the @gmail.com?

---

### Post by scouser73 on 2008-10-09
No, you shouldn't remove the @gmail.com.

---

### Post by dangermouse28 on 2008-10-24
Could someone be more specific - how does the outgoing username differ from the incoming?

I'm using Gmail with POP - can read emails fine but can't send any!!!

Many thanks

---

### Post by _sAm_ on 2008-10-24
@dangermouse28:

Guide here; 
[http://mail.google.com/support/bin/answer.py?answer=38343](http://mail.google.com/support/bin/answer.py?answer=38343)

Whyd dont you use imap and not pop, imap is faster.
Guide for imap +gmail here; [http://mail.google.com/support/bin/answer.py?hl=en&answer=75725](http://mail.google.com/support/bin/answer.py?hl=en&answer=75725)

---

### Post by dangermouse28 on 2008-10-28
Ok - sorted it.

Problem was I was using ***@gmail.com in the username box instead of ***@googlemail.com. :oops:

---

