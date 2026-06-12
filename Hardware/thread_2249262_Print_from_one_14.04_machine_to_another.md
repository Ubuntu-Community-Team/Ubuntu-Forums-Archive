---
title: "Print from one 14.04 machine to another"
date: 2014-10-20
forum: Hardware
---

### Post by Mike_Walsh on 2014-10-20
Evening, all.

Admins; sorry if this is in the wrong place; please move if necessary. Also further apologies for starting multiple threads on the same subject... :oops:

I'm getting nowhere fast. :confused:

I've been trying to set up network printing between two Ubuntu 14.04 machines. One has the printer connected by USB, and has an Ethernet connection to the local network; this is a desktop PC. The other is dual-booting Win 7 and Ubuntu 14.04, and is connected to the LAN via wireless; it's a laptop.

I want to print from the laptop to the PC, which has been configured as a print server. I've given up on the Win7 install at the moment....it's a nightmare! I'm more concerned with getting the two 'buntu installs to recognise each other, so that I can share files as well as the printer.

I've installed SAMBA, and also the SAMBA front-end (the GUI configuration tool), and as far as I can tell, I have got this set up correctly; at least, everything tallies, and the system tells me it's all working.

I've got the localhost printer configured.....has been for months. When I configured the network printer which I've added, it appeared in the Printer Settings box on the client machine (the laptop), so as far as I can tell, the client is recognising the network printer connected to the host. I understand that sharing between two 'buntu installs is supposed to be easy; apparently just a case of ticking the 'Shared' option on the host machine, and 'Publish this machine to the Network', in the 'Server Settings' box. I'm beginning to wonder though; I've read many posts on this forum, and others, and they are unanimous in saying that this all worked perfectly in 12.04, but 14.04 seems to have gone haywire with regard to network sharing.....I can't dispute this one way OR the other, however, as 14.04 is the first 'buntu I've used. :)

Do I need to install SAMBA on BOTH machines.....and IF so, how do I configure the client? I guess most of you are more used to doing all this via the terminal, but having looked at the /etc/samba/smb.conf file, it looks horrendously complicated; I don't know if I'm quite ready for that!

Or should I not need SAMBA at all between two 'buntus? I don't quite know what I did, but when I first tried this, simply by ticking the appropriate boxes (as stated above), I DID actually get the client to print a test page from the host; but I've not been able to repeat this.....and I've tried SO many different combinations, I honestly forget how I had things set at the time...

Apologies for the length of this post, but I just wanted to 'state my case', as it were; I really have almost reached the 'hair tearing out' stage, I'm getting that frustrated with the whole business. Like as not, it will all turn out to hinge on something small and insignificant; that's usually the way. I've got rather good at getting things to work in Ubuntu.....but this one has got me stumped. ](*,)

Does anybody have any advice at all on this matter? 'Twould be MUCH appreciated!

Regards,

Mike.

---

### Post by deadflowr on 2014-10-20
From the gist I'm not sure if you did this,  
Go to Printers >> add printer > Network Printer >> Windows Printer Via Samba >> right panel:Smb Printer > Browse.
After you set it you should be prompted to add drivers, if memory serves me right.
Then you get to the test page; run or don't run a test page, up to you.
Then the properties page will appear and from there you can set whether or not you weant the prnter to be the default or not, and some other settings if you like.

And for the record you only need to install samba(samba server more precisely) on the machine with the printer physically attached.

---

### Post by Irihapeti on 2014-10-20
I've got a similar setup, but a different printer (I think) from yours: a HP Officejet 5610. I'm running 14.04.

First point: if you're trying to network one Ubuntu machine with another, you don't need Samba. I use CUPS (available from the repos) to handle the networking.

I had a housemate for a couple of months who had a Windows laptop. In that case, I did use Samba, but I had some difficulty getting it to work properly at first. (I succeeded in the end.) While doing my research, I found that some people recommend not using Samba at all, even for Windows clients and prefer to use CUPS instead. I can't remember the details now, but I probably can find them again.

Having said all that, I know that HP machines generally play very nicely with Linux. I'm not sure what kind of a difference it would make if you're using another brand.

---

### Post by WinEunuchs2Unix on 2014-10-20
Well to cheer you up... I just got a broken Brother printer from work that is a "Windows only" printer and I'll have to set that up with Windows Printer Server on the network using a backup laptop and fudge Ubuntu as a client on the primary laptop somehow :D

BTW it's only broken because it stops scanning on page 3 at 78% and the printer and copier work perfectly.  I figure it was just running out of memory in Windows somewhere and scanning isn't important (too busy writing junk to scan junk :P)

---

### Post by Mike_Walsh on 2014-10-21
Hi, everybody - thanks for the replies.

@deadflowr; I probably DID do that at some stage.....but I've tried so many different combinations, I forget whether or not I did. Appreciate the suggestion, though..!

@irihapeti; When you say about CUPS being available from the repos, I thought CUPS was the default print handling system used BY Ubuntu (or any other Linux distro, come to that)..? As I understand it, you only need to enter

> localhost:631

in your web browser, and the CUPS web interface opens up, and there's your installed printers, along with the same configuration & admin tools as you have when you open 'Printers' from the main 'Settings' menu....yes?

Unless I'm understanding CUPS completely wrong; the Epson has been printing reliably from the Compaq for months.....it was one of the first things I sorted out after the original install, back in late May.

The scanner part of the all-in-one took a little bit longer to figure out; but I now have the scanner & printer both configured and set up in every one of my 'buntu installs. HOWEVER; I've basically followed the advice (which ALL boils down to the same set of things to do) from many blogs & various different forums.....and I don't understand, yet, why it's not networking as it's supposed to. Here's just a few:-

[http://www.howtogeek.com/191323/how-to-share-printers-between-windows-mac-and-linux-pcs-on-a-network/](http://www.howtogeek.com/191323/how-to-share-printers-between-windows-mac-and-linux-pcs-on-a-network/)
[https://help.ubuntu.com/community/Samba/SambaClientGuide](https://help.ubuntu.com/community/Samba/SambaClientGuide)
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)
[http://ubuntuhandbook.org/index.php/2014/06/how-to-share-a-printer-in-ubuntu-14-04-trusty-lts/](http://ubuntuhandbook.org/index.php/2014/06/how-to-share-a-printer-in-ubuntu-14-04-trusty-lts/)
[http://askubuntu.com/questions/488191/how-to-get-network-to-see-14-04-desktop](http://askubuntu.com/questions/488191/how-to-get-network-to-see-14-04-desktop)

That's a small sample of what I've been looking at the last few days!

I've JUST had a thought; could it be anything to do with opening ports in the firewall, to allow communications back-and-forth between the different 'puters??

Regards,

Mike.

---

### Post by Irihapeti on 2014-10-21
Seems like you understand what CUPS is about. No problems there, that I can see.

Yes, port 631 needs to be open on the computer that the printer is connected to. If it's not, that would be causing problems.

---

### Post by Mike_Walsh on 2014-10-21
> **Irihapeti said:**
> Seems like you understand what CUPS is about. No problems there, that I can see.

Yes, port 631 needs to be open on the computer that the printer is connected to. If it's not, that would be causing problems.

Irihapeti, thanks for that.

I DID wonder about the firewall ports! As I said, it only just occurred to me this morning. I shall have to do a bit of research into setting open ports'n'stuff, since I'm still fairly new to Linux.....and I haven't really got my head round just quite what it is that iptables does, or even how it works, yet. :-k

So, let me get this straight; you're saying that ONLY the machine with the printer needs to have port 631 opened.....I don't need to configure it on the client machine, no?

Regards,

Mike.

BTW; I've got sort of half an idea as to how you do this, but my biggest stumbling block is probably syntax; i.e., entering things with the dots and dashes and commas and brackets and so on in exactly the right order!

Would you do me a HUGE favour, and have a look for that info about doing everything with CUPS, please? There's NO rush; whenever you get the chance.....it WOULD be appreciated. Thanks.

---

### Post by Irihapeti on 2014-10-21
The machine with the printer attached has to allow the laptop to connect at any time. That is, port 631 needs to be open. An easy way to test is to turn the firewall off completely (temporarily) and see if that makes any difference.

On the laptop, you're unlikely to run into problems with the firewall unless you've set up rules to block outgoing connections. In that case, you'd need to allow port 631.

Re printing with CUPS in Windows, I ended up not using it, because I was able to get Samba to work. Now that there's no Windows laptop at home, I can't test it, but I'll have a look around today for the reference.

---

### Post by Irihapeti on 2014-10-21
I think the answer to this question may help.

[http://superuser.com/questions/296718/printing-from-windows-to-ubuntu-shared-printerhttp://superuser.com/questions/296718/printing-from-windows-to-ubuntu-shared-printer](http://superuser.com/questions/296718/printing-from-windows-to-ubuntu-shared-printerhttp://superuser.com/questions/296718/printing-from-windows-to-ubuntu-shared-printer)

As I mentioned earlier, I've not tried this myself so can't confirm from personal experience.

---

### Post by Mike_Walsh on 2014-10-21
Many thanks, Irihapeti.

I'll have a look at that in the morning. Of course, you're about 11 hours ahead of us here in the UK; by my reckoning it's just after midday where you are (or just before!); here, it's 1 a.m in the morning, and I'm yawning my head off...

Bed is beckoning, I think. Will get back to you tomorrow, and let you know how it's going.

Thanks again.

Regards,

Mike. ;)

---

### Post by JKyleOKC on 2014-10-21
I'm printing from Xubuntu 14.04.1 to a 12.04.5 box; on this box (the 14.04 one) the URL to list printers is "http://xubuntu2:631/printers/" rather than "localhost:631" -- "xubuntu2" is the 12.04 box, connected via cat5. For the printer configuration on this box, I set it to "ipp://xubuntu2.local:631/printers/HP_LaserJet_1320_series" to connect to my HP-1320. Note the "ipp" prefix rather than http -- this identifies Internet Printing Protocol, which CUPS handles quite nicely. The ".local" after "xubuntu2" makes sure that its IP is found; I later modified configuration in the DNS area so that it gets added automatically when needed, which is why the URL I use with the browser doesn't need it...

Hope this helps. It took me several weeks of "err and err and err again, but less and less and less" (to quote Piet Heim's "Secret of Success") to discover how to make it work here...

---

### Post by Mike_Walsh on 2014-10-22
> **JKyleOKC said:**
> I'm printing from Xubuntu 14.04.1 to a 12.04.5 box; on this box (the 14.04 one) the URL to list printers is "http://xubuntu2:631/printers/" rather than "localhost:631" -- "xubuntu2" is the 12.04 box, connected via cat5. For the printer configuration on this box, I set it to "ipp://xubuntu2.local:631/printers/HP_LaserJet_1320_series" to connect to my HP-1320. Note the "ipp" prefix rather than http -- this identifies Internet Printing Protocol, which CUPS handles quite nicely. The ".local" after "xubuntu2" makes sure that its IP is found; I later modified configuration in the DNS area so that it gets added automatically when needed, which is why the URL I use with the browser doesn't need it...

Hope this helps. It took me several weeks of "err and err and err again, but less and less and less" (to quote Piet Heim's "Secret of Success") to discover how to make it work here...

Hallo there, Jim.

As you probably read further back when I was answering Irihapeti, I THINK my current problem is the firewall. I'm shortly going to disable it, and see if that will allow communications from the Dell (client) to the old Compaq (the host, with printer attached).

If that IS the problem, then I shall set a rule for port 631 incoming.

Like you, I too have been trying everything I can think of the last few days; then different combinations; & then variations on those again! I initially set mine to:-

'ipp://localhost:631/printers/EPSON-Epson-Stylus-SX218',

but then changed it to

'ipp://mic-w:631/printers/EPSON-Epson-Stylus-SX218'

where 'mic-w' is the host machine (the old Compaq). So; if I try your suggestion out, I would need to change that to:-

'ipp://mic-w.local:631/printers/EPSON-Epson-Stylus-SX218'.....is that correct?


Regards,

Mike.

---

### Post by Irihapeti on 2014-10-22
It depends on how your LAN DNS is set up.

You can test it by using the command

```
ping -c 5 mic-w
```

from the laptop and see if you get a response. If you do, use that in the printer address line. If not, try the host's LAN IP address instead.

---

### Post by Mike_Walsh on 2014-10-22
@Irihapeti & Jim Kyle;

SUCCESS.....Yes!!!

It was the firewall all along. Everything worked as soon as I disabled it; I fired off a test document from the Dell, and it printed straight off, sweet as a nut. So, I've set up rules for CUPS, AND for SAMBA (because I want to set up file sharing, too). And it still prints after I did that.

Now I've just got to set up printing from Windoze 7.....*arrgh!*

Many thanks for your help, guys. Appreciate it!

BTW; Jim... I noticed, upon disabling the firewall, and then the printer registering when I opened 'Settings>Printers' on the Dell, that it had in fact set itself up automatically with the '.local' appendage. Thanks for the tip, though; it's yet another one to add to my steadily growing collection of tips, tweaks, and workarounds..!

Will mark this as 'Solved', since the question as posed HAS been answered. Thanks again, both of you.


Regards,

Mike. :)

---

### Post by JKyleOKC on 2014-10-22
I've not tried with Win7 but you may be pleasantly surprised to find that searching for network printers automagically finds it, once you have Samba Server set up on the box with the printer. That's how it's SUPPOSED to work, but things don't always work as intended...

---

### Post by Mike_Walsh on 2014-10-22
TELL me about it...

I used XP for its entire lifetime; I liked it, alright, but for the last 2-3 years I was constantly needing to re-install it; something or other was ALWAYS going wrong. It was quite a revelation when I tried Ubuntu for the first time. I tried it on a Live-CD for a couple of days, intending to dual-boot it; it didn't take me long to realise that I'd found what I was looking for, and so I took the plunge.....bye-bye, Microsoft. I had nothing that I actually needed Windows FOR; so I had no qualms about waving goodbye to MS.....boy, I'd grown to HATE that registry..!

Well, I hope to have Samba up-and-running properly within the next few days. I've gotten RATHER good at making things work in Ubuntu... ;)

And there's this, too; I really like the Ubuntu forums; folk don't look down their nose at you like they do on the MS forums, if you're not running the latest, most up-to-date system!

Regards,

Mike.

---

