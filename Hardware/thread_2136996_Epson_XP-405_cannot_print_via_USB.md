---
title: "Epson XP-405 cannot print via USB"
date: 2013-04-19
forum: Hardware
---

### Post by chrisasl on 2013-04-19
Hello,

I bought the epson xp-405 printer, and I am trying to succeed in printing via usb. 
I've followed these steps [here]("http://ubuntuforums.org/showthread.php?t=2091976") but it doesn't seem to work.
The thing is that when I am clicking print, even a simple txt file, the window that displays the printing dialog closes and simply nothing happens.

After this, I click, Printers (at the Dash) and then double click the printer. At the window that opens, at "Printer State:" it says "Idle - Sending data to printer." 
When right click the printer and select "View Print Queue", it displays nothing. But when I click the "check" all the jobs are displayed with status "Completed".

What can I do?


(System: Ubuntu 12.10, 64bit)

---

### Post by pdc on 2013-04-20
> I've followed these steps

1) can you tell us what you did please 

....and.......

2) could you please copy and paste this command into a terminal            use the top line of the Menu in the terminal........File ..across to Edit .....down to paste ...........

> [COLOR="#FF0000"]sudo dpkg -l | grep epson-inkjet-printer[/COLOR]

and copy and paste back what you get ............

and 

3) paste this [http://localhost:631/printers/](http://localhost:631/printers/)

into a spare browser window ...........can you see an Epson driver?

---

### Post by chrisasl on 2013-04-22
1)
[a] For the downloading of the driver this is what I did:
Visited [this link]("http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX") and searched for 405, clicked Download at the 1st row (look below for screenshot of this page) > Accept > and then downloaded this "epson-inkjet-printer-201203j_1.0.0-1lsb3.2_amd64.deb" as my system is 64bit.

[IMG]http://i35.tinypic.com/2125uus.jpg[/IMG]

[b] Installed with ubuntu software center by double clicking it.
[c] After that I opened the "Printers" tool. Clicked "Add" and in the devices select box, the epson printer was there and at the right side it said, "a printer connected to a USB port."
[d] clicked forward and then a small window opened and it printed "searching for drivers"
[e] after the previous window closed, this is what I saw: 
[IMG]http://i35.tinypic.com/359xy6w.png[/IMG]
So I selected "Yes I accept this license" and then "Forward". A small window opened saying installing driver and then this new window opened:
[IMG]http://i35.tinypic.com/359xy6w.jpg[/IMG]
**But also a crash was occured with the install-printerdriver.py script. **
[U][I]The info of the crash from /var/cache/ are attached to this post.
[/I][/U]
[f] After the previous window, I clicked "Forward" having selected the "Generic Driver".
Then I got this window:
[IMG]http://i38.tinypic.com/24lr8mf.png[/IMG]


[g] Clicked forward, got this:
[IMG]http://i34.tinypic.com/2v2tnbs.png[/IMG]
And finaly "apply".  

[h] It then asked me if I want to print a test page, clicked yes, nothing printed and job is classified as "Completed".


2) This is what I get: 
> ii  epson-inkjet-printer-201203j                1.0.0-1lsb3.2                              amd64        EPSON PX-405A/PX-435A - Epson Inkjet Printer Driver


3) Yes, this is what I get:
> EPSON-XP-402-403-405-406-SeriesEPSON XP-402 403 405 406 Serieschris-desktopGeneric ESC/P Dot Matrix Printer Foomatic/epson (recommended)Idle

---

### Post by pdc on 2013-04-22
so you have the XP-405;

when I enter that in the Epson search box I get what is in the thumbnail; ([COLOR="#0000FF"]XP-405[/COLOR])

you seem to have downloaded a driver for the PX-405A.........similar to yours........maybe the driver makes no difference but I would feel downloading and installing the driver Epson release for the XP-405 might be the best-est thing to do

I suspect you downloaded the driver for the PX405A ......just a suspicion........see the thumbnail of that name...........so you got [COLOR="#008000"]epson-inkjet-printer-201203j_1.0.0-1lsb3.2_amd64.deb[/COLOR] whereas the other is [COLOR="#008000"]epson-inkjet-printer-201201w_1.0.0-1lsb3.2_amd64.deb[/COLOR] ..maybe no real difference..

I sort of get a bit bewildered watching all the clicking you .........I think your printer dialogue didn't notice what you had done by downloading from Epson and instead 

.............wait a minute..............one of your thumbnails shows the [COLOR="#FF0000"]201201w[/COLOR] ......that is the XP-405 driver .......so looks like your system went to Epson for that ..after you had installed the [COLOR="#FF0000"]201203j[/COLOR] ..because you document that also ..

.........I suspect it would be best to clean out all and start again.........that is only my advice........that means go to Administration ..Printing and deleting all there and opening package manager and deleting epson-inkjet entries.........

I think from what you document................*.that what I had read about*.............seems to happen ...............namely that _**Ubuntu is all set up now to talk directly to Epson when it recognises a new printer**_...........and goes to Epson and installs what it needs........

.......so you could just delete your existing [COLOR="#008000"]201203j[/COLOR] and instead just go on the [COLOR="#008000"]201201w[/COLOR]

---

