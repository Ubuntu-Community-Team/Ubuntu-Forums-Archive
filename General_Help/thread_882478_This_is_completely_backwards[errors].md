---
title: "This is completely backwards[errors]"
date: 2008-08-07
forum: General Help
---

### Post by 5h4dy on 2008-08-07
Ok, so I know Linux is supposed to be the freedom pc users are looking for. Except here's the thing: Why does it keep locking up, and I ALWAYS have to manually reboot?

Why do certain things not work, that are supposed to work?

I had read something about logs that linux creates, is there a way to post you guys something to help me out here?

I switched from windows cause windows has problems already, I didn't switch to aquire more problems.

---

### Post by dreadmeat on 2008-08-07
i had a similar problem, disabling hyper threading solved it [for me]

---

### Post by 5h4dy on 2008-08-07
> **dreadmeat said:**
> i had a similar problem, disabling hyper threading solved it [for me]


from your bios, or is there an option in ubuntu?

---

### Post by dreadmeat on 2008-08-07
from my [award] bios.
there may be an option somewhere in the depths of the untu though ;)

---

### Post by 5h4dy on 2008-08-07
> **dreadmeat said:**
> from my [award] bios.
there may be an option somewhere in the depths of the untu though ;)

Thanks, I turned HT off from my bios, let's hope this fixed it for me too. Thanks for the quick response, even if it doesn't work, also.

---

### Post by cdtech on 2008-08-07
> **5h4dy said:**
> Ok, so I know Linux is supposed to be the freedom pc users are looking for. Except here's the thing: Why does it keep locking up, and I ALWAYS have to manually reboot?

Why do certain things not work, that are supposed to work?

I had read something about logs that linux creates, is there a way to post you guys something to help me out here?

I switched from windows cause windows has problems already, I didn't switch to aquire more problems.

Is there a certain program you are running when it locks up? Could you be a bit more specific about not working, maybe which programs.

"/var/log/dmesg" is the kernel boot message, and there are other logs such as /var/log/messages that helps track problems.

You can view the log files through "System > Administration > System Log"

---

### Post by dreadmeat on 2008-08-07
that's cool =)

---

