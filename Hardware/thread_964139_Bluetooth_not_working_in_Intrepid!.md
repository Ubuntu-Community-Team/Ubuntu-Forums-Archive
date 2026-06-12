---
title: "Bluetooth not working in Intrepid!"
date: 2008-10-30
forum: Hardware
---

### Post by isecore on 2008-10-30
This is simply a copy & paste of [my thread over in the dev-forum]("http://ubuntuforums.org/showthread.php?t=962254"), now closed since Intrepid has been released. This is still an issue for me, and I would _REALLY_ like to figure out why Bluetooth stopped functioning after upgrade. If you need any information, just let me know. My system is a x64-installation, upgraded from Hardy to Intrepid.

---

After upgrading to Intrepid from Hardy bluetooth no longer works. If I tickle it with a sudo /etc/init.d/bluetooth restart the icon appears but is non-functional. Cannot set the name of my device, can't send files, can't receive files. Nada.

Anyone know anything about this? I filed a [bugreport on Launchpad]("https://bugs.launchpad.net/ubuntu/+bug/289836") but it's seen very little action or response. There's also [another thread]("http://ubuntuforums.org/showthread.php?t=858463") on the forums about this, but there's been no responses for four days and we're getting close to launch soon.

I'm running Intrepid x64, all patched up as of the 29th.

---

### Post by ukblacknight on 2008-10-30
My bluetooth stopped too!  Worked perfectly fine in 8.04, now it won't recognise the device.  It's listed with lsusb.

My dongle is a Belkin F8T009.

I'm running 8.10 (32bit), with all the updates as of 30/10/2008.

Edit:

I also get the same issue when doing the sudo /etc/init.d/bluetooth restart.  The icon appears again, but it's non-functional.  Also, the lsusb output it showing it as a broadcom corp device.

---

### Post by infie on 2008-10-30
Same here! I was using anyremote with my nokia phone and my Sweex usb bluetooth dongle and all was good. But then I finished upgrading to 8.10 and bluetooth stopped working completely....

Edit: When running 'hcitool scan', the phone is visible.. but I can't connect to it...

---

### Post by churchyard on 2008-10-30
Same for me.

---

### Post by gaelfx on 2008-10-30
All right, I'll throw my nickel in too, my bluetooth does not work also, but mine is on a fresh install of Intrepid, the beta version, but fully updated. My issue is this: my bluetooth dongle is recognized, the bluetooth icon seems to function fine, except that the first time I tried to add my mouse, it said it paired successfully, but it did not function. So, I deleted it from the trusted items list in the bluetooth applet and tried to re-add it. This time, and every time thereafter, the pairing has failed.

After some research, I discovered that there is a samll possibility that the problem lies in my lack of sdpd. So my request from all of you with non-functioning bluetooth is this: Is sdpd present in you /usr/sbin/ folder? Could you please check this for me, since we have a few people without functioning bluetooth, it might be helpful to know if this is the source of all of our woes. Thank you.

---

### Post by Dropbear on 2008-10-30
Here as well. The bluetooth applet can see other devices but times out when I try to pair with them. If I pair from the phone it works. I can usually send a file from the phone to the computer but not from the computer to the phone. If I try to send a file via the nautilus menu i get an error. "Obex push file transfer unsupported" even though obex-data-server is running.

To the above poster,   I dont have sdpd in /usr/sbin either

---

### Post by paranoid_humanoid on 2008-10-30
i have the same problem.
my bluetooth adapter is recognized. i tried to pair my nokia phone from the bluez applet but it always failed even though it could see my phone clearly.
i initiated the pairing from my phone and it was fine, paired successfully. but now i can't send anything from my phone to ubuntu. and whenever i try to send a file to my phone from nautilus, it says that "obex push file transfer is not supported".

bluetooth was functioning perfectly in 8.04. i just did a fresh install of intrepid only to find that bluetooth is not working :/
what now?

---

### Post by fierymaelstrom on 2008-10-31
Downloaded and burned Intrepid only to find BT not working. I plugged in a spare kb/mouse and checked the new BT icon; no devices are even listed. It's been working fine in Hardy, of course. :(
Using the Logitech MX5500 set.

---

### Post by ukblacknight on 2008-10-31
> **gaelfx said:**
> All right, I'll throw my nickel in too, my bluetooth does not work also, but mine is on a fresh install of Intrepid, the beta version, but fully updated. My issue is this: my bluetooth dongle is recognized, the bluetooth icon seems to function fine, except that the first time I tried to add my mouse, it said it paired successfully, but it did not function. So, I deleted it from the trusted items list in the bluetooth applet and tried to re-add it. This time, and every time thereafter, the pairing has failed.

After some research, I discovered that there is a samll possibility that the problem lies in my lack of sdpd. So my request from all of you with non-functioning bluetooth is this: Is sdpd present in you /usr/sbin/ folder? Could you please check this for me, since we have a few people without functioning bluetooth, it might be helpful to know if this is the source of all of our woes. Thank you.

sdpd is NOT in my /usr/sbin/ folder.

---

### Post by akai_kenshi on 2008-10-31
My bluetooth works...for a while. I can pair my bluetooth mouse and keyboard beautifully with the new wizard, but after coming back from idle or restarting my laptop, they cease to function. I can only get them to work again by deleting them from the list and pairing them again.

This is a pretty major annoyance for me, as I've grown used to using a bluetooth mouse most of the time. I'm on Intrepid 64-bit.

---

### Post by kszys on 2008-10-31
I installed Intrepid as beta and the bluetooth worked just fine (MS Bluethooth Mouse 5000). Unfortunatelly, it seems that before the final release the bluetooth got "fixed". Although I can still pair the devices, and the bluetooth applet even reports successful device configuration, nothing works :(

---

### Post by jcoenen on 2008-10-31
Same thing over here, installed on an Akoya E1210, flawlessly.
Wifi working via the ndiswrapper. 
Inserted a BT2 USB dongle (sitecom CN-516), mileage varied, at one point I could see devices, but never succeeded to Pair.

---

### Post by churchyard on 2008-10-31
sdpd is NOT anywhere.
hcid is NOT anywhere.

Many of commands disapeared from bluez-utils in intrepid.

---

### Post by euklidis on 2008-10-31
Same problem here. it was working perfectly in 8.04 but now it stoped. i cannot pair my mobile with the pc. if i from my mobile i can pair them but it doesn't work event if they are paired.

---

### Post by isecore on 2008-10-31
I don't have sdpd, although my gut-instinct says that this is much more complicated than a simple file missing.

Again, my bluetooth is completely non-functional. When I login there's no icon in the tray. If I tickle it doing a /etc/init.d/bluetooth restart then the icon appears but is non-functioning. I can open preferences but none of the buttons do anything. Can't pair devices, can't send. Etc etc.

---

### Post by erlguta on 2008-10-31
I have problems to.
I can't send files from my mobile to Intrepid.
In hardy it worked ok.

It seems to be this bug:
[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/283064](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/283064)

---

### Post by isecore on 2008-10-31
> **erlguta said:**
> I have problems to.
I can't send files from my mobile to Intrepid.
In hardy it worked ok.

It seems to be this bug:
[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/283064](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/283064)

I read that bug-report and I refuse to install gnome-user-share. All it does is install Apache, and apparently depends heavily on it. Why would we need to install Apache in order to get bluetooth working? No, not buying it.

---

### Post by ukblacknight on 2008-10-31
> **isecore said:**
> I read that bug-report and I refuse to install gnome-user-share. All it does is install Apache, and apparently depends heavily on it. Why would we need to install Apache in order to get bluetooth working? No, not buying it.

Sending files to my PC from my phone never worked anyway, my phone would just say "Sending failed" instantly, so that's got nothing to do with this.

I'm thinking this is more of a driver issue.

---

### Post by mkarnicki on 2008-10-31
> **kszys said:**
> I installed Intrepid as beta and the bluetooth worked just fine (MS Bluethooth Mouse 5000). Unfortunatelly, it seems that before the final release the bluetooth got "fixed". Although I can still pair the devices, and the bluetooth applet even reports successful device configuration, nothing works :(

Just yesterday I made a fresh install of Ubuntu 8.10 (yay!). And, this is  the funny part, on my HP tx1320us the bluetooth actually **started** working. Maybe there are some issuse whilst upgrading from beta? I'm also using MS Bluetooth Mouse 5000 (recommend it!). The GUI device pairing wizard was a nice surprise.

---

### Post by ukblacknight on 2008-10-31
> **mkarnicki said:**
> Just yesterday I made a fresh install of Ubuntu 8.10 (yay!). And, this is  the funny part, on my HP tx1320us the bluetooth actually **started** working. Maybe there are some issuse whilst upgrading from beta? I'm also using MS Bluetooth Mouse 5000 (recommend it!). The GUI device pairing wizard was a nice surprise.

Ok ok, rub it in why don't you!! ;)

---

### Post by ukblacknight on 2008-10-31
> **mkarnicki said:**
> Just yesterday I made a fresh install of Ubuntu 8.10 (yay!). And, this is  the funny part, on my HP tx1320us the bluetooth actually **started** working. Maybe there are some issuse whilst upgrading from beta? I'm also using MS Bluetooth Mouse 5000 (recommend it!). The GUI device pairing wizard was a nice surprise.

I did a fresh install (keeping my /home partition, however) from 8.04, so that can't be the problem.

---

### Post by churchyard on 2008-10-31
I updated from 8.04 (with all updates) to 8.10...

If you look here:
[http://packages.ubuntu.com/search?searchon=contents&keywords=hidd&mode=exactfilename&suite=hardy&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=hidd&mode=exactfilename&suite=hardy&arch=any)
[http://packages.ubuntu.com/search?suite=intrepid&arch=any&mode=exactfilename&searchon=contents&keywords=hidd](http://packages.ubuntu.com/search?suite=intrepid&arch=any&mode=exactfilename&searchon=contents&keywords=hidd)


and:
[http://packages.ubuntu.com/search?searchon=contents&keywords=hcid&mode=exactfilename&suite=hardy&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=hcid&mode=exactfilename&suite=hardy&arch=any)
[http://packages.ubuntu.com/search?suite=intrepid&arch=any&mode=exactfilename&searchon=contents&keywords=hcid](http://packages.ubuntu.com/search?suite=intrepid&arch=any&mode=exactfilename&searchon=contents&keywords=hcid)

You can see hidd has moved to bluez-compact and hcid is missing.

---

### Post by isecore on 2008-10-31
> **churchyard said:**
> I updated from 8.04 (with all updates) to 8.10...

If you look here:
[http://packages.ubuntu.com/search?searchon=contents&keywords=hidd&mode=exactfilename&suite=hardy&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=hidd&mode=exactfilename&suite=hardy&arch=any)
[http://packages.ubuntu.com/search?suite=intrepid&arch=any&mode=exactfilename&searchon=contents&keywords=hidd](http://packages.ubuntu.com/search?suite=intrepid&arch=any&mode=exactfilename&searchon=contents&keywords=hidd)


and:
[http://packages.ubuntu.com/search?searchon=contents&keywords=hcid&mode=exactfilename&suite=hardy&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=hcid&mode=exactfilename&suite=hardy&arch=any)
[http://packages.ubuntu.com/search?suite=intrepid&arch=any&mode=exactfilename&searchon=contents&keywords=hcid](http://packages.ubuntu.com/search?suite=intrepid&arch=any&mode=exactfilename&searchon=contents&keywords=hcid)

You can see hidd has moved to bluez-compact and hcid is missing.

That would be bluez-compat. I installed it, made no difference.

---

### Post by isecore on 2008-10-31
For what it's worth, I tried booting off of the live-cd. Well, the live-USB in my case since I used the included tool to make a USB thumbdrive with Ubuntu 8.10 on it.

It detected everything and even showed the bluetooth icon in the tray. That's the good news. The bad news was that nothing else was different. Still couldn't send files, receive files or anything.

I'd been contemplating a reinstallation (desperate measure) but now I feel confident that a reinstall wouldn't solve this problem.

---

### Post by Nightmare JG on 2008-10-31
My Bluetooth won't work either.
I upgraded from Hardy (where Bluetooth work, no problems) to Intrepid, and now it doesn't work right.

The applet won't let me change the visibility, or the device name, I think it might be related to the config files, the new bluetooth doesn't seem to use the config files in /etc/bluetooth...so where are the new config files?

My Bluetooth mouse still works (kind of) I can't pair it, it doesn't show up in the applet, and the wheel won't work.

---

### Post by jcoenen on 2008-10-31
I reported earlier on a BT not working properly on a BT 2 dongle (USB), since, I installed Ibex on an HP NW8440 with integrated BT and there it does see and pair with my mouse (haven't tried anything else). Installation are made from scratch.

Just found this quote in another forum:

"Bluetooth is currently broken for Kubuntu Intrepid due to a last minute upgrade of the bluez stack. We hope to have a fix for this but only as an update after release, 2008", maybe this is related to what we experience.

From: [http://forum.ubuntu-fr.org/viewtopic.php?pid=2166210](http://forum.ubuntu-fr.org/viewtopic.php?pid=2166210)

---

### Post by isecore on 2008-10-31
> **jcoenen said:**
> Just found this quote in another forum:

"Bluetooth is currently broken for Kubuntu Intrepid due to a last minute upgrade of the bluez stack. We hope to have a fix for this but only as an update after release, 2008", maybe this is related to what we experience.

From: [http://forum.ubuntu-fr.org/viewtopic.php?pid=2166210](http://forum.ubuntu-fr.org/viewtopic.php?pid=2166210)

One can hope that a simple update will make this go away [-o<

---

### Post by Nightmare JG on 2008-10-31
I think it's a kernel module, hopefully it'll be fixed by an update.
BT works perfect with an older kernel, just not with the newest.

---

### Post by wolandt on 2008-10-31
me too! my mouse doesn't work!!!! :( and i was so happy when i saw how it worked after installation, then rebooted and .... nothing :(((

---

### Post by spo0ner on 2008-10-31
I have to be honest and I really hate saying this because I am not a fan of Microsoft (hate their business practices) and am a true fan of Linux but they really need to rethink this "release every 6 months" cycle if they are going to continue to ship stuff that is half broken and call it a release.  They become no better than Microsoft for pushing out software that has known LARGE bugs.  A simsilar thing happened with gvfs in the 8.04 LTS release and it kept many clients from connecting to secured Windows shares on a network.

Seriously, Bluetooth is almost a necessity for all users for them to just discount this as a "we'll fix later" or "who the heck uses bluetooth anyways" kind of issue is just unacceptable.  I really hope they get this resolved soon or I'm going to have to switch back to Debian raw (and I really like Ubuntu in general).

---

### Post by ukblacknight on 2008-10-31
> **spo0ner said:**
> I have to be honest and I really hate saying this because I am not a fan of Microsoft (hate their business practices) and am a true fan of Linux but they really need to rethink this "release every 6 months" cycle if they are going to continue to ship stuff that is half broken and call it a release.  They become no better than Microsoft for pushing out software that has known LARGE bugs.  A simsilar thing happened with gvfs in the 8.04 LTS release and it kept many clients from connecting to secured Windows shares on a network.

Seriously, Bluetooth is almost a necessity for all users for them to just discount this as a "we'll fix later" or "who the heck uses bluetooth anyways" kind of issue is just unacceptable.  I really hope they get this resolved soon or I'm going to have to switch back to Debian raw (and I really like Ubuntu in general).

Is what I don't understand is, how can something that works perfectly fine suddenly stop working in the next release?  Didn't they spot this when they upgraded the bluetooth modules?  It's not a major problem for me, but it's the only way I really connect my phone to my PC (lost the USB cable), however, it worked fine in 8.04 - why is it now so broken?

Maybe they should do 12 month releases, with constant minor roll outs in between.

---

### Post by Dropbear on 2008-10-31
I remember in hardy there was a bug that would cause the computer to lock up completely when pairing. This happened on both my desktop and laptop. I fixed it by installing blueman from it's repository which updated a few bluetooth packages. This also fixed it when using bluetooth through gnome. There is currently no version of blueman for intrepid so not a solution. :(

---

### Post by akai_kenshi on 2008-11-01
> **wolandt said:**
> me too! my mouse doesn't work!!!! :( and i was so happy when i saw how it worked after installation, then rebooted and .... nothing :(((

You're in the same boat as me, then? Mouse works perfectly until restart or timeout?

[quote=spo0ner]I have to be honest and I really hate saying this because I am not a fan of Microsoft (hate their business practices) and am a true fan of Linux but they really need to rethink this "release every 6 months" cycle if they are going to continue to ship stuff that is half broken and call it a release. They become no better than Microsoft for pushing out software that has known LARGE bugs. A simsilar thing happened with gvfs in the 8.04 LTS release and it kept many clients from connecting to secured Windows shares on a network.

Seriously, Bluetooth is almost a necessity for all users for them to just discount this as a "we'll fix later" or "who the heck uses bluetooth anyways" kind of issue is just unacceptable. I really hope they get this resolved soon or I'm going to have to switch back to Debian raw (and I really like Ubuntu in general).[/quote]

I don't know, I kinda like the 6 month releases, they give me something to look forward to:)

I see where you're coming from, though. On one hand you've got Debian, which is really stable but also stagnant, and on the other hand you've got non-LTS Ubuntu, which is very cutting edge but occasionally has major bugs. Where's the middle ground?

---

### Post by kylea on 2008-11-01
Uhm - this is **[COLOR="Red"]very frustrating[/COLOR]**. Have committed to Linux and Ubuntu - dropped XP (now run only inside Sun xVM for Logmein and some Tax web sites that only work with Windows)

- I need Bluetooth as I live via my Calendar in my Nokia.

I could Sync on Monday, Tuesday and Wed - but Thur onwards its a big no go.

Have spent days getting this to work and days trying to figure why its stopped.

Not sure how a 'standard' Windows user would survive this.

:confused:

---

### Post by ukblacknight on 2008-11-01
> **kylea said:**
> Uhm - this is **[COLOR="Red"]very frustrating[/COLOR]**. Have committed to Linux and Ubuntu - dropped XP (now run only inside Sun xVM for Logmein and some Tax web sites that only work with Windows)

- I need Bluetooth as I live via my Calendar in my Nokia.

I could Sync on Monday, Tuesday and Wed - but Thur onwards its a big no go.

Have spent days getting this to work and days trying to figure why its stopped.

Not sure how a 'standard' Windows user would survive this.

:confused:

I've always found the Windows BT stack to be horrendous!  It's better in Vista, but in XP it always used to crash on me or stop working for long periods of time.

I guess this is a module problem in the kernel, I hope they get it fixed pretty quick!

What bluetooth device have you got?

---

### Post by dmonkey on 2008-11-01
My problem is the same as akai_kenshi; I have an MS Bluetooth 5000 mouse, and it DOES pair with Ubuntu and works great, but after some time (or after a restart or going into standby) it just breaks. The mouse is still listed in the bluetooth devices list, but the mouse doesn't actually work.

The only fix I have is to delete the mouse, and then add it again.

---

### Post by Nightmare JG on 2008-11-01
> **akai_kenshi said:**
> 
I see where you're coming from, though. On one hand you've got Debian, which is really stable but also stagnant, and on the other hand you've got non-LTS Ubuntu, which is very cutting edge but occasionally has major bugs. Where's the middle ground?

The LTS releases? Seems pretty middle ground-y to me.

---

### Post by isecore on 2008-11-01
> **akai_kenshi said:**
> I don't know, I kinda like the 6 month releases, they give me something to look forward to:)

I see where you're coming from, though. On one hand you've got Debian, which is really stable but also stagnant, and on the other hand you've got non-LTS Ubuntu, which is very cutting edge but occasionally has major bugs. Where's the middle ground?

I understand Debians philosophy. Stability and testing above everything. But it's become a bit of an anchor for them, and I know the developers are trying to move in a somewhat quicker direction, i.e. releasing new versions a little more often than once a decade. But still, that's their philosophy, they sacrifice cutting-edge for superior stability.

Which is excellent when running a server actually, as long as you get regular security-patches.

So I think Ubuntu is the middle-ground. All that's good with Debian without the glacial pace of releases. I can accept breakage, even though I hope this BT-thing gets sorted sooner rather than later.

---

### Post by dmonkey on 2008-11-01
What frustrates me the most is that in the previous release, the bluetooth worked perfectly for me. I suppose it just comes with the territory when you have so many different parts of the overall package all being developed separately. It's a pretty incredible feat that some much of it just works out of the box in the first place!

That being said, I'm also looking forward to this getting fixed soon!

---

### Post by gweaver on 2008-11-02
I have the same issue. When I use the Bluetooth applet to setup a connection with my phone it fails to pair.
It worked fine under Hardy.

---

### Post by billWalker on 2008-11-02
Count me in for dmonkey & akai_kenshi's problem.

I can connect my logitech dinovo mini, but after a reboot it doesn't work although it's still on the bluetooth device list.  I have to remove and add again, same as them.

I notice that in Intrepid the bluetooth driver now requires that I type in a passphrase to pair the keyboard.  Is it possible this function is the culprit?

---

### Post by isecore on 2008-11-02
Let me restate my problem again for the record:

No bluetooth functionality at all. I'm just happy that I don't have a bluetooth keyboard and/or mouse since I would be up sh*t creek without a paddle then. I can't set anything, can't add any device, can't do a dang thing since my bluetooth panel is completely non-functional. Hell, the only way to even get the icon to show up is to restart the BT service, and it's a complete waste of time since I only get a eunuch of an icon.

I envy those of you who have any kind of functionality because it's eons more than I've got.

---

### Post by ukblacknight on 2008-11-02
> **isecore said:**
> Let me restate my problem again for the record:

No bluetooth functionality at all. I'm just happy that I don't have a bluetooth keyboard and/or mouse since I would be up sh*t creek without a paddle then. I can't set anything, can't add any device, can't do a dang thing since my bluetooth panel is completely non-functional. Hell, the only way to even get the icon to show up is to restart the BT service, and it's a complete waste of time since I only get a eunuch of an icon.

I envy those of you who have any kind of functionality because it's eons more than I've got.

I echo what isecore said.  Icon appears if you restart bluetooth, but if you go into preferences and try to change anything - the icon disappears.  No device will even find it.  The blue light on my USB stick doesn't even come on.

---

### Post by Zularan on 2008-11-02
I too was having issues transferring between my Windows Mobile device and Ubuntu using bluetooth.  In the past it used to work as I just use it to send/receive files/photos but now nothing seemed to work.

Installing 'obexpushd' from Synaptic solved half the problem and I can now send from Ubuntu to my mobile, but I can't send the other way.  Still tinkering around I'll see if I have any success.

---

### Post by erlguta on 2008-11-03
Ok, it does not work for anybody. But saying around the world that just does not work for you is not going to fix all of a sudden just by magic. The thing to do is post in the bug and comments in launchpad:
[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/283064](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/283064)

For a solution as soon as possible.

---

### Post by ukblacknight on 2008-11-03
> **erlguta said:**
> Ok, it does not work for anybody. But saying around the world that just does not work for you is not going to fix all of a sudden just by magic. The thing to do is post in the bug and comments in launchpad:
[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/283064](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/283064)

For a solution as soon as possible.

Did you read the original post of this thread?  The OP created a bug report on launchpad, which is different to the bug report you've just linked to.  I've commented on it too.  The bug report you linked to is for bluetooth not receiving files - our problem is that BLUETOOTH DOES NOT WORK AT ALL!!  E.g. our bluetooth devices are totally dead in the water.

People talk about the problem here because someone might come along and provide a solution.

---

### Post by jennysmith on 2008-11-03
The main reason is with the latest updates to Intrepid testing, the new bluetooth device setup wizard (which is an excellent improvement over the previous setup methods) fails to pair with my Apple Keyboard (pre-aluminum, broadcom based). No debug  information or error messages are given other than failed to pair.
--------------------------------
Jennysmith

[Influencer]("http://www.drivenwide.com")

---

### Post by akai_kenshi on 2008-11-03
Here's the bug report for the problem affecting me (mouse and keyboard pair but stop working after idle or restart):[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/292030](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/292030) I would encourage everyone with this problem at the very least to log into Launchpad and register that they're being affecting by clicking "change" next to "This bug doesn't affect me."

---

### Post by stevenyu on 2008-11-03
I am having problem with bluetooth losing the configuration after reboot, this have already report as a bug in launchpad

---

### Post by Ragnar0k on 2008-11-03
This has been driving me nuts too, although mine's a little odder.

I have a MX5500 keyboard set, and it doesn't work. Unless I unplug and re-plug the BT dongle, then it pairs up and I can type to my heart's content.

What the frack?

This is on a fresh 8.10 install today.

-Rag

---

### Post by DrJohn999 on 2008-11-03
Same same here. BT <--> mouse, phone file transfer worked fine on Hardy, broke on Ibex. Have BT icon but no functionality.

My solution: it's too early for the Ibex upgrade, I'm restoring from backup and returning to Hardy until Ibex is more stable. I don't have the time to mess with not-quite-well-done releases.

--  DJ

---

### Post by bluebook on 2008-11-03
> **DrJohn999 said:**
> Same same here. BT <--> mouse, phone file transfer worked fine on Hardy, broke on Ibex. Have BT icon but no functionality.

My solution: it's too early for the Ibex upgrade, I'm restoring from backup and returning to Hardy until Ibex is more stable. I don't have the time to mess with not-quite-well-done releases.

--  DJ
Funny you say that, I'm sticking with Intrepid because the latest kernel update broke my wireless on Hardy, and it's much faster in Intrepid. Skype is also now working when it wasn't previously. Bluetooth is a smaller consideration for me at the moment, though I would like it fixed. You win some you lose some I guess.

---

### Post by gaelfx on 2008-11-03
I really suspect this is part of the problem, but I can't figure out any good way to get that command back, with the possible exception of using backports, but that makes me very worried about other parts of my system being affected. I think we need to do a little more research about where sdpd is supposed to come from because every time I talk about this on the IRC channel, the people with working bluetooth tell me that sdpd is running on their machines.

---

### Post by peddy on 2008-11-04
Me too! Even with the latest Bluetooth set of updates :/

---

### Post by 3aTi3 on 2008-11-04
On a fresh install and live cd, the bluetooth wizard sees my device, but on the actual setup don't. So it's maybe a package-incompatibility.
but i didn't install any software connected with bluetooth :S

---

### Post by Borlag on 2008-11-04
Just bought an A-Link BlueUSB21 bluetooth dongle, and it worked pretty much out of the box on a quick test with a Nokia 2760 phone and filetransfers.

Somewhat amusing that the exact same dongle required additional software in Windows side (was at work) for it to work properly with my Nokia N95.

---

### Post by ImNeat on 2008-11-04
I used to connect my bluetooth keyboard using ```
hidd --connect
``` but now I get the error ```
sudo: hidd: command not found
``` It looks like hidd was removed from the bluez-utils package. 

Since that's apparently the out-of-date way to connect a bt keyboard... what's the new way?  I've never seen any documentation on the issue.

---

### Post by svguy on 2008-11-04
I upgraded my 8.04 to 8.10 on my dell d600 and now my built in bluetooth doesn't show up as a device.

I have to hciconfig hci0 up to have the device register, and then it will detect my mouse on a scan, but won't connect.

---

### Post by Nicolas Viau on 2008-11-04
Similar problem here. My Logitech BT mouse worked in Intrepid beta, but it stopped working after the update to the final release. The Bluetooth applet no longer shows any device. Rebooting does not help.

The hidd command is now available in the bluez-compat package, but I can no longer connect using  it either, I get the error:

```
Can't get device information: No route to host
```

---

### Post by DrJohn999 on 2008-11-05
Before restoring to Hardy from backup, I did a fresh install of Ibex from the Live CD, and ta-da bluetooth (and WPA, which also was broken) is up and running. The wizard detects my devices (mouse, phone, headset) when I make them discoverable. A small problem with the mouse getting lost the first time, but now it persists.

Onward with Ibex then.

This is a Dell Dimension D610 laptop, FWIW.

-- DJ

---

### Post by ukblacknight on 2008-11-05
I kept my /home partition.  Maybe that could be having an effect?  I'll try the LiveCD later and see if it picks up bluetooth there.  Tempted for a re-install :(

Saw there was a kernel update when I came back to my PC earlier, however it didn't fix the issue :\

---

### Post by Portending Ennui on 2008-11-05
8.10 doesn't even see my BT adapter.  Worked great in Hardy though. Fn+F8 doesn't do anything for me anymore, and I've tried booting with my wireless switch off, and turning it on after log-on, a tip from a friend. Will reboot into Ubuntu and try some other Fn keys to see if its an ACPI issue for me, or if it could be related to this.

Fresh install, decided to dual-boot XP-Pro due to work so I had to repartition anyways. Toshiba Qosmio G35-AV600, but I'm upgrading soon... (I hope, come on work bonus!!!! :p )

Might try toshset as a temporary fix....

---

### Post by Portending Ennui on 2008-11-05
Relevant (I think) syslog from last boot, regarding BT:

```
Nov  5 12:07:46 Zeus-Nix bluetoothd[5319]: Bluetooth daemon
Nov  5 12:07:46 Zeus-Nix kernel: [   74.062916] Bluetooth: Core ver 2.13
Nov  5 12:07:46 Zeus-Nix kernel: [   74.064376] NET: Registered protocol family 31
Nov  5 12:07:46 Zeus-Nix kernel: [   74.064382] Bluetooth: HCI device and connection manager initialized
Nov  5 12:07:46 Zeus-Nix kernel: [   74.064386] Bluetooth: HCI socket layer initialized
Nov  5 12:07:46 Zeus-Nix bluetoothd[5319]: Starting SDP server
Nov  5 12:07:46 Zeus-Nix kernel: [   74.077920] Bluetooth: L2CAP ver 2.11
Nov  5 12:07:46 Zeus-Nix kernel: [   74.077928] Bluetooth: L2CAP socket layer initialized
Nov  5 12:07:46 Zeus-Nix kernel: [   74.101477] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Nov  5 12:07:46 Zeus-Nix kernel: [   74.101484] Bluetooth: BNEP filters: protocol multicast
Nov  5 12:07:46 Zeus-Nix kernel: [   74.131852] Bridge firewalling registered
Nov  5 12:07:46 Zeus-Nix bluetoothd[5319]: bridge pan0 created
Nov  5 12:07:46 Zeus-Nix kernel: [   74.132534] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
Nov  5 12:07:46 Zeus-Nix kernel: [   74.142125] Bluetooth: SCO (Voice Link) ver 0.6
Nov  5 12:07:46 Zeus-Nix kernel: [   74.142133] Bluetooth: SCO socket layer initialized
Nov  5 12:07:46 Zeus-Nix bluetoothd[5319]: Starting experimental netlink support
Nov  5 12:07:46 Zeus-Nix bluetoothd[5319]: Failed to find Bluetooth netlink family
Nov  5 12:07:46 Zeus-Nix bluetoothd[5319]: Can't init plugin /usr/lib/bluetooth/plugins/netlink.so
Nov  5 12:07:46 Zeus-Nix kernel: [   74.169048] Bluetooth: RFCOMM socket layer initialized
Nov  5 12:07:46 Zeus-Nix kernel: [   74.169067] Bluetooth: RFCOMM TTY layer initialized
Nov  5 12:07:46 Zeus-Nix kernel: [   74.169069] Bluetooth: RFCOMM ver 1.10
```


I just use linux, don't know what that means, but if it helps I'll be glad!  Check you're syslogs, too!

I think I'm gonna post a bug report, in case it's a different problem.


EDIT:

It seems my problem is the toshiba kernel modules are not include in 8.10, so no BT until I figure out how to get them, namely toshiba and toshiba_acpi.

```

*******@Zeus-Nix:~$ sudo toshset
required kernel toshiba support not enabled.

*******@Zeus-Nix:~$ sudo modprobe toshiba_acpi
FATAL: Module toshiba_acpi not found.

*******@Zeus-Nix:~$ sudo modprobe toshiba
FATAL: Module toshiba not found.

*******@Zeus-Nix:~$ 

```

Anyone have an idea?

---

### Post by nb_alexiev on 2008-11-05
Same problems here... My bluetooth dongle worked perfect with 8.04. Now I have fresh install of 8.10 and can't get bluetooth working any more. I can pair my phone with to the notebook, but this is not possible vice-vers. Any way one the devices are paired I can't do anything (send files, use phone as HID).
I'm afraid that the phone doesn't see what are the services provided by the other device (notebook). It says that no services are provided at all.

I hope this will be solved soon... I can live without bluetooth but using phone as a remote control is one of the greatest things I can do with Ubuntu!

Thank you!

---

### Post by bluebook on 2008-11-05
If you're having this problem (like I am) you might want to go and comment on this bug page on launchpad: [https://bugs.launchpad.net/ubuntu/+bug/284982]("https://bugs.launchpad.net/ubuntu/+bug/284982") so that the powers-that-be see this as an issue and prioritize it accordingly.

---

### Post by unclejac on 2008-11-05
> **ukblacknight said:**
> 
Saw there was a kernel update when I came back to my PC earlier, however it didn't fix the issue :\

No sadly it didn't fix it. 

I was hoping that the update would have had some magic in it and solve our BT troubles. . . 

Guess we will all have to be a bit more patient until someone comes us with a solution.

---

### Post by johndoe32102002 on 2008-11-05
I upgraded from Hardy to Intrepid and bluetooth now fails to recognize devices.  I see it scanning, but it will not connect to any bluetooth device!

---

### Post by hyperboloid on 2008-11-06
I was having problems with my Bluetooth mouse pairing not surviving a reboot, similar to problems reported by others in this thread. Found a simple workaround here in [ubuntuforums.org/showthread.php?t=966436]("http://ubuntuforums.org/showthread.php?t=966436") and it fixed my problem. :)

---

### Post by bluebook on 2008-11-06
Hyperboloid - Unfortunately I think our problem is that our bluetooth device (in the computer) is simply not recognized. It sounds like there's been varying issues with Bluetooth and Intrepid, hopefully they'll get resolved soon.

---

### Post by xens on 2008-11-07
bluebook: I'm not so sure about it...

read the comments on the bug report page

---

### Post by PowerPanda on 2008-11-07
Same problem here:
Two different Intrepids, one 32bit one 64bit, cannot connect to Z310i phone and also V470 Mouse :(

---

### Post by demsbad on 2008-11-07
OK...I was having the issue in 8.10 (establishing connection, rebooting, not being able to re-pair) on a Thinkpad X61 tablet, but seem to have figured it out.

Right-click on the bluetooth icon, select preferences, and change the visibility setting to "always visible." With that change, my pairing issues seem to have resolved themselves. I've rebooted the computer several times and the pairing has stuck.

YMMV.

:guitar:

---

### Post by markinf on 2008-11-07
same problem here

---

### Post by emulantie on 2008-11-07
> **demsbad said:**
> OK...I was having the issue in 8.10 (establishing connection, rebooting, not being able to re-pair) on a Thinkpad X61 tablet, but seem to have figured it out.

Right-click on the bluetooth icon, select preferences, and change the visibility setting to "always visible." With that change, my pairing issues seem to have resolved themselves. I've rebooted the computer several times and the pairing has stuck.

YMMV.

:guitar:
The 1st post

I had the same problem with Vaio bluetooth and an Microsoft 5000 BT mouse but after changing the visibility settings to always, it seems to be just fine. Ive rebooted several times and it still works!

---

### Post by ukblacknight on 2008-11-07
> **emulantie said:**
> The 1st post

I had the same problem with Vaio bluetooth and an Microsoft 5000 BT mouse but after changing the visibility settings to always, it seems to be just fine. Ive rebooted several times and it still works!

Clicking anything in the bluetooth preferences just makes the icon disappear.  Bluetooth is completely screwed for me! :(

---

### Post by PowerPanda on 2008-11-08
I can confirm, my problem is same as Nightmare JG's. When I reboot to kernel 2.6.24-21 generic everything works fine. Lucky I didn't delete it.

---

### Post by BionicSeahorse on 2008-11-08
> **ukblacknight said:**
> Clicking anything in the bluetooth preferences just makes the icon disappear.  Bluetooth is completely screwed for me! :(

This is exactly what happens to me. Sometimes my phone even shows up inside the "known devices" list; unfortunately, as soon as I click on the "always visible" radio button, every field clears up ("visibility settings", "friendly name", and "known devices"). :confused:

---

### Post by markinf on 2008-11-08
* Found a fix *

This is how I fixed.

I downgraded the kdeframework to hardy (which is kde 3, while on intrepid is kde 4) and used kbtobexclient to push the files to my Nokia phone.

Steps to get this working...

Download the following packages and it's dependency, I think those four might be satisfatory.

[http://packages.ubuntu.com/hardy/kdebluetooth](http://packages.ubuntu.com/hardy/kdebluetooth)
[http://packages.ubuntu.com/hardy/kdelibs4c2a](http://packages.ubuntu.com/hardy/kdelibs4c2a)
[http://packages.ubuntu.com/hardy/libkbluetooth0](http://packages.ubuntu.com/hardy/libkbluetooth0)

put these packages in a separate folder

now lets install it...

sudo dpkg -i *.deb

and

run kbtobexclient

=)

---

### Post by churchyard on 2008-11-08
Actually I don't have KDE and and I don't want to do this on my Xfce.

---

### Post by canabal on 2008-11-09
Just an fyi guys, OpenObex 1.4 is out.  1st release in 2 years according to [http://www.bluez.org/](http://www.bluez.org/) .

Maybe that can help.

---

### Post by ukblacknight on 2008-11-09
> **canabal said:**
> Just an fyi guys, OpenObex 1.4 is out.  1st release in 2 years according to [http://www.bluez.org/](http://www.bluez.org/) .

Maybe that can help.

That's quarter worked for me!  The icon showed up and I was able to configure bluetooth.  When I went to set up a new device, a device was listed in the list, looked like a mac address, however when I tried to pair with it, it just failed.  My phone can't see my PC and the light on my bluetooth adapter isn't lit up like it normally would be.

---

### Post by KhaaL on 2008-11-09
wrong post

---

### Post by ravi.xolve on 2008-11-09
> **markinf said:**
> * Found a fix *

This is how I fixed.

I downgraded the kdeframework to hardy (which is kde 3, while on intrepid is kde 4) and used kbtobexclient to push the files to my Nokia phone.

Steps to get this working...

Download the following packages and it's dependency, I think those four might be satisfatory.

[http://packages.ubuntu.com/hardy/kdebluetooth](http://packages.ubuntu.com/hardy/kdebluetooth)
[http://packages.ubuntu.com/hardy/kdelibs4c2a](http://packages.ubuntu.com/hardy/kdelibs4c2a)
[http://packages.ubuntu.com/hardy/libkbluetooth0](http://packages.ubuntu.com/hardy/libkbluetooth0)

put these packages in a separate folder

now lets install it...

sudo dpkg -i *.deb

and

run kbtobexclient

=)

you said four. i THINK YOU MISSED ONE.

---

### Post by cas118 on 2008-11-10
> **Ragnar0k said:**
> This has been driving me nuts too, although mine's a little odder.

I have a MX5500 keyboard set, and it doesn't work. Unless I unplug and re-plug the BT dongle, then it pairs up and I can type to my heart's content.

-Rag

When you unplug the Logitech receiver and plug it in again, it acts as a USB dongle rather than bluetooth. That works fine as long as you don't want to use Bluetooth. In fact, if that's the case the easiest way to get it working is to remove the bluez package completely.

Alternatively, leave it plugged in and doe one of the following:

a) Plug in another mouse and run the connection wizard.

b) Install the **bluez-compat** package
Run **sudo hidd --search** in the terminal
Press 'connect on the keyboard and mouse to get the to be discovered.
NOW use the wizard to connect.

If you have a spare mouse, I'd suggest 'a'. I only had a spare keyboard...

---

### Post by ravi.xolve on 2008-11-10
The problem is with the kernel I install the kernel that comes with hardy and bluetoth works fine. If you downgrade to bluez-utils that come with gusty it also allows to recieve he files from phone. meane bluetooth on linux needs a long way to go.

---

### Post by Keith_Beef on 2008-11-10
There seem to be at least two different problems all mixed up in this thread.

[LIST=1]
[*]The Bluetooth hardware of the computer is no longer detected of correctly configured, since moving to Intrepid.
[*]The Bluetooth hardware of the computer no longer works, since moving to Intrepid.
[*]The computer no longer pairs with my device, since moving to Intrepid.
[/LIST]

And diagnosing the problem is a pain, since tools that were present in Hardy have disappeared, and you need to installed the compatibility package bluez-compat, to get them back.

I'm having (sort of) the third problem, in that my computer cannot pair with the GPS receiver due to the bad design of the Gnome Bluetooth Applet.

I recommend everybody to file bug reports, but make an extra effort to file them correctly.
[LIST]
[*][Launchpad 284994 ]("https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/284994") is for pairing problems due to bad applet design.
[*][Launchpad 283064 ]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/283064") is for file transfer problems after pairing.
[*][Launchpad 284982 ]("https://bugs.launchpad.net/ubuntu/+bug/284982") seems to be problems recognizing BT hardware.
[/LIST]

There might be more bug reports, just try to file in the most relevent.

K.

---

### Post by ravi.xolve on 2008-11-10
If you install the kernel that came with hardy you will be able to pair up with the device.

---

### Post by ImNeat on 2008-11-10
> **Nicolas Viau said:**
> The hidd command is now available in the bluez-compat package

Thanks! Now I just need it to auto-pair on reboot or after idling.

---

### Post by PowerPanda on 2008-11-12
Still nothing works :( Will we have to wait for new kernel, and if so when should it come out around? Thx.

---

### Post by ravi.xolve on 2008-11-13
Well old kernel 2.6.24 will work. Its available in Hardy and it works great for me.

:)

---

### Post by benvantende on 2008-11-13
I am waiting with upgrading (for the first time in years) to ibex until this is solved probably with a new kernel.

---

### Post by PowerPanda on 2008-11-13
Unfortunately old kernel won't work with my fglrx drivers so it's not really an option. Thanks anyway though.

---

### Post by mac.ryan on 2008-11-15
I am also having an hard time with BT under Ibex64. The funny bit is that my PC's behave inconsistently (sometimes they see the device, sometimes not, sometimes they pair, sometimes not, sometimes...).

I filed a new bug here: [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/298430](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/298430)

If anybody feels it is close to what is happening to them, please go there and click on the almost-top left, where you can say if the bug affects you too...

---

### Post by debernardis on 2008-11-15
After consulting this thread, and fiddling with synaptic in that I installed a number of packages involving bluetooth, obex and the so, I succeeded in what I mainly need, i.e. sending and receiving files to/from my other bluetooth-enabled devices as phones and tablets.
Ah, and my os is intrepid ibex on a usb stick, with persistence.

These are the packages I have installed... most likely, not all of them are needed.

```
~$ dpkg -l | grep -E "blue|obex|push"
ii  bluetooth                                 4.12-0ubuntu5                           Bluetooth support
ii  bluez                                     4.12-0ubuntu5                           Bluetooth tools and daemons
ii  bluez-alsa                                4.12-0ubuntu5                           Bluetooth audio support
ii  bluez-cups                                4.12-0ubuntu5                           Bluetooth printer driver for CUPS
ii  bluez-gnome                               1.8-0ubuntu1                            Bluetooth utilities for GNOME
ii  bluez-gstreamer                           4.12-0ubuntu5                           Bluetooth gstreamer support
ii  bluez-utils                               4.12-0ubuntu5                           Transitional package
ii  gnome-bluetooth                           0.11.0-0ubuntu3                         GNOME Bluetooth tools.
ii  gnome-vfs-obexftp                         0.4-1build1                             GNOME VFS module for OBEX FTP
ii  libbluetooth3                             4.12-0ubuntu5                           Library to use the BlueZ Linux Bluetooth stack
ii  libopenobex1                              1.3+cvs20070425-2build1                 OBEX protocol library
ii  obex-data-server                          0.3.4+svn1951-0ubuntu1                  D-Bus service for OBEX client and server side functiona
ii  obexfs                                    0.10-3build1                            mount filesystem of ObexFTP capable devices
ii  obexftp                                   0.19-7ubuntu2                           file transfer utility for devices that use the OBEX pro
ii  obexpushd                                 0.7-1ubuntu2                            program for receiving files via Bluetooth or IRDA
ii  obextool                                  0.33-0ubuntu1                           graphical frontend for obexftp written in TCL/TK
ii  ussp-push                                 0.9-2ubuntu1                            Client for OBEX PUSH

```

It's noteworthy that I *cannot* send a file by right-clicking it and using the send to command; instead I have to right-click the bluetooth icon on the gnome panel and choose the send file option. Who knows why?

---

### Post by Yezinki on 2008-11-15
Ubuntu 8.10 as a rule supports/ has drivers for newer devices.

BT dongle you shall have to configure it yourself as I did.

It picks up & pairs fine with Dell 3.55 BT module.

So if your system peripherals are old stick with Hardy.

My thoughts,

Regards,

Yezinki.

---

### Post by isecore on 2008-11-15
> **Yezinki said:**
> Ubuntu 8.10 as a rule supports/ has drivers for newer devices.

BT dongle you shall have to configure it yourself as I did.

It picks up & pairs fine with Dell 3.55 BT module.

So if your system peripherals are old stick with Hardy.

My thoughts,

Regards,

Yezinki.
Why should I stick with an older version just because my dongle happens to be 2+ years old? It's just silly. I find it rather absurd that support is dropped or regressed for some hardware. Why shouldn't everything "just work"? Why should we have to stop from upgrading to the latest for fear that something might not work? Again, I feel that this is a Windows-mindset, and we don't need that.

---

### Post by isecore on 2008-11-15
Okay... the strangest thing just happened.

I was fiddling around with some things. I read somewhere that gnome-bluetooth was antiquated, so on a whim I removed --purged that. Made no difference after I tried /etc/init.d/bluetooth restart.

So I shrugged. Then I tried removing all the bluetooth modules loaded in the kernel. In my case AFAIK these are bnep, sco, rfcomm, l2cap and btusb. All except l2cap and rfcomm unloaded just fine. Unplugged my dongle, the kernel automagically reloaded these modules. Made no difference.

So, I decided to try the Live-CD once again. Rebooted with that, nope. Bluetooth was still non-functional. Icon was there, but it was inoperable. Nothing happened when clicked on, detected no devices.

So I rebooted into my "real" install... and guess what? I noticed the BT-icon had returned to the tray when I logged in. Weird... clicked it, and lo and behold - the panel works! My devices were listed, my computers name was filled in, I could set visibility.

Could it have been gnome-bluetooth who was keeping it back?

However, when I tried adding a device it still doesn't show any, and a hcitool scan still looks like this:

```
isecore@superbeast:~$ hcitool scan
Scanning ...
Inquiry failed: Connection timed out
isecore@superbeast:~$
```

Is this of any use to anyone?

update: Well, huh. I logged out, then back in again. Now there's no icon and everythings dead again.

update 2: yep, whatever caused this to happen disappeared as quickly as it came. I have no idea what happened, what I did.

---

### Post by ravi.xolve on 2008-11-16
apart from this, ubuntu intrepid is being reported to lack many things. many people are just sticking to hardy because *it still works*. i guess we need to wait for package updates.

---

### Post by lordfoul on 2008-11-16
Anyone try this [http://ubuntuforums.org/showpost.php?p=6086632&postcount=5](http://ubuntuforums.org/showpost.php?p=6086632&postcount=5)

---

### Post by isecore on 2008-11-16
> **lordfoul said:**
> Anyone try this [http://ubuntuforums.org/showpost.php?p=6086632&postcount=5](http://ubuntuforums.org/showpost.php?p=6086632&postcount=5)

That's a useless advice for me (and several others in this thread) since our bluetooth panel is completely non-functional. We can't change options in it, we can't do anything.

---

### Post by lordfoul on 2008-11-16
Yah I know, but considering the title of this thread and the number of people complaining about this issue I thought it worth posting.

---

### Post by piggyb on 2008-11-18
Same problem...my bluetooth will not work at all. After about 10 minutes my phone gets found by mac address not friendly name and that is as far as it gets. I try to pair them but it just says pairing failed - the icon on my phone (k800i) also does nothing. I use pand to connect to my phone on 8.04 so I can browse the web but it is not provided with 8.10. Even after installing the bluez-compat library it still does not work. It is lucky that my 8.04 wouldn't upgrade to 8.10 because of other issues or I would have been right royaly screwed. It is a shame because I quite like 8.10 (hey it even has gfx drivers for my laptop! :) ) but without being able to get online it is as useful as a chocolate teapot. I hope this gets fixed SOON or my 8.10 partition is being overwritten by fedora 10 when it comes out - you got 7 days! For now I guess I'll just stick to 8.04 and hope for a fix (crosses fingers).

---

### Post by Yezinki on 2008-11-18
My Nokia N 93 pairs great...can send/receive files /data in secs.

---

### Post by peddy on 2008-11-18
> **Yezinki said:**
> My Nokia N 93 pairs great...can send/receive files /data in secs.

Could you please post the output of ```
dpkg -l | grep bluetooth
```?

Thanks :)

---

### Post by Yezinki on 2008-11-18
[B][SIZE="4"]ubuntu@ubuntu:~$ dpkg -l | grep bluetooth
ii  bluetooth                                 4.12-0ubuntu5                         Bluetooth support
ii  libbluetooth3                             4.12-0ubuntu5                         Library to use the BlueZ Linux Bluetooth sta
ubuntu@ubuntu:~$ 
[/SIZE][/B]




Good luck & have fun!

Regards,

Yezinki.

---

### Post by peddy on 2008-11-18
Oops, could you please do it replacing bluetooth with just 'blue'? So 
```
dpkg -l | grep blue
```

Thanks :)

---

### Post by bbengtsson on 2008-11-19
I was in the "no hcid.conf" thread with my bluetooth issue.
I have a D-Link DBT-120 BT dongle and a Logitech BT mouse.  When I plug the dongle in, I get the BT icon at the top of the screen.
I used the "Set up new device" wizard which showed no devices until I hit the reset button on the mouse.  Then the mouse BT address showed up.  I was able to pair with the mouse when I clicked on it's address in the wizard.  
I then tried to pair with my Blackberry 8330 and that worked as well.  However, when I tried to browse the Blackberry, the computer locked up.  Powered down and restarted.  The mouse paired up after reboot.

I have a fresh install of 8.10.....with XP dual boot.
First time Linux user.

---

### Post by Yezinki on 2008-11-19
```
ubuntu@ubuntu:~$ dpkg -l | grep blue
ii  bluetooth                                 4.12-0ubuntu5                         Bluetooth support
ii  bluez                                     4.12-0ubuntu5                         Bluetooth tools and daemons
ii  bluez-alsa                                4.12-0ubuntu5                         Bluetooth audio support
ii  bluez-cups                                4.12-0ubuntu5                         Bluetooth printer driver for CUPS
ii  bluez-gnome                               1.8-0ubuntu1                          Bluetooth utilities for GNOME
ii  bluez-gstreamer                           4.12-0ubuntu5                         Bluetooth gstreamer support
ii  bluez-utils                               4.12-0ubuntu5                         Transitional package
ii  libbluetooth3                             4.12-0ubuntu5                         Library to use the BlueZ Linux Bluetooth sta
ubuntu@ubuntu:~$ 
```

---

### Post by Yezinki on 2008-11-19
> **peddy said:**
> Oops, could you please do it replacing bluetooth with just 'blue'? So 
```
dpkg -l | grep blue
```

Thanks :)

Hope that helped......

---

### Post by Yezinki on 2008-11-19
```
ubuntu@ubuntu-laptop:~$ dpkg -l | grep bluetooth
ii  bluetooth                                 4.12-0ubuntu5                         Bluetooth support
ii  libbluetooth3                             4.12-0ubuntu5                         Library to use the BlueZ Linux Bluetooth sta
ubuntu@ubuntu-laptop:~$ dpkg -l | grep blue
ii  bluetooth                                 4.12-0ubuntu5                         Bluetooth support
ii  bluez                                     4.12-0ubuntu5                         Bluetooth tools and daemons
ii  bluez-alsa                                4.12-0ubuntu5                         Bluetooth audio support
ii  bluez-cups                                4.12-0ubuntu5                         Bluetooth printer driver for CUPS
ii  bluez-gnome                               1.8-0ubuntu1                          Bluetooth utilities for GNOME
ii  bluez-gstreamer                           4.12-0ubuntu5                         Bluetooth gstreamer support
ii  bluez-utils                               4.12-0ubuntu5                         Transitional package
ii  libbluetooth3                             4.12-0ubuntu5                         Library to use the BlueZ Linux Bluetooth sta
ubuntu@ubuntu-laptop:~$ 

```


For BT dongle on a fresh install of 8.10 without even updating it.........still pairs good with N 93.

Regards,

Yezinki.

---

### Post by peddy on 2008-11-19
Could you please post the output of 
```
uname -r
```
?

Thanks

---

### Post by Yezinki on 2008-11-19
ubuntu@ubuntu-laptop:~$ uname -r
2.6.27-7-generic
ubuntu@ubuntu-laptop:~$

---

### Post by Yezinki on 2008-11-19
peddy what exactly are you trying to achieve?

Regards,

Yezinki.

---

### Post by isecore on 2008-11-20
> **peddy said:**
> Could you please post the output of 
```
uname -r
```
?

Thanks

I'm not sure what you're trying to achieve, but my uname -r is 2.6.27-8-generic.

---

### Post by yurukov on 2008-11-20
Hi all, 

I have the same problem but with a Motorola PC850 dongle. It was recognized, but didn't work at all. Just now and again it found my stereo headphones, but showed just their mac address. 

The funny thing is that I have a Chinese (fake) bt dongle that normally doesn't work half of the time. In ubuntu it worked and managed to pair with my pda. It didn't however keep the connection for long.

I tried installing the original windows drivers through ndiswrapper and it did show that the hardware is recognized, but I couldn't use it in any way, since none of the bt tools seem to see it. I uninstalled the driver and now ubuntu won't find my dongle at all. 

Can someone help me fix the drivers/configuration problem or suggest a dongle that actually works in 8.10 and supports a2dp?

---

### Post by Yezinki on 2008-11-20
How many usb ports do  you have?

Buy a quality BT dongle not the one you mentioned?

Type pw correctly when trying to pair.

---

### Post by yurukov on 2008-11-20
3 usb ports. The Motorola Bluetooth dongle is one of the best ones out there. I mentioned the bad one just to illustrate that 8.10 has better support for the old ones. I never get to the point of entering the pairing code. Like I said - it doesn't work at all. Even when it recognized the dongle (before I tried the windows drivers), it didn't find any devices to pair with, although I had a few switched on discovery mode.

---

### Post by Yezinki on 2008-11-21
Its not the question of the best.

Motorola doesn't function in 8.10.

Buy like the one I have, costs around 20 bucks at CC or Office Depot.

---

### Post by peddy on 2008-11-21
> **Yezinki said:**
> peddy what exactly are you trying to achieve?

Regards,

Yezinki.

I was seeing what kernel you were running, so I could match your configuration exactly to determine whether the problem is with my BT adapter not being supported or whatever.

---

### Post by Yezinki on 2008-11-21
Did it help??

---

### Post by painterh on 2008-11-23
Hello;  Painterh here.  I have had somewhat similar issues with Intrepid and bluetooth.  I have a Microsoft Elite Keyboard and Explorer Mouse bluetooth set.  In Hardy, I had edited the default bluetooth file and also put in the mac address of my mouse and keyboard, so  finally (with a little more tweaking ) I got them to pair on boot-up.  They worked pretty well except that they would only pair when I turned my machine off and then re-started. They would not pair when just doing a restart without shutting completely.  Now, since upgrading to Intrepid, I was able to pair them using the new bluetooth applet.  The problem is whenever my mouse or keyboard is idle for a few minutes, it takes about 8 to 10 seconds for them to wakeup from the time I move the mouse or try to type on the keyboard. My mouse and keyboard still only pair on start, and not on restart (just like before), but I can live with that.  The sleeping issue happens every time and is extremely irritating.  It seems they took 2 steps forward and 1 backward when it comes to the way bluetooth works in intrepid.  If anyone knows of a fix for the delayed awakening of keyboard and mouse, I would really appreciate knowing about it.

---

### Post by Shankar108 on 2008-11-23
Hello all,

I just upgraded to Ubuntu 8.10 (Intrepid Ibex w/Gnome) and had similar problems with my Bluetooth Sony speaker (unable to pair with this device which has a hardcoded pincode). The problem is that the Gnome Bluetooth applet generates a random pincode and the Sony speaker has no way to respond to this pincode as it doesn't have a built-in keypad.

PROBLEM SOLVED! -- Just now I came across this page ([http://www.technetra.com/2008/11/22/pairing-stubborn-bluetooth-devices-in-fedora-10-ubuntu-ibex/](http://www.technetra.com/2008/11/22/pairing-stubborn-bluetooth-devices-in-fedora-10-ubuntu-ibex/)) -- which provides a script using DBus commands to pair Bluetooth devices. I tried it on my Ubuntu Ibex system and it definitely worked for me. I'm now able to pair my Sony speaker and use Rhythmbox.

HTH
Cheers

---

### Post by ukblacknight on 2008-11-23
I think someone needs to create a new thread: Bluetooth not pairing properly.

This thread was created originally about the fact that bluetooth doesn't work AT ALL.  Many people in here are complaining about things not pairing.  Different issues.

Original issue: Bluetooth doesn't work. period. It can't find the adapter. We can't configure the adapter.  Pairing isn't the problem here!

Anyone know if there is going to be a fix for this?

---

### Post by Yezinki on 2008-11-23
Agreed...Start a new thread about BT Pairing issues!

Regards,

Yezinki.

---

### Post by ImNeat on 2008-11-23
> **ImNeat said:**
> Now I just need it to auto-pair on reboot or after idling.

I was able to solve my pairing problems. I removed all bluetooth-related packages and deleted all related configuration files. I then installed the Bluetooth Analyzer package in Add/Remove.  I manually executed bluetooth-applet and I setup my keyboard. The pairing now survives timeouts and reboots.

---

### Post by gatman3 on 2008-11-24
Just a total shot in the dark, but... I think I had the same Belkin adapter with my old laptop, and in 7.10 (if memory serves) it would load the pegasus driver instead of the proper driver (can't remember which one it was).  Do an lsmod and see if the pegasus driver loaded by mistake, and if it did add a line to your /etc/modprobe.d/blacklist to blacklist the pegasus driver.

Of course... it's probably something else... but thought I'd share in case this is the problem.

---

### Post by paranoid_humanoid on 2008-11-25
at first i couldn't send stuff from my mobile phone to ubuntu, now i can't even browse the files on my phone too. this is really getting on my nerves :mad:

---

### Post by bigbrovar on 2008-11-25
I think ubuntu should really work on the standard of its releases especially when basic things like bluetooth ,webcam, and inbult mic dont work .. things that just use to work in feisty (my first ubuntu all the way to hardy) are we making progress or are we going backwards. we are nolonger an OS for hubbiest we are a serious OS and if we want to be mainstream problems like this are just not acceptable. maybe its the 6 months release period.

---

### Post by mac.ryan on 2008-11-26
Paranoid Humanoid... This is the bug I filed. You might go there and click on "this bug affects me too" to get it higher on the priority queue...

Differently than other bugs, I also experience an inconsistent behaviour of the BT connectivity.

[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/298430](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/298430)

---

### Post by lordfoul on 2008-11-26
New reply to this bug...[https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/284982/comments/20](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/284982/comments/20)

---

### Post by isecore on 2008-11-27
> **lordfoul said:**
> New reply to this bug...[https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/284982/comments/20](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/284982/comments/20)

I'm running Bluez 4.19 from that repo (the Blueman-repo PPA) and it's still dead for me. Well, mostly dead. The icon appears upon login, and it has my hostname pre-filled in. But make any changes and it dies, and it's still a dud as far as anything else goes.

---

### Post by drsjp on 2008-11-27
> **bigbrovar said:**
> I think ubuntu should really work on the standard of its releases especially when basic things like bluetooth ,webcam, and inbult mic dont work .. things that just use to work in feisty (my first ubuntu all the way to hardy) are we making progress or are we going backwards. we are nolonger an OS for hubbiest we are a serious OS and if we want to be mainstream problems like this are just not acceptable. maybe its the 6 months release period.
I have to agree that, while I'm impressed with Intrepid, I'm also slightly disappointed that Linux products are not completed and well tested before release. My BT is recognised, but it seems that the problem is more related to pairing. It also seems that this is the problem experienced by most.

---

### Post by okkie on 2008-11-27
same story 32bit x86.Has been my problem after every upgrade

---

### Post by peddy on 2008-11-28
Ah, using the Blueman Intrepid PPA, Bluetooth is MUCH better, in fact I was a little excited that it was going to start working perfectly. Here's what worked:

Device pairing: I was able to 'set up new device', and enter the key on both my mobile phone and computer. Pairing was successful. The computer updated my phone's updated Bluetooth name (not a big thing but at least it worked)

Here's what didn't work: 
Pretty much everything else bluetooth-related, but more specifically,
Obex ```
Could not display obex://[my.phone's.mac.address]. Error: Connection to the device lost
Please select another viewer and try again.
```

I haven't tried serial port services and such, though.

A question for someone, if you right-click on the Bluetooth icon in your system tray, and choose 'preferences', is there a 'services' tab? Because there isn't for me.

Cheers

---

### Post by fluid_motion on 2008-11-28
I hope this gets fixed soon or someone finds a workaround, my bluetooth dongle can't be detected and it worked fine in all previous versions. Its so annoying when something breaks after you upgrade.

---

### Post by Yezinki on 2008-11-28
I bought a 18 bucks Silicon Cambridge radios, BT Dongle from Office Depot for this Sony machine worked great no issues....

Visit their website.

---

### Post by fluid_motion on 2008-11-30
Somehow I managed to get it to work with a reinstall by accident. 

I followed the directions here for setting up blueman, installed then it removed some bluez files. Restart and it still didn't work so I ran install for bluez and then it worked. weird.

Update: It doesn't work again after a restart, uninstall and reinstall bluez only loads it for that session. Something is not loading right. Back to the drawing board...

---

### Post by peddy on 2008-12-02
I just installed Bluez and obexd from source, and I still can't pair or use OBEX or anything like that. Bluetooth does not work in a clean install either :/

---

### Post by stz184 on 2008-12-03
Jist tried to install Blueman. Bluez dissaper after installing of Blueman (I think they can't work simulationly o.O). I have the same problem with Blueman - can't pair the phone.Hope somebody smarter than me with find out a solution.:D

---

### Post by paranoid_humanoid on 2008-12-04
the whole thing is just starting to sound less like a bug and more like a gypsy curse. what's happened to our ubuntu guys! why isn't anyone from the developers trying to fix this!? it's been long enough now. i'd hate to have to downgrade to hardy again :(

---

### Post by peddy on 2008-12-04
> **paranoid_humanoid said:**
> the whole thing is just starting to sound less like a bug and more like a gypsy curse. what's happened to our ubuntu guys! why isn't anyone from the developers trying to fix this!? it's been long enough now. i'd hate to have to downgrade to hardy again :(

Yeah, this is ridiculous, Bluetooth even works in Damn Small Linux, a 50MB minimalist distro. :/

---

### Post by Yezinki on 2008-12-04
I don't understand why its become such a big issue.

When I had 8.10 installed as my OS, no issues with BT dongle or pairing with N93, sending receiving files......

What are you guys doing?

Regards,

Yezinki.

---

### Post by OverlordManny on 2008-12-04
Well the new Blueman for Intrepid is in the PPA repo at launchpad. I have installed it and it works great. I think that our issue was/is bluez-gnome because once I installed Blueman it showed a history of seeing my cell phone and it was off. Bluez must have been seeing it even though Bluez-gnome didn't, just a guess though. The version of Bluez in the Blueman repo is 4.22, which is the newest. Hope this helps you guys. Here's the addy:

[https://launchpad.net/~blueman/+archive](https://launchpad.net/~blueman/+archive)

BTW Bluez gnome STILL doesn't see my adapter, WTH? Lol

---

### Post by PowerPanda on 2008-12-04
Hey you mentioned the version of bluez 4.22, but when I install blueman from that repo bluez is removed. Is that how it's supposed to be? Blueman seems to install bluetooth3 instead of 4.

---

### Post by PowerPanda on 2008-12-04
My Blueman gets stuck at Resolving Names.

---

### Post by russofris on 2008-12-05
Good evening,

I am considering an Intrepid installation on my wife's PC after she inquired about Linux.  She's using a Logitech MX5500 combo.  Has this issue been resolved to the satisfaction of other users utilizing this kybd/mouse set?  I would like only need to discover and set the devices "once", never to repeat the procedure.  I'll be really upset if I receive constant nagging "my keyboard isn't working" requests from her.

So what's the skinny?
Frank

---

### Post by peddy on 2008-12-05
Hi russofris, 

Installing Hardy for now sounds like a good idea, especially if you're going to be using BT for an input device. BT worked perfectly and out-of-the-box for me and many other users. 

It's not a bad idea to try the Intrepid live CD though, and see if Bluetooth works on your hardware.

---

### Post by benvantende on 2008-12-05
Hey,

I see some positive and negative remarks. Very confusing to me. I am still not going to upgrade to Intrepid until i see a full page here with enthousiastic replies.

gRTz

ben

---

### Post by isecore on 2008-12-05
> **russofris said:**
> Good evening,

I am considering an Intrepid installation on my wife's PC after she inquired about Linux.  She's using a Logitech MX5500 combo.  Has this issue been resolved to the satisfaction of other users utilizing this kybd/mouse set?  I would like only need to discover and set the devices "once", never to repeat the procedure.  I'll be really upset if I receive constant nagging "my keyboard isn't working" requests from her.

So what's the skinny?
Frank

Bluetooth is still a dud for me. So far Intrepid has been a most anticlimactic experience for me.

---

### Post by ndale686738 on 2008-12-05
I finally got my bluetooth working correctly in Intrepid by installing blueman. Thanks goes to launchpad for making a repo for easy dependency resolution, blueman uses older libraries and it is a major drag to install them manually since several packages appear to have circular dependencies. i Have detailed the steps i took below. 

1) remove blues-compat if its installed (failure to remove will result in install failure and broken packages in following steps)
```
sudo apt-get remove bluez-compat 
```

2) add the blueman repo, also need to make sure "universe" is enabled
```
sudo sh -c "echo 'deb http://ppa.launchpad.net/blueman/ubuntu $(lsb_release -sc) main' >/etc/apt/sources.list.d/blueman.list"
```

3) install updated (actually the old) packages
Your package manager should pop up with updates. if not go to System/Administration/Update Manager and install all the updates

4) install blueman
```
sudo apt-get install blueman 
```

5) configure blueman
start blueman from the terminal so you can see whats going on by typing "blueman"

click "List Seen" and select the device. 
-select bond (i used passkey of 0000) (may have to hit the connect button on the device to get passkey prompt)
-select other/add trust
-selct edit/services and click the config icon next to input. remove the device shown there and click close

my mouse started working right away and it initializes automatically on reboot. i now like bluetooth again:D

hope this helps someone else

---

### Post by russofris on 2008-12-05
> **peddy said:**
> Hi russofris, 

Installing Hardy for now sounds like a good idea, especially if you're going to be using BT for an input device. BT worked perfectly and out-of-the-box for me and many other users. 

It's not a bad idea to try the Intrepid live CD though, and see if Bluetooth works on your hardware.

Agreed,

I run intrepid on my personal machine and like the majority of changes.  Unfortunately, the livecd does not detect the MX5500 combo (as expected).  It works for the BIOS,, it works for grub and the language select, but does not seem to be properly detected on init.

I am taking a look at the instructions posted for removing blue compat and rolling back the bluetooth stack which someone kindly posted.  I may simply wait a couple weeks for the devs to work out the remaining issues.

Thanx much,
Frank

---

### Post by Morientes on 2008-12-05
I really love Ubuntu in general but this issue does not make it look good! It's taking quite a long time to find a fix. :-(
Let's hope it will be here soon...

---

### Post by PowerPanda on 2008-12-06
Well blueman doesn't work for me at all now. It doesn't even find my mouse when I click inquiry (and click connect on mouse). It used to find it before but just not bond.

I am in 64bit ubuntu as well btw.

---

### Post by paranoid_humanoid on 2008-12-06
installed blueman and it did nothing for me too.. bummer...

---

### Post by russofris on 2008-12-06
I have found that many things do not work under the 64bit versions of most distributions (console FB was the killer for me).  I would highly recommend running the 32bit build for general use, and only installing the 64bit version if you want to contribute to fixing the issues (contributing includes filing defects).  Unfortunately, most of us do not have the time or patience to do this on our main PCs.

Alternatively, you may have an actual need for a 64bit OS.  

Frank

---

### Post by peddy on 2008-12-06
With today's updates, I thought the problem was fixed, as pairing worked flawlessly and the services menu was there. But then I got the dbus error again. :(

---

### Post by paranoid_humanoid on 2008-12-06
update: i'm able to send stuff from my phone to ubuntu now if gnome-obex-server is running.

---

### Post by paranoid_humanoid on 2008-12-07
i found a stupid work-around to get things working.
i got remuco-server to work by installing libbluetooth2 from [http://packages.ubuntu.com/hardy/libbluetooth2](http://packages.ubuntu.com/hardy/libbluetooth2) as it said so on their wiki.

after then i initiate a connection from my phone's remuco-client to the remuco-server and it works fine. during the connection between my phone and ubuntu i can pretty much do anything. browse the phone, send stuff from ubuntu to the phone and vice versa :D

---

### Post by PowerPanda on 2008-12-10
The new updates didn't seem to fix anything for me. Hrm

---

### Post by isecore on 2008-12-10
> **russofris said:**
> I have found that many things do not work under the 64bit versions of most distributions (console FB was the killer for me).  I would highly recommend running the 32bit build for general use, and only installing the 64bit version if you want to contribute to fixing the issues (contributing includes filing defects).  Unfortunately, most of us do not have the time or patience to do this on our main PCs.

Alternatively, you may have an actual need for a 64bit OS.  

Frank

But unless we actually start using the 64-bit version, this will never change. I'm not a developer, but I run 64-bit Ubuntu and have been quite happy with it. It wasn't until Intrepid that things started to go funky.

I don't buy into this attitude that 64-bit is somehow more mystical and magical than regular 32-bit platforms. It isn't. Especially not with open-source software which is (relatively) easily transposed from one to the other.

64-bit is the future. With the current trends of memory being essentially free more and more people will want a 64-bit operating system to fully take advantage of things like this. Advising them against it and acting as if 64-bit systems are inherently more buggy is just counter-productive. Especially since this isn't Windows, where the workings are hidden from us.

---

### Post by peddy on 2008-12-10
> **isecore said:**
> But unless we actually start using the 64-bit version, this will never change. I'm not a developer, but I run 64-bit Ubuntu and have been quite happy with it. It wasn't until Intrepid that things started to go funky.

I don't buy into this attitude that 64-bit is somehow more mystical and magical than regular 32-bit platforms. It isn't. Especially not with open-source software which is (relatively) easily transposed from one to the other.

64-bit is the future. With the current trends of memory being essentially free more and more people will want a 64-bit operating system to fully take advantage of things like this. Advising them against it and acting as if 64-bit systems are inherently more buggy is just counter-productive. Especially since this isn't Windows, where the workings are hidden from us.

I completely agree. Besides, BT still doesn't work on a 'regular' i386 arch install, either. I've tried with a clean install.

---

### Post by nkri on 2008-12-11
I've been having the same problems as most people...no bluetooth at all, and it won't detect the adapter.

I tried installing Blueman, and it hasn't solved the problem, but it has provided some insight as to what's going on: at the bottom of the Blueman window, it says "Can't get device list.  Reason: 'module' object has no attribute 'adapter'"

What is a module object, and with what other programs is it assosiated?  I'm wondering if this is at all similar to a problem in Hardy with Wacom tablets, where all that was missing was a link to the Wacom driver.  Is there some vital file or missing link which would solve the problem altogether?

I also agree with what everyone has been saying about this...if we want Ubuntu to be more mainstream, there really shouldn't be problems with something as widely used as bluetooth:(

-nkri

---

### Post by Xirtambus on 2008-12-11
> **ndale686738 said:**
> I finally got my bluetooth working correctly in Intrepid by installing blueman. Thanks goes to launchpad for making a repo for easy dependency resolution, blueman uses older libraries and it is a major drag to install them manually since several packages appear to have circular dependencies. i Have detailed the steps i took below. 

1) remove blues-compat if its installed (failure to remove will result in install failure and broken packages in following steps)
```
sudo apt-get remove bluez-compat 
```

2) add the blueman repo, also need to make sure "universe" is enabled
```
sudo sh -c "echo 'deb http://ppa.launchpad.net/blueman/ubuntu $(lsb_release -sc) main' >/etc/apt/sources.list.d/blueman.list"
```

3) install updated (actually the old) packages
Your package manager should pop up with updates. if not go to System/Administration/Update Manager and install all the updates

4) install blueman
```
sudo apt-get install blueman 
```

5) configure blueman
start blueman from the terminal so you can see whats going on by typing "blueman"

click "List Seen" and select the device. 
-select bond (i used passkey of 0000) (may have to hit the connect button on the device to get passkey prompt)
-select other/add trust
-selct edit/services and click the config icon next to input. remove the device shown there and click close

my mouse started working right away and it initializes automatically on reboot. i now like bluetooth again:D

hope this helps someone else

*CONFIRMED*

This fix works. Thank you :)

---

### Post by isecore on 2008-12-11
> **ndale686738 said:**
> I finally got my bluetooth working correctly in Intrepid by installing blueman. Thanks goes to launchpad for making a repo for easy dependency resolution, blueman uses older libraries and it is a major drag to install them manually since several packages appear to have circular dependencies. i Have detailed the steps i took below. 

1) remove blues-compat if its installed (failure to remove will result in install failure and broken packages in following steps)
```
sudo apt-get remove bluez-compat 
```

2) add the blueman repo, also need to make sure "universe" is enabled
```
sudo sh -c "echo 'deb http://ppa.launchpad.net/blueman/ubuntu $(lsb_release -sc) main' >/etc/apt/sources.list.d/blueman.list"
```

3) install updated (actually the old) packages
Your package manager should pop up with updates. if not go to System/Administration/Update Manager and install all the updates

4) install blueman
```
sudo apt-get install blueman 
```

5) configure blueman
start blueman from the terminal so you can see whats going on by typing "blueman"

click "List Seen" and select the device. 
-select bond (i used passkey of 0000) (may have to hit the connect button on the device to get passkey prompt)
-select other/add trust
-selct edit/services and click the config icon next to input. remove the device shown there and click close

my mouse started working right away and it initializes automatically on reboot. i now like bluetooth again:D

hope this helps someone else

I've tried this. It does not work for me. When installing the older Bluez 3.x-packages I get a long list of confusing (non-apt) related errors. Bluetooth is still as dead as before - I cannot send or receive files from my phone, or bond a headset to my computer.

---

### Post by cleentrax on 2008-12-12
Any resolution here?

I have a USB Bluetooth adapter that will work on my Home Theatre PC (running Intrepid) but not on my Acer Aspire One (also running Intrepid).

Bluetooth adapter simply isn't recognized. It's like it's not there. I've tried everything in this thread -- blueman included, with no luck.

---

### Post by nkri on 2008-12-12
> **cleentrax said:**
> Any resolution here?

I have a USB Bluetooth adapter that will work on my Home Theatre PC (running Intrepid) but not on my Acer Aspire One (also running Intrepid).

Bluetooth adapter simply isn't recognized. It's like it's not there. I've tried everything in this thread -- blueman included, with no luck.

I think this is what is making this issue so hard to solve; some people's bluetooth works all around...for some people, Ubuntu can't seem to find their internal adapter...for some people Ubuntu can't find their USB adapters; the list goes on.

In my case, the bluetooth receiver for my Logitech V450 Nano works flawlessly, while my internal bluetooth adapter is not even recognized.  I'm wondering if this is a kernel/hardware related issue where the kernel can only recognize certain types or brands of bluetooth adapters.  Maybe we should all post our specs and see if there is any consistent similarity between the computers that aren't working and the ones that are?

I have a Toshiba Portege M400 running 2.6.27-9-generic-i686; not sure about the make of the bluetooth adapter, but I would venture a guess that it's Intel since that what most other hardware is on this system.

-nkri

---

### Post by ndale686738 on 2008-12-12
I agree that the issues need to be broken up into at least two main categories. I think this thread can still be useful if the posts have more information. Just posting that you agree that it sucks and yours does not work either does not contribute to solutions. Perhaps just following the below guidelines will give this thread some direction without having to split it.

[B]
Main Issue 1 - Bluetooth controller is not being detected (or more likely there is an error loading it).[/B]
try to find out what kind of controller it is and list any previous releases or distributions it did work with on your current hardware setup. Even though the same models may have different hardware is might be useful to know it is a "inspiron 1521 running X64"

try installing the gnome-device-manager with apt and see if it tells any information about the device at all. 

Internal bluetooth is installed under a usb controller also so if its not detected regardless of whether your bluetooth is internal or external post the following inside of "code" tags. 

a. The last 30 lines or so from a "dmesg" command run in a terminal after you connected the USB device.
b. "lsusb"

Before you just post without looking at the output for yourself try some searches on the output, even if you have no idea what it all means there might actually be an error that is intuitive enough to be recognized as an error and a search could lead you to the solution immediately.

[B]
Main issue 2 - Controller is detected but i cannot attach a device[/B]
This is perhaps a much broader issue.
a) Post the exact make and model of the equipment you are tring to connect. Some equipment have solutions that have been created specifically for them.
b) Post what you have already tried in detail, maybe a simple step could create a solution out of what you have already done.

Happy posting, the Linux community has ALWAYS helped me solve my problems, usually because someone posted useful information about their issue.\\:D/

---

### Post by nkri on 2008-12-12
> **ndale686738 said:**
> I agree that the issues need to be broken up into at least two main categories. I think this thread can still be useful if the posts have more information. Just posting that you agree that it sucks and yours does not work either does not contribute to solutions. Perhaps just following the below guidelines will give this thread some direction without having to split it.

[B]
Main Issue 1 - Bluetooth controller is not being detected (or more likely there is an error loading it).[/B]
try to find out what kind of controller it is and list any previous releases or distributions it did work with on your current hardware setup. Even though the same models may have different hardware is might be useful to know it is a "inspiron 1521 running X64"

try installing the gnome-device-manager with apt and see if it tells any information about the device at all. 

Internal bluetooth is installed under a usb controller also so if its not detected regardless of whether your bluetooth is internal or external post the following inside of "code" tags. 

a. The last 30 lines or so from a "dmesg" command run in a terminal after you connected the USB device.
b. "lsusb"

Before you just post without looking at the output for yourself try some searches on the output, even if you have no idea what it all means there might actually be an error that is intuitive enough to be recognized as an error and a search could lead you to the solution immediately.

[B]
Main issue 2 - Controller is detected but i cannot attach a device[/B]
This is perhaps a much broader issue.
a) Post the exact make and model of the equipment you are tring to connect. Some equipment have solutions that have been created specifically for them.
b) Post what you have already tried in detail, maybe a simple step could create a solution out of what you have already done.

Happy posting, the Linux community has ALWAYS helped me solve my problems, usually because someone posted useful information about their issue.\\:D/

Yup, the above steps are exactly what we need to get this issue sorted out:)

I fall under Main Issue 1: the kernel fails to load the bluetooth module and does not detect the adapter.

I took a look in System Log, and found that when trying to load bluetooth, it can't initiate a plugin; I attached the relevant information from /var/log/daemon.log and /var/log/messages.

I did a google search and it returned nothing helpful, just more people having the same problems.

-nkri

---

### Post by Stiff on 2008-12-14
My dongle ```
Bus 002 Device 002: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
```
not works in intrepid with kernel 2.6.27. It can scan devices, but cannot connect to any services on them.
But this dongle works fine with kernel 2.6.24 from hardy.
Of course, it is regression.
I have reinstall ubuntu 8.04 on my computer, but i can post the logs of dmesg, lsusb or something else if i boot from livecd. Ask me what logs to post if it is necessary.

---

### Post by ndale686738 on 2008-12-15
> **nkri said:**
> Yup, the above steps are exactly what we need to get this issue sorted out:)

I fall under Main Issue 1: the kernel fails to load the bluetooth module and does not detect the adapter.

I took a look in System Log, and found that when trying to load bluetooth, it can't initiate a plugin; I attached the relevant information from /var/log/daemon.log and /var/log/messages.

I did a google search and it returned nothing helpful, just more people having the same problems.

-nkri

Nkri, I found a bug report that has the same errors you are getting here. [https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/284982](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/284982)
there is reports about half way down about blueman getting some functionality back. Have you tried the steps i posted previously for installing blueman using the launchpad repo?

---

### Post by nkri on 2008-12-16
> **Stiff said:**
> My dongle ```
Bus 002 Device 002: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
```
not works in intrepid with kernel 2.6.27. It can scan devices, but cannot connect to any services on them.
But this dongle works fine with kernel 2.6.24 from hardy.
Of course, it is regression.
I have reinstall ubuntu 8.04 on my computer, but i can post the logs of dmesg, lsusb or something else if i boot from livecd. Ask me what logs to post if it is necessary.

Would you mind posting /var/log/daemon.log and /var/log/messages, as well as your computer specs?

Also, could you post the output of
```
dmesg | grep 'Bluetooth'
```

Thanks!

> **ndale686738 said:**
> Nkri, I found a bug report that has the same errors you are getting here. [https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/284982](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/284982)
there is reports about half way down about blueman getting some functionality back. Have you tried the steps i posted previously for installing blueman using the launchpad repo?

Yeah, I tried Blueman and it says that it can't detect the adapter; here's exactly what it says:
> Can't get device list.  Reason: 'module' object has no attribute 'adapter'

It would be great if you could also post your specs; if there is one type or brand of computer on which this is happening, we'll have better chance of fixing it:)

-nkri

---

### Post by cleentrax on 2008-12-16
With yesterday's updates, my bluetooth modules is now recognized, and can see my phone. So, progress.

Now I need to find a way to access my phone's Edge data over bluetooth -- tethered as a modem to my Aspire netbook. Doesn't seem to be an easy way to do this in Intrepid, which is a shame. It's dead simple on my MacBook in OSX 10.5.

---

### Post by abhitux on 2008-12-17
My bluetooth works with Blueman as detailed on these pages. The reason why it wasn't connecting to my phone properly was because my Nokia supports 2.0 while the older bluetooth dongle just supported 1.1. I got myself a brand new dongle and it worked out of the box! Voila! I can browse my phone, send and receive files without any problems. Sometimes, the solution to the problem can be quite elementary. I hope that this helps. Though I do agree that it should work out of the box to make it more cooler.  :guitar:

---

### Post by EEed on 2008-12-17
I had not used Linux for a long time and was recommended Ubuntu. I loaded up Intrepid - maybe four weeks ago - specifically to do a Bluetooth project. I bought the book Bluetooth Essentials for Programmers, and I was able to get the first example for GNU/Linux compiled and run. It detected my iPhone as well as an older Motorola Phone. Try as I might using the HCItools or adding to the program I could never connect. I did a number of posts - hopefully to the right forums - and I received some answers. No matter what I tried I could not connect.

Last night, at the end of my wits, I tried simply clicking on the Bluetooth icon at the top of the page. Low and behold the wizard itself could not find either phone, both put in discoverable mode or not.

I am sad: I became familiar with Ubuntu, love it, but can not get my work (priority one!) done. I did notice that bluez has a newer version than the one in Intrepid. Is there a way to use this? I am really hurting!

Thanks,

EEed

---

### Post by EEed on 2008-12-17
BTW, I am using a D-Link DBT-120 with the Cambridge chip on an HP DV1300 laptop.

EEed

---

### Post by nkri on 2008-12-17
> **abhitux said:**
> My bluetooth works with Blueman as detailed on these pages. The reason why it wasn't connecting to my phone properly was because my Nokia supports 2.0 while the older bluetooth dongle just supported 1.1. I got myself a brand new dongle and it worked out of the box! Voila! I can browse my phone, send and receive files without any problems. Sometimes, the solution to the problem can be quite elementary. I hope that this helps. Though I do agree that it should work out of the box to make it more cooler.  :guitar:

That's interesting...so maybe the kernel only supports bluetooth 2.0?  Would you mind posting your specs?

> **EEed said:**
> I had not used Linux for a long time and was recommended Ubuntu. I loaded up Intrepid - maybe four weeks ago - specifically to do a Bluetooth project. I bought the book Bluetooth Essentials for Programmers, and I was able to get the first example for GNU/Linux compiled and run. It detected my iPhone as well as an older Motorola Phone. Try as I might using the HCItools or adding to the program I could never connect. I did a number of posts - hopefully to the right forums - and I received some answers. No matter what I tried I could not connect.

Last night, at the end of my wits, I tried simply clicking on the Bluetooth icon at the top of the page. Low and behold the wizard itself could not find either phone, both put in discoverable mode or not.

I am sad: I became familiar with Ubuntu, love it, but can not get my work (priority one!) done. I did notice that bluez has a newer version than the one in Intrepid. Is there a way to use this? I am really hurting!

Thanks,

EEed

I agree...I need bluetooth for school, and am actually in the process of finding a temporary(?) new distro until this gets fixed.  I built (and attached) the new version of Bluez into a .deb for i386 architecture.  It doesn't seem to change anything on my system, but maybe it'll work for you:)

Before you install it, though, type the following 2 commands into a Terminal so the package will install correctly:
```
sudo mkdir /etc/bluetooth
```
```
sudo mkdir /usr/local/lib/bluetooth
```

-nkri

---

### Post by EEed on 2008-12-17
I am sorry but my previous post that stated the Bluetooth Wizard could not find either my iPhone or my Motorola phone was INCORRECT! Actually, the reason they did not appear in the search was that they had already been found. Sorry, not that familiar with the wizard. 

After selecting "Browse files on device":


The iPhone error window reads:

Could not display "obex://[00:21:E9:44:36:02]/".

Error: Service search failed
Please select another viewer and try again.

I believe that the iPhone does not offer this service,
so this might be OK.

Then trying the Motorola, the error window reads:

Could not display "obex://[00:15:A8:D4:3D:E6]/".

Error: Connection to the device lost
Please select another viewer and try again.

After selecting grant access on the phone and trying it again it does in fact display the files.

If there is anything else I could try or report I would be quite happy to do so. Thanks,

Ed

---

### Post by EEed on 2008-12-17
nkri,

Thank you. The first directory I have, the second I made. Are you able to give me the code (or method to use) to install the deb file you were so kind to make for me?

Thanks again,

Ed

---

### Post by nkri on 2008-12-17
To install it via GUI, you just double-click on the .deb and click "Install," then type your password and you're good to go!

If you want to install from Terminal, cd into the directory where you saved the file; for example, if you saved it to the desktop, type
```
cd Desktop
```

Once in the correct directory, type
```
sudo dpkg -i bluez_4.22-1_i386.deb
```

This will install it for you, and it should work right away, but you might want to try restarting just to be sure:)

Good luck!
-nkri

---

### Post by EEed on 2008-12-17
Thank you, nkri! I have completed the install - thanks to you - and now I will restart!

Ed

---

### Post by EEed on 2008-12-18
I did the install of 4.22, thanks to all the help from Nkri. Now I have no Bluetooth wizard and hciconfig, etc. do not work. Do I have to turn on bluetooth or . . .? Any ideas I would appreciate since I am not sure how to proceed with this development project. Thank you, Ed

---

### Post by nkri on 2008-12-18
Did you uninstall the repository version of Bluez before installing the new one?  If not, try that...the actual program (the wizard and such) works fine on my system, but it still can't seem to detect the adapter.

Good luck!
-nkri

---

### Post by c0mp13371331337 on 2008-12-23
Having similar problems to everyone else here.  I suppose I'm one of the lucky ones, relatively speaking, as my system is recognizing my bluetooth adapter at least.  It's picking up on my phone (LG Rumor), both by name and by MAC address.  However, I'm unable to do anything with detected devices.  I tried connecting two different Wii-motes, as well as my phone and my bluetooth headset.  Nothing is able to pair.

I followed the instructions for installing blueman provided by a previous poster.  That kind of seemed to work, although I'm still not able to bind or pair, or do anything else for that matter.  I've got Intrepid (x64) that was a fresh install from a few weeks before it came out of beta, all packages are up to date (with the exception of the ones that I downgraded from the blueman repos).  I've spent hours trying to get this working, but it's coming to the point where I'll probably just wait for the packages to be fixed.

Bluetooth adapter is just a generic e-bay special, model DZ-006.  If anyone wants any more information, let me know and I'd be more than happy to provide it.  Thanks!

---

### Post by nkri on 2008-12-24
> **c0mp13371331337 said:**
> Having similar problems to everyone else here.  I suppose I'm one of the lucky ones, relatively speaking, as my system is recognizing my bluetooth adapter at least.  It's picking up on my phone (LG Rumor), both by name and by MAC address.  However, I'm unable to do anything with detected devices.  I tried connecting two different Wii-motes, as well as my phone and my bluetooth headset.  Nothing is able to pair.

I followed the instructions for installing blueman provided by a previous poster.  That kind of seemed to work, although I'm still not able to bind or pair, or do anything else for that matter.  I've got Intrepid (x64) that was a fresh install from a few weeks before it came out of beta, all packages are up to date (with the exception of the ones that I downgraded from the blueman repos).  I've spent hours trying to get this working, but it's coming to the point where I'll probably just wait for the packages to be fixed.

Bluetooth adapter is just a generic e-bay special, model DZ-006.  If anyone wants any more information, let me know and I'd be more than happy to provide it.  Thanks!

Would you mind posting the outputs of
```
hcitool dev
```
and
```
grep | dmesg 'Bluetooth'
```

That would be great, and also could you post your computer/bluetooth adapter specs?

Thanks!
-nkri

---

### Post by c0mp13371331337 on 2008-12-25
> **nkri said:**
> >Would you mind posting the outputs of
```
hcitool dev
```

Certainly,

```
me@ISUS:~$ hcitool dev
Devices:
    hci0    00:11:67:3E:82:7A
me@ISUS:~$ 

```> **nkri said:**
> >and
```
grep | dmesg 'Bluetooth'
```

```

me@ISUS:~$ dmesg | grep 'Bluetooth'
[   21.594561] Bluetooth: Core ver 2.13
[   21.600612] Bluetooth: HCI device and connection manager initialized
[   21.603714] Bluetooth: HCI socket layer initialized
[   22.175049] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   31.567827] Bluetooth: L2CAP ver 2.11
[   31.567831] Bluetooth: L2CAP socket layer initialized
[   31.583717] Bluetooth: RFCOMM socket layer initialized
[   31.583735] Bluetooth: RFCOMM TTY layer initialized
[   31.583743] Bluetooth: RFCOMM ver 1.10
[  383.337467] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  383.337477] Bluetooth: BNEP filters: protocol multicast
me@ISUS:~$ 

```> **nkri said:**
> >That would be great, and also could you post your computer/bluetooth adapter specs?

My computer specs are:
Asus P5N-D mobo
Intel Core 2 Quad Q6700
4GB G-Skill RAM
Asus nVidia 8800GTS 512MB GPU
WD 250GB HD + older WD 60GB HD

Bluetooth adapter, not so sure about.  It's an 'el-cheapo' adapter that my wife got off e-bay.  I'm attaching a picture of it, maybe someone will recognize it.  No brand/model listed anywhere on the device, or on the ebay listing for it.

> **nkri said:**
> >Thanks!

No, thank you!

> **nkri said:**
> >-nkri

---

### Post by Lesterchakyn on 2008-12-26
There's something funny about all this "Bluetooth not working in Intrepid fuzz".

I've been using Intrepid since the betas and bluetooth worked with no problems, I paired the computer (Lenovo T61) to 2 phones and a gps receiver and had no trouble sending and receiving files, or finding my location.

Last week I got an Acer Aspire One, and I brought a micro Bluetooth receiver.

After two days of pain, I decided to stop trying, thinking maybe even in upgrading the kernel, because the thing didn't work at all.  It showed on the panel, but no sync, no pairing, nothing.

Ocassionaly it would pair and only once I was able to send one file.

I tried with another bluetooth dongle that I had with me, and the exactly same thing happened.

Then it came to me, I had been using the Lenovo machine with NO PROBLEMS, so I found another BT stick lying around, I connected and It Worked!!!

It seems that some kernel/package update broke only some kinds of hardware, while others still work with no problems.

I can't find the right bug filing to put this and information about my 4 BT devices, anyone one knows which is it?

---

### Post by ravi.xolve on 2008-12-26
Its here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/297075](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/297075)

---

### Post by Sjums07 on 2008-12-27
Okay, new problem at me :p i can pair, send from pc to my SE k750i, scan with hcitool, open and browse, BUT i can't send files from my k750i to my laptop :/ WHY!!! evil world!? :/

I'm using a build in BT adapter,

---

### Post by chrisinspace on 2008-12-29
Same problem here.  I started a [_thread_]("http://ubuntuforums.org/showthread.php?t=1016810") on the topic, thinking my issue seemed a little different, but after a couple of exchanges with nkri, I realized it's probably related.

Has anyone who is working on the kernel or the BT stack weighed in on this thread or a thread in any other forum? It would be nice to have an official update or some feedback.  This seems to be a wide-spread problem.  Intrepid has been out for a couple months now, so I'm really hoping there is an effort to correct the issue.

Can anyone enlighten us users?

---

### Post by nkri on 2008-12-30
We've been testing new things in [_this_]("https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/284982") bug report, and downgrading to the Hardy kernel seems to be a good workaround (not a fix, though), at least temporarily.  For me, bluetooth worked with this kernel, but the wireless was messing with my router so I had to go back to the Intrepid kernel.  Other people have said this method works fine for them, so it's probably worth a shot:)
-nkri

---

### Post by ebruzzone on 2009-01-01
Hi everyone! 

I was having the same problem with Intrepid. In Hardy I used a usb mouse (Asus) and I received the infamous sudo: hidd not found... 

what I did

1. uninstall bluez -- using synaptic

2. type hidd hidd --connect
3. then the terminal replied that 

The program 'hidd' is currently not installed.  You can install it by typing:
sudo apt-get install bluez-compat
bash: hidd: command not found

4. so I did! 

eric@eric-desktop:~$ sudo apt-get install bluez-compat
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bluez-compat
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 53.1kB of archives.
After this operation, 193kB of additional disk space will be used.
Get:1 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) intrepid/universe bluez-compat 4.12-0ubuntu5 [53.1kB]
Fetched 53.1kB in 2s (17.8kB/s)      
Selecting previously deselected package bluez-compat.
(Reading database ... 105779 files and directories currently installed.)
Unpacking bluez-compat (from .../bluez-compat_4.12-0ubuntu5_i386.deb) ...
Processing triggers for man-db ...
Setting up bluez-compat (4.12-0ubuntu5) ...

5. then again
eric@eric-desktop:~$ sudo hidd --search
Searching ...
	No devices in range or visible

6. and again! 
eric@eric-desktop:~$ sudo hidd --search
Searching ...
	Connecting to device 00:07:61:4D:FC:82

7. the end :)  hope it helps someone

---

### Post by ravi.xolve on 2009-01-02
it has not been solved bluetooth is woriking for a few and perhaps you are among the few lucky ones.

the problem is with the kernel I downgraded to the hardy kernel and it just worked fine. doesn't mean solved, since the problem is with intrepid and should be solved in intrepid.

---

### Post by aaronsharpe on 2009-01-05
My bluetooth was finding other devices just not connecting. I tried with a new bluetooth adaptor today and everything now works perfectly.

The new adaptor is bluetooth 2.0, the old one was bluetooth 1.2

I hope this helps someone fix the bug.

---

### Post by PowerPanda on 2009-01-06
I have the problem with the new kernel - where if I boot in older kernel then everything works fine. Is that what you had - before upgrading to adapter with bluetooth 2.0 when it started working?

---

### Post by PowerPanda on 2009-01-11
Hey thanks a lot aaronsharpe that was my problem as well. Looks like the new linux kernel or ubuntu are just not backward compatible with old bluetooth 1.2 adapters.

---

### Post by chrisinspace on 2009-01-12
> **nkri said:**
> ... downgrading to the Hardy kernel seems to be a good workaround (not a fix, though), at least temporarily.  For me, bluetooth worked with this kernel, but the wireless was messing with my router so I had to go back to the Intrepid kernel.  Other people have said this method works fine for them, so it's probably worth a shot:)
-nkri

Over the weekend, I downgraded to Mythbuntu 8.04 on my HTPC.  I'm working on reconfiguring everything.  I'll share the results when I get around to setting up my BT keyboard/trackball.  Hopefully this issue will be resolved in Jaunty.  It's running a newer kernel.

---

### Post by nco on 2009-01-12
My Bluetooth isnt working either.

I am trying to pair with my phone for Internet access.  I can do it with the USB cable but it just doesn't find any bluetooth hardware when I do a search.

Out of interest I tried it with LinuxMint, OpenSuse and Fedora Core Live CDs - the latest versions and all of them can't find any Bluetooth devices.  I think it's more likely a kernel issue with my particular hardware rather than Ubuntu.

I can pair the phone with my MAC in OsX so I know that works ok.

I'm running on a new Toshiba Laptop P300-1AY. (Anyone know what chip set it is using?)

I've tried at the command line use "hcitool scan" and nothing is found.

I did some basic fault finding and it seems to be something to do with network.so

/usr/local/lib/bluetooth/plugins/network.so

I've downgraded my BlueZ bluetooth stack to run Blueman but still no go.  I've also tried upgrading to the latest version by downloading and compiling manually but all to no avail.

I've also tried connecting with bluetooth on an eeepc using a modified ubuntu disto (eeeasy peasy) and that doesn't work either.

The bottom line is it doesn't seem to find the hardware properly.

I think it is a kernel/module config issue and not Ubuntu and I hope there is a fix soon.  

Phone reception is poor where I live and I need to site my mobile on the shelf for faster download speed but my cable is too short.  Bluetooth should work and I can't believe new "stable" releases are being advertised as such if they don't actually support normal run of the mill PC hardware.

Hopefully we have a fix soon!
Neil

---

### Post by nco on 2009-01-14
I have done a bit more research and came across the following (from Gentoo wiki page)
************
  Bluetooth

This is a tricky one. After you've enabled all the bluetooth support in the world you can get in the kernel, you find yourself screwed. The bluetooth device is disabled by default in BIOS. The toshiba or toshiba_acpi drivers will not help, because the laptop has a Phoenix BIOS.

Fortunately, the omnibook drivers are in portage and they seem to work, at least for Bluetooth. Make sure you emerge the latest omnibook version (masked by ~x86 keyword)
Code: omnibook

# echo 'app-laptop/omnibook ~x86' >> /etc/portage/package.keywords

# emerge -va app-laptop/omnibook

# modprobe omnibook ectype=14

Now you should be able to turn the Bluetooth device on and off along with the wireless radio using the RFkill switch on the front side of the laptop. IT should also appear in the lsusb listing.

**********

So it appears bluetooth is turned off by defualt (hence can't see any devices!)

The chipset is INTEL 0x4232.

The possible fix is to use the omnibook drivers.  Downloaded from sourceforge:

[http://sourceforge.net/projects/omnibook/](http://sourceforge.net/projects/omnibook/)

Trouble is I don't know how to compile and make them.  There is no configure file.  Can anyone give me some pointers so I can try?

I suspect this effects everyone using the intel chipset/phoenix BIOS

Help appreciated to get this tested out.

Thanks
Neil

---

### Post by nco on 2009-01-14
I made more progress and now have Bluetooth working on my Toshiba Satellite pro.

It seems that latest 8.10 release does not use "toshset" utility since the kernel tosh-utils module is not loaded on the latest release of Ubuntu Interpid Ibex 8.10 so there is only basic support for the laptop.

The bluetooth device is disabled by default in 8.10 and to make matters worse there is no utility to enable it.  The utilities on the desktop don't actually connect ot the module to make the switch switch state.

However a work around for all Toshiba uses that use the Phoenix BIOS is to install the module for the omnibook. (I wonder if this is the same sort of problem others are having - the kernel support to turn on and off bluetooth isn't implemented and it stays turned off by default).  If you cant see and devices when you issue

hcitool scan  

(with a bluetooth device nearby)

Its a bit tricky to do and you need to be familiar with the terminal!

Have a look at :
[http://ubuntuforums.org/showthread.php?t=316358](http://ubuntuforums.org/showthread.php?t=316358)

Also there is some useful comments at:
[http://sourceforge.net/tracker/index.php?func=detail&aid=2011260&group_id=174260&atid=868542](http://sourceforge.net/tracker/index.php?func=detail&aid=2011260&group_id=174260&atid=868542)

a switch setting called ectype=14 is need for the P300 and U400. (Read the thread for a full explanation)

Hope of some use to Toshiba users wanting Bluetooth and it might give some direction for other non tosh users to check the software switch is enabled in the kernel.

;)

---

### Post by nco on 2009-01-14
Hold fire on last post - although I have bluetooth working it has now caused my power management to do weird stuff and it keeps shutting the PC down as if the battery is flat after a few minutes of run time.

It appears to have stopped charging the battery and it runs until flat.

Might be something to do with the ectype=nn switch not set correctly for my model of laptop.  I'll get back to this in a few days.

Fix one problem and make another! doh!

:(

---

### Post by gardara on 2009-01-19
kdebluetooth4-0.3 has been released! 
Take a look at [https://bugs.kde.org/show_bug.cgi?id=172267#c20](https://bugs.kde.org/show_bug.cgi?id=172267#c20)

---

### Post by laeg_ on 2009-01-23
bump.

---

### Post by jeffmart on 2009-01-30
Ok. Still not working in Intrepid. But I think that is a Bluez4 bug, not Ubuntu, kdebluetooth or other bug...

I recently changed my principal notebook. In the old one, I runned under OpenSUSE 11, and my dongle BT left to work for receiving files after last updates.

After change my hardware, in a clean Ubuntu 8.10 (with KDE4, not Gnome) install, it still has the receiving problem...

I suspected that the problem was dongle, then got a new one. But keep the problem. After update bt packages with blueman and bluetooth (ppa.launchpad.net) specific repositories, I got pairing and sending files working, but none for receiving nor headset bt!

I compiled my own bt stack from bluez sources, and same: just send or pairing working. Nothing more...

Has anybody a workaround about?

---

### Post by Ferrat on 2009-01-30
Having the same problem, my dongle is listed when doing lsusb but wont be recognized as a bluetooth device, the older drivers show my bluetooth as bluetooth but doesn't work otherwise :/ 

is there a new module or something that is needed??

---

### Post by icyest on 2009-02-03
Ah hardware... this is probably Linux's greatest fail. I'd  like to add on to the fact that I'm also having bluetooth issues with sending files. Everything seems like it should work, but it just doesn't function. 

Funny, it works with Windows XP PERFECTLY! Can you believe that? Can Linuxvangalists acknowledge this (and many many more problems)?

---

### Post by isecore on 2009-02-05
> **icyest said:**
> Ah hardware... this is probably Linux's greatest fail. I'd  like to add on to the fact that I'm also having bluetooth issues with sending files. Everything seems like it should work, but it just doesn't function. 

Funny, it works with Windows XP PERFECTLY! Can you believe that? Can Linuxvangalists acknowledge this (and many many more problems)?

This is actually one of the few times something "just doesn't work" under Ubuntu/Linux. The only other thing I have to tickle to get working properly is my graphics adapter, and with Intrepid that meant activating the proprietary driver.

[rant]I never had much hardware issues previously to Intrepid, but bluetooth for whatever reasons (kernel? bluez? evil gnomes?) is borked. My experience with Windows is almost always the opposite - that eeeeeverything needs to be tickled to work. Hell, I can't even install it without having a floppy full of drivers (for XP) or loaded onto a USB-drive (for Vista) since it won't recognize my AHCI SATA-drives otherwise.[/rant]

---

### Post by peddy on 2009-02-05
This is the first time I've been unable to fix something that an update broke... 

Bluetooth worked out-of-the-box in Hardy, and I can confirm that it still doesn't work in Jaunty alpha 3.

---

### Post by ravi.xolve on 2009-02-07
Unless this is fixed in kernel upstream the problem will remain.

Is there any way to downgrade bluez from version 4 to 3?

---

### Post by Dropbear on 2009-02-07
I have it working fully on a live cd of Jaunty alpha 4. It was not working for me on intrepid.

Just hope it doesn't get broken again.

---

### Post by newore on 2009-02-09
> **Dropbear said:**
> I have it working fully on a live cd of Jaunty alpha 4. It was not working for me on intrepid.

Just hope it doesn't get broken again.

any comments on your actions to get it working. I'm looking at 
alpha 4 on a lenovo s10 and still having problems.

as in this bug report:
[https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/285007](https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/285007)



have similar issues in intrepid, still.

any advice appreciated

---

### Post by HyRax on 2009-02-09
Out of interest, does Bluetooth work if you boot up on an 8.10 LiveCD or LiveUSB media?

If it doesn't, then I daresay something has changed (or is missing) in the driver for select Bluetooth adapters, because [my adapter](http://www.jaycar.com.au/productView.asp?ID=XC4892&keywords=bluetooth&form=KEYWORD) is working perfectly (except for having to do the manual PSCAN change to the adapter to get BT mice and keyboards working properly).

---

### Post by Dropbear on 2009-02-09
> **newore said:**
> any comments on your actions to get it working. I'm looking at 
alpha 4 on a lenovo s10 and still having problems.

as in this bug report:
[https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/285007](https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/285007)



have similar issues in intrepid, still.

any advice appreciated

All I did was plug in my KY-BT100 Bluetooth Adapter then pair with my phone from the computer it wouldn't work vice versa. I can send files from the computer to the phone (couldn't from Intrepid). It wouldn't send from the phone to the computer but all I had to do was browse the phone and copy and paste the files onto the phone. 

It would fail to connect sometimes but all I had to do was unplug and replug the adapter then it was ok.

---

### Post by RgnKjnVA on 2009-02-09
I'm running 8.10 32-bit with a Rocketfish BT micro dongle and have most everything working. I can even pair it with my phone and browse however I can't for the life of me get it to even see my Motorola S9-HD headset. If I use the script mentioned [earlier]("http://www.technetra.com/2008/11/22/pairing-stubborn-bluetooth-devices-in-fedora-10-ubuntu-ibex/"), it at least sees the headset but won't pair. The Bluetooth version, I believe, is 2.13 (see below) so I'm not so sure the version of BT is the issue. I'm going to try the Blueman trick and if that doesn't work, back to Hardy I go. 

Tragically, I decided to embark on my first foray into the world of Bluetooth with this laptop I just got and installed Intrepid on. *sigh* Seems there's always some frustrating hurdle with each version of Ubuntu. Regression in functionality is a very bad thing.

```
Linux laptop 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux

```

```
laptop:~$ dmesg | grep Bluetooth
[   19.208005] Bluetooth: Core ver 2.13
[   19.208005] Bluetooth: HCI device and connection manager initialized
[   19.208005] Bluetooth: HCI socket layer initialized
[   19.296005] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   30.208007] Bluetooth: L2CAP ver 2.11
[   30.208007] Bluetooth: L2CAP socket layer initialized
[   30.276009] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   30.276009] Bluetooth: BNEP filters: protocol multicast
[   30.296012] Bluetooth: RFCOMM socket layer initialized
[   30.296012] Bluetooth: RFCOMM TTY layer initialized
[   30.296012] Bluetooth: RFCOMM ver 1.10
[   30.518421] Bluetooth: SCO (Voice Link) ver 0.6
[   30.518448] Bluetooth: SCO socket layer initialized

```

```
laptop:~$ hcitool dev
Devices:
	hci0	00:19:15:6D:B8:3E

```

---

### Post by newore on 2009-02-09
> **HyRax said:**
> Out of interest, does Bluetooth work if you boot up on an 8.10 LiveCD or LiveUSB media?

If it doesn't, then I daresay something has changed (or is missing) in the driver for select Bluetooth adapters, because [my adapter](http://www.jaycar.com.au/productView.asp?ID=XC4892&keywords=bluetooth&form=KEYWORD) is working perfectly (except for having to do the manual PSCAN change to the adapter to get BT mice and keyboards working properly).

tried a live dvd (see [https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/285007](https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/285007)) for some tracks and experiments.

the bluez 4.29 just upgraded on the 9.04 jaunty system is acting
better for me.

it did work on 8.10 from dvd, with ptrace, just not nearly as
well as the new stuff.

bob

---

### Post by joe_geek on 2009-02-15
> **RgnKjnVA said:**
> I'm running 8.10 32-bit with a Rocketfish BT micro dongle and have most everything working. I can even pair it with my phone and browse however I can't for the life of me get it to even see my Motorola S9-HD headset. If I use the script mentioned [earlier]("http://www.technetra.com/2008/11/22/pairing-stubborn-bluetooth-devices-in-fedora-10-ubuntu-ibex/"), it at least sees the headset but won't pair. The Bluetooth version, I believe, is 2.13 (see below) so I'm not so sure the version of BT is the issue. I'm going to try the Blueman trick and if that doesn't work, back to Hardy I go. 

Tragically, I decided to embark on my first foray into the world of Bluetooth with this laptop I just got and installed Intrepid on. *sigh* Seems there's always some frustrating hurdle with each version of Ubuntu. Regression in functionality is a very bad thing.

```
Linux laptop 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux

```

```
laptop:~$ dmesg | grep Bluetooth
[   19.208005] Bluetooth: Core ver 2.13
[   19.208005] Bluetooth: HCI device and connection manager initialized
[   19.208005] Bluetooth: HCI socket layer initialized
[   19.296005] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   30.208007] Bluetooth: L2CAP ver 2.11
[   30.208007] Bluetooth: L2CAP socket layer initialized
[   30.276009] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   30.276009] Bluetooth: BNEP filters: protocol multicast
[   30.296012] Bluetooth: RFCOMM socket layer initialized
[   30.296012] Bluetooth: RFCOMM TTY layer initialized
[   30.296012] Bluetooth: RFCOMM ver 1.10
[   30.518421] Bluetooth: SCO (Voice Link) ver 0.6
[   30.518448] Bluetooth: SCO socket layer initialized

```

```
laptop:~$ hcitool dev
Devices:
	hci0	00:19:15:6D:B8:3E

```

What Rocketfish bluetooth dongle did you buy? Mine says EDR Class 2 on it. I can't for the life of me even get it to register properly in hcitool. Nothing shows up in the devices column, even though I have bluez installed.

lsusb returns 3 Broadcom devices, the -v flag says one is a mouse, one is a keyboard and one is a hub. For note, I do not have any bluetooth keyboard/mouse, this was bought to sync with my phone.

---

### Post by RgnKjnVA on 2009-02-16
Per Blueman,

Version: Bluetooth 2.1 + EDR
Revision: 149.66 / 14

For the record, I didn't experience any problem with the dongle. It was recognized out of the box.

---

### Post by Hemanti on 2009-02-16
Bluetooth didn't work for me either since I upgraded to intrepid, but now it does (well just as good as in hardy which isn't perfect, but it does work). So I hope I can help you by telling you what I did.

I started bluetooth-applet via the terminal, then paired my phone, sent a file with the panel and now it even works from Nautilus which it did not before. Blueman still doesn't recognize my dongle but I don't care anymore.

So you might wanna give it a try.

---

### Post by isecore on 2009-02-18
Well, it works for me now.

What did I do? I went out and bought a new bluetooth-adapter, is what I did. I bought one that looks exactly the same as my previous dongle - except it's Bluetooth 2.0. Yanked the old one, plugged the new one in and immediately everything started working. I can now pair my phone, send/receive files (using gnome-obex-server) as well as everything I previously did.

However I still find that this is not an acceptable solution really, since there's plenty of BT 1.1 devices built into older computers that still should work.

But it solved it for me.

---

### Post by stink on 2009-02-18
This thread is very long, so I haven't read the whole thing, but I wanted to add this bit of info:

If you have a dongle with this lsusb output

1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter

and it works under hardy but not under intrepid, see this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268502](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268502)

The problem in the kernel bluetooth stack is known and a fix seems to be nearing.  Some moderately advanced workarounds are in the bug comments.

I found this forum thread and the above linked bug report doing a google search, so I imagine others may do the same.

---

### Post by ukblacknight on 2009-02-20
I noticed a load of Bluetooth updates this morning, doesn't seem to of done anything though :(

Why is this taking so long to fix?  Is it just Bluetooth 1.0 devices that have this regression problem?

My girlfriend is getting me a BT 2.0 dongle of my birthday soon though so hopefully that will end this stupid issue!

---

### Post by isecore on 2009-02-20
> **ukblacknight said:**
> Why is this taking so long to fix?  Is it just Bluetooth 1.0 devices that have this regression problem?

That would indeed seem to be exactly what's going on. My first dongle (which was why I started this thread) was 1.1 and didn't work. My new one is 2.0 yet is the exact same manufacturer. It seems to be based on a completely different chip though, since it identifies differently.

```
Bus 002 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
```

But everyone who's had flawless success with BT in Intrepid in this thread (me included) seems to have a 2.0-device. That's the common theme of success here.

---

### Post by nkri on 2009-02-20
> **isecore said:**
> That would indeed seem to be exactly what's going on. My first dongle (which was why I started this thread) was 1.1 and didn't work. My new one is 2.0 yet is the exact same manufacturer. It seems to be based on a completely different chip though, since it identifies differently.

```
Bus 002 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
```

But everyone who's had flawless success with BT in Intrepid in this thread (me included) seems to have a 2.0-device. That's the common theme of success here.

+1

This is what makes me think it has something to do with the module being improperly loaded by the kernel, but I'm not a developer and don't know for sure...

---

### Post by ukblacknight on 2009-02-21
I got *more* bluetooth updates this morning!  Seems to of made a slight difference:

1) The applet doesn't disappear any more when configuring it, the icon is always there.

... and that's it.  When entering details into the applet such as the ID of the computer, it doesn't save it.  hcitool scan still times out and my phone still cannot see my PC!

So, it seems we are making some very slow progress!  I tried 9.04 alpha 4 in a VM and that just has the same results.

---

### Post by kaligus on 2009-02-21
I have NOT yet read the whole thread, but will get there eventually.

Upgraded 8.04 to 8.10 recently, and due to some insanity ended up mkfs /dev/sda1 with only my /home /junk and /storage being kept.  / was fresh install of 8.10.

I have not used bluetooth at all since moving to ubuntu  and even in windows I threw it out because it refused to work correctly more often than not.

So today I decided to get a dongle on a lark and see what is so cool about bluetooth and my phone<->computer.

for the record
```
Bus 001 Device 008: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
```

1st time I paired the devices all went well, I copied several files, browsed the phone etc.

The 2nd time I tried I found the bluetooth system crashed
```
Feb 20 20:32:08 bigwill kernel: [ 2628.961167] bluetoothd[6241]: segfault at 8 ip 00007f1557266ce8 sp 00007fff60b9ad30 error 4 in audio.so[7f155724e000+23000]
Feb 20 20:45:11 bigwill kernel: [ 3412.298669] bluetoothd[9680]: segfault at 8 ip 00007f4dc5abfce8 sp 00007fffcf3f43d0 error 4 in audio.so[7f4dc5aa7000+23000]

```

I did a little noodling around and found several people telling me to try blueman instead which I did.

I have managed to keep the icon on the screen, and the audio turned off completely so no more crashes there but...

Same deal, 1st time worked, all subsequent attempts at anything except pairing fail.

If I delete the devices from each others list and re-search either direction I can get a pairing to work phone->computer 95% and computer->phone 80% but everything after that fails, not even a / listing.

** Now even if I switch bluez <-> blueman all I can do is pair the devices, no more first time works subsequent fail.

If I were to uninstall the whole bluetooth mess and start fresh could I make it work?  What do I need to uninstall and remove by hand?

What more information would be helpful?

Now that I have seen what I can do I would really like to be able to connect to my phone and exchange addresses, pictures, music, etc. via bluetooth because getting the micro-sd in and out is painful and cables make the kids (3 young cats) nuts and things/people get hurt

****EDIT: yes, the failure of all started after 3 or 4 updates related to bluetooth just before I started this messsage.

---

### Post by eee1000huser on 2009-02-23
where's the missing hcid.conf in Intrepid? How can I get it back?

---

### Post by HyRax on 2009-02-23
> **eee1000huser said:**
> where's the missing hcid.conf in Intrepid? How can I get it back?

You don't get it back. Bluetooth changed considerably between Hardy and Intrepid.

---

### Post by eee1000huser on 2009-02-24
Thanks for your reply HyRax,

Could you please point me towards a HOWTO for setting up a PAN between two Intrepid machines using the new Bluetooth mechanisms?


Thanks a lot.

-e

---

### Post by HyRax on 2009-02-24
A quick Google gives me this: [http://www.viciouslime.co.uk/articles/3-howtos/19-howto-bluetooth-networking-pan-on-ubuntu](http://www.viciouslime.co.uk/articles/3-howtos/19-howto-bluetooth-networking-pan-on-ubuntu)

Not that it's really worth it - Bluetooth is too slow for general networking - you'd be better off buying a $5 cross-over ethernet cable to hook up PC's within 10 metres of each other!

---

### Post by sarel29 on 2009-02-28
Hi, can I ask if anyone ever figured out what the problem was?  I've just tried to get my bluetooth connection to recognise another computer, but Intrepid is not acknowledging my own bluetooth, let alone anything else.
Thanks.

---

### Post by fragos on 2009-02-28
I been using a TRENDnet BT dongle, ID 1310:0001 Roper Class 1 Bluetooth Dongle, for a number of releases. There have been some changes in bluetooth with 8.10 and things do percievably work differently but they do for me work. I use bluetooth a lot between my desktop and a Nokia N810 transfering files. I have found that not all bluetooth devices are created equally. I could send files to my Palm E2 but it could never send to the desktop. Not all devices support the same list of bluetooth protocols. Some devices are very finicy about pairing. I have a Nokia SU-8W bluetooth keyboard that took 6 tries to get it to pair with the N810. Note: most bluetooth devices can pair with many devices but can only work with one device at a time. Most headsets can't work with both your phone and your PC at the same time. To get OBEX file transfer to work you used to install the gnome-obex-server. In 8.10 it will be found in Add/Remove as "Blutooth File Sharing". The Nautilus send to bluetooth doesn't work but right ckicking the bluetooth icon will give you a bluetooth send that does work.

---

### Post by wet-willy on 2009-03-01
I had my Dell BT Travel Mouse working upon every reboot for a while, not sure what I did to get it happening. But then I wiped out the partition and reloaded an image of the original installation...where the mouse would not work after reboots...duh!.
So...after lots of editing and trading files with Debian, I finally come up with something that just about works perfectly for me.

I installed bluez-compat, and rigged my /etc/rc.local file as described below, only thing is I have to make the mouse discoverable during boot-up, I'll keep plugging away to get that step eliminated eventually.
```
#!/bin/bash 
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
#hciconfig hci0 pscan
sleep 5
sudo hidd --connect 00:07:61:b8:35:c7

exit 0
```

I also edited my /etc/default/bluetooth file as below, but don't think that part is doing anything, never got nothing till setting up rc.local.
```
# Defaults for bluez

# start bluetooth on boot?
# compatibility note: If this variable is not found bluetooth will
# start
BLUETOOTH_ENABLED=1
HIDD_ENABLED=1
HIDD_OPTIONS="-i 00:07:61:B8:35:C7 --server"

# This setting will switch HID devices (e.g mouse/keyboad) to HCI mode, that is
# you will have bluetooth functionality from your dongle instead of only HID.
# Note that not every bluetooth dongle is capable of switching back to HID
# mode, see http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497
HID2HCI_ENABLED=1
#HID2HCI_UNDO=1
```

---

### Post by wet-willy on 2009-03-03
Well, I played around with images of the OS and got it working without installing the soon to be quashed hidd (bluez-compat) package. Found the answer in a bug report. After successfully getting the mouse set up through bluetooth applet in task bar, I added "hciconfig hci0 pscan" in /etc/init.d/bluetooth file and a couple in /etc/rc.local as shown below. And enabled HID2HCI in /etc/default/bluetooth.
```
case "$1" in
  start)
	log_daemon_msg "Starting $DESC"

	if test "$BLUETOOTH_ENABLED" = "0"; then
		log_progress_msg "disabled. see /etc/default/bluetooth"
		log_end_msg 0
		exit 0
	fi

	start-stop-daemon --start --quiet --exec $DAEMON || true
	log_progress_msg "bluetoothd"

	run_sdptool || true

	start_uarts || true

	if test "$HID2HCI_ENABLED" = "1"; then
		enable_hci_input || true
	fi
	start_rfcomm || true
	log_end_msg 0
        [COLOR="Red"]hciconfig hci0 pscan[/COLOR]
    ;;
  stop)
	log_daemon_msg "Stopping $DESC"
	if test "$BLUETOOTH_ENABLED" = "0"; then
		log_progress_msg "disabled."
		log_end_msg 0
```


```
#!/bin/bash 
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
[COLOR="Red"]sudo hciconfig hci0 restart
sudo hciconfig hci0 pscan[/COLOR]
macchanger -r eth1

exit 0
```

---

### Post by balak on 2009-03-04
> **wet-willy said:**
> Well, I played around with images of the OS and got it working without installing the soon to be quashed hidd (bluez-compat) package. Found the answer in a bug report. After successfully getting the mouse set up through bluetooth applet in task bar, I added "hciconfig hci0 pscan" in /etc/init.d/bluetooth file and a couple in /etc/rc.local as shown below. And enabled HID2HCI in /etc/default/bluetooth.


Can you point me to the bug report ? I would like to see if there is a long term solution.

---

### Post by wet-willy on 2009-03-09
Sorry, just realized I did not have email notification for new replies enabled.
[This is one of the reports]("https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/249448") I read, I spent many a spare time reading up on this, none had the ultimate answer. There are many suggestions that work for different folks in that link.
I found that again...the mouse does not reconnect after reboot if I am not moving it around. I've been using Debian with KDE desktop for many years now, and when Debian would do that to me I would power cycle the mouse and it would connect. Finally, I tried the same in Ubuntu and it is exactly like Debian, it connects.
It's sort of funny how if you're not moving it around during the last stages of boot-up it will not connect, but wiggle it before the nvidia splash and desktop appears it will, cycling the power switch does the trick in both OSs if I forget to wiggle.

---

### Post by wet-willy on 2009-03-09
As I feared, this was a double post.
OH!
I set up WPA wireless encryption at buddy's place, when I'm there with my laptop, I usually don't get a successful bluetooth mouse connection even with the wiggling thing. Seems there's an issue with the request for access to gnome-keyring before the wireless connection is established which prevents the bluetooth connection with the mouse. But the power cycling thing after wireless connection is established works.

---

### Post by Scubdup on 2009-03-26
> **HyRax said:**
> A quick Google gives me this: [http://www.viciouslime.co.uk/articles/3-howtos/19-howto-bluetooth-networking-pan-on-ubuntu](http://www.viciouslime.co.uk/articles/3-howtos/19-howto-bluetooth-networking-pan-on-ubuntu)

Not that it's really worth it - Bluetooth is too slow for general networking - you'd be better off buying a $5 cross-over ethernet cable to hook up PC's within 10 metres of each other!

Hyrax, you're clearly the leading global Ubuntu Bluetooth authority! Just found a thread of yours [here]("http://forums.overclockers.com.au/showthread.php?t=694010") which totally sorted out my bluetooth on Ubuntu. It doesn't work on restart but I'm pretty sure that's a matter of going through your instructions and finding out what's "one session" only and either making it load on start up or better, making it a process that runs prior to luanching Spotify in Wine (the only time I really use the bluetooth audio). Many many thanks for such a decent Howto.

By the way - my bluetooth device - a gizmo that allows you to play music from your bluetooth-enabled PC through any music device with a headphone lead-in - never worked on Windows XP. One-nil to Ubuntu and Linux.

---

### Post by HyRax on 2009-03-26
Oh boy, that's a really old post I did on OCAU back in July last year...! Glad it helped! Note that there's a lot of Hardy Bluetooth instruction (in general) that no longer applies to Intrepid, though those instructions for getting a headset to work are still OK to use (for the moment - they may not work for Jaunty).

---

### Post by azdavef on 2009-03-29
I have a Toshiba Satellite A205 with Toshiba BIOS, a Cambridge dongle and Logitech v470 mouse.  When I installed the dongle, everything worked fine and it paired with the mouse.  When I reboot, the dongle is not detected, but if I sudo /etc/init.d/bluetooth restart my dongle comes to life and I can reconnect to my mouse with the manager.  Can anyone point me to one of the many solutions I have seen that might fix this?   Thanks

---

### Post by savantelite on 2009-03-30
bluetooth is very easy in Jaunty:)

You can connect through the graphical bluetooth icon

---

### Post by Ferrat on 2009-04-02
Still having problems connecting my phone, also seems that bluetooth-properties doesn't save any settings or even change them??

---

### Post by RgnKjnVA on 2009-04-16
Happen to see this on the bluez site, may be of interest to the unresponsive client sufferers?

[http://www.bluez.org/](http://www.bluez.org/)

Release of bluez-4.35
11th April 2009, 07:00 pm by Marcel Holtmann

This release fixes various bugs, crashes and other problems found during testing. It should make the Bluetooth audio support (Headset and A2DP) more stable now.

bluez-4.35.tar.gz

---

### Post by billybag on 2009-04-17
I, for the life of me, CANNOT get the bluetooth icon to appear in my toolbar. that is my main problem
FIXED
```

info here:https://bugs.launchpad.net/ubuntu/+bug/289836

add "deb http://ppa.launchpad.net/blueman/ubuntu intrepid main" to sources list

get key: "sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6B15AB91951DC1E2"

sudo apt-get update
sudo apt-get install blueman

What this DOES is uninstalles bluez4 and installs bluez3. Bluez4 is buggy and you need bluez3.

after all that go into your menu and click on BLUETOOTH MANAGER

hope this helps


```

---

### Post by RgnKjnVA on 2009-05-20
[SOLVED] FYI I'm happy to report I can finally get audio from my bluetooth headset in Intrepid from my browser! w00t These two threads did the trick...

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
[http://blueman-project.org/forum/viewtopic.php?f=5&t=111](http://blueman-project.org/forum/viewtopic.php?f=5&t=111)

I just need to figure out why my media players won't play anything now.

---

### Post by raghuram_c on 2009-09-27
hi community,
i recently upgraded to bluez 4.42 and bluez-gnome 1.27-1. my device seems configured but i fail to pair my phone 
 
raghu@DL:~$ sudo hciconfig -a
hci0:	Type: USB
	BD Address: 00:1D:D9:EF:BC:B2 ACL MTU: 1017:8 SCO MTU: 64:8
	UP RUNNING PSCAN ISCAN 
	RX bytes:882 acl:0 sco:0 events:49 errors:0
	TX bytes:461 acl:0 sco:0 commands:49 errors:0
	Features: 0xff 0xff 0x8f 0xfe 0x9b 0xf9 0x00 0x80
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
	Name: 'DL-0'
	Class: 0x5a210c
	Service Classes: Networking, Capturing, Object Transfer, Telephony
	Device Class: Computer, Laptop
	HCI Ver: 2.0 (0x3) HCI Rev: 0x213b LMP Ver: 2.0 (0x3) LMP Subver: 0x41d3
	Manufacturer: Broadcom Corporation (15)

raghu@DL:~$ hcitool scan
Scanning ...
	00:1D:25:2C:DF:52	Kalyan
	00:16:41:B9:D7:2A	WEBLAYS02
	00:1C:BD:7F:6C:AE	Fly SX210

raghu@DL:~$ hcitool dev 
Devices:
	hci0	00:1D:D9:EF:BC:B2

however when i try to connect to my "fly sx210" mobile phone the pin is asked in the phone, when i enter the pin i get this

raghu@DL:~$ hidd --connect 00:1C:BD:7F:6C:AE
Can't get device information: Invalid exchange

raghu@DL:~$ sudo hcitool cc 00:1C:BD:7F:6C:AE
Can't create connection: Input/output error

then i check bluetoothd i get unable to get on DBus

raghu@DL:~$ sudo bluetoothd -nd
bluetoothd[8382]: Bluetooth daemon 4.42
bluetoothd[8382]: Enabling debug information
bluetoothd[8382]: parsing main.conf
bluetoothd[8382]: discovto=0
bluetoothd[8382]: pairto=0
bluetoothd[8382]: pageto=8192
bluetoothd[8382]: name=%h-%d
bluetoothd[8382]: class=0x5a210c
bluetoothd[8382]: discov_interval=0
bluetoothd[8382]: Key file does not have key 'DeviceID'
bluetoothd[8382]: Unable to get on D-Bus

then i did modprobe btusb reset =1 still i get the same result

my /etc/Dbus-1/system.conf  is like this 

<policy context="default">
    <!-- All users can connect to system bus -->
    <allow user="*"/>

    <!-- Holes must be punched in service configuration files for
         name ownership and sending method calls -->
    <deny own="*"/>
    <deny send_type="method_call"/>

    <!-- Signals and reply messages (method returns, errors) are allowed
         by default -->
    <allow send_type="signal"/>
    <!-- commented out part
    <allow send_requested_reply="true" send_type="method_return"/>
    <allow send_requested_reply="true" send_type="error"/>
    -->
    <!-- Newly added line to fix permission problems -->
    <allow send_requested_reply="true" />
    <!-- All messages may be received by default -->
    <allow receive_type="method_call"/>
    <allow receive_type="method_return"/>
    <allow receive_type="error"/>
    <allow receive_type="signal"/>

    <!-- Allow anyone to talk to the message bus -->
    <allow send_destination="org.freedesktop.DBus"/>
    <!-- But disallow some specific bus services -->
    <deny send_destination="org.freedesktop.DBus"
          send_interface="org.freedesktop.DBus"
          send_member="UpdateActivationEnvironment"/>
  </policy>

my hcid.conf is as follows

options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security auto;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# Default PIN code for incoming connections
        passkey "1234";
	
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x5a210c;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;
}

no matter what i try my bluetoothd cant get on DBus and also my bluetooth applet does not appear as it says 

raghu@DL:~$ bluetooth-applet 
Bluetooth OBEX server failed: Could not create server socket
Bluetooth FTP server failed: Could not create server socket

please suggest a solution as everthing used to work perfectly before the upgrade, it has been a very frustrating week.

my email is [email]raghuramconu@gmail.com[/email]

thanks in advance

Raghuram

---

### Post by fragos on 2009-09-27
Your bluez is newer than that with Ubuntu 9.04. There was a time when CLI and configuration files were required to set up Bluetooth. With 9.04 my TRENDnet Bluetooth dongle was automatically detected and pairing is easily done by right clicking the Bluetooth icon in the applet bar and selecting "Setop new device..." I believe that 9.10 has some changes/improvements in Bluetooth setup which are yet to be released.

---

### Post by raghuram_c on 2009-09-29
Thanks fragos,
 I solved it by downgrading to blue-utils 3.xx. everything works now.

---

