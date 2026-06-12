---
title: "Help me configure my Lexmark Z1420"
date: 2008-07-07
forum: Hardware
---

### Post by KingNeil on 2008-07-07
I just upgraded from Vista to Ubuntu 8.04. I need help installing my Lexmark Z1420. Now, this is a wireless printer, and it can be detected wirelessly, so detecting it is no problem.

It's really actually getting the thing to print something which is troubling. It gives it by default a text-only driver, but even that doesn't seem to work. I've tried some of the generic ones, and they also don't seem to work.

Can someone help me?

---

### Post by adam_kimber on 2008-07-07
Hi. There are several things that are of annoyance in Linux and one is printing. Its come on leaps and bounds though and will continue to get better. Currently though according to the [openprinting database]("http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z1420") your printer has no Linux drivers. 

There are a couple of other people here who don't seem to have got anywhere. :( 

[http://ubuntuforums.org/showthread.php?t=763853]("http://ubuntuforums.org/showthread.php?t=763853")

However. My first choice would be to hard plug it in and see if Ubuntu likes it then.

---

### Post by KingNeil on 2008-07-07
No, this really doesn't seem to be working. I don't know what the hell I'm going to do. The whole thing is almost useless if I don't have a working printer. I really don't want to have to go back to Vista. I love the peace of mind of not having to check for viruses.

---

### Post by tijmz on 2008-07-08
I had the exact same problem and messed around with it for ages, but to no avail. Lexmark printers are notorious (even on Windows and OS X they require their huge software package to be installed) and unless someone very crafty is going to reverse engineer the software required to make it happen or  -and this is even less likely - Lexmark makes an effort to have all their printers support Linux, you're plain out of luck. 

I know how frustrating it is, especially if you can't just buy another, compatible printer. For a while I dual-booted Windows just to print :(

---

### Post by KingNeil on 2008-07-08
Yeah, that's really annoying. Linux will absolutely never be ready for the mainstream until you can plug and play a printer.

And it's really weird, because even though I'm no expert programmer, I don't see how hard it would be to make some kind of standard for all printers. Surely the data can just be sent from the computer and then the driver is installed only on the printer.

---

### Post by dogscoff on 2008-07-08
> **KingNeil said:**
> Yeah, that's really annoying. Linux will absolutely never be ready for the mainstream until you can plug and play a printer.

You can plug and play a printer on Linux. Just not that printer =-/

> And it's really weird, because even though I'm no expert programmer, I don't see how hard it would be to make some kind of standard for all printers. Surely the data can just be sent from the computer and then the driver is installed only on the printer.

There are plenty of standards, and linux supports them. The problem is wise-**** manufacturers refusing to comply with those standards for whatever stupid reason. 

To the original poster:

Aside from getting a sensible printer, the only help I can suggest is to pick up an old second hand PC from somewhere (an old Win98-era laptop would be ideal- cheap and not too power hungry, you can add wifi via the PCMCIA slot for not much money) install Windows on it and use it as a dedicated print server. Stick a software firewall on it (zonealarm or similar- free), lock down absolutely everything except what it needs to act as a print server, and you shouldn't have to worry about anti-virus/updates/windows maintenance.

Networking it to your linux box and getting it to share the printer *should* be fairly simple, although that's by no means my area of expertise. Doubtless someone on this forum could assist further.

---

### Post by KingNeil on 2008-07-08
Well, I do have quite a lot of other printers in my house. I'll see if any of them work.

---

### Post by xevous on 2008-08-28
Hey, I have the same printer and I tried going to my browser and typing in [http://localhost:631](http://localhost:631) and using the cups way to install the z1420. I did not use the z600 driver (it does not work and my printer is wireless).

After this I used my printers ip to set it up (using ipp - hopefully).

using these settings below:

Description: test_z1420
Location: [http://192.168.1.xxx](http://192.168.1.xxx)
Printer Driver: Lexmark Z51 Foomatic/lx5000 (recommended)
Device URI: socket://192.168.1.xxx

Now with this driver, it will spool the page - but not print. Methinks that this paperweight may have some use yet. Also a little footnote - if there is a way to strip the newest mac drivers...it is named 1400_Series_Web_Installer_**LPD**.dmg 

(The **LPD** is what is interesting) this may be an alternative...but this is a little above my level.

Any thoughts?

---

### Post by Crafty Kisses on 2008-08-28
Lexmark doesn't really do Linux support, sometimes they do, but check out these links.

[http://www.linuxfoundation.org/en/OpenPrinting/Database/SuggestedPrinters](http://www.linuxfoundation.org/en/OpenPrinting/Database/SuggestedPrinters)
[http://www.linuxfoundation.org/en/OpenPrinting/Database/LinuxSupportByPrinterVendors](http://www.linuxfoundation.org/en/OpenPrinting/Database/LinuxSupportByPrinterVendors)

---

### Post by xevous on 2008-08-28
> **Codename said:**
> Lexmark doesn't really do Linux support, sometimes they do, but check out these links.

[http://www.linuxfoundation.org/en/OpenPrinting/Database/SuggestedPrinters](http://www.linuxfoundation.org/en/OpenPrinting/Database/SuggestedPrinters)
[http://www.linuxfoundation.org/en/OpenPrinting/Database/LinuxSupportByPrinterVendors](http://www.linuxfoundation.org/en/OpenPrinting/Database/LinuxSupportByPrinterVendors)

Yeah, well as everyone has stated - no support for linux there... I'm just too stubborn to give up yet, I guess. Thanks. 

Anyone else? Or is this just a dead end with no hope?

---

### Post by rocksplit on 2008-11-17
there has to be a way to make it work with UBUNTU! come on

---

### Post by mike909 on 2009-01-28
Also, has anyone noticed you can FTP into it? You can send files to it via ftp...would be a nice workaround if it would just print what you ftp to it...not likely, but see below:
```

230 User modtime logged in.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ?
Commands may be abbreviated.  Commands are:

!		debug		mdir		qc		send
$		dir		mget		sendport	site
account		disconnect	mkdir		put		size
append		exit		mls		pwd		status
ascii		form		mode		quit		struct
bell		get		modtime		quote		system
binary		glob		mput		recv		sunique
bye		hash		newer		reget		tenex
case		help		nmap		rstatus		tick
cd		idle		nlist		rhelp		trace
cdup		image		ntrans		rename		type
chmod		lcd		open		reset		user
close		ls		prompt		restart		umask
cr		macdef		passive		rmdir		verbose
delete		mdelete		proxy		runique		?


```

---

### Post by MentalOxide on 2009-04-06
So... I've just bought a Lexmark z1420 and I don't have the cash and I can't buy another. I run Ubuntu 7.10. The last post was 9 months ago, has anything changed in regard to this? Is there any hope that my printer will work in the near future, or have I just thrown my money away.

---

### Post by mike909 on 2009-04-06
My post was 4 months ago, and...well...I believe we are all screwed on this one. Doesn't seem possible, just no drivers. I even tried sharing it from an XP box as a generic printer...no joy.

---

### Post by MentalOxide on 2009-04-07
Oh yeah... 4 months... don't know how I came up with the 9months figure.. bad maths I guess. So today, I tried to return my printer, but the shop wouldn't take it back because the cartridges were opened, albiet unused. Soooooo angry! Hopefully I can sell it on to a Windows user. To solve the problem I hit up my credit card and bought an Epson Stylus office t33. Brought it home, and three hour later... and 4 different install guides, and it sill isn't working. Printers and Ubuntu.... oil and water. I thought Ubuntu was really close to being a serious mainstream contender until I ran into this printer wall. Unbelievable. Are the linux overlords working hard on this?

---

### Post by mike909 on 2009-04-07
Honestly, Ive had a lot of luck with hp printers, and if you want to be sure it will work, head over to [http://linuxprinting.org](http://linuxprinting.org).
It's a resource dedicated only to printing from Linux.

---

### Post by Nikos.Alexandris on 2009-09-25
> **KingNeil said:**
> ...installing my Lexmark Z1420

FYI, an official reply from Lexmarks' Support Team:

[b]Dear Nikos,

Thank you for contacting Lexmark Email Support Team. We are working to assist you and address your email as soon as possible.  We apologize for any inconvenience; if immediate support is needed please visit our website at: [http://support.lexmark.com](http://support.lexmark.com) to review other Lexmark Support options.

I understand you are having difficulties on installing your Lexmark printer X1420 and making it to work with your current operating system. However, I regret to inform you that this printer model is not compatible with Linux Ubuntu. Printers that are compatible with Linux are Z2300 and X2600 only and drivers can be downloaded at [www.lexmark.com](www.lexmark.com). I apologize that I cannot send you driver for Linux but rest assured that our Product Engineers are still working on developing other printer drivers that would be compatible with Linux OS. 

If you have any more questions or concerns, please contact me at your convenience and I will be happy to assist you. (If I am not available, another representative may reply to your request.)or contact our Technical Phone Support at 1-800-LEXMARK(539 6275) for assistance. We’re open Mon - Fri: 8 am - 11 pm; Sat & Sun: 11 am - 8 pm, Eastern Standard Time. Please take note of your reference # for this communication: 1-2311238871.

To respond, please select "Reply" in your e-mail software, and be sure that the past e-mail is included in this reply.

[AOL Users: In order to include the previous e-mail, you must highlight it with your mouse when you are replying.]

If your e-mail client automatically deletes prior e-mail thread information, it will cause a delay while we look up your support history. If this is the case you may want to save the old e-mails as attachments and attach them to the current e-mail.

Sincerely,
Evangeline
Lexmark eSupport Team
[http://support.lexmark.com](http://support.lexmark.com)[/b]


**********Original Message**********
Dear Support Team,

I am an Ubuntu-Linux (9.04) user and I want to use the Lexmark z1420 printer. Unfortunately, I can't find anywhere the proper driver (a "linux" version, binary or open source, of the driver for the printer). Is there any chance to release a "linux" driver for this model?

Thank you in advane, Nikos

---

### Post by dasajed on 2010-01-24
> [AOL Users: In order to include the previous e-mail, you must highlight it with your mouse when you are replying.]

How many linux AOL users are there?

---

### Post by patrickvdbemt on 2012-03-14
same problem currently on Ubuntu 11.11 32-bit

Lexmark Z1420 does not seem to be able to attach to ubuntu

frustrating ! it can't be so difficult for multinationals like Lexmark to write drivers for Linux as they do for Micro$ and Apple$ ! I am sure there is the issue. these companies do NOT like the users to migrate to free OS, sure about that !
Easy for them to say 'just buy another printer' rather than fixing/writing their drivers for users and really become appreciated by the growing open source community.

---

