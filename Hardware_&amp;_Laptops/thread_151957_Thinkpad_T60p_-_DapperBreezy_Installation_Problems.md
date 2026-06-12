---
title: "Thinkpad T60p - Dapper/Breezy Installation Problems"
date: 2006-03-28
forum: Hardware &amp; Laptops
---

### Post by nahham on 2006-03-28
I recently bought a Lenovo IBM Thinkpad Core Duo T2500 2 GHz - 15" TFT.  Such a nice laptop.  It has a ATI MOBILITY FIRE GL V5200 - 256 MB.  I did want to dual-boot with this machine and was hoping Dapper would work out-of-the-box but it didn't.  It reports that "no screen found".  I tried to install Breezy, but with no luck.  I really want to use Ubuntu but if no solution is found I might try other distros. Does anyone know how to fix this problem?

Thanks for the help in advance..

---

### Post by mips on 2006-03-29
Your laptop is reletavely new but I'm pretty sure we can get it to work with one or two tweaks.

We are going to need a bit more information though.

I don't know exactly whats worg but from the command line you can try this command.

```
sudo dpkg-reconfigure xserver-xorg
```

BUT you mentioned the display cannot be found so the above might not work. I'll have a look around in the meantime but hopefully someone else here has a solution.

Could also try Dapper Drake Flight 5 (or current build) as it might have support for the dispaly.

[http://www.thinkwiki.org/wiki/ATI_Mobility_FireGL_V5200](http://www.thinkwiki.org/wiki/ATI_Mobility_FireGL_V5200)
[http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki)

So far I have read that Suse10.1 beta6 works but their is no real support for the ATI video card so you are stuck with the VESA driver for now.

What is the output of the **[COLOR="Red"]lspci -v[/COLOR]** command, paste it here.

Another issue you might encounter is your wireless card if it is a Intel 3945 model as the drivers are very new. [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

Just found this, installation instructions for Dapper Flight 5 on the T60, [http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.04_Flight_5_on_a_ThinkPad_T60](http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.04_Flight_5_on_a_ThinkPad_T60)

---

### Post by nahham on 2006-03-29
Well Dapper now works using "vesa" instead of "ati" in the driver section in xorg.conf.  I'm upgrading everything and then will try to install the proprietary ati driver.  Still have to get the wireless working.  Thanks for the links mips.  I did search for a t60 page on the thinkwiki with no luck before.

---

### Post by mips on 2006-03-30
[QUOTE=nahham]Well Dapper now works using "vesa" instead of "ati" in the driver section in xorg.conf.  I'm upgrading everything and then will try to install the proprietary ati driver.  Still have to get the wireless working.  Thanks for the links mips.  I did search for a t60 page on the thinkwiki with no luck before.[/QUOTE]

Not to discourage you but I don't think the ATI driver is going to work. As far as I can tell it does not support your gfx chipset 'yet'. It won't hurt trying though.

Could you clarify what ati chipset you are using ???

---

### Post by nahham on 2006-03-30
Well, the i3945ABG wireless card is working on a basic level.  Does not seem to work with encryptioin and Network-Manager does not work.

However, iit was done by using those links:

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.04_Flight_5_on_a_ThinkPad_T60](http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.04_Flight_5_on_a_ThinkPad_T60)
[http://doc.gwos.org/index.php/Network_Manager_with_WPA](http://doc.gwos.org/index.php/Network_Manager_with_WPA)

(thanks mips)

As for the display, as you said the ATI driver didn't work.  The chipset is 

0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 71c4 (prog-if 00 [VGA])
        Subsystem: Lenovo: Unknown device 2007
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 2000 [size=256]
        Memory at ee100000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at ee120000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] #10 [0011]
        Capabilities: [80] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-

according to lspci -v command.

I might use XP until dapper becomes final and there might be a better support for the device in general.

---

### Post by mips on 2006-03-30
I think the device is a x1600 or something of the sorts and not supported as yet. I would however recommend you ask in the Audio/Video section here as I could be wrong and hopefully I am.

The vesa driver will work but without 3d acceleration.

It's not really up to dapper to provide proper support for those devices. That responsibility lies with ATI & Intel.

---

### Post by Paulo Wageck on 2006-05-10
i am also waiting for the drivers....

its a nice notebook!

firegl is supposed to be more linux compatible ati says.. hehehe

lets see!

---

### Post by Paulo Wageck on 2006-05-10
firegl shoud me more linux friendly as ati says.. heheh

ops...

double posting sorry...](*,)

---

### Post by jml on 2006-05-10
Try this link to help troubleshoot your wireless issues.  Its the Ubuntu wiki on wireless troubleshooting.  Hope it helps.

[https://wiki.ubuntu.com/WifiDocs](https://wiki.ubuntu.com/WifiDocs)

Joe

---

