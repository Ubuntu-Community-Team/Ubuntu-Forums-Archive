---
title: "Switching internet connection please help!"
date: 2008-07-18
forum: General Help
---

### Post by Parasitesss on 2008-07-18
Hey,

At the moment, I have a wired internet connection, using the Westell 6100.
I'm planning on changing to a wireless connection using a Westell Versalink 327W, which a friend gave me.

If anyone could give me basic steps to proceed with the transition that'd be a great help! 


Thankyou

---

### Post by nikgare on 2008-07-18
Turn off the computer, put the card in, turn on the computer ;-)

If the card is supported by the kernel this is probably all that you need to do, if it isn't you will need to post back here with some more info, eg the output from the command **lspci**

---

### Post by lswb on 2008-07-18
First Have you considered calling your ISP and asking them? If they can't/won't help...

Google "Westell 327W" and you will find that it is configured in a similar manner to the Westell 6100, by using a web browser pointed to the router ip address. 

First get the info from the 3100. The default address is 192.168.1.1. Try entering that in a web browser address bar and if it has not been changed, it should open a page with the Westell logo. If this address does not work, open a terminal and type "ping dslrouter" Press Control-C to stop and use the IP address you see there. 

Click on the "Profile Editor" button and you will be prompted for the router username and password. The defaults are "admin" and "password" If this is a verizon account, try "admin" for both user and password. 

After you have successfully entered these, you should see a "connection name" with your ISP name and a delete and edit button. Press the edit button, it will open a window that says something like "Edit (ISP Name) Connection". The ISP account name will be visible but the password will not. You will need to have this password to get the 327W to connect after you plug it in. If you don't know it, call your ISP

Now it's a matter of getting the configuration information from the 3100 and entering it in the 327W. The 327W is accessed more or less the same as the 3100. You can first reset it to factory default by using a reset button on the back of the unit, google for info on that if necessary.

If you have a laptop availble, you can connect the 327W to that next to the Desktop with the 3100 page open, or you could print the pages from the 3100. If the desktop has 2 ethernet ports, you can temporarily change the 327W ip address to be different from the 3100 address and open them both at the same time. (It may be possible to do the same using the USB prot on one of the devices, but I beleive it requires additional software to use the USB port)

Hope this info gets you started.

---

