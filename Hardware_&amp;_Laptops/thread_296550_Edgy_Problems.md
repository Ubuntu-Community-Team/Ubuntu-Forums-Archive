---
title: "Edgy Problems"
date: 2006-11-09
forum: Hardware &amp; Laptops
---

### Post by Permafrost91 on 2006-11-09
All my issues have been resolved! Thanks for all the help!

[COLOR="Silver"]I just installed a fresh copy of Edgy after giving FC6 a try and I am having the following issues with Edgy that I didn't have with Dapper:
(1) why do I need to specify an ESSID to set up my wireless card? I roam a lot and don't always want to change the ESSID manually (RESOLVED)

(2) on that same note, why does network-manager not see my wireless card when I am currently connected to the Internet through it? The "Enable Networking" checkmark exists and is checked but I remember in Dapper there also was a second checkmark for "Enable Wireless Networking" if a wireless card was found. This option is non-existent (RESOLVED)

(3) resuming from suspend does not work (hibernation does). I have an IBM X30 ThinkPad and did not have this problem with Dapper. I am not running Compiz or Beryl. (RESOLVED)

That's about all so far. If anyone has any helpful pointers for me, I'd appreciate it. Thanks! [/COLOR]

---

### Post by Permafrost91 on 2006-11-11
is no one else having similar issues?

---

### Post by rrwo on 2006-11-11
> **Permafrost91 said:**
> I just installed a fresh copy of Edgy after giving FC6 a try and I am having the following issues with Edgy that I didn't have with Dapper...

You should put each issue in a separate post, and the subject should be specific about each issue.

> **Permafrost91 said:**
> (1) why do I need to specify an ESSID to set up my wireless card? I roam a lot and don't always want to change the ESSID manually ](*,)

(2) on that same note, why does network-manager not see my wireless card when I am currently connected to the Internet through it? The "Enable Networking" checkmark exists and is checked but I remember in Dapper there also was a second checkmark for "Enable Wireless Networking" if a wireless card was found. This option is non-existent ](*,) 


We'd need to see your network and wpa_supplicant configuration.


> **Permafrost91 said:**
> (3) resuming from suspend does not work (hibernation does). I have an IBM X30 ThinkPad and did not have this problem with Dapper. I am not running Compiz or Beryl. ](*,) 


You'll find several threads about handling hibernation problems.

---

### Post by Permafrost91 on 2006-11-12
ok, I got network-manager to work! after doing some more research, I realized that I had to disable all network devices in System->Administration->Networking and now network-manager handles everything automatically. sweet! :)

only leaves the issue with resume from suspend now ...

---

### Post by Permafrost91 on 2006-11-12
got suspend/resume to work with this thread:
[http://www.ubuntuforums.org/showthread.php?t=274511](http://www.ubuntuforums.org/showthread.php?t=274511)

---

