---
title: "hp nc6000 and atheros wireless"
date: 2005-08-27
forum: Hardware &amp; Laptops
---

### Post by jjanssen on 2005-08-27
A few questions for anyone out there with an nc6000 and an atheros wireless adapter.

I'm running HP + Ubuntu which seems to work pretty nicely.  My problem with wireless is:

a) for my home access point (a D-link 802.11b router), I have to explicitly run 'iwconfig ath0 channel 1' before the adapter will associate with the router.  Once I run that I can connect (almost) normally.  Until I do that it appears as though the adapter is scanning for an AP, but it never seems to find one.  The standard network configuration gnome tool doesn't have an option on it for a channel.  I tried adding the line 'wireless-channel   1' into my /etc/network/interfaces, but that didn't seem to work.  Any ideas?

and

b) I can't get WEP to work, no matter what I do.  I've entered my 64-bit WEP key into the gnome network configurator, and used 'iwconfig ath0 enc <key>' with no success.  My key is 10 characters long (and worked in Windows BTW) and I'm wondering if I'm using the right format:  xxxx-xxxx-xx or xxxxxxxxxx ?  Any clues here?

I have another HP nc6000 question, but I'll save that for another thread.

---

