---
title: "Video Driver Problems"
date: 2008-09-12
forum: General Help
---

### Post by tklinge on 2008-09-12
I am running a home built machine and everything works fine except my video.  Whenever watching movie files, DVDs, or playing a game that requires any graphical power whatsoever, the screen will start flashing rapidly and become extremely choppy.  My video card is an ATi Radeon HD 2600, and I HAVE activated the restricted drivers.

Any help would be greatly appreciated.

---

### Post by Tank Jr on 2008-09-12
Hi,
I was having the same problem with Ubuntu 8.04. I have an ATI Radeon HD 2400 PRO 128MB video card with the proprietery drivers.
I turned off the desktop special effects and the problem was resolved for me.

---

### Post by tklinge on 2008-09-13
Alright, so I turned off the visual effects and that fixed the problem with video flashing and freaking out.  However, it didn't fix the choppiness while playing a game of any sort.

While running XP I am able to play Warcraft 3 at max settings with absolutely no lag whatsoever, but with Ubuntu I can't even navigate the main menu the lag is so bad.  Any more ideas?

---

### Post by northern lights on 2008-09-13
tklinge, can you post the output of ```
sudo lshw -C display
```Thank you.

---

### Post by tklinge on 2008-09-14
Alright I've posted it below.  Linux is also picking up my integrated nvidia card that I am not using.

  *-display               
       description: VGA compatible controller
       product: RV630 [Radeon HD 2600 Series]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: driver=fglrx_pci latency=0 module=fglrx
  *-display UNCLAIMED
       description: VGA compatible controller
       product: C51G [GeForce 6100]
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:05.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller cap_list
       configuration: latency=0

---

### Post by tklinge on 2008-09-15
bump action

---

### Post by park8b156 on 2008-09-18
bump----note 2400 is doing the same thing envy is installed but ubuntu restricted drives when trying to install them says no drivers needed?????

---

