---
title: "HP Mini 210 HD and Ubuntu 9.10"
date: 2010-02-12
forum: Hardware
---

### Post by Sabot on 2010-02-12
I finally had a chance to pickup a new Netbook and was not sure how well it would work with Ubuntu 9.10.

All I can say is job well done for the HP Mini 210 HD.  

Almost everything worked right out of the box.

The two exceptions are the trackpad and wireless.

For wireless you have to run update manager and get the latest updates to 9.10. Then you can run System>administration>hardware drivers and install the broadcom sta wireless driver.

For the trackpad it works but the buttons that are integrated into it do not work. 

To get the trackpad working correctly you need to use the terminal and enter in these commands:

    ```
sudo su
```

    ```
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
```

    ```
reboot
```

What is really cool is the webcam and built in mic just work.

Also you can connect an external monitor and use the button on the keyboard to change from external only to internal only view of the screen.

The brightness and volume keyboard function keys also work.

I do a lot of youtube viewing and it works great for normal videos, but it does not play anything over 380p.  Not a good tool for watching HD Youtube videos.

Battery performance and general performance are just perfect for this little mini.  I highly recommend this netbook for ubuntu use.

---

### Post by CompShrink on 2010-02-16
Hey, I'm considering getting a HP Mini 210 HD or an Asus Eee PC 1001P. I was wondering if you could give me an idea how long the battery life is?

According to Amazon, the 210 (NOT HD) with 6 cell battery is rated 9.75 hours battery life, whereas the 1001P is rated 11 hours. The 1001P (same basic specs, other than resolution) is only $300 at newegg, so while the extra screen real estate is tempting (1366 vs 1024 is a reasonably big jump) it'll be about $60 more to get the 210HD with 6-cell battery.

By the way, **thank you** for posting compatibility, and how to deal with the minor issues. It's nice to see posts like this when considering what hardware to buy.

---

### Post by Sabot on 2010-02-17
Make sure you try the keyboard on the mini 210.  It is soft and you may not like it.  Battery life for me at 100% brightness is about 2.5 hours with the 3 cell.

I would only purchase a netbook if it has 1366x768 resolution.  I find the lower resolution netbooks to be very limiting.

---

### Post by OldTroll on 2010-02-21
I'm seriously considering the 210 HD, but since I can't lay hands on one, could I ask you to confirm a few things?

1)  Is the keyboard the chiclet/island style keyboards (small keys with space around them?)  That's the style keyboard that I can see on the normal 210's in the stores, but a few reviews have mentioned two styles of keyboards and would like to confirm that this is the style on the 210 HD.

2)  If this is the island style keyboard, does it have the in-key led indicators for Caps Lock, Wireless and Audio Mute?

3)  Did you get the Broadcom Video accelerator in your system?  If so, is it functional?

4)  Did you get the Bluetooth module?  If so, is it functional?

Sorry to pepper you with so many questions, but there are very few solid sources of information and I'm not crazy about buying something I can't get a good specs list for...

Thanks,
OldTroll

---

### Post by Sabot on 2010-02-21
The 210 HD does come with the chiclet/island style keyboard with the Led indicators in the keys.

I did not purchase the bluetooth or the broadcom accelerator for my computer,so I was not able to test those features.

---

### Post by wbest on 2010-02-21
I have the HP Mini 210 1010NR (Not HD), and I'd like to say add a few things.
I had to go to the Package Manager then reboot the computer to get the wireless to work.  It's still the same thing, but its in the package manager.  For some reason, after I installed UNR, it didn't show up as a Driver.  It did when I ran the LiveUSB, but not when I booted into the real deal.

Also, I had Windows 7 and wanted to Dual-Boot.  So I had to remove the HP_TOOLS partition, which I checked with HP just to make sure, is safe to do.

Everything else about this seems to be true of my machine.

The one problem I do have is that scroll doesn't work on the trackpad in linux after making the above change.

Are you having this problem, Sabot?

I found this website that mentions other psmouse options (other than exps).  I don't know if you know if they work or not.  I haven't had a chance to test them.  But maybe if we use one of the other options we can get scrolling back (unless you didn't loose it like I did).
[http://www.idevelopment.info/data/Unix/Linux/LINUX_ErraticMouseBehaviorwithMouseFedoraandBelkinKVM.shtml](http://www.idevelopment.info/data/Unix/Linux/LINUX_ErraticMouseBehaviorwithMouseFedoraandBelkinKVM.shtml)

---

### Post by boot_sectorz on 2010-02-25
> **Sabot said:**
> The 210 HD does come with the chiclet/island style keyboard with the Led indicators in the keys.

I did not purchase the bluetooth or the broadcom accelerator for my computer,so I was not able to test those features.

I got my broadcom accelerator working on my Dell D630 using restricted drivers. Not sure now but, i think you have to add repos somewhere. In case one gets the HD card, works like a charm. U need the XBMC to fully enjoy the accelaration

---

### Post by MsKK on 2010-03-15
I had the same issues and bypassed them the same way, but I am also curious as how to restore the scrolling feature. 

Also, I am having troubles resuming when the display goes to sleep. Sometimes it does, sometimes it just hangs there with a black screen (of death) and I have to restart the computer. Could it be the USB (wireless) mouse I'm using? :confused: or something to do with the BIOS maybe?

Thanks guys for the thorough description. ;)

---

### Post by jnetman1 on 2010-03-18
Posted a "how to fix" here: [http://ubuntuforums.org/showthread.php?p=8989185]("http://ubuntuforums.org/showthread.php?p=8989185")  Actually patches the synaptics driver and solves the problem.

---

### Post by Julian Lewis on 2010-04-23
> **Sabot said:**
> I finally had a chance to pickup a new Netbook and was not sure how well it would work with Ubuntu 9.10.

All I can say is job well done for the HP Mini 210 HD.  

Almost everything worked right out of the box.

The two exceptions are the trackpad and wireless.

For wireless you have to run update manager and get the latest updates to 9.10. Then you can run System>administration>hardware drivers and install the broadcom sta wireless driver.

For the trackpad it works but the buttons that are integrated into it do not work. 

To get the trackpad working correctly you need to use the terminal and enter in these commands:

    ```
sudo su
```

    ```
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
```

    ```
reboot
```

What is really cool is the webcam and built in mic just work.

Also you can connect an external monitor and use the button on the keyboard to change from external only to internal only view of the screen.

The brightness and volume keyboard function keys also work.

I do a lot of youtube viewing and it works great for normal videos, but it does not play anything over 380p.  Not a good tool for watching HD Youtube videos.

Battery performance and general performance are just perfect for this little mini.  I highly recommend this netbook for ubuntu use.

---------------

Thanks a lot for that, your post was brilliant, it worked a treat. Thanks

---

### Post by kameleontti on 2010-07-21
Sorry folks but I just have to warn you ;)

That HD-screen, 1366x768 resolution, model of this netbook is of no good, because

1) It still has that Intel Media Accelerator 3150 graphics circuitry with shared memory, so it can't play smoothly better videos than dvd/tv/basic flash -resolution. Not HD-flash nor HD-mp4-videos are smoothly playable. There just isn't enough hardware graphics card power.

2) With screen size of just 10" that 1366x768 resolution tends to irritate eyes after longer use - due to human eye natural limits. So that basic model 1024x600 resolution is better in that way. For that 1366x768 resolution I strongly recommend a little bigger screen - at least those 11.6" screen  models, like HP mini 311 has (that netbook can even play HD videos, bcause it has Ati's video circuitry, not that Intel bacis) - those are much better for your eyes. There's lot's of same experience information of that problem in web, just google and read... 

It's so shame that these netbooks don't have 1024x768 or even 1280x800/1024 resolution - that would be much better. That HD sized is stupid, while they even can't play HD-videos - and taller screen would be much better with software/web-use.

---

### Post by deangl on 2010-07-27
A good HP reference for understanding the HP_TOOLS partition is:
HP Business Notebook Computer EFI Guidelines    (EFI = Extensible Firmware Interface)
at:
[http://h20000.www2.hp.com/bc/docs/support/SupportManual/c01564727/c01564727.pdf]("http://h20000.www2.hp.com/bc/docs/support/SupportManual/c01564727/c01564727.pdf")

---

