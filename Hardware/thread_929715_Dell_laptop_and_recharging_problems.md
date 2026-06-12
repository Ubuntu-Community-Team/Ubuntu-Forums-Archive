---
title: "Dell laptop and recharging problems"
date: 2008-09-25
forum: Hardware
---

### Post by stefistef on 2008-09-25
Hi all,

I've been reading about a lot of people having problem with dell laptop because they do not recharge. Ubuntu's forum answer where all pointing to "Dell's problem" rather than some incompatibility with Ubuntu, but I think this is not the case.
I have a Dell Inspiron 630m, and it's always worked fine. Then one day I updated the kernel and it stopped recharging. I want to point out the fact that when I boot on Windows I CAN recharge the battery without any problem and it's working life is almost as good as it was when I bought the laptop so it can be any battery and/or laptop related problem but rather some problem with the OS. By the way, when I boot on Linux I receive a message saying that the recharge can't be recognized, despite the fact that I've never changed it and it's always been the same that worked up to a couple of months ago (and still works with Windows!).
Can anyone say soemthing about that? I'd really like to remove completely Windows but I won't do that until I can make everything fine with Ubuntu!

---

### Post by timcredible on 2008-09-25
well, you could just use the old kernel if the new kernel has an issue.  just choose the old kernel at boot from the grub menu.

---

### Post by El Rogueo on 2008-09-27
> **stefistef said:**
> when I boot on Linux I receive a message saying that the recharge can't be recognized, despite the fact that I've never changed it and it's always been the same that worked up to a couple of months ago (and still works with Windows!).
Can anyone say soemthing about that? I'd really like to remove completely Windows but I won't do that until I can make everything fine with Ubuntu!

While you've clearly established that the problem is not integrally a hardware failure (seeing as Windows still recharges fine, which you assert numerous times) I'm not entirely convinced with your assessment of ubuntuforums unanimously deciding that recharge problems are "dell's fault", and it sounds like a little more research or trial and error could help your troubles considerably. Without knowing any details (nothing specific is really provided :(), it would help if you:

post the exact error you get when booting the computer

check the system logs, specifically for those generated when shutting down or closing the lid of the computer

provide more details about your machine

Et cetera. Secondly, I'm not entirely sure what you're asking when you say, "Can anyone say soemthing [sic] about that?" What would you like to be said about what? In defense of the operating system, it is neither perfect nor fully supported, due to the fact that it is free, both as in beer and in freedom. On the opposite side, unless you have truly pressing hard drive space concerns, dualbooting linux and windows is the best combination of functionality and compatibility.

tl;dr it sounds like an acpi problem, maybe looking there would help

---

### Post by DarkSoul1984 on 2008-11-21
Hi.

Forgive me for sounding new, but I just installed Ubuntu on my laptop and got rid of Windows entirely.

When I boot up the machine, a warning comes up saying the Setup doesn't recognize the battery and won't be able to recharge it (much the same as stefistef).

I'm searching through for whatever programs I can find that allow me to monitor battery/power usage, but I am a new user to Ubuntu and haven't used Linux in general in many years.

Is there a resolution at this point in time?

Thanks

---

