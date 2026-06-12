---
title: "PCMCIA not working on fresh xubuntu install"
date: 2006-08-26
forum: Hardware &amp; Laptops
---

### Post by Theo Hopman on 2006-08-26
Hi all. I just installed xubuntu (6.06) on my old NEC Versa SX (P2-233/192M/6G) laptop. I'd like to use a Xircom CreditCard Ethernet/Modem PCMCIA card to connect to my network, but unfortunately the card is not detected. It works fine under Win2K, and worked with the old Mandrake installation I used to have.

I've poked around, but I can't seem to find any HOWTOs or the like which address this.

Some symptoms:
- the startup messages say PCMCIA services have started OK.
- the two CardBus bridges are detected by lshw, with the configuration line saying driver=yenta_cardbus. If necessary I can retype the complete output of lshw.
- lsmod shows that the pcmcia_core, pcmcia, yenta_socket and rsrc_nonstatic modules are loaded.
- /etc/pcmcia/ is empty. I don't think this should be the case, but I don't know what should be here.
- when I insert the card, there's no beep to indicate that the card is recognized.

Any help is greatly appreciated!

THeo

---

### Post by dannyboy79 on 2006-08-26
type in "dmesg" in a termianl and go through the list and look to see if your pcmcia is being detected. If it is than you know it's a driver issue. If it's not detecting it than you know it's that the pcmcia services aren't working. I can tell you that I have a pcmcia card working as my wireless adapter. It's a netgear wireless card. I am a linux newbie so I wish I could hekp you more but as I am trying to get my external usb cd-writer to work people have suggested that I type in dmesg. Good luck

---

### Post by TSK on 2006-10-08
I have the same experience: my Intel ethernet PCMCIA card is not detected after a fresh Xubuntu 6.06.1 installation. Interesting thing is that the same card on the same machine worked without any problems at all with Ubuntu 6.06. In Xubuntu, the card would not even appear in the Networking (network-admin) tool. I tested with another card (D-Link Wireless DWL-G650+) which did appear in Networking, and I was allowed to do IP-settings etc. However, the diods on the card never indicated it was working, and I never got internet access. I was not able to ping the local IP-number of my router.

After reading that others had noticed that PCMCIA worked fine before installing Xubuntu, while still running from the Desktop CD, I tested that. Sure enough, Xubuntu run from CD detects the network card (Intel ethernet card) and allows me to configure it in the Networking (network-admin) GUI. I get internet access.

When in CD-mode, Synaptic Package Manager reports that both PCMCIAUTILS version 012-1ubuntu4 and PCMCIA-CS version 3.2.8-5.2ubuntu7 are installed (in the sense that they are "available" packages on the CD - nothing at all is really installed at this point).  

In case you didn't know, PCMCIA-CS is a tool/component that has been replaced by PCMCIAUTILS. PCMCIA-CS will be phased out and is said not to be required as long as PCMCIAUTILS is in place. I just learnt that myself in the past few hours trying to solve this problem.

I suspected that PCMCIA-CS is skipped at Xubuntu install, but is required for my kind of ethernet PCMCIA card. I monitored the installation process carefully, and when the process was at 95%, I noticed this message in the progress bar window: "Completely removed pcmcia-cs" in a row of several messages of completely removed stuff.

When the installation was finished, I verified that my network card was not available in Networking and that PCMCIAUTILS was installed, while PCMCIA-CS was not installed. Since I had no network connection (i.e. the actual problem) I could not get the PCMCIA-CS package from the web. The solution to that is to do Edit > Add CD-ROM and insert the Desktop CD (installation CD). Thereby, all the installation packages on the CD becomes available to Synaptic. 

After that, I marked PCMCIA-CS for installation and clicked Apply. I got a message saying that installing PCMCIA-CS would result in 30 other packages being held back and not updated. I was prepared to take that, and clicked OK. Guess what? I get an error message saying that there was a problem connecting to the internet to download the package.

So, Synaptic was unable to extract the PCMCIA-CS package from the installation CD, inspite of the CD being added as a package repository.

Using a tip I found in another forums posting, I re-opened Synaptic and marked PCMCIA-CS for installation, but this time did not press Apply. Instead, I selected File > Create Package Installation Script. That gave me a shell script file that could open with Mousepad in order to see the URL of the package. I saved that as a textfile on a USB-stick and moved that to my other computer (yes, lucky me I had another one). I put that URL in the address bar of a browser window, and was prompted to save a file called "pcmcia-cs_3.2.8-5.2ubuntu7_i386.deb" (Debian kernel package for Ubuntu with PCMCIA-CS). Then, I moved the USB-stick back to the Xubuntu computer, and copied the .deb-package to the desktop. Following the advice on manual package installation that I found here:
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)
I double-clicked the deb-file, and got a window up where I could press "Install". I was warned of a few things before the installation finally took off.

Following that, I verified with Synaptic that PCMCIA-CS had been installed. I rebooted the machine. And there it was, my PCMCIA ethernet card available for configuration in Networking. With a surprise. It was already configured exactly like I had done previously while still in the Desktop-CD mode, before harddrive installation. I find that quite mysterious.

Problems with PCMCIA on Ubuntu (or Linux generally?) seems to be quite common, and of many different kinds.

---

