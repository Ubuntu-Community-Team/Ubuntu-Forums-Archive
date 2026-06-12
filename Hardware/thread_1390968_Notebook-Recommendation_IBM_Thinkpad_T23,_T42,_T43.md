---
title: "Notebook-Recommendation: IBM Thinkpad T23, T42, T43/T43p"
date: 2010-01-26
forum: Hardware
---

### Post by night-wing on 2010-01-26
Hello.

I need a recommendation from you. My father's pc is gone and I want to replace it (give him) a used notebook and install ubuntu on it.

He needs it for
- text writing
- spreadsheet calculating
- surfing
- emailing
- watching a dvd from time to time

I thought about buying a thinkpad in ebay or so. A few years ago, I got one myself. It should be work without issues in karmic/lucid.

Can someone tell me, if the types, I listed, are good and performant enough for ubuntu? Of course, I would like to hear/read, if you have another recommendation for me to buy.

Thanks!

---

### Post by tgalati4 on 2010-01-26
I picked up a used 43p for $250.  I cloned the old drive and put in a 320 gig scorpio.  It came with 2 gig of RAM.  It runs jaunty and  everything works as expected--inlcuding sleep.

---

### Post by night-wing on 2010-01-27
Hello.
Thank you for your post. Did you have experiences about the "flexing" - problem?
Regards
night-wing

---

### Post by tgalati4 on 2010-01-29
Pick it up with both hands--one on each side.  I stepped on mine accidently.  It was on the floor and the room was dark.  I put one foot on it with all of my weight (185 lbs--hey it was around Christmas)--and said to myself--Oh that can't be good.

No issues with it.

The bigger potential problem is the ATI graphics chip in earlier T40-T43's.  The ball-solder joints give out after several hundred thermal cycles--causing lockups.  The repair is either a simple reheating of the chip with a pencil torch to reflow the balls or replace the motherboard.  The later models were made with better solder techniques and some boards have 4 blobs of glue on the edges of the graphics chip to prevent delamination.

It's an unfortunate defect, but if the machine is used for light duty, then it should be OK for years.  If you try to play games on it and get the chip toasty--70C, it doesn't shut down until it hits 90C, then you are at greater risk of delamination.

I installed the smart fan control and you can set the fan level to progressively faster as the chip heats up, which lowers the thermal gradient.  Also, I keep my machine in suspend mode all the time, so it's only 10 seconds to a working desktop.  This keeps some voltage on the motherboard which also lowers the thermal gradients.

Flexing is an issue for a machine that has seen a lot of field use.  Many of these thinkpads were issued for outside sales and insurance brokers.  They have seen a lot of use and it shows as loose hinges, cracks in the palmrest, cracked screen bezels, missing keys etc.

If you get a machine that has been well-cared for then you should be OK.  Bring an Ubuntu LiveCD with you to evaluate the machine.  Run memtest for a few minutes to test the RAM then boot and verify that things work as expected.

These machines are out of warranty, but there are a lot of spare parts available.  There are lots of on-line tutorials for self-repair.  Hard disk is super easy to replace.  RAM is 2 screws from upgrading.  At $200-$300, they are a much better value than the netbooks and consumer grade laptops available.

They run linux well, but you already knew that.

---

