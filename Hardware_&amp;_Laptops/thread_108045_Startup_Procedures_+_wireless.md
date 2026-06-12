---
title: "Startup Procedures + wireless"
date: 2005-12-24
forum: Hardware &amp; Laptops
---

### Post by wwbdd on 2005-12-24
I am having some difficulty getting my wireless to work.  I installed the ndiswrapper drivers like the wiki said and it actually worked for a brief moment but when I tried to set it to my own network (encrypted) as opposed to my neighbors network (unencrypted) things just kinda died.  I tried switching things back to the way they were, I tried reinstalling the drivers, i tried rebooting... nothing.  This is very frustrating because it did work, but no longer.  The other thing that is bothersome is how it takes forever to boot.  It gets hung up on the networking step (whatever it is called i dont know, but it seems to have trouble because it doesn't have a network to connect to).  I plan to use this laptop in places outside of my house so I dont want to have to wait 10 minutes while the laptop searches for a network that may be several miles away.  Is there any way to make this step a little quicker???  Any help on either of these two problems would be greatly appreciated.

---

### Post by Gooks on 2005-12-24
Can you help me setup my wireless?

---

### Post by wwbdd on 2005-12-24
I would if i could but I'm afriad i can't.  I got mine to work only for a little while and then it died and it hasn't worked since then.  The best advice I can give is to go to the wiki page 

[https://wiki.ubuntu.com/WiFiHowto?highlight=%28wifihowto%29](https://wiki.ubuntu.com/WiFiHowto?highlight=%28wifihowto%29)

and then take the ndiswrapper link and do that too.  It worked well for me for about 10 minutes before i tried to change networks then it hasn't worked since.

---

### Post by Gooks on 2005-12-24
I need help with Driver

---

### Post by wwbdd on 2005-12-25
I just followed the steps from the wiki which I have copied below:

1. Important: Do NOT use the drivers on your bundled wifi card CD. They may work, but you may experience serious problems. Instead, you need to download appropriate Windows XP driver for your card from the ndiswrapper wiki's list. To identify the driver that you need, first identify the card you have with 'lspci' and note the first column such as 0000:00:0c.0 and then find out the PCI ID of the card that with 'lspci -n' corresponding to the first column of 'lspci' output. The PCI ID is third column or fourth in some distributions and of the form '104c:8400'. Now you need to get the Windows driver for this chipset. In the ndiswrapper wiki [WWW] list, find out an entry for the same PCI ID and download the driver corresponding to it. Do not worry if the driver link does not have the exact name of your wifi card as many cards have the same chipsets. Decompress the Windows driver with an unzip tool and find both the INF file (.INF or .inf extension) and the SYS file (.SYS or .sys extension). (this is important as some drivers have a connection with the .sys file which makes the driver work properly) If there are multiple INF/SYS files, try looking at the [WWW] list to see if there are any hints about which should be used. Make sure the INF file, SYS file and any BIN files (TI drivers use BIN files) are all in one directory on your harddrive.

2. Install the Windows driver with the following command. Remember, substitute your driver filename for mine. In the example given below, my driver filename is bcmw15.inf yours may be different depending on your wireless hardware, but it will always end with the .inf file extension. For some cards, it may be necessary to have both the .inf and the .sys files in the same location before using the following command.

ndiswrapper -i ~/windows_drivers/bcmwl5.inf

3. Now we create and alias for wlan0 into module configuration file so that this module is used whenever the wireless interface is started.

ndiswrapper -m

4. Lastly, before you configure your wireless connection, load your new module in the running kernel.

modprobe ndiswrapper

5. You should be able to check whether the driver was loaded successfully now and whether the hardware has been detected or not.

ndiswrapper -l
  Installed ndis drivers:
  bcmwl5 driver present, hardware present

6. You also need to add the ndiswrapper module to the startup modules so Ubuntu can setup the device when your machine starts. You need to add ndiswrapper to the end of the /etc/modules file. You can do this by:

sudo gedit /etc/modules

Add ndiswrapper to the end of this, save and close. When your machine reboots, it will find the Wireless Adaptor and start it up. 

That's what i did and it worked for me up until the point where i tried to connect to my own network as opposed to my nieghbors unencrypted network.

---

