---
title: "Canon LBP-660"
date: 2009-02-12
forum: Hardware
---

### Post by ditta on 2009-02-12
Hello,

I'm using Ubuntu 8.10 and I'm trying to install my Canon 660 printer:


1) I downloaded lbp660-0.3.1.tar.gz from [http://www.boichat.ch/nicolas/lbp660/](http://www.boichat.ch/nicolas/lbp660/) and extracted it
2) changed restartcups.sh like it is described [http://ubuntuforums.org/showthread.php?t=610734](http://ubuntuforums.org/showthread.php?t=610734)
3) deleted /usr/share/cups/model, made a new folder called model and copied Canon-LBP-660-lbp660.ppd into it like someone here suggested: [http://ubuntuforums.org/showthread.php?t=610734&page=2](http://ubuntuforums.org/showthread.php?t=610734&page=2) (post #15)
4) Then I installed the lbp660 script using sudo make cups-install-660-a4:
```
install -s -m a=rxs lbp660 /usr/bin
install -s -m a=rxs lbp460 /usr/bin
echo "Installing foomatic..."
Installing foomatic...
install -m a=rx foomatic-rip /usr/bin
install -m a=rx foomatic-gswrapper /usr/bin
rm -f /usr/lib/cups/filter/foomatic-rip
ln -s /usr/bin/foomatic-rip /usr/lib/cups/filter/foomatic-rip
echo "Foomatic installed."
Foomatic installed.
install -m a=rxs ppd/Canon-LBP-660-lbp660.ppd /usr/share/cups/model
install -m a=rxs ppd/Canon-LBP-460-lbp460.ppd /usr/share/cups/model
echo "Restarting CUPS..."
Restarting CUPS...
./restartcups.sh
./restartcups.sh: 3: /etc/init.d/cupsys: not found
Waiting 5 seconds...
echo "CUPS restarted."
CUPS restarted.

```

But I still can't print!

I can see the printer under [http://127.0.0.1:631/printers/](http://127.0.0.1:631/printers/)
```
LBP-660
Beschreibung: LBP-660
Ort:
Marke und Modell: Canon LBP-660 Foomatic/lbp660 (recommended)
Druckerstatus: frei, Aufträge akzeptieren, publiziert.
Geräte URI: file:/dev/null 
```

but the testpage won't get printed.

What do I have to do to make it work (it worked with windows) ?

---

### Post by ditta on 2009-02-12
/dev/null seemed to be weird.

I read about apparmor [here]("https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/163148")

and run:
```
sudo /etc/init.d/apparmor stop

```

Them I installed the printer in the cups interface again which now displays

```
Beschreibung: LBP-660
Ort:
Marke und Modell: Canon LBP-660 Foomatic/lbp660 (recommended)
Druckerstatus: verarbeitend, Aufträge akzeptieren, publiziert.
**Geräte URI: parallel:/dev/lp0** 
```

However this changed nothing :(

---

### Post by ditta on 2009-02-17
Is there something what I could do to make it work?

---

### Post by joseluisgomez on 2009-03-26
I do, here explanation:

[http://ubuntuforums.org/showthread.php?t=1106839&highlight=canon+lbp+660](http://ubuntuforums.org/showthread.php?t=1106839&highlight=canon+lbp+660)

---

