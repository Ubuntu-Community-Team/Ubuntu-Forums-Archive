---
title: "network Disabled"
date: 2006-03-07
forum: Hardware &amp; Laptops
---

### Post by Bill Door on 2006-03-07
Ok I have a Chicony MP979 laptop 233 with 128 MB ram.  I have no idea whose Motherboard it is.  Breezy is on the machine and i have been trying to get a network card working MSI ID 1814/0201 and I believe it is supported by the RT2500 driver.  I have gone through nearly all the help and HOWTO  threads that i can find to get the network card working.  

When i turn on the computer with the card in the light comes on.  I can go to Network settings and the card is visible as ra0 but is not configured.  When I click on the card and then "properties" the timer starts and then I get a freeze.  I have to turn off reboot. 
Lspci shows network  disabled and the card has an IRQ allocated (10). It shows the product name and vendor logical name ra0 and the bus info :pci @01:00.0
Lsmod shows that the rt2500 module is there.
Cardctl config shows that the interface is "cardbus" in socket 0 (but not as ra0) and has IRQ 10 [exclusive] [level]

I have looked at the way that the card links to the maiin bus and there is no problem with 00 linking to the other subordinates.

I have tried ndiswrapper using windows 2000 through to XP but no difference.  I have tried looking at the logs but there doesn't seem to be anything there (have seen nothing in any of the logs to show that there is a problem.

The wireless troubleshooter has a section of "device seems to be there but device disabled"  the indications are that there might be a work around.  There is no external switch for the wireless and the manual does not mention anything about turning on the PCMCIA bus.  I have searched the internet for information but nothing comes to light.

I have tried the APICoff etc but nothing helps.  The Bios in minimal and have tried various options for the settings but still no success.  As far as i can see i am using kernel 2.6.12.9.i386.  there is no mention of SMP or preempt  I have tried another card and that is no different.  There is nothing other than the lo network in the network interfaces.  So for some reason I can't get it configured.  I have tried iwconfig ra0 up with the same results.  So if anyone can make any suggestions it would be appreciated.  I have not included any prints as i am having difficulties putting this up on the site as this is my other computer (desktop) running XP and until I am satisfied that linux is the way to go then i don't want to change it just yet.

I have tried to use the lastest cvs but have met a blank wall cos i can't find gcc.3.4 and the last time i tried i had a heck of a job trying to get this old computer cleared for another clean boot ( it chuntered away for at least an hour before i switched it off).

Anyway over to you I will be looking in, hopeful, once a day. (I have loaded adjusted and read so many threads that i think i ahve been doing it in my sleep).

regards  Bill

---

### Post by Bill Door on 2006-03-09
So that's 33 down.  Not sure how long it will take to get help but can wait

for a while

Bill

---

