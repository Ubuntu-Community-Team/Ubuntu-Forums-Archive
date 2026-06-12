---
title: "Software updates broke Aspire One wireless driver"
date: 2009-03-15
forum: Hardware
---

### Post by wersdaluv on 2009-03-15
I installed Intrepid on the 8gb Aspire One yesterday by following [https://help.ubuntu.com/community/AspireOne#Install%20Ubuntu%20Intrepid%20Ibex%208.10%20on%20the%20Acer%20Aspire%20One](https://help.ubuntu.com/community/AspireOne#Install%20Ubuntu%20Intrepid%20Ibex%208.10%20on%20the%20Acer%20Aspire%20One) . At first, the wireless LAN worked after I applied the instructions from the page. I just did a long software upgrade to update all packages. After that, the wireless LAN stopped working. I applied the instructions again but it still does not work.

Any idea how to fix this? :)

---

### Post by .:Justus:. on 2009-03-15
No worries mate, i had the same problem, it&#347; an issue with the newer kernels, you´ll have to use kernel -7 rather than the newer ones.
You seem like an experienced linux user so i´m sure you know how to switch between kernels, but just in case heres a link to a thread from earlier with the fix.

[http://ubuntuforums.org/showthread.php?t=1078602](http://ubuntuforums.org/showthread.php?t=1078602)

Good luck!

---

### Post by wersdaluv on 2009-03-16
Thanks. The -7 kernel recognizes the existence of the wlan unlike the -11 kernel. However, even if the wlan card is detected, the wlan card still can't connect because it does not detect my wireless router. 

Any idea? 

:)

Edit: It works now. It seems that I have to turn wireless on with the hardware key every time I boot. :)

---

### Post by .:Justus:. on 2009-03-16
> **wersdaluv said:**
> Thanks. The -7 kernel recognizes the existence of the wlan unlike the -11 kernel. However, even if the wlan card is detected, the wlan card still can't connect because it does not detect my wireless router. 

Any idea? 

:)

Edit: It works now. It seems that I have to turn wireless on with the hardware key every time I boot. :)

Yup, i have to do that aswell, but that´s normal, and i think you mean the keyring entry to enable the networkmanagerapplet not the hardware key.
If it´s not that you might have to do something else than me, but as long as it works now who cares^^

---

