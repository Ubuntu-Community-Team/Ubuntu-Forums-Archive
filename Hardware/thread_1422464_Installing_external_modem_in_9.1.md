---
title: "Installing external modem in 9.1"
date: 2010-03-05
forum: Hardware
---

### Post by caribconsult on 2010-03-05
I have 9.1 Ubuntu on a desktop and it appears to be working OK. It has not frozen yet.  I've even installed Crossover Office and I have Outlook running on it. Quicken is next.

But here's the problem: I also have a real USRobotics Sportster 56K Data/Fax external modem, connected to COM1 on the computer, but Ubuntu does not recognize it, and I can not find anything in the system administration to add a modem, either by detection or manually. I also can't find anything in any of the help pages, or here on Ubuntu Forums...the results I find all have to do with PCI winmodems, which is not my situation.

Can someone please give me some **explicit** instructions on (A) anything that needs to be downloaded, and (B) just **exactly** how do you install this modem in **this version** of Ubuntu?  

It's not a USB or Winmodem...it's a real hardware external and it works well under Windows.  I don't want to use it to connect to internet...I have a LAN here and Ubuntu connects just fine...I want to use this modem strictly for sending faxes.

Thanks to any who respond.  I don't mean to digitally 'shout' with the boldface; I just want to be clear about what I have and what I need.

You can also email me at [email]jeff@tcconsult.net[/email]

---

### Post by IcarusR on 2010-03-05
Modem should not need to be 'installed' but just work using the kernel serial driver.

I believe you need efax & the gui efax-gtk, both in the repos.

Or use efax & Open Office 
[http://www.eskimo.com/~meik/linux/configuringsoftware.html#efax]("http://www.eskimo.com/~meik/linux/configuringsoftware.html#efax")

---

### Post by lyall on 2010-03-07
Why would you want to send Faxes?
When you can just attach the file in an e-mail
Also sent files as PDFs not is data files, legal reasons.
When you sent a fax it will cost you a long distance change if you send it out of your local calling area, E-mail do not.  

also Faxes are slow, sent in bits not Kbits.

good luck and have fun learning

---

### Post by caribconsult on 2010-03-07
There are many reasons to send faxes, which I don't want to get into here, but suffice it to say I have my reasons.

Now, getting back to the issue at hand: I have installed EFax GTK, the Java interface and all other required packages.  What I can't find is the 'fax printer' that allows you to fax out of any program by printing to the fax printer.  Where is this? I would think it would get installed automatically when you install the program but I can't find it anywhere.

The EFax program finds my modem at ttyS0, and I will say it is clunky, compared to what's available for windows, but without the fax printer, it's really a challenge to put together a multipage fax.

Can someone tell me where this fax printer is hiding, or what I have to do here?

Thanks.

---

### Post by sybille on 2010-03-10
Try the following instructions:
> • Go to System -> Administration -> Printing
• In the Printer configuration dialog, click on the upper left-hand icon OR on Server -> New -> Printer. There will be a popup that says "Searching for printers."
• When that's finished, you should see the "New Printer" dialog. Although it may identify your serial modem there, do not choose that.

• Instead, select network printer, AppSocket/HP JetDirect
• Type "localhost" in the Host box.
• Set the port to 9900.
• Click Forward.

• In the next dialog, select "Generic."
• Click Forward.

• In this dialog, choose "Raw Queue."
• Click Forward.

• Now type in a name such as "Fax" or "eFax" for the Name, replacing "printer". Fill in the other optional fields if you like.
• Click Apply, the close the Printer configuration.

• Go to Applications -> Office -> efax-gtk.
• Select 'Socket' as the fax entry method, then close eFax, which will minimize it to your tray/notification area.

That's it. Now, when you go to print a file in any application, you should be able to choose the name of the fax printer you entered above. When you select "Print," an efax-gtk popup should appear asking you to enter the telephone number of the recipient. You can send then or queue for later. Or, if efax-gtk is not already running, you should see an error in the printing status icon; if you then start efax-gtk, the printer should spool to it and eventually the popup will appear.

What this procedure does is tell your application to send the document you'd like to print using a Unix socket to efax-gtk, in raw postscript format, at which point efax-gtk takes over and sends the fax. More about Unix sockets: [http://en.wikipedia.org/wiki/Unix_socket](http://en.wikipedia.org/wiki/Unix_socket)

From:
[http://www.dslreports.com/forum/r23918177-](http://www.dslreports.com/forum/r23918177-)
and
[http://ubuntuforums.org/showpost.php?p=2027377&postcount=2](http://ubuntuforums.org/showpost.php?p=2027377&postcount=2)

---

### Post by caribconsult on 2010-03-10
TO SYBILLE:  thank you very much for your extremely specific instructions about creating the EFax printer.  I followed your notes and they worked perfectly

Why this is not done automatically on installation of the Efax program totally escapes me.  This is, I think, symptomatic of the Ubuntu world in general...too much is left to the user instead of happening as part of the installation routine.  I know windows has its faults, but one of them is not incomplete installation of programs.

---

### Post by sybille on 2010-03-10
Here's a link you might find useful for thinking about the GNU/Linux experience. Please read:
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by caribconsult on 2010-03-10
I did read the post you suggested, and I have to agree with much of it...I'm expecting too much from Linux.  If this were 15-20 years ago, while I was active as a consultant, I might have had more patience with it and dug a bit deeper, but I'm spoiled in certain sense in two aspects: I'm a Windows XP user, and I'm used to programs that completely install themselves, and I'm also an engineer, and I expect more complete products, but I guess that's the beauty of Linux...they leave lots of stuff undone so the tinkers have something to do. I just downloaded a copy of Moneydance and it took me nearly an hour to figure out how to install it and then get it on menu, and I really think I just stumbled across the right procedure because I was on the verge of just trashing it at one point.  That's just a bit much for me.

At this point in my life I'm just a guy who uses computers and not really interested in learning a new language and a raft of new procedures just to be able to handle my email and finances.  And I also am worn out by some of the sarcastic criticism from 'the experts' on another forum which shall remain nameless, who like to ridicule the fact that I'm experiencing a somewhat steep learning curve here and questioning some of the engineering.  But thank YOU very much.

---

### Post by IcarusR on 2010-03-10
15 - 20 years ago you would have liked linux even less !! It is good now compared to then !!

---

### Post by sybille on 2010-03-10
> **caribconsult said:**
> ...I'm experiencing a somewhat steep learning curve here...

I think that's the key. It is hard at the beginning, especially for those who have expertise in other operating systems.

But the more you experience and learn, the easier things will go. And eventually, once some of the "culture shock" wears off, you might even find the learning experience enjoyable.

That's if you decide to stick with it, and of course you're free to chose otherwise. :)

---

