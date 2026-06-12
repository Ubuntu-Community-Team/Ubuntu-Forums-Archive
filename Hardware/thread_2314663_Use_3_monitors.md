---
title: "Use 3 monitors"
date: 2016-02-22
forum: Hardware
---

### Post by Madman1978 on 2016-02-22
[COLOR=#111111][FONT=Ubuntu]I am a novice on trying to do something like these, so please bear with me.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I am using ubuntu 14.04 LTS I have 1 Acer, 1 Compaq and a generic monitor. I would love to use 3 desktops

[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]1 is on the DVI and the other 2 are presently on the VGA with a spliter.
I don't know what model the video card is.
I have read like 20 different so called solutions and no success yet.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Will be grateful for any assistance.

Ran this 
[B]sudo lspci | grep -i VGA


[/B]
The following was returned
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series] 

Thank you in advance

[/FONT][/COLOR]

---

### Post by QIII on 2016-02-22
First, it depends on the capabilities of the exact model of the graphics adapter.

Second, you are not likely to get an independent output from splitting VGA, but identical outputs.  VGA is analog, not digital.

Can you tell us what sort of outputs the GPU provides?

---

### Post by Madman1978 on 2016-02-22
This card has DVI, VGA and HDMI outputs

---

### Post by QIII on 2016-02-22
Many AMD products will support output to either HDMI or DVI, but not both.  Some will.  So without the exact model number, it would be hard to say if that will work.

As for VGA, again it's analog and the output is likely to be identical with a splitter.

You would really need to know the specs of the adapter.  If it will output to the HDMI and DVI simultaneously, you could probably do this with all three outputs simultaneously.  I'd stay away from the VGA splitter idea for now. 

If you can find out the exact model number of the adapter, we might be able to look this up.

I'm assuming this is a desktop?

---

### Post by Madman1978 on 2016-02-22
Yes, this is a desktop.  
Yes, I found out you can only run 2 outputs at one time.  To find the exact model means I have to open it up and look.

---

### Post by Madman1978 on 2016-02-22
I wonder if I just add a second VGA card that I can achieve what I am looking to do.  I am hoping to have 3 desktops when done.

---

### Post by CharlesA on 2016-02-22
What does this return?

```
sudo lshw -C video
```

[http://askubuntu.com/questions/72766/how-do-i-find-out-the-model-of-my-graphics-card](http://askubuntu.com/questions/72766/how-do-i-find-out-the-model-of-my-graphics-card)

---

### Post by QIII on 2016-02-22
There are a couple of important considerations there:

Most OEMs do no create Linux drivers that support a mix of different manufacturers' adapters.  So you'd have to get another AMD adapter.

Even within a single manufacturer's products, the drivers often will not work with a mix of models.  Certainly the driver will not work if you get anything earlier than an HD 5000 series card, because AMD no longer supports them.  Even an HD 6000 series would not be guaranteed to work if it is not the same model.

---

### Post by Madman1978 on 2016-02-22
*-display               
       description: VGA compatible controller
       product: Cedar [Radeon HD 5000/6000/7350/8350 Series]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:43 memory:d0000000-dfffffff memory:fe9e0000-fe9fffff ioport:dc00(size=256) memory:fea00000-fea1ffff

---

### Post by QIII on 2016-02-22
I think you may need to take out the thumb screws and pop the side off the case.  I don't want to tell you to spend your money, but a second card would certainly be helpful.  If you have an inexpensive card, you may be able to match it and we can talk you through initializing both cards.

---

### Post by Madman1978 on 2016-02-22
I only have one PCI Express slot and 2 other PCL Slots 
Someone suggested this : [COLOR=#111111][FONT=Ubuntu]Use an HDMI to DVI adapter cable for the DVI monitor, a DVI to VGA adapter cable for one VGA monitor, and a VGA to VGA cable for the last monitor.
[/FONT][/COLOR]

---

### Post by Madman1978 on 2016-02-22
I have only one PCI Express slot.  with 2 other PCI Slots. 

Someone suggested this 
[COLOR=#111111][FONT=Ubuntu]Use an HDMI to DVI adapter cable for the DVI monitor, a DVI to VGA adapter cable for one VGA monitor, and a VGA to VGA cable for the last monitor.[/FONT][/COLOR]

---

### Post by QIII on 2016-02-22
The problem is that the adapter may only output to DVI or HDMI, but not both.  That's a physical design limitation.  The only way to know is to find out the exact model and look at AMD's specs for that card.

---

