---
title: "Acer 1690 suspected hardware issue"
date: 2011-07-08
forum: Hardware
---

### Post by SD_Korf on 2011-07-08
Hi,

I've been trying to get to the bottom of a suspected hardware issue with an Acer Aspire 1691 WLMi. I have done stacks of searching, reading, trying but come up empty. I'm hoping that someone can suggest a next step. Here the challenge: the laptop (with WinXP) was in use basically for e-mail and internet only (older user, non-IT). One day it froze. It was going to be thrown away pending my diagnostic. I inherited it. I tried within Windows to disable all sorts of services, stop things loading, etc. Intermittent fault, so sometimes it looked like I'd nailed it, then it froze again. (It never froze in safe mode, though). Eventually I decided to try Ubuntu - compare operating systems and possibly determine once and for all if it was hardware or software. Well, initially Ubuntu ran fine (10.04). But, you guessed it, it, too, froze. Then I continued fault-finding under Ubuntu. Through a laborious process I learned about ACPI and DSDT. Unfortunately the custom DSDT patch has been discontinued so I couldn't explore that. (Well, I actually downloaded the source code, even managed to compile my own kernel, but never took the step of creating custom DSDT tables and recompiling.) Anyway, I found that if I run with ACPI=OFF the machine works. That's how I've been and am using it for now. However, it is just nagging at me to get to the bottom of this.

My main suspects are battery and wireless. I think the battery is shot and/or was never really working. However, running without the battery worked for two weeks in  Jan this year (without the ACPI parameter, in other words, full ACPI - no boot parameters at all except what 10.04 installed). So, I am no longer convinced it is the battery - but she is not off the suspect list yet.

Wireless isn't a clear culprit, either. (It's an Intel PRO/Wireless 2200BG [Calexico2]; driver IPW2200 ver 1.2.2kmprq.) When I start with ACPI=off, the kill switch doesn't work. The messages log shows that kill switch is off, needs to be on for wireless to work, but the system never recognises the switch toggle. (Strangely, because sometimes in the past - don't know which circumstances - I would get the key press shown in a log file, suggesting it needs to be mapped.) However, if I start the machine without the ACPI boot parameter and let it crash, then on the next start the kill switch is recognised and works perfectly. (That is my current work-around to use wireless.)

Now the puzzling thing is, that if the machine freezes (most frequent symptom when starting withouth acpi=off) then my only recourse is to power off (hold the power button 15 sec). In other word a cold start (ok, with possibly residual charge in capacitors and the like). But it does not seem to make sense that the kill switch recognition should be remembered. However, I am grateful for that. :)

So here the challenge and/or appeal: can anyone tell me how I can get closer to the detail of the kill switch? When does it get checked during boot? How is that check different with ACPI on and off? With ACPI=off, the op sys finds all my components, even the wireless: it gets listed, ipw driver is loaded only the network icon (to bar on right) shows it greyed out.

Oh, one more symptom that may be significant and that seems to have happen more often: sometimes on cold-cold start (i.e. the machine has been off for hours) when switching power on, the screen goes a milky white (like only the backlight is on) and doesn't get past its hardware initialisation. Well, it does eventually. I haven't timed it every time, but sometimes it's quick, sometimes it doesn't even happen, once I timed about 2 minutes. No key press works. It seems like it is standing there, waiting for some hardware init signal to be received.

BTW, I have dismantled the machine all the way. Even taken the screen apart. Didn't find anything obvious. Ensured all connectors and cables and modules are properly seated. Tried leaving wireless module and RAM modules (2 * 256MB - I know, it's little, but hey, a gift horse) out - no difference.

Heat, fan? Been there, nothing definite. BIOS - tried I don't know how many times but cannot re-flash. I'm only one version from latest - I think. But, on the other hand, it had been working well for 5 years or so and the user definitely would not have done any fancy things like BIOS flash. 

What I'd really like to try or find is a way of getting that kill switch to work without crashing/freezing the machine. I've tried echoing 1 or 0 to the rf_kill file - no difference. And I can't see why it should - I think we're talking hardware level here.

Is there a program that can query hardware registers of chips on these wireless cards? I mean, the BIOS POST and initialisation does that, doesn't it?

Sorry for the really long story, but I thought you should get all the detail of my months of investigating.

Anyone up for this challenge?

---

