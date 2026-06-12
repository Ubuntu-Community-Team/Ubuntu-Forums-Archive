---
title: "Battery life HP dv6699"
date: 2009-05-25
forum: Hardware
---

### Post by fontis on 2009-05-25
Hey guys, the topic says it all.
I'm a pending user between Vista and Ubuntu on my laptop. 
I curse myself every day for using Vista instead of trying to go open-software radical.. So I'm trying to figure out which is the best for my laptop to run.

Can anyone somewhat estimate how long the laptop battery lasts on an HP DV6699 (or DV6000 series) laptop? And also, how is the CPU temperature? I notice my fan is working a LOT in Vista and the CPU seems strained a lot, how is this in Ubuntu 9.04?

Thanks!

---

### Post by Dark_Stang on 2009-05-25
I have a dv6636nr. With my old 6 cell battery it would last 2.5 - 3.5 hours, depending on what I was doing. With my new 12 cell battery it will last 6 hours pretty easily.

---

### Post by rob2uk on 2009-05-25
Tenuous link, but please please please, if you have an HP DV-series make sure you update the BIOS!

I'm getting 5 or 6 DV's in at work, all with the same problem - the fan control in the BIOS is basically useless, laptop overheats and destroys the graphics card.

Not exactly a cheap repair as it's an integrated card...

---

### Post by Dark_Stang on 2009-05-25
> **rob2uk said:**
> Tenuous link, but please please please, if you have an HP DV-series make sure you update the BIOS!

I'm getting 5 or 6 DV's in at work, all with the same problem - the fan control in the BIOS is basically useless, laptop overheats and destroys the graphics card.

Not exactly a cheap repair as it's an integrated card...
Really now? Because I work for a fairly large company that sees a few thousand machines a day. The only issue that I have heard of and seen with the dv series is related to the mini pci slot on the the early dv2xxx, dv6xxx, and dv9xxx laptops. I have yet to see any have overheating issues that weren't related to massive amounts of dust and pet hair being stuck in the vents.

---

### Post by rob2uk on 2009-05-25
> **Dark_Stang said:**
> Really now? Because I work for a fairly large company that sees a few thousand machines a day. The only issue that I have heard of and seen with the dv series is related to the mini pci slot on the the early dv2xxx, dv6xxx, and dv9xxx laptops. I have yet to see any have overheating issues that weren't related to massive amounts of dust and pet hair being stuck in the vents.

How many links would you like?

[HP forums]("http://forums11.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1179013")

[Notebook Review forums]("http://forum.notebookreview.com/showthread.php?t=218354")

[HP Warranty Enhancement (about as close to a product recall as HP ever get)]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01087277&lc=en&cc=us")

[Notebook Review (again)]("http://forum.notebookreview.com/showthread.php?t=219927")

[Yahoo answers]("http://answers.yahoo.com/question/index?qid=20080117135105AAkGUVC")

Need any more? Google has nearly 5000 hits for "DV2000 BIOS fan control"

---

### Post by rob2uk on 2009-05-25
(sorry to double-post)

One more link:

[version F.39 BIOS update for DV2000]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-56219-1&lc=en&dlc=en&cc=uk&product=1817074&os=228&lang=en")

> PURPOSE: Critical
Enhancements: 		Updates the fan control algorithm of the system to reduce the likelihood of future system issues

---

### Post by Dark_Stang on 2009-05-25
The service alert is about the mini pci slot for earlier laptops. Please note that his laptop is not in the service alert. As I stated before, only the earlier dv laptops had the issue. And this is a known issue that I see on a weekly basis.

One post on yahoo answers doesn't mean anything. Look at how many idiots ask what sex is and how babies are made on there. Sorry, but I just can't take anything from there seriously.

And the bios update was released by HP because they thought the laptops may have overheating issues or failure in the future. I haven't seen this with any of the dv laptops that walk through the door at my work. Nor have I heard any rumors from other employees. The theory that the overheating makes the wireless fail first is crazy. The wireless cards are in a well vented spot next to the RAM on these laptops. If anything, the video card or processor would be the first thing to fail due to heat damage.

Now if you had said Toshiba a215 laptops had overheating issues, I would agree. I saw hundreds of those things come across my bench needing BIOS updates. Not to mention the whole "I think you need a random bios password on this laptop on the next reboot" thing. I still see a few of those.

---

### Post by rob2uk on 2009-05-26
Fair enough, your experiences seem to differ to mine.

I completely agree with you on the wireless card thing, btw...

The overheating issue *does* seem to affect *almost* all of the DVxxxx series, some models to a very high degree, others almost non-existent - although again, you are right about his particular model not being affected - I saw that it was a dv6xxx series and jumped the gun

If you read the service alert again you'll notice that it doesn't *only* refer to the wireless issue:

[quote]The following symptoms apply to the dv6000, dv9000 and v6000 series notebooks:

    *  The notebook does not detect wireless networks and the wireless adapter is not detected in the Device Manager.
    * **There is no video on the computer LCD panel or external monitor.**
    * The notebook has no power and no active LEDs.
    * The notebook does not start.
    * The battery charge indicator light does not turn on when the battery is installed and the AC adapter is connected.
    * The notebook issues a single beep during boot indicating no power.
    * **The external monitor functions but there is no image on the notebook LCD panel.**

(apologies if I've come across as being arrogant or anything - it's 5am and my hayfever is causing a sense of humour failure)

---

### Post by fontis on 2009-05-26
I have to second the BIOS thing though.
Because I recently flashed my BIOS to the latest version, prior to that the BIOS version was frmo 2007. 

And I **DID** have a problem with my laptop generating more heat, and the fans working weirdly compared to my girlfriends Acer. And I too heard that the BIOS upgrade was necessary to sort this out. 

So.. don't mean to stomp on any toes, but the BIOS flash I did a couple of days ago completely changed everything. My laptop generated heat is much better handled now and it's generally both cooler and more effective. For once my laptop doesn't sound like an old AMD-Thunderbird.

Back to the battery thing... is the battery life higher on win compared to ubuntu or do you get the same amount of juice on both ends with your new one?

Thanks!

---

### Post by Dark_Stang on 2009-05-27
My battery lasted longer under Linux. Powernowd and the gnome power settings do a much better job than Windows' power management on my laptop. 

My laptop still runs the original BIOS version and my processor runs 100F-110F (34C-38C). If I'm playing an intense game or compiling a large program, then it runs a little bit hotter, but not by much.

---

### Post by fontis on 2009-05-27
Hmm, that's weird. I guess you're lucky not to be affected :D

Anyhow, anyone else got any other estimations?

---

