---
title: "[SOLVED] Thunderbird &amp;quot;marked as read&amp;quot; config"
date: 2008-09-11
forum: General Help
---

### Post by L8erG8er on 2008-09-11
Does anyone know what setting in about:config in Thunderbird will prevent the messages from being automatically marked as read?

In other words, I would like to be able to highlight a message but NOT mark it as read until later.

Thanks!

---

### Post by quibbler on 2008-09-11
I believe the only thing you can do that is increase the delay time:

Edit-Preferences-Advanced..then increase the Wait to 999

Regards quibbler

---

### Post by sv1cdn on 2008-09-11
Go to Edit->Preferences->Advanced->General and uncheck Wait...

---

### Post by L8erG8er on 2008-09-12
Thanks to both of you for the help.  I already had my Wait box unchecked, but that just made the messages get marked immediately.

For now, I have edited the about:config like this:

mailnews.mark_message_read.delay user set boolean true
mailnews.mark_message_read.delay.interval user set integer 999999999

Putting nine 9s in the value is all she can take without falling over to a hex value.

So, this gives me what, about 17 million minutes until the messages will be marked as read, I guess? :)  I think that will suffice for now, until I figure out how to change it for real.

Thanks again.

---

