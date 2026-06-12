---
title: "Ununtu, Firefox and Flash"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by da85 on 2009-05-12
Hi all,

I'm running Ububtu 6.06 and I'm having real difficulty trying to install flash for firefox to watch videos such as youtube.

I've tried both synaptic and the standard prompts if you go to a site such as youtube to no avail.

I am running firefox version 1.5.0.3

Can anyone help me???

---

### Post by _Purple_ on 2009-05-12
Drapper will reach end of life soon. Why don't you upgrade to the next LTS (8.04) or the latest version?

---

### Post by overdrank on 2009-05-12
You may look [here]("https://help.ubuntu.com/community/RestrictedFormats#Ubuntu%206.06%20and%206.10")

---

### Post by hansdown on 2009-05-12
+1 for 8.04

It is rock stable, and the support will be here until 2011.

---

### Post by lovinglinux on 2009-05-12
+1 for 8.04, unless you cannot upgrade to a newer version due to hardware incompatibility.

Besides, Firefox 1.5 is kind of old. It was replaced by Firefox 2.0 on October 2006 and we are currently using Firefox 3.0.10. Running an old version like 1.5 might be a security risk and might give you incorrect rendering of some web sites, since the web standards are always evolving.

---

### Post by da85 on 2009-05-12
Is it possible to upgrade my firefox and ubuntu to newer versions over the net without a CD?

Forgive me for being a total newbie, but could anyone direct me how to do this?

---

### Post by _Purple_ on 2009-05-12
You can check here under Upgrade from 6.06 LTS to 8.04 LTS (Network Upgrade)

[https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

---

### Post by gandaran on 2009-05-12
> **da85 said:**
> Hi all,

I'm running Ububtu 6.06 and I'm having real difficulty trying to install flash for firefox to watch videos such as youtube.

I've tried both synaptic and the standard prompts if you go to a site such as youtube to no avail.

I am running firefox version 1.5.0.3

Can anyone help me???
I would recommend to upgrade the new ubuntu 9.04 but if you still prefer 6.06 then the only way to install flash is to do it manually, download the tar.gz package [here]("http://get.adobe.com/flashplayer/") unpack and just move the libflashplayer.so file to /home/user/.mozilla/plugins (make the plugins folder) or /usr/lib/mozilla/plugins, thats all to install.
please note I don't know if the new adobe flash can work with an older version of firefox.

---

