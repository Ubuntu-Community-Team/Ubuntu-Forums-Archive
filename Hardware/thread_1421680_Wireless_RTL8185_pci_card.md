---
title: "Wireless RTL8185 pci card"
date: 2010-03-04
forum: Hardware
---

### Post by markmaus on 2010-03-04
I have installed Ubuntu 9.10 on a desktop machine with a wireless network card (pci type) that has the chipset rtl8185.
I connect to an open network with no security enabled.  Originally the card would connect automatically.  Now it just keeps trying to connect for a couple of minutes and then reports that the wireless network is not connected.  
I have discovered that if I type the following in a terminal, that the card will connect.

sudo rmmod rtl8180

sudo modprobe rtl8180

This is good that it works, and I'm not complaining, but it's a little too laborious.  (This machine will be given to my sister who won't comprehend any of this.)  So I've added rtl8180 to the /etc/modprobe.d/blacklist.conf file, which seems to prevent that module from loading at boot time.  Now I just have to type "sudo modprobe rtl8180" into a terminal to get it to connect.  But I want to automate it further by adding a script to load the module after it boots.  

I've added the line "modprobe rtl8180" in the file /etc/init.d/rc.local
and it does load the driver, but it seems to load it too soon and I get the original behavior of trying to connect and then failing.

Any suggestions? Is there some kind of delayed rc.local file that I can load this module from?  Any help is appreciated.

---

### Post by markmaus on 2010-03-06
I've gotten the wireless card to connect reliably by doing the following:

Add the following lines to /etc/modprobe.d/blacklist.conf

blacklist mac80211

blacklist rtl8180

blacklist cfg80211

I have created a desktop icon (named Activate Wireless) that runs the following command:

sudo modprobe rtl8180

Once the computer has booted up, the user just has to double click on the Activate Wireless icon and enter the password.  The network manager will then connect automatically to the wireless network.  It works everytime and is a little more user friendly than having the user type commands in a console.  

I'm surprised that no one has come up with a way to get the rtl8185 chipset to work in a more normal fashion.  Still hoping for a response to solve this issue.

---

### Post by markmaus on 2010-03-13
The method that I was using to connect with the RTL8185 wifi card (above) turned out to be unreliable.  It was hit and miss at best when loading the rtl8180 driver.  So I finally caved and installed the Win98 driver using ndiswrapper.  It works great now. It even reports the signal strength correctly. I would have preferred not to have to use a windows driver, especially when the linux 8180 driver is so close to working, but without additional help that's what I'm stuck with.  Let's hope the next kernel update doesn't nuke the ndiswrapper.  I kind of feel like I've been talking to myself in this thread.  Since I received no replies.  But maybe someone will find this info useful.

---

### Post by markmaus on 2010-03-20
Ok, I've uncovered another piece of this puzzle.  I still haven't given up on the rtl8180 driver.  I've disabled ndiswrapper and enabled rtl8180.  I've found that if I go into System/Preferences/Network Connection and click on the Wireless tab and edit my connection so that the connection is "Available to all users", everything seems to work fine.  I can now use the Network Manager to connect and disconnect to and from different wireless networks.  (The signal strength indicator is still incorrect though.) It is a bit premature to conclude that this fix will "stick" because I have found that what works today may not work tomorrow, but it looks promising. I'll post again at a future date if this is a reliable fix.

---

### Post by markmaus on 2010-03-23
Still not reliable.  The "Available to all useres" solution mentioned above did not turn out to be reliable.  It worked for about five days and then it quit connecting.  I'm back on the ndiswrapper.  Oh well....

---

