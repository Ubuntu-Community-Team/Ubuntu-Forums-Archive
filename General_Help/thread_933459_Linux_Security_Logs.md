---
title: "Linux Security Logs"
date: 2008-09-29
forum: General Help
---

### Post by anotherdisciple on 2008-09-29
I bet this thread is going to be moved to security discussions, but I put it in "general" in hopes that I will receive more answers.

I just found out that my debit card information was stolen. Someone bought all kinds of stuff with it! I canceled the card, all is taken care of, but I want to start thinking like a criminal so that I can prevent it from happening again.

Here's my long list of questions:

- It's unlikely that my linux box was hacked, but how can I check the logs and what do I look for exactly?

- I have said before that I use WEP-128 bit, but I'm going to change that to WPA today. What are the chances that my info could be stolen wirelessly? What should I look for in my wireless logs (I'll have to figure out how to check those too)?

- I'm very careful about who I give my debit information to, I only used trusted websites, what are the chances that it was intercepted by a fake website or something of that nature?

- And lastly, what are the other possibilities? I want to start digging into security and plugging holes.

Thanks-

Nick

---

### Post by Nepherte on 2008-09-29
- An interesting log file to examine is /var/log/auth.log You can also look for suspicious user names.

- A WEP connection can easily be cracked, thought that doesn't mean it's done that way.

- Just be careful to use the correct url. Just pay attention to the spelling. You could bookmark it or search the bank in google.

---

### Post by ibuclaw on 2008-09-29
It is unlikely that you'll find it in the logs after it as happened, unfortunately...

What you can do is to build up a safeguard to prevent it from happening again.

Things like tripwire, wireshark, etc.
There are quite a few good HowTos in the tutorial section.

I'd recommend Bodhi's: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)


Regards
Iain

---

