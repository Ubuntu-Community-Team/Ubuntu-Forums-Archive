---
title: "I'm having a few problems with my computer, lend a minute?"
date: 2009-04-02
forum: Hardware
---

### Post by Oplix on 2009-04-02
My specs:
ASUS M2N32-SLI Deluxe
AMD Athlon 64 X2 Dual Core 4200+
EVGA GeForce 9800 GTX
CPU Fan - forget what make it was, it's working well though and has been for over a year
PC Power & Cooling SILENCER 500W Power Supply
2.00GB RAM

Ok, first it started with artifacts after long periods of gameplay. Eventually, games wouldn't even load. Dust insulated, and cooked my GPU. Fair enough, lesson learned there. Dust was also insulating and overheating my CPU, but luckily it was undamaged.

Dust was cleared out, graphics card was replaced, computer was checked out at a shop and seemed fine. Got it home, started screwing around on it, and again, artifacts in game after playing for some time.

Quit the game immediately and ran PC Probe and speedfan...

MB - 63C
GPU - 65C
CPU - 182C!?
CPU Fan - 2700rpm

PC Probe also gave 2 warnings regarding my voltage. +12.0 and I think +3.3, however seeing the 182C CPU, I shut down without thinking to write it all down.

Several minutes later I turned my computer on again, let it idle for awhile, and ran PC Probe and speedfan again. All temps in the 40C range, all voltage normal.

Shut down the computer, let things cool, opened it up, and started looking around to see if perhaps the guy at the shop hadn't cleared the dust he said he did, or if something was out of place/blocking airflow. Nothing. However, the adhesive between the fan and the CPU seemed melted and was doing nothing to hold the two together. I'll need to fix that...

So here's what I'm looking at...

I have no idea what's causing my CPU to read 182C after playing games for awhile. My fans are working, and I haven't had this problem before. 

Should I be very concerned about the voltage problem? I think the +12 was low, but I don't remember exact numbers. It's a new power supply.

What can be causing this, what is your suggested course of action?

For the purposes of fixing my computer I will be running XP. Thank you for your time and advice.

---

### Post by kpatz on 2009-04-02
That CPU probably would have cooked (or at least shutdown) long before reaching 182C, so I'm more likely to say whatever sensor utility you were using was giving inaccurate results.

63C motherboard temp seems high too.  Usually MB temps are only slightly over ambient.  Does the case have decent airflow?

I'd fire it up cold, put the sensor utility up, and maybe run Super PI or Toast to load the CPU and see how much the temperature changes over time.  Also feel the CPU heatsink, see if it's getting warm.  If the CPU is 182C the heatsink fan would probably be melting off, unless there is poor CPU-heatsink contact, something else to check.

Try the temperature readings in the BIOS as well (usually it's in a Hardware Monitor menu item), to see if they're different than the probe utility.

---

### Post by creative blank on 2009-04-02
I haven't encountered this problem yet, but here's a link that might help: [http://www.linuxjournal.com/content/adjust-fan-speed-you-nvida-graphics-card]("http://www.linuxjournal.com/content/adjust-fan-speed-you-nvida-graphics-card")

It's for installing a problem called nvclock, which is supposed to help with this sort of thing.  I know that if you type "sudo nvidia-settings" in a terminal, the settings display shows up and it will show your GPU and CPU temperatures.  However, I don't think it allows you to adjust fan speeds.

Also, make sure that everything is properly connected.  I can tell you from experience that nVidia cards are actually pretty good at maintaining a decent temperature within the computer, unlike my experience with ATI cards.  Hope the program helps, I can't boot into X at the moment so I can't really check it out myself.

---

### Post by Oplix on 2009-04-02
Air flow has never really been a problem for me with this computer. I mean I ran fine for over a year before running into any heat problems.

However my case fan is feeling a little ware. Every few seconds it makes a vibrating noise and the blades slow ever so slightly. It's not enough that I'd suspect it's really raising the internal temperature that much or limiting the air flow, but maybe I'm wrong *shrug*.

I believe, if memory serves, that my internal temp was in the low 50's right after the artifacts started appearing. Which is higher than normal...

My room temp was about 30C. 

But about those voltage issues? Could that be related to the temperature? Or is that a separate issue I need to worry about now?

I'll get the CPU and fan back together, get the case fan running like new again, run one of those CPU programs you suggested, and let you know how the results come back.

Thanks for helping.

---

### Post by cariboo on 2009-04-02
It looks like the OP is using Windows, as PC probe is not a Linux program. It almost looks like you got some bad sensors on the Motherboard. The sympthom you are describing does sound like a bad video card, that has thermal issues.

Jim

---

### Post by Oplix on 2009-04-02
Ok, I'm gonna accept my failure here and put on the dunce cap, but I was examining the CPU for any damage, and I went and dropped it (trying not to get the adhesive onto anything, and all), and it landed right onto my macbook trackpad... So here's hoping the magnet didn't go and screw it up...

It seems like there's 4 possible problems I may be facing here...

- Graphics card is overheating
- CPU is overheating
- Motherboard is overheating
- The case is overheating

and 3 possible causes

- defective graphics card
- poor air circulation (ie. malfunctioning fan)
- problem with the heat sink.

If my graphics card was the problem, I should be able to feel that through the exhaust, correct? Since the hot air would be blowing out. This however is not the case, and from what information I've been able to find on my card, the temperatures my GPU reaches under load really aren't above what websites are reporting as normal for this card.

What I do know... The adhesive on my CPU was melted pretty good, so it was definitely getting too hot for the adhesive to handle. Not sure how much that says though...

The back of the case also feels quite warm, I'd say on the border between being warm and hot. The air that my case fan blows out is also quite warm/hot. So, clues would suggest it's the internal case temperature. In other words, that fan I didn't think was that broken, probably wasn't doing as well as it looked.

Anyways, since I don't have a CPU fan on my CPU anymore, not much I'm gonna do with it today.

Hopefully someone here will know enough to reassure me that I haven't damaged the CPU at all by dropping it on the trackpad, but if I have, well, not much I can do about it now but feel like an idiot, learn my lesson, and set up a better work space for this stuff in the future.

---

### Post by norwoods on 2009-04-03
the 'glue' between the cpu and heatsink is not glue, it is a conductive thermal paste to help heat flow from the cpu to the heatsink.

---

### Post by kpatz on 2009-04-03
As long as you didn't bend any pins on the CPU it's probably ok.

When you said "he adhesive between the fan and the CPU seemed melted and was doing nothing to hold the two together.", are you saying the CPU heatsink was loose?  Depending on the sink's design it is either held on with clips that hook on to the sides of the socket or it's screwed down onto a bracket.  The "glue" you mention is thermal paste.

Go to a 'puter store or Best Buy or someplace and pick up some thermal paste (preferably Arctic Silver 5).

Put the CPU back in its socket but don't attach the heat sink yet.  Use some rubbing alcohol and a soft cloth to remove the old compound from the CPU and the bottom of the heat sink.  Then, apply a THIN coat of Arctic Silver to the CPU, and reattach the sink, making sure it's making good contact with the CPU (it might help to remove the motherboard from the case).  Reconnect the fan and power up with the case cover off.  Go into the BIOS settings, go to Hardware Monitor and watch the temperatures for a while.  Also make sure all the fans are working properly while you have the cover off.

Also, gently feel around the inside of the case to see what's getting hot in there.

As for your voltage issue, what voltages is PC Probe reporting?  Usually +/- 10 percent of rated voltage is ok.

---

