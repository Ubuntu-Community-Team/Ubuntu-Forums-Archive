---
title: "How to make work NotOnlyTV LV3H DVB PCI card. STEP BY STEP"
date: 2014-07-17
forum: Hardware
---

### Post by parasistemas on 2014-07-17
**Following this steps I did it work:**
  **1. Open the shell and execute line per line:**
  ```
git clone git://linuxtv.org/media_build.git

git clone --depth=1 git://linuxtv.org/media_build.git

cd media_build

./build    

sudo make install  

gedit /etc/modprobe.d/LV3H.conf

```  **2. Add this line to the blank file:**
  options cx88xx card=81 tuner=71  
  **3. Save it and close Gedit. In the shell execute:**
  ```
wget http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip

unzip -j HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip Driver85/hcw85bda.sys

wget http://linuxtv.org/hg/v4l-dvb/raw-file/3919b17dc88e/linux/Documentation/video4linux/extract_xc3028.pl

perl extract_xc3028.pl

sudo cp xc3028-v27.fw /lib/firmware

modprobe cx88-dvb

```  **7. Reboot. Congratulations! You have your Me-TV (or like program) running and waiting to autodetect channels.**

---

