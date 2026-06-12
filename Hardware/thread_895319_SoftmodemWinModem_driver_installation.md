---
title: "Softmodem/WinModem driver installation"
date: 2008-08-20
forum: Hardware
---

### Post by Psychoscorpic on 2008-08-20
Hi all.

I have been trying for a week now to get my laptop to be able to dial out via the embedded Softmodem/WinModem (Agere 11c11040 chip).

I can get it to dial after going through the laborious driver  installation procedure, but all is lost at rebooting.
How can I make the drivers load at boot?

Steps to Install:
1) Use **scanModem** to identify the chipset: [http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz)
2) Got the pre-compiled Ubuntu driver for my chipset. 
agrsm-ubuntu8.04.1-2.6.24-19-generic.tar.gz
3) Run the setup inside (2)and reboot (as per instructions in the terminal after running ./setup)
4) Load the drivers:
[I]sudo modprobe agrmodem
sudo modprobe agrserial[/I]
(This creates /dev/ttyAGS3 but doesn't let you know)
5) Make symbolic links to the driver that wvdial or PPP can follow:
[I]sudo ln -s /dev/ttyAGS3 /dev/ttySAGR
sudo ln -s /dev/ttyAGS3 /dev/modem[/I]
6)Test driver with:
*sudo wvdialconf /etc/wvdial.conf*
7)All works, so dial with PPP.

So far so good - no audible feedback, but after a few seconds, I can get my mail.

NOW: How do I make these settings stick?!!! :confused:
- Have to do all the above each time after a reboot!! (Tried just the last few steps, but it doesn't work)

This is a core function, for crying out loud! One should be able to simply boot up & dial out. ](*,)

EDIT:

In /etc/modules.

Add the following two lines (init.d boot script will run them with modprobe at boot time):
agrmodem
agrserial

Reboot.

Check: /dev/ttyAGR3 exists!

WvDial . . . Yes! (after editing to point to ttyAGR3 instead of ttySAGR) it dials & connects! Whohoo!

Awesome stuff.

*Thanks so much to Bjorn Wielens who helped me from LinModems.*

---

### Post by Psychoscorpic on 2008-08-22
Rats!
The euphoria is over - that "fix" made my system unstable - had to boot with a LiveCD and "#" out the driver loading lines in "modules" in order to boot.

I was just thinking, though:
Would there not be a way to do this with modprobe.d ?
I had to add a line there for my sound to work, and I just remembered seeing the following lines there too:

```
#Prevent abnormal drivers from grabbing index 0
options snd-atiixp-modem index=-2
options snd-via82xx-modem index=-2
```

There are also a pile of install...modprobe... commands.

1) My notebook has an ATI sound chip. What does the ATI line above mean? Would another value there allow it to be visible?
2) Can we not use an "install ... modprobe" command here to install & load the drivers?

---

