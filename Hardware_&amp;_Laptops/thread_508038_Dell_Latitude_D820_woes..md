---
title: "Dell Latitude D820 woes."
date: 2007-07-23
forum: Hardware &amp; Laptops
---

### Post by bilbobagginz on 2007-07-23
Hello, guys.
My friend has got a laptop from work.
I've tried to install it with Feisty.

The laptop is this model of Latitude:
[http://support.dell.com/support/edocs/systems/latd820/en/ug/specs.htm#wp1057468](http://support.dell.com/support/edocs/systems/latd820/en/ug/specs.htm#wp1057468)

I cannot state the "Machine Type/Model", but it has:

[LIST=1]
[*]1280x800 display
[*]Intel 945GM and 945PM based graphic chip
[*]Broadcom 1390 based wifi card
[*]fingertips reader device with security chip.
[/LIST]
The installation went as follows:
[LIST]
[*]the auto detection of the display didn't work properly, the live CD took only the regular ratio display, probably 1024x768.
[*]the installtion completed ok
[*]the system rebooted the 1st time.
[*]after the 1st boot, I could not boot once again. i.e.: the kernel was found, and loaded, but it got stuck at some point between the USB driver detection and keymap loading.
[/LIST]
The trick I made was: to boot into the single mode,
then type as root: 
init 2

and it would come up, but this is not something you want to give a 1st time user of linux.

I've tried to add to the grub configuration the following options:
notsc
no_timer_check
this doesn't help.

I've managed to install the ndiswrapper with the windows driver, but this not functioning booting is getting on my nerves.

What is the problem ?
Is this a known issue ?
What do you think I can do to debug this ?

---

### Post by brettr on 2007-07-23
This seems like a pretty standard setup, except for the fingertip reader device, perhaps this is causing the problems. As for the resolution problem, i have heard of people with the intel video device using a app called 915resolution in order to get the correct resolution going, although i was under the impression that this was no longer required. Is there a way to disable the fingertip device in the bios. I am don't have any other adivce than that, hopefully somebody else can help you out some more.

---

### Post by bilbobagginz on 2007-07-23
Thanks for the reply. 

I shall try to actually enable the finger tip device, since I assume this is the same chipset as on the IBM's thinkpads, which actually works with linux.

will try to update the forum on how it went.

---

