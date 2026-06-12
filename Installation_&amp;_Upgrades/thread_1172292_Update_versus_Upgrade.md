---
title: "Update versus Upgrade?"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by benali72 on 2009-05-28
I'm running 8.04 ("cat /etc/issue" returns "8.04.2").

When I go into the Update Manager and run a Check, I get this message:

"Not all updates can be installed."

and am given the choice of two buttons labelled:

"Partial Upgrade"   and   "Close"

I want to ensure all updates are applied to my 8.04 instance, but I have no interest in upgrading it to 9.x (I'm on a very old box and don't want a newer but larger or slower system).

My question is:  if I select "Partial Upgrade" does that mean it will upgrade me to a newer Ubuntu version like 9.x?  When I tried it it responded like it was going to Upgrade my version instead of just applying updates to my current version (so I cancelled out). 

Or is the question simply telling me I need to pick that option to get all possible updates to my current release 8.04?

Thank you for your help.

---

### Post by bostonaholic on 2009-05-28
> **benali72 said:**
> I'm running 8.04 ("cat /etc/issue" returns "8.04.2").

When I go into the Update Manager and run a Check, I get this message:

"Not all updates can be installed."

and am given the choice of two buttons labelled:

"Partial Upgrade"   and   "Close"

I want to ensure all updates are applied to my 8.04 instance, but I have no interest in upgrading it to 9.x (I'm on a very old box and don't want a newer but larger or slower system).

My question is:  if I select "Partial Upgrade" does that mean it will upgrade me to a newer Ubuntu version like 9.x?  When I tried it it responded like it was going to Upgrade my version instead of just applying updates to my current version (so I cancelled out). 

Or is the question simply telling me I need to pick that option to get all possible updates to my current release 8.04?

Thank you for your help.

I'm pretty sure it won't upgrade you to a newer version.  I've clicked that several times and my home machine is still on 8.04.2.  After you run the "Partial Upgrade", run an update and upgrade again and there should be some new things.

I think what they mean by "Partial Upgrade" is that there are packages that need upgraded but cannot do so until other packages are upgraded first.

That's my take on it.  Like I said, I've clicked "Partial Upgrade" and it's still running Hardy.

---

### Post by raymondh on 2009-05-28
Hello Benali72,

Dist-upgrade is what'll make your system jump to a higher/newer Ubuntu version.

Regards,

---

### Post by benali72 on 2009-05-28
Thank you both. 

I went ahead and did the "Partial Upgrade," and it updated all possible 8.04 packages and kept me on 8.04 (just as you said).

Looks like I unnecessarily got confused between the words "update" and "upgrade" in the Ubuntu messages.

Thank you.

---

### Post by raymondh on 2009-05-28
You're welcome.  Have fun Ubuntu-ing

Regards,

---

