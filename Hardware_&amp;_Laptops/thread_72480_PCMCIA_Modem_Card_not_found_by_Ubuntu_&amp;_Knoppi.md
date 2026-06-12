---
title: "PCMCIA Modem Card not found by Ubuntu &amp; Knoppix"
date: 2005-10-06
forum: Hardware &amp; Laptops
---

### Post by ham-on3wheels on 2005-10-06
I have a laptop and don't know if this is a hardware specific problem or
something about my software configuration.

I have a PII, Proc speed-(?somewhere in the 300Mhz range) Panasonic 
Toughbook CF71 that is running a dual OS of Win2000 and Ubuntu Hoary.  I am not able to get Ubuntu to get me online with the only modm I have, a Xircom modem/ethernet PCMCIA card.  I do not have broadband, so dial up is what I use.    

An interesting thing, earlier this year I had a different hard drive in the pc running Win98se and first ran Ubuntu Live and later erased the HD and just Ubuntu installed.   With both of these configurations, I had the same problems.   I have a Knoppix Live CD called Harv's Ham Shack and again, I try to configure the modem / network fields and still unable to get the OS to recognize the PCMCIA card.    

I don't get any "failed to recognize" error messages, rather I am just not able to get online.   In Hoary, I have to uncheck a box in one of the networking/modem areas, so I can enter information, but then I have to click and check the box so I can save things.  However, clicking the box, always deletes my information.  

I need all the help I can get on this one.   I am a newbie and have been
puzzled with this dilemma for months.

Thanks

---

### Post by spd106 on 2005-10-10
I have a Xircom Global Access CreditCard modem 56 (CM-56G) on my laptop running Hoary. It doesn't show up with **lspci**, though **dmesg | tail** shows a device set to ttyS3 when plugged in. I can also see that **sudo cardctl ident** shows the card correctly. Also use **lsmod** to check if the serial_cs module is loaded.

I found that setting up the ppp0 connection was just a matter of opening the network manager, then putting in the number to dial and selecting ttyS3 as the device. On activation it dials out fine. 

Perhaps it might work after installation to disk. 

Good luck

---

### Post by stray1 on 2007-03-17
> **ham-on3wheels said:**
> I have a laptop and don't know if this is a hardware specific problem or
something about my software configuration.

I have a PII, Proc speed-(?somewhere in the 300Mhz range) Panasonic 
Toughbook CF71 

Did you use any special boot commands to get Ubuntu on there? I have the exact same laptop and cant even get it installed....

---

### Post by turtles on 2007-03-17
Can you run this script and post the output.
```
#a pcmcia-tool by turtle
echo "list everything we know about this card"
pccardctl status
pccardctl ls
pccardctl info
pccardctl ident
echo "dmesg:"
dmesg | grep pci
dmesg | grep pcmcia && dmesg | grep Yenta
echo "/etc/pcmcia/config.opts"
less /etc/pcmcia/config.opts | grep memory
echo "lspci":
lspci | grep CardBus
lspci -v | grep subordinate 
```

---

