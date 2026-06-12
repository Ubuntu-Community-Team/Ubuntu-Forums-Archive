---
title: "Looking for advice"
date: 2008-03-21
forum: Hardware &amp; Laptops
---

### Post by yazuki101 on 2008-03-21
I have recently purchased my first laptop. To my dismay  not only is it preloaded with Vista, but it also seems to be a model specific to Canada and therefore hard to find info on. I could only find 5 sites about this particular model using google, and that was just looking for the specs. 

I have ubuntu successfully loaded using the LiveCD. But I cannot seem to get the built in wireless to work (it doesn't even seem to be recognized by ubuntu), also I cannot not get the effects to work.

As this is my first laptop, I am loathe to experiment on it as I would a desktop model. So I figured I would consult the Gurus and see what people can tell me about it. The Specs are as follows:

OS: 7.10 Gutsy Gibbon
Model: Toshiba A200-MR0 (Supplier Part Number: PSAE3C-MR008C)
Processor (CPU): Intel Celeron Processor 540 1.86GHz
Memory: 1 GB DDR2
HDD: SATA 160GB
Video Card / Ram: Mobile Intel GMA X3100 with up to 251MB of shared video memory
Wireless (WIFI): 802.11b/g

*Note: Copied Verbatim (except the HDD line) from [[COLOR="Red"]http://209.167.114.38/support/TechSupport/quickspecs/quickspecs.asp?id=Quick%20Specs%20Chart&family=Satellite&partnum=PSAE3C-MR008C[/COLOR]]("http://209.167.114.38/support/TechSupport/quickspecs/quickspecs.asp?id=Quick%20Specs%20Chart&family=Satellite&partnum=PSAE3C-MR008C")

---

### Post by Yellow Pasque on 2008-03-21
For desktop effects, see the following link. You'll either have to disable the effects when you want to watch video or turn off hardware-accelerated video playback (slow):
[http://ubuntuforums.org/showpost.php?p=4202892&postcount=6](http://ubuntuforums.org/showpost.php?p=4202892&postcount=6)

For the wireless, you'll need to give more info. Post the output (just the section about your wireless adapter) of:
```
sudo lshw -C network
```

---

### Post by tommcd on 2008-03-21
A quick google search turns up no info on the the laptop model # you posted. Type "sudo lspci -v" in terminal to find the wireless chipset your laptop uses. It should be near the end of the output. If the wireless chipset is recognized the the chipset used will determine what you need to do to get it working. You may just need to install a driver, or use ndiswrapper to use the windows driver in linux.

---

### Post by yazuki101 on 2008-03-21
alright, so after putting "sudo lshw -C network" into the terminal it brought up my hard line card first (which is working properly so I won't bother copying that in). But here is what came up for my wireless card.

*-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0

As for the graphics, I have yet to try anything. I will post back once I have.

---

### Post by yazuki101 on 2008-03-21
> **Temüjin said:**
> For desktop effects, see the following link. You'll either have to disable the effects when you want to watch video or turn off hardware-accelerated video playback (slow):
[http://ubuntuforums.org/showpost.php?p=4202892&postcount=6](http://ubuntuforums.org/showpost.php?p=4202892&postcount=6)

For the wireless, you'll need to give more info. Post the output (just the section about your wireless adapter) of:
```
sudo lshw -C network
```

So I went to that post and tried the first step, and I figured I would post my output from typing 'compiz' into the terminal, as per the final step. Then I will follow the instructions regarding blacklisted hardware.

Output:
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 

Also regarding the video playback, would an earlies version of ubuntu (or perhaps even using xubuntu) resolve that?

---

### Post by yazuki101 on 2008-03-21
ok so finally, here is the output from my final step (the black list removal):

yazuki101@yazuki101-laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 0c) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity ^[[B

---

### Post by wncben on 2008-03-21
> **yazuki101 said:**
> alright, so after putting "sudo lshw -C network" into the terminal it brought up my hard line card first (which is working properly so I won't bother copying that in). But here is what came up for my wireless card.

*-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
  

As for the graphics, I have yet to try anything. I will post back once I have.

You have an atheros ar5006eg chipset on your wifi, the fact that it is saying it is 'unclaimed' means that you do not have a driver set up for it yet.
 I believe the driver you need is 'madwifi' which is the atheros driver, which I believe is available if you got system>admin>restricted drivers.  madwifi uses a hal with some sort of copyright issue (i believe) so there is also a driver called ath5k which is free as in free beer and freedom, which is sort of an offshoot of the madwifi project.  there are many posts here in the forums which deal with each, (I am cursed with a broadcom card myself, and believe you are in for a lot easier time than I had)
Good Luck
~Ben

---

### Post by yazuki101 on 2008-03-21
i am relieved that I have an easier system to install ubuntu on this time. My last experience was pretty rough, it seemed like all the hardware I had was the wrong kind to run linux (AMD, nvidia, etc...) 

I will look in the drivers that you mentioned and post back.

---

### Post by yazuki101 on 2008-03-21
i am having issues with the madwifi, and have posted to another thread about the errors I am having [[COLOR="blue"]here.[/COLOR]](http://ubuntuforums.org/showthread.php?p=4560021#post4560021)

---

