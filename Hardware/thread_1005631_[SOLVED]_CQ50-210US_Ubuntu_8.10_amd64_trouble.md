---
title: "[SOLVED] CQ50-210US Ubuntu 8.10 amd64 trouble"
date: 2008-12-08
forum: Hardware
---

### Post by Nodnelg on 2008-12-08
I have a Compaq CQ50-210US with the AMD Athlon X2 64 in it. I have tried multiple methods of installing Ubuntu 8.10 amd64 and finally had limited success by following a HowTo post on this forum([http://ubuntuforums.org/showthread.php?t=988691](http://ubuntuforums.org/showthread.php?t=988691)). 

It looked as if the install went well using the alternate install disk but the system stalls while booting during the "Loading Drivers" step ( I get an "end trace" after several "? init_ath_pci" entries and directly after a "? system_call_fastpath" entry). I think it may be due to the Atheros wireless interface that so many people have had trouble with. 

Anyone know how to get around this, or how to bypass the offending driver by passing an option to the kernel?

I will also try the 32bit version to see if there is a difference and report back, but would much rather run the 64 bit version.

---

### Post by bl4hbl4hbl4h on 2008-12-08
I also have a CQ50 although not the same model and I can honestly say that it is pain to install 64-bit on one. This is what I did.

Use the 8.04 64-bit alternate. The 8.04 seems to either ignore the ath_pci part or bypass it somehow. Then after the install, I upgraded to 8.10 and it worked fine.

Hope it works out on yours.

---

### Post by Nodnelg on 2008-12-08
> **bl4hbl4hbl4h said:**
> I also have a CQ50 although not the same model and I can honestly say that it is pain to install 64-bit on one. This is what I did.

Use the 8.04 64-bit alternate. The 8.04 seems to either ignore the ath_pci part or bypass it somehow. Then after the install, I upgraded to 8.10 and it worked fine.

Hope it works out on yours.
Did you get the Wirless to work before or after upgrading to 8.10? 

Which method did you use to upgrade?

Thanks

---

### Post by theozzlives on 2008-12-08
My Brodcomm wireless works better in 8.1

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by Nodnelg on 2008-12-08
> **Nodnelg said:**
> Did you get the Wirless to work before or after upgrading to 8.10? 

Which method did you use to upgrade?

Thanks
8.04 alt amd64 had a Kernel panic message after intall upon loading drivers booting. 
   RIP  [<ffffffff8036ddb0>] vgacon_cursor+0x10//0x1f0
    RSP <ffffffff80635f78>
   CR2: 000000000000004c
   ---[ end trace ...
   Kernel panic - not syncing Aiee, killing interrupt handeler!

---

### Post by bl4hbl4hbl4h on 2008-12-08
> **Nodnelg said:**
> 8.04 alt amd64 had a Kernel panic message after intall upon loading drivers booting. 
   RIP  [<ffffffff8036ddb0>] vgacon_cursor+0x10//0x1f0
    RSP <ffffffff80635f78>
   CR2: 000000000000004c
   ---[ end trace ...
   Kernel panic - not syncing Aiee, killing interrupt handeler!

Hmm...

I'm going to have to ask you to try the 8.04 install again but with a boot parameter. Also, unless you still have enough hard drive space, you might want to boot back to vista/xp and remove the linux partitions.

When you boot off the alt cd, before you select install, press f6 and add priority=medium. It may be a little confusing as to what to select but all of the options are automatically on default. 

The only option that you may have to change is when the installer begins to detect hardware. First it will ask about loading a usb thing. After that it will ask whether you want to start PCMCIA card services. Select no for that and for every successive prompt that asks you about it. Everything else should be by default.

---

### Post by Nodnelg on 2008-12-08
> **bl4hbl4hbl4h said:**
> Hmm...

I'm going to have to ask you to try the 8.04 install again but with a boot parameter. Also, unless you still have enough hard drive space, you might want to boot back to vista/xp and remove the linux partitions.

When you boot off the alt cd, before you select install, press f6 and add priority=medium. It may be a little confusing as to what to select but all of the options are automatically on default. 

The only option that you may have to change is when the installer begins to detect hardware. First it will ask about loading a usb thing. After that it will ask whether you want to start PCMCIA card services. Select no for that and for every successive prompt that asks you about it. Everything else should be by default.
We are progressing. I can now boot into the system. The startup sound played though it did have some static. I heard others report of this also, and I will look for a solution after upgrading. Should I get the Wifi working now or after upgrading?

---

### Post by bl4hbl4hbl4h on 2008-12-08
> **Nodnelg said:**
> We are progressing. I can now boot into the system. The startup sound played though it did have some static. I heard others report of this also, and I will look for a solution after upgrading. Should I get the Wifi working now or after upgrading?

What I did was to get the upgrade first since a kernel update usually wipes out the wireless drivers. It did for me anyway.

Also, the sound thing automatically fixes itself after the upgrade to 8.10.

---

### Post by Nodnelg on 2008-12-08
> **bl4hbl4hbl4h said:**
> What I did was to get the upgrade first since a kernel update usually wipes out the wireless drivers. It did for me anyway.

Also, the sound thing automatically fixes itself after the upgrade to 8.10.
Did you use the 8.10 Alt 64 CD to upgrade?

---

### Post by bl4hbl4hbl4h on 2008-12-08
> **Nodnelg said:**
> Did you use the 8.10 Alt 64 CD to upgrade?

No, I used the update manager.

Note that you may have to edit the update settings since 8.04 is long term support and does not automatically offer the 8.10 upgrade.

This link has useful info on that: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Also note that it says to get all updates for 8.04 first. I do realize that it will take long time, but I suppose it's better to be safe.

---

### Post by Nodnelg on 2008-12-08
> **bl4hbl4hbl4h said:**
> No, I used the update manager.

Note that you may have to edit the update settings since 8.04 is long term support and does not automatically offer the 8.10 upgrade.

This link has useful info on that: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Also note that it says to get all updates for 8.04 first. I do realize that it will take long time, but I suppose it's better to be safe.
Update completed and everything works except the wireless interface. Thanks for all your help. I been using Linux since 1996 or 97 and this has been the one of the best yet on relativly new hardware. I must say the ease of install was due to your laying the path for me. Hope I can return the favor sometime.

---

### Post by bl4hbl4hbl4h on 2008-12-08
> **Nodnelg said:**
> Update completed and everything works except the wireless interface. Thanks for all your help. I been using Linux since 1996 or 97 and this has been the one of the best yet on relativly new hardware. I must say the ease of install was due to your laying the path for me. Hope I can return the favor sometime.

Cheers.

I can try to help out with the wireless. Type in lshw -C network in the terminal and post what comes up.

---

### Post by Nodnelg on 2008-12-09
> **bl4hbl4hbl4h said:**
> Cheers.

I can try to help out with the wireless. Type in lshw -C network in the terminal and post what comes up.
I just about got it to work. I can see my wirless networks now, but the PSK is not working. When I check the show password what I typed has been replaced with encryption or the like. Im very close but need to get some sleep. I will work on it some more tomorrow.

---

### Post by Nodnelg on 2008-12-09
I installed wicd and it is working. I was confused for a while because wlan0 was not seeing anything iwlist scan but the interface was not enabled. Pushing the orange Wifi button did the trick. I do wish it would change to blue when enabled. Maybe I will create an applet that changes color when the interface in enabled/disabled. 

Thanks again for your assistance. After I back up the system, I will install Virtualbox and kiss the windows partition goodbye. :)

---

