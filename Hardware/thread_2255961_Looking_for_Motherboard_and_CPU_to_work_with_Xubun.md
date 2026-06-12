---
title: "Looking for Motherboard and CPU to work with Xubuntu"
date: 2014-12-08
forum: Hardware
---

### Post by troy7 on 2014-12-08
I checked the sticky thread on hardware - newest post is from 2007.

I put a system together with a [ASUS M5A97 R2.0 AM3+ AMD 970 SATA 6Gb/s USB 3.0 ATX AMD Motherboard     ]("https://www.amazon.com/gp/product/B008V9959O/ref=od_aui_detailpages00?ie=UTF8&psc=1")and [AMD FD8320FRHKBOX FX-8320 FX-Series 8-Core Black Edition     ]("https://www.amazon.com/gp/product/B009O7YU56/ref=od_aui_detailpages00?ie=UTF8&psc=1")cpu and have had nothing but grief.  The only thing I could get loaded was Xubuntu 12.04 LTS (64 bit) - and this works well, but about once a week it locks up such that I have to hit the reset button.  

Windows 7 wouldn't load - just freeze when installing

Slackware and Xubuntu 14.04 LTS (64 bit) won't install.  I get a kernal panic during the install and couldn't find a reason for it - even put up a post with no luck.  I've tried another power supply, video card, same problems.  I ran memtest overnight - no errors.  Didn't show heating problems, but still got a bigger heat sink and expensive heat gel - no improvement.  So, there is something bad about this motherboard/cpu combination.  I've used the system for over a year - trying different things - but will only install 12.04.  I even varied the install from CD and USB - both work on other computers I have, but no go on this problem combination.

So, I'm trying to move on.  I thought I had a new system picked out - was ready to push the by button on a                                                                [             Gigabyte Black Edition LGA 1150 Intel Z97 HDMI SATA 6Gb/s USB 3.0 ATX Intel Motherboards GA-Z97X-UD5H-BK     ]("http://www.amazon.com/gp/product/B00KYCSCVS/ref=ox_sc_act_title_2?ie=UTF8&psc=1&smid=ATVPDKIKX0DER")with a                                                                [             Intel Core i5-4690K Processor 3.5 GHz LGA 1150 BX80646I54690K]("http://www.amazon.com/gp/product/B00KPRWB9G/ref=ox_sc_act_title_1?ie=UTF8&psc=1&smid=ATVPDKIKX0DER") cpu.  However, went to read the reviews one more time and someone posted they had no luck installing Kubuntu, but windows would install.  I barely missed further dissapointment.

I would like to get a $150 to $200 MB and an i5 processor.  If anyone that is using Xubuntu 14.04 on a combination like this - please post a reply what you have.  I don't want the latest greatest stuff, but a good system that will last me a while.  Thanks.

---

### Post by Darth Riker on 2014-12-09
In regards to the machine that you have - with the AMD FX-8320 and ASUS M5A97 motherboard - have you tried running Ubuntu/Xubuntu/etc 14.04.1 from a Live USB (which - assuming you have a windows machine to work with - was built using this method: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)?") )?

---

### Post by troy7 on 2014-12-09
I did try running live - didn't run a long time, but it did get up and going live on 14.04.  Tried to install after live boot - same results.  Thanks for the link, but it doesn't work.  I'm guessing the elispes in the middle should have some text.

---

### Post by Darth Riker on 2014-12-09
Sorry about that. Link fixed now.

When you say "didn't run a long time" when running live what happened? Did it crash/freeze?

---

### Post by mörgæs on 2014-12-09
How does Xubuntu 14.10 work?

---

### Post by pqwoerituytrueiwoq on 2014-12-09
This is the board i am using with my i5-4690k
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813157501](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157501)
um using xubuntu 14.04 w/ xorg edgers and a overclocked nvidia gtx 650 TI Boost w/ linux 3.16.7
i only have 2 issues, i have no idea which voltage readings are for what, but i know my fan speeds so there is that
WOL is a no go under linux with this NIC (nothing getting a cheap old obsolete 2ed nic could not solve, but that would luck ugly in my windowed case)

the board you picked has a intel NIC so that is good to go
[http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.2060362](http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.2060362)
you may want to google the audio chipset unless you are using the one on you gpu's hdmi

have you tested you hdd? use gsmartcontrol

---

### Post by oldfred on 2014-12-09
I just built a new system with Asus Z97-AR. Cannot say it was particularly easy as there were a lot of UEFI/BIOS settings to change to get it to work.
Many with Gigabyte have reported it works but need iommu setting in UEFI.
 turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)

---

### Post by troy7 on 2014-12-11
Thanks for this info - I'm going to try the board you are using - I have no plans to use Wake On LAN.

---

### Post by pqwoerituytrueiwoq on 2014-12-11
just remember that board does not support SLI and can only use M.2 or (not and) SATA express
i went with this one cause of the price i was able to get it for back in july ($295 w/ i5-4690k)

---

### Post by troy7 on 2014-12-15
Thanks.  Wasn't sure what SLI and M.2 were till I googled them.  I will only have one NVidia card in the system - so should be good? if I understand what I read and what you are telling me.

That was a good price - I paid about $360 for both.

---

### Post by troy7 on 2014-12-23
This is more like it - installation is going very smooth.  I got Win7 and Xubuntu on a dual boot and system is FAST.  Thanks oldFred!

---

### Post by troy7 on 2014-12-31
I made this system a dual boot - Win7 and Ubuntu 14.04.  I found I needed Win7 to do firewire capture from an 'old' Sony HandyCam. I will only do this every couple years or so - otherwise, I'm running all Unbuntu.  The few windows things I still 'need' are run in a VMPlayer virtual.

System has been running great for about 1.5 weeks now.  All I changed was the motherboard and CPU - keep all my existing hardware.  The only flaw to report - and this existed before - is SuperTuxKart doesn't play very well.  But according to forums I've read - that's more to do with the video card.

---

