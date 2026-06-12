---
title: "GEfore GTX 980 TI low reslution"
date: 2016-03-22
forum: Hardware
---

### Post by darkadvice on 2016-03-22
I'm helping my friend set up a 14.04 ubuntu box and trying to to install a driver for the Nvidia Geforce GTX 980 TI card  [http://www.geforce.com/drivers/results/98373]("http://www.geforce.com/drivers/results/98373")  but the resolution is getting stuck at 1024x 768. What exactly am I doing wrong?

---

### Post by darkadvice on 2016-03-22
Now we're on the "no video mode activated error." Please help!

---

### Post by pqwoerituytrueiwoq on 2016-03-22
id suggest adding the xorg edgers ppa
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa)
you will need the newer drivers for your card that it offers

---

### Post by Drone4four on 2016-03-22
You'll actaully want to add the Graphics Drivers Team's repo and then install one of the more recent nvidia proprietary drivers: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

---

### Post by Drone4four on 2016-03-22
This guide [here]("http://ubuntuhandbook.org/index.php/2014/10/install-latest-nvidia-340-46-via-ppa/") should help if your having difficulty adding a ppa.  This guide installs the mamarley which is slightly dated.  To add a more up to date repo, just replace 'sudo add-apt-repository ppa:mamarley/nvidia' with 'sudo add-apt-repository ppa:mamarley/nvidia'.

---

