---
title: "Laptop review: Lenovo ThinkPad SL500"
date: 2009-04-25
forum: Hardware
---

### Post by some_random_noob on 2009-04-25
I installed 9.04 on the Lenovo ThinkPad SL500. Most things work, however:

**Atheros PCIe Wireless...**

It works with the default drivers, but only gets around 20% reception, compared with 50% in Vista. Maybe I should try MadWifi from the repos.

**Bluetooth module...**

Does not work yet... I've wasted about $100 on the BlueTooth Module and mouse, so hopefully I can get it going. But so far, the mouse can't be detected.

**Hotkeys and function key...**

These don't work, and I have yet to try the experimental driver.

---

### Post by redpointpete on 2009-05-01
I also have a SL500 with Ubuntu 9.04 It took a while but everything that I can test is working (ie. fingerprint, wireless, screen brightness with hotkey buttons, trackpoint scrolling) I don't have any hardware to test the card reader, the firewire, or the HDMI out. I am very happy with this laptop now that it is working properly. I would be happy to help as much as I can if anyone is also trying to get their SL model working. I have attached a screenshot of Ubuntu on my SL500

---

### Post by michalzuber on 2009-05-04
@redpointpete Cool conky (I think it's it) Do you know how to turn on the wifi without restarting? I mean when I turn it on the LED isn't on and after restart the Wifi works fine. Please could you give some info how did you manage that your bluetooth and webcam(I tried it in Cheese, the green light is on but no picture :P) work. I solved the acpi and the FN keys problems. Big thanks for your info ;)

---

### Post by johnjust on 2009-05-04
I just got my Lenovo SL500 today, and installed 9.04, but not too much is working...

The brightness wont increase above 2 notches, I'm trying the nvidia driver now, but something tells me it wont work.

How did you get your brightness to work?

---

### Post by redpointpete on 2009-05-04
I don't have the webcam or bluetooth. I just noticed the wifi issue today that you write about. I have never switched the wifi switch on the front before but I noticed that if you power on with the switch in the on position and then turn it off it will work as intended. This has been my best experience with Ubuntu yet.

---

### Post by redpointpete on 2009-05-04
> **johnjust said:**
> I just got my Lenovo SL500 today, and installed 9.04, but not too much is working...

The brightness wont increase above 2 notches, I'm trying the nvidia driver now, but something tells me it wont work.

How did you get your brightness to work?

___________________________________________________

Start with this page: [http://www.linlap.com/wiki/Lenovo+Thinkpad+SL500](http://www.linlap.com/wiki/Lenovo+Thinkpad+SL500)   It was a huge help in getting all the hardware to work. This really is a great laptop once you get it working.

---

### Post by michalzuber on 2009-05-05
> **johnjust said:**
> I just got my Lenovo SL500 today, and installed 9.04, but not too much is working...

The brightness wont increase above 2 notches, I'm trying the nvidia driver now, but something tells me it wont work.

How did you get your brightness to work?

Hi. I made it with this great tutorial at [http://gianlucamagalotti.wordpress.com/2009/02/16/lenovo-thinkpad-sl-series-hotkeys/](http://gianlucamagalotti.wordpress.com/2009/02/16/lenovo-thinkpad-sl-series-hotkeys/)
I made a Slovak translation available at [http://michalzuber.blogspot.com/2009/05/nastavenie-lenovo-thinkpad-sl-klaves.html](http://michalzuber.blogspot.com/2009/05/nastavenie-lenovo-thinkpad-sl-klaves.html)
Big thanks to Alexandre Rostovtsev and Gianluca Magalotti

---

### Post by michalzuber on 2009-05-05
> **redpointpete said:**
> I don't have the webcam or bluetooth. I just noticed the wifi issue today that you write about. I have never switched the wifi switch on the front before but I noticed that if you power on with the switch in the on position and then turn it off it will work as intended. This has been my best experience with Ubuntu yet.

After my post I tried to turn Wifi on and tried to set wifi in NetworkManager and it worked, but it didn't scan for wifi networks. After a while the LED went up, but don't know what i did :P I searched after bluetooth setting, but no solution found. I have the server kernel due 4GB of RAM and all BT modules are compiled, but in the lspci and lsusb there is no bluetooth device, so my conclusion is that it doesn't know about the bluetooth HW. Do you know what kind of HW could it be. On the net there is just BlueTooth 2.0 EDR but no producer and in the /lib/modules/ are just some code names for BT modules.

---

### Post by some_random_noob on 2009-05-07
Hi guys,

Just letting everyone know that my BlueTooth (thinkpad branded) mouse DOES in fact work. I fluffed around a bit and entered the pin number for it (which is on the bottom of the mouse, 0309). Everything works out of the box. Only a few things to ponder:

[LIST]
[*]How the heck do I change contrast? My monitor can't display faint shades of yellow very well (Vista did it better). Also, I think Ubuntu is forgetting my brightness settings.

[*]Hotkeys?????? Gosh I'm not sure if I want to try the experimental drivers...

[*]When will the drivers catch up with Windows versions? My wireless goes between 20-40% all the time, which is kind of annoying as I certainly feel the performance drop a bit.

[*]Do suspend and hibernate work? (haven't tried yet, and don't really plan to).
[/LIST]

---

### Post by CompBio on 2009-06-17
> **redpointpete said:**
> ___________________________________________________

Start with this page: [http://www.linlap.com/wiki/Lenovo+Thinkpad+SL500](http://www.linlap.com/wiki/Lenovo+Thinkpad+SL500)   It was a huge help in getting all the hardware to work. This really is a great laptop once you get it working.

All the tutorials I've seen say compile the program using make.  I've tried "make", "make all" and "make lenovo-sl-laptop".  Only the last command does anything, and it spews a ton of error messages.

I started trying to debug the thing, but it claims it can't find include files such as linux/module.h, even though the file exists.

I'm not a C expert by a long shot, so I have no idea what to do at this point.  Below is an example of a make run.

EDIT: I found the problem -- the Makefile I downloaded directly from the website did not have valid TABs.  Once I fixed that problem, and figured out how to add the commands to a boot script, it works fine.

---

### Post by nadeepa on 2009-06-21
Just received my new SL500 yesterday. Tested with Jaunty live CD. Almost everything works except sound up/down/mute buttons. I did not tested media card reader or HDMI. Hope everything will be fine after proper install. Just waiting to do Vista backup, just in case I wanted to sell it.

---

### Post by mbuller10 on 2009-06-26
Hey to all of those with a thinkpad sl500 and a nvidia geforce 105m graphics card (higher clocked geforce 9300M) i got it working mixing stuff together from random threads

3) sudo apt-get install build-essential

4) gksudo gedit /etc/modules
    4.a) Add "nvidia" without quotes to the list.
    4.b) Save and Exit

5) gksudo gedit /etc/default/linux-restricted-modules-common
    5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
    5.b) Save and Exit

then I went to the synaptic package manager and downloaded all the nvidia 177 stuff

then I went to hardware drivers and clicked on activate the 177 drivers

then I restarted

don't know how it worked but it worked for me on ubuntu 8.10 32 bit

---

### Post by dxxvi on 2009-07-05
> **some_random_noob said:**
> **Atheros PCIe Wireless...**

It works with the default drivers, but only gets around 20% reception, compared with 50% in Vista. Maybe I should try MadWifi from the repos.

Did anybody solve this problem yet? I'm going to have a SL500 soon and I don't want to see Linux is worse than Vista in any aspect :p

---

### Post by sol0 on 2009-07-26
any results?

Im waiting for one with dual core cpu? Did you get it to work?

Hoping to install arch on it else I will run ubuntu.

---

### Post by div3rs on 2009-09-06
hi all,
i own a sl500 laptop with nvidia 9300m gs. Im running ubuntu 9.04 64 Bit. I have some problems with a graphic temperature, if i start a 3d Game like Quake 3 the temperature rises up to 107 °C. When im using nvidia twin view for dual monitors it goes up to 88 °C. Does someone have same problems?

---

### Post by cyberpower on 2009-10-24
hello,i just got a sl500 with vista business.my wifi picks up my router but has only limited access.someone told me to change my ip address but it did not help.in my previous laptop there was no need to change ip and i dont see any need to.can some1 help me as i am getting frustrated.

---

### Post by curlymurly on 2009-10-24
hi every1!
im new to this forum. just got my sl500 and installed jaunty. everythg except sound and brightness keys works from the box. wifi works perfectly. yesterday i updated to karmik beta. everythg looks ok for me, but i have this little annoying problem. i dont know why, but my keyboard started to make sounds, like typing sounds on every letter/digit key press. this really is a bit annoying cos i work a lot with laptop and after 2-3 hrs of this typewriter bangs my head is about to blow ((( tryed googling but i guess not many ppl updated to karmik yet - so i have no luck finding any solution. ((

btw. after updatin to 9.10 brightness problem solved, but sound control keys still not func.

thanx in forward, any help is appreciated.

gl 2 all.

-----------------------------
add: problem solved! it appeared the gxnero i use as a key switcher was making typing sounds even thou sounds were disabled in options. 2 days of karmik, looking good so far.

---

### Post by osaks on 2009-10-25
I bought a new lenovo sl 500 and I installed ubuntu 9.04 first. I think everthing is working but brigthness keys. I cannot change brightness in any case. Then I installed ubuntu 9.10, and it seems everything including brightness keys are working but the problem is my cpu's are working much and fans are emitting too much sound. Anyone with the same problem?

---

### Post by elsealio on 2009-11-13
Hi,

Another SL500 user here, good to see the brightness controls and volume buttons are fixed on 9.10. But I am having trouble with a few things which worked perfectly on 9.04.

I can't get the middle button to work for scrolling, it worked in 9.04 using the following guide:

[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint)

But this doesn't seem to work in the current release.

Suspend/hibernate is not working either, entering these works fine but on resuming the screen is off. A hard reset is needed to fix this. The problem is documented here:

[http://ubuntuforums.org/showthread.php?t=1307618](http://ubuntuforums.org/showthread.php?t=1307618)

Anyone else here have the same problem? I'm not sure if it is model specific or not?

Temperatures seem to be up a little bit from 9.10, on average ~5 degrees Celsius. I'm consistently getting temperatures of: 52 - HDD, 50 - CPU, 60 - GPU. The CPU and GPU are slightly higher than in Vista, but the HDD is consistently 10 degrees higher all the time.

So does any other 9.10 users have similar issues?

edit: the suspend/hibernation can be fixed by updating the nVidia drivers (version 185 in my case).

---

### Post by JohnnyK on 2009-11-14
I've had my SL500 for a while now, and everything works fine (volume controls with the kernel module, rest OOTB) with Karmic. The only small issue I have is that brightness up has no overlay so the display overlay with the brightness symbol and bar do not show up when I increase brightness; brightness is increased though, and the icon and bar do show up when I lower the brightness.

Anyone got this issue as well?

BTW, going off on a tangent, I upgraded from ext3 to ext4 (using [this German tutorial]("http://wiki.ubuntuusers.de/Upgrade_auf_ext4"); a tutorial in English is [here]("http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21"), although the steps are slightly different. I installed grub2 before booting the Live-CD) and boot times about halfed. This is obviously no SL500-specific, but if you did not do a clean Karmic install (and chose ext4 as your filesystem), I would strongly recommend this.

---

