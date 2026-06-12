---
title: "Conexant internal modem finishup."
date: 2008-08-14
forum: General Help
---

### Post by ZeroRider13 on 2008-08-14
I have been trying to get and instal drivers for my conexant internal modem and mc4man helped me totally, and now everything is set and downloaded.  All te libs, the alsa driver, the modem driver, and the patch. Now that this is all done, how do I configure it and connect up?  Im using NetZero by the way.

---

### Post by prshah on 2008-08-14
> **ZeroRider13 said:**
> I have been trying to get and instal drivers for my conexant internal modem and mc4man helped me totally, and now everything is set and downloaded.  All te libs, the alsa driver, the modem driver, and the patch. Now that this is all done, how do I configure it and connect up?  Im using NetZero by the way.

Usually, ```
sudo pppoeconf
``` is used to setup dial-up connections. I have no idea what NetZero is (ISP?)

EDIT: The above is wrong; thanx to Irihapeti for pointing it out; The correct command is indeed "pppconfig"; leaving it as it is to prevent confusion. This is the second time today. Maybe I need a rest and/or psychiatric evaluation.

---

### Post by Irihapeti on 2008-08-14
Just a minor correction:
PPPoEconf is for PPP over Ethernet modems.

For a dialup modem, use:

```
sudo pppconfig
```

You can also install Gnome-PPP (in the repositories) which gives you a GUI interface.

My experience is that it's best to use pppconfig for the initial setup. Whenever I've started out with Gnome-PPP, the connection has died almost immediately after connection. But if I use pppconfig first, then Gnome-PPP behaves fine. Why? I don't know.

Irihapeti

---

### Post by ZeroRider13 on 2008-08-14
Well, number one, it asks me for an ip number..what is that?  Can you help me through what to put into the pppconfig stuff?  Oher than that, if I did everything right, I saved the connection, then wrote pon into the tewrminal, and nothing happens, Ijust get another line.  When I press wvdial it says internet dialer 1.60, when I press wvdialconf it says it cant find a modem...but I instlaled the drivers and everyhting for that conexant driver...

---

### Post by ZeroRider13 on 2008-08-14
Sorry for the double post, but I went ahead ad downloaded Gnome ppp basically because Im not so good with Linux, so an easy interface was nice, but I tested all my ports...and my modem STILL isnt recognized...how is it not if I have all the drivers?  Anyway i can get it recognized?

---

### Post by Irihapeti on 2008-08-14
ZeroRider13:
Have you configured the modem drivers? You need to open a terminal and enter the command:
```
sudo hsfconfig
```
If you don't have a license for it yet, that doesn't matter - you'll still be able to get it to work if everything else is set up right. It will be restricted to 14K, though.

Your ISP may be different (I'm in New Zealand), but all I had to do in Gnome-PPP was click on "dynamic ip" and "automatic dns". 

The modem is most likely to be /dev/ttysHSF0. pppconfig is not good at finding my modem, and I have to put it in by hand.

Irihapeti

---

### Post by ZeroRider13 on 2008-08-17
Well, does it help If I told you I have 4 slots in the abck of my computer and the mdoem is the 3rd?  Would that give you a better idea of where it is?

Also, is it a Analog, ISDN, or USB modem?  SO far, itc ant detect no matter what I do, but if you answer those qustions up there it mgih tmake it easier to do.  ALso I have a USR USB modem, if I plug that in, what location would I type in with USB modem?

---

### Post by Shazaam on 2008-08-17
ZeroRider13....
Juno user here (brother to netZero). The drivers for your modem, do you know if they are HCF or HSF drivers?
The config code for the terminal will be either...
```
sudo hcfpciconfig
```
or...
```
sudo hsfpciconfig
```

---

