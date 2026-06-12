---
title: "Evolution to Exchange server lockup freeze"
date: 2008-07-24
forum: General Help
---

### Post by CheeseEatingBulldog on 2008-07-24
I am trying to set up an ubuntu box at work to integrate with the windows network. I have gotten it to log on to the domain controller and get access to SAP, but evolution keeps on freezing.

I have set it up and can see mail coming in if I send a test, but as soon as I open a mail it freezes.

I did a debug out of the terminal and I get the same error over and over again (about two pages worth):

> ** (evolution:21370): WARNING **: couldn't connect to daemon at $GNOME_KEYRING_SOCKET: /tmp/keyring-PHyChe/socket: Connection refused

It also does not remember my passwords, eventhough I ticked the box and it constantly asks permission for access to my keyring, which I set to "always allow" and aparently doesn't save that either as it prompts me for it each time I log in to evolution.

Any ideas, this is sending me nuts

---

### Post by CheeseEatingBulldog on 2008-07-25
This was caused by the Global Address Book address not being correct. The GAB was on the domain controller and not on the exchange server, so I removed the exchange server from the addy and it worked:

so instead of > exchangeserver.domain.com it was > domain.com.

---

