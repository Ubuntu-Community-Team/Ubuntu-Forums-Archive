---
title: "Graphikkarte ATI Radeon X1950 Pro kompatile 8.10 i368"
date: 2009-01-03
forum: Hardware
---

### Post by schmiedc on 2009-01-03
Die ATI Radeon X1950 Pro funktioniert bei mir dank gweep blendend auf einem 8.10 Ubuntu 32-Bit


```
lspci | grep VGA
```

gibt mir folgendes:

```
01:00.0 VGA compatible controller: ATI Technologies Inc RV570 [Radeon X1950 Pro]
```



installiert man sich dan envyng:
[http://albertomilone.com/envyngfaq.html#A]("http://albertomilone.com/envyngfaq.html#A")

läuft nach dem restart alles bestens



Das dazugehörige ATI Catalyst Contorl Center befindet sich zwar im Menü unter Anwendungen/Zubehör lässt sich dort aber nicht starten da man root-Rechte benötig

Der dazughörige Befehl lautet:

```
sudo amdcccle
```



Sollte dabei noch ein Fehler kommen wie Disalbe ist in dieser Section ein ungültiger Parameter oder so ähnlich einfach die entsprechende Zeile in der xorg.conf auskommentieren

```
sudo vim /etc/X11/xorg.conf
```

will man sich voher noch eine Sicherheitskopie anlegen:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```


danach sollte das Contoll Center über die Shell zu starten sein.

Bei mir funktioniert somit 2 Monitore parallel zu betreiben. Unter Windows würde die Option "Erweiterter Desktop" heißen

---

