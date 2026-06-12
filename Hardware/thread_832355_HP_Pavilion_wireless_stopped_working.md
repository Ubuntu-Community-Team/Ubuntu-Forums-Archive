---
title: "HP Pavilion wireless stopped working"
date: 2008-06-17
forum: Hardware
---

### Post by red_bear on 2008-06-17
I had set up an HP Pavilion ze4900 laptop with Ubuntu 8.04 LTS and had the wireless (Broadcom BCM4306 Rev. 3) working with ndiswrapper.

A couple of days later, the owner called me and said the wireless just stopped working out of nowhere.

This laptop has a wireless button with a blue light that used to come on; all of the sudden, the light won't come on and the button doesn't work. The wireless card no longer shows up under System->Administration->Settings, but when I go to System->Administration->Windows Wireless Drivers, the bcmwl5 entry shows up and says Hardware Present: Yes. I tried removing and reinstalling the driver, but it didn't help.

What could possibly cause this? Any suggestions for a fix? I will post more info if it will help.

---

### Post by cwbar_1 on 2008-06-17
If the light does not show up at all, (yellow when not on, blue when on) the System> Administration> Windows Wireless Drivers will still show.  It would appear that your laptop wireless card (or the switch) has gone bad.  I confirmed this by turning my wireless switch to off and checked wireless drivers....still present with yellow light on.
Update;  I did a little extra research and found that re-seating the w-lan card may help.  Go to HP site and look for owner's manual for instructions.  Good luck!

---

### Post by red_bear on 2008-06-18
Thanks, I will check for docs on their site.

---

### Post by CPNowell on 2008-06-18
(cwbar_1) That's a bit of a sweeping statement that probably has no foundation and could worry red_bear unduly. From reading many posts in these forums, It has become quickly apparent that Hardy Heron has managed to "break" the network driver part in most laptop/notebooks that controls the offending light and/or switch and not necessarily stopped the laptop's built-in wifi from actually working either. In my case (Acer Aspire 5612 WLMi) the built in wireless still works fine and connects to my AP 100% (I'm typing on it now) but the switch on the front refuses to light up or control the connection. How do I know this? Simple, put my Windows XP HDD back in and the switch functionality is restored and lights up fine with restored control. As the saying goes, "Never judge a book by its cover"...

---

### Post by red_bear on 2008-06-18
Well, the interesting thing here is that after upgrading to Hardy and reinstalling ndiswrapper, the wireless was working fine. Then, seemingly out of nowhere, it died; nothing had changed software-wise.

Given that the machine left my hands for a few days, I can't discount the possibility that it may have been dropped or otherwise banged up. Who knows.

I found the service manual, the pdf is [here]("http://h10032.www1.hp.com/ctg/Manual/c00325428.pdf"). I'll report back after work when I have time to open it up and reseat the card, the procedure looks simple so it's worth a shot.

---

### Post by red_bear on 2008-06-18
OK, just tried reseating the card. No change.

---

### Post by cwbar_1 on 2008-06-18
(red_bear) If I have steered you wrong, as CPNowell suggests, I am sincerely sorry.  I based my assumputions only on my previous and current experiences with HP laptops.  It might be wise at this point to do a search for his ideas and follow that path. (Leave no stone unturned.)  You might also want to install WICD, and completely remove network-manager, to see if the networks can be seen.  I have found that WICD is a much more reliable program for network management.  (I hope this has helped, and not hurt.)

---

### Post by red_bear on 2008-06-19
cwbar_1,
No worries, re-seating the MiniPCI WLAN card on this thing turned out to be quick and easy. It was worth a try, thanks for the suggestion.

I am going to try installing WinXP on a spare HD to test the hardware as CPNowell recommened. I will report back here in case anyone else with the same problem ends up reading this thread.

---

### Post by red_bear on 2008-06-19
I just noticed something. When I press the button, I get this in dmesg:```
[  211.430168] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[  211.430175] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[  211.630209] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[  211.630214] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
```I guess that means the button itself still works.

---

### Post by maybememe on 2008-07-18
any fix for this yet ?

I have a similar issue on the hp dv6000 laptop.
The light appears on, but doesn't switch to blue. The Broadcom wireless worked when I first installed hardy. Then mysteriously stopped working. I figure an update may have messed it up? I no longer see it in restricted drivers, ifconfig lists only eth0, don't see it running hwinfo in the terminal either.

---

### Post by Clodo_zz on 2008-07-31
Hi to all, i think i have the same problem.

I have a DV8000 with two partitions: XP and Ubuntu 8.04.
Some months ago, both SO works great with WLAN.
After an update on Ubuntu, WLAN doesn't work anymore.
I have a special button for the Wifi on my laptop, that are on (blue) on XP, always off on Ubuntu.

This for me is a GREAT problem, because i don't have any mode to connect to internet (my RJ45 are broken), and i can't try to update to check if a patch is available.
Any ideas? thanks very much!

---

### Post by vigilantpa1adin on 2008-08-01
I am having the same sort of problem.  Fortunately I still have XP on my laptop (even though I never use it), although, it does not work in XP either.  I have been using 8.04 for some time now, and this morning it just suddenly stopped working.  

My model (DV6000z) is known for having many issues.  HP has been losing a lot of money becasue of hardware defects and is offering to extend the warranty on some models.  I have already sent it back once to HP due to an issue with the graphics card.  

HP does suggest to try to update the bios, and here is a link you may find useful:
[http://forums12.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1179013&admit=109447627+1217609775806+28353475]("http://forums12.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1179013&admit=109447627+1217609775806+28353475")

I'm goign to try to update my bios, see if the extended warranty will apply, and get back to you!

---

### Post by CPNowell on 2008-08-02
> **Clodo_zz said:**
> Hi to all, i think i have the same problem.
 
I have a DV8000 with two partitions: XP and Ubuntu 8.04.
Some months ago, both SO works great with WLAN.
After an update on Ubuntu, WLAN doesn't work anymore.
I have a special button for the Wifi on my laptop, that are on (blue) on XP, always off on Ubuntu.
 
This for me is a GREAT problem, because i don't have any mode to connect to internet (my RJ45 are broken), and i can't try to update to check if a patch is available.
Any ideas? thanks very much!
Hi, as I posted earlier in this thread, don't necessarily believe what your light/switch is (or isn't) telling you. Although my light "went out" on my Acer Laptop (Intel 3945ABG) after upgrading to Hardy Heron, because I knew it was working fine with XP I simply ignored it and instead clicked on the network icon on the toolbar. The drop down showed that my wireless network was being detected and could see my AP but was disconnected, so I just clicked on "connect" and up it came but with no light indication at all on the switch to reflect that. As far as I am aware, all Hardy Heron "broke" was control and recognition of the switch/light and not the actual network adaptor itself.
 
Colin

---

### Post by Clodo_zz on 2008-08-04
> **CPNowell said:**
> Hi, as I posted earlier in this thread, don't necessarily believe what your light/switch is (or isn't) telling you. Although my light "went out" on my Acer Laptop (Intel 3945ABG) after upgrading to Hardy Heron, because I knew it was working fine with XP I simply ignored it and instead clicked on the network icon on the toolbar. The drop down showed that my wireless network was being detected and could see my AP but was disconnected, so I just clicked on "connect" and up it came but with no light indication at all on the switch to reflect that. As far as I am aware, all Hardy Heron "broke" was control and recognition of the switch/light and not the actual network adaptor itself.
 
Colin
Yes, thanks.
The button light are always off, but now my Wifi works on my Ubuntu (without updating/reinstalling anything).
I'm not sure about that, i need to re-try to be sure, but seems that if in WinXP the button are switched from ON to OFF, and restart with Ubuntu, Ubuntu doesn't work. We need to come back to XP and re-switch to ON.
Bye and thanks again!

---

### Post by Naturally on 2008-08-09
Hi,

I am having a similar issue with my HP Pavilion.

Mine is a dv2000. I installed 8.04 LTS with Vista, both work fine.

All was working well and I even downloaded all the updates of more than 110 MB using wireless.

All of a sudden the network manager stopped recognising that I have a wireless card. It shows only wired connect and I cannot add wireless. Old SSID is still present though.

All still works find when I boot to Vista.

Any help, guidance, suggestions, pointers ... etc will be appreciated.

---

### Post by starcannon on 2008-08-09
I'd choose a mini pcie card from the known working wifi card list, go to ebay and replace that broadcom. I have yet to see ndiswrapper cards that didn't cause intermittent grief. I know, some out there can administer them just fine, but this sounds like a case where the end-user is going to be bothered by it frequently, and the techie is going to get calls regularly on it. Worst case scenario is you pay for the card yourself if need be, and cut your losses by not having to put in 20 hours of phone support per week.

Just my 2 cents, and at the rate of inflation I probably owe someone an apology.

P.S. Naturally, you likely have an atheros card, I think thats whats in the dv2000's i'd have to go look to be certain, but thats what I'm remembering, you should work outta the box, I have one and no issues at all. If yours is not a broadcom you should search your particular card/chipset, or start a new thread, hijacking isn't generally considered polite (just an fyi, not harshing on you)

---

### Post by Naturally on 2008-08-09
> **starcannon said:**
> I'd choose a mini pcie card from the known working wifi card list, go to ebay and replace that broadcom. I have yet to see ndiswrapper cards that didn't cause intermittent grief. I know, some out there can administer them just fine, but this sounds like a case where the end-user is going to be bothered by it frequently, and the techie is going to get calls regularly on it. Worst case scenario is you pay for the card yourself if need be, and cut your losses by not having to put in 20 hours of phone support per week.

Just my 2 cents, and at the rate of inflation I probably owe someone an apology.

P.S. Naturally, you likely have an atheros card, I think thats whats in the dv2000's i'd have to go look to be certain, but thats what I'm remembering, you should work outta the box, I have one and no issues at all. If yours is not a broadcom you should search your particular card/chipset, or start a new thread, hijacking isn't generally considered polite (just an fyi, not harshing on you)


Thanks for the information and the hint.

I did not realise that it was bad form to put in my issues.

My Apologies.

I will check on the card type and start a new thread.

---

### Post by ENS on 2010-08-30
hi i got the same problem with my hp pavilion dv6000 i've just change my pc from windows to ubuntu (lucyd) and it was working fine but as some of you said i just stopped working i notice that the light in the switch do not turn to blue (working fine signal) it stays in orange (not working signal or off signal) besides in the task bar where its located the wireless icon it shows that its off with an exclamation sign so i know its not working i tried to reset the drivers for the wireless card or something (I'm new in ubuntu ) but i did;t find how to do it or how to fix the problem, so what i did it was a power cycle my computer on, took the battery and disconnect from the power supply i waited some seconds and put the battery and plugged back to source and it started to work again i do not know why but it works and now I'm trying to find a solution not just doing power supplies all times that this happens so? did you find somehow to fix the problem or any recommendations

---

### Post by gfd_2 on 2010-10-01
Same issue... HP Pavilion dv6500 for which wireless card worked great until this morning. I did install a partial upgrade last night.  Any idea how to revert a "partial upgrade"? 

Thanks in advance.

---

### Post by gfd_2 on 2010-10-01
OK here we go... on 09/29 the  wireless card in my HP Pavilion dv6500  was working fine. Afer installing a partial upgrade I shut down for the night and when I started up on 10/01 – no wireless. 

Not knowing how to revert a partial upgrade I looked through the forums and it seems that this isn't an uncommon issue.... LEAVE THE WIRELESS ALONE1

Any way, I found a thread with a similar issue and here's what resolved my problem:

1.)System/ Admin/ Synaptic
2.)Download and mark for installation and install the bcmwl-kernel-source
3.)System/ Admin/ Hardware Drivers
4.)Inactivate the Broadcom STA wireless driver 
5.)reboot.
6.)System/ Admin/ Hardware Drivers.
7.)Mark the Broadcom STA wireless driver as Active.
8.)Your little yellow light should turn blue.
9.)I couldn't force the connection at this time, I rebooted and viola – the wireless connection was established. 
Hope this works for you

---

