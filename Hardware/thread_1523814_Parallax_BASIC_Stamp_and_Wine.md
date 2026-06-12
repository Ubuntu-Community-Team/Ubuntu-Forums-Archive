---
title: "Parallax BASIC Stamp and Wine"
date: 2010-07-04
forum: Hardware
---

### Post by mike72204 on 2010-07-04
After several days of frustration, I have finally found a solution.

This is for anyone trying to use Parallax's BASIC Stamp Editor in Wine.

Hardware:
Dell Inspiron Laptop 1764 (Wal-Mart)
Dynex USB PDA/Serial Adapter (Best Buy)
Board of Education (parallax.com)

Software:
Ubuntu 10.04
Wine 1.1.42 [Applications / Ubuntu Software Center]
BASIC Stamp Windows Editor v2.5 (R2) [http://www.parallax.com/tabid/441/Default.aspx]("http://www.parallax.com/tabid/441/Default.aspx")

1. WITHOUT the USB adapter, open a terminal window and type:
```
lsusb
```

You should see something like this:
```
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 003: ID 0c45:641d Microdia 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

2. Plug in the USB adapter and again type:
```
lsusb
```
Now look for a change:
```
**Bus 002 Device 004: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port**
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 003: ID 0c45:641d Microdia 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
UBUNTU will assign it to /dev/ttyUSB0

3. Now you need to set up a symbolic link. In your terminal type:
```
cd
cd .wine
sudo ln -s /dev/ttyUSB0 ./dosdevices/com1
```

4. **VERY IMPORTANT STEP**... apparently, Wine has stopped supporting serial ports out of the box, so you'll have to install registry entries. Do the following in your terminal:
```
wget -O comport.reg http://bugs2.winehq.org/attachment.cgi?id=10210
regedit comport.reg
```

5. Finally, install the STAMP Editor software. You can get it from Parallax at the link above.

6. Connect your STAMP and start the Editor. Go to RUN / Identify... to see if it's working.

---

### Post by robatron on 2010-09-27
I realize this post is over three years old, but I just wanted to say that I just ran across it, and it solved my problem perfectly! You've made me a very happy man.

Also, I didn't have to perform step four at all and it still worked for me. Maybe Wine changed their ways since then...

Thanks again!

---

### Post by dribron on 2011-04-17
Absolute genius. Not only did this work for the basic stamp, it works just as well for my brainsteam gp 2.0. I was becomming so desperate that I was begining to consider returning to windows on one of my machines for the love of a microcontroller.... LOL You'v saved me!:popcorn: Free popcorn for you!

---

### Post by sageseeker on 2011-04-21
I just used this fix and it still works

Even with the newer 2.6.5 BASIC Stamp

Thank you so much however you did this you've saved my microcontroler class

---

### Post by nrsmac on 2011-12-19
i tried this once and it worked great. However, after re-installing Ubuntu afresh,  then trying again with my BS2 and BOE, I still get the "No Usable Ports" error from my stamp editor....:confused::confused::confused::confused::confused:

Help me please!!!

---

### Post by r2ro on 2012-01-08
Yes, works great in my new laptop Vostro 130.  But tried in my old laptop Inspiron 8100 using the serial (not the USB) and I am stuck.  Any help will be appreciated.

---

### Post by Murphy-10332 on 2012-03-10
This post rocks!!   Thank you. Worked great right from the start.:D

---

### Post by firemonkeyballz on 2013-03-28
I also tried those out dated source files (broken) in Fedora 17... this seems to also work best! TY!!

---

### Post by tjmackmer on 2014-01-31
Hey, Guys! I used this fix in 2014 and it still works!!!:P

I messed up because i did not give myself read and write permissions for the ttyUSB0 file.

If you don't enable this you will get "Can't Open Port: In Use"

Thanks for the fix!!!

---

