---
title: "Lexmark Pro 200 Series Printer?"
date: 2010-01-11
forum: Hardware
---

### Post by Buuntu on 2010-01-11
My family just bought a new wireless printer - a Lexmark Prospect Pro 205 to be exact.  It's already been configured fine with all the Windows computer in the house by using the installation CD.  I was just wondering if this printer was compatible with Ubuntu, I already looked in the list of supported printers and it wasn't listed.  Furthermore I tried adding it with the Printer tool in Ubuntu and I couldn't find it (maybe because I don't know what options to chose :P).  Anyways, the printer is Wireless and uses my network - it isn't connected to any computer.  It has its own built in WiFi and even it's own IP.

Can someone help me set it up or tell me if this printer is even supported?  I would really like to be able to print - it would make things very difficult if I couldn't.
Thanks.

---

### Post by LinuxDeal on 2010-01-13
It would help us help you to provide the actual model.  "Lexmark Pro 250" doesn't seem to exist.

[http://www.google.com/search?q=Lexmark+Pro+250](http://www.google.com/search?q=Lexmark+Pro+250)

---

### Post by Buuntu on 2010-01-13
Oops, it's 205, not 250.  *Lexmark Prospect Pro 205.

Thanks for pointing that out :P.

---

### Post by Dark_Stang on 2010-01-14
Lexmark is generally a no-no for Linux. But they actually have some drivers posted for that model, they appear to be x86 only though.
[http://support.lexmark.com/index?locale=en&segment=DOWNLOAD&startover=y&userlocale=EN_US&question=pro+205&productCode=LEXMARK_PROSPECT_PRO205&page=answers&detectedProductFacet=CMS-CATEGORY_REF.LEXMARK.PRODUCTS.ALLINONE.LEXMARK_PROSPECT_PRO205&searchid=1263450195282#2](http://support.lexmark.com/index?locale=en&segment=DOWNLOAD&startover=y&userlocale=EN_US&question=pro+205&productCode=LEXMARK_PROSPECT_PRO205&page=answers&detectedProductFacet=CMS-CATEGORY_REF.LEXMARK.PRODUCTS.ALLINONE.LEXMARK_PROSPECT_PRO205&searchid=1263450195282#2)

Just click the downloads button and you'll see Linux at the bottom. Good luck.

---

### Post by Buuntu on 2010-01-15
Sweet, that worked like a charm :).

Thanks man!

---

### Post by gitano on 2010-01-28
i would like to know if the original poster of the question was using 32 or 64 bit ubuntu, as it would help me decide whether or not to buy this printer. i see there is 32 bit drivers on the lexmark support site.
and i can see you got them working.
but whats o.s. version are you using?

---

### Post by gitano on 2010-01-28
well buuntu must be using 32 bit ubuntu, as dark_stang mentioned, the drivers provided by lexmark are 32 bit only. 
i got on the phone with lexmark support and they mentioned that they do support ubuntu, but only 32 bit. (what? why?) she seemed a bit unsure.  anyway she actually called me back 10 minutes later to explain that without a doubt they have no 64 bit ubuntu drivers.  according to her its a matter of demand, and they might publish some in the future.
well what this means for 64 bit gnu/linux ubuntu users is that this lexmark prospect pro 205, is not compatible.

also she seemed to have checked their whole current line up- and the situation is the same.

but i cant be sure, as i only have personally tried the prospect pro205.

its going back to office depot- too bad because it was very cheap, $99-
not to mention it works really well under windows 7 ultimate 64 bit and xp home 32 bit

---

### Post by Samuraidog on 2010-02-24
I noticed that Lexmark took down their Ubuntu drivers for the Lexmark Prospect Pro205 about a week or two ago. Now they are only offering drivers for Fedora and OpenSuSE. 

Prior to this, I called Lexmark technical support asking when they would offer Ubuntu 64-bit drivers. I was told that they couldn't give an answer, but the Ubuntu 64-bit drivers would be posted on their site "very soon".  

I'm glad I saved the 32-bit Ubuntu driver downloaded before they took it down. I've got a bad feeling that they aren't going to post it up again anytime soon, and I highly doubt we will see a 64-bit version.

---

### Post by FatalChaos on 2011-01-07
> **Samuraidog said:**
> I noticed that Lexmark took down their Ubuntu drivers for the Lexmark Prospect Pro205 about a week or two ago. Now they are only offering drivers for Fedora and OpenSuSE. 

Prior to this, I called Lexmark technical support asking when they would offer Ubuntu 64-bit drivers. I was told that they couldn't give an answer, but the Ubuntu 64-bit drivers would be posted on their site "very soon".  

I'm glad I saved the 32-bit Ubuntu driver downloaded before they took it down. I've got a bad feeling that they aren't going to post it up again anytime soon, and I highly doubt we will see a 64-bit version.

Hey, the deb drivers are still there, but it just doesn't appear on the previously given link for some reason. 

Here you go: [http://support.lexmark.com/index?locale=EN&page=product&userlocale=EN_US&productCode=LEXMARK_PROSPECT_PRO205&focusedTab=DOWNLOADS#1](http://support.lexmark.com/index?locale=EN&page=product&userlocale=EN_US&productCode=LEXMARK_PROSPECT_PRO205&focusedTab=DOWNLOADS#1)

---

### Post by Feenix3k on 2011-01-09
The Lexmark Pro 205 now has 64 bit drivers for Ubuntu 10.10. I just downloaded the drivers.  [http://support.lexmark.com/index?locale=en&page=product&productCode=LEXMARK_PROSPECT_PRO205&segment=SUPPORT&userlocale=EN_US&frompage=null#1](http://support.lexmark.com/index?locale=en&page=product&productCode=LEXMARK_PROSPECT_PRO205&segment=SUPPORT&userlocale=EN_US&frompage=null#1)

---

### Post by heyandy889 on 2011-01-30
[COLOR=Black]Awesome, glad to see that others have this working too. :-D The link posted before me by [/COLOR]Feenix3k was how I installed and printed with this printer. I had a minor issue with a failure to gain administrator access. Had to run the install script with sudo. Anyways, here are the gory details.
[COLOR=Black]
Go to "Lexmark United States Support & Downloads for Lexmark Prospect Pro205" [http://support.lexmark.com/index?locale=en&page=product&productCode=LEXMARK_PROSPECT_PRO205&segment=SUPPORT&userlocale=EN_US&frompage=null#1](http://support.lexmark.com/index?locale=en&page=product&productCode=LEXMARK_PROSPECT_PRO205&segment=SUPPORT&userlocale=EN_US&frompage=null#1) Scroll down the page and click "See Downloads for Linux/Unix." I clicked on the third option, "Printer Driver without JRE for 32-bit Debian Package Manager based Distros." Gives you a popup, click download, choose download location. After download of the .tar.gz is finished, extract that sucker. Should give you a file "lexmark-inkjet-legacy-1.0-1.i386.deb.sh" Instead of double clicking to run the script, what you want to do is open a terminal Ctrl-Alt-T and type "sudo that file" where that file is the path of the .deb.sh. Should open a nice GUI installer. When I initially installed the printer on Windows XP about a year ago, I remember various bugs with getting the printer to print over our local wireless network. I eventually had my roommate fix the wireless printing. 

Not too tough in comparison to compiling a custom kernel and other stuff my CS classes are having me do right now. :-D

edit: installed printer software on another ubuntu computer. I got this weird error about not having the lexmark JRE something installed. I Googled "JRE" and apparently it means "Java Runtime Environment." I went to the Ubuntu Software Repository, downloaded the Java Runtime Environment, and the printer installation went great.
[/COLOR]

---

### Post by sbrbot on 2011-06-08
I have the same printer Lexmark Prospect Pro205 and I can confirm that it works fine with Ubuntu as wireless printer. It work even as a wireless scanner on Ubuntu with Xsane software ([xsane.org]("http://xsane.org")).

---

### Post by David Mitch99 on 2011-08-08
Hi -- I am a total newbie with Linux (LinuxMint 10). I also have the Prospect 205 and I installed it just fine. It used to work great with LinuxMint 10, but in my haste to get smarter, I started to add a Guest account and started fooling around with Permissions. Now my printer will only print a Testpage. If I try to print something else, I get an Error *"/usr/local/lexmark/legacy/bin/printfilter failed"*. Any ideas to fix this?

---

### Post by ebbygonzo on 2011-10-20
I keep getting this when trying to install in 11.10:

Lua error detected: While parsing install.lua: config/run.lua:1476: attempt to index global 'ownhership' (a nil value)

me no like-y......and I have no idea what it means.

---

### Post by Genesius on 2012-01-18
Hoping someone has an idea before I get on the phone with Lexmark support.

Just bought a pro 205 printer. Downloaded the drivers from Lexmark (running Ubuntu 11.10 64-bit), found the fix for the lua error [here](http://dylanmtaylor.com/2011/04/17/fixing-lexmark-printer-driver-installation-in-ubuntu-11-04/). Conected the printer and my system sees it, but when I try to print I get "Printer Error - the printer cannot communicate with the computer".

Printing with USB cable. I know it's good, because I was able to install the printer & print with no problem from my XP VM on the same machine.

Guess it's the price I pay for saving a couple of bucks on a Lexmark. . .

---

### Post by T8r on 2012-05-29
Getting the same error. Printer worked perfectly on 11.10, and after upgrading to 12.04 any document that gets sent to the cue eventually fails. (unable to communicate with printer)

I Removed the drivers using synaptic and reinstalled using the Lexmark installer (this fixed the issues I had after upgrading to 11.10). If the installer is run using sudo, it completes without any error messages. 

The usb connection is good, because I can print without any problem using my virtual XP machine. 

I used the Device URI that came up on the list when the computer 'saw' the printer connected during the set up process. The laptop recognises the printer and everything shows up in cups ([http://localhost:631/printers/](http://localhost:631/printers/) from a web browser) but the status is listed as " Idle - "/usr/local/lexmark/legacy/bin/printfilter failed" 

Any time I try to print a test page or document, it sits in the cue and eventually gives the "unable to communicate with printer" error message. 

Any assistance or insight is greatly appreciated. As embarrassing as it would be, I'd love to find out that my problem is somewhere between the chair and the keyboard.

---

### Post by mewtwo532 on 2013-01-27
it still won't work for me.

---

### Post by mewtwo532 on 2013-01-27
> **T8r said:**
> Getting the same error. Printer worked perfectly on 11.10, and after upgrading to 12.04 any document that gets sent to the cue eventually fails. (unable to communicate with printer)

I Removed the drivers using synaptic and reinstalled using the Lexmark installer (this fixed the issues I had after upgrading to 11.10). If the installer is run using sudo, it completes without any error messages. 

The usb connection is good, because I can print without any problem using my virtual XP machine. 

I used the Device URI that came up on the list when the computer 'saw' the printer connected during the set up process. The laptop recognises the printer and everything shows up in cups ([http://localhost:631/printers/](http://localhost:631/printers/) from a web browser) but the status is listed as " Idle - "/usr/local/lexmark/legacy/bin/printfilter failed" 

Any time I try to print a test page or document, it sits in the cue and eventually gives the "unable to communicate with printer" error message. 

Any assistance or insight is greatly appreciated. As embarrassing as it would be, I'd love to find out that my problem is somewhere between the chair and the keyboard.
It is happing to me to

---

