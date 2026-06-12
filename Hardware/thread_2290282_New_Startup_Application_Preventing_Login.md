---
title: "New Startup Application Preventing Login"
date: 2015-08-11
forum: Hardware
---

### Post by Christopher_DiPers on 2015-08-11
First of all, I apologize for not finding the right sub-forum. It is EXTREMELY late where I am and am at my wits end with this issue.

I was attempting to setup Bumblebee for my laptop to switch between the NVidia card and intel graphics, and it looked like I had installed everything correctly. The last step in the tutorial I was following said to set it as a startup application and reboot. I did that and arrived back at the login screen. Wrote in my password, and the screen went black. Login screen came back up again. Wrote in the password another time; same thing happened. I cannot log into Ubuntu on my computer.

Is there a way to remove startup applications from recovery mode? The laptop dual boots Windows 10; is there a way to remove the startup app from within Windows 10? Would you suggest just reinstalling Ubuntu to get rid of the error entirely? Doing that, would I just reinstall in the same partition it's currently installed in without having to create a new swap partition, etc.?

Thank you!

---

### Post by howefield on 2015-08-11
Thread moved to the "*Hardware*" forum.

You could have a look to see if there is anything relevant in 

```
~/.config/autostart/
```

Might help to know which version of Ubuntu you are using.

---

### Post by Christopher_DiPers on 2015-08-11
I'm using 14.04.

---

