---
title: "wifi turns off when lcd display goes to sleep"
date: 2010-04-01
forum: Hardware
---

### Post by tengteng on 2010-04-01
Hello.. I observed that when my laptop's screen goes to sleep after its been inactive for a few minutes (I set it to 5 minutes in the power management gui), the wifi also disconnects.  This is a problem if i'm downloading large files.

I am using lucid beta and the laptop is a thinkpad edge amd turion neo x2 version.

Am I missing some settings?  Is there a way to not let the wifi sleep together with the screen?  Hope somebody can help.  

Thank you very much!;)

---

### Post by mrhhug on 2010-06-03
i agree, had to seearch hard on google to find this config file, guess i didn't know the right keywords:

/etc/default/acpi-support

# Add to this list network interfaces that you don't want to be stopped
# during suspend (in fact any network interface whose name starts with
# a prefix given in this list is skipped)
SKIP_INTERFACES="wlan0"

obviously change wlan0 to the active wireless in you find in iwconfig

---

### Post by tengteng on 2010-06-28
Thanks for your help! I tried your instructions but I can't seem to make it work.  However, I found out that if i plug in a usb mouse on the laptop the wlan doesn't turn off with the screen.  So I just do it that way. :p Not an elegant solution though..

---

