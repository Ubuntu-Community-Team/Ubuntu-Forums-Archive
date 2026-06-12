---
title: "Compaq EVO N610c *HELP*"
date: 2008-09-03
forum: Hardware
---

### Post by kwdizzy87 on 2008-09-03
Hi,

Pretty much a newby to linux here running 8.04, but I'm having a problem with the installation of some drivers to get the W200 wireless up n running. Here is the documentation I have been fallowing:

[https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200](https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200)

now my problem is that when i get to the end of the prerequisite section after i have put in the command that it states for 6.06 or later i am getting this:

Reading Package List...Done
Building dependency tree
reading state information...done
package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted,or is only available from another source

any one have any idea whats going on? 

also too I am trying to get the ati radeon 7500 in this thing up n running any suggestions?

---

### Post by lazyart on 2008-09-04
Hmmm... I have an N620c.  I skipped the whole W200 thing because 1) it was a pain and 2) it's 802.11b.  Using it on a 11g network would make everyone slow down to 11b speeds.

What I did was open up the bottom of the laptop, removed the miniPCI modem and put in an Intel miniPCI wifi card.  I found later that I would have to downgrade the BIOS because Compaq put in code to verify that the installed card was manufactured by Compaq or else it won't boot.

To recap-> Downgrade BIOS to 1.06. Install Intel miniPCI wifi card. Ubuntu doen't even flinch.

Here's an ebay search for you: [http://search.ebay.com/minipci-wifi-intel_W0QQfrppZ50QQfsopZ1QQmaxrecordsreturnedZ300](http://search.ebay.com/minipci-wifi-intel_W0QQfrppZ50QQfsopZ1QQmaxrecordsreturnedZ300)
Don't get PCI-E.  Won't fit.

---

### Post by kwdizzy87 on 2008-09-04
Thanks for the advice but...im fixing this machine up for a freind that doesnt wanna pay for new part, im just trying to get the thing up n running all she will be doing is using this at her home just to surf the web. 

lol any ideas why i can create a link to the home folder?

---

### Post by lazyart on 2008-09-04
> **kwdizzy87 said:**
> lol any ideas why i can create a link to the home folder?
??

---

