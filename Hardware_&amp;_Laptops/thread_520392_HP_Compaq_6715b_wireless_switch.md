---
title: "HP Compaq 6715b wireless switch"
date: 2007-08-08
forum: Hardware &amp; Laptops
---

### Post by mgazb on 2007-08-08
I have installed 7.04 as a dual-boot system with Vista on my HP 6715b laptop. I have got it all working correctly (text install followed by graphics updates and rebuild ndiswrapper for the BCM4310 wireless). I have successfully connected to several networks.

My problem is the switch to turn the wireless card on and off that is above the keyboard.
It works fine in Vista.
It works fine in Ubuntu if it was switched on when the laptop was turned off.

If wireless was turned off before the laptop was shut down then I cannot turn it on with Ubuntu. There is no entry for wlan0 if I run iwconfig.

Has anyone else found this problem? Is there a solution (apart from turning wireless on before shutdown)?

thanks

---

### Post by barrack on 2007-11-24
BUMP!

i am currently having this problem. i had to reinstall 7.04 on my compaq c500.

i am trying to get the wireless card back up and running as i have in the past, but i first need to be able to turn it back on... unfortunately i'm not dual booting.

thanks.

---

### Post by Podmornik on 2007-11-26
Exactly the same problem here. If I turn the wireless off I have to restart the laptop to get wireless working again.
:(

---

### Post by hekto5 on 2007-12-22
Same here... After booting with switched off wireless I don't even see BCM in lspci output. I guess the button doesn't activate the hardware - it only switches antenna power on/off.

I think that special HP software activates the hardware on button press. When booting up with wifi on - BIOS does the job.

Can someone verify this (I don't dualboot):
[LIST=1]
[*]Switch off wifi
[*]Uninstall HP software
[*]Reboot
[*]Can you enable wifi using the button?
[/LIST]

---

### Post by jukoz on 2008-03-18
For all those with only one system: Go to BIOS and do the Restore original settings. That will keep all your passwords and ID settings, but it will reset everything else.
With this reset, the BCM4328 should reappear in lspci. Now don't touch the wlan switch. To disable wlan click on the network icon with right-click and disable wireless there.

Hope this helps. Needed almost a week to figure this one out.

Ajt!

---

### Post by orkid on 2008-04-29
Is there any way to detect what event is generated when the wireless button is pressed ?

---

### Post by tobyadams on 2008-05-01
Same here, installed using wubi on my HP Compaq 6715b, and cant turn the wireless on, still not on even if it was left on after a reboot of vista. I just don't get it though, because my volume controls work perfectly?!?!?!?!

:confused:

---

### Post by bob scott on 2008-05-03
I have the same problem with the wireless switch not being on. The result is no wireless!

I have Ubuntu 8.04, HP dv6225,  dual boot with Vista.  My card is BCM94311MCG.   Ubuntu sees my network(it gives me the name of the network).  In the restricted drivers manager wireless is not enabled.  I am told to reboot. Rebooting does not enable wireless. The wireless switch light is not blue which indicates enabled. 

When I installed Ubuntu 8.04 I installed the  restricted drivers.

Thanks for any help.

---

### Post by bob scott on 2008-05-03
I just checked to see when wifi is enabled in windows.  It looks like after the bios turns the computer over to windows the wifi is enabled if the switch is on.  The wifi light goes from amber to blue.

---

