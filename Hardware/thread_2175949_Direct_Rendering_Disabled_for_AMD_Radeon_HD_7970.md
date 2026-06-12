---
title: "Direct Rendering Disabled for AMD Radeon HD 7970"
date: 2013-09-22
forum: Hardware
---

### Post by zhengalanzheng on 2013-09-22
Hi, I'm using Linux Mint 13 KDE and I'm experiencing this problem and my graphics card is: AMD Radeon HD 7970. ```
alan@alan-desktop ~ $ inxi -Gx
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Tahiti XT [Radeon HD 7970] bus-ID: 01:00.0 
           X.Org: 1.11.3 driver: fglrx Resolution: 1920x1080@60.0hz, 1920x1080@60.0hz 
           GLX Renderer: AMD Radeon HD 7900 Series GLX Version: 1.4 (2.1 (4.3.12441 - CPC 13.20.11)) Direct Rendering: No

```
I have used Ubuntu 12.04 LTS and Linux Mint MATE before and it wasn't a problem.
Any help will be greatly appreciated.

---

### Post by Yellow Pasque on 2013-09-22
First, remove your current fglrx install (at least one of these commands will fail depending on how you installed it):
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo rm -rf /etc/ati
```

Next, get packages:
```
sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases fakeroot libqtgui4
```

If you are using the x86_64 architecture (64 bit):
```
sudo apt-get install lib32gcc1
``` 

```
cd ~/
wget http://www2.ati.com/drivers/linux/amd-catalyst-13.9-linux-x86.x86_64.zip
unzip amd-catalyst-13.9-linux-x86.x86_64.zip
chmod +x amd-catalyst-13.9-linux-x86.x86_64.run
sudo sh ./amd-catalyst-13.9-linux-x86.x86_64.run  --buildpkg Ubuntu/precise
sudo dpkg -i fglrx*.deb
sudo amdconfig --initial -f
```

Instructions adapted from: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

---

### Post by zhengalanzheng on 2013-09-22
> **Temüjin said:**
> First, remove your current fglrx install (at least one of these commands will fail depending on how you installed it):
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo rm -rf /etc/ati
```

Next, get packages:
```
sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases fakeroot libqtgui4
```

If you are using the x86_64 architecture (64 bit):
```
sudo apt-get install lib32gcc1
``` 

```
cd ~/
wget http://www2.ati.com/drivers/linux/amd-catalyst-13.9-linux-x86.x86_64.zip
unzip amd-catalyst-13.9-linux-x86.x86_64.zip
chmod +x amd-catalyst-13.9-linux-x86.x86_64.run
sudo sh ./amd-catalyst-13.9-linux-x86.x86_64.run  --buildpkg Ubuntu/precise
sudo dpkg -i fglrx*.deb
sudo amdconfig --initial -f
```

Instructions adapted from: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)
Thanks, it worked like a charm.

---

