---
title: "Ralink-based wifi card - is it supported?"
date: 2006-11-15
forum: Hardware &amp; Laptops
---

### Post by The Grum on 2006-11-15
Hi. Im looking at the Edimax EW-7180PCg wifi card and Ive heard it used to use the RT2500 chipset until recently (and with no change in the product id) when it changed to the RT61.

Are both these chipsets supported by Ubuntu (Dapper onwards)? Is this card safe enough to buy (Ive already been stung by Netgear pulling the same trick)?

Thanks in advance.

---

### Post by Compaq Armada 7800 on 2006-11-15
i saw the driver for that on sourceforge just earlier today, while i was browsing

---

### Post by jon419 on 2006-11-15
I am using a WMP54G wireless network adaptor from Linksys.  Before using Ubuntu, I had to download the Railink 2500 drivers myself, compile, and install them to get my wireless card to work.  So, the rt2500 driver does work on linux.

Now, after moving to Ubuntu 6.06 a few months ago, my wireless card has worked out of the box, I did not have to do any configuration short of entering my WEP key.  Not sure which driver it is using, I would assume it is using the linux rt2500 driver.  But, it did work as soon as I installed Ubuntu.

My long winded two pennies.

---

### Post by The Grum on 2006-11-15
Thanks for the replies, guys.

For info, I emailed the manufacturer who confirmed it is using the RT61 chipset, but Linux drivers were available. Sadly, there seem to be a lot of threads with people having problems with this chipset in Dapper and Edgy.

---

### Post by neocookie on 2006-11-16
Just out of interest, do you have the CD with the original windows drivers? Might be worth installing ndiswrapper and trying those drivers - worked a treat with my Marvell card on my new laptop.

---

### Post by The Grum on 2006-11-16
I havent actually bought the card yet. I have a Belkin wifi card which works fine under ndiswrapper, but Im looking for one that will work out of the box.

---

