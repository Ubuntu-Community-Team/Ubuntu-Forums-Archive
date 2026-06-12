---
title: "Epson XP-211 Printer - WiFi fails to work"
date: 2015-01-15
forum: Hardware
---

### Post by Tacuabe on 2015-01-15
Hello there!

I've just bought an Epson XP-211 printer, downloaded the drivers from the Epson official page and my printer is working when connected with cable via USB port.

However, I'm unable to print wireless. I'm using Lubuntu 14.04 with LXDE.

When using System Tools/Printers and trying to locate a Wireless Printer I get up to a point and then the systems seems to enter an endless loop. Cancelling the operation clears the loop but further intents repeat the behavior and refuse to continue.

I am attaching four screen captures that show the steps I went through. Capture_002 shows the printer is indeed located and also shows the SMB Browser output. Capture_003 is the error I get when using the Verify... key. Capture_004 shows a different error I'm getting now when using that same key.

Click image for larger version. 

Name:	Capture_001.png 
Views:	0 
Size:	40.9 KB 
ID:	259273Click image for larger version. 

Name:	Capture_002.png 
Views:	0 
Size:	127.7 KB 
ID:	259274Click image for larger version. 

Name:	Capture_003.png 
Views:	0 
Size:	61.1 KB 
ID:	259275Click image for larger version. 

Name:	Capture_004.png 
Views:	0 
Size:	66.1 KB 
ID:	259276

The Epson manual (found in the Web) is much more explicit than the Quick Setup enclosed in the box. However, there are some obscure points:

a) To activate WiFi one has to press the corresponding key for 3 seconds. The manual does not say what is supposed to happen. Actually two lights, one green the other orange blink alternatively for several minutes. After some time the orange light goes steady and the green light is off. Pressing the WiFi key clears (turns off light) and you can press the button again for 3 secs...

b) The printer must be connected via USB until detected by the system as wireless. Then a message will request to remove the cable. I suppose this refers to the Windows and OSX software included in the CD. Linux is not mentioned anywhere and I've never seen the message.

c) Scanning does not work via cable. Tried with Simple Scan and XSane to no avail. Anyhow, I suppose this is a different issue which must be attacked after WiFi is working.

Any help will be much appreciated.

Thank you guys!

P.S. I've also posted this in another thread. Since it was marked as SOLVED I decided to start anew just in case.

---

### Post by Tacuabe on 2015-01-15
Am attaching the images again as they are not appearing in the above text.

[ATTACH=CONFIG]259280[/ATTACH][ATTACH=CONFIG]259279[/ATTACH][ATTACH=CONFIG]259278[/ATTACH][ATTACH=CONFIG]259277[/ATTACH]

---

### Post by Mike_Walsh on 2015-01-15
Hello, Tacuabe.

If you go to the other thread about the XP-211, I've outlined the steps you'll need to take, in order to get your scanner 'up-and-running'.

Regards,

Mike. ;)

---

### Post by Tacuabe on 2015-02-15
Mike Walsh provided directions regarding the Epson XP-211 drivers and the printer now works flawlessly when connected via USB cable. Scanning also works OK. However, I'm stuck with network printing which, to date, has not been possible.

Pdc offered some suggestions on this last issue but in the end it was impossible to find how to provide the necessary data to the printer. The problem here is that the XP-211 does NOT have a display, therefore the information must be supplied by other means.

Additionally, my Internet provider does NOT allow WPS to be activated. Therefore, this becomes an additional hurdle on the wireless printing issue.

Can anybody help here?  Thanks!

---

### Post by Pilot6 on 2015-02-16
Did you install Epson network plugin? If yes, you need to edit /etc/sane.d/epkowa.conf

And write there ip address of your printer like

net 192.168.1.234

---

### Post by Tacuabe on 2015-02-20
Hello Pilot6!

Thank you for writing. 

I have a few questions regarding your comments and help:

a) I just installed the Epson drivers following directions supplied by Mike_Walsh. Don't know if those include the network plugin.

b) Looking into /etc/sane.d I do find epkowa.conf. Does that mean the network plugin is installed? Where and how do I look for it?

c) If the network plugin is not installed, where should I go to download it?

d) I printed an Epson Status Sheet but the ip address is not there. How do I find this data?

I'm sorry to ask that many questions but this is the first time in 8 years using Lubuntu that I'm faced with an issue of this kind.

Thanks for your time, patience and help.

---

### Post by Tacuabe on 2015-02-27
Hello again Pilot6!

Don't know if you've seen my post of 6 days ago.

Can you provide answers for my questions?

Sorry to insist but I'd like to get everything working properly asap.

Thanks

---

### Post by Tacuabe on 2015-03-04
I have been waiting for help with this issue, specifically to an answer to the questions I posed a week ago. 

Pilot6 did supply some directions but I am a at a loss to complete his suggestion unless somebody provides further help.

Hope to hear from somebody soon.

Thanks

---

### Post by Mike_Walsh on 2015-03-05
Hallo, Tacaube.

I've just been doing a bit of research into this, and I confess, I COULD do with a bit of clarification here.

You're talking about network printing, yes? By which I take it you mean that your printer OUGHT to be able to work WITHOUT being connected by a physical cable, right? And I'm guessing here that the USB port is there as a 'fallback' device, in case the wireless connection doesn't work?

Or, ARE you talking 'network printing' in the sense of being able to have multiple machines **all **using the same printer?

It's this network plug-in that's throwing me out, you see. It **appears** to be only provided as part of the scanner package.....NOT the printing side of things. THAT'S what confusing me. Network printing on your local area network (LAN) is very easy to set up in Ubuntu, and its derivatives. But I don't think that's what you're referring to.....is it?

Sorry if I'm covering 'old ground' again, but it's a couple of weeks or so since I was last here..!

I think (and I'm not convinced I'm right on this at all) that the network address that's being mentioned in /etc/sane.d/epokwa.conf is your network address on the LAN. This is easy enough to find; I **have** used Lubuntu before, but not for a little while. 

(I'm in 'Puppy' at the moment, but /etc/sane.d/epokwa.conf is here, too, as Xsane is installed by default.....and epokwa.conf is pretty much a standard script in Linux.) 

Clicking on your network icon (can't remember if it's left- or right-click; Lubuntu splits the Ubuntu network menu into two halves!) will bring up your connection info.....and it's usually the number starting '192.168.....'. That **should **be the network entry that's wanted in epokwa.conf. As to the port number, I need to do a bit more research on that one.

Bear with me. We'll get you sorted out ONE way or another.


Regards,

Mike. :)

---

### Post by Tacuabe on 2015-03-05
Hello Mike

You're allways ready to help! Thanks a lot! Will try to supply answers and clarify the issue as much as I can for you.

To your first question the answer is YES. I bought a wireless printer to get rid of cables as much as possible. My former one was an HP D110 which worked fine until it had a hardware problem too expensive to repair.

The second question gets a NO. It could be useful but is not really important.

This, of course, also answers the third question. I'm not referring to printer over the LAN.

I first heard of a 'network plug-in' from Pilot6 post. I really don't know if it's installed or not. It may be part of the package you suggested, which I indeed installed and had me up and running, albeit via USB cable only. Don't know if the presence of epkowa.conf is indicating that the plug-in is installed.

I use Wicd instead of Network Manager and the the IP here is 192.168.1.102. However, I believe this IP is just used for the Internet connection and I think the printer address may be similar (but not the same). I've no clue about the port number.

As I said before, the main thing here is that the XP-211 has no display and therefore data cannot be entered directly. It would appear that, if Pilot6 is right, that editing epkowa.conf might be the way to go. If we find out what must be entered there...

Thanks again and kind regards,

Hector

---

### Post by Mike_Walsh on 2015-03-05
Hallo again, Hector.

Okay; that's fair enough. That's cleared things up a wee bit. 

As far as this 'network plug-in' goes, I'll confess.....I'm not too clear on what it actually does. I've never bothered with a wireless printer; my big old Compaq desktop sits in my bedroom, with printer attached. It's always up-and-running; I have networking set up with my old Dell laptop, so if I want to work anywhere else in the house, I just use that and connect through the router to the Compaq. I can access all my drives, print stuff.....do everything as though the laptop WAS the main machine. And since they're both running the same O/S, it cuts down on possible cross-contamination from different config, files, etc...!

As to the IP address; as I understand it, the address that everybody tends to be aware of for their machines IS the LAN address. Yes, it IS used for connecting to the internet, but it then connects via the firewall, etc. in your router, and via something called a submask (!) Don't ask me what it is; that's about the extent of my knowledge as far as networking goes. When it boils down to it, the internet is also a 'network'; just a much bigger one.  After the 'submask', I believe it's then resolved via the local DHCP server, which assigns you a different, random address every time you connect.....but YOU retain the same, local, 'fixed' address so that YOU know what the hell you're doing.....!

With regard to the 'epokwa.conf' file, it's a bog-standard part of every /etc/sane.d directory that's ever been installed, whatever the O/S in question. If you have Xsane installed, THAT directory will be somewhere in /etc. It will be there, regardless of whether you have the 'network-plugin' installed, or not. Don't, however, ask me how exactly how you check to see whether it's installed or not; my knowledge of the terminal is quite limited at the moment.....I'm slowly picking it up as I go along. Some stuff you can't help but learn, anyway; 'cos you're ALWAYS using it, one way or another. It'll be handy when I do pick a bit more up, since it's a much more direct way of communicating with the system, and telling it what it is you want it to do.

I'll show you what I mean with the network settings & stuff; I'll post back in the next hour or two; I have to go out for a little while. Bear with me for a bit, and we'll see if we can figure out what needs to be entered in the 'epokwa.conf' file. I don't guarantee that will fix it, but it's got to be worth a shot.


Regards,

Mike. ;)

---

### Post by Tacuabe on 2015-03-14
Hello Mike,

Thanks for the lengthy reply and data. Have I missed your post? You said you would write again in an hour and it's been a week since, with no news. Just wondering...

Kind regards,

Hector

---

### Post by Mike_Walsh on 2015-03-16
Hallo again, Hector.

Sorry it's been a while. Busy week last week; I was going to reply the same night, got sidetracked at the last moment, and it slipped my mind; I'm sure you know how it is..!

Now, then; I've had to re-read the thread, to remind myself of where we were. IP addresses, and stuff; yes. I'm in Puppy Linux at the moment, but the networking info panel in Puppy illustrates the points I wanted to make somewhat better than Ubuntu's does.....it gives you more information.

Have a look at the panel below:-

[ATTACH=CONFIG]260668[/ATTACH]

If you look on the line starting with eth0, at the end of the line you've got a hardware address. It's a unique code that identifies every individual piece of computer hardware that's ever been produced. It's always the same layout; six groups of two digits in hexadecimal format, separated by colons. Your printer will have one of these. Now, if I have my facts right (and I'm not at all certain about this), you've got to put that into the 'epokwa.conf' file, along with a couple of other bits of information.

If you look on the line below, you'll see '192.168.1.67'. That's my local area network IP address. If you've got more than one machine on a local network, you'll sometimes find that the router will swap IP addresses around among the machines; this is normal, but it confuses matters somewhat! This is why I have mine set to 'static' addresses, rather than 'dynamically allocated' ones; just means that each machine keeps the same address permanently. Simplifies matters. THIS is the one you'll need to add into the 'epokwa.conf' file.

If you then look on the line above the one starting 'eth0', you'll see '86.129.149.38'. Now,** &#8203;this **is the one I was telling you about that changes all the time. That's only with me for this session; this changes EVERY time you log on. This is the IP address that the DHCP server randomly allocates you for your current connection......it's not the one YOU need, but I wanted to illustrate the point. The one you need is your LAN address; it'll invariably start with '192', and then more often than not '168'. I don't understand the rules behind all this; I've researched it on the web, and came away more confused than I was before I'd started!

But; most people don't need to understand the mechanics behind it.

I'm doing a bit of research into the 'epokwa' file, so bear with me. Am I right in thinking you were originally trying to connect using SAMBA? The screenshots you showed at the start of the thread would seem to suggest so. Do I have it right, that you want to** print **wirelessly? Because as far as I can make it out, the 'epokwa' file is specifically for using the scanner. Can you confirm that for me, one way or the other? Because I rather think we're approaching this from completely the wrong angle.....


Regards,

Mike. :)

---

### Post by Tacuabe on 2015-03-16
Hello Mike,

Thanks for replying and for a most complete explanation.

As far as I know, my IP address is 192.168.1.102 (this is what Wicd is showing when connected to my provider). I also suppose this is my LAN address. What I cannot find is the Hardware address for my printer. Don't how or where to look for it.

Those screen captures appeared when I tried to add the printer. Never knew these were supposed to come from SAMBA.

And again, YES I want to print wirelessly.

Hope this helps. Please take your time to answer. Meanwhile the printer is working fine if connected via USB cable.

Regards,

Hector

---

### Post by Mike_Walsh on 2015-03-17
Hallo, Hector.

Right! That's fair enough; I had a feeling we were approaching this from the wrong angle. It may be a day or two before I get back to you; I need to do some more research on this myself, anyway. I've been thinking that sooner or later I may be replacing the SX 218 with a wireless printer; it will, of course, BE an Epson.....though model specifics are still for the future at present. 

That being the case, I need to 'bone up' on the basics. I'm one of those people who, for ANY project, likes to get all necessary information together BEFORE I implement. Just my way of doing things; but it does work, as it usually means there's fewer nasty surprises in store when it comes to the moment of truth!

I may appear to have a slightly different approach to many of the forum regulars; I don't tend to ask for lots of command-line info. I CAN use it myself (I go all the way back to the days of DOS...and THEN some), but being from the 'newer' generation of Linux users, I'm also aware that that the simpler you can keep stuff, the easier it is for new users to absorb it.....and if that means keeping it GUI-based wherever possible, then so be it.

Please be patient, and as soon as I've found out what I need to know, I'll post back, and we'll see where it leads us.

BTW: I don't think those windows were 'supposed to come from SAMBA', as you put it; I think you'll find that the SAMBA option just happens to be the first in the list (it's a little while since I had a Lubuntu install, and I forget exactly how everything looks); but of course, if you don't know any different, you're not looking for it. It's a mistake that's easily made by anybody new to CUPS & the Linux way of doing things. Nothing to worry about; it's easily remedied.


Regards,

Mike. :)

---

### Post by Tacuabe on 2015-03-17
Hello Mike,

Will look forward to your post. I'm quite comfortable with command-line if need be. Feel free to suggest whatever you find that may work.

Thanks again for your continued interest in helping.

Kind regards

Hector

---

### Post by Tacuabe on 2015-04-21
Hello Mike!

I have not visited this forum for some time. It appears my post of March 17th is the last one. Any news from your side on this issue?

Kind regards

Hector

---

### Post by danielandrews7396 on 2015-05-02
Hi there Tacuabe!

Just seen this thread and thought I'd jump in as I've just had a very similar issue myself, using an XP-215. I've managed to solve my problem and wondered if I could
be of an help, if yours is still ongoing? This is my first time posting as I'm rather new to Linux, but I'd be happy to assist if needed.

Regards,

Danny

---

### Post by Tacuabe on 2015-05-03
Hi Danny!

Thanks for the offer! Most welcome, certainly. My XP-211 is working fine if I use an USB cable, no dice with the Wi-Fi. Please post whatever your solution was, it might work for me too. 

Never mind you being a newbie. I've been using Linux (Lubuntu) for eight years now and still get stuck sometimes with issues like this one with the Epson printer.

Best regards

Hector

---

### Post by Tacuabe on 2015-08-03
I've been visiting this thread for the last months and nobody appears to have come with a solution to my quest. Any takings out there?

Thanks in advance!

Hector

---

