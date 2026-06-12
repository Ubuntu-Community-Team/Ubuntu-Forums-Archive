---
title: "cant turn on visual effects"
date: 2008-10-12
forum: General Help
---

### Post by macman3130 on 2008-10-12
i think ive read everything i can find on this and maybe its just cause im a newb and dont know what to do but i cant figure this out. im running a macbook with tiger and using vmware fussion to run ubunto 8.4 as a virtual machine. i cant turn my visual effects. they are set on none and when i swap them to anything else it flickers and then says cant turn on. please please help me. i love ubuntu used it for a while off cd just playing around before i installed it and now im frustrated!! any suggestions:confused::confused:

---

### Post by icyest on 2008-10-12
Do you know how to put the traditional beryl red diamond icon in the top right corner?

---

### Post by macman3130 on 2008-10-12
nope, i can navigate around, im just new to the command typing and stuff.

---

### Post by Kevbert on 2008-10-12
What you need to do is check the display adapter make/manufacturer.  Go to Applications-Accessories-Terminal and enter
```
lspci
```
The display adapter will be the last item listed.  If it's Intel, ATI or Nvidia compiz 3d effects are possible.  You may need to do a few things to get them going.  If you don't have Advanced Desktop Effects (under System-Preferences) you need to install the compiz manager. You can install this via Applications-Add/Remove and search for ccsm and then install it.  From Advanced Desktop Effects you be able to set up your rotating cube.

---

### Post by armageddon08 on 2008-10-12
> **icyest said:**
> Do you know how to put the traditional beryl red diamond icon in the top right corner?

You can't put that. Because Beryl has long been dead. Beryl has been merged with Compiz to give birth to Compiz Fusion, which you are using now.

---

### Post by macman3130 on 2008-10-12
> **Kevbert said:**
> What you need to do is check the display adapter make/manufacturer.  Go to Applications-Accessories-Terminal and enter
```
lspci
```
The display adapter will be the last item listed.  If it's Intel, ATI or Nvidia compiz 3d effects are possible.  You may need to do a few things to get them going.  If you don't have Advanced Desktop Effects (under System-Preferences) you need to install the compiz manager. You can install this via Applications-Add/Remove and search for ccsm and then install it.  From Advanced Desktop Effects you be able to set up your rotating cube.

thanks im try that when i get off in a few hours ill post back. thanks!!:guitar:


this is what it said----

 lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 01)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 01)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:07.7 System peripheral: VMware Inc Virtual Machine Communication Interface (rev 10)
00:0f.0 VGA compatible controller: VMware Inc Abstract SVGA II Adapter
00:10.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 01)
00:11.0 PCI bridge: VMware Inc Unknown device 0790 (rev 02)
00:15.0 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:15.1 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:15.2 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:15.3 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:15.4 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:15.5 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:15.6 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:15.7 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:16.0 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:16.1 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:16.2 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:16.3 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:16.4 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:16.5 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:16.6 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:16.7 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:17.0 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:17.1 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:17.2 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:17.3 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:17.4 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:17.5 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:17.6 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:17.7 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:18.0 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:18.1 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:18.2 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:18.3 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:18.4 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:18.5 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:18.6 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
00:18.7 PCI bridge: VMware Inc Unknown device 07a0 (rev 01)
02:00.0 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB
02:01.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 10)
02:02.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)
02:03.0 USB Controller: VMware Inc Abstract USB2 EHCI Controller

---

### Post by Kevbert on 2008-10-12
Unfortunately with that VMware display driver I believe you won't be able to run advanced desktop effects as 3d graphics acceleration is not supported.  Compiz-fusion only supports most ATI, Nvidia and Intel display adapters.

---

### Post by theltemes on 2008-10-12
> **Kevbert said:**
> Unfortunately with that VMware display driver I believe you won't be able to run advanced desktop effects as 3d graphics acceleration is not supported.  Compiz-fusion only supports most ATI, Nvidia and Intel display adapters.

Here's my answer (this guy has made a bunch of cross-posts on this):

[http://ubuntuforums.org/showpost.php?p=5953154&postcount=2]("http://ubuntuforums.org/showpost.php?p=5953154&postcount=2")

---

### Post by macman3130 on 2008-10-12
[http://laurentbois.com/2008/04/26/install-ubuntu-804-using-vmware-fusion-on-mac-os-x/](http://laurentbois.com/2008/04/26/install-ubuntu-804-using-vmware-fusion-on-mac-os-x/)



what do you think about what this guy says?	](*,)	](*,)

---

### Post by alexkehrli on 2008-11-24
Can anyone help me? When I click on normal or extra it searches for drivers then says it cant be enabled. I already tried to download compiz-fusion but it doesn't change anything.

---

### Post by rakan21 on 2008-11-30
Yeah. The solution is you can't run advanced graphic desktop effects in VMWare Fusion or Parrallels. Sad but true its because your runing everything through a virtual machine. I've tried so like a million times. Then I just read it on some forum. You just simply can't.

Theres nothing wrong with your graphix card or anything. You can run ubuntu through your CD that you burnt it to. I recommend you do so with a CD-RW because then you can install things such as Compiz Fusion which I recommend for all of you. When your done with everything just restart and take out the CD.

Warning: If you liked ubuntu then use BootCamp Assistant to make a partition. No matter what it will always be called Windows for the start up disk. Even when you insert another OS cd into your mac and click Alt after you click the power button. You will always see Windows as the name of the OS, I suggest you use Ubuntu 8.10 if you install it on your Macbook. 

-Rabayah, Rakan
 any other questions just email me at [email]rakan21@gmail.com[/email].
We all start out as newbs but we some how get a basic understanding of something throw someone else's help.

---

### Post by Forlong on 2008-11-30
> **alexkehrli said:**
> Can anyone help me? When I click on normal or extra it searches for drivers then says it cant be enabled. I already tried to download compiz-fusion but it doesn't change anything.
Post the output of this: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by arcs123 on 2009-11-28
I'm in same situation as [macman3130]("http://ubuntuforums.org/member.php?u=681872") above - using VMWare installed on windows XP with ubuntu 9.10 - my underlying graphics card is ATI Radeon X600 but the VMWare is "bridging" and therefore Ubuntu is not directly talking to the hardware. Has anyone found a way round this issue ? 

have installed cairo, emerald themer, ccsm (compiz config settings manager) etc but cannot switch to "Custom" (which gets installed via ccsm) on the Appearance Preferences -> Visual Effects tab. Get an error message (after searching for available drivers) "Desktop effects could not be enabled". 

am a relative newb to ubuntu  - is there a particular log file i can reference for more info / diagnostics ? Any suggestions welcome - have googled for a while but nothing definitve has been written on how to get advanced desktop features working with ubuntu installed as VMWare virtual machine.

---

### Post by DemonSharkKisame on 2009-11-28
Well, you can't run Compiz, but have you tried sudo apt-get install xcompmgr? If that works, press Alt+F2, tpye gconf-editor and press Enter, go to Apps -> Metacity -> General and check the box where it says "compositing_manager"; if it works, you should be able to get some desktop effects up and running...

---

### Post by bluestar14 on 2009-11-28
probably because its a virtual machine...it can't use all of the resources of the mac, u would have to have it running alone, not as a guest os

---

