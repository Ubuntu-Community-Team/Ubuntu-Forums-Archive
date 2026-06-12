---
title: "Can an external HDD get its firmware infected by a rootkit or other corrupted code ?"
date: 2017-06-30
forum: Hardware
---

### Post by kris.kolev on 2017-06-30
Helly, I'm new to the forum and I'm really sorry if this thread doesn't belong here.

The following questions are related only to external HDDs, and not the computer's hardware configuration ones:


Does an ordinary external HDD come with some factory firmware in it, or it does NOT need one since the computer's UEFI/BIOS or other firmware runs it ?
If it does have some firmware coded in it, can an external HDD (you may answer on SSD to, would be appreciated, but mechanical HDD is my priority) get infected by a rootkit ? I'm not talking on infecting a computer to which it connects. Can the external HDD's own firmware (if it has such) get infected ?
If the above questions's answers are both "yes", then is the process of completely wiping out all of the external disk (considering all the data on it can be sacrifised) going to solve the problem of the infection ? Even if all of the memory is overwritten by zeroes ?
If even complete wipe-out and zeroes overwritting will not "heal" the firmware, what has to be done to get a completely clean (like a new one just bought) external HDD, free of all kinds of infections ? Will a reflashing of the firmware solve the problem ? If so, how could you reflash an external HDD's firmware in home ?


I note again that I'm talking about a case in which not the data on it is so important, but the physical device.


Thank you in advance!

---

### Post by TheFu on 2017-06-30
Yes and yes.  Physical HDDs do have firmware.  That firmware **has** been hacked previously by TLA.

There isn't any method that an admin or end user can use to clear the hacked firmware because the first thing to be removed would be a method to allow replacement of the new, do-what-that-organization-wants firmware.
[https://www.malwaretech.com/2015/04/hard-disk-firmware-hacking-part-1.html](https://www.malwaretech.com/2015/04/hard-disk-firmware-hacking-part-1.html)

[https://www.wired.com/2015/02/nsa-firmware-hacking/](https://www.wired.com/2015/02/nsa-firmware-hacking/)

Rootkit?  Well, anything on the disk could be targeted by the modified firmware, so a specific program could be modified to do anything, including installing anything it can get access to silently.

BTW, this applies to many flash devices too. I've heard of it for certain types of flash USB devices.  Not all USB devices have the ability to have their firmware modified.  However, if you ever find one in a parking lot, don't ever plug it into any computer you care about. This is a commonly used attack vector to get a foothold inside a company.  Cross-platform payloads exist, so running Linux/OSX doesn't help.  If you do decide to plug in an unknown device, please do it on a throw-away computer without any networking (including bluetooth) configured at all.

I have not heard about SSDs being hacked in this way, but expect it is very common now for specific targets.  And that wouldn't be just SATA/SAS SSD devices, but the faster SSDs with more direct interfaces too.

If you are really paranoid about this stuff and some organization wants to hack you, then the only way I know to have any hope of getting clean devices is to walk into a store, probably not a convenient location to your home or work, and pull a fresh device off the shelf yourself and buy it.

Don't use mail order.  Organizations have been known to intercept orders in the mail and modify those devices.
[https://arstechnica.com/tech-policy/2014/05/photos-of-an-nsa-upgrade-factory-show-cisco-router-getting-implant/](https://arstechnica.com/tech-policy/2014/05/photos-of-an-nsa-upgrade-factory-show-cisco-router-getting-implant/)

I'm pretty paranoid, but not about these things.  There is no proof modified HDDs have been widely deployed or deployed by anything other than "state actors."  However, I have purchased a cheap chromebook using the pull-from-shelf-and-buy method, more just to see that it could be done and what would be needed to get that machine working in the way I'd prefer.  If you can get the exact same model you have already, swapping the storage is pretty easy. Great for travel outside your country.

My general thoughts on these sorts of capabilities is that if I can think it up and come up with a method for it to work, then someone has done it already or is working on it somewhere inside some govt organization, somewhere in the world.

BTW, never do anything you want secure on any smartphone or tablet if you've ever installed any 3rd party app.

---

### Post by kris.kolev on 2017-07-01
Thank you very much for the detailed explanation and your advices!

I'm not fanatically paranoid, but I want to have some advanced security.
I always buy my devices and technology pull-from-the-shell exactly because of my worries of even legally modified devices, as you suggested.

I'm studying mechanical engineering and basically I use computer devices with both windows (never liked that fact, but you have to do what you have to) and linux, as tools to do my job. So software/firmware isn't my primary job, but I'm trying to constantly educate myself and get skilled about computer tech and security, so I can do my primary job seamlessly.

I don't have any important data at the moment, I do not use paypal, ebay and other online payment platforms.
But I'm a second-of-four year student on a full-time education, plus it's a very tough education program and so I cannot get a job until I finish my bachelor degree and let's say,
because of all that, physical devices are more important to me than the data stored in them.

I'm planning to buy an external mechanical drive (I never had a problem with physically malfunctioning mechanical drives, so I prefer them, even with all their cons, that's just personal opinion).
And want to know more about security, since I've been reading about rootkits and people say firmware ones are the most dangerous and hard to deal with.

I would be very thankful to know,

If I buy a new, straight from the shell, unmodified external HDD, as is from the factory, and later when using it get it infected by a rootkit while normally transferring some data...
Is throwing the device to the trash and buying a new one (again) the only method of dealing with the rootkit which infected its firmware ?

And lastly, if I really have to throw it away but it's an expensive for me device...
If I spend some more money and buy a programmer which can electrically flash the EEPROM chip containing its firmware, and flash it on physical 0's-and-1's-level (0-and-5-volts), so I can physically erase the rootkit, then install the factory firmware in some way ? Is this even possible even if I have to get more skilled ?

Or can I just order a new same firmware chip from the manufacturer, remove the old one and solder the new one (if possible for the specific device) ?

I really don't want to spend some big money on a 2TB device (yes, I live in Bulgaria and here salaries are not very high, but devices are very expensive), then get it infected and have to throw it away.

Sorry if I look stupid, but I want to learn.
Really thankful for your support!

---

