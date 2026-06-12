---
title: "Skypephone s2 as Modem?"
date: 2008-10-02
forum: Hardware
---

### Post by spegru on 2008-10-02
I just got an Three Skypephone S2, ( [http://www.three.co.uk/personal/mobiles_/discover.omp?CID=1218698836875&PAYG=true](http://www.three.co.uk/personal/mobiles_/discover.omp?CID=1218698836875&PAYG=true)) which is also able to be a 3G dongle.
It contains an embedded CD image for windows software (just like other 3G dongles from Three). It also has bluetooth and USB and can apparently  connect as modem using either.

I've connected via usb to my ubuntu hardy PC and it can access either the internal CD image or the memory card if the phone is set to USB mode

Anyone had any luck on this device as a 3G modem for Linux? - especially via bluetooth?

spegru

---

### Post by spegru on 2008-10-03
bump

---

### Post by spegru on 2008-10-10
bump

---

### Post by darkteckno on 2008-11-22
Bump...........

---

### Post by spegru on 2008-11-23
In fact connecting via cable would also be good.

I tried this using the new mobile network tools in Intrepid.
Although it detect my Huawei E220 modem automatically, it does not do anything with the Skypephone S2 except to say there is some (windows) software that wants to run automatically (which is also what the E220 normally wants to do - and has to be blocked in order to allow the modem to work under Hardy)

It does work fine as a 3g modem under windows by the way.

spegru

---

### Post by spegru on 2008-12-01
Bump again

I was under the impression that these things were all fairly standard - obeying traditional AT commands etc. Of course there may be the neccessity to block the virtual CD that tries to auto run (as there is in the Huaw i E220), but even that should be unneccessary with bluetooth.

Is there a way to run these things in windows, and sniff out the command  messages to see what is required?

C'mon someone please? it can't be that hard and there are sure to be loads of these 3g things out there............

---

### Post by mjwhitfield on 2008-12-29
Has anyone had any luck with this? I'm planning on getting an S2 and it would be nice to have this working.

---

### Post by spegru on 2009-01-02
I've done it - using my Skypephone S2 as a 3g modem via Bluetooth!
Thanks to this site [http://tanere.blogspot.com/2008/11/mobile-broadband-over-bluetooth-on.html](http://tanere.blogspot.com/2008/11/mobile-broadband-over-bluetooth-on.html) and the comments from Emir Taner.
It's not specifically for the Skypephone but just as I hoped, the S2 is pretty standard.
**EDIT**  The key to it was installing Blueman. It offers much more control over the bluetooth functionality.
In order to install it you have to add the following repositories, (using System>Administration>Software Sources>Third Party Software, and Add): 
deb [http://ppa.launchpad.net/blueman/ubuntu](http://ppa.launchpad.net/blueman/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/blueman/ubuntu](http://ppa.launchpad.net/blueman/ubuntu) intrepid main

Once you have installed Blueman you can use it to set up a serial link service on bluetooth (presumably this is equivalent the usb) between the pc and the phone - and of course accept whatever authorisation requests are asked for by the phone.

It's also necessary to set up the Skypephone to be a bluetooth modem from Menu>Settings>Connectivity>Mobile modem connection> via bluetooth

You also set up a new Mobile broadband service from system>preferences>network configuration> mobile Broadband

The  name of the network should be 3 and the APN should be set to three.co.uk
**edit:** User name is Three and password is also Three
The new mobile broadband service should then appear as an option - 3, against the bluetooth address of the phone (couldn't find a way of showing the friendly name so it only shows as a hex address - If you have two mobile broadband options as I do, then both services will appear against both bluetooth addresses, but it's not too hard to remember which is which)

So just select and connect - the connection is then confirmed just as with any other network

However what confused me at first was that when connected, although Skype would go through from the PC, I couldn't get any websites. However it seems that this is because Three's DNS servers are rubbish, unreliable/slow (I have noticed the same problem with my Asus 701 and 3g dongle). DNS is used fo convert from  website name to an IP address - so it's vital for web use.

So to solve this I selected an alternative DNS called OpenDNS. (I didnt realise you could use an alternative DNS, but it seems you can). 
From system>preferences>network configuration> mobile Broadband edit the IPv4 settings and set DNS Servers to 208.67.222.222 , 208.67.220.220 

So it all works fine now and it's a heck of alot more convenient to use a bluetooth connection to the phone in my pocket than using an external dongle. I will definitely cancel my subscription for the usb dongle asap

Regards & Happy New Year
spegru

---

### Post by raver31 on 2009-01-12
I have one of these excellent phones. They are simply to use under ANY Linux distro, simply plug in a USB cable, install gnome-network-manager and click the Mobile Broadband. It gives you country option and provider, then left click the network manager tray icon and your provider is in there...

---

### Post by spegru on 2009-01-12
That's interesting. I began to try this on ubuntu hardy and did not retry the cable method after I upgraded to intrepid which has the new network manager, now with 3G devices capability

However I did just try it without any success - No modem popped up under network manager

Could you explain what you did in a bit more detail?


thanks

---

### Post by spegru on 2009-02-02
bump

---

### Post by spegru on 2009-02-16
bump
I'd still like to know how to use the wired connection

---

### Post by darkteckno on 2009-02-16
> **raver31 said:**
> I have one of these excellent phones. They are simply to use under ANY Linux distro, simply plug in a USB cable, install gnome-network-manager and click the Mobile Broadband. It gives you country option and provider, then left click the network manager tray icon and your provider is in there...

Your full of sh!t.

---

### Post by spegru on 2009-02-17
I thought you were talking to  me for a moment!
Still not very nice though

I can certainly confirm that the cable solution does not work for me simply as raver31 said.

I'd like to be able to do that though!

---

### Post by darkteckno on 2009-03-30
> **spegru said:**
> I thought you were talking to  me for a moment!


Nope, the fact I did not quote you may have been the give away...

---

### Post by benoid.hosek on 2009-11-10
Hey,
I bought my skypephone s2 in September but just a week ago changed system to ubuntu.
I got the mobile internet to work through usb trying hlaf a billion ways e.g. with usb_modeswitcher. What works for me is this: after connecting my skypephone through the usb cable, it loads the skypephone data cd. Then type this:

```
 sudo modprobe usbserial vendor=0x1614 product=0x0407
```vendor and product id you can find by typing ```
lsusb -v
``` after doing that it just pops in my network manager and I can surf!

Good luck for anyone else trying.

---

### Post by spegru on 2009-11-21
Interesting.
I always wondered why the windows autorun program does not interfere with windows itself. 
I also had this problem with a ZTE (not Huawei) 3G dongle from Three. That required a special AT command to set the dongle to prevent the autorun prog so that the modem could work.
It seems to be a similar problem with the skypephone.

So it seems from your success that the action of loading the usb serial module was enough.
I shall try it shortly
I'd still like to understand why the autorun does not pop up every time in windows. Maybe it is doing something similar........

---

### Post by afspeter on 2010-02-21
**3 skypephone S2 & INQ1 bluetooth modem on Linux  UBUNTU 9.10**


[http://www.youtube.com/watch?v=kzRRfQVhZyg](http://www.youtube.com/watch?v=kzRRfQVhZyg)

---

### Post by mimimi on 2010-02-22
Hi 
 I have just installed ubuntu and encountered the same problem of getting my skypephone to work as the modem. 

Ive got it semi working, what i did was install this usb mode switch program

[URL="http://http://packages.ubuntu.com/karmic/i386/usb-modeswitch/download"]http://packages.ubuntu.com/karmic/i386/usb-modeswitch/download
[/URL]
Then i ran this command

> sudo modprobe usbserial vendor=0x1614 product=0x0407After doing this network manager picked up the phone/modem and automatically connected.

The only problem i am having is that i have to run the sudo command above in order to get online every time i start up the computer? any info on how to fix this would be great.

---

### Post by hoppipolla on 2010-05-20
> **benoid.hosek said:**
> Hey,
I bought my skypephone s2 in September but just a week ago changed system to ubuntu.
I got the mobile internet to work through usb trying hlaf a billion ways e.g. with usb_modeswitcher. What works for me is this: after connecting my skypephone through the usb cable, it loads the skypephone data cd. Then type this:

```
 sudo modprobe usbserial vendor=0x1614 product=0x0407
```vendor and product id you can find by typing ```
lsusb -v
``` after doing that it just pops in my network manager and I can surf!

Good luck for anyone else trying.

heya just wondering if anyone can help me too, I'm trying this but it still isn't coming up at least not on Lucid. I put in the correct product and vendor ids.. I wonder what I'm doing wrong :(

Also am I right in saying usb_modeswitch is not needed as the device offers you the option to select mode upon connecting it? I simply select "PC Suite" as opposed to "Memory Card Transfer" as that's what appears to load the S2 Driver Disc.. o.O

---

### Post by hoppipolla on 2010-05-20
bump! :)

---

### Post by spegru on 2010-12-11
Slow response......

I just had to get this going again with Mint9 (Ubuntu 10.04 based).
Still works!

Make sure to include the 0x bit in front of the USB ID numbers though. (they don't appear in lsusb responses)

Also if you are in a poor coverage area (this is 3 after all) it wont work. If the phone appears in your connection list it is job done as far as linux is concerned, but it wont fix signal strength!

---

### Post by spegru on 2011-01-25
now I am confused.
I just tried this again using Mint 9 (ubuntu 10.04 based) and Mint10 (ubuntu 10.10 based)

On Mint 10 it doesnt work
and When I do lsusb the code is wrong too, 
It says
Bus 002 Device 010: ID 1614:1000 Amoi Electronics

But on Mint 9 it still works 
It says 
Bus 002 Device 010: ID 1614:0407 Amoi Electronics
as before

I wonder if this is to do with the power capability of the mint10 laptop being lower.....

---

### Post by spegru on 2011-01-25
No I don't think that USB power is the problem as I've just tried it on another Mint10 machine with a mains powered usb hub.
Why should the USB ID change?
I am guessing that this must affect Ubuntu 10.10 as well

---

### Post by spegru on 2011-01-28
I read in some other forums that you can get different USB IDs if you plug in several times. I didnt try that yet but I will this weekend I hope.
I guess this has something to do with the different USB modes that are available such as PC suite, USB disc drive etc

However in any case this sounds very crude. Surely there must be some command that can be sent to the phone to force it into the right mode and therefore the right USB ID.

Windows must have the same problem. How do they do it?

---

### Post by spegru on 2011-01-28
I read in some other forums that you can get different USB IDs if you plug in several times. I didnt try that yet but I will this weekend I hope.
I guess this has something to do with the different USB modes that are available such as PC suite, USB disc drive etc

However in any case this sounds very crude. Surely there must be some command that can be sent to the phone to force it into the right mode and therefore the right USB ID.

Windows must have the same problem. How do they do it?

---

### Post by jamesmorton on 2011-03-03
Hello.

I'm having a similar experience as others.  I've previously - under Ubuntu 9.10 I think - had the ability to use my S2 as a modem using the modprobe usbserial vendor=0x1614 product=0x0407 command. Then this seemed to stop working for me - I think due to a kernel upgrade.

The current situation is that on a laptop running 10.04 it's working perfectly again - I just plug in and it goes (with lsusb showing the S2 as 1614:0407). However, on a netbook running 10.10 I ca't get it to work at all. Lsusb shows the S2 as 1614:1000 - and no amount of plugging/unplugging, switching on/off or anything I can think of seems to get it to switch to 1614:0407. It's very frustrating as this is the machine I really need a mobile connection with.

Can anyone explain why two versions should have this difference, and suggest whether there is a way of forcing the S2 to switch?

Thanks very much

---

### Post by spegru on 2011-03-21
bump

---

### Post by spegru on 2011-03-29
Having a few problems with this now that I upgraded to Mint10 (Ubuntu 10.10)

a) USB doesnt work any more: lsusb always reveals the wrong ID - 1614:1000 instead of 1614:0407 like it used to in previous versions. What is the difference between 10.10/M10 that causes this behaviour to be different? There has to be some command to force it into modem mode.

b) Bletooth tethering no longer seems to work either. I used the standard bluetooth manager but it doesn't recognise the device as a DUN modem. I used Blueman, which does, but then the option doesnt appear in network manager.
I even tried some manual command line stuff but that didnt work either.
And all the time my Nokia N810 tablet tethers to the same phone without any problem



An extra point about Bluetooth connection is that it appears there is a small bug in the phone so that when you send it a pairing request with code, it seems to think it needs to generate a code of its own instead of confirming the code - so registration never works PC to phone, you have to do it phone to PC instead. But does this make any difference to Bluetooth service discovery?

---

### Post by spegru on 2011-03-31
bump

---

### Post by spegru on 2011-04-02
Made some progress on the bluetooth side.
However I am not 100% sure what happened

It appears that Blueman works with a series of plugins that you can access by right clicking in the task bar icon. The plugins control many things via dbus service announcements. However it looks like there may be some plugin problem between Blueman and Network Manager. That seems to be why, you dont get any bluetooth internet connection listed under network manager even when you add the phone to the bluetooth list and Blueman recognises it as phone. It also may explain why, after adding the phone from blueman and right clicking on the phone and select serial > ports Dial up networking, you get an error message about modem-manager.

So what I did was to go into the blueman plugins and disable NMPANsupport and NMDUNsupport since those were listed as having conflicts with NMIntegration and PPPsupport.
After I did that, right clicking on the phone from Blueman and selecting Serial>Dialup still brought up an error, so I deleted the phone, restarted the PC and the phone and re-added it. This time, when selecting dialup there was an extra box  'dialup settings' that I had never seen before. In there goes the dial number *99# as usual and the APN of the network operator, which since I am on 3 is ThreeUK.

So now when right clicking the phone from blueman and selecting serial ports > dial up networking it actually works! 

You can tell something changed because when connected the blueman icon gains a little green blob! 
Network Manager still can't understand what is happening but at least there is a connection!

Slightly clunky but it works

Anyone who can get this working with Network Manager, or indeed understands how bluetooth pairing and service detection really works pls let me know. My guess is that this applies to the tethering of many other bluetooth phones

Now for that USB ID problem......

---

### Post by kingofswords on 2011-04-02
does this not work then? ive spend hours trying to do the sudo cmd with the usb app.

blue tooth isnt an opion for me but ive just installed ubuntu for the 1st time but the s2 is my only source for internet but seems im better off going back to windows?

how come some ppl say they had it working while others cant?

im on ubuntu 9.04 or soethiong btw.

cheers
james

---

### Post by spegru on 2011-04-03
In fact conncting to the internet using this phoone has mostly been quite good. The problem i have been having is with Ubuntu 10.10/ Mint10. If you are using something earlier then it could well be quite fine.
However a small bit of command line stuff may be required.
Try this: open a terminal and type lsusb. If you see the phone listed as an Amoi device with following ID
 the following you are probably ok.

 Bus 002 Device 010: ID 1614:0407 Amoi Electronic

  ..............Note the 0407 part.

If you do see that then type this (complete with those odd looking 0x bits)

 sudo modprobe usbserial vendor=0x1614 product=0x0407

Once you have done that the phone should appear under network manager. If that happens you then have to put in the details of your mobile network using the wizard and it should work fine as long as there is nework coverage.


You could try bluetooth though....USB adaptors are cheap enough and once working it's easier if anything. If you try it I suggest installing Blueman, and looking back into the older parts of this thread to see how to use it

---

### Post by kingofswords on 2011-04-05
nah bluetooth isnt an opion as the phones display has gone.

anyway im using 9.04 i think and have typed the sudo cmd a toiusand times and have had no luck in its coming up in the network manager.

ive even dled and installed the usbmodswitch programmme with no effect.

so what am i doing wrong?
yeh whn i typ lsusb i get 1614 for the vendor and 0907 for the product(think that is standard) but it isnt connecting?

---

### Post by spegru on 2011-04-06
I'm guessing that ID is really 1614:0407 Amoi Electronic
In which case that is the correct one.

Did you do this?
sudo modprobe usbserial vendor=0x1614 product=0x0407

If you do it should appear in network manager.....

If it doesn't it might be worth trying a newer live CD session to eliminate possible stuff you broke... such as for 10.04 (but not 10.10 as even I'm having problems with that one)

Hold on though another thought: You may have to put the phone modem into USB mode. It might be in Bluetooth mode right now...
On the phone: Menu>settings>connectivity>mobile modem connection> select USB

Mind you, if your display is broken there's not alot you can do about that.....

---

### Post by kingofswords on 2011-04-07
sorry meant to say 0407 and not 0907.

anyway got this working yesterday with the sudo cmd and everything was working find but now ive tried this morning and its suddenly stooped working. i was getting slow internet last nitght so was tring to disable the ivp6 but i couldnt it, do you think this has stoped me connecting

i nearly fainted, couldnt believe i got it working, i didnt try anything new so have no idea why it suddenly started working.

btw i thought anything past ver9 didnt work with the s2 thats why i got ver 9.04

---

### Post by kingofswords on 2011-04-07
ok back online now...but my internet speed is really slow....a quater of what it is in windows. before anyone suggest it..yes my ivp6 is disabled.

anybody got any ideas.

this linux seems to be a ferrerai with no wheels.

---

### Post by spegru on 2011-04-08
Great that you got it working.
However speed is very unlikely to be altered by linux vs. Winows.
Much much more likely it's the network  coverage, 

or just possibly (but only if you are using a different physical pc or at least usb  port), you only have usb 1 on one compared to usb 2 ports on the other

I think this usb modem stuff has been working in an integrated way with network manager since about 8.04
the only problem is because of these integrated virtual cds for windows that sometimes get in the way and hence usb modeswitch etc. With my 10.10 I do have a remaining problem with this phone but that only happened in that version and I'm not sure why - but the issue is that I get the wrong usb id.

---

### Post by kingofswords on 2011-04-08
with mint 9 i sometimes get the 1614/1000 usb ids, i just lsusb first and adjust the sudo cmd according and it then connects.

anyway i have;
**LAPTOP A**1.5ghz 256mbram i broken screen and deing harddrive with loads of virus that i cant get rid and xp!

**LAPTOP B**2.4 duo core 4gb ram ssd hdd and im guessing newest usb2.0 with ubuntu 9.1 and then mint 9.

i run speedtest.net on laptop A and get 2meg dl all the time the pull out usb and connect laptop B the always give me 0.49meg.then swapped back to laptop A and tried again for a few times.

so surely this is a linux issue.

everybody i spoken to sounds like they think im mad. i have read nurmous posts about ppl having the same issue in 9.1 ubuntu.
its to do with ivp6 conflicts and in 9.1 ipv6 has to be disabled with kernal.
ive seemd to disabled the kernal but still have slow internt.

ive got no idea how to sort this out but have dled 10.04.2 ubuntu and now having problems installing that from usb so not really liking my linux experience so far.


anyway i read 'connections properties' that the phone was gsm...even the it should be 3g so do you think perhaps linux or the modswitch program is switching it over to gsm and hence the slow speed?

if i get it sorted and it still persist will more than likely go back to windows.

---

### Post by spegru on 2011-04-10
Been doing some work on this. Will get back in a bit

---

### Post by kingofswords on 2011-04-11
omg finally sorted out my internet(after days of messing and headbangin). a couple of days ago.
for some reason karmic and mint 9 restricted my net speed so switched to 10.04(thought i read 10.10 doesnt work with s2)?

i nearly fainted i was so delighted,for some reason i dont even have to unmount and sudo cmd it does it all automaticly when i plug in phone.

i have been disconnected a lot today and had downtime, i guess this must be 3 network thou.

btw the way if you get 1614/1000 for the usb ids..cant you just type those numbers in?

anyway thx for all your help, really appreiate it.:popcorn:

---

### Post by spegru on 2011-04-13
I did a few speed tests although the results are not entirely conclusive
I tried to maintain the same position in the house (upstairs in our none too good Three UK coverage area).

First I tried a USB dongle modem (Huawei E169G)
This works in Linux without any need for drivers etc you just have to follow the wizard to set up yur operator details - just the once (and luckily for me it just defaults to 3 as that's even lower in the ASCII alphabet than A). After you do that, as long as the dongle is plugged in it appears as an option in Network Manager. In Windows the virtualCD thing runs and installs a big friendly window thing with a connect button that does the same job (in a more intrusive way)

Speed Results:
Windows7: ~1Mb/s
Linux (Mint10/Ubuntu10.10): ~1Mb/s


So in this case the OS made no difference - tallying with my understanding that the phone/modem does all the work and the OS is irrelevant.

Next I tried the Skype phone, and got some very different speed results.

Linux connected by bluetooth using Blueman as previously discussed: 0.5Mb/s
(not able to connect by USB due to inability to get the correct USB ID as previously discussed)
Windows7 connected by USB after running the virtualCD that installed another, different big window thing: 2.5Mb/s - alot faster
(not able to connect by bluetooth because I dont know how to do that)

So yes I also saw a big difference in speed between Linux and Windows - but only on the Skypehone. Unfortunately for the test, the connection to the phone was different between OSs, and it may be that bluetooth is the slowest link in the chain.

The difference in speed between the Dongle Modem and the Skypephone is probably simply because the phone has a higher spec radio than the dongle.

I really must get the USB connection to Skypephone sorted out to complete this. However I maintain that the phone or dongle does all the work to connect to the mobile network and the OS is irrelevant. Bluetooth and USB are basically the same thing as far as the PC is concerned.

That modprobe thing is also clunky. I am sure we could do better than this!

---

### Post by spegru on 2011-04-13
For some reason I just typed my previous answer before noticing that you (kingofswords) had already responded!

I'd be interested whether you are sure that Mint9 restricted speed: Was all the hardware and the position the same? Mint9 is based on 10.04 so they should be the same for this.

The problem with the sudo modprobe thing in Mint10/10.10 is that if the correct USB ID is not visible to the system it is no good sending the commend to a device that does not exist!

So you managed to get it working in 10.04! I suppose you get the correct USB ID? I wonder if my problem is hardware related? I am also running 64bit - I wonder if that matters.....?

I also wonder if a newer Bluetooth3 dongle would help speed things up....

---

### Post by spegru on 2011-04-14
I just tried the speed test again with a Bluetooth 3 adaptor.
I got exactly the same speed test as before.
However, whether it was really running as Bluetooth 3 depends on what kind of Bluetooth is in the phone..

So I really need to get the Wrong USB ID problem sorted and/or to know how to to bluetooth tethering windows in order to get a proper understanding o f the dramatic speed difference

How does Windows get round the VirtualCD problem?

---

### Post by kingofswords on 2011-04-14
hi 

really enjoying linux now i got it sorted...just installed wine which is a great prog.

im a linux newbie so dont take y advice as gospel(althout these problems have probably taught me a thing or2).

its wierd as 9.1(karmic) slowed net down and really strange that i tried mint 9(10.04) and did same thing but when i tried ubuntu 10.04 it sorted problem out so i dont really know other than perhaps try out ubunutu! in fact i think linux even speeds things up a little as i was getting 2.8 at one point last night and im usually 2meg give or take a little. read of ppl actually getting 3-4meg(lucky £$%&).
my internet has actually vastly improved since switched to payg ayce as well as not nearly as many disconnection and downtime, although alas my s2 is on its way out(as i said b4 screen broken) and it need to be heated up in front of heater for a hr or so b4 it connects(lose wire or s'thing). so just use as  a modem at moment.

spegru some times i get 1614|0407 others i get 1614|1000 for the usb ids i dont think it makes difference. but i dont need to type modprobe cmd in so never check anymore.i presume you could just type lsusb b4 typing to get correct numbers.

spegru ? have you tried connecting in wine? perhaps that will give different results? i installed s2 driver earlier and it worked.

good luck james

---

### Post by steves12 on 2011-06-08
All of your replies sound really hard work!!! the easyest way i have found with most 3g dongles and the ZTE phones after you have set up the vpn connection to 3internet all you have to do is go to places, right  click on the 3conect icon select eject, then the dongle will connect straight away, that is if you set it to connect automatically, if not just click the network icon and hit connectl, hope this helps its really easy, but for some reason this does not seam to work with the s2 skypephone. well it may im just really impatient and got bored.

---

### Post by spegru on 2012-02-05
Weirdly perhaps I am still trying to do modem connection via cable several months later. Yes bluetooth works but it's a bit flaky

I am now using Mint 12 - based on Ubuntu 11.10

Key to this is the USB ID
when I lsusb I get  - 1614:1000   which is the virtual CD
I cant seem to eject the Virtual CD no matter what I do


However some time ago I was using Mint 8 - based on Ubuntu 9.10 I think

when I boot into that (even today), I get the usb ID  -  1614:0407   - which is the modem - at least about half of the time that I connect


Why should the USB ID depend on the Linux Version  - and therefore how can I change it?

---

### Post by spegru on 2012-02-06
Made some good progress with this

I have XP installed in virtualbox so I gave it access to the skypephone by adding it from the list of possible USB interfaces.

When I did this the USB ID changed from 1614:1000 to 1614:0407 which is the one I want!  
I did not install the windows software from the virtual CD. In fact that option did not even appear so far. So this seems to be a pure windows thing.

I noticed that if the skypephone was already plugged in when the VirtualXp was started, this did not happen, but when plugged in when the virtualXP was already running, then it did. The XP made two noises - Bong Bing, followed by Bing Bong (If you can understand that!) - does that sound like it was detected and then disconnected?

After the USB ID changed I can close the VirtualXP and the USB ID stays as 1614:0407.

Then I added the new USB ID using 
sudo modprobe usbserial vendor=0x1614 product=0x0407

Voila! The phone is now available as a usb modem from network manager!
It works - that is how I am posting this!

OK so now for finding out what windows did to achieve the change to the USB ID. I dont really want to have to use virtualbox xp every time. I am wondering if wireshark can tell us something useful

---

### Post by spegru on 2012-02-06
A bit of an update


I just set this up again on another PC and this time I noticed that the Skypephone installsheild wizard did in fact run - automatically. It must have been hidden behind another window when I did it before. It was after this that the 'ding dong' happened. therefoe it looks like it is something specifically installed rather than being purely windows after all.

By the way I also had to add myself to the vboxusers group before I could add access any USB devices from virtualbox

Oh yes, for completeness (although this may not be of interest to ubuntu users) I also added an extra admin application before I could access the groups from Mint 12 - like this: sudo apt-get install gnome-system-tools . Another way of doing it is to type: sudo gpasswd -a USERNAME vboxusers

---

### Post by spegru on 2012-02-07
Since I'm on Mint really I'm now moving over to mint forums on this matter

You can find the thread here
[http://forums.linuxmint.com/viewtopic.php?f=49&t=93790&p=538444#p538444](http://forums.linuxmint.com/viewtopic.php?f=49&t=93790&p=538444#p538444)

However you might be interested to see the latest so I'm double posting this...

I used wireshark yesterday to snoop the messages coming out of windows. XP was running in virtualbox. To be honest this was easier than having a physical XP machine!

It seems XP mounts (Dong Ding) and then unmounts (Ding Dong) the virtual CD before the correct ISB ID is shown.
Wireshark (which has to be run as root) is able to see all the messages from the selected USB port. After some experimentation I also used a filter to show only scsi commands.

Well the command that seems to permanently eject the virtual CD is this one:

805 9.990000 host 40.5 USBMS SCSI Command: 0x2b LUN:0x00. 
(This is how wireshark shows it although it may be binary in fact as there is a second window - I am no wireshark expert....)

Anyone know how to get linux to do that?

---

