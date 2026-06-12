---
title: "Conflict between Yubikey / Keepass / Touchpad frozen"
date: 2021-12-03
forum: Hardware
---

### Post by pascal06 on 2021-12-03
Hello everybody,
I'm facing a strange problem between my Yubikey, Keepass, and the computer's Touchpad. Before posting here, I first asked help to Yubico developpers. They suggested me in return to ask help to Xubuntu developers. In the mean time, I asked help on Keepass' Github, I have been suggested to ask to Yubico !

So, here the steps to reproduce the problem:


[LIST=1]
[*]Open a Keepass database, unlock it with master password and Yubikey 5 
[*]Lock the computer session, then login again 
[*]Open keepass, if Yubikey is detected automatically, go to step 5 
[*]If Yubikey isn't detected by Keepass, unplug and re-plug from USB, then click refresh button 
[*]Enter master password 
[*]Database is unlocked, but at this time most of the time touchpad stops functioning. **However, the stick still function.** 
[*]Strangely, if computer session is then locked and thus goes to  user's select screen, touchpad is working, but it still doesn't into the  "faulty" user session. 
[/LIST]

Below, you'll see communication with Yubico team:
[quote=Yubico Nov 24, 2021, 5:15 PM GMT+1]
Hi Pascal,
Thanks for contacting Yubico Support.
I'm afraid there might not be much we are able to do to help concerning this, as this isn't an issue we've seen or had reported previously.
[/quote]

[quote=Yubico Nov 24, 2021, 5:15 PM GMT+1]
Hi Pascal,
Thanks for contacting Yubico Support.
I'm afraid there might not be much we are able to do to help concerning this, as this isn't an issue we've seen or had reported previously.
If you are able to provide steps we can follow to reproduce it consistently, we'd be happy to do some further investigation. Otherwise, the only pointers I can think to offer are to investigate in the general direction of udev, and to consider raising the issue in the Xubuntu community.
I apologize for the inconvenience, but hope that helps.
[/quote]

[quote=Pascal06]
Dear Yubico team,
I received my two Yubikeys 5 NFC last week. I configured them for my Xubuntu 18.04.06 LTS. So now, I'm using one of my Yubikey (the other one is a backup) to login into my session, and I can use it with my KeepassXC password manager too.
However, It happens something strange sometimes: my laptop ALPS touchpad stops to work. I think it is hardly linked to Yubikey. Strangely, at this very moment, KeepassXC isn't able to access to the Yubikey, I need to unplug the Yubikey and plug it again to let KeepassXC access again to the key. To let the touchpad works again, I must reboot my laptop. For the moment, I'm no able to reproduce the problem voluntarily.
Can you help me ?
Thanks a lot in advance.
[/quote]

 My communication with Keepass team is visible [here]("https://github.com/keepassxreboot/keepassxc/issues/7189").

Debugging infos from KeepassXC:

```

KeePassXC - Version 2.6.6
Révision : 9c108b9

Qt 5.9.5
Le mode débogage est désactivé.

Système d’exploitation : Ubuntu 18.04.6 LTS
Architecture de l’unité centrale : x86_64
Noyau : linux 5.4.0-90-generic

Extensions activées :

    Saisie automatique
    Intégration aux navigateurs
    Agent SSH
    KeeShare (partage signé et non signé)
    YubiKey
    Intégration à « Secret Service »
KeePassXC - Version 2.6.6 (installed from ppa)
Révision : 9c108b9

Qt 5.9.5
Le mode débogage est désactivé.

Système d’exploitation : Ubuntu 18.04.6 LTS
Architecture de l’unité centrale : x86_64
Noyau : linux 5.4.0-90-generic

Extensions activées :

    Saisie automatique
    Intégration aux navigateurs
    Agent SSH
    KeeShare (partage signé et non signé)
    YubiKey
    Intégration à « Secret Service »

Bibliothèques cryptographiques :

    libgcrypt 1.8.1
 
```

My system:
```

Operating System: Linux
Desktop Env: XFCE
Touchpad: AlpsPS/2 ALPS DualPoint TouchPad
Computer: Dell Latitude E6420

```

Have you any idea of my problem ?
Thanks a lot in advance for your help.

---

### Post by pascal06 on 2021-12-09
Hello everybody,
I found a little workaround to make the touchpad work again without logout from my session:
```
sudo modprobe -r psmouse
sudo modprobe psmouse
```
Theses two command remove then add again the module from the kernel, and so reset the touchpad.
(source [https://askubuntu.com/questions/528293/is-there-a-way-to-restart-the-touchpad-driver](https://askubuntu.com/questions/528293/is-there-a-way-to-restart-the-touchpad-driver))

---

### Post by pascal06 on 2022-03-05
Hello everybody,
I recently bought a knew computer, and installed the last LTS version of Xubuntu (20.04). So this is a brand knew fresh install.
And bam, I've got exactly the same issue !
Can you help me with this problem ?
I asked help on KeepassXC github and they almost fired me when I said I think there could be a possible issue with KeepassXC !

---

