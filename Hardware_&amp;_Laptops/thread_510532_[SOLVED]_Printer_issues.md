---
title: "[SOLVED] Printer issues"
date: 2007-07-26
forum: Hardware &amp; Laptops
---

### Post by rouge568 on 2007-07-26
I have a Pixma iP1700 that I just got working using the ip2200 drivers (as recommended). I printed a test page fine, but then I tried a quick OpenOffice document (what I will be primarily using it for) and nothing happens. The print shortcut does nothing, and crl+p puts it on the queue briefly, says its printing, and goes away, while my printer sits silent. Image Viewer printing does the same, so it's not program-specific. Any advice?

---

### Post by ronny_d on 2007-07-26
> **rouge568 said:**
> I have a Pixma iP1700 that I just got working using the ip2200 drivers (as recommended). I printed a test page fine, but then I tried a quick OpenOffice document (what I will be primarily using it for) and nothing happens. The print shortcut does nothing, and crl+p puts it on the queue briefly, says its printing, and goes away, while my printer sits silent. Image Viewer printing does the same, so it's not program-specific. Any advice?


I remember this issue or a similar issue. It was some years ago. In OpenOffice by then (version 1.1. or even before StarOffice) i adapted the printersettings in this wordprocessor to the settings of the driver of my printer. I had a postscript printer that had some specific postscript level. After that OpenOffice printed fine. Look at 'properties' in the OpenOffice printer settings.  Check the properties of your printer in the set up of the printer for this. With me, this worked and i am sure it will work in the latest OpenOffice the same.

---

### Post by rouge568 on 2007-07-26
They are the same settings - I don't know what version of OO you use, but all the settings are set to "driver". And again, it is not a program-specific problem.

---

### Post by ronny_d on 2007-07-27
> **rouge568 said:**
> They are the same settings - I don't know what version of OO you use, but all the settings are set to "driver". And again, it is not a program-specific problem.

The OO-version does not matter. What is important: in OpenOffice do not set it to driver, but in my case my printer was a postscriptprinter and ps-level 2, so i set in OpenOffice and by then StarOffice and after that the former OpenOffice version..., the level to '2' because that was the level of the postscript language of my postscriptprinter. So in OpenOffice: do not set it 'literally' to driver settings, but see the details you can choose. This solved it all for me; it is independent of which version of OpenOffice you use. Really: this works.

---

### Post by ronny_d on 2007-07-27
P.S.: also make sure that the language of the hardware device 'printer', so the actual printer is set to the same printer language as in your printer configuration, and that also this is done in OpenOffice. That is: all three speak the same printer language then. Again: i had this issue too some time ago and did this and it all worked perfectly after that. I at first looked at what the language was in my printer set up configuration tool, then i changed the properties in the wordprocessor and then i checked my actual printer and made sure "all three" were set in the same language level and could print without any problems all programs that i needed prints from, and when i could not, i changed in the program the printlevel properties. Anyway: i had no problem with printing after all that.

---

### Post by rouge568 on 2007-07-27
Thank you for your help. I tried both postscript levels in OO: neither worked. How do I go about finding out the languages that they are using, and then changing that?

---

### Post by ronny_d on 2007-07-27
Hi, you must check out what is the language your printer is using  in the actual printer, that is: the device printer, the "machine" printer itself. Look in the menu of your printer. Though i am not familiar with what your printer looks like, in my printer there was a menu and i skipped through that menu and found out about its language settings. Then i checked in the printer configuration and what it said there about the language (like postscriptlevel so and so, for example), then i made sure i set my printer, that is the device itself, the... thing itself, to that same language, and then in OpenOffice i by then went to printer properties and set it to the same level of the configuration, of the device and so then "all three" had the same language. 

If your printer is printing the testpage from the configuration tool in Ubuntu, it so works. All you need to do is make sure that OpenOffice speaks the same "level" in the printerproperties. 

Maybe else, deconfigure / uninstall your printer and install it again and see whether 'postscript is recommended' or something like that is given when you choose the driver / when you set the driver, then take that level in OpenOffice, reboot..., and check whether your configuration tool prints a testpage... and then check if OpenOffice prints any page you want, and then check the other applications like texteditor and the image program and make sure for the image program you also check the printer options in that program. 

(I suppose you have a postscript printer...)

---

### Post by ronny_d on 2007-07-27
By the way... True: i am not familiar with your printer and who knows there are issues i do not knowm but look what i found from a geek in Indonesia (it is in English) and i hope it is good news for you:

[http://choxblog.wordpress.com/2007/06/09/](http://choxblog.wordpress.com/2007/06/09/)

check out this link, maybe it is of help for you.

---

### Post by ronny_d on 2007-07-27
p.s.: check out what this Indonesian geek says about '600 dpi' of your (and his) printer's resolution on that page link

---

### Post by rouge568 on 2007-07-28
My printer is not a postscript printer (as off of amazon). However, OO only has option for "driver, Postcript level1, and Postscript level2". I tried all of them just in case, and none work. And I set it up originally via that link.

---

### Post by ronny_d on 2007-07-28
> **rouge568 said:**
> My printer is not a postscript printer (as off of amazon). However, OO only has option for "driver, Postcript level1, and Postscript level2". I tried all of them just in case, and none work. And I set it up originally via that link.



Have you also checked the 600 dpi in the printer as a maximum? That geek said such is necessary for that printer. But i remember i had exactly the same printing issue with OpenOffice when it still was named StarOffice and after that too; the corrections in the properties of that wordprocessor solved the problem. If your printer for sure is not a postscript printer, than level 1 and 2 in OpenOffice properties for the printer are of no use, because that is about postscript level.  

What is the exact driver you see in the list of your printerconfiguration that is used when you check this under 'system' and administration and then 'printers'?

---

### Post by ronny_d on 2007-07-28
Else i would recommend: post on this geek's blog, [http://choxblog.wordpress.com/2007/06/09/](http://choxblog.wordpress.com/2007/06/09/) because there is room for comments and he will not show your e-mail address, as i read. it is my impression that  he speaks English and Linux and Ubuntu all in one. Just send him the link of your thread here maybe too.  He has the same printer as you. Explain him your difficulties with printing in OO. I guess he must be able to fix this problem and i am sure he would love to help you out on this.

---

### Post by rouge568 on 2007-07-28
Yes, 600dpi is the maximum. And the driver was the one from his site. I'll go and post.

---

### Post by rouge568 on 2008-03-27
Update:
Problem was solved using [http://www.oooforum.org/forum/viewtopic.phtml?t=60488&sid=59c97470ea3d72220b6095eefadddb03]("http://www.oooforum.org/forum/viewtopic.phtml?t=60488&sid=59c97470ea3d72220b6095eefadddb03")

---

