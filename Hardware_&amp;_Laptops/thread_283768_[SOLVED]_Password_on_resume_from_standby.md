---
title: "[SOLVED] Password on resume from standby"
date: 2006-10-24
forum: Hardware &amp; Laptops
---

### Post by finster on 2006-10-24
Hi all,

Edgy is working great on my Dell Inspiron 6000 - I just have a small problem. When I open my laptop lid it prompts for a password - is there any way to disable this? 

I only have one user set up on it which is shared, but I don't want everybody to have access to the main password. I've already set up automatic logon which is great - I just need to sort this out.

Thanks....

---

### Post by 5-HT on 2006-10-25
Take a look at /etc/default/acpi-support. There should be a line in there to toggle screen locking on resume.

HTH

---

### Post by finster on 2006-10-25
Thanks, I commented out the line "LOCK_SCREEN=true" in /etc/default/acpi-support as suggested but the password screen still appears on resume.

I've tried restarting acpid and rebooting the laptop but still no change.

Any other ideas?

Thanks.

---

### Post by 5-HT on 2006-10-25
> **finster said:**
> 
Any other ideas?

What about  explicitly setting LOCK_SCREEN=false?
Another thing that may be worth a shot might be to disable screen locking in the screensaver preferences. If that does the trick, you could always lock the screen manually when needed.

HTH

---

### Post by finster on 2006-10-25
Thanks,

Tried setting it to false instead with no joy.

I'd already gone down the screensaver route and tried disabling the screen lock there.

Sure there is a simple setting somewhere. It's just finding it!

Any other ideas?

---

### Post by finster on 2006-10-25
Found it!

For others with the same problem, here is what to do: -

Open gconf-editor
Go to apps / gnome-power-manager
Switch off "lock_on_suspend" (and some of the other lock parameters too if needed)

Tried it and it works great.

Thanks 5-HT for your help anyway....

---

### Post by 5-HT on 2006-10-26
> **finster said:**
> Found it...gconf-editor
Damn, gconf slipped my mind.
Glad you found it!:p

---

### Post by strawman on 2007-11-04
thanks finster!  this has eluded me for a long time.  :)

---

### Post by alhead on 2008-07-22
Awesome, gconf-editor worked for me.  Should this be marked "solved" now?

---

### Post by finster on 2008-07-23
Glad it worked.

> **alhead said:**
> Awesome, gconf-editor worked for me.  Should this be marked "solved" now?
Done!

---

