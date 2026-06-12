---
title: "Fool Proof Setup of Dell 6400/1505E Wireless Connetivity"
date: 2007-09-30
forum: Hardware &amp; Laptops
---

### Post by cameronjcc on 2007-09-30
First of All; WPA or WEP or Open Network, none of this should matter when your network is configured correctly.  It took me a little work to get it right, but here is what I did.  Now my network works great, no harder than working in windows.

1) Blacklist bcm43xx driver
Open a Terminal window
Type "sudo gedit /etc/modprobe.d/blacklist"
At the bottom add the lines

# get rid of the default kernel drivers
blacklist bcm43xx

2) Make sure network interfaces file is correct
Type "sudo gedit /etc/network/interfaces"

Remove all comments ('#') that you see so that all devices arehandled by the default network manager.

I would reboot here and make sure the wireless light goes out

3) Install ndiswrapper

Put in Ubuntu CD. Open Synaptic Package Manager (ClickSystem -> Administration -> Synaptic Package Manager),search for ndiswrapper-utils, and install it.

You could also type "sudo apt-get install ndiswrapper-utils 
(IF you are not using ubuntu then make sure you have ndiswrapper-utils somhow installed)

4) Conigure ndiswrapper
Open terminal and navigate the folder where your drivers are."cd Desktop/bcm43xx"

Type "sudo ndiswrapper -i oem3.inf"Then type "sudo ndiswrapper -m"
Type "sudo gedit /etc/modprobe.d/ndiswrapper"

Change the one line in that file to read "alias eth1 ndiswrapper"

Now you should reboot so all the drivers load.

Once you reboot the wireless light on your laptop should be lit. 

If it worked, you should be able to click the Network Manager icon in the top right. 

It will probably show a disconnected connection because the computer is not plugged in.

Left click it and select eth1 from the drop down menu.

Click Configure

Click Wireless Connection, then Properties. 
Here just enter your network information. 
If you're using an unprotected network you should only have to type yout SSID.

Click OK and you should now be connected! 

If a green signal meter and connected network icon appear in the upper right you'll know it worked.

---

