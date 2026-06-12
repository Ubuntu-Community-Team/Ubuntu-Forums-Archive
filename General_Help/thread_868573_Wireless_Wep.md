---
title: "Wireless Wep"
date: 2008-07-24
forum: General Help
---

### Post by SpenceMakesSense on 2008-07-24
At my house I have 3 computers with ubuntu/xubuntu. And they re dualbooting with xp. The problem is is that ubuntu/xubuntu cant connect to my home network which has a wep code while my windows install can. Ive had it working before and stopped using wifi for a few months while on a direct connection and when I come back they wont connect. But i can connect to my neighbors connections which doesnt have a wep code. Im very lost:confused: and dont understand why its doing this. I know my cards(actually usb adapters) work correctly because I can connect via windows and I can connect to a connection that doesnt have wep.

---

### Post by ajmorris on 2008-07-24
> **SpenceMakesSense said:**
> At my house I have 3 computers with ubuntu/xubuntu. And they re dualbooting with xp. The problem is is that ubuntu/xubuntu cant connect to my home network which has a wep code while my windows install can. Ive had it working before and stopped using wifi for a few months while on a direct connection and when I come back they wont connect. But i can connect to my neighbors connections which doesnt have a wep code. Im very lost:confused: and dont understand why its doing this. I know my cards(actually usb adapters) work correctly because I can connect via windows and I can connect to a connection that doesnt have wep.
 
hi there,
what method are you using to connect to your WEP network? i.e. the network icon in your gnome taskbar, wicd, straight terminal commands etc.
 
AJ

---

### Post by danwood76 on 2008-07-24
It could be a keyring issue.

Right click the network manager icon and click edit wireless networks, delete your home network and try and reconnect, re entering the wep key and so on.

---

### Post by cszikszoy on 2008-07-24
Might seem obvious, but it gets me sometimes.  When you're typing in the wep key, make sure you've selected 64/128 hex, if your password is hex.

The default is 64/128 bit passphrase, and I find myself typing my hex password in with the passphrase option selected sometimes.

If it's not that, what kind of usb wireless adapters are you using?  Have they ever worked with ubuntu?

What you describe, being able to connect with no encryption, but not able to connect with encryption could be a driver issue.  One fix might be to use ndiswrapper and just use the windows drivers.

---

### Post by SpenceMakesSense on 2008-07-24
> **ajmorris said:**
> hi there,
what method are you using to connect to your WEP network? i.e. the network icon in your gnome taskbar, wicd, straight terminal commands etc.
 
AJ

I am connecting from the gnome taskbar. 


> **cszikszoy said:**
> Might seem obvious, but it gets me sometimes. When you're typing in the wep key, make sure you've selected 64/128 hex, if your password is hex.

The default is 64/128 bit passphrase, and I find myself typing my hex password in with the passphrase option selected sometimes.

If it's not that, what kind of usb wireless adapters are you using? Have they ever worked with ubuntu?

What you describe, being able to connect with no encryption, but not able to connect with encryption could be a driver issue. One fix might be to use ndiswrapper and just use the windows drivers.

No luck..when i enter the wep code it wont let me connect with anything but the default 128 bit passphrase selection. I am using linksys wireless N for my ubuntu and my xubuntu computers. In which I installed via ndisgtk and they had worked about 4 months ago. But I had stopped using wireless. Meaning between the time I stopped using is and was forced to use it again that there was some update that messed it up. But my xubuntu was a clean install without any updates because I couldnt connect to the internet. But I had burned that disc and installed xubuntu only about 2 weeks ago.So that also mght mean they they added some update to it.

---

### Post by SpenceMakesSense on 2008-07-25
bump:cool:

---

### Post by danwood76 on 2008-07-25
Have you tried deleting all the wireless networks in your keyring?
Or deleteing the keyring entirely?

---

