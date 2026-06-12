---
title: "Network issues. Can't see a router sitting an inch away"
date: 2009-02-26
forum: Hardware
---

### Post by Keithamus on 2009-02-26
I was on Intrepid, and everything was fine. Suddenly my network manager would not even show my network in the list. I thought maybe there was interferance, so gradually got closer to the router while trying to connect. No dice.

Today I decided to reformat and  install Jaunty. Still having exactly the same problem. I know its not the card, as it can see other (WEP and WPA protected) networks, plus, up until a few days ago it was connecting fine. Its not the network blocking my card - because I dualboot osx86 which works flawlessly. I ran nm-applet in the terminal window to get the logs:

<code>
** Message: <info> New secrets for *censored*/802-11-wireless-security requested;ask the user
</code>

Every time that  I get that message, it pops up with the "re-enter password" dialogue - except it prompts me for WEP password. The network is WPA2 secured.

I should also mention the network is using 802.11N MIMO

Any help is appreciated.

---

### Post by Keithamus on 2009-02-28
It seems to be because this is an N network. I can connect to WPA2 based G networks. But this N network just doesn't show up.

My card is a Atheros AR5008 according to lspci.

Does anyone have any solutions?

---

