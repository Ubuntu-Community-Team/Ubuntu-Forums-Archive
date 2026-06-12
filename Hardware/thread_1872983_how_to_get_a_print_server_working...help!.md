---
title: "how to get a print server working...help!"
date: 2011-10-31
forum: Hardware
---

### Post by Lorro on 2011-10-31
Hello everyone!
I have problems with a [COLOR=Red]TP-link tl-ps310u[/COLOR] print server.
can't find linux drivers for it and I have my MFP and a usb hard drive connected to this device via a usb hub and I'm not able to use them.....
Any suggestion for a newbuy? 
will I be able to use my hard drive and the printer or should I give up?
help please!
By the way Ubuntu is great!!
Ciao:)

---

### Post by win0922 on 2011-10-31
What version of Ubuntu are you running

---

### Post by win0922 on 2011-10-31
[http://www.tplink.com/en/products/details/?model=TL-PS310U#down](http://www.tplink.com/en/products/details/?model=TL-PS310U#down)
 
Is this it?-

---

### Post by Lorro on 2011-10-31
yes it is that one.... I run ubuntu studio 11.04
help please!!!!

---

### Post by Lorro on 2011-11-02
no clues?
I managed to install the printer as a network printer but it's not working properly anyway... the printer seems to receive the print order but it stops suddenly and hangs ....
help please :(

---

### Post by varunendra on 2011-11-03
> **Lorro said:**
> no clues?
I managed to install the printer as a network printer but it's not working properly anyway... the printer seems to receive the print order but it stops suddenly and hangs ....
help please :(
Please explain everything you have done to get it work as a network printer. If it works wile connected as a USB printer, it 'should' work the same way while connected as a network printer, provided your LAN connection to the print server is at least High Speed (100 Mbps).

However, as I mentioned in my PM reply to you, I crashed my system on which I installed my HP LJ3050 earlier using the same print server, and now can't get it to work again with my Xubuntu on a portable hard drive, using the same method that I think I used earlier. So I am confused a bit at the moment and can't suggest a proper way. Besides, I've still got all that data-recovery work to do, so can't do many experiments either.

Just a question apart from how you have currently connected it (I guess it's the same LDP/LPR method, since the problem is same :(), have you tried its software on wine? I haven't tried it yet, but will as soon as I get time (and space on my hard drive ;)).

---

### Post by Lorro on 2011-11-03
yeah... tried with wine but when I open the print server manager and try to connect it to the printer or to the hard drive it just tells me that the hardware is not recognized and I need drivers... should I install windows driver through wine as well? I don't think it'll work .... sounds weird...
so the print server is connected via lan cable to my wireless router... the printer  and the hard drive are connected to mini usb hub (which has 4 usb connectors) via usb cables. that's it.

---

### Post by Lorro on 2011-11-10
Right I see that is not an easy one....... furthermore....
I have upgraded to 11.10 but now it's even worse.
the system doesn't seem to see the printer at all now......
not even if I try to find it under the lpd/lpr thing......
:confused:
help me please

---

### Post by Lorro on 2011-11-28
Does anyone knows if going back to previous release will delete my home with all my documents and stuff?

---

### Post by Mark Phelps on 2011-12-01
> **Lorro said:**
> Does anyone knows if going back to previous release will delete my home with all my documents and stuff?

Basically, you can't "go back" to an earlier releaes.  Ubuntu does not provide any roll-back capability.  You have to reinstall the older version.

What you CAN do is save off the contents of your /home folder (including all the hidden files and directories), do the reinstall, and then selectively copy stuff back.

However, the reinstall will also set you back to an initial install of that version -- meaning that any apps you've installed will be gone as well.

Regarding the print server itself, there are no actual drivers for it, as it is a networked device and only connects to your PC over the network.  I also use a D-Link print server, and I used CUPS to install the networked printer that is connected to it.

To use CUPS, open a browser and enter "localhost:631" (without the quotation marks).  Once there, use the option to Add a printer -- if CUPS sees it, it will be listed as a selectable printer.

---

### Post by Lorro on 2011-12-02
You are the best!!!! Why didn't anyonelse tell me about cups? I'll try that!!!.
if it'll work no need to change to previous version..... by the way.... here is another question, since I have my home directory in a partition different from the system folder.... could it be easier to install another release?
Thank you again!!!!
:)

---

### Post by Lorro on 2011-12-09
Ok the thing with Cups worked.... let's say that i'm able printing now.... but anyway there is a strange printer behaviour, it's amazingly slow.... it starts printing but then suddenly stops.... then a line and stops again.... and so on. I'm talking about up to 10 minutes for a single page.....what could it be?
tried configuring all parameters within cups and in the preferences of the printer in the system > print thing from the main menu.... but .....
any idea?
thanks again

---

