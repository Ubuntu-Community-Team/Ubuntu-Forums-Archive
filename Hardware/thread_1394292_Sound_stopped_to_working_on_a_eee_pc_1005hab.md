---
title: "Sound stopped to working on a eee pc 1005hab"
date: 2010-01-30
forum: Hardware
---

### Post by mikeannike on 2010-01-30
Hey.  I have been working using ubuntu on my netbook for about 2 months now.  I have to say that using it on my netbook has been a pleaseure and a great learning experience in the process.  I have one problem.  I went to go unsuspend ( take my comp out of suspend mode) and when I went to do anything with sound, the sound was gone.

  The computer in using is EEE pc 1005hab
  
  I ran "sudo lshw -C multimedia".  These are the results:

    *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7db8000-f7dbbfff


Any help is appreciated.  Thanks.

---

### Post by IcarusR on 2010-01-30
I think the sound module has failed to restart.
Post output of 

```
lspci | grep snd
```

| is the character (bar) above \ ie shift + \

---

### Post by mikeannike on 2010-01-30
Ok i ran lspci with and piped the output like you said im not sure what it did or where it went.  But these are the result from the lspci command.


00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
01:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by guine on 2010-01-31
Try doing this with alsamixer - [http://www.shareconnector.com/no-sou...-in-ubuntu-904](http://www.shareconnector.com/no-sou...-in-ubuntu-904)
I had my sound randomly stop on me too and this fixed it for me.

---

### Post by IcarusR on 2010-01-31
Sorry I should have said 

```
lsmod | grep snd
```

---

### Post by IcarusR on 2010-01-31
Googling a bit came up with a lot of results.
Try this...

[https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20ALSA%20to%20work%20after%20suspend%20/%20hibernate]("https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20ALSA%20to%20work%20after%20suspend%20/%20hibernate")

---

### Post by mikeannike on 2010-02-04
> **IcarusR said:**
> Googling a bit came up with a lot of results.
Try this...

[https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20ALSA%20to%20work%20after%20suspend%20/%20hibernate](https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20ALSA%20to%20work%20after%20suspend%20/%20hibernate)


  This works.  The only thing is that went it wake it up from hibernating, I have to manually turn the sound back up.  This is kind of annoying but hey its better than no sound.  Thanks.

---

