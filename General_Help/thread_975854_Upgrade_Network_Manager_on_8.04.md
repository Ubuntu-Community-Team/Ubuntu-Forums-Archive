---
title: "Upgrade Network Manager on 8.04"
date: 2008-11-08
forum: General Help
---

### Post by alzaf on 2008-11-08
Hi

I have been using XUbuntu 8.04 with no sound problems but when I have upgraded to Xubuntu 8.10, I have lost sound. I have goggled to find a solution and seen that this is a major problem but I have had no success with workarounds.

The only reason why I upgraded to 8.10 was to get NetWork Manager which recognised my T-Mobile 3G mobile-broadband stick. I had got it to work on 8.04 but for some reason it intermittently did not recognise the stick but with 8.10 it works perfectly.

How hard would it be for me to reinstall 8.04 and try to upgrade the latest version of Network Manger?

---

### Post by soro2005 on 2008-11-08
[Here](http://ubuntuforums.org/showthread.php?t=797059&highlight=howto+network+manager+hardy).

---

### Post by cariboo on 2008-11-08
It would be a lot easier to fix your sound problem. Could you paste the output of:

```
sudo lshw -C multimedia
```

in your next post. Because nothing guarantees that sound will work when you install hardy.

Jim

---

### Post by alzaf on 2008-11-09
Thanks. I've reinstalled 8.04 with new network manager update. I have automatic network support and I have sound back.

---

