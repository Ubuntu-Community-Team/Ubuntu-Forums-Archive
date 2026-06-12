---
title: "can't...make...work.....* pounds fist*"
date: 2008-11-23
forum: General Help
---

### Post by VicTome on 2008-11-23
okay so i asked one question yesterday about running a windows based software on my 8.04, i have yet to get a response.  so i have continued to search and explorer and think my number one issue is that i do not have internet access on the machine as of yet, currently i am on a XP laptop with a wireless network connection.  i want to set up the same kind of connection my ubuntu machine, but using my fiancees HTC ppc6800 as the connection point ( internet sharing) i have now confirmed that USB ports do in fact work, at first i thought they did not.  i was told a few weeks ago by a guy on a website that i needed nothing to install a windows based software on ubuntu, but i have come the conclusion I do.  i have tried several programs and every time i can view the files, but when i click on the autoruns, it comes up and ask it i want to run the program, or jsut display it.  the options are as follows : run in terminal, display, cancel, or run.
i have tried all of them adn nothing ever happens except when i click run in terminal, it flashes a terminal screen up and then disappears.  i have come to the conclusion that i need wine....no the spirits, but the install.  i have checked winehq and become confused.  i need to be able to download to a flash drive and then transfer to my other machine.  i am sure i can do this, but i have not figured out just what i need to do it.  the command line is still eluding me also, so if i have to do any command prompts i will need step by steps.  i am a self taught computer builder who has till now only ever used windows.  i want to switch because i have a new found interest in programing and am too cheap to buy a new copy of xp or a new machine.  from the reviews i have read, ubuntu will do everything i want it too, i just have to learn how to make it do it.  and the first thing i need to do is get this sucker online.  i also have use of a Huawei air card model EC228 from alltel.  but this requires installing the alltel access program so i am back in the same place.  if i could find a Linux friendly driver for the HTC PPC6800 i could just go that route, but i can't even find a windows driver online, i have the disk for the phone, but again, windows based and i can't get it to do anything.

---

### Post by oaxacamatt1 on 2008-11-23
Hi Victome,
It seems like you got a lot on your plate, hmmm.  As for loading or running Windows aps on your machine, *you are Correct, sir*. You need a program like WINE or CrossOver.  Wine you should be able to get thru your 'Add/Remove' installer.  But a word of advice, first.  Go to the WINE section of the Ubuntu website forum or even the WINE website and look up your ap.  In other words make sure that your Windows ap will run 'nicely' on WINE.  For example, Word2000 does not work on WINE period.  CrossOver is another prog that 'emulates' windows on Linux.  This software is generally not free but sometimes you can get gratis...  Obvisouly you will have install that first then...  But of course remember to see if you software will work under CrossOver.

For the rest of the stuff.  Be the consumate scientist, in other words, DO ONE THING AT A TIME.  Don't throw three or four things together or else you will never see what effects one change has over another.

Hope this Helps,
MAtt

---

### Post by VicTome on 2008-11-23
a new question stuck me as i read your replay, and your right one thing at a time, so internet access is first. and i guess i just need to go look, but all i really need is the driver for the HTC PPC6800.  and also, if i don;t have internet, i don;t think i can get wine from the add/remove, can i???? thats where the flash drive install come into play.

---

### Post by jimmy the saint on 2008-11-23
As far as tethering your device to your laptop and using it as a modem, you can check out this article and see if it will work for you.
[http://www.sysadminsjourney.com/2008/09/06/set-it-and-forget-it-tether-your-windows-mobile-6-phone-to-linux](http://www.sysadminsjourney.com/2008/09/06/set-it-and-forget-it-tether-your-windows-mobile-6-phone-to-linux)

As far as windows apps, slow down.  For nearly anything you need there will be an Ubuntu (linux) app to do the job.  You can install apps through applications>add/remove.  The problem with trying to isntall Windows apps as a beginner is that you are trying to do it to make your transition easier.  Unfortunately, you will likely find that you need to partake in more advanced troubleshooting and setup in order to make it work at all, thus defeating the point.  

Once you are comfortable working in your new desktop environment and have explored some linux apps, got everything working and researched a little, then try to make some windows apps work.  I would recommend using a virtual machine like VirtuaBox because you will actually be running a windows session and will have less bugs to worry about.

---

### Post by VicTome on 2008-11-23
the laptop is not really part of the situation here, it;s just the only machine that internet.   maybe i am no being straight forward with my problem.


need ubuntu desktop to connect to HTC PPC6800 to share internet.
need driver for phone to allow connection.
have driver disk, but need to run windows app. to obtain it.
ubuntu desktop has NO internet at all, so introduction of new apps has to be done via flash drive. ( if possible)  

i may jsut have to wait to get the cable interent hooked up here, i dunno.

---

### Post by Mr_JMM on 2008-11-23
Have you tried using any of the Ubuntu built in applications for connecting the HTC device? You shouldn't need to worry about any other drivers.

For example, my Sony Ericsson W910i connect no problem. I can download everything (messages, contacts etc,) and it automatically detected the modem function creating a new network connection.

Have a look through the synaptic packages and / or add/remove under Applications for Wammu.

---

### Post by VicTome on 2008-11-23
i will have a look, thank you, i plugged the phone in once and it didn't see it, but maybe i have to go into the app.

---

### Post by VicTome on 2008-11-23
nothing, i looked through the whole list in both the add/remove and synaptic package and found nothing for wammu

---

### Post by jimmy the saint on 2008-11-23
you need to make sure that ALL AVAILABLE APPLICATIONS is selected in the dropdown box, not supported applications

---

### Post by Mr_JMM on 2008-11-23
That's odd. Did you try putting Wammu in the search filter?

If it makes a didffenece to find Wammu, I have selected Multiverse and Restricted in the Software sources list.

Another program that might work (although I've not tried it) is gMobileMedia.

---

### Post by VicTome on 2008-11-23
sweet, found it cool.....buuuuuut, i don;t havea internet connection....needs one to continue...is there away around it, i am goign to do a search for it online with this computer

---

### Post by VicTome on 2008-11-23
got on the web site, Wammu does not support any HTC, but i think this is what i need
got some other options i will look into

---

### Post by Mr_JMM on 2008-11-23
Ok.

I'm afraid I can't think of anything else you haven't already tried.

Do let me know how you get on though. My wife has a HTC Diamond that I'd love to be able to use with Ubuntu.

---

### Post by VicTome on 2008-11-23
i am getting ready to try gmobilemedia it doesn't have a list and has only been tested on nokias, but hell it's worth a shot.  but is there no way for me to load wine with out a interent connection to the machine???

---

### Post by VicTome on 2008-11-23
aww pisser, they both rely on python-gammu, and that is where the support come into play, damn it.  okay, so yeah the wine question.

---

### Post by Mr_JMM on 2008-11-23
I never managed to get anything working in WINE.

As a last resort you can use something like VirtualBox (but NOT the OSE version as it doesn't support USB connections which you need).

I'm getting a litle closer. I found this:

[http://www.synce.org/moin/SynceWithUbuntu]("http://www.synce.org/moin/SynceWithUbuntu")

Go straight to the bit about openSync.

Still not sorted much out but it's a start and I thought we could both work on it and se where we get (I'm using the Wife's HTC Diamond).

---

### Post by VicTome on 2008-11-23
cool man, nice to know i got a friend with the same issue, i prolly won;t be back on the issue till this next weekend, with thanksgiving and all, let me know what you find.

---

### Post by VicTome on 2008-12-01
so yeah.  gonna be a while before i get back on this hoss. my daughter was born on black Friday 15 weeks early.  so we are going to be away from home for a few months.  i will get back to you when i can.

---

