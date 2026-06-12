---
title: "Dv8000 wifi switch"
date: 2011-07-25
forum: Hardware
---

### Post by sconnyuk on 2011-07-25
Hi, very new to Ubunutu forums and on top of that very new to Ubuntu. Straight to the point, ive searched all day trying to fix my issue but still cant seem to find out how to fix it. So ive had to give in and ask on here for help. Ive a HP DV8000, well actually the exact make of it is dv8263ea. I have just installed Ubuntu 11.04 on it and when it was installing i had my ethernet cable plugged in to let it download updates for me while it installed, as it did not pick my wifi up. Now after trawling lots of posts on various sites ive recognised my wifi card is an intel pro wireless 3945abg card installed, But im unsure if the correct driver is installed, on top of that the wifi light right in the top centre above my keyboard will not switch on when i press the button. If there is anyone who has had this issue before or knows how to fix it can help i will be very grateful, as i do not want to go back to a windows machine as i very much like ubuntu, ive got it installed on my desktop and runs very good. Thanks in advance.

---

### Post by grahammechanical on 2011-07-25
Hi and welcome to the forums.

If you are still connected by ethernet cable, do you see the network manager icon in the top panel? It is two arrows going in opposite directions. When you click on it do you see;

1) a list of wireless networks, including your own?

2) Is the line Enable Wireless ticked? If not tick it.

Or do you see a small menu with no tick mark against Enable Networking? If so, click on that line.

If you have Windows installed did you switch off wireless before you shut down Windows? This will turn the wireless adapter off and Ubuntu will find it very difficult to turn it back on.

Can you turn on wireless at the keyboard before you load Ubuntu. This is better than turning it on after you load Ubuntu.

The driver should already be installed but just to check, do you see an icon on the top panel telling you that additional drivers are available?

You can click on the icon to load the utility or go to System Settings>Additional Drivers and see if you are being offered a wireless driver. If so, activate it. You need to be connected by ethernet as the utility will download the driver from the Intel web site.

Regards.

---

### Post by sconnyuk on 2011-07-25
Thanks for the reply, and the welcome. Right, my network icon on the top panel is a lead in a hole icon, ethernet cable plugged in. when i click on it i see

wired network 'in a dull gray colour'
auto eth0
disconnect
wireless networks 'in a dull gray colour'
wireless is disabled by hardware switch 'in a dull gray colour'
vpn connections
enable networking, with a tick in the checkbox
enable wireless with no tick in the checkbox and is a dull gray colour
enable mobile broadband
connection information
edit connections
ive no windows installed on this laptop so cant say it switched on or off in windows. the wifi button does not come on when pressed before i load ubuntu up either. There was an icon that told me there was drivers available, but only for my video card.

im a competent windows user and can tell you this laptop was originally shipped with windows xp, when i got it, i installed windows 7, and did have the same issues as im having now, the wireless switch would not turn on, the driver was installed, and had no problems but just would not turn on. so had to revert back to xp.

---

### Post by sconnyuk on 2011-07-26
Well i stumbled upon the answer to my problem, another person in these forums was having issues slightly resembling mine, [http://ubuntuforums.org/showthread.php?t=1604665&highlight=HP+WIFI+BUTTON](http://ubuntuforums.org/showthread.php?t=1604665&highlight=HP+WIFI+BUTTON) with a HP laptop and i applied the said fixes to my problem and alls fine. Thanks for the help.
The actual fix was (temp)

rfkill list all
sudo rmmod -f hp_wmi
rfkill list all

and permanent was 

Please do:
Code:
sudo su
echo "blacklist hp_wmi" >> /etc/modprobe.d/blacklist.conf
gedit /etc/rc.local
Add a new line right above the line 'Exit 0':
Code:
rfkill unblock all
Now reboot and do not press the button. Is the LED orange or blue? When you click the Network Manager icon, do you see networks? What is the result of:
Code:
sudo iwlist scan

---

