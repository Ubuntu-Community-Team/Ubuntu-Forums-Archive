---
title: "Installing Wireless Athero AR5007 on HP Pavilion dv6000"
date: 2009-01-24
forum: Hardware
---

### Post by cliffc on 2009-01-24
I had trouble getting the wireless drivers working so here are the steps of what I did to make it work.

1. Go to "System->Administration-Hardware Drivers" Disable any Atheros support.

2. sudo apt-get install ndiswrapper-common ndisgtk ndiswrapper-utils-1.9

3. download the windows drivers (If you are using 32 bit, make sure to download the 32 bit driver, if you are using 64 bit make sure to download the 64 bit.   This link shows the 64 bit since that is the one I had to use)

wget [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)

4. tar -zxvf ar5007eg-64-0.2.tar.gz (this will unzip the drivers into an ar5007eg-64-0.2 directory)

5. sudo ndisgtk

6. Click "Install New Driver" select the directory you extracted the drivers and select the file "net5211.inf"

7.  Thats it my wireless immediately started working using the steps above.

---

