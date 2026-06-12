---
title: "Epson XP-322 printing problem"
date: 2015-01-17
forum: Hardware
---

### Post by kimberley2 on 2015-01-17
I have been trying without success to get my new Epson printer to actually print! The copy and scan features work OK so the printer is recognised and a page which I had copied actually printed albeit at a snail's pace. Could someone please assist me in overcoming the problem using simple instructions step by step.):P

I did manage to take a screen shot of the error log but have not managed to copy it onto this page :mad:

Thanking you in advance for any help anyone is able to give.

---

### Post by Mike_Walsh on 2015-01-17
Hallo, kimberly.

First of all, what OS are you using? Can you let us know your machine's specifications (CPU, RAM, graphics card, 32- or 64-bit, etc)?

And lastly, what steps have you taken so far with getting the printer installed?


Regards,

Mike.

---

### Post by kimberley2 on 2015-01-18
Hello Mike

Thank you for your response. I am using xubutu 14.4, 32 bit but that is basically all I know as the hardare/software was put together by a friendly 'expert' and I do not know how to go about ascertaining the specifications. I cannot ask my 'expert' as we are now in different countries and have lost touch..A sudden thought which should have occurred to me before I asked the question - the printer is wireless operated but my computer is connected via an ethernet cable. This is probably the reason it will not work!

---

### Post by Mike_Walsh on 2015-01-18
Hallo, Kimberly.

Oh, that's a bit rough. Can't even ask him/her what they did..!

I doubt your combination of wired & wireless connections will make any difference, actually. Routers are designed to handle both, in ANY combination.....that's their function, after all. I have my printer hooked to my main desktop via USB, and my old laptop can print to my desktop via its wireless connection to the router, then Ethernet to the desktop, then from the desktop to the printer via the USB cable. 

At the end of the day, it doesn't much matter HOW the data gets from your 'puter to your printer, just so long as it does!

You say the copy and scan functions are working okay. Are you operating them from your machine.....or directly, from the printer's control panel? Because they WILL work from that, regardless of anything being sent from the computer; in that sense, copy & scan are 'standalone' functions. They don't necessarily HAVE to have anything sent FROM your machine; they CAN work with material presented manually.

You say, too, that it has part-printed a page, but at a snail's pace? Sounds like a case of an incorrect driver, to be honest. I'm going to get you to visit Epson's download Centre, and download what SHOULD be the correct drivers for your machine.....OK? You've told me the part I need to know, which is that you're running a 32-bit version.

Go to this web page:-

[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

Enter your model in the top box; just enter XP-322, and then select 'Linux' in the drop-down box where it says 'Operating system'. Then click on the magnifying glass.

You should get a search results page, with two lines in it. You'll need to download both entries, but I'm going to get you to do this one at a time. You'll see why shortly.

Click on 'Download' for the first line. You'll come to another page, with a very long list of supported items; scroll down to the bottom, and click on 'Accept'. The page will extend a little further; and the item you want here, is 'epson-inkjet-printer-escpr_1.4.4-1.lsb3.2_i386.deb'. Click on the 'Download' button next to this, and save to your downloads folder.

Go back to the search results page (if your browser won't let you, just run the search again). You'll now need to 'download' the second entry, where it says 'core scanner/data package'. Again, click on 'Accept' at the bottom of that long list when it comes back up.

This time, you need to download TWO items. 'iscan_2.30.1-1~usb0.1.ltdl7_i386.deb', & 'iscan-data_1.34.0-1_all.deb' Again, save to your downloads folder.

----------------------------------------------------------------------------------------------------------------------------------

OK. NOW, we'll start to install things. Before we do, though, I need you to enter ONE command in the terminal for me. Go to the 'Whisker' menu (the little mouse head in the top-left corner), and click on it. Click on 'Accessories' in the right-hand column, then scroll down to where it says 'Terminal'. Click on this.

Enter the following command EXACTLY:-

```
sudo apt-get install lsb
```

Press 'Enter'. You'll be asked for your password (this is what you log in with). Enter it in; you won't see anything come up....this is perfectly normal. Hit 'Enter' again. Allow the terminal to finish what it's doing, and when your ID (xxxxx@xxxxx) appears at the bottom again, close the terminal.

When you've done this, open your downloads folder. Double-click on the 'epson-inkjet-printer-escpr' entry (or single-click if you have that set). The Software Centre will open up, and it will install the driver for you.

Now, repeat this for the other two items, the scanner ones. However, this bit is VERY important; you must install the 'data' file BEFORE you install the scanner package. This is because the scanner package requires what's in the data file in order to install correctly. Once again, the Software Centre will open up, and install them for you.

---------------------------------------------------------------------------------------------------------------------------

At this point, the scanner software is now installed. We'll now set-up the printer.

First of all, turn your printer on.

Now, for this next bit, I'm not that certain, since I've not got a wireless printer..! We'll try it the conventional way first. 

'Whisker' menu>Settings (like a little checkered square beside the power off button, in the bottom right-hand corner), then>Printers.

When the printer window comes up, it'll say one of two things, Either you'll see an icon of a printer (in which case your friend has set it up for you), or it'll say 'No printer configured yet'.....and you'll see a '+' sign. If so, click on this.

The next window will show you a list of printer types. You should see your printer there. Click on it, and then 'Next' or 'OK' at the bottom.

IF the wireless printer is rcognised, the rest of the set-up is straight-forward! Just follow the next window through, and accept the default settings. If you want to rename the printer to something else, do it at this point, in the top box. Click 'Next' or 'OK'. 

At this point, it SHOULD be installed, and will ask you if you want to print a test page. I'm sure you can take it from here.

If not, then we'll have to wait for somebody who knows about connecting wireless Epsons.....!!


Hope this all helps, as far as it goes.


Regards,

Mike.

---

### Post by kimberley2 on 2015-01-19
Good morning Mike

Thank you so very much for all the trouble you have taken in giving me such detailed instructions. I am away from home for the next few days so am unable to do what you suggest. As soon as I return I shall follow your instructions and of course let you know the outcome. 

Best regards
Kimberley

---

### Post by Mike_Walsh on 2015-01-19
No problemo.

Let us know how you get on with things when you get a chance. I don't guarantee that my suggestions WILL work; but I've set up Epson printers on so many distros this last nine months or so, I can nearly do it blind-folded.

That was almost entirely from memory...


Regards,

Mike. ;)

---

### Post by kimberley2 on 2015-01-22
Mike I don't seem to be having much luck at the moment as I have tried for the pst 2 das and 'service is temporarily unavailable' on the link you gave. I have searched elsewhere for drivers but without success as Epson, AVYS and Seiko Epson no longer supplyl so I will try your link again in a day or so .

Regards
Kimberley

---

### Post by Mike_Walsh on 2015-01-22
Hallo, Kimberley.

Hm. Doesn't surprise me! The site is often unavailable (almost always when you really need it, too). All you CAN do is to keep trying. I find the best time to access the site is during the early hours of the morning (I rarely turn in much before 2 am), so if I need to get anything I usually access it before turning in. 

Usually the servers are bringing the site from the States, but sometimes I have accessed it from Japan. Go figure. I hate to think how many redirects the data is having to take when it has to come all that way!

Keep on trying, though. Be best if you try as frequently as you can. We'll get this sorted, one way or another.

I'll do a bit more research in the meantime. Bear with me.


Regards,

Mike. ;)

---

### Post by kimberley2 on 2015-01-23
Hallo Mike

I will do as you suggest but I must admit it seems pretty incredible that having bought a product one cannot get it to work. I specifically asked in the store if the XP-322 could be used with Linux and the answer was  a definite 'yes'.  Had I known that I would have to download drivers I would not have purchased this printer - soooooo frustrating.
I will keep you informed of any progress.

Regards
Kimmberley:p I'm trying to keep smiling!

---

### Post by kimberley2 on 2015-01-24
Mike,
 I have now managed to download and install the drivers above that you recommend (thanks to your easy to follow instructions) and although everything seems to be working OK and the paper feeds through it is BLANK. 

When I checked my downloads this one has also been installed (I am not sure if I did this previously) - 'epson-inkjet-printer-escpr 1.4.4-llsb3.2'.  Do you think this could be a problem and, if so, how do I remove it as there is no 'uninstall' button on these drivers on the Ubuntu software centre?

They do say patience is a virtue, don't they !!
Best regards
Kimberley


Your instructions

---

### Post by Mike_Walsh on 2015-01-24
Hallo again. 

Hm! Well, now; it shouldn't actually make any difference if you have an extra driver installed, since, if I understand the way Linux works correctly (and I'm MORE than willing to be corrected on this one), the hardware in question - in this case your printer - SHOULD automatically sym-link to the driver that will actually work.

However; if you wish to remove it, do you have that particular one in your downloads folder? You ought to have, since those drivers can ONLY have come from the Epson download site; you'll not find it anywhere else. If so, double-click on it again; the Software Centre will once again open, only THIS time, it should show as already installed. The button on the far side that will normally show as 'Install' will now show as 'Uninstall, so just click on this, and the system will remove it for you.

I know there's a command-line way for doing this through the terminal, but you need a wee bit of experience and a bit more knowledge to do it that way.....and for the life of me I can't think what it is off the top of my head. The Software Center just makes it easier for newcomers, until they get the hang of using the terminal (which, actually, is a LOT quicker than talking to the system via other layers of software).


Regards,

Mike.

---

### Post by kimberley2 on 2015-01-29
EUREKA  Epson XP-322 now working perfectly.  Not quite sure what solved the problem. Mike, I think it was a combination of your suggestions and then moving around some of the information that appeared. 

Thank you and best wishes
Kimbrley;)

---

