---
title: "Disable internal wifi card"
date: 2012-03-05
forum: Hardware
---

### Post by c2tarun on 2012-03-05
Hi friends,

I have Dell Inspiron -N4010 laptop.
I want to disable my internal wifi card. My internal wifi card is little bit buggy with KDE's network manager, as it freezes whole KDE as soon as I connect to any network. I got external wifi adapter and I want to use that only.

I google and found that I can add some entry to /etc/modprob.d/blacklist.conf file to disable a hardware.
I dont know what to add :( can anyone please help me?

Below is the output of my lsmod
[http://pastebin.com/MRSQwvWH](http://pastebin.com/MRSQwvWH)

---

### Post by ahallubuntu on 2012-03-05
Try disabling the internal wireless card in the BIOS Setup.

It isn't that difficult to replace the internal WiFi card in a Dell laptop.  If you have a Broadband card, you might try a compatible Intel wireless card instead.  I find USB wireless cards a bit of a burden for a laptop.

---

### Post by bkratz on 2012-03-05
If the bios option is not available:

We would need to find out what card you have for the internal wireless. Enter the terminal and post the output of the following back here: (using the code tags <>).
[FONT=monospace]
[/FONT]```
lspci -nnk | grep -iA2 net
```

and 


```
lsmod
```

the first will show the wired and wireless devices, the second what modules are loaded.

---

