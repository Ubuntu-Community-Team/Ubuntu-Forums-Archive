---
title: "Wireless takes 30min to reconnect after sleeping"
date: 2013-04-18
forum: Hardware
---

### Post by strycat on 2013-04-18
So on a fresh install of Kubuntu 12.10 I'm having this problem on my laptop.  When I boot up it connects to my wireless network just fine. Not sure how important it is but my network doesn't broadcast the ssid.  I do have the "connect automatically" and "system connection" checkboxes checked.

The problem starts when I close the lid and the laptop goes to sleep.  When I open the lid and  it wakes up, I'm not conntect to the wireless.  It shows the no connection icon on the panel.  If I wait about 30min it will magically connect without me doing anything.

I've come across posts that say add something /etc/pm/sleep.d to restart NetworkManager.  Others suggest doing rmmod and modprobe.  There's also been posts about adding the line SUSPEND_MODULES=modulename to /etc/pm/config.d/00sleep_module.

None of this seems to have any useful effect. 

rfkill list says nothing is blocked.

I've also tried manually doing some of these things.

service network-manager restart 
It will sometimes cause a crash and sometimes it will add a 2nd wireless network adapter which never connects although the 1st one eventually connects (after about 30min).

/sbin/rmmod iwlwifi

The makes a red x icon on the network indicator on the panel

/sbin/modprobe iwlwifi

This removes the x, but the wifi still takes 30min to connect.

So at this point I'm at a total loss.  In Kubuntu 11 the wireless reconnected almost immediately (usuallly by the time I got the screen unlocked).  That's the behavior I want.  Is it possible in 12?

Thanks in advance.

---

### Post by strycat on 2013-04-26
I'm sorry to bump this, but it is still a serious problem.  Can someone please help me?

---

