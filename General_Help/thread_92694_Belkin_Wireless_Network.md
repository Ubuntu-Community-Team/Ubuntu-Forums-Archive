---
title: "Belkin Wireless Network"
date: 2005-11-20
forum: General Help
---

### Post by byronsterk on 2005-11-20
help me!!!!

i have a belkin 54g PCI wireless network card, and i want to make it work in Ubuntu, in my house we have a windows network with 4 computers (including mine, all Dell Dimension 2400) and i have looked everywhere in these forums, all with technical information on how to install ndiswrapper etc, but that's all too difficult for me really... example, it tells me to 

'Download the latest version of the ndiswrapper sources from here and extract it with 

tar zxvf ndiswrapper-version.tar.gz '

were do i enter that command? i have no idea how these things work...:( 
 
i like the way ubuntu works, it's an easy operating system, but i just can't set up these difficult things...

can anyone help me?

thank you, byron.

---

### Post by gypsy_roadhog on 2005-11-20
Don't panic - ndiswrapper should work fine.  You must to make sure that ndiswrapper is installed and running and you can then configure your Belkin card.

!) Ndiswrapper
You shouldn't need to use the "tar" comand as I'm sure that there is already an Ubuntu version. With luck it is already installed but if not it may be on your distribution CD. If so you can install it with the Synaptic package manager - look in the system menu. 

Synaptic allows you to search for the name ndiswrapper and should either show it as installed or available) If it is available then install it!

(If the package is not on your CD you will have to download it from the Internet using one of your existing PCs).

2) Running ndiswrapper
Once you think the ndiswrapper is installed you can try to run it. You do this from the command prompt using a terminal application(if you can't find this in the menus or use the run command option and select a command such as xterm).

At the command prompt type "ndiswrapper -l" ...... if ndiswrapper is there is should display a list of any installed drivers.


ndiswrapper -h should display a list of available command options!

You then need to tell ndiswrapper the hardware and driver it should use. Assuming that you have the driver software (probably a .sys file and a .inf file) you can type "ndisrappwer -i INFfile" where INF file is the name of the inf file. This will install the driver and hardware.

If ndiswrapper -l then shows both driver an hardware present then you are nearly there. "modprobe ndiswrapper" should load the drivers ready for configuration by the standard network tools.

ndiswrapper -m will save the correct modprobe settings

Your problem is that ndiswrapper may not work with the driver supplied by Belkin. looking at [http://www.linux-wlan.org](http://www.linux-wlan.org) I think you may need to use a broadcom driver for a Belkin 802.11g pci card.

If the existing Belkin driver doesn't work you can try to find an alternative broadcom or atmel driver.  (I can't be more specific - I use an earlier version Belkin card but have to use a Realtek driver!)

Since Ubuntu has probably recognised you card as a Belkin card it won't want to use a broadcom driver . Fortunately ndiswrapper has a command option to allow you to sepcify the hardware to use. To do this you need to know the pci device id which can be found easily using the lspci command. (the dev id will be in the form xxxx:xxxx).

IF none of this works there is a fairly reliable commercial alternative from linuxant.com. I think the cost is about $20. If your Belkin drivers don't work with ndiswrapper  AND you can't locate an alternative driver then linuxant is a very attractive alternative.

I hope this helps. If you can find a working driver then ndiswrapper will work very well ... if not well there is always linuxant.

Neil

---

### Post by patrickfromspain on 2005-11-20
You must install an app called ndiswrapper. It allows to use windows drivers for wlan cards in linux. just go to synaptic and search for ndiswrapper. Ndiswrapper utils or tools should come out. Install it. The copy your windows drivers into some location.

Now, from the terminal (Applications -> Accessories -> Terminal) do:

sudo ndiswrapper -i 7path/to/drivers/drivernamehere.inf
sudo ndiswrapper -l (L, not 1) to see if it's properly installed. It should say something like driver present, hardware present.
sudo ndiswrapper -m
sudo modprobe ndiswrapper (to load the driver)

Now, go to system -> administration -> network and configure the wireless card properly. You should also disable your ethernet card so that they don't try to connect at the same time. Also don't forget about the DNS.

Hope this helps. If not, ask.

---

### Post by byronsterk on 2005-11-20
i have installed ndiswrapper with synaptic, i think it is installed sucessfully, when i run it in the prompt window (or whatever it's called) i get this:

byron@byron:~$ ndiswrapper -i bcmwl5.inf
Installing bcmwl5
Unable to create directory /etc/ndiswrapper/bcmwl5. Make sure you are running as root
byron@byron:~$

(by the way, byron is my name and the computer name)

I have the driver located on the desktop.

---

### Post by gypsy_roadhog on 2005-11-20
Yes, one of the "strengths" of linux is its security. The system is "owned" by a super-user called "root". It is possible (in theory at least) for an inattentive root user to delete the entire filesystem by typing something as simple as "rm *".

In order to protect you from this the normal Ubuntu user does not have root privileges ...... but you need them for ndiswrapper. (I forgot this in my last message).

The simplest way is to prefix your ndiswrapper commands with "sudo" (as suggested by someone else who responded to your question).

Alternatively, in the Hoary Hedgehog release, there was a menu option to open a "root" terminal where you have full admin privileges. I'm not sure if this is still available under Breezy Badger!

Neil

---

### Post by ecobuntu on 2005-11-20
[QUOTE=byronsterk]i have installed ndiswrapper with synaptic, i think it is installed sucessfully, when i run it in the prompt window (or whatever it's called) i get this:

byron@byron:~$ ndiswrapper -i bcmwl5.inf
Installing bcmwl5
Unable to create directory /etc/ndiswrapper/bcmwl5. Make sure you are running as root
byron@byron:~$

(by the way, byron is my name and the computer name)

I have the driver located on the desktop.[/QUOTE]

Try your same command but with sudo in front of it....i.e.
sudo ndiswrapper -i bcmwl5.inf

---

### Post by byronsterk on 2005-11-20
i've tried your instructions, and this is what i get when i enter -l   =

byron@byron:~$ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5  invalid driver!
byron@byron:~$

the driver i used, i copied that straight from the install CD that came with the card.

---

### Post by gypsy_roadhog on 2005-11-20
I'm not sure what is happening but it would be sensible to remove the invalidly installed driver (I think the command will be something like sudo ndiswrapper -e bcmwl5)

then do  sudo ndiswrapper -l  to check that no drivers are installed.

Then try reinstalling again. 

Also I found something relevant on another site:-

    Where is your file called bcmwl5.inf?
    In this case it should be in the same directory that 
    you are in when you run the command. 
    If it's somewhere else, you'll need to say so. 
    If the file was in, say /home/me/broadcom, you'd need to type:
    ndiswrapper -i /home/me/broadcom/bcmwl5.inf
    This is called defining the 'absolute path'.

If the file is in your desktop folder it will be something like /home/byron/Desktop/bcmwi5.inf


Neil

---

### Post by byronsterk on 2005-11-20
yes i used absolute path, the driver is located in a folder called driver on the desktop, the path is /home/desktop/Driver/here the driver or something like that

---

### Post by byronsterk on 2005-11-20
i just tried something, here is the result:

byron@byron:~$ sudo ndiswrapper -i 7home/byron/bcmwl5.inf
bcmwl5 is already installed. Use -e to remove it
byron@byron:~$ sudo ndiswrapper -e 7home/byron/bcmwl5.inf
Driver 7home/byron/bcmwl5.inf is not installed. Use -l to list installed driversbyron@byron:~$ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5  invalid driver!
byron@byron:~$ sudo ndiswrapper -m
modprobe config already contains alias directive

byron@byron:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted
byron@byron:~$

maybe it can be of help.

---

### Post by gypsy_roadhog on 2005-11-20
Byron

I think that you may need to tell ndiswrapper to use the belkin card with this (broadcom driver).

type lspci and you should get an installed pci devices. Note down the device id for the belkin card    - it will be in the format xxxx:xxxx

you then need to do a sudo ndiswrapper to link this device id to the broadcom driver. I'm not at a Linux PC at the moment so can't check on the exact parameter but I think it is sudo ndiswrapper -u....... but you can check this from the ndiswrapper help message or by typing man ndiswrapper.

Neil

---

### Post by byronsterk on 2005-11-21
anyone have something yet?

---

### Post by patrickfromspain on 2005-11-21
Ok.. you're doing wrong when uninstalling the driver. ;) 

Go to terminanl and put:

sudo ndiswrapper -e bcmwl5
sudo ndiswrapper -l to check that there are no drivers. If there still is a driver do  the same.. if the driver name is driver then sudo ndiswrapper -e driver, no driver.inf. And don't put the path, just -e driver.

Ok, when no drivers are installed:

sudo ndiswrapper -i /home/byron/bcmwl5.inf
sudo ndiswrapper -l
and, finally, sudo modprobe ndiswrapper.

If everything has gone fine, you can now go into system -> administration -> network and there you'll have your wlan0.

hope it helps.

---

### Post by ygarl on 2005-11-21
I have *precisely* the same probs. Ndiswrapper says the driver is invalid. I _know_ the driver is the right one, but fortunately I also have a NIC inside both PCs. I just haven't had time to wrestle this one out yet.
We'll keep at this together, eh Byron?
I'll check the ndiswrapper -u option when I get home from work...

---

### Post by patrickfromspain on 2005-11-21
if you look here:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B)

there are some belkin cards listed.. maybe it helps you.

---

### Post by patrickfromspain on 2005-11-21
from the same site:

Card: Belkin 54g Wireless Desktop Network Card (F5D7000) Rev 03

    * Chipset: BCM4306
    * pciid: 14e4:4320
    * Driver: [http://ftp.us.dell.com/network/R81433.EXE](http://ftp.us.dell.com/network/R81433.EXE) (use bcmwl5a.inf in directory AR)
    * Other: I tried to use the belkin driver (bcmwl5.inf) but the whole system just locked up as soon as I modprobed ndiswrapper. Apparently the belkin driver works for the older rev 02 cards, but not rev 03. So I'm suggesting this for folks with the Rev 03 card. You can check the revision by doing a "lspci" The Dell driver has been working great for me, for about a day.
    * Other: The rev.03 problem is probably not all that sinister. It is caused by the presence of the NetworkType|0 line which ends up in the*.conf files (from the *.inf driver file). Removing this allows the supplied Belkin driver to work, although I'd probably recommend using the Dell R81433.exe driver anyway if only because it's a later version. For non-US users you may wish to edit the Channel parameter to be 13 (Europe) (or 14 in Japan?). Applies to both PCMCIA and PCI versions (F5D7000 and F5D7010). #*Other: Using a PCI 2.1 motherboard, I first had trouble getting the card to associate with a base station, although everything loaded without errors. This was fixed by moving the card to the first PCI slot.#*Otherwise, I've had complete success with a Rev 03 card using the supplied Belkin drivers, without modifying the NetworkType|0 setting. Also, I had some trouble getting the Gentoo Init scripts to properly initialize the card. The trouble there is several fold, though one problem appears to be that the init scripts don't give the card enough time to initialize. N.B.: I had to enter the WEP key first before the card would associate with any station. I'm using kernel 2.4.26 with gentoo patches, ndiswrapper-0.11.

---

### Post by byronsterk on 2005-11-21
Sorry for the late reply, i don't have much time now i have a lot of 'business' to take care of with the dutch airline transavia... i hope i can try out your suggestions if i have time tomorrow

---

### Post by gypsy_roadhog on 2005-11-22
Byron

It sounds like you should be getting close now but you may also be interested to see this article from Tuxmagazine on configuring ndiswrapper - the url is:_

[http://www.tuxmagazine.com/node/1000167](http://www.tuxmagazine.com/node/1000167)

Neil

---

### Post by faikwo on 2005-11-22
Check this out also

[http://www.ubuntuforums.org/showthread.php?t=31926](http://www.ubuntuforums.org/showthread.php?t=31926)

---

