---
title: "Ethernet and resolution issues on a Toshiba NB510-10R"
date: 2012-08-02
forum: Hardware
---

### Post by thanasis57 on 2012-08-02
I recently bought a netbook for my wife, on which I wanted to install some GNU/Linux distro (and then get a Windows tax refund as [I had already done a couple of years ago]("http://www.ardin.gr/?q=node/3893")).
 It is therefore evident that the installation should have a high WAF (Wife Acceptance Factor), or I would never hear the end of it!
 
 I chose to install Ubuntu 12.04. The main problems after a fresh install were that the ethernet card (eth0) was not even recognized and that the resolution was stuck at 800x600. These issues were quite easily resolved from already posted solutions. I am just reposting the solutions, distilling them down to the bare essentials for future reference.
 
 **1) Ethernet**
 The solution was found [here]("http://askubuntu.com/questions/157223/12-04-does-not-detect-eth0atheros-ar8162"). The problem resides with the Atheros ar8162, for which a driver needs to be manually installed.
 
 Execute the following:
```
wget http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2012-02-28-p.tar.bz2 
tar -xvf compat-wireless-2012-02-28-p.tar 
cd compat-wireless-2012-02-28-p 
scripts/driver-select alx 
make 
sudo make install 
sudo modprobe alx

```**2) Resolution**
 The solution was found [here]("http://askubuntu.com/questions/163448/fixing-800x600-resolution-in-toshiba-nb510-gma-3650-with-vesa-driver").
 
  a) Add repository and install packages 
```
sudo add-apt-repository ppa:sarvatt/cedarview 
sudo apt-get update 
sudo apt-get install cedarview-drm cedarview-graphics-driver 

``` b) Restart and at the GRUB prompt, select the Ubuntu entry and press "e".
  
c) Using the cursor keys, move to the line containing [FONT=Courier New]quiet splash[/FONT] and delete [FONT=Courier New]$vt_handoff[/FONT] from it. 
  
d) Press F10 to boot. 
  
e) After booting, open [FONT=Courier New]/etc/default/grub[/FONT] as root:
```
sudo nano /etc/default/grub
``` (or use any other text editor)
Add the following line at the end of the file:
[FONT=Courier New]GRUB_GFXPAYLOAD_LINUX="auto"[/FONT] 
  
f) Save changes, close and run
```
sudo update-grub
```That's it! Afterwards everything worked fine (including shortcut keys and suspend) and I was a happy husband!

---

### Post by mfbx9da4 on 2013-04-10
Hi i have tried your instructions but since i have no internet i have had to download the driver and unzip it that way. problem is i cant use the make command as i am on puppy linux any suggestions

---

