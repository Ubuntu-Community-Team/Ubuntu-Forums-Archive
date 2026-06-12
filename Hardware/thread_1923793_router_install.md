---
title: "router install"
date: 2012-02-11
forum: Hardware
---

### Post by MMcQuown on 2012-02-11
Help! I am trying to install a Belkin N300 router and am having no luck. I can get the disk to open, and provide information, but it doesn't go to an install screen. I need to get this done by noon Sunday so DirecTv can finish installation of the HD tv/DVR setup.

---

### Post by uRock on 2012-02-11
You shouldn't need the disk. Once connected, you can simply enter the router's IP in your browser, which is 192.168.2.1 by default, then leave it blank when it asks for a password, there is no default password on belkin routers. From there you should be able to set up everything to get your router the way you want it. 

[http://www.belkin.com/support/article/?lid=en&pid=F5D8232-4&aid=10177&scid=221](http://www.belkin.com/support/article/?lid=en&pid=F5D8232-4&aid=10177&scid=221)

---

### Post by MMcQuown on 2012-02-11
I got a long list of sites that talk about that IP address, but nothing that actually connected me to the router install.  Aaaaaarrrrrgggghhhh!

---

### Post by drmrgd on 2012-02-11
Did you try doing as uRock suggested?  You just need to make sure your computer is connected to your router, open up a browser window, and go to the address: 192.168.2.1.  Then you can log in (no password by default for new installs), and set it up from there.

---

### Post by MMcQuown on 2012-02-11
As stated, I entered the IP address in the browser window and I got a long list of sites about the IP address, but no the actual site of the IP address. The problem may become clearer once the DirecTV installation is complete. At the moment, the router is connected to the modem on one side and the interface for the interactive TV on the other, but that's not connected to anything yet. The modem-router connection is the phone cord and the router-TV is the Ethernet cord.

---

### Post by ahallubuntu on 2012-02-11
OK - what you're being asked to do is not SEARCH for the address "192.168.2.1" - you're being asked to *OPEN* that page. You can do this even if you aren't on the internet, because you're not actually going out on the web, you're going "inside" your router.   you can even unplug the internet connection from your router while doing this if it helps avoid confusion.

In Firefox or Chrome, type "192.168.2.1" in the address bar, then hit the Enter key.  You should then be asked for a username/password - follow the instructions in the link,.

---

### Post by uRock on 2012-02-11
If you are connected to the router and want to find your router's IP, then open a terminal and run the following,```
ifconfig
```

---

### Post by MMcQuown on 2012-02-11
It's not working. No matter how I do it, Firefox refers the entry to Google, which produces a list of sites.

---

### Post by ahallubuntu on 2012-02-11
If you do what I suggested and UNPLUG the internet connection temporarily, you *CAN'T* get any suggestions from Google.  Not online = no way to get to Google.  But you are still connected to the router, either wirelessly or via a LAN connection.  And router is connected to nothing else.

People have been saying it's 192.168.2.1 - but do what uRock suggests and find the real IP via ifconfig and make sure.  (It should be 192.168.2.SOMETHING .  If by chance it's 192.168.1.SOMETHING, then you'd go to 192.168.1.1 .

---

### Post by MMcQuown on 2012-02-12
I unplugged the Ethernet line from the modem to the computer. The tool bar shows it's disconnected. As soon as I enter the IP address or the config command and hit enter, I get the message that the server can't be found, still referring everything to Google. Firefox opens with Google, which may be the problem, or the router needs to be connected directly to the computer and not through the modem?  But any way you slice it, I can't seem to contact the router.  As I had thought earlier, perhaps when the other connection is put in, this may clear up. OR -- the TV adapter has a power cord which I haven't attached, assuming it was only relevant to the outside connexion.
Tried that; doesn't seem to change anything.

---

### Post by MMcQuown on 2012-02-12
Some forward movement: I can enter the IP address in the top window on the screen and it is trying to connect, but it's not succeeding. If I try entering the config command, it goes to Google and lists related websites.

---

### Post by MMcQuown on 2012-02-12
Once the other connexions were made, everything fell into place. Thank you all for your help and advice.

---

