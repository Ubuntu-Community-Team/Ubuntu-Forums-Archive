---
title: "Printing woes....Or rather lack of printing"
date: 2015-11-01
forum: Hardware
---

### Post by nevets68 on 2015-11-01
Hello all - 

I'm running ubuntu 15.04 on a Asus laptop. Everything seems to be working (well the fn brightness didn't but i ended up using - indicator brightness and all is good.) Now my next project is :

Installing a printer.

The setup is as follows -  wireless router - Asus RT-N66U. The printer - Brother HL-2140.   I've added the printer via system settings / printer/ LPD/LPR / added the ip address and attempted to print out a test page. 

When I check the printer status in ubuntu , it says - Held. I've released it but it reverts back to the same thing. I then see a message in the print status window that the printer "may not be connected." Keep in mind i have no issues printing from windows ( from my other laptop or desktop.)

---

### Post by SeijiSensei on 2015-11-01
Let me suggest another method.  First remove the printer you have already installed via SystemSettings.  Next open a browser and point it to the URL [http://localhost:631/](http://localhost:631/).  You'll get the CUPS interface.  Choose Administration > Add Printer.  Enter your username and password when prompted.  Do you see the printer in the list of Discovered Network Printers?  If so, select it, and if there are multiple entries for the printer, just choose the top one.  You should now be able to step through the rest of installation.  When you get to the final page, pick Maintenance > Print Test Page.  Does that work?

---

### Post by Bucky Ball on 2015-11-01
Did you install the [driver]("http://support.brother.com/g/b/downloadlist.aspx?c=au&lang=en&prod=hl2140_all&os=128") for it first? Download the Driver Install Tool or the two .debs then go to 'Printers' and delete whatever printer you've added> add a printer using 'Printers' or the CUPS interface as suggested by Seijisensei> now the correct driver for it will be there.

---

### Post by nevets68 on 2015-11-02
Thanks for the replies. I've tried both options and neither of them worked.

---

### Post by Cope57 on 2015-11-02
You could possibly retrieve the driver from the [Brother website]("http://support.brother.com/g/b/downloadtop.aspx?c=us&lang=en&prod=hl2140_all") itself.
Try the [COLOR="#DE4C19"][Driver Install Tool]("http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=hl2140_all&os=128&dlid=dlf006893_000&flang=4&type3=625")[/COLOR], or the [COLOR="#DE4C19"][LPR printer driver (deb package)]("http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=hl2140_all&os=128&dlid=dlf005857_000&flang=4&type3=559")[/COLOR].  If you still do not have the printer working, try the [COLOR="#DE4C19"][CUPSwrapper printer driver (deb package)]("http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=hl2140_all&os=128&dlid=dlf005859_000&flang=4&type3=561")[/COLOR].  If none of the .debs work for you, try and compile the driver from source using the [COLOR="#DE4C19"][CUPS wrapper Printer driver Source Codes]("http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=hl2140_all&os=128&dlid=dlf006677_000&flang=4&type3=576")[/COLOR].

Hopefully one of these will fix your issue.

---

### Post by SeijiSensei on 2015-11-02
This is beginning to sound more like a network connectivity problem.  Did the web CUPS manager find the printer and list it in Discovered Network Printers?  Did you assign the printer a static IP address?  Can you ping the address from the Ubuntu box?

Generally speaking, it helps all of us trying to help you if you give more specific answers than "I've tried both options and neither of them worked."  Telling us how it didn't work makes for more useful answers and less time wasted on our all parts.

---

### Post by nevets68 on 2015-11-02
I don't believe it's a network issue as i can print from any windows machine in the house. Web cups didn't find the printer. I did assign a static ip. I'll play around with this a bit more but i'm not going to loose any sleep over this as ubuntu isn't my main o/s (more of a - let's see how linux works - or doesn't.) ;)

---

### Post by kurt18947 on 2015-11-03
I don't know if this will help you, it does me. I install system-config-printer as a matter of course. I assume this works with Ubuntu - it does with Ubuntu-gnome.  I find it much more useful than the 'printers' app bundled with Ubuntu Gnome and I think Ubuntu. In particular I've had to manually set 'device URI'.  Brother seems to hew pretty closely to HPs protocols.  I set a static I.P. address on the printer then in the device URI space I put "socket://xxx.xxx.xxx.xxx:9100" where xxx=i.p address of the printer. I've found this pretty straightforward and reliable but wouldn't work if the i.p. address of the printer changed on power-up.

---

### Post by kurt18947 on 2015-11-03
> **cole13 said:**
> I have followed a variety of instructions, including downloading the driver (for Samsung c410w in my case), sudo install commands and now the cups website method suggested above. No luck. Having found installation less than a breeze and installing a printer a nightmare, I fail to understand why people boost Ubuntu as easy to use. For me, when I get a new computer, installing a printer is a given and usually straightforward. Less than impressed.   Has anybody got a straightforward way of setting up a printer, step by step?

Do you need to download anything for Samsung?  I have a SL-M2870. The first few times I installed it (different machines, different distros) I used Samsung's linux installer. That requires running a script from a terminal, I believe.

[http://www.samsung.com/us/support/owners/product/SL-C410W/XAA](http://www.samsung.com/us/support/owners/product/SL-C410W/XAA)

The last few times I've just started "system-config-printer" (install from the repositories if necessary though the default 'printers' app may work too), told it to look for printers, when it found the Samsung I told it to go ahead and install the drivers. Done. Printer works, scanner works.  I didn't have to use a terminal or download anything.  I suspect people use the same techniques and procedures with Ubuntu and its ilk as they do with Windows. After all, that's always worked in the past.  I don't find Ubuntu/Linux particularly hard but it is **different** and there's a lot of incorrect, overly complex and outdated information out there. If you've tried installing different ways, you may need to uninstall your previous attempts first. I'm not sure where you'll find the Samsung uninstaller or even if there is one. I'd probably look in /home or maybe /home/Downloads for any installer folders or files. You could also use Synaptic to look for anything with Samsung in the name.

---

### Post by nevets68 on 2015-11-04
MODS - feel free to delete this thread.  I've decided to go back to windows (where printing isn't a problem.) Ubuntu is nice but when I've tried every option ( printing wise)and nothing happens then it's not the os for me.  Like i said - in windows it was super easy to install the network printer ( and it worked...the 1st time.) Honestly I don't want to fight with my operating system to get things to work. It's a tool nothing more...nothing less. When it doesn't work then it's time to go to something that does.

Anyways , thanks again for the suggestions and assistance.

---

### Post by nevets68 on 2015-11-04
UPDATE : I figured ...let me give this one more shot (and have another glass of wine. Merlot if your curious.) 

 I followed the instructions here : [http://askubuntu.com/questions/527741/printer-prints-blank-pages](http://askubuntu.com/questions/527741/printer-prints-blank-pages)


  1.  Press the "go" button on the printer three times. If the test page prints ok it is your driver.
  2.  Ubuntu software center - search for hpijs - install it all.
  3.  Remove the printer - add it back
  4.  Use the Brother HL-2170W Foomatic/hpijs-pcl5e driver
  5.  And WE HAVE PRINTING!  


  Thanks one and all for your assistance. :)

---

### Post by kurt18947 on 2015-11-06
I'm glad you were able to solve your dilemma.  Persistence pays -- usually.

---

### Post by Bucky Ball on 2015-11-06
Excellent! Whack a 'solved' on this to help others by following the link in my signature. Cheers and enjoy. :)

(PS: If you enjoy wine, I'm in South Australia and grew up about 15 minutes drive from McLaren Vale. The Barossa, Clare, the Coonawarra, all here in SA, if that means anything to you. It's a wine heaven! Not that I drink anymore ... :))

---

### Post by echotech2 on 2015-11-06
> **Bucky Ball said:**
> Not that I drink any more ... :))

...But do you drink any LESS?

---

### Post by Bucky Ball on 2015-11-06
> **echotech2 said:**
> ...But do you drink any LESS?

Haha. I probably couldn't have drunk any more than I was or did, so yes! :D

---

### Post by nevets68 on 2015-11-06
My "fav" wine lately is Yellow Tail - from Yenda Australia. :)

---

