---
title: "Issues on Acer Travelmate 5742G"
date: 2012-02-26
forum: Hardware
---

### Post by Ghost_Mazal on 2012-02-26
Lo All ,

I have 2 issues on my laptop:

Acer Travelmate 5742G , Kubuntu 11.10 32bit fresh install with all updates till today

I can't get my graphics drivers (ATI) or wireless drivers (Broadcom) installed.
I go to  System-additional drivers. It shows and I select it , but then it just fails with
the message "Unable to install this driver". see /var/log/jockey.log

I checked the log but can't understand the problem.

The error is the same for both the graphics driver and the wireless driver.

Here's the log file:

```
2012-02-26 19:03:54,668 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-02-26 19:03:54,668 DEBUG: fglrx_updates is not the alternative in use
2012-02-26 19:03:54,680 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2012-02-26 19:03:54,709 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-02-26 19:03:54,709 DEBUG: fglrx is not the alternative in use
2012-02-26 19:03:54,749 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-02-26 19:03:54,749 DEBUG: fglrx_updates is not the alternative in use
2012-02-26 19:03:54,761 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2012-02-26 19:03:54,798 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-02-26 19:03:54,798 DEBUG: fglrx is not the alternative in use
2012-02-26 19:03:54,827 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled


```

How can I get my wireless and graphics drivers installed please.

Thank you

---

### Post by Ghost_Mazal on 2012-02-26
I tried installing the Broadcom STA wireless driver from package manager. No luck , now wireless doesn't show at all anymore as if there is no wireless hardware :(

---

### Post by Ghost_Mazal on 2012-02-28
Lo All , 

I kind off found the problem. Very weird. So when I started up today (on my ethernet as wireless don't work) I was prompted that there is updates. I proceeded to do the updates and bam , same error !!! I am not allowed to update. Only this time with more info , apparently the source can not be verified. I have main server selected with all the ubuntu servers as well (suc as mediubuntu etc.)

So I decided to try something. I switched download location from "main server" to "South-Africa server" where I live. I ran the update again and there all the updates works perfectly. I then wondered by myself and ran the "additional drivers" again as well. And there the wireless driver comes down and installs perfectly and my wireless works now.

So the problem was the "main server" setting in the download from option.

But why ?????? I always used the main server. Anybody have an answer for this weird issue ?

---

