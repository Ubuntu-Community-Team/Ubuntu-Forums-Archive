---
title: "how to connect to internet"
date: 2004-12-29
forum: General Help
---

### Post by dummyfish on 2004-12-29
Hi, i am a new user of linux. i have installed ubuntu and i tried to connect the pc to internet. but it is not successful. do i need to set up some things before connecting to internet? If so, how can i do it?

thanks

dummyfish

---

### Post by nemin on 2004-12-29
[QUOTE=dummyfish]Hi, i am a new user of linux. i have installed ubuntu and i tried to connect the pc to internet. but it is not successful. do i need to set up some things before connecting to internet? If so, how can i do it?[/QUOTE]
First you have to tell how you connect to the Internet. For example, if you have a Cable/DSL connection with a router, you have to setup the network and select your router as gateway. But there are much more scenarios, so give us some more information :)

---

### Post by Buffalo Soldier on 2004-12-29
Can you tell use a bit more about your computer system and internet service provider? (modem dial-up, broadband: cable / dsl)

Before using Ubuntu/Linux, what OS were you using? What did you have to do to connect to internet back then?

---

### Post by dummyfish on 2004-12-29
First of all, thank you for your hint.

Before installed Ubuntu, the os is win98 without internet connection. 
I am now using broadband (i.e. cable modem) and lan card without router. My PC is Celeron 400, 384MB RAM. By the way, is there any installation guide or user manual of ubuntu? If yes, pls tell me where i can find it such that  i can refer to it first before posting questions. Thx.

---

### Post by hardcandy on 2004-12-29
Run "ifconfig: and see if it returns more than "localhost". Also, there is a forum called Howto/FAQ which have several good tweaking and getting started guides. Excellent guides from users. 
If you do not see anything other than localhost after "ifconfig" then try "sudo ifconfig eth0 up". If still no address,  then probably the cable modem is not allowing you to connect. Look at the cable modem's documentation on accessing the setup menu via web browser. For my Bellsouth connection I use a router which is accessed via "http://192.168.1.1" in the address bar of the browser. So your cable modem should have a setup menu available.

---

### Post by NewbieNik on 2004-12-29
Most Cable connections require you to specify the hardware or MAC address of the NIC (Network Interface Card) that is connecting to the cable modem. This is the only card that will be recognised by the cable supplier and therefore work on the connection. This then allows your card to pick up an IP address from their servers.
Without this you will not be able to access the internet.

Ensure you have given these details to your supplier. If not they will be able to talk you through finding these details and get you up and running.

---

### Post by nemin on 2004-12-29
[QUOTE=dummyfish]Before installed Ubuntu, the os is win98 without internet connection. 
I am now using broadband (i.e. cable modem) and lan card without router.[/QUOTE] 
OK, so your computer is directly connected to the cable modem by a LAN cable, correct?

First, you have setup your network card. Usually the network card is detected automaticly, and you only have to enter 'sudo ifconfig eth0 up' to get your network card up. Since most cable modems have a integrated DHCP server, your computer will retreive a IP-address (You can check that by looking at 'sudo ifconfig eth0') 
If not, you have to set up a IP address yourself and set the IP of your modem as 'gateway'.
Usually you can connect to a webbased administion module of your modem and cofigure it correctly. Your cable modem documentation should cover this all. 
[QUOTE=dummyfish] By the way, is there any installation guide or user manual of ubuntu? If yes, pls tell me where i can find it such that  i can refer to it first before posting questions. Thx.[/QUOTE]
You can always search this forum for already asked questions. There is also a very good "Unofficial Ubuntu 4.10 Starter Guide" on [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/).
Google is your last hope, or ask here :)

Hope this helps and let us know if it doesn't :)

---

### Post by dummyfish on 2005-01-04
Thank you all.

The problem is solved.

---

