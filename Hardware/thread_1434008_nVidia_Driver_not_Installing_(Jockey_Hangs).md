---
title: "nVidia Driver not Installing (Jockey Hangs)"
date: 2010-03-19
forum: Hardware
---

### Post by shantaram.nz on 2010-03-19
have installed Ubuntu plenty of times on this machine and never had problems getting Jockey to install the video drivers. However with 9.10 it appears to hang when trying to install the nVidia driver (any version).

My graphics card is a nVidia GeForce 8800

lshw -c display:

 *-display UNCLAIMED     
       description: VGA compatible controller
       product: G80 [GeForce 8800 GTS]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f5000000-f5ffffff memory:c0000000-cfffffff(prefetchable) memory:f2000000-f3ffffff ioport:9c00(size=128) memory:f65e0000-f65fffff(prefetchable)

---

### Post by Ayuthia on 2010-03-19
I am not for sure about how Jockey looks like for Ubuntu (I am using Kubuntu) and their is no progress meter for the Download.  Is it possible that it was not done downloading or did you wait for a long time and it did noting?  I am not for sure if your are able to see it data is being downloaded from your router or not, but that was how I was able to tell that something was still running.

---

### Post by shantaram.nz on 2010-03-20
I fixed this issue, by un-installing and re-installing jockey-gtk.

---

