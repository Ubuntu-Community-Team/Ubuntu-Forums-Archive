---
title: "SATA HDD's + PCI card = randomness"
date: 2010-02-03
forum: Hardware
---

### Post by guerd87 on 2010-02-03
First post here to the forum, long time reader though. Have been using Ubuntu for a while now.

I built myself a home file server a few weeks ago consisting of a few older pieces I had around

2500+
Gigabyte Motherboard
2GB DDR

I have had the server running well for nearly 2 weeks now, web server, torrentflux, rsnapshot backups etc etc. My motherboard doesnt have and SATA ports so im using 2 x 250gb IDE HDD's right now + an 80gb for the OS

Now the server has proved itself in reliability I want to throw in my 4 x 500gb SATA drives and run a software raid 5 with MDADM and LVM over the top. I picked up 2 x 2port SATA PCI cards today to chuck them in.

The cards use the Via VT6421A chipset which I researched and does work under linux. I installed the cards with no drives and booted it up, SSH'd to the box and setup modprobe sata_via and the cards where then recognised straight away.

After a shutdown and plug in my HDD's im getting errors, it is very hit and miss. With all 4 HDD's plugged in i get nowhere, after my post screen i just get a blank screen with flashing cursor in the top left of the screen. At this time my SATA card's have a green light showing.

Tried many different combinations of 1 drive, 2 drives, 3 drives, different cables etc etc with no luck really. I did have it into linux once with 2 drives attatched.Once I was up and running the lights on the cards were out, im guessing the green is an error of some sort, but not sure yet. Need to search for it.

When I finally got it up with 2 HDD's I partioneded them and then started writing the file system on there and then I hit another error. Green light is back on again and the computer just hangs. Had to manually cut the power to get it to go off. 

After another few hours of playing around i have now removed the cards and HDD's as i cant get them to work.

Anyone have any ideas what it could be? Im assuming it is hardware related, but i cant really put anything up to prove it. I was thinking PSU may be overworked, but at the same time i can run only the OS HDD and 1 SATA HDD and still get errors.

Im kind of lost here, been playing with it all day, might just have to use a motherboard that has onboard SATA maybe

cheers
John

---

