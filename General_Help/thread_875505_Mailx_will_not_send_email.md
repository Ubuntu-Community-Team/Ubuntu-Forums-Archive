---
title: "Mailx will not send email"
date: 2008-07-30
forum: General Help
---

### Post by Yuki_Nagato on 2008-07-30
When I enter this command, it will appear to work (the command will disappear and the terminal will snap to a new line with the prompt at the ready), but when I check the Inbox, no e-mail is sitting in there.

```
echo "test" | mailx -s "XYY" ME@gmail.com
```

---

### Post by rmccarri on 2008-10-16
Same here.  Does anyone have any ideas of what to check?

---

### Post by delorayn1 on 2009-02-15
Here same problem to...

---

### Post by heindsight on 2009-02-15
By default your MTA (exim, postfix or sendmail) is configured for local mail delivery only. which means that mailx can only send mail to users on your own computer. 

It is possible to configure your MTA to send mail to other addresses. It's quite tricky to get right though and you can easily end up compromising your security.

Unless you really have a good reason for needing to change it, and know what you're doing, I'd recommend keeping the default configuration of your MTA.

---

