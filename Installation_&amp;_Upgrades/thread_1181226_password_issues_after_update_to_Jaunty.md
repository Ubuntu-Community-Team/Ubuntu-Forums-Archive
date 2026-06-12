---
title: "password issues after update to Jaunty"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by remco_t on 2009-06-07
Recently upgraded my Intrepid installation to Jaunty, which appeared to pass without a hitch...

Rebooted the system after the upgrade, wanted to start Synaptic and was prompted for the root password, as usual. But this time my password wasn't accepted while I'm 100% confident the password is correct. Sudo commands in Terminal aren't accepted either when I get prompted for my password. I followed the guide to reset my password [here]("https://help.ubuntu.com/community/LostPassword") and ended up trying "the Other way":

```
root@(none):/# password remco
send-mail: fatal: could not find any active network interfaces
Can't send mail: sendmail process failed with error code 75
root@(none):/# _
```

So, it doesn't really prompt me to give a new password as you would expect, but instead it starts yappin' about send-mail. Any ideas on how to get root access back to my machine? :?:

---

