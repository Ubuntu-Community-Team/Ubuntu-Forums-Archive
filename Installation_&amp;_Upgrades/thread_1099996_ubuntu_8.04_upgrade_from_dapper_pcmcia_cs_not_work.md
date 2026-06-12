---
title: "ubuntu 8.04 upgrade from dapper pcmcia cs not working"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by petebarchetta on 2009-03-18
hello all
Recently upgraded my dapper lts on my tosh tecra 550cdt, all upgrade went well. Machine went thru reboot after install pcmcia cs still functioning, when turned off for a couple of hrs went back to laptop the pcmcia cs does not recognise. where there used to be three or four entries in the netwiorking folder there is now none, another issue that has recently sprung up which was sorted in Dapper was the USB  access, in Dapper an edit of the grub menu.lst adding "noapic" and "irqpoll" allowed the usb to be seen as a drive and enabled on desktop,, this has also no gone
i want to re install this in the current LTS version if possible any hints

---

### Post by petebarchetta on 2009-03-19
As you know Ubuntu Dapper 6.06 LTS was on the machine and running nicely, screen resolution issue has now been addressed and resolved, makes the small screen very usable. Recently I have decided on the route of upgrading the Dapper install to the Hardy 8.04 LTS, in the install it informs unsupported modules, PCMCIA-CS being one of them as it has now been integrated into the 2.6 kernel.

Doing 
sudo apt-get install pcmcia-cs
returns a answer that it is already at the newest version.
Then 
Lspci
Gives an answer for the cardbus bridges / Topic97 (where pcmcia cards are accessed of
00:02.0 & 00:02.1 respectively showing I do not need a resource database
Going through the link below
[http://kernel.org/pub/linux/utils/kernel/pcmcia/howto.html]("http://kernel.org/pub/linux/utils/kernel/pcmcia/howto.html")Then I get lost, 
Also I cannot acess the network settings as in Dapper that allowed me to see the cards / eth connections suggesting that the cards are not seen in hardy, whereas in dapper the airo prompt popped up in the scrolling lines when it booted up before the gnome manager kicks in.

I’ve downloaded the pcmcia utils and the latest CS files too

Doing a bit more research going through the /etc/pcmcia browses the network.opts and wireless.opts files shows my airo 340 entry, although unsure how to edit these (hence just browsing) its currently commented out

Then looking through the /sys/bus/pcmcia/devices area, I have been unplugging the devices and watching the ls command showing the 0.0 and 1.0 disappearing and re-appearing when pushed in and out. So shows devices are appearing / seen by machine

The usb also seems to be displaying the same characteristics, in that when plugging it in it displays bad volume etc. going into the  /sys/bus/usb/devices area shows

1-0:1.0 1-1  1-1:1.0 usb1

The second group is the usb device and the first is the hub onboard, again plugging and unplugging shows the device coming online, but the error is still displayed, in Dapper it jumped straight in, with no issues

Just a thought if this is kernel dependant, can Hardy run with a  Dapper kernel??? As these problems seem to have happened since the upgrade.

Also the only file that was kept current was the menu.lst, this surely should not have affected this? everything else was upgraded

Any ideas?

---

