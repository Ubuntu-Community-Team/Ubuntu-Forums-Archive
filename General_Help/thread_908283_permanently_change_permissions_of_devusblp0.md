---
title: "permanently change permissions of /dev/usb/lp0"
date: 2008-09-02
forum: General Help
---

### Post by Arrowx7 on 2008-09-02
Hello,
I was ripping my hair out for the whole day trying to get my printer to work.
Then I found that /dev/usb/lp0 only had root privilages.  I changed it by running sudo chmod 666 /dev/usb/lp0
Now each time I reboot, it goes back to the old permissions.

Is there a way to permanently change permissions of that device.

Actually, more importantly, what's the proper way to make sure my user has printing rights?  (I heard you have to add yourself to the group called lp, but that group doesn't exist).

If someone can clear up my confusion, I would greatly appreciate it.

Thanks!

---

### Post by Vivaldi Gloria on 2008-09-02
> **Arrowx7 said:**
> Then I found that /dev/usb/lp0 only had root privilages.  I changed it by running sudo chmod 666 /dev/usb/lp0
Now each time I reboot, it goes back to the old permissions.

Is there a way to permanently change permissions of that device.

You can put a line in /etc/rc.local:

```
chmod 666 /dev/usb/lp0
exit 0
```

> Actually, more importantly, what's the proper way to make sure my user has printing rights?  (I heard you have to add yourself to the group called lp, but that group doesn't exist).

Not sure about this. I have a group called lpadmin.

---

