---
title: "external hdd disconnecting itself"
date: 2013-12-31
forum: Hardware
---

### Post by m-sheehan23457 on 2013-12-31
hi,

im using a clean install of lubuntu 13.10 32bit. my external hard drive no longer shows up in pcmanfm unless i disconnect and reconnect the power source. after i do this it usually remains connected for a minute or two and then completely disappears. if i reboot in this state with the device plugged in the system restarts very slowly.

as far as i know the external hdd has been working perfectly up to now. any ideas what could be happening?

---

### Post by varunendra on 2014-01-04
Welcome to the forums m-sheehan !

The behaviour you described above is usually a symptom of a weak connecting cable (too long or too thin conducting part), low voltage at USB ports or some physical problem in the drive causing it to require abnormal amounts of power which the USB port can't keep up with.

In cheap circuits, it can also be due to an overheating chip in the drive.

If possible, try using a shorter and/or better quality data cable.

If you hear 'clicking' noises inside the drive, it can be bad for its health, if not already succumbed to physical damage. The best way to check if the actual drive (inside the USB enclosure) is healthy is to bring it out of the enclosure and connect it directly to the SATA port (or PATA port, whichever it has) of the motherboard using standard SATA power and data cables. If it works fine there, the problem is definitely in the USB cable or the adapter circuit in the enclosure.

By the way, which brand/model is this External drive? What capacity? Some of our friends here may have personal experience with it to share with us. :)

---

### Post by m-sheehan23457 on 2014-01-06
hi varunedra,

thanks for responding.

its a seagate freeagent 500gb. it doesn't make audible clicking noises. i tried a shorter usb cable and performance seemed better but ultimately it suffered the same fate.

next step is to acquire a SATA cable and try that. i will report back here with the results, although im busy this month so it may take some time.

if anyone has any other potential solutions i'm all ears.

thanks.

---

### Post by varunendra on 2014-01-07
Can you try an externally powered USB hub?

It seems the kernel in _Ubuntu 13.10_ *may have a bug* due to which it can't supply sufficient power to demanding USB devices. Something that one of our members "Leechpool" noticed and mentioned here : [http://ubuntuforums.org/showthread.php?t=2197638&p=12893261#post12893261](http://ubuntuforums.org/showthread.php?t=2197638&p=12893261#post12893261)

One of my two external HDDs is Seagate Freeagent GoFlex 500 GB ([this one]("http://static.techspot.com/images/products/storage/external-hds/org/1953238738_803840743_o.jpg")), and I can confirm it works fine here with my 12.04.1 (kernel 3.2.0-36-generic).

Although I should also mention that it _does disconnect sometimes_ when using the cable supplied with it. It remains more stable when I use an older cable that came with Seagate Freeagent Go 320 GB, that one is slightly shorter in size, and slightly thicker as well.

But these drives are not easy to open up. Even though its sata and power connector is detachable ([like this]("http://www.pcstats.com/articleimages/201202/segategoflex_hdd3.jpg")), normal sata cables can't reach that deep without completely opening the enclosure, which is a bit tricky, and would definitely void the warranty. So if it is under warranty, try other alternatives first to make sure it is not the power or cable issue as pointed out above.

---

