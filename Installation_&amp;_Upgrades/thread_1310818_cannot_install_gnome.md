---
title: "cannot install gnome"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by almodovaris on 2009-11-02
I have just upgraded to Karmic with sudo update-manager -d. I cannot install gnome:

```
$ sudo apt-get install gnome
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd
De status informatie wordt gelezen... Klaar
Sommige pakketten konden niet geïnstalleerd worden. Dit kan betekenen dat u
een onmogelijke situatie gevraagd hebt of dat u de 'unstable'-distributie
gebruikt en sommige benodigde pakketten nog vastzitten in 'incoming'.
De volgende informatie helpt u mogelijk verder:

De volgende pakketten hebben niet-voldane vereisten:
  gnome: Vereisten: gnome-desktop-environment (= 1:2.22.2~4ubuntu8) maar het zal niet geïnstalleerd worden
         Vereisten: gnome-vfs-obexftp maar het is niet installeerbaar
E: Niet-werkende pakketten:
```

For the English speakers, this means that the required gnome-desktop-environment won't be installed. The same applies to gnome-vfs-obexftp.

---

### Post by arubislander on 2009-11-02
Hi Almomaris...

Maybe you could try refreshing the package sources? Open a terminal emulator and type:
```
sudo apt-get update
```
You'll be asked for your password. After that the packages sources will be refreshed, you could then try again

---

### Post by almodovaris on 2009-11-02
Now, I did sudo apt-get update before sudo install gnome. Thinking that it may help, I wiped the Ubuntu partition and reinstalled Kubuntu AMD64 9.10 from the boot CD. Again, when I type:

```
$ sudo apt-get update
$ sudo apt-get install gnome
```

the result is:

```
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd
De status informatie wordt gelezen... Klaar
Sommige pakketten konden niet geïnstalleerd worden. Dit kan betekenen dat u
een onmogelijke situatie gevraagd hebt of dat u de 'unstable'-distributie
gebruikt en sommige benodigde pakketten nog vastzitten in 'incoming'.
De volgende informatie helpt u mogelijk verder:

De volgende pakketten hebben niet-voldane vereisten:
  gnome: Vereisten: gnome-desktop-environment (= 1:2.22.2~4ubuntu8) maar het zal niet geïnstalleerd worden
         Vereisten: gnome-vfs-obexftp maar het is niet installeerbaar
E: Niet-werkende pakketten:
```

I.e gnome-desktop-environment won't be installed, and gnome-vfs-obexftp is not installable.

```
$ sudo apt-get install gnome-vfs-obexftp
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd
De status informatie wordt gelezen... Klaar
Pakket gnome-vfs-obexftp is niet beschikbaar, hoewel er naar verwezen wordt door
een ander pakket. Mogelijk betekent dit dat het pakket ontbreekt,
verouderd is, of enkel beschikbaar is van een andere bron
E: Pakket gnome-vfs-obexftp heeft geen installeerbare kandidaat
```

It says that gnome-vfs-obexftp has no installable candidate.

```
$  sudo apt-get install gnome-desktop-environment
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd
De status informatie wordt gelezen... Klaar
Sommige pakketten konden niet geïnstalleerd worden. Dit kan betekenen dat u
een onmogelijke situatie gevraagd hebt of dat u de 'unstable'-distributie
gebruikt en sommige benodigde pakketten nog vastzitten in 'incoming'.
De volgende informatie helpt u mogelijk verder:

De volgende pakketten hebben niet-voldane vereisten:
  gnome-desktop-environment: Vereisten: fast-user-switch-applet (>= 2.22.0) maar het is niet installeerbaar
                             Aanbevelingen: fam maar het zal niet geïnstalleerd worden
E: Niet-werkende pakketten:
```

It says that fast-user-switch-applet won't be installed.

```
$ sudo apt-get install fast-user-switch-applet
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd
De status informatie wordt gelezen... Klaar
Pakket fast-user-switch-applet is niet beschikbaar, hoewel er naar verwezen wordt door
een ander pakket. Mogelijk betekent dit dat het pakket ontbreekt,
verouderd is, of enkel beschikbaar is van een andere bron
Echter, de volgende pakketten vervangen dit:
  gdm
E: Pakket fast-user-switch-applet heeft geen installeerbare kandidaat
```

It says that gdm replaces fast-user-switch applet and that fast-user-switch-applet has no installable candidate.

Googling gnome-vfs-obexftp, I found some articles saying that it has been replaced long ago with gvfs. But, I have gvfs installed and I have also installed (later) the gdm package.

I think that the packages for installing gnome from the KDE or other environments have broken dependencies, maybe because their refer to packages which have been replaced with newer packages.

---

### Post by almodovaris on 2009-11-02
And here comes the really good part: 

I am able to log to the Gnome environment. In fact, I am writing this message being logged in Gnome.

However, sudo apt-get install gnome produces the results which I have mentioned.

---

### Post by arubislander on 2009-11-03
> **almodovaris said:**
> I think that the packages for installing gnome from the KDE or other environments have broken dependencies, maybe because their refer to packages which have been replaced with newer packages.

Sounds like you might be right. Maybe you should send in a bug report.

---

### Post by purct on 2009-11-05
> **almodovaris said:**
> And here comes the really good part: 

I am able to log to the Gnome environment. In fact, I am writing this message being logged in Gnome.

However, sudo apt-get install gnome produces the results which I have mentioned.

How did you manage to login to Gnome environment unless it was ready installed on you system? or did you force the install by using a switch to ingnore the dependancies?

When I try to install gnome I get the same error as you...  but it doesn't even try to download/install gnome because of the unmet dependancies....

---

### Post by purct on 2009-11-08
OK, I have managed to install GNOME.   Instead of installing GNOME or GNOME-DESKTOP-ENVIRONMENT, I installed GNOME-CORE.  I could then access GNOME desktop.

:)

---

