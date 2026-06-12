---
title: "Touchpad on Toshiba Satellite"
date: 2009-01-01
forum: Hardware
---

### Post by bbrennan on 2009-01-01
Hey everyone, I just made the switch from Vista to Ubuntu 8.10, I have a Toshiba Satellite A200-AH5. I'm having trouble setting up my touchpad. I've looked at many tutorials but i still am unable to set it up. From the looks of it, my xorg.conf is missing some stuff. These are the only sections after a new install of ubuntu.

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

My keyboard and mouse both work fine, one of the tutorials i saw showed how to make sure te touchpad is recognized, it was, but i cant get it to work under the mouse or touchpad options in Preferences.

Any help would be greatly appreciated.
Thanks, Bill

---

### Post by dk21 on 2009-01-04
Same problem at toshiba a200-21t...

I tried to add sections manually and I currupted the file... X server didn't worked...

Now, its solved, but I really would like to configure my trackpad...

---

### Post by gmoctav on 2009-08-20
> **dk21 said:**
> Same problem at toshiba a200-21t...

I tried to add sections manually and I currupted the file... X server didn't worked...

Now, its solved, but I really would like to configure my trackpad...

could you tell me how did you solve it ?

---

### Post by dk21 on 2009-08-21
I said Solved about xserver, not about trackpad... Sorry...

I'm not using Ubuntu anymore. Requires lots of time to learn, and for now, I don't have that time... Maybe later.

Version 9.04 doesn't solve your problem?

Best regards

---

### Post by dk21 on 2009-09-17
Hi.

Just moved AGAIN to ubuntu and finaly found it...

Check [https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig) to enable SHMConfig... Gsynaptics will work after it...

---

### Post by brunolopes446 on 2009-12-22
I had the same problem with my synaptic touchpad after upgrading my ubuntu from 9.04 to 9.10. This is how I solved the problem:
Open a terminal
type "sudo su"
then type you password
after that, type this: sudo echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
and them, type: reboot
after rebooting your synaptic touchpad will work

Best wishes

---

