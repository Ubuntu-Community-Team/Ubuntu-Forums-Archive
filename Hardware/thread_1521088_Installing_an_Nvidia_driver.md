---
title: "Installing an Nvidia driver"
date: 2010-06-30
forum: Hardware
---

### Post by Tedel on 2010-06-30
Hello, I'm a newcomer in Linux. So far, everything has worked fine for me, except for my monitor, so I turned to Nvidia website to see whether I could use a driver update.

The last version of Nvidia driver for my computer is 256.35. Xubuntu seems to have version 175. What I wish to know is whether I can download and install the driver myself ([link]("http://www.nvidia.co.uk/object/linux-display-amd64-256.35-driver-uk.html")).

My video card is a GeForce 8600

---

### Post by dino99 on 2010-06-30
if you want/need the latest driver, open synaptic repo and add this ppa:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

then update, upgrade

reboot, then check driver activation: system admin hardware driver

---

### Post by Tedel on 2010-07-01
mm... It didn't work. Synaptic didn't find any file.

ppa:[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

Was it the worng line? What do I need to write exactly?

---

### Post by wojox on 2010-07-01
This is the post I used to upgrade my driver to the more current version [Install NVIDIA drivers manually on Lynx]("http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+lynx")

To add that ppa try:


```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```

---

### Post by Tedel on 2010-07-02
Actually, I tried the first method,, yet I couldn't make it through. There was an error or something, so I went back to the previous configuration. The ugly side of things is that I still have my problem with the graphics. They are OK, but not as they should.

I'll try this second method in the evening. Thank you.

---

### Post by ratcheer on 2010-07-02
That repository is "404 not found".

Tim

---

