---
title: "Completely random crashes/reboots in Vista AND Linux.... hardware?"
date: 2008-11-24
forum: Hardware
---

### Post by TomX19 on 2008-11-24
Hi,

I hope someone can advise me on what I can check for regarding this issue.

My PC crashes or reboots itself with alarming frequency, perhaps on average every half hour... not that I could really pick out any kind of pattern.  What happens is sometimes the screen will "blur" and the sound (if playing) will stutter like a skipping CD and I have to hit the reset button on the base unit, or sometimes the screen will go black and the PC reboots by itself.

I started out with Vista and thought this was a Vista issue as everyone says it's crap, which is what prompted me to move to Linux.  However, now I'm running a dual boot the problem is almost as bad in Ubuntu and I'm worried that it's damaging.

I have a desktop PC, specs as follows:

Pentium Dual Core E2180
nVidia Geforce 7050 & 1333Mhz FSB
500GB Serial ATA 2.0 With 16MB Cache
4096MB (4GB) DDR RAM Memory 2 x 2GB STICKS
GeForce nVidia 7050TC 512MB

The crashing is not more common with any particular activity.  Today it even crashed when booting, usually it can crash with nothing more than browsing with Firefox.  I'm wondering if it has to do with temperature.  The room is always below 21°C and the highest I've seen the CPU temp go is 28°C

Are there any tests I can run on the hardware?

Thanks in advance :)

Tom

---

### Post by Bucky Ball on 2008-11-24
Yep, sounds like a hardware problem to me as is it consistent using either OS. RAM usually just dies (no half measures) so doubtful it is that, though don't quote me! Maybe confusion with the two vid cards or one of them is on the way out. How old is the hard drive?

Was this machine working without a hitch with this setup previously? Is there anything, any changes that you have made that coincide with the problem?

Maybe think about the age of the hard drive and also, you have some nice stuff in the box but what is powering it? Some users overlook the power supply. If that is a nameless silver box, they are extremely inefficient (normally -70% energy efficient) with no inbuilt safety precautions or switches (usually) and if it is the PSU, you are lucky it is going by stages as the silver box variety often go off with a bang and cook the other components. Maybe check the heat of that. If you can cook an egg, something is wrong.

My guess is that this has nothing to do with your software. Can't give you any clues at the moment as to how to check your hardware, maybe someone else can join in and help there. Will have a bit of a look around later.

---

### Post by TomX19 on 2008-11-24
The whole lot is about a month old - I can't say I've ever had it working without a hitch but I spent the first month assuming it was down to Microsoft, and as I was spending the first few weeks ripping CDs into iTunes I was blaming the iTunes/Vista combo for a while, but now I'm sure it's not that....

I don't know what the PSU is, but the PC is not a name brand so the maker might have cut costs on the PSU.  I'll have a look.  

I did have the unit located about 4" from a wall and have now moved it further away to give it more room to breath, so I will see if that has any effect.  As it's so new, I've always got the option of returning it to the maker (independent UK maker)

Thanks very much for the reply :)

---

### Post by Bucky Ball on 2008-11-24
> **TomX19 said:**
> 
I don't know what the PSU is, but the PC is not a name brand so the maker might have cut costs on the PSU.  I'll have a look.  



If costs are going to be cut, the PSU is not an unusual place to start (if there is plenty of RAM and hard drive space, nice processor, most folkoverlook  the PSU). Moving it away from the wall is a good idea, might help. If the vendor is nearby, I would take it in and get them to check it out if it is still covered by warranty. The clincher for me is that it happens in both OSs and that the machine has always been problematic. You sort of ruled out a software problem when you installed a second OS.

Maybe you could give them a ring or email and explain situation first up, get their opinion and see if they come up with an obvious fix without you having to send it back in. Good luck with it all. :)

---

### Post by sandy8925 on 2008-11-24
It's obviously a hardware problem and as Buckyball said it could very likely be the PSU. Check how much power your comp needs and then check the wattage of the PSU. Most PSU's don't supply the full wattage that they claim to do. It could also be a problem with the RAM/CPU/motherboard. Just test everything if you can.

---

### Post by Bucky Ball on 2008-11-24
> **sandy8925 said:**
> It could also be a problem with the RAM/CPU/motherboard. 

As I mentioned earlier, RAM normally just dies, but this could be an exception. CPU or motherboard are other possibilities though. But could (hopefully) be a dodgy card reader shorting or something dumb (but and not so drastic)!

One thing you can test is the RAM. Just pull a stick and boot it. If it works, pull it and try the other. You will get a beep if the RAM is dead (which is another reason I don't think it is RAM). Make sure this doesn't void any kind of warranty, though - check first and if it does, let them do this test. Some places wash their hands of you as soon as you open the box.

Is there anything exotic in there? Another thing you can do, if you have the maker's approval to do so, is unplug everything except the RAM and 1 hard drive. No cd/dvd/cardreader/USB dongle. Nothing. Then boot and see if you get the problem. If not, plug things in ***one by one***, booting each time until you do, then you'll have found the culprit. If it is misbehaving with just a drive in the box, then you have narrowed it down to the motherboard or processor, or of course the drive. So try another drive and rule that out.

Changing processor or motherboard is about when I would be taking it back, but I would be probably letting them do all this anyhow. After all, it is faulty merchandise by the looks.

---

### Post by TomX19 on 2008-11-24
Would the RAM test option in the grub menu suffice?  I have run through this and it's come up ok.

I won't invalidate the warranty by having a butchers inside as there are no seals or anything...  I'm looking for a screwdriver now!

EDIT: PSU is Alphapower ATX-450W, whether this is any good or not I don't know!

Other than looking there's not much else I can do in there.  Soundcard and graphics card appear to be incorporated on the same motherboard.  The only thing I could remove for testing would be the memory cards.  I think I'm going to email the manufacturer and get them to take it back for testing

---

### Post by Bucky Ball on 2008-11-24
[http://nickj.org/Linux_setup_steps#Run_memtest_overnight](http://nickj.org/Linux_setup_steps#Run_memtest_overnight)

You are talking Memtest86+? My issue with this is, will the computer stop crashing long enough to complete the test(s)? That is why physically removing stuff is more surefire (and a lot quicker). But not everyone is comfortable with this option. So sure, sounds good, give Memtest a go and keep your fingers crossed for a window of good behaviour from the box! Memtest86+ will also test CPU, incidentally.

---

### Post by oldsoundguy on 2008-11-24
If it is hardware, just a memory test will not suffice.  You need to test it ALL.
This disk (download and burn it!) [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) is more than way cool.  Linux/DOS based, it will make your computer groan if there are any issues.  MANY testing programs within.
I have found it a totally invaluable tool for FREEEEEEEEE

I also lean toward the PSU problem .. especially if you have added items such as extra drives and cooling in and above what came stock on that box.

my second "guess" would be a bad capacitor on the mother board power rails.  Especially if you are having stutter issues with the drives or problems with USB.

(just because it is new, does not mean that something was not missed in quality control)

---

### Post by TomX19 on 2008-11-24
One thing of possible note then is that it has an extra cooling fan pointing down at the CPU (other than that nothing extra).  This was an option they persuaded me was beneficial - it's kind of a custom build anyway so I would hope they accounted for this extra fan and specced the right kind of PSU... I wouldn't know myself as I am only semi PC literate.

Haven't had any issues with drives or USB.

Thanks for the link.  I'll have a bash at it tomorrow, as I'm off to work shortly.

EDIT: Yes, memtest 86+ was what I used to test the memory.

---

### Post by cariboo on 2008-11-24
If your system is only a month old why bother asking questions here, Take it back to where you got it from and get them to repair the problem under warranty. Make sure to remove Ubuntu before returning it, as there are a lot of techs that will blame Linux for the problem.

Jim

---

### Post by Skripka on 2008-11-24
> **TomX19 said:**
> I'm wondering if it has to do with temperature.  The room is always below 21°C and the highest I've seen the CPU temp go is 28°C



That alone sounds like a bum thermostat or botched thermal compound.  28C on the CPU is practically arctic in comparison-especially for a HIGH temp on a desktop tower, unless you're water-cooling or using a very good after-market heatsink fan.


Wipe traces of Ubuntu, and warranty it.

---

### Post by TomX19 on 2008-11-25
:confused: Since removing and reintroducng the RAM to test it I now have a blank screen and nothing else. Nightmare!  Surely not ESD in this day and age???  I didn't touch the chips:confused:

....posting from work

As far as warranty goes, yes it has it but I have to pay the carriage both ways and if they deem it not to be a hardware fault I'll be liable to pay costs before my unit is returned.  Still, I'm certain it's hardware

---

### Post by Bucky Ball on 2008-11-25
Make sure you have the single stick in slot 1 of the RAM slots. When they are new also, they can be a bit temperamental and might need to pull out and reseat once or twice. A pain, I know. Sometimes they work fine in one slot but take some massaging in another.

Are you getting a beep code? As in, when you boot, is the machine making beeping noises? If so, don't panic. Take note of the sequence. Long/short beeps and how many. This can give you a clue as to what is happening (we can attempt to look up the code for your motherboard).

---

### Post by TomX19 on 2008-11-25
No beeping at all, just.... well, nothing.  I'm going to have a fiddle with it later.  I was really careful when I removed them and replaced so I'm sure I couldn't have done any damage.  I'm having a shocker here! :confused:

---

### Post by Bucky Ball on 2008-11-25
> **TomX19 said:**
> No beeping at all, just.... well, nothing.

Do you mean nothing? The machine is not powering up *at all*? Listen for the fan and check the fan in the power supply. When you have the side off fiddling with the RAM, check the details on the PSU. They should be on the side, clearly visible.

Just remember to be careful; try not to touch too much on the board and earth yourself before grabbing anything (ie: grab the metal case). Try to touch as little as possible, including of the RAM, just grab the edges if poss. They usually only break by twist! but can be shorted if you are not earthed.

And naturally, unplug power to the beast! lol (and this means if you have a monitor which is still powered up; even though the computer might be unplugged, the monitor is not and is plugged into the computer. ... :)

---

### Post by TomX19 on 2008-11-25
Well, I'm typing this on the computer in question so some good news :)  I've got it running on 2GB but if I plug in the second 2GB of memory I get power (i.e., fan running, can hear hard drive fire up) but a completely blank display - as though the monitor is not plugged in.  It took some faffing with the first memory slot as you suggested, so I'm trying the same thing with the second but getting nowhere so far :(

---

### Post by Bucky Ball on 2008-11-25
That sounds promising. Good work! Might be that stick then. But strange there is no beep code.

So in other words, it is running without problems on 2gb? I would suggest you run it and play around for an hour or two, just to be sure. The RAM is usually covered by the manufacturer so re-sellers don't normally have a problem replacing them if you can be pretty positive that is the cause.

---

### Post by TomX19 on 2008-11-25
Yeah, I think I'm getting somewhere.  

OK, Let's call the RAM Dave and Betty; so....

Dave in slot 1, slot 2 empty - Boots up ok.

Dave in slot 1, Betty in 2 - power (PSU, fans, hard drive) with blank screen....

Betty in slot 1, two empty - Same problem....

Betty in slot 1, Dave in slot 2 - Same problem.....

-

Of course there's a chance that I just knackered the second 2GB of memory by pulling it out so I'm currently going to sit here watching BBC iPlayer until I crash (or not) so I can get an idea if I'm still getting the crashing problem.  It was very rare to be able to sit through a half hour programme on iPlayer without crashing before all this, so this should be a good test.

-

Thanks for all the help so far :)

---

### Post by Bucky Ball on 2008-11-25
Betty sounds like she could be the culprit. Fingers crossed. Still bamboozled about the beep though. Oh, well. Sounds like you might have nailed it though. Temperature still okay and everything normal with the one good stick in?

As I say, pretty hard to knacker the ram unless you are reasonably violent (twisting or shorting is what normally kills 'em - or they just die but normally DOA with RAM).

---

### Post by TomX19 on 2008-11-25
Temp average 25°C according to the readout which comes up at reboot.

No noticable drop in performance in Ubuntu with "only" 2GB BUT... still crashing.  Some notes;

In Vista: 
- More likely to crash when synching iPpod using iTunes.  Especially bad when ripping CDs.
- More likely to crash if watching/listening to media (more likely than in Ubuntu).
- Likely to crash after about twenty minutes of running a screensaver if left alone.
- Small chance of crashing again on reboot (sometimes before reaching login screen) following a crash.

Ubuntu:
- Pretty stable with general tasks like file management, web browsing in Firefox.  Occasional crashes though, maybe after an hour or two but quite rare.
- Quite likely to crash when watching video; YouTube, BBC iPlayer etc.  Will probably crash within 30 minutes.  Can sometimes get away with about 45minutes.
- More likely to crash when listening to online radio streams or playing music files.  Not quite as common as when using audio-visual media.     
- Almost guaranteed to crash if left alone to launch the screensaver (Matrix GL - set to come in at twenty minutes).  Will probably crash within 30 minutes on the screensaver.


The frozen screen/stuttering sound crash is more common than the self-reboot type.

I can send it back to the maker, but I'm paying packaging and shipping both ways by recorded delivery, so I could probably buy a new PSU and motherboard for what that will cost me!  

And I could probably find a friend who could test the suspected faulty memory for me on a different machine.

---

### Post by loadinglinux on 2008-11-25
I had a machine once that did just this exact same thing.  Come to find out it was a bad GPU.  Swapped it out with a new card - same model and problem went away.

LL

---

### Post by upchucky on 2008-11-25
the first thing to check was the power supply, is it underpowered for the twin vid cards? I suspect it is.

If a psu is underpowered then you can have varying symptoms and if the system is shutting down on low power then it should have been logging this somewhere. google the error code for the beep you hear.

this is a custom built machine, are the motherboard jumpers set right? are the jumpers set right on the vid cards?

more data......neeeed more data........

---

### Post by TomX19 on 2008-11-26
Thanks for the replies.  My computer literacy is low-average so I'm doing my best ;)

loadinglinux, I'm afraid I don't know what a GPU is:oops:

So, my PC has a 450W PSU, it has two cooling fans (three if we include the one on the CPU), one HDD, one CD drive.  The sound and graphics are built into the motherboard as far as I can tell.

---

### Post by Bucky Ball on 2008-11-26
GPU = graphics card and RAM on it ...

A couple of cards hanging off that power supply could be your problem. They chew the juice, if you follow me. loadinglinux has a point, but I think upchucky (and you gotta love that handle) has a better one.

---

### Post by TomX19 on 2008-11-26
Right, after a good half hour of unpluggling, jiggling the RAM cards, unplugging, jiggling the RAM cards etc. etc. etc. I'm back up to 4GB

After doing so I've unplugged the second cooling fan to see how I go with one less thing running off the PSU.  Worth a try???  Most have said that as my CPU temp is always less than 30°C it doesn't seem to be a concern...

I'll try and re-post the spec as best I can.  There's no secondary GPU, just a motherboard with no additional cards:

- PSU: Alphapower ATX-450W
Specifications: **maximum **power: 450 watts. Overload protection: +5v:60a maximum / +12v:35a maximum / +3.3V:50a maximum. Input voltage: 100-132 vac or 200-264 vac user selectable. Input frequency: 50-60 hz. Input current: 8a max for 115 vac/4.5A max for 230 vac. Hold up time:14ms at maximum load and normal ac input voltage. Efficiency: >65%. Fan size: 20 mm x 120 mm x 25 mm. Fan type: ball bearing. Unit dimension: 1/2 l x 5 1/2 w x 3 3/8 h. Mtbf:30000 hours of continuous operation at 25dc full load. Switches: atx logic power rocker switch.

- 2 x unbranded DC12v fans (one currently disconnected - as above)

- 2 x Samsung DDR2 2GB 800Mhz 256MB RAM cards

- Biostar GF7050V-M7-SE GeForce 7050 Socket 775 mATX Motherboard w/LAN
    *  Biostar GF7050V-M7-SE GeForce 7050 Socket 775 mATX Motherboard General Features:
    * NVIDIA GeForce 7050 chipset 800/1066/1333 MHz Front Side Bus (FSB) Socket 775 mATX form factor
    * Supports up to 4 GB DDR2 667/800 MHz SDRAM Realtek ALC662 6-channel HD audio CODEC
    * Realtek RTL8201CL 10/100 Ethernet controller One (1) UDMA/133 IDE controller
    * Four (4) Serial ATA controllers

- Pentium E2180 CPU

- 1 x Lighstribe CD-ROM drive, unsure of model.

- Maxtor 500GB DiamondMax22 9GT154-325


upchucky - I don't hear any beeps, I either get a frozen and blurred screen or a reboot out of the blue, usually the locked screen though.

Second edit:  I'm googling Motherboard jumpers now to avoid asking another stupid question! ;)

---

### Post by TomX19 on 2008-11-26
Only been an hour but early signs are good.  Have watched half an hour of audio visual online stream with no problems - CPU temp between 18 and 21 even with one of the cooling fans unplugged.  Am currently googling (is that a verb? it is now ;)) crashes caused by underpowered PSU.

Something I didn't mention graphics-wise is that I have a 22" monitor and am running 1680x1050 resolution.


Edit: PC just rebooted itself after about one hour.  Was only browsing forums with Firefox

---

### Post by TomX19 on 2008-11-27
I've run a Memtest in Memtest386+ since successfully reseating the cards, and it's come out ok:

Next time I crash I'll note the time and have a look at the syslog

---

### Post by Bucky Ball on 2008-11-27
Efficiency: >65%

Poor. The current standard (pretty much) is 85+ (and is actually called that) so this sounds like the silver box type generic PSU. I think they have gone for the cheap option as these are inexpensive in comparison with the well known (and trusted) brands. That could be the problem but really hard to know from a distance. FYI:

[http://www.overclockers.com.au/wiki/Power_Supply_Unit](http://www.overclockers.com.au/wiki/Power_Supply_Unit)

Disconnecting the cooling fan, incidentally, won't make much difference as it is *very* low powered and would not be (should not be) causing the problem.

---

### Post by TomX19 on 2008-11-27
Thanks for that, I noticed that low efficiency along with the fact that **maximum** power is 450, but **continuous** power is not quoted.  I think an upgrade is not a bad idea *anyway*. 

I've been looking at these:

Coolermaster RealPower 520W
[http://www.ebuyer.com/product/134696?ref=ga&gclid=CKj7oYqsk5cCFc0a3godFzNVJA](http://www.ebuyer.com/product/134696?ref=ga&gclid=CKj7oYqsk5cCFc0a3godFzNVJA)

or

Antec Neo HE 550 (UK)
[http://www.misco.co.uk/applications/SearchTools/item-details.asp?EdpNo=33081&CatId=41](http://www.misco.co.uk/applications/SearchTools/item-details.asp?EdpNo=33081&CatId=41)

---

### Post by TomX19 on 2008-11-27
Incidentally I had another crash at 16:13 (I noted the time on the toolbar) but the only thing in the syslog is this:

Nov 27 16:03:51 nlcutxd-desktop -- MARK --
Nov 27 16:14:20 nlcutxd-desktop syslogd 1.5.0#2ubuntu6: restart.

---

### Post by Bucky Ball on 2008-11-27
Excellent choices, both of them. Coolermaster also makes the GreenPower (GP - I have one in my desktop and extremely cool and quiet) and Antec makes the Earthwatts. They could also be worth the look. 

From your two posted PSUs, I would opt for the Antec simply for these reasons:

[LEFT]**Highly efficient (upto 85%) - **one super-silent 80mm fan keeps Neo HE cool; less than 18dBA noise level.

The Coolermaster is 80% or better. This might only mean a few cents saving in the short term but either of these is going to save you $ in the long term compared to what is in the box now.  Plus, *18dba* is extremely quiet.

Apart from overlooking the power supply anyhow, people overlook this fact too -  bit more expensive for a decent one but less energy used, save money, save the planet ... we all win! That is why the old ones get so hot - energy transfers to heat instead of powering the machine (in the case of your PSU, up to 40% of the power is being transferred to heat).

ps: the PSU may, of course, not be the problem!
 [/LEFT]

---

### Post by TomX19 on 2008-11-27
Thanks again :)  I've stuck the PSUs on my Amazon wishlist for now.  VAT in the UK is coming down from 17.5% to 15% in December so I'll wait before ordering and hopefully get a slightly better deal.

In the meantime, I might use the dreaded Vista a little and see if I can find stuff in the error logs for any crashes I get....

---

### Post by oldsoundguy on 2008-11-27
set Vista in classic mode, and, at least, you will be able to find your away around as all of the "help" stuff will miraculously appear where most of it used to be in XP.  I use that method when I set up a Vista computer for friends .. sometimes they prefer it be LEFT in classic and opt out on the memory wasting, totally useless, eye candy!

---

### Post by TomX19 on 2008-11-27
> **oldsoundguy said:**
> set Vista in classic mode, and, at least, you will be able to find your away around as all of the "help" stuff will miraculously appear where most of it used to be in XP.  I use that method when I set up a Vista computer for friends .. sometimes they prefer it be LEFT in classic and opt out on the memory wasting, totally useless, eye candy!

Absolutely I agree! :lolflag:

---

### Post by TomX19 on 2008-11-28
ALL the crashes in Vista have event ID 6008 (the reason there aren't many is because I don't use it much):

Error	28/11/2008 12:06:32	EventLog	6008	None
Error	23/11/2008 20:06:18	EventLog	6008	None
Error	22/11/2008 19:43:36	EventLog	6008	None

- <Event xmlns="http://schemas.microsoft.com/win/2004/08/events/event">
- <System>
  <Provider Name="EventLog" /> 
  <EventID Qualifiers="32768">6008</EventID> 
  <Level>2</Level> 
  <Task>0</Task> 
  <Keywords>0x80000000000000</Keywords> 
  <TimeCreated SystemTime="2008-11-28T12:06:32.000Z" /> 
  <EventRecordID>19633</EventRecordID> 
  <Channel>System</Channel> 
  <Computer>nlcutxd-PC</Computer> 
  <Security /> 
  </System>
- <EventData>
  <Data>12:05:37</Data> 
  <Data>28/11/2008</Data> 
  <Data /> 
  <Data /> 
  <Data>18</Data> 
  <Data /> 
  <Data /> 
  <Binary>D8070B0005001C000C00050025002502D8070B0005001C000C000500250025023C0000003C00000000000000000000000000000000000000010000002C090000</Binary> 
  </EventData>
  </Event>

The power management setting in Vista was set to maximum performance, i.e.,

Energy Savings: **
Performance:    *****

I have changed this to:
Energy Savings: *****
Performance:    **

Just to see what happens.  I wouldn't know how to do this in Ubuntu, if it's possible. (I had changed this from the standard ***/*** some time ago as I thought it might be responsible for the crashing.)

The crash above happened while using BBC iPlayer on their website (audio visual)

---

### Post by TomX19 on 2008-12-03
I found something on the Alphapower, it IS made by Kingwin and if this is anything to go by it is CHEAPO!!

£12.02 Inc VAT (British pounds)
[http://www.cocc.co.uk/itemcode=450WATXALP&sTitle=components&prodesc=450W~ATX~ALPHA~POWER~PSU~OEM.html](http://www.cocc.co.uk/itemcode=450WATXALP&sTitle=components&prodesc=450W~ATX~ALPHA~POWER~PSU~OEM.html)

I think that cements my decision to upgrade anyway

---

### Post by TomX19 on 2011-03-08
I know this thread is ancient, but as I forgot to give it closure and I just found it when I was looking at my threads, I'm going to update it anyway for the benefit of anyone who might stumble across it on a search.

New PSU made no difference (but no harm in replacing the cheapo one right?).

The problem was resolved completely by replacing the memory.

---

