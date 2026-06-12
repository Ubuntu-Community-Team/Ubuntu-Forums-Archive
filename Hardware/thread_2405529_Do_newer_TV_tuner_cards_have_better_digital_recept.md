---
title: "Do newer TV tuner cards have better digital reception??"
date: 2018-11-07
forum: Hardware
---

### Post by linuxhippy on 2018-11-07
I've been using Mythbuntu on old computers for about 15 years.  During all that time I've been using 2 Pinnacle PCI analog/digital tuner cards:

[https://linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_(800i)]("https://linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_(800i)")

I use them now for antenna TV and don't get all the TV channels available in my area.  I've tried to get better reception in different areas of my house with no change, so I'm wondering if these old tuner cards I'm using can see 2018 channels?

If I need a new tuner card, what is recommended in Linux?  I've looked at the ones on linuxtv.org but don't see anything new for 4+ kernel.  This is what I've been looking at there for ATSC channels for USA:

[https://www.linuxtv.org/wiki/index.php/ATSC_devices]("https://www.linuxtv.org/wiki/index.php/ATSC_devices")

---

### Post by deadflowr on 2018-11-07
*Thread moved to **Hardware***

You'll probably get better reception with a newer card that has low noise amplifier functions built in.

---

### Post by linuxhippy on 2018-11-07
Thanks for the quick response!  I was thinking tuner cards now are probably better than ones in 2003 but I wanted confirmation before I start buying a newer one that works with Linux.  Over the years I also bought a nice HD antenna shown here:

[https://www.xsdepot.com/Product/346862-Antennas-Direct-Clearstream-2-Long-Range-IndoorOutdoor-HDTV-Antenna]("https://www.xsdepot.com/Product/346862-Antennas-Direct-Clearstream-2-Long-Range-IndoorOutdoor-HDTV-Antenna")

And a plug in signal booster shown here:

[https://www.amazon.com/gp/product/B003DRMKXW/ref=od_aui_detailpages00?ie=UTF8&psc=1]("https://www.amazon.com/gp/product/B003DRMKXW/ref=od_aui_detailpages00?ie=UTF8&psc=1")

Any tuner card or usb suggestions that are newer and work in Linux?

---

### Post by #&amp;thj^% on 2018-11-07
All though this site has not been updated since 2015, should still give you some ideas: [https://nucblog.net/2014/12/recommended-usb-tv-tuners-for-linux/](https://nucblog.net/2014/12/recommended-usb-tv-tuners-for-linux/)
Forgot to add this one as well: [https://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices](https://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices)

---

### Post by linuxhippy on 2018-11-07
Cool thanks!  I think some tech within last 5-6 years would work nicely with 2018 TV waves.  Thanks and USB tuners will work with my old pc.  I probably have USB 2.0 ports-are those fast enough for these USB tuners or should I update the motherboard with USB 3.0 ports?

---

### Post by #&amp;thj^% on 2018-11-07
It probably won't matter much with 90% of them, but I'm the type that craves "_more power more power more power"_:)
I have to admit that USB3 is a noticeable improvement for devices that support it.

---

### Post by TheFu on 2018-11-07
For OTA - just get a Silicon Dust HDHR4 or later device.  That removes the tuner from any specific computer and places it on the network for use by any devices you like.  You can place the network tuner closer to your antenna which will reduce the signal loss from long coax runs as well.  Ethernet easily goes from 1 end of a house to another, whereas coax signals drop for every foot.

HDHR tuners are well supported by all platforms and MythTV.  I'm using 6 (3 tuner boxes with dual tuners each).  Two are the older HDHR3 models which require specific drivers.  1 is an HDHR4 which supports DLNA ... so pretty much any computing device in your home can use it.  I was watching the election results last night on a 2inch VLC screen while the family watched a movie on the projector via a Kodi system running on a v2 Raspberry Pi.

Plus trying to get an antenna that is tuned for the actual RF signals in your part of the world would be smart too.  Good antennas are often smaller, plus pointing them in the correct direction to get the best reception helps greatly.  [http://tvfool.com/](http://tvfool.com/) will help with this.  I've done lots of research about different antennas.  After building a few different types and buying both a DB4 and Yagi, it turned out that the best antenna for my location was a specifically designed DB4 where I made the whiskers long enough to get VHF-Hi and the core UHF channels in my area.  TVFool provides the needed data for those design choices, if you are so inclined.

  [http://www.tvfool.com/?option=com_wrapper&Itemid=29&q=id%3d9038fd805ee086](http://www.tvfool.com/?option=com_wrapper&Itemid=29&q=id%3d9038fd805ee086) is a generic TVFool report for Philly.  Looks like pointing the antenna at 340 deg magnetic will get almost all the stations. Most are UHF, but ABC is in the VHF-Lo range - get some rabbit ears for that 1 station. All the others are UHF.  If you are N-NW of the city center, you'll get better reception - assuming there aren't any hills or buildings in the way. The transmission towers are only 7 miles out, so a fancy antenna shouldn't be needed.

I'm 52 miles from 1 set of transmission towers and 23 from another. They are in 2 different directions, so I point my home made DB4 at the 23 mile away towers and use the Yagi for the 52 mile towers.  Great signal to noise here, luckily.  In fact, a few channels come in too strong when the leaves all fall, so I have to shift the direction of the antenna for winter.

---

### Post by 1clue on 2018-11-07
Not really familiar with PCI cards that implement TV tuners, but I'm familiar with TV in general. So pardon any stupid questions :)

1. Do you have an antenna hooked up to your card?
2. Have you tried the same antenna and same connector with a conventional TV? If so, how do they compare?
3. Are you using the correct connectors on your antenna wires?

So, here's what I know:
1. Computers are in cases, and those cases are designed to limit electromagnetic noise going through the case. That means both directions.
2. The PCI card is inside the case. So electromagnetic noise (signals from your TV stations) can't get in very well.
3. That also means that any noise created by your computer (there's a lot of it) is bouncing around inside the case, making it even harder for your tuner card to work.
4. If you're using a TV antenna and it's not correctly hooked up with a well-installed standard connector, you attenuate (lose) signal.

The entire signal path from your antenna to your tuner is designed to maximize signal and minimize noise. Do-it-yourself connectors (just making the wires touch the jack on your tuner card, or improperly attaching the correct connector) will not fix the problem and may actually introduce noise.

You want an antenna, even if your normal TV set doesn't have one. That antenna should be placed advantageously in spite of your computer/TV location, unless you're living in a large city with a bunch of transmitters, which it seems you're not.

---

### Post by #&amp;thj^% on 2018-11-07
> **TheFu said:**
> 
Plus trying to get an antenna that is tuned for the actual RF signals in your part of the world would be smart too.  Good antennas are often smaller, plus pointing them in the correct direction to get the best reception helps greatly.  [http://tvfool.com/](http://tvfool.com/) will help with this.  I've done lots of research about different antennas.  After building a few different types and buying both a DB4 and Yagi, it turned out that the best antenna for my location was a specifically designed DB4 where I made the whiskers long enough to get VHF-Hi and the core UHF channels in my area.  TVFool provides the needed data for those design choices, if you are so inclined.

Golf Clap ; very important " antenna that is tuned for the actual RF signals in your part of the world"
A very needed and well worded input.

---

### Post by linuxhippy on 2018-11-07
I didn't know they had manufactured tuner boxes and I like the Silicon Dust ones.  I just bought the SiliconDust HDHomeRun Connect Duo 2-Tuner LiveTV for Cord Cutters (HDHR5-2US) and hopefully this will work nicely with my HD antenna in mythbuntu.  Do u think that booster just amplifies the noise that was mentioned in tuning over the air signals in?

---

### Post by TheFu on 2018-11-07
Don't have that model, but Silicon Dust is well respected in the HTPC world. I think you'll be happy. My HDHR4 is better than the HDHR3 versions before it.  Using an android app, I suppose I could figure out how much better, but it just hasn't been important.  

Something you should know - the USA will be changing from ATSCv1 to a newer standard at some point.  2022-2025 is likely.  That will break all our existing tuners, since the new standard encoding will be h.265 or AVC1, not MPEG2 like today. 

Getting antenna reception is a very local issue.  Even people in the same neighborhood will have different reception, so without seeing a correct, exact, tvfool diagram, nobody can say anything.  The sort of antenna you have matters greatly too. None of that data has been provided here and really, it would be off-topic in Ubuntu forums.

---

### Post by linuxhippy on 2018-11-07
> **TheFu said:**
> For OTA - just get a Silicon Dust HDHR4 or later device.  That removes the tuner from any specific computer and places it on the network for use by any devices you like.  You can place the network tuner closer to your antenna which will reduce the signal loss from long coax runs as well.  Ethernet easily goes from 1 end of a house to another, whereas coax signals drop for every foot.

HDHR tuners are well supported by all platforms and MythTV.  I'm using 6 (3 tuner boxes with dual tuners each).  Two are the older HDHR3 models which require specific drivers.  1 is an HDHR4 which supports DLNA ... so pretty much any computing device in your home can use it.  I was watching the election results last night on a 2inch VLC screen while the family watched a movie on the projector via a Kodi system running on a v2 Raspberry Pi.

Plus trying to get an antenna that is tuned for the actual RF signals in your part of the world would be smart too.  Good antennas are often smaller, plus pointing them in the correct direction to get the best reception helps greatly.  [http://tvfool.com/](http://tvfool.com/) will help with this.  I've done lots of research about different antennas.  After building a few different types and buying both a DB4 and Yagi, it turned out that the best antenna for my location was a specifically designed DB4 where I made the whiskers long enough to get VHF-Hi and the core UHF channels in my area.  TVFool provides the needed data for those design choices, if you are so inclined.

  [http://www.tvfool.com/?option=com_wrapper&Itemid=29&q=id%3d9038fd805ee086](http://www.tvfool.com/?option=com_wrapper&Itemid=29&q=id%3d9038fd805ee086) is a generic TVFool report for Philly.  Looks like pointing the antenna at 340 deg magnetic will get almost all the stations. Most are UHF, but ABC is in the VHF-Lo range - get some rabbit ears for that 1 station. All the others are UHF.  If you are N-NW of the city center, you'll get better reception - assuming there aren't any hills or buildings in the way. The transmission towers are only 7 miles out, so a fancy antenna shouldn't be needed.

I'm 52 miles from 1 set of transmission towers and 23 from another. They are in 2 different directions, so I point my home made DB4 at the 23 mile away towers and use the Yagi for the 52 mile towers.  Great signal to noise here, luckily.  In fact, a few channels come in too strong when the leaves all fall, so I have to shift the direction of the antenna for winter.

So I got this HD Home Run (HDHR5-2US):

[https://www.amazon.com/gp/product/B07GL4VK1H/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1]("https://www.amazon.com/gp/product/B07GL4VK1H/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1")

Your router plugs right into this (pictured) and then u can have an ethernet cable (I think) go from your router to your Mythbuntu backend to store these shows.  How does Mythbuntu know to use your ethernet line as a tuner card?

---

### Post by TheFu on 2018-11-07
[https://www.mythtv.org/wiki/Silicondust_HDHomeRun_Dual](https://www.mythtv.org/wiki/Silicondust_HDHomeRun_Dual)

Just connect the HDHR to your normal wired ethernet network.  The MythTV backend is already connected to it with wired ethernet. Diagram here: [https://www.silicondust.com/product/hdhomerun-connect/](https://www.silicondust.com/product/hdhomerun-connect/)

---

### Post by linuxhippy on 2018-11-07
> **TheFu said:**
> [https://www.mythtv.org/wiki/Silicondust_HDHomeRun_Dual](https://www.mythtv.org/wiki/Silicondust_HDHomeRun_Dual)

Just connect the HDHR to your normal wired ethernet network.  The MythTV backend is already connected to it with wired ethernet. Diagram here: [https://www.silicondust.com/product/hdhomerun-connect/](https://www.silicondust.com/product/hdhomerun-connect/)


That diagram was also on the Amazon page (2nd image) and is what made me wonder how Mythbuntu will see eth0 (or enp2s3 on this pc) as a tuner source?  Do I need to create a symbolic link from eth0 to /dev/dvb/adapter2?

---

### Post by TheFu on 2018-11-07
No. Check out the first link. It is a network protocol.

I don't use mythtv.  I use kodi/OSMC or vlc or 7MC or any download tool, like wget.   But mythtv has worked with these devices for a very, very, long time.  I'd guess 15 yrs.

---

### Post by linuxhippy on 2018-11-07
I've seen it always prompt me in settings if I have an HD home run device.  I guess I just pick that this time.  I'll find out soon if it's that easy.

---

### Post by linuxhippy on 2018-11-10
I got my HD HomeRun 5 tuner box yesterday and setting it up with mythbuntu once it was on my network was easy in the backend settings.  Here's the default settings that were picked for me:

[ATTACH=CONFIG]281607[/ATTACH]

I still can't get all the channels that TV Fool says are available to me by my address.  My neighborhood is in a sort of small valley, so I've always thought that my neighborhood terrain was why I couldn't get 6 ABC here but TV Fool thinks I should be getting it.  I didn't realize it was on the low area of the VHF band still so maybe a simple rabbit ears antenna would work for me as the TV tower is only 10 miles away.

My current antenna is a clearstream that cost $80 so I'm surprised it can't pull in VHF with the UHF.  Their new design has the VHF poles but I'm not sure how to add these without buying the new antenna.  This is what I have for an antenna:

[https://www.xsdepot.com/Product/346862-Antennas-Direct-Clearstream-2-Long-Range-IndoorOutdoor-HDTV-Antenna]("https://www.xsdepot.com/Product/346862-Antennas-Direct-Clearstream-2-Long-Range-IndoorOutdoor-HDTV-Antenna")

So a number of different antennas were mentioned here.  Is it possible to have 2 antennas wired into the same computer tuner?

---

### Post by TheFu on 2018-11-10
You should ask those TV signal and antenna questions on the tvfool forums.

At first look, you shouldn't need that expensive antenna and definitely shouldn't need any amplifier.  10 miles is nothing. A $2 antenna should be fine if it has line of sight to the transmission point.  But we don't have **any** data about your location or antenna setup.  Ask on tvfool.

---

### Post by linuxhippy on 2018-11-10
ok-I'll look at TV fool forums.  I liked your comments on the various antennas though and didn't realize rabbit ears were still used for HDTV till u mentioned it.  I have one of these coaxial splitters but never used it to join 2 antennas.  Is that what u do?

[ATTACH=CONFIG]281608[/ATTACH]

---

