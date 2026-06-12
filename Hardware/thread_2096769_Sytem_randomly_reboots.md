---
title: "Sytem randomly reboots"
date: 2012-12-20
forum: Hardware
---

### Post by skaramanger on 2012-12-20
Greetings,

I need some help.  I have an M2N-SLI MB bios 5001 running an AMD Phenom IIX4 940 with 4 X 1GB OCZ800 DDR2 dimms.  I have a degraded Raid 1 array (that I'll deal with later) a 320GB system disk and a dvd/rw drive. Originally, I had a Palit GT240 video card (non-sli).  Recently, I replace my Palit with an EVGA GT560ti. This all powered by a Thermaltake TR2-600w PSU.  The machine awhile back had a problem with usb port problem (okay I just moved some connectors around and forgot about it).  Now though the machine frequently reboots when under any kind of load or I'll come in in the morning and find it sitting at the login screen.

When I first power on the machine I hear a revving sound from one of the fans. (Palit)  Always heard this from the Palit?  dmesg always showed a message regarding mal-non-functioning cpu thermal sensor :(.  Okay I ignored that for maybe too long.  but the machine never displayed any issues before and it has run mostly 24/7.

hardware specs in bios shows the voltages as follows:

vcore: 1.31
3.3V: 3.29
5V: 4.91V
12V: 12.09V

I have been doing some troubleshooting:

The every ram stick fails in any slot running memtest at test 7 and it is massive thousands if I go away for awhile. I have disconnected every non-essential device and still the sam.  I went to the asus websit:


[http://support.asus.com/powersupply.aspx?SLanguage=en]("http://support.asus.com/powersupply.aspx?SLanguage=en")

and input the specs and came up with a minimum of an 800 psu or so.

I want to know if there is a definite answer here.  Did I slowly cook my MB running under powered and inturn toasted the RAM?  Or Just my MB? or just the RAM.  I did try a smaller known good power supply got the same memory errors from memtest.   So I don't have alot of money to throw around and I want to be able to use my SLI ready card.  What recommendations do u my fellow (k)ubuntu hardware gurus recommend?

TIA

btw I have done some internet research (Toms Hardware) and no problem quite matchs mine

---

### Post by cwsnyder on 2012-12-21
I am confused.  Did you switch back to the Palit 240GT video card, or stay with the EVGA GT560ti video card during these tests?  When you tried the 'known good' lower power supply, were you running the Palit 240GT video card, the EVGA GT560ti, or another lower power video card?

I am tempted from your description of your problems to recommend a new power supply, and definitely increase it to 800W+ if you are wanting to run the EVGA GT560ti video card.  From your system description, I looked up that even with the Palit video card, the video card is pulling around 170-200W, and the EVGA video card would be pulling 170-205W as well.  Your PSU is definitely under-rated for a quad-core and those video cards, even with only 4G RAM.

---

### Post by skaramanger on 2012-12-21
> **cwsnyder said:**
> I am confused.  Did you switch back to the Palit 240GT video card, or stay with the EVGA GT560ti video card during these tests?  

I switched to the Palit for all my testing.

When you tried the 'known good' lower power supply, were you running the Palit 240GT video card, 

The Palit

the EVGA GT560ti, or another lower power video card?

I am tempted from your description of your problems to recommend a new power supply, and definitely increase it to 800W+ if you are wanting to run the EVGA GT560ti video card.  From your system description, I looked up that even with the Palit video card, the video card is pulling around 170-200W, and the EVGA video card would be pulling 170-205W as well.  Your PSU is definitely under-rated for a quad-core and those video cards, even with only 4G RAM.

I looking locally for a new psu.


I just tested now with two hardly used Crucial 2GB sticks and the same memory error on memtest #7.  I just shut it off as it stared to reboot.  No need to mess with the HDD and my installation.

---

### Post by skaramanger on 2012-12-24
> **cwsnyder said:**
> I am confused.  Did you switch back to the Palit 240GT video card, or stay with the EVGA GT560ti video card during these tests?  When you tried the 'known good' lower power supply, were you running the Palit 240GT video card, the EVGA GT560ti, or another lower power video card?

I am tempted from your description of your problems to recommend a new power supply, and definitely increase it to 800W+ if you are wanting to run the EVGA GT560ti video card.  From your system description, I looked up that even with the Palit video card, the video card is pulling around 170-200W, and the EVGA video card would be pulling 170-205W as well.  Your PSU is definitely under-rated for a quad-core and those video cards, even with only 4G RAM.


My new Seasonic 1000W PSU arrived today and I am working at my station now.  I noticed a big difference when first starting the computer up.  The fans didn't didn't make a rev'ing  sound and it started up quietly.  A nice change.

However, I still am experiencing the memtest errors in test seven.  I'm currently running memtest 4.20.  And after failing with the 1GB ocz' rated at 5-5-5-15 by memtest, I installed the 2GB Crucials that memtest rates at 6-6-6-18.  I still got the same random number tests errors.  I'm going to continue my search using google some more.  Anybody else have any suggestions?

Tia.

---

### Post by skaramanger on 2012-12-24
Okay I found out that there is a build problem with all the memtest 4.20z that show up on 'buntuz. 

[http://forum.canardpc.com/threads/72840-Ubuntu-12.10-build-Memtest-v4.20-fails-on-Sandy-Bridge]("http://forum.canardpc.com/threads/72840-Ubuntu-12.10-build-Memtest-v4.20-fails-on-Sandy-Bridge")

---

### Post by skaramanger on 2012-12-24
Sorry this link:

[https://bugs.launchpad.net/ubuntu/+source/memtest86+/+bug/1071209]("https://bugs.launchpad.net/ubuntu/+source/memtest86+/+bug/1071209")

Thanks:D

---

### Post by absolute512 on 2013-02-11
I have a similar problem, so decided to post right here...
New system build for media center, following components:

- Intel Core i3-3225 @ 2.0 GHz
- Intel DH77DF Mobo
- Kingston HyperX PC10600 (2x 4GB)
- Intel Advanced-n 6235 wifi/bt (miniPCI express)
- Streacom Nano150 psu
- Streacom fc8 evo case
- Logitech diNovo mini Keyboard (over internal bt)

The System reboots randomly (after about 15-20 Minutes) and enters a reboot-loop (just until the mouse-pointer shows and bam - reboot). If I wait 10 minutes it boots normally.
Also, the system will enter the reboot-loop directly when running Memtest86 (Memtest loads the blue/red screen for less than half a second and the system reboots).
Reboots do not happen within Intel visual bios/efi (within 5 hours)

Steps taken:
* Have changed the memory to the currently equipped Kingston (was using some Samsung sticks before), no change.
* installed psensors (reports ~45ºC on average, ~28ºC when running it on the balcony (It's -5ºC outside).
* Voltages (from within Efi) are stable.

I'm going to swap cooler (to stock intel instead of passive one) and psu next.

Any Ideas?

---

### Post by wt-lists on 2013-10-20
> **absolute512 said:**
> I have a similar problem, so decided to post right here...
New system build for media center, following components:

- Intel Core i3-3225 @ 2.0 GHz
- Intel DH77DF Mobo
- Kingston HyperX PC10600 (2x 4GB)
- Intel Advanced-n 6235 wifi/bt (miniPCI express)
- Streacom Nano150 psu
- Streacom fc8 evo case
- Logitech diNovo mini Keyboard (over internal bt)

The System reboots randomly (after about 15-20 Minutes) and enters a reboot-loop (just until the mouse-pointer shows and bam - reboot). If I wait 10 minutes it boots normally.
Also, the system will enter the reboot-loop directly when running Memtest86 (Memtest loads the blue/red screen for less than half a second and the system reboots).
Reboots do not happen within Intel visual bios/efi (within 5 hours)

Steps taken:
* Have changed the memory to the currently equipped Kingston (was using some Samsung sticks before), no change.
* installed psensors (reports ~45ºC on average, ~28ºC when running it on the balcony (It's -5ºC outside).
* Voltages (from within Efi) are stable.

I'm going to swap cooler (to stock intel instead of passive one) and psu next.

Any Ideas?

Hi,

I'm wondering if you ever found out what's the problem? I've similar problems with an Intel DH77DF and while it runs stable for hours sometimes it repeatedly reboots within 20 seconds on other days. Logs, temp. monitor etc. show nothing...

br
Wolfgang

---

### Post by t-golightly on 2013-10-20
> **wt-lists said:**
> Hi,

I'm wondering if you ever found out what's the problem? I've similar problems with an Intel DH77DF and while it runs stable for hours sometimes it repeatedly reboots within 20 seconds on other days. Logs, temp. monitor etc. show nothing...

br
Wolfgang

I havn't run memtest in some time on my rig.  my random reboots have ended after adding the 1000W Seasonic Platunum I PSU.  I have a cheap Chinese Power supply tester and while testing a customer's computer, the voltages all checked out fine.  Reconnect it to the MB, and the machine fails to boot with an amber pwr button (Dell desktop).  It could be a combination of the mb damaging the psu  or a psu that won't handle a normal load placed on it.  Have any of you tried disconnecting all peripherial and just see how that affects you rig's.  From my experience an intermittant electrical issue that only a properly equipped test bench with a capable tech can ferret out problems like these.  Check for even minute damage to wires and give them a wiggle.  It can be the most inobvious cause.

Regards,

T-Golightly a.k.a. Skaramanger

---

