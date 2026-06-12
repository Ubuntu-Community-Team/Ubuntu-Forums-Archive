---
title: "Linux on a hp ipaq"
date: 2008-04-21
forum: Hardware &amp; Laptops
---

### Post by aquavitae on 2008-04-21
I've  got a friend who wants to install linux on his hp ipaq hx4700.  I've hunted around on the internet and found two sites: [http://familiar.handhelds.org]("http://familiar.handhelds.org") and [http://www.angstrom-distribution.org/]("http://www.angstrom-distribution.org/").  There also seems to be two popular guis: [http://opie.handhelds.org/cgi-bin/moin.cgi/]("http://opie.handhelds.org/cgi-bin/moin.cgi/") and  [http://gpe.handhelds.org/]("http://gpe.handhelds.org/")
Has anyone used any of these, or something else?  Know anything about the pros and cons?

---

### Post by oldsoundguy on 2008-04-21
I attempted to install Familiar on one of my PDA's (a 4155) to no avail as the flash utility failed to work.  This is a great idea, but support for the system is "part time to spotty" and the forums get no answers for WEEKS.

Just be apprised, that if you DO attempt flash the iPaq and it fails, you are the proud possessor of a shiny brick!  SOME iPaq units can be re-flashed back to Windows, and HP will accept the newer models (the current ones) and flash them back to CE, but they disown the older ones. EVEN THOUGH they are paying lip service to the conversion on their site!

This is the single most important reason that I still have ONE computer in my place that is Windows!  I need to be able to use my PDA's, since I have GPS and Wi-Fi on both of them.
(I did install Opera vs IE! and I installed dotPocket to be able to rotate the screens.)

---

### Post by aquavitae on 2008-04-23
Thanks for the reply.

From what I've seen it looks like familiar is quite old and unmaintained, but angstrom is more up to date so it might be ok... And there are full instructions of how to do it for my model, but I hear your point.

Any idea how well a linux PDA would talk to a PC (linux or windows)?  My friend has winXP on his laptop at the moment, although I'm trying to talk him into ubuntu.

I don' know much about flash technology - if I do a dd backup of the ipaq would I be able to restore it if the installation goes wrong? The windows installation on it is messed up as only windows can get - somes stuff works, other stuff doesn't and there's no logical reason for any of it!

---

### Post by oldsoundguy on 2008-04-23
only Palm has true Linux support.  The need has not arisen to make the effort to get Linux on to a hand held since, in the US, LAPTOPS rule.  (Not so in the UK or Japan, but that is another story.)

Sync programs for Ubuntu DO exist in the system .. the issue is not the desktop/controller software, but the hand held software.  I left my units running CE (2003) and have a Windows XP box set up to to the sync activities.

The first thing you have to do with an iPaq is remove the batteries, let it discharge, put the batteries back in, recharge and then RE-LOAD your programs.  Wi-Fi will be your biggest issue .. go bare bones and do NOT get fancy with any set up.  Only then will it work.  Blue tooth .. if being used for a GPS, should be initially set up OUTSIDE with your receiver so all possible satellites can be located.  Replace the IE with Opera (it is not free) and you will be able to browse with a real browser, not some crippled piece of junk!

---

### Post by aquavitae on 2008-04-24
Thanks for the help.

Not sure I entirely understand what you're suggesting - are you saying I should put windows back on it, with better software (i.e. Opera), or do you think its worth trying linux. Bearing in mind that he might put linux on his laptop. I don't think he uses it for GPS, possible only because he doesn't know he can though... but more as a PIM. Basically somthing he can use to check emails, track appointments, occasionally work on some documents and use the internet, connecting wither through wi-fi or bluetooth to cell-phone.

---

### Post by oldsoundguy on 2008-04-24
Just remember, the procedures for installing Linux on a PDA will REMOVE the Windows system including the Windows bootloader .. it is NOT dual booting software programs.  So you will lose all of the Windows program. In actuality you BURN the program into a chip similar to the CMOS chip on a regular computer. With the current state of the Linux programs for the PDA, there is an element of risk in doing that .. as, unlike a desktop or laptop, you cannot just "reload" the system and TERMINAL or a package manager to FIX issues is NOT THERE. You have to RE-Burn using the recovery you generated prior to burning .. IF that works .. again, at present, a crap shoot!

There IS another choice now that 8.04 has come out .. that of running Hardy within Windows on the host computer, thus having sync capabilities in Windows.  He really should NOT change the PDA over unless he is prepared to pay the consequences if it goes south. PDA/Linux is at the point where Linux was a few years back .. a couple of steps above an experiment from what I see.  (too bad, but that IS the way it is .. considering it is a free system and people work on it "when they can.")
Familiar WAS a project at one time .. not sure just what happened.
The last time the Angstrom home page was updated was 2006.

Really, IF you want Linux on a PDA and Linux on your desk and want either to talk to each other .. get a Palm and be safe. Then sell the iPaq on eBay.

---

### Post by aquavitae on 2008-04-25
Ok, thanks for the advice. I think I'll suggest he reloads windows then - or gets HP to do so, and install opera, etc. Will hardy sync with the ipaq, or is windows required?  I remember a couple of years ago getting a different pda to talk to linux (I think it was gentoo) but I can't remember the details.

---

### Post by oldsoundguy on 2008-04-25
have not a clue if Hardy will talk to a Windows CE PDA via Wine .. but it COULD.  Might be worth a try as you won't KILL anything. 

I have a Windows machine that I use for sync with my PDA units and I run Windows CE versions on them.  The only major changes to the on board PDA system was the addition of dotPocket as a screen control and additional loading system (which I have not used YET) and the substitution of Opera 8.6 for that really badly crippled Internet Explorer. Opera will function on HTML sites, whereas Pocket IE will NOT a lot of the time and you have to surf using WEP and then you get text only on the sites!

I do NOT use the PDA's in a Wi-Fi situation for anything critical or financial .. such as sending eMail or on line transactions simply because most free Wi-Fi sites have NO security or encryption.

But, using the HP Blue Tooth GPS receiver and their software, they do receive a workout in that area.

---

### Post by solitaire on 2008-04-30
Hey guys

I've got an old Ipaq 3860 that i'll probably never use (under the "1 year in drawer rule")

So I've decided to bite the bullit and stick OPIE on it.

*note*

The "1 year in drawer" rule states:
"...any device, gizmo, thingemajig or electrical hardware placed in a drawer or cupboard for at least 365 days without being touched, is now open for customisation or nonstandard upgrade (if aplicable). Else it's heading for the bin.."

---

### Post by tdeverell on 2008-05-06
I was able to accomplish Opie on my HP3900 series.  Yes, I had to remove the Win CE bootloader, but the Linux bootloader will boot both Linux or Win CE.  After a week or so of screwing around with Opie, I decided to go back to Win CE, simply because it has more apps than Opie has for handhelds.

If you do Virtualbox, it passes the USB signal thru, and I do all my Syncing there.

My big question is...  Has anyone got Android or any other Distro to work
with iPAQ?  Damn it would be swell to have Ubuntu on a Pocket PC!

---

