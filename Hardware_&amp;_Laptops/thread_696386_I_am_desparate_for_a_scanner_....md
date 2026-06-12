---
title: "I am desparate for a scanner ..."
date: 2008-02-14
forum: Hardware &amp; Laptops
---

### Post by dryder on 2008-02-14
Hi,
I'm using Feisty ...

I apologise for trying this plea again but I am desperate to know if anybody in Australia is using a currently available, stand alone USB scanner with SANE?

If so, which one(s), please?

I badly need a scanner for my work and switching to XP just for that is too time consuming and preventing me from getting rid of Windows altogether.

I have spoken to Epson Australia and checked on the SANE website for Epson scanners. They say the Perfection V350 Photo and Perfection V200 Photo 'work with Linux' but I don't know what 'good' means - does it mean just the one touch buttons don't function, for example?

Nor do I understand what the SANE website is saying I need to install to get either working  ... help there would be appreciated ( [ **[COLOR="Blue"]here[/COLOR]**]("http://avasys.jp/hp/menu000000500/hpg000000442.htm") and [**[COLOR="Blue"]here[/COLOR]**]("http://www.avasys.jp/english/linux_e/dl_scan.html") as examples).

mikeize, thanks for your reply to my previous incomplete post but I want a standalone. I can not find a current document/photo flatbed hp model on hp's Australian website that is compatible.  Thanks for replying :-)

David ](*,)

---

### Post by Whiffle on 2008-02-14
Just so you know, its possibly to run Windows under Virtualbox and use a scanner through that.  Thats what I do with my canon 8800f and it works quite nicely.  Might come in handy if you get in a tight spot.

---

### Post by dryder on 2008-02-14
Whiffle, thanks for replying.

Did you make any particular settings in VirtualBox to make it so?

My current scanner, a Microtek Scanmaker 5800, would not - it started to scan but 100% of the time stopped within a second or two.

David

---

### Post by Whiffle on 2008-02-14
I had to use the non-Open source edition of virtualbox to get usb support, (from their website).  And I had to change the permissions of the scanner, I think it was in

 /etc/udev/rules.d/40-permissions.rules

changing the line
SUBSYSTEM=="usb_device",                MODE="0660"

to
SUBSYSTEM=="usb_device",                MODE="0666

It would be a good idea to search that though, I'm not entirely sure that was it.  One ofthese days I should write these things down :-P

---

### Post by dryder on 2008-02-14
Thanks Whiffle - I'll look into it.

> It would be a good idea to search that though, I'm not entirely sure that was it. One ofthese days I should write these things down  A HOWTO on wiki or as a sticker here would be good too :-)

Cheers,
David

---

### Post by dryder on 2008-02-14
Looking at my installed Virtualbox, I am running 1.5.4. It has under 'Details' a USB link to a page for setting up the USB filter device (Enable USB controller,Enable USB EHCI controller, Name, Vendor ID, Product ID, Revision, Port, Manfacturer, Product, Serial No, Remote).

I don't recall paying for this - so how can I tell if I have the OSE or the closed source edition?

Many thanks,

David

---

### Post by Whiffle on 2008-02-14
OSE edition is the one you get from the ubuntu repositories, the other one (its still free, but some parts are closed source if i remember right), comes from the virtualbox website: 
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by oldsoundguy on 2008-02-14
seems like a huge hassle!  But a learning experience, I guess.

I have two HP units .. a 3 in 1 (old 1150 Office Jet Pro) and a 4 in 1 (6110x) that both installed using the synaptic installer and both work.  Granted, they are multiple units, but they do scan in SANE and do it well.  No need to run some other  program to get them to function.

---

### Post by o.besner on 2008-02-14
HP's F4180 is dirt cheap and can both print and scan with Linux (With HPLIP). Nothing professional though. It's okay for school and documents, and average for photos.

---

### Post by Whiffle on 2008-02-14
The biggest reason I did it the way I did was to use canon's software, which makes it *easy* to scan to pdf, which is alot of what I scan.  Click and go pretty much.

---

### Post by dryder on 2008-02-14
... continued ... :)

Whiffle - I notice I have entered the non-free virtualbox repository already in synaptic so obviously that's the one I have.

I managed to get it to scan (uses microteks scanwizard) but, though better than rebooting to XP, it is still tedious scanning to a shared folder and then opening gimp. The same is true of faxing and emailing. Thanks for the temporary relief though.

So - I am still hunting for a current model 4800 x 9600 flatbed (front opening lid) scanner in Oz ... any suggestions from anybody most welcome, but IMHO 2/3/4-in-one's just don't have the quality I need.

Fingers crossed and hoping people see this ...

David

---

### Post by 1inxs on 2008-04-22
Here is a front load Scanner that will work in Linux.
[http://www.epson.com/cgi-bin/Store/consumer/consDetail.jsp?BV_UseBVCookie=yes&oid=63060806](http://www.epson.com/cgi-bin/Store/consumer/consDetail.jsp?BV_UseBVCookie=yes&oid=63060806)
Good Luck

---

### Post by dryder on 2008-04-22
1inxs,

minds think alike !

I ordered one a few days ago from epson and it arrived this morning - and works fantastic!

Thank you for posting - had Epson not contacted me I would never have had the 'will it / won't it' conundrum sorted out.

Don't know whether I iscan does more than xsane though - might try it here on Feisty before getting Hardy.

Now if there was only a 64 bit driver ... oh, well, it's the only thing holding me back from moving to 64 bit now - everything else I have I've tested OK in 64 bit.

Many thanks!
David:)

---

