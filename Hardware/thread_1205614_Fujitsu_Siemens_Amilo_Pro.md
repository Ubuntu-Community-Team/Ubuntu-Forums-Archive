---
title: "Fujitsu Siemens Amilo Pro"
date: 2009-07-06
forum: Hardware
---

### Post by jonnyhuck on 2009-07-06
Hi all,

I'm new to Ubuntu and have installed it on my Fujitsu Siemens Amilo Pro V2000D Laptop.

It works fine except there appears to be no drivers for the DVD player and the wireless won't work, reason being it is activated in Windows via a hotkey on the keyboard which no longer works now Windows is no longer on the machine. (if you test it on the terminal it recognises the wireless but has it as DISABLED)

Has anyone come across this before and knows where to get the driver (and what to do with it once I've got it) or knows how to sort the wireless thing?

Thankyou!

---

### Post by Esa on 2009-08-13
> **jonnyhuck said:**
> the wireless thing?


Hi,

I Just installed Ubuntu 9.04 to Amilo Pro V2085 and it works fine.
Have you enabled the wireless in BIOS settings?

  Cheers, Esa

---

### Post by montevjl on 2009-08-20
> **Esa said:**
> Hi,

I Just installed Ubuntu 9.04 to Amilo Pro V2085 and it works fine.
Have you enabled the wireless in BIOS settings?

  Cheers, Esa

Hi,
It's not the bios or wireless switch. I never had the problem with 8.10. and even with a 9.10 (dev) version!

But now the issue appears in 9.04. All devices are there (I even use 2 network cards, internal... that nightmare of Intel 2200BG and a usb (Netgear).

It seems from forum that the issue is with drivers. Strange because they are all "nicely" set. If anyone has a clue, please post. Mny tks

---

### Post by mundge on 2009-09-02
I too have had the same problem. I have though come across this link [here](http://odzangba.wordpress.com/2007/05/15/intel-corporation-prowireless-2200bg-amilo-pro-v2000-ubuntu/) which mentions typing in:
 
***sudo modprobe fsam7400 radio=1 ***
 
which turns on the wireless radio, but doesn't last past the boot.
 
It then has 2 more lines
 
***sudo echo fsam7400 >> /etc/modules***
***sudo echo options fsam7400 radio=1 >> /etc/modprob.d/options***
 
which apparently turns the radio on permanently. I can't get it to work, it says 
 
***bash: /etc/modules: permission denied***
 
If anyone can help me straighten this up, I would be grateful, as if these command lines work as well as the first one, then it should sort out the radio.
 
***Thanks!***

---

### Post by djurny on 2010-01-24
> **mundge said:**
> 

***sudo modprobe fsam7400 radio=1 ***

***sudo echo fsam7400 >> /etc/modules***
***sudo echo options fsam7400 radio=1 >> /etc/modprob.d/options***


try this:

```

# become root
sudo su

# have fsam7400 loaded at every boot
echo fsam7400 >> /etc/modules

# set default options for fsam4400
echo options fsam7400 radio=1 >> /etc/modprob.d/options

# insert fsam module
modprobe fsam7400 

# return to normal self
exit

```

sudo will not escalate the '>>' redirection and therefor the redirection is done as yourself and not as sudo'd root :)

---

### Post by ActionParsnip on 2012-04-08
Why not just run:

echo "fsam7400" | sudo tee -a /etc/modules > /dev/null
echo "options fsam7400 radio=1" | sudo tee -a /etc/modprob.d/options.conf > /dev/null
sudo modprobe fsam7400

Your /etc/modprob.d/options file would be ignored as ALL the files in that folder MUST have the '.conf' ending.

As you can see there is no 'sudo su' nonesense here, much neater.

---

### Post by howefield on 2012-04-08
Old thread closed.

---

