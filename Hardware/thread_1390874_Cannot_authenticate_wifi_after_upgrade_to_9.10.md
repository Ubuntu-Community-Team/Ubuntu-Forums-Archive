---
title: "Cannot authenticate wifi after upgrade to 9.10"
date: 2010-01-26
forum: Hardware
---

### Post by erasmosis on 2010-01-26
So I upgraded my OS from 9.04 to 9.10 today and now the wireless cannot connect to a secure network.   The wireless connects just fine to public networks, I can connect to the library network without a hitch. But my home network cannot authenticate.  When I  attempt to connect, it says preparing to connect, acquiring network address, and then sends me back to the password dialog.  I can connect with my windows laptop and my roommates mac laptop, so im certain its not the router.  I was able to connect just fine a few hours ago.  Now it can see the network, but cannot connect.

Im using a dell latitude D610.

---

### Post by neeraj2608 on 2010-01-26
> **erasmosis said:**
> So I upgraded my OS from 9.04 to 9.10 today and now the wireless cannot connect to a secure network.   The wireless connects just fine to public networks, I can connect to my neighbors network just fine. But my home network cannot authenticate.  When I connect to it the computer connects, acquires network address, and then sends me back to the password dialog.  I can connect with my windows laptop and my roommates mac laptop, so im certain its not the router.  I was able to connect just fine a few hours ago.  Now it can see the network, but cannot connect.

Im using a dell latitude D610.

Try deleting the network from the "Wireless" tab of the "Network Connections" dialog (the one you get by right clicking the Network icon in the notification area and choosing 'Edit Connections') and then trying again.

---

### Post by erasmosis on 2010-01-26
> **neeraj2608 said:**
> Try deleting the network from the "Wireless" tab of the "Network Connections" dialog (the one you get by right clicking the Network icon in the notification area and choosing 'Edit Connections') and then trying again.

The network is called Project Mayhem and so the connection profile is called project mayhem.  Is that what you mean? if not, I dont know how to delete the wireless tab

---

### Post by erasmosis on 2010-01-26
> **erasmosis said:**
> The network is called Project Mayhem and so the connection profile is called project mayhem.  Is that what you mean? if not, I dont know how to delete the wireless tab

Furthermore, if that is what you mean... I have deleted that and recreated it many times at this point with no luck.

---

### Post by erasmosis on 2010-01-26
Ok, so I just went through and deleted all the connection profiles there were. (One for home and one for the library.)  I set up a new profile.   When I click connect it does this...
Configuring interface
Acquiring Network address
And then Authorizing

At this point the password dialogged pops up asking me to start the process over again. 

Any other ideas?

---

### Post by neeraj2608 on 2010-01-26
> **erasmosis said:**
> Furthermore, if that is what you mean... I have deleted that and recreated it many times at this point with no luck.

Yeah, that's what I meant.

---

### Post by neeraj2608 on 2010-01-26
> **erasmosis said:**
> Ok, so I just went through and deleted all the connection profiles there were. (One for home and one for the library.)  I set up a new profile.   When I click connect it does this...
Configuring interface
Acquiring Network address
And then Authorizing

At this point the password dialogged pops up asking me to start the process over again. 

Any other ideas?

Try to connect to the network using Gnome (if you have it). Alternatively, try to use Gnome's network manager in KDE (type 'nm-applet' without quotes in the Alt + F2 dialog).

Also see [plasma widget networkmanager couldn't connect wpa]("https://bugs.launchpad.net/ubuntu/+source/plasma-widget-network-manager/+bug/378145"). Might be relevant.

---

