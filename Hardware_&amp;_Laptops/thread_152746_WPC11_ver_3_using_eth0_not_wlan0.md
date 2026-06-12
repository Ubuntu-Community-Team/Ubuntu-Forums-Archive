---
title: "WPC11 ver 3 using eth0 not wlan0"
date: 2006-03-30
forum: Hardware &amp; Laptops
---

### Post by Yimmy on 2006-03-30
My linksys WPC11 ver 3 is working perfectly, except that it's working under eth0 and not wlan0.  This means I don't have the ability to scan for available networks other than the ones I already know exist.  At home and work, this is fine, but not out and about.  Is there anyway to make this card work as wlan0 instead?  I've searched and searched but haven't found any definitive answers.  Thanks in advance.

James

---

### Post by Yimmy on 2006-04-06
Either no one else considers this a problem, or no one's using this card.  Surely somebody else here has had this problem?  Not being able to scan for wireless networks is a pretty big issue.  Anybody got any ideas?

---

### Post by az on 2006-04-06
Er, the fact that the driver creates an eth0 device has nothing to do with the fact that you are not able to scan.  It's just a naming scheme.

My orinoco_cs pcmcia card uses an eth0 device and it can scan perfectly well.

What chipset is it?

---

### Post by Yimmy on 2006-04-06
According to the developers of wifi radar it is.  The card is a linksys WPC11 ver 3 pc card.  I get an error when I try to scan for networks from the terminal or any other wireless scanning application (such as wifi radar).  I'm not sure what driver it's using as I don't have the machine in front of me at the moment.  Any thoughts?  So you've got your card scanning even though it's showing up as eth0?  I was told that wasn't possible.

James

---

### Post by az on 2006-04-06
"The Linksys WPC11 ver.3 is an Intersil Prism3-based 802.11b PCMCIA card that works with the orinoco_cs drivers in the 2.4, 2.5 and 2.6 kernels. It supports 128bit multiple-key WEP encryption and is a good performer. "

Looks like we have the same kind of card.

Yes, I can scan.

---

### Post by Yimmy on 2006-04-06
Hmmm.  That's odd.  Wonder why mines not working.  Your's worked right after installing Ubuntu?  No modifications?  Dang, I need to look into what driver it's using.  I'm going to go check now and see what the deal is.  I'll write back in a few.

---

### Post by Yimmy on 2006-04-06
Let's start with basics.  What do you use to scan for wireless networks?  It appears my set up is correct.  Maybe I just didn't use the right tools.  Suggestions for what works best with the linksys wpc11 v3?

---

### Post by az on 2006-04-06
I click on the networking tool and in the wireless connection section, it shows me my essid without asking me to type it in.  It scanned to find out the name.

---

### Post by Yimmy on 2006-04-06
Huh.  That's interesting.  Mine puts "any" in there.  Of course I have to type in my hex code for my security, but it won't show me any other connections that are available when I'm out.  I guess it's "sort of" working.

---

### Post by Mega24 on 2006-11-29
I am also trying to get my WPC11 v3 card to work. I have Ubuntu (alternate version) 6.10 installed on a Dell Latitude CPi. The card shows up in the Network controls. I can enter ESSID, but I cant enter the entire 128 bit WEP key. I also tried switching my access point to use 64 bit WEP, but I still couldnt connect. I went to linksys site and d/l the Linux driver for the card, but it is in .tar.gz and I have no idea what to do. I tried extracting and doing 'make config' but it wanted location of my linux source files (default /etc/src/linux). Tried changing this to what I found in /etc/src/ but I got an error saying that my version is actually different than what is the files in the /etc/src/ directory are reporting. I am lost...I love Ubuntu, but I feel like an idiot here. HELP!

---

### Post by Permafrost91 on 2007-01-21
I use a WPC 11 version 3 (important! version 4 uses a different chipset) on an IBM Thinkpad X30. I have used this card successfully since Breezy (on Dapper and now on Edgy). It *should work right out of the box (at least in Dapper and Edgy, Breezy required a manual ndiswrapper installation).

For scanning and connecting to wireless networks, I suggest you use network-manager. It's a little tray icon that shows available networks and connects automatically to ones you've been on before. Works splendidly under Dapper and Edgy with this card. Just remember to disable the card in the GUI network settings to allow network-manager to configure the card.

---

