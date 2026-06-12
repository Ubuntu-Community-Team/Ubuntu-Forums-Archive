---
title: "My password isn't working - why?"
date: 2008-07-18
forum: General Help
---

### Post by Bruno12 on 2008-07-18
I just switched on my computer, and for some reason my password is not being accepted, i've used it 1,000 times before, there's no way its wrong, why has ubuntu suddenly stopped recognising my password? 

A. how can i get past the password?
B. how can i find out what caused it? IF I CAN GET BACK ON. I've got the installation disk here, will that help? Could i have deleted something last time i was on? Where can i look to find out? 

Or is this common...

---

### Post by unutbu on 2008-07-18
Maybe first check that the Capslock and Numlock keys are not on?

---

### Post by Bruno12 on 2008-07-18
Yes, i did, they're not that's why i'm confused. I'd expect this of windows
I'm worried that there could be some kind of virus on my computer?

---

### Post by bapoumba on 2008-07-18
Could you please describe what happens after entering your password? Do you get a blank screen or does GDM say it is incorrect ?

---

### Post by WRDN on 2008-07-18
As a solution, boot into Recovery Mode (it should be an option at the GRUB menu), drop down to root shell (2nd option) and type:

```
passwd [username]
```

This will allow you to change the password, and hopefully, login normally again.

---

### Post by Bruno12 on 2008-07-18
can a virus reset my password to something else? or just disable my password?

---

### Post by Pro-reason on 2008-07-18
> **Bruno12 said:**
> can a virus reset my password to something else? or just disable my password?

We can't answer that, because none of us has ever seen a Linux virus.

You probably made some accidental change, or there is a bug with a recent update.

---

### Post by The Marsh Man on 2010-12-22
I had the same problem, was running 10.04, so did a clean install of 10.10. Let me login once, and was fine with it in synaptic, then again on driver installer. Restarted, and now my password is apparently incorrect, and I have no way whatsoever of getting anywhere, no obvious way to login as a guest, in recovery mode, or anything else. Just a login screen telling me that the password I chose 5 minutes ago is incorrect.

---

