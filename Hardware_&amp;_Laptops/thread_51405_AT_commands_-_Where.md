---
title: "AT commands - Where??"
date: 2005-07-23
forum: Hardware &amp; Laptops
---

### Post by Oceola on 2005-07-23
I'd like to find the file where I input "AT" commands to initialize the modem.
I am looking for the file which will allow me to toggle on and off the games mode of this USR5610B Internal PCI/Serial Internal card.
I found most of the configuation stuff for dialup access but can't find anything which looks like a good spot to put the AT string.

Also I'm seeing a lot of files which are locked not only to the user side but the root side too. I thought this was open architecture?

Ubuntu 5.04 Hoary /Compaq Deskpro EP i440bx (686T2) PIII 550/100 mhz.
USR5610B Modem. FF 1.06 (no issues except it wouldn't dump the 1.02 off the box)
Clean install, not even a lousy ext Dos Partition.

Thanks :confused:

---

### Post by autocrosser on 2005-07-24
Use Synaptic & get Gome PPP--In it's setup there is a tab to input AT commands--I put a link on my upper menu panel & it's the only app I use to dialout--

As far as the "locked" files--have you enabled root user? If so--login as root(not just sudo or su)--you will need to goto System>Login Screen Setup> Security & add the option--Allow root to login with GDM---You can now login as root--Remember!! You will now have FULL access & can bork you system good! :wink: 

Hope this helps---

Cheers!!
Dean

---

### Post by Oceola on 2005-07-25
Thanks for the suggestion.
PPP Gnome does not exist in that name or description in Synaptic under user, maybe it's in the list under root but I don't think so. There's only a PPP/ISDN configuration. I'm not ISDN.
I'm looking for the file to input the simple AT string to turn off the games side of the modem.
It will help with performance.
I used the sudo command to configure and found the files under /etc which seem to pertain.
Nothing so simple as the configuration you speak of.
I've looked at Chaps and Peers for a file where I could precede or follow a modem connect call with the configuration change.

Thanks. :|

---

### Post by autocrosser on 2005-07-26
Use search in Synaptic--Its Gnome PPP--Have you opened up to all the respositories? Should be under universe-net--version is 0.3.17-2   It will make your life MUCH easier :) 

If you have not opened repositories--look at  [http://ubuntuguide.org/](http://ubuntuguide.org/)  Lots of info you need to know :wink: 

Cheers!!
Dean

---

### Post by Oceola on 2005-07-26
Thanks. I'm off to look.

---

