---
title: "Working around for slow boot due to network starting delay"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by xarmian on 2007-05-23
The following is a proposed work-around if you are having problems with a slow boot-up due to a 30-40 second delay in the networking service start-up.  Other work-arounds exist, however whenever I tried them, my wireless network stopped working.  Please note that I am not 100% sure of the security implications of this workaround, and as always I am not going to be responsible of this screws up your system :)

If you notice a long pause during the Ubuntu logo screen at about 40%, try hitting Alt+F8 to see if it's paused starting the network.  Then you're likely encountering this problem.  You will also see the delay in your messages system logfile (/var/log/messages) which looks something like this on my system:

> 
May 23 01:17:51 dave-laptop kernel: [   24.644000] wlan0: ethernet device 00:90:4b:4f:ee:b4 using NDIS driver: bcmwl5, version: 0x50000, NDIS version: 0x500, vendor: '', 14E4:4320.5.conf
May 23 01:17:51 dave-laptop kernel: [   24.648000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
May 23 01:17:51 dave-laptop kernel: [   24.648000] usbcore: registered new interface driver ndiswrapper
May 23 01:17:51 dave-laptop kernel: [   25.820000] NET: Registered protocol family 17
May 23 01:17:51 dave-laptop kernel: [   65.068000] NET: Registered protocol family 10
May 23 01:17:51 dave-laptop kernel: [   65.068000] lo: Disabled Privacy Extensions
May 23 01:17:51 dave-laptop kernel: [   65.068000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 23 01:17:51 dave-laptop kernel: [   67.252000] input: Power Button (FF) as /class/input/input5


To work around this delay, I changed networking to start with my session rather than as a service.. This allows networking to start after Ubuntu has loaded, and it loads much faster.  **If you are using your machine for remote connections and need the network to be started at the Ubuntu login screen, this work-around WILL NOT WORK**

To begin, I copied the /etc/init.d/networking script to an alternate location.  In my case, it was /home/dave/.gnome/networking

> 
cp -a /etc/init.d/networking /home/dave/.gnome/networking


Then, remove executable permissions from the init.d script:

> 
sudo chmod oug-x /etc/init.d/networking


Then edit your /etc/sudoers file:

> 
sudo visudo


Now we need to add a line to the sudoers file which will allow the execution of our networking script without requiring a password.. This way we don't need to be prompted every time we log in for a password.. So add line(s) with the following sheme to the **very last line(s)** of your sudoers file.. If you have multiple users who will need networking enabled, you will need to add a line similar to the following for each user:

> 
username ALL=(ALL) NOPASSWD: /path/to/networking


for example:

> 
dave ALL=(ALL) NOPASSWD: /home/dave/.gnome/networking


Now, we need to run the networking script at the start of our session.  This will need to be done for every user who need networking support (every user added to your sudoers file).  So (in gnome) go to System -> Preference -> Session and select the Startup tab, then add a new item, name it "Networking" and use the following for the command:

> 
sudo /path/to/networking start


For example:

> 
sudo /home/dave/.gnome/networking start


If you are not using Gnome, use whatever procedure is required to add at startup command in your desktop environment.

Let me know if this works or if you have trouble.. This sped my startup by over 40 seconds.. from 97.5 seconds to 54 seconds from kernal initialization to loaded desktop, including logging in.

**If you need to UNDO:**

If you need to undo this work-around, the key pieces are to remove the session startup value and re-add execution rights to the /etc/init.d/networking startup script.  To re-add execution rights, run:

> 
sudo chmod oug+x /etc/init.d/networking


Other items include removing the lines you added with visudo and deleting the copy of the networking script..

Good luck.

-Dave

---

