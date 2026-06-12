---
title: "Compaq Evo N410c page up"
date: 2005-08-30
forum: Hardware &amp; Laptops
---

### Post by David Gerard on 2005-08-30
I've started a page on putting Ubuntu on the Compaq Evo N410c:

     [http://thingy.apana.org.au/~fun/n410c/](http://thingy.apana.org.au/~fun/n410c/)

It's a combination of N410c-specific stuff, Ubuntu-general stuff and pontification :-)

I've also been putting a pile of friends onto Ubuntu and using their experiences.

Anyone else with N410c tips is most welcomed to help!

---

### Post by Mimsy on 2006-08-26
Hi forum!

I will hopefully get my hands on a Compaq N410c some time soon, and I am considering trying Ubuntu on it. I've been reading the forums and articles onthis site, to get an idea of what I'm getting into, and I was delighted to come across the page linked to in the post above. I was considerably less delighted to find the page apparently has been taken down. :-(

Does anyone know where that page is now, or if there is a similar one out there somewhere?

Thanks,
Mimsy

EDIT:
I just realised this is an old version of Ubuntu. I found the post through a forum search, and didn't pay attention to which specific forum it was in. Sorry about that. But if there is a similar page for Daper Drake, I'd still love to know where it is. :)

---

### Post by David Gerard on 2006-08-26
Yeah, that page was mine. Unfortunately thingy.apana.org.au doesn't exist any more! I really should put it back up on davidgerard.co.uk, which is my own site ... mind you that's having problems too (our box just got haxx0r3d) so that won't happen immediately.

Quick guide: Dapper just works. If you don't have the Compaq W200 wifi, just get a PC card wifi that works properly and save the pain!

And put in as absolutely much memory as you can afford (I think it goes up to 2x512MB), but that applies to any PC.

Problems:

1. Suspend and Hibernate *mostly* work, but I suspect the wifi driver.

2. The W200 wifi (the one in the lid) is supported by a source-only driver you have to compile yourself. There's a page on the Ubuntu wiki about this, which I've added a pile of bitter experience to. (In short: you spend a lot of time hitting Fn-F2.) The trouble is that the Orinoco driver is considered so crappy even by its developers that you have to get the code from CVS if you insist on running this thing ;-)

3. My N410c occasionally powers itself off abruptly from overheating. Again, I suspect the wifi driver's tentacles getting into the ACPI settings, 'cos when it powers off it's usually been quite quiet but when I switch it back on the fan is going full blast.

Honestly, I should just sell the W200 wifi and dissect a USB wifi adapter that works well with Linux and put it into the lid myself ... but that would require effort.

---

### Post by Mimsy on 2006-08-26
Thanks for the quick reply! I'll try Dapper and see what happens. Out of curiosity, would I get an accurate idea of what problems it will have by runnig it off the live CD or do I have to actually install it?

Thanks,
Mimsy

---

### Post by David Gerard on 2006-08-26
I'm not sure! I got to Dapper on this box by doing a dist-upgrade from Breezy some time in February and keeping it updated since.

In my experience, though, stuff works better from an installation than from the live CD.

You will definitely want to install tpconfig, which is a config tool for the Synaptics touchpad.

The modem is a Lucent LT winmodem; I understand that the Linux drivers for this are pretty good, but I have no use for a modem so I've never used this at all. (I probably should just for hack value.)

The volume control buttons on the front seem to Just Work, at least in GNOME.

Problems:

* You can't attach or detach the base while the machine is running and have stuff Just Work as it does in Windows. You basically have to shut down, attach or detach then start the machine. This is annoying enough that I never use the base at all now and wish I had a PC-card CD-ROM drive for ripping CDs with. (I use Exact Audio Copy running under Wine - works perfectly. cdparanoia still works well and isn't bad at all.)

* I haven't found how to adjust screen brightness.

* I have no idea how to control the four buttons above the keyboard - they're not part of the keyboard as far as X is concerned.

* The W200 wifi is all but unsupported in Linux. Its only advantage is that it fits nicely in the lid. You have to be a bit bloody-minded to insist on using it. I strongly recommend just getting a PC card known to work with Linux.

The Google cache has the pages [here for Breezy]("http://216.239.59.104/search?q=cache:OUVJNfyBtnUJ:thingy.apana.org.au/~fun/n410c/+n410c+ubuntu&hl=en&ct=clnk&cd=1&client=mozilla") and [here for Hoary]("http://216.239.59.104/search?q=cache:TZC2Wo_XSjcJ:thingy.apana.org.au/~fun/n410c/hoary.html+n410c+ubuntu&hl=en&ct=clnk&cd=2&client=mozilla"). Most of it is me rambling about Ubuntu setup in general, much of which is obsolete and you should take no notice at all. This is another reason I should do a rewrite before putting them back on my own site.

---

### Post by Mimsy on 2006-08-26
Thanks again! I'll bookmark the thread for when I get my hand on the EvoN410c - assuming I ever do. :-)

/Mimsy

---

### Post by Mimsy on 2006-08-27
Well, good things and bad things happening...

Good thing is: I'll get a Compaq EvoN410c for free. Yay.

Bad thing is: I _have_ to have wifi access, and I am on a very limited budget right now. So if I can't get Ubuntu or any other version of Linux to recognise the W200 wifi, then I'll have to stick with That Other Operating System after all... Darnit! And I was so excited about a chance to play with something new. :-| 

/Mimsy

---

### Post by David Gerard on 2006-08-27
The "good" news is - the W200 was an optional extra, and most N410c's don't have it installed, so you'll *have* to use a cheap wifi PC card that'll probably be much better supported under Linux ;-)

---

### Post by Mimsy on 2006-08-27
Define "cheap"? When I said I'm on a *very* tight budget I was not exaggerating... can I get away with less than $20?

The fact that this laptop is free and has the W200 are the two best things about it, as far as my wallet is concerned, since I need both, but would prefer not to auction off my kidneys any time soon. If I can find a wifi card that Ubuntu supports that I can afford, I'll be very happy though. Where could I find a list of supported ones?

---

### Post by David Gerard on 2006-08-27
Oh really, yours has the W200 included? Lucky! You could probably sell it and just use a card that works ;-p

(Having suffered with it most of this year, I am *so* not a fan. But anyway.)

Um, most wifi chipsets are supported in Linux. Just about anything Atheros is supported by MadWifi, for example. which is in the kernel. A cheap 802.11b card, for example, would do up to 11mbps (same speed as the W200), and most people would consider it so obsolete they'd give it away if they had an 11g card instead (54mbps).

Ones like the Orinoco chipset in the W200 not being supported are the exception these days. Which also left me cursing slightly, and thanking the developers of the Orinoco driver for bothering with the horrible thing.

---

### Post by David Gerard on 2006-08-27
[https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200](https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200)

That's the page on getting your W200 to work. You'll need either Ethernet or a separate wifi card to get the driver onto the laptop. The procedure isn't quite as scary as it may look there ...

---

### Post by Mimsy on 2006-08-27
Another page being bookmarked... I'm building an Ubuntu link library. Go me! :) 

Thanks for taking the time to answer all my questions. I really appreciate it. 

/Mimsy

---

### Post by Mimsy on 2006-08-30
Um, a little help again? Please?

I followed that guide very carefully, I copy-pasted every command into the terminal and so on, and I was doing pretty well, right up until I came to the part with downloading Windows firmware and activating the adapter. After I pasted in

cd firmware
  ./get_ezusb_fw

and hit Enter, I got this back:

chili@chili-laptop:~$   cd firmware
bash: cd: firmware: No such file or directory
chili@chili-laptop:~$   ./get_ezusb_fw
bash: ./get_ezusb_fw: No such file or directory
chili@chili-laptop:~$

I'm not sure what that means, or where to go from here. A long-time Windows user, my first instinct is to reboot and start over. Would that even work?

/Mimsy

EDIT: 
I decided to move this to the Absoltue Beginners forum, partl becuase I'm an absolute beginner, and partly so more people can see it. I hoping I'll get more help that way...

---

### Post by Mimsy on 2006-09-01
Never mind, it works now. :)

---

### Post by sawjew on 2006-09-02
I use a Compaq EVO N400C, which is pretty similar to the N410C I think with Xubuntu Dapper.  I don't have the built in wireless, I use a PCMCIA card which works beautifully, better than it does in Windows 2000 on the same computer.  Almost everything just worked when I installed but I only had 128M of ram so I used the alternate cd not the graphical install.  It worked quite well with 128M but it works really well now with 384M under Xubuntu.

I don't know how much memory you have but Xubuntu is significantly lighter on this computer although it doesn't have quite as many graphical configuration tools.

I managed to get the extra 4 keys working using keytouch ([http://keytouch.sourceforge.net/]("http://keytouch.sourceforge.net/")). I created a template for the N400C, it may be on the site by now.  If there is no suitable template it is really easy to create one with the keytouch editor and you can configure the keys to do anything you like.

let me know if there is anything else you want to know.

---

### Post by David Gerard on 2006-09-05
That could be just the thing! The N400c and N410c are similar enough that they share a repair manual.

I should put that page back up, but really it should go on the wiki. Is this sort of page suitable for the wiki? i.e., not the usual laptop-testing template but a page of "install this, try this", etc. If so, what sort of title should it have?

---

### Post by canardo on 2006-09-12
Another n410c here I got the wireless working with a belkin pc card and works a treat apart from when I suspend you have to reboot

A few little things I havent got fully working is
* the graphics driver anyone have any tips?
* the secondary keys such as screen brightness, not even sure what the ones with the battery etc on them do, since I have only ever run ubuntu on this laptop

---

### Post by canardo on 2006-09-12
please delete sorry double posted

---

### Post by sawjew on 2006-09-13
I got the graphics driver working properly on my N400C using this howto [http://ubuntuforums.org/showthread.php?t=7200&highlight=ati+display+driver]("http://ubuntuforums.org/showthread.php?t=7200&highlight=ati+display+driver")

I am not sure if the N410C uses the same graphics card but this works fine on my N400C.

as far as the other buttons go;
[LIST]
[*]The screen brightness - I am not sure how to get this working, if anyone has any ideas I would love to know also.
[*]The other buttons - In Windows 2000 the F7 button brings up the Power Management utility and the F8 button brings up the current battery status
[/LIST]

I have not been able to get any of the alternate functions on buttons F2, F5, F6, F7, F8 or F10 to work.  I have not even been able to get the system to react at all to the Fn button yet it does seem to work on all the other functions apart from those I have just mentioned.

If anyone has any ideas how to get these buttons to be recognised I would love to get them working also.

---

### Post by Mimsy on 2006-09-13
Fn-F2 works on the N410c without hassle, at least on mine it did. I haven't really tried the other ones yet.

/Mimsy

---

