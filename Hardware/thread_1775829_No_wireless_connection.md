---
title: "No wireless connection"
date: 2011-06-05
forum: Hardware
---

### Post by DC80 on 2011-06-05
Hi all,
 
I have a problem connecting to my wireless network. When i installed 11.04 everything worked great! Even my wireless connection, however after updating i lost my connection to my network.
 
As I open the network manager i can see that the wifi card is disabled by a hardware switch. I can not enable the wireless connection in any other way. I will try to give as many as posible information. I will start with:
 
- Laptop: Acer Aspire 3680
- Ubuntu: 11.04
- Network device: Atheros (do not know the model)
- NIC Drivers: ath5k, ath, mac80211
 
I did try some suggestions like rfkill but this didn't work.
 
rfkill output:
 
```

user@laptop:~$ rfkill list all
0: phy0: Wireless LAN
            Soft blocked: no
            Hard blocked: yes
user@laptop:~$ 

```
 
A rfkill unblock all command didn't work.
 
Please can someone help me?
 
Kind regards,
 
DC80

---

### Post by dmizer on 2011-06-05
Try toggling the wireless switch on the front of the laptop until the wireless light comes on.

---

### Post by DC80 on 2011-06-05
It is always on, it won't even go out/off when i try to toggle it. :(

---

### Post by dmizer on 2011-06-05
Please post the output of the following two commands:
```
lshw -C network
```
```
lspci
```

---

### Post by DC80 on 2011-06-05
May i ask what you are looking for? I have no cable at hand this moment so i'm not able to "paste" any output.
 
From what i understood was that the network was disabled.
 
Some info:
 
Product: AR2413
Vendor: Atheros communications inc
Version: 01
Config:
- broadcast: yes
- driver: ath5k
- driver version: 2.6.38-8-generic
 
The second command is too much to type (i'm using a mini laptop and it is hard to type) :oops:

---

### Post by dmizer on 2011-06-05
> **DC80 said:**
> May i ask what you are looking for? I have no cable at hand this moment so i'm not able to "paste" any output.
 
From what i understood was that the network was disabled.
 
Some info:
 
Product: AR2413
Vendor: Atheros communications inc
Version: 01
Config:
- broadcast: yes
- driver: ath5k
- driver version: 2.6.38-8-generic
 
The second command is too much to type (i'm using a mini laptop and it is hard to type) :oops:

If you've got a thumb drive handy that would be a good way to transfer the information, but I was looking for the product ID (AR2413), which you've included so no reason to wear out your netbook keyboard :). It would be nice to have the actual output so if you can edit your post to include it later, it might help.

---

### Post by dmizer on 2011-06-05
Have a look here for your possible solution (post 4) -> [http://ubuntuforums.org/showthread.php?p=10884683](http://ubuntuforums.org/showthread.php?p=10884683)

You will need a network connection to apply the fix though. Sorry.

---

### Post by DC80 on 2011-06-06
Hi dmizer,
 
This is not a problem. I will test it this evening. Also post 4 is nothing useful (or i looked wrong). I will let you know how this turned out.
 
Thank you for your support.
 
Kind regards,
 
DC80
 
Edit: It was post 7 :).

---

### Post by DC80 on 2011-06-06
Hi dmizer,

It worked! Thank you for helping me. I will set this topic to solved!

Kind regards,

DC80

---

### Post by dmizer on 2011-06-06
> **DC80 said:**
> It worked!
\o/

Fantastic.

---

