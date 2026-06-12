---
title: "Linksys WPC 11 please"
date: 2005-12-05
forum: Hardware &amp; Laptops
---

### Post by harisund on 2005-12-05
Hello

I have a linksys wpc 11 ver 3 instant wireless card

I know it works, since I have seen it on Hardware compatibility lists and even ndiswrapper wiki says it works. 

I would like to get it working on my live CD before starting to install it on the laptop. So which driver should I use? On the website it has drivers for Fedora though. 

Thanks

---

### Post by jml on 2005-12-05
If you are running the current version of Ubuntu (5.10) you may already have the drivers loaded.  Boot the live CD with the card plugged in.  After login, go to:  System--->Administration--->Networking.  If you see an option labled "Wireless Connection"  that is your card, its already been recognized.  Highlight the card, click on properties, check enable this connection, and fill in all the blanks.  Click on OK.  With the wireless connection still highlighted, click on activate this connection.  It may take several minutes, but it should come up with the message connection activated.  Click on OK until all windows are closed and you should be good to go.  If you have problems, try setting up an unencrypted connection first, after you get that working, then switch over to WEP encryption.

If you want to set up WPA encryption, your life just got more complicated.  First, the WP11 does not support WPA.  You need to get a card that:  1-supports WPA, 2-has Linux drivers available for it (or Windows drivers using NDSWRAPPER), and has a chip set that is supported by an application called WPA_Supplicant.  This is an application that configures WPA in Linux.  There is no graphical interface, you must manually edit a configuration file to get it to work.  So far, I have not been very successful getting this last bit to work.  There are other posts on this forum that talk about success, however, so if you need WPA, there may be some good ideas here.  Hope this helps.

Joe

---

### Post by harisund on 2005-12-06
Awesome ! Now why didn't I think of that? 

Yes.. it works.. Actually I plugged the card in the PCMCIA slot after GNOME loaded up, and immediately the lights started blinking. I then used the Network Connections panel and activated the card, set the essid and the WEP key and acquire DHCP IP it started working !

Now here is the important question. I am going to install Ubuntu on my laptop, now that I know my wireless card works. The thing is, I will be starting out installing a server version and adding components that I think are necessary. Besides, I would be doing apt-get install xubuntu-desktop

So will it continue to work even after a server installation, or does it require some thing that is available only as a part of the regular installation? 

Thanks for your help !

---

### Post by Lambert on 2005-12-06
If it worked on live cd, it should work on a plain server isntall. You'll just have to know the commands to configure and bring up the interface.

iwconfig 
ifup

you can look at the man pages.

but I have seen some posts where users had no problem with livecd and problems with wireless on an install. If you have problems start a new thread with where you're stuck.

---

