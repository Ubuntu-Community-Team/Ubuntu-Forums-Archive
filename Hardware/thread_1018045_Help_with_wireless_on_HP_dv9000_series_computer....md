---
title: "Help with wireless on HP dv9000 series computer..."
date: 2008-12-21
forum: Hardware
---

### Post by knightrider37876 on 2008-12-21
I'm having a difficult time with the new Ubuntu. I used the LIVE cd option and booted into the OS. When everything loaded the Wireless configuration was grayed out. Should the wireless not work right off the bat? Any help would be appreciated!

---

### Post by 2hot6ft2 on 2008-12-21
What wifi card does it have there are a good 20 versions of that model?

If it has the AR5009 pci-e card it will work with kernel 2.6.27-7 and ath9k which is installed by default (at least it is in Ultimate Edition) I couldn't tell you in straight 8.10 since I don't run it.

The live cd doesn't have all the updates like kernels and the other stuff which takes care of some issues.

So without knowing the wifi card who knows what it can or can't do.

---

### Post by rbringh on 2008-12-21
It will if you go wired versus wireless. Actually you probably need to go wired to do the research and downloads needed. The wireless mode will take a lot of effort to get going if it has the Atheros card like my DV9000. I would recommend you search the group for Atheros. Some will recommend you load a Windows driver, I do not recommend this. I went that route and it is very unreliable. Stay with the Linux Drivers.

This will get you started. Mine works so I know you can get yours going.

Good Luck.

---

### Post by knightrider37876 on 2008-12-21
Hi Guys,

Thanks for responding. I pulled up the system info via the "lspci" command. The wireless card that was listed is:

Broadcom Corporation BCM4311 802.11 b/g WLAN (rev 02).

---

### Post by metra on 2008-12-21
rbringh: I also have an Atheros wireless card. While I will be looking around for those drivers it would be helpful, if you remember, to know which driver you used to have yours work.

---

### Post by knightrider37876 on 2008-12-22
anyone have any other suggestions?

---

### Post by rbringh on 2008-12-23
I also have an Acer Aspire with a Broadcom card. It was easy to get working compared to the Atheros. I used a wired connection to get the Broadcom drivers. Go to System, Select "Hardware Drivers" It will search for drivers. Mine came up with a Broadcom. Select and enable it.

Remove the wired connection.

Next I right clicked on the network icon, i chose to disable wireless. Then go right back and enable it. The wireless card should turn on at that point. Use the Netork options to setup your wireless card to match the router settings.

Try it. It worked everytime using LiveCD with the Broadcom.

---

### Post by knightrider37876 on 2008-12-23
> **rbringh said:**
> I also have an Acer Aspire with a Broadcom card. It was easy to get working compared to the Atheros. I used a wired connection to get the Broadcom drivers. Go to System, Select "Hardware Drivers" It will search for drivers. Mine came up with a Broadcom. Select and enable it.

Remove the wired connection.

Next I right clicked on the network icon, i chose to disable wireless. Then go right back and enable it. The wireless card should turn on at that point. Use the Netork options to setup your wireless card to match the router settings.

Try it. It worked everytime using LiveCD with the Broadcom.

Cool! Thanks for the tip. I'm glad to hear that this process is possible without having to reboot out of the LIVE session. I will definitely give this a try. I'll post back on the results.

---

### Post by rbringh on 2008-12-23
> **metra said:**
> rbringh: I also have an Atheros wireless card. While I will be looking around for those drivers it would be helpful, if you remember, to know which driver you used to have yours work.

This is what I used. I do not know the post number so I have copied it to this reply. Sorry about that..

 Re: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01
Thanks so much to those above for figuring this out for me. Let me spell out the installation in a little more detail to save those after me some time.

I did this on a fresh Ubuntu 8.04 install on a Compaq Presario C770US Laptop with an ethernet cable plugged into my router.

The device string displayed by lspci -v was as follows:

Code:

01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 137a
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 91300000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

First under System/Administration/HarwareDrivers disable both the Atheros HAL and the Atheros wireless thing and then reboot.

The kernel headers and the compiler are needed to build this driver so I started by installing build-essential. In a terminal window (Applications/Accessories/Terminal) enter:

Code:

sudo apt-get install build-essential

The driver code will be downloaded with the subversion source code manager so I installed subversion:

Code:

sudo apt-get install subversion

I needed a place to put the driver source without mixing it up with other stuff so I changed directory to my home directory:

Code:

cd ~

Created a directory:

Code:

mkdir madwifi

And changed to the new dirctory:

Code:

cd madwifi

Use subversion to download (checkout) a copy of the code:

Code:

svn co [https://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6](https://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6)

The above command failed for me at first because subversion couldn't find svn.madwifi.org
Madwifi will probably have their DNS problems worked out by the time you read this. But if not then see the section at the bottom of this post titled "Cant find svn.madwifi.org" for a solution before continuing.

After the driver code is downloaded by subversion, change to the directory, which should be madwifi-hal-0.10.5.6

Code:

cd madwifi-hal-0.10.5.6

Run the make script to have the compiler build the driver:

Code:

make

Install the driver

Code:

sudo make install

Add the Atheros kernel module to the list of modules to be automatically loaded at boot by adding "ath_pci" (without the quotes) to the end of the /etc/modules file. I used the vi editor which I won't describe here. Gedit is probably easy to use so try:

Code:

sudo gedit /etc/modules

Now you can reboot and it should work. To get it working without a reboot you need to load the module manually:

Code:

sudo modprobe ath_pci

That should do it. The little wireless button seems to always stay lit orange. When I press it it seems to disable the wireless but it still stays lit orange. WPA works for me. I assume WEP will also. I haven't tried WPA2



CANT FIND svn.madwifi.org

If subversion has a hard time finding svn.madwifi.org then add it's IP address to your hosts file. I found this page [http://madwifi.org/ticket/1982](http://madwifi.org/ticket/1982) at madwifi.org that gives the IP address 217.24.1.142 of svn.madwifi.org in one of the last messages. I tried just giving subversion the command to connect to the IP address instead of the domain name, but it failed before finishing the checkout. Edit the file /etc/hosts and add "217.24.1.142 svn.madwifi.org" (without the quotes). I added it just after the 127.0.1.1 line

Code:

sudo gedit /etc/hosts

Now you can continue with the subversion checkout. You should probably remove this line from your hosts file when you're done with this so that if you want to go back there some day and they've moved it then DNS will give the most recent IP address.
Last edited by reasoner; September 2nd, 2008 at 06:20 AM.. Reason: Minor clarifications
reasoner is offline Report Post   	Reply With Quote Multi-Quote This Message Quick reply to this message

---

### Post by metra on 2008-12-25
Thanks! The last set of instructions worked, finally!

---

