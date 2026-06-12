---
title: "HOWTO: Ubuntu 6.06 on eMachines W4605 (Wal-Mart Special)"
date: 2006-09-25
forum: Hardware &amp; Laptops
---

### Post by HoneyGutClusters on 2006-09-25
[SIZE="2"]After many headaches and fried brain cells, I've finally figured out how to configure Ubuntu to use all the hardware in my eMachines W4605 laptop. This HOWTO should also work for the W4620 model and other similar machines.

Prerequisites:
An Ubuntu 6.06 CD, access to a wired internet connection, and about an hour to kill

Setting up:

**_Step 1: Preparing_**

After installing Ubuntu, connect your laptop to your wired internet connection, start the computer and log on with your user account. Once at the desktop, an Orange update icon should appear at the top bar.

Install these updates (may take up to 30 minutes) then restart.

**_Step 2: Install BCM4318 drivers_**

Follow the steps as lined out at [http://www.ubuntuforums.org/showthread.php?t=190177&highlight=BCM4318]("http://www.ubuntuforums.org/showthread.php?t=190177&highlight=BCM4318") to install the BCM4318 drivers

**_Step 3: Enabling ATI IXP SB400 Sound_**

There is a issue with ALSA and the ATI IXP sound in Ubuntu. ALSA enables the external amplifier by default. The ATI IXP doesn't like this and you must mute the external amplifier. Here's how:

Go to Applications -> Accessories -> Terminal to start a console. At the console, type:

```
alsamixer
```

In alsamixer, hit the right arrow key until you highlight "External". Hit the "m" key to mute the external amplifier, then hit Escape twice to exit alsamixer. Now, again, at the console:

```
gstreamer-properties
```

Change "output" in Default Output Plug-in to ALSA, then hit Test. Hopefully, you hear sound. This will work about 50% of the time.

SUCCESS: Go to Step 4

FAILURE: Follow the processes outlined in [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")(After trying each step, make sure "external" is muted in alsamixer)

**_Step 4: Installing fglrx_**

Follow the steps as outlined at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

And that should be it. Please let me know if this helped you. This is my first writeup for an ubuntu HOWTO.[/SIZE]

---

