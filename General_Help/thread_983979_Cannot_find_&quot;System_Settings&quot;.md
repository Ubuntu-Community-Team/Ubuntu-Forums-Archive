---
title: "Cannot find &quot;System Settings&quot;"
date: 2008-11-16
forum: General Help
---

### Post by CX15 on 2008-11-16
In an attempt to fix a slow internet browsing speed in 8.10 I am trying to follow the following advice.

> I tried all the configurations people posted on this thread and nothing helped until by accident I unchecked "system settings" check box in > network connections - wired/wireless >edit > "system settings"

However, I cannot find this setting anywhere in Ubuntu 8.10

I'm new to Ubuntu, so can someone please help.

Thanx in advance.

CX

---

### Post by CatKiller on 2008-11-16
That's in System -> Preferences -> Network Configuration. Choose the Wired or Wireless tab depending on which type of connection you're using. Select the adaptor and click on Edit.

---

### Post by CX15 on 2008-11-16
Thanx Ck - found it. Did not however solve my problem :(

Can you perhaps help me find the following two places as well:

1.
> ...by removing the DNS configuration from DNS tab at System->Administration->Network...

I dont have "Network" under Administration at all.

2.
> ...selected to "aut4odetect proxy settings" under the connection options and had forgot to set it back to "direct connection"."

Where can I find these options?


thanx again

---

### Post by CatKiller on 2008-11-16
The network tools have changed in 8.10 with the new NetworkManager framework. What was at System -> Administration -> Network in 8.04 is that same tool at System -> Preferences -> Network Configuration as far as I know. I don't know exactly how to set a proxy with the new tools.

I haven't had any slow browsing problems either, so I can't give any advice on how to fix your underlying issue, other than to suggest that you post some detailed descriptions of your symptoms in the Networking & Wireless forum to see if anyone there can help you with your problem.

---

