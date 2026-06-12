---
title: "printing problem (canon ip1200)"
date: 2008-11-28
forum: Hardware
---

### Post by agunk agriza on 2008-11-28
hai everybody,
i have a problem. my printer (canon ip1200) does not work when i load a file for print it. there are not message from system. i had followed a tutorial on internet how to install ip1200 driver [http://setrom.inbom.com/2007/04/19/canon-ip1200-dan-ubuntu-edgy/]("http://setrom.inbom.com/2007/04/19/canon-ip1200-dan-ubuntu-edgy/").maybe someone can help me? how to fix this problem.

agunk - indonesia

---

### Post by phpmonkey on 2008-12-15
I just got this working on my laptop using the following steps, from [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon)

Open up a terminal and 


1. ```
sudo nano /etc/apt/sources.list
```
Add the line > deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./ 

2. ```
sudo apt-get upgrade
```

3. ```
sudo apt-get install libcnbj-2.6 bjfilter-2.6 pstocanonbj
```

4. Open your web browser and go to > [http://127.0.0.1:631/](http://127.0.0.1:631/) which is the cupsys admin. Under the "home" tab" click "add printer" and follow the instructions, choosing > Canon iP2200 Ver.2.60 as your driver

5. Go to the "Printers" tab, and click "Print Test page".


It shoud be possible to do steps 4-5 through System>Administration>Printing but the correct driver wasn't showing up there for me, so I went through the cupsys browser admin instead.

Note: The only available printing option appears to be 600dpi

---

