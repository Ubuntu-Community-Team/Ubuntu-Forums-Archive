---
title: "limewire/java trouble"
date: 2005-12-29
forum: Installation &amp; Upgrades
---

### Post by Akya on 2005-12-29
i cant run limewire without java but for some reason java makes it so i cant use the internet which means i cant search for anything on lime wire, how can i set up java or limewire so i can fix this

---

### Post by Perfect Storm on 2005-12-30
remove your previous java and limewire.

Then:

```
sudo gedit /etc/apt/sources.list
```

add:

[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/b]

```

sudo apt-get update
sudo apt-get install sun-j2re1.5

```

Download Limewire (linux other): [http://www.limewire.com/english/content/downloadfree2.shtml](http://www.limewire.com/english/content/downloadfree2.shtml)

```

cd /where/you/saved/limewire/
sudo unzip -u LimeWireOther.zip -d /opt/
sudo chown -R root:root /opt/LimeWire/
sudo gedit /usr/bin/runLime.sh

```

add the line:

[b]cd /opt/LimeWire/
./runLime.sh[/b]

```

sudo chmod +x /usr/bin/runLime.sh
smeg
```

Click **Internet**, and then **New Entry**.

name: **Limewire**
Comment: **P2P Client**
Command: **runLime.sh**
Icon: **/opt/LimeWire/LimeWire.ico**

---

### Post by don_frank on 2006-01-02
I was actually having this same problem and I followed these steps.  I was able to run all of these steps.  When I go to apps-internet and select limewire, nothing happens.  Any suggestions?

---

### Post by Perfect Storm on 2006-01-03
try run this in the terminal:

```

cd /opt/LimeWire/
./runLime.sh

```

---

### Post by Yautja_Ender on 2006-01-05
Hey, i had the same problems as above and when i tried your last two commands the first worked the second told me i didnt have permision....(im running frostwire instead of limewire(a clone))

---

