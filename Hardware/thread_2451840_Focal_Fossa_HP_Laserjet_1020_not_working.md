---
title: "Focal Fossa HP Laserjet 1020 not working"
date: 2020-10-12
forum: Hardware
---

### Post by kadal27 on 2020-10-12
Unable to install HP Laserjet 1020 after installing Ubuntu 20.04 Focal Fossa. Searched everywhere and found that HP has no driver for Focal Fossa. foo2zjs driver is also not working. Is there any way to make my HP Laserjet 1020 to work on 20.04 or I need to switch the operating system?

---

### Post by CelticWarrior on 2020-10-12
You need to install hplip:

```
sudo apt install hplip-gui
```

That IS the driver.

---

### Post by ajgreeny on 2020-10-12
That printer used to also need a plugin but installing that plug in was another step in the hplip installation process.

---

### Post by slickymaster on 2020-10-12
Thread moved to **Hardware**

---

### Post by cogier2 on 2020-10-13
This printer is supported by HP. You can check out supported printers [here]("https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index"). If you have used **hplip-gui** to install the printer and it sees it but then can't communicate with it then it could be a problem with a file called **ippusbxd**. I have fixed 2 printers and one scanner all on Linux Mint, which is based on Ubuntu, by removing this file. You could try removing the file with **sudo apt-get -y purge ippusbxd**. Normal warnings apply about backups etc. but I have had no issue. Interestingly this issue is not present in Ubuntu 20.10.

---

