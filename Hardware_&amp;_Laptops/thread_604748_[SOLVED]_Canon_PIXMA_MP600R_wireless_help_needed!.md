---
title: "[SOLVED] Canon PIXMA MP600R wireless help needed!"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by dorkdork777 on 2007-11-06
[B][COLOR="Blue"]Edited at OP's request and in their own words -

But its instructions are now long out of date, take a long time to follow and generally don't work at all.

Could you please edit the first post on that topic so it has a link to this other thread, which has been tested many times on new versions on Ubuntu:

[http://ubuntuforums.org/showthread.php?t=1095406](http://ubuntuforums.org/showthread.php?t=1095406)
The instructions are on posts 9 and 10 of this thread.[/COLOR][/B]


Hello again, we have a Canon PIXMA MP600R printer which connects wirelessly to our wireless router. (There's only one cable that plugs into the printer - the power cable.) To get this printer working on Windows/Macs we had to install Canon software that came with the printer, and though I have searched and searched, I have found no Linux version.

[Here's the link to the printer's hardware details]("http://www.canon.co.uk/For_Home/Product_Finder/Multifunctionals/Multifunctionals/PIXMA_MP600R/index.asp"), if it helps!

I'm using Ubuntu 7.10 Gutsy Gibbon, and I connect to the internet via a wireless card, which connects to the same network as the printer is on. I really don't know where to start with this problem. Would getting the printer's IP or MAC address help?

I know that this problem is pretty specialist, but absolutely any help would be much appreciated!

(If technical details of this printer are needed, like the IP address, I'll need to wait until the administrator gets in who'll be able to find out.)

---

### Post by dorkdork777 on 2007-11-07
Bump

---

### Post by thejimster on 2007-11-07
Hi there,

I used this guys advice:

[http://waterseven.universebox.com/?cat=7](http://waterseven.universebox.com/?cat=7)

and it worked a treat.  It does involve some third party modules but they seem ok to me (probably not saying much...). Tried same approach with official canon drivers (Japanese I think) but only the ones in the above website worked for me.

It works fine for general documents, but photos come out too small.  If you find out how to make photos print properly then please let me know (I assume the the resolution is too low or something like that...)

---

### Post by dorkdork777 on 2007-11-07
That link's dead, but I found it on archive.org, [thankfully]("http://web.archive.org/web/20070819055405/waterseven.universebox.com/?p=29"). Will these instructions be the same for a MP600R with a NETGEAR router?

---

### Post by thejimster on 2007-11-07
I've got an MP600R, and its on the network via wireless router (Belkin as it happens).

As I said the print works OK for general stuff.  Never bothered to try any scanning from Linux.  Doubt that there's any support for network scanning as under windows and I didn't go for networked printer to go back to wires...

Just tried link from original post and it worked fine for me.  Strange...

---

### Post by dorkdork777 on 2007-11-08
OK, I've got as far as this:

> 
ADDING THE PRINTER (if connected to an ASUS router)

Turn your printer on.

Go to System->Administration->Printers

Double click new printer.Choose Network Printer of type &#8220;Unix Printer (LPD)&#8221;. Click next.

Fill in the Server Field with:

192.168.1.1(change 192.168.1.1 accordingly if your ASUS router has a different address in your network)

And in the Queue Field the text:

LPRServer

Click next.

Now, choose Maker &#8220;Canon&#8221; and Model &#8220;MP 500 v.2.60&#8243;. Click Next. Fill in the description and place fields if you like.

Click Apply.

You are done!:)

The only thing is, I can't select 'Unix Printer (LPD)' - the closest I can get is 'LPD/LPR Host or Printer' - and there's no Server or Queue field to fill in! There's only Host Name and Printer name, with a 'Probe' button.

Also, to get there, I have to click on System - Administration - Printing, rather than Printers. I'm running Ubuntu 7.10.

Any help?

---

### Post by thejimster on 2007-11-08
I originally did this quite a few months ago, and there was only a 'version 1' of his tutorial - V1 uses a webbrowser to install the printer.  V2 uses the GUI as you've seen.  I now remember that I can across the same problem as you, and so followed a combination of the 2 sets of instructions.

I downloaded and modified the printer file as shown in V2 of the tutorial, and then installed the printer as in V1.

Does that make sense?

---

### Post by dorkdork777 on 2007-11-08
You, my friend, are a genius. I got it to work with only one correction - instead of putting 'lpd://192.168.1.1/LPRServer' in the box, I just put 'lpd://192.168.0.5', with 192.168.0.5 being the IP adress of the printer. I've managed to print text documents just fine thanks to your expert advice, now to try some more complex stuff. :)

EDIT: Just printed a picture in an ODT document, and a picture by itself. They both came out perfectly, but the picture has about 15mm borders on each side, which (I think) is a technical limitation of the printer. TYVVVM for the help! I've now switched to Ubuntu fully - there's no reason to boot into Windows, when I can have it running in VirtualBox with seamless integration, and now all of my hardware works 100% under Ubuntu. :D

(Before, I had problems with my video card, and before that, my wireless card. Both work fine now. :))

EDIT 2 - That said, I don't know how to get scanning to work. Though I would appreciate any suggestions, I never really used that feature anyway. ;)

---

### Post by sirfin on 2008-06-11
The Jimster,

Can I just add to Dork777s humble thanks!
When I moved over to ubuntu as a Vista fugee i was very worried about getting my beloved wireless printer running.....little did i know how easy you would make it!
Well done and thanks again,

Regards,

Sirfin

---

### Post by anywebloco on 2008-07-17
Hi - can anyone help me with how to make the printer connect to the router? I don't have windows installed so I can't use the windows-wizard  Canon provides.

---

