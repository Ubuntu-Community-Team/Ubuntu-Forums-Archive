---
title: "Epson LQ570+ Printer"
date: 2015-01-25
forum: Hardware
---

### Post by james_king2 on 2015-01-25
First I know this printer is a Model T Ford sort of speaking but it has been a very good and dependable printer. I am using Ubuntu 14.04.1 LTS 32 bit on an older Azus Desk top machine with 2Mgs Ram and two 500GB Stata HDs. 
I have seen several old Threads about this particuliar printer as well as others but, I simply haven't been able to get the printer to even come close to working anywhere near right. It prints out garbage and spits pages out non-stop when using the ppds one can find concerning Linux OP systems.  Not knowning anything about any part of programing, I gave up after a couple of weeks trying to get the printer to work. Most of the time and seemingly no mater what port I might try to get around the above problem, the printer would not print anything at all.
Today, I tried using a USB Cable I had purchased years ago now from Cables Unlimited called ( USB to IEEE1284 Parallel Printer Cable), The package only mentions a couple of Epson Printers in the serries "Epson PM and Epson EPL printers."  It seems to be more inclined for the Epson Stylus, HP laser jet, Desk jet, and Cannon BJC printers as a whole. 
I have put all this down incase someone else might have an older printer model and trying to make it work. The disk that came with it only has the installation for Windows up to 2000 but also has a Linux driver which has the code and something I know nothing about at all.
I conected the cable to the computer and the LQ 570 and then went to add a printer. It was found as well as going through the listings of suggested printers, I found mine. It installed and I tried the printer test page and it printed out nice. However, the only remaing problem is once the page prints it doesn't reset the printer to ready as well as advance the page. I have to shut the printer off and manually position the paper . Would anyone have an idea how to get this part of it working properly?  :mad:

---

### Post by Mike_Walsh on 2015-01-25
Hallo, James.

Normally, I find setting up Epsons is quite easy; easier than,say, a Brother or an HP (!), but then, yours is the first impact printer I've come across for quite some time. The last time I used one was my old FX-80, which I used for the best part of 16 years, until 2004. I eventually had to replace it because I could no longer get hold of the cartridges for it. You're not wrong about the old impact Epsons, neither; mine was SO reliable (albeit a wee bit on the noisy side!), I never needed to worry about whether or not it would work.....it just DID.

Which PPDs have you tried? Have you tried the ones from openprinting.org, as specified [here]("http://www.openprinting.org/printer/Epson/Epson-LQ-570plus")?

I also don't really know for sure, but perhaps[ this]("http://www.linuxfoundation.org/collaborate/workgroups/openprinting/database/ppddocumentation") page might be of some use to you, if you need more specific help with PPD files (which I'm afraid are really the only available option for such old equipment).

Hope that helps.


Regards,

Mike. :)

---

### Post by james_king2 on 2015-01-27
Thank you for taking time to answer my question. I did try the PPD on the Open Printing page but I have not been fooling around with Ubuntu very long and certainly do not know what I am doing when working with the OS. With that said and when trying to print with that PPD, the printer only printed out from one to many garbage graphics and wouldn't stop. It would spit out page after page of garbage and the only way to stop the printer was to power it off. 
I would think that there must be a way to make the printer work properly but I am in no way any sort of programmer and totally dense when it comes to that end of things. 
I like the printer for normal everyday stuff that doesn't require a lot of graphics and what have you. Also not to mention that it is  less costly to print test documents that the Deskjet, and laser printers I have. I can't remember everything I have tried but The add printer shows the LQ570+ and everything concerning that area seems to look as it should but it just doesn't work properly. 
Jim

---

### Post by Mike_Walsh on 2015-01-28
Hallo again, Jim.

I'm afraid I'm not being a lot of help to you on this one! I've only been using Linux for less than a year myself, but I've already figured out that Epsons seem to be one of the easiest makes of printers to get up-and-running; certainly a lot easier than Canons or HPs, and as for Brothers.....they appear to be a nightmare.

Epson drivers and what have you are very easy to get hold of, but Epson themselves have this annoying stance on Linux drivers and PPDs, until you suss out where to actually get hold of them. I had a long chat conversation with one of their customer service people back in June last year. I've been messing around with these things in one form or another since the late 70's/early 80's ( the days when home computing was just starting to take off). I reckon I've tried just about every O/S on the market at some point.....and just wish I'd discovered GNU/Linux sooner, as it really is incredibly configurable.

Their customer service people WERE insisting that they 'don't do Linux drivers', and at that time were passing people on to a Japanese company called Avasys, who used to develop the Linux drivers for them. What they don't tell you is that Avasys dropped responsibility for the driver repositories in 2012, and passed that responsibility back to Epson themselves.....who, until quite recently, weren't passing that information on to the customers. Wee bit naughty!

I don't think I've used any other brand of printer apart from Epsons; the old FX-80 was SO ridiculously reliable, that when it finally came time to put it out to pasture, I didn't look anywhere else. It served me well for 16 years, and in 2004 I purchased a Photo Stylus 830U...which did likewise, until the ink costs began to get prohibitive (they have the all-in-one colour cartridges; as soon as ONE colour runs low, they refuse to function till you replace the cartridge. I must have thrown away more ink than I actually used.....) Then, in 2011, I bought the SX218 ( a basic version of the Workforce semi-pro small business printers), which I've used ever since. Never been an ounce of trouble.

But back to your printer. I'm one of these folk who like to keep old hardware running (I happen to think older stuff was made better years ago), and certainly a few businesses in our town, including our local timber merchants, are still using old Epson impact printers to this day, although they're probably using Windows (and like as not, XP at that!) But as for Linux drivers for such old hardware, I don't really know. It's possible there was better support for older printers and suchlike a few years ago; I know for a fact that although Linux is renowned for keeping old hardware going, even IT has a cut-off point when support is finally dropped.

Sorry I can't be of more help.


Regards,

Mike. :)

---

### Post by james_king2 on 2015-01-28
Mike, you sound a bit like myself concerning older equipment. I was just on Epson's site and they seem to offer an LQ 590 impact printer but, it is out of stock. They probably have ended producing it in reality though. I saw that they had some drivers for Linux but they are not for the impact printers. I downloaded and older driver for my printer for DOS and am not expecting that it will do me any good but maybe, somehow, I can get to look at the code in that driver and get a few ideas from it??? My real deal is this, I look at a computer as being something like a toilet, you are always flushing money down it for stuff that needs endless upgrades. As far as Inkjet printers go, when you first purchase one, the cartridges are not priced to as high but a couple of years dow the road they seem to about double in cost and never go the other direction. I can't complain to much about the HP Deskjet printers I have purchased concerning their reliability but the cartridges that were say about in the $50 for both is now closer to $80. The ribbon for my Epson even from Epson is less than $10 each and they last reasonably well if you are not doing graphics. However as you know Inkjet cartridges soon by-pass the original cost of the printer even though I usually try to stick with a more "business printer" than the very low line ones. 
I did get the LQ 570 to print one page at a time using a Cables Unlimited USB TO IEEE1284 cable. It prints normally the test page but, the driver evidently has a problem when it get to the end of the page. The data light stays on and doesn't go off as it should and there by doesn't advance to the next page. I have to turn the printer off and advance the paper manually. The problem with the cable is I have had it for years and it was still in the original package. It was actually made for the Epson Stylus 300-850 printers and Stylus photo 700 and EX printers as well as Canon, HP laser Jet and HP Deskjet printers. Also Epson PM, EPL, Lexmark ans Panasonic printers of several models. 
I also tried the printer using that cable on my 3yr old HP Lap Top running Windows 7 and it automatically installed and operates very well as it should do normally. So, I know that the USB to IEEE1284 cable its self does actually work with the printer. Sort of speacking with the exception of Ubuntu. If I actually knew what I was doing, it would probably work in the Linux OS as well.
Oh! I started fooling around with Commodore C-128's, Epson Equity 2 computers and have built a number of others but, I never could understand programming.
Thank you ,Jim

---

### Post by JeQhdMD on 2015-01-29
Did you read these first few paragraphs about this printer/driver?   There are two files needed (the driver file itself and "foomatic-rip".   Also, the info says don't use cut/paste when downloading and putting the file into the final directory you want (you don't want to keep it in /downloads as that get's cluttered with other downloads).  The site says this driver works "perfectly" . . use the 2nd url to do the download.


[http://www.openprinting.org/ppd-o-matic.php?driver=epson&printer=Epson-LQ-570plus&show=1](http://www.openprinting.org/ppd-o-matic.php?driver=epson&printer=Epson-LQ-570plus&show=1)

[http://www.openprinting.org/printer/Epson/Epson-LQ-570plus](http://www.openprinting.org/printer/Epson/Epson-LQ-570plus)

---

### Post by Mike_Walsh on 2015-01-29
I think JeQhdMD has got the answer right there, Jim; I've had a look at it myself (in fact, I looked at it the other night, but wasn't quite sure what it was).

It seems the 'foomatic-rip' file works together with the PPD file to make things happen. In very much the same way as you currently install Epson's scanners in Linux; you MUST install a 'data' package first, before you install the scanner driver. The one requires data from the other to be able to install itself correctly.....

Give it a try. I think it may well get things working. BTW, thanks for reminding me about the 'ribbon' for the impact printers; I'd forgotten they worked like an old-fashioned typewriter! I've installed so many ink-jet printers for various folk over the last decade or so, I'd forgotten there WAS anything other than cartridges...

> [COLOR=#000000] My real deal is this, I look at a computer as being something like a toilet, you are always flushing money down it for stuff that needs endless upgrades.[/COLOR]

Which is one of the very best things about Linux, by and large; the very fact that you DON'T need to constantly upgrade your hardware. Most electronic hardware has a far longer lifespan than the 'trade' would have you believe. Both of my current machines are 'cast-offs' from other members of the family, who NEEDED upgraded hardware to run their updated Windows OSs! I think my total costs over the last few years come to something like £75 or so ($125?); an external hard drive, a PCIe USB 3.0 expansion card, and a couple of flash drives.....most of which I could probably have done without! They weren't NECESSARY...


Regards,

Mike. ;)

EDIT: MY first machine was a C-64.....and the closest I ever got to programming was writing my own 'Hangman' game in BASIC (with a database of ALL of 25 words)!

---

### Post by james_king2 on 2015-01-29
JeQhdMD, Thank you for your reply. First I did read the information but I will tell you that I really didn't under stand what was being talked about. I looked at the "foomatic-rip" but it means very little to me as I really don't know what is actually is. I searched my machine and had seen a file with that name had been installed throughthe Ubuntu software center as there are a number of listings concerning Cups and a bunch of other things. I am just learning a little bit about Ubuntu and Linux and most of that sort of thing is pure Greek to me as I have been using strictly Windows OS from 3.1 - 7 and never had to go through all of this sort of thing to get a printer up and working. (foomatic but I didn't notice a "rip") (I am just trying to indicate the little I know as yet.) 
I downloaded the Epson LQ 570 driver with Firefox but it does it so quickly it really doesn't even seem to give me a choice during the download to point it to any specific area and ends up in the "download folder." (I was expecting Firefox to tell me it was at least downloading the file but, it didn't do that.) (I clicked on the download arrow and saw that the file was already there!?) It is a lot different that how Internet Explorer 11  lets you pick out a folder to place a file in. So I am just learning the ropes the hard way with Firefox as well. The thing I didn't do was cut/ paste the file to any other place either. I just left the file as it was downloaded so it wouldn't get changed. 
I will try the two links you have indicated but I really don't know what to do with the "foomatic-rip" file as far as getting it to install or, whatever has to take place to do it correctly.
I have only been fooling around with this machine on the side trying to learn how to get things done as far as setting up things on it as well as seeing what programs might do what I need to do concerning my uses. Until I get somewhat efficent at using this OS I have kept my Windows 7 machine as it is due to all the years of pictures and many important documents I hae amassed over the years. Again, I deeply appreciate any help as I trip along learning the ropes. Jim

---

### Post by james_king2 on 2015-01-30
Mike, I am in a position very late in life I wasn't expecting and has changed things to a point I have to go as cheep as possible or not eat. So, I can't go for the latest or gratest stuff. I also learned to dislike MS from windows 95 and the more they kept pushing their upgrades and never really getting any one system all that bug free has made me like it even less. The best machine I ever bought was a MAC back in the early 90's but that cost me a small fortune and the software was very expensive as well so, the reason I went to Windows. 
I checked the Epson site last night for ribbons for the 570 and they are $5.50 each and the LQ 590 has replaced my printer but they are out of stock and you have to have them E-mail you when they have them. (Not that I am in the market for one!) I also had a C 64 but never used it and gave it to my son to play games on it. I never could master the programng for those machines eiter as I am a person that has to see a picture to do most things or it is pointless for me. 
I recycle most everything I can and even when I replace a hard drive I keep it if it is good. Then I install it in a Sabrent enclosure and use it as a back up drive. I have another Idea that I am going to try if I end up needing to do so should I not find the programs I need in Linux. I ordered Windows 7 for a refurbished PC as it is the least expensive way to go and a new Segate 500GB drive (OEM) so I can set up a dual boot system for Ubuntu and W 7. That way I can still run Turbo Tax, Quicken, and another specialized program to do sound and pictures together. I have to much work on some things to take many chances on blowing away years of work in those areas and want a completely clean setup just in case. 
I have tried Kmymoney and GNUcash but the first will not download from a bank and the second one I haven't figured out how to make the download work as yet. 
I do thank you for your suggestions as well and hope that "if" I get smart enough, I can also be of some help as time goes on to folks as well. Thw problem is I am a bit slow when it comes to some things. Jim

---

### Post by Mike_Walsh on 2015-01-30
Jim,

I wouldn't worry too much about impecuniosity; I've been there AND done that. Not a pleasant position to be in, but we have to make the best of whatever situation we find ourselves in.

I was using XP up until May last year; like you, I'd used Windows from 3.1 onwards, and too, like you, I came to like it less and less with each new release (not least being the fact that you could very rarely run the new version on the old hardware). I have a friend in his late 60's, who was running Vista on an old Dell Inspiron desktop; he only ever uses it to surf, do e-mails, and keep in touch with his daughter in New Zealand via Skype.

I've been his unofficial 'admin guy' for years now, and noticed, two or three months ago, that his machine was no longer updating (turned out to be something to do with his SP1 not being updated when it should have been, so the SP2 wouldn't 'take', but anyway...) I pointed out to him that meant his machine was pretty unsafe to use, He asked me what he could do about it, and reminded me that he wasn't really in the market for a new version of Windows, because he basically couldn't afford it.

So I told him about all the various different Linux distributions, which are all completely free. He asked if he could do the same things with them that he was used to doing in Windows; I told him yes, he could. So he gave me the green light to go ahead and install a new O/S; and with a wee bit of research, I figured out his machine would quite happily run Ubuntu 14.04. So that's what I did.....and he's chuffed to bits with it. He really likes the Unity desktop (says it looks very 'smart'!), and says it's a lot faster and more responsive than it ever used to be.

So; another satisfied Linux user. He's getting the hang of it quite nicely, despite being a self-confessed 'dinosaur' where tech's concerned. He reckons its a lot easier to learn than Windows, too.


Regards,

Mike.

BTW: You probably found Firefox downloaded as fast as it did because the driver files and what have you for the printers ARE pretty small; only a few MB at most. And in most Linux distros that I've tried, the 'Downloads' folder is the default destination for web downloads. You CAN change the destination if you want, but since file transfer is so ridiculously easy in Linux, it's very simple to move them to where you actually want them...

---

### Post by james_king2 on 2015-01-30
Mike, I really appreciate the input and I am so close to 70 and there is no fun in it! My memory stick seems to be made out of OAK rather than gray matter and (memory) is so short it burns me up. I just read "Foomatic From the User's Point of View by Till Kamppeter." However, I don't really know if I have to go through all of that to be able to install the ppd for the printer or not?? I tried his command of "gs -h" in terminal and it gave a long list of "installed drivers" but, I didn't see my Epson listed in them. There were a few Epsons listed but I would assumer they are most likely ink jets. I tried to use the "chmod etc.etc.command," but didn'y get it right or, the Epson model or whatever has to be put in the command line. (on page 8 of the print out of his information.) So, before I really mess things up, I stopped at that point.  Much of everything I see is for HP printers and I have a Deskjet 6980dt which works with no problems through my WiFi router. (Another use-to-was printer now.) Even Windows 7 doesn't really support it per-say. ( I have upper and lower trays on it and double sided printing thing but their plain Jane driver wouldn't work those options but, through my router, I was able to use all the features the printer has.
Getting back to the more important things, VISTA, pure junk! When I bought my first HP Pavillion it came with XP Pro and offered a free upgrade to Vista pro. I kept Vista on the machine for several months but it was a total headache. I removed it and went back to XP. Then I went for Windows 7 as it was next to XP and supported. The rest is not worth the bothering with an older machine period! I haven't heard people raving about the newer systems either! MS is shooting themselves in the foot concerning many areas of their OS's and they are getting gaget crazy and, fads are super hard to try to keep up with.
I greater problems with getting the hang of Linux systems is mainly the things like my printer and a few other things like Terminal. For the most part, everything else is straigt forward and just letting Unbuntu's software installer do it. I have over the years fooled around with Open Office for Windows and it worked well but it would not handle large word processing documents without getting lost so I stuck with MS Word 2010 as it seems to keep pages and grafics where they belong in 500+ page documents with pictures. I haven't tried the word processor in Ubuntu other than importing a large doucment and it seemed to be good. I know Word has tons of stuff added to a document that adds a lot of overhead to it as well. So, I will try printing out a large document Lib Office and see how it works at some point in time down the road.
Lastly, I did learn how to point a download to a new folder which I named print driver ppd last night. Right now that is where the ppd is for the Epson printer that I had originally downloaded using JeQhdMD's suggestion but I don't actually find two seperate files on his supplied links but, I just might be missing something? I looked for quite some time and went back and forth to the likes on his post trying to see the difference but I couldn't actually find any. 
I hope I haven't driven you goofy with all my nonsense?  Thank you, Jim

---

### Post by james_king2 on 2015-01-31
I finally got to this point after looking and reading many things about Cups. It seems that the Cups installed is "Cups 1.7.2" I read an article which pointed to using the Web Browser pointed to: [http://localhost:631/printers/Epson-LQ570+](http://localhost:631/printers/Epson-LQ570+),. There is quite a lot of information which I will list to see if anyone might be able to steer me in a direction to hopefully fix the problems I have run into trying to get the printrer installed and other than printing just garbage and continiously spitting out page after page non-stop.
Print-out has the following; Description: LQ570+, Location: James-System-Product Name; DRIVER: Epson LQ570+ Foomatic/Epson (recommended) (_grayscale, 2-sided printing_)  **_I know this printer isn't capable of the last two items mentioned to my knowledge_.**
Connection: parallel:/dev/Lp0; Defaults: job-sheets=none, none media=na_8.5x11in sides=one-one.
There is a jobs search, search in Epson-LQ-570+: ** BLank in the search box.** Then, Show Completed Jobs, Show All Jobs ** both seperate boxes. **
The last things listed are: ID Epson-LQ670+-156; Name: Set Default Options; User: anoymous 1k, Size Pages: Unknown; State: stopped "filter failed". 
That is the end of what is shown on the page. I saw some other options listed as well as EDIT at the top of the page but I don't dare fool with all of that yet without knowing more about all of this stuff. The ppd came from Open Print which says the driver works "perfectly."  I would think that it probably may well "work perfectly" if I could figure out what I am doing a miss. I have found though up to this point  there is little information as concerning the proper way concerning the installation of an impact printer such as this one.  At least fo myself. :mad:
Thank you Folks in advance for any help you possible could give to me. Jim

---

### Post by Mike_Walsh on 2015-01-31
Hallo again, Jim.

Now then; time to get serious. Let's see if I can help you with this CUPS business.

I take it, after your reading, that you know what CUPS stands for by now? It's the [COLOR=#ff0000]C[/COLOR]ommon [COLOR=#ff0000]U[/COLOR]nix [COLOR=#ff0000]P[/COLOR]rinting[COLOR=#ff0000] S[/COLOR]ystem, and as far as I'm aware, every single Linux distro uses it.....because Linux is based on Unix, either directly or indirectly. Now; the majority of distros hide this from the user, and give you instead a nice GUI to add & install your printers with.....but it's still working through CUPS in the background.

I've had a little bit of experience in using this thing directly. I run some of the Puppy Linux distros; everything's lean, and mean, and as minimal as possible, to keep the footprint as small as they can get it. So they don't give you a GUI to add your printer with; they send you straight to CUPS, which can be accessed via any web browser. And as you've found out yourself, 'localhost:631' is what you type into the browser's address bar to access it. It's really a 'web interface'; CUPS IS installed on your machine, but it's simpler to tell you to use the browser to access it, than to give you a GUI.

Now; before I go any further with this, how far have you got with the process? Have you followed it all the way through, from adding your printer, to adding the PPD file (which is the last step before selecting your default options)? Once you've selected the default options, it'll then tell you whether your printer has been added successfully. I need to know how far you've got with the process before I can tell you what needs doing next.

Incidentally, I think that what 'gs-h' is doing is merely listing the hardware devices (in this case, printers) which are supported by what's known as Ghostscript. This, I think you'll find, is the default, fall-back, open-source 'filter' provided with every CUPS installation. It'll provide very basic functionality for the listed models, but I don't think, looking at it, that it's been updated for quite some time.
 
'Filter' is merely the term used in Unix/Linux for 'driver'; from what I can figure out, reading some of the history of Unix in Wikipedia, this term has been used right from the outset. And don't take any notice of where it says 'developed by Apple' at the bottom of the page; that's all right, because Apple is actually based on POSIX, which is loosely related to Unix. I think POSIX actually defines the interfaces that Unix-like systems run on; but anyway, that's what OS X is based on.

[http://en.wikipedia.org/wiki/POSIX](http://en.wikipedia.org/wiki/POSIX)

A lot of folk don't know this. Remember the hoo-ha about the 'Bash' bug, back in October? My brother's just recently treated himself to a brand-new, top-of-the-range iMac. I told him about this as soon as I found out about it.....and he just pooh-poohed it, as if I didn't know what I was talking about. John's a long-term Windows 'power-user', and only just switched to Apple; no doubt seduced by all the marketing spiel! He tends to equate cost with suitability; in other words, if it's the most expensive, it MUST be the best... I'm sure you must have run into a few folk like that yourself! John looks down his nose at me, 'cos I run Linux on my sister's cast-off 10-yr old Compaq desktop.....but then, my software's not costing me a penny, whereas he's paying through the nose for his.....! \\:D/

This is what my CUPS 'Printers' tab currently looks like (I'm in Puppy, running from a flash-drive, on the old Dell at the moment:-

[ATTACH=CONFIG]259643[/ATTACH]

Let me know how far you got with the installation process, please, and we'll see where to go from there.


Regards,

Mike. ;)

---

### Post by james_king2 on 2015-02-01
Mike, right at the moment I can't tell you everything I tried but the first thing I had done was to delete the printer I had installed through the GUI. Then I went to the Local Host 631 and went to the Add Printer there. I had pointed it to the PPD I had downloaded and un-zipped from Open Print (I think it was? The "perfect driver as it was referred to.)  I tried the print test page and it did nothing at all. Now, I don't recall everything at the moment but I also checked to see what the program said was installed and it did show the Epson but it listed the "pages-un-known," and the "state as stopped, filter failed." I didn't try the "reprint." Move Job," or "Cancel Job" boxes next to that information. I did look in the Administrator box but didn't do anything with that either and ""Quit."" 
To me, the printer is being basically set up by the PPD as a either a USB or router controlled printer and none of which it is as it is simply connected to the Parallel port. 
I decided to go to Epson and all they provide is a PPD for a Generic 24 Pin printer which I did download and burned on a disk. I didn't bother with that driver but wanted it just in case. The last binge I went on was looking up my system disks for windows 95, 98 and XP Home. I tried to look into the printer folders on each of those systems but there is nothing for the LQ 570 and mainly everything for Ink jet and Laser printers only. I was getting burned out going through all of that as well as reading so I gave up as I had to pay my bills. Hopefully that might help you some but to get back into it better I would have to go back to my computer with the Ubuntu system on it as I had to take it off of my desk to do the bills on my W-7 HP machine. (I have no room sort of speaking.) 
I also went nuts looking for the manual for the LQ 570 and found it. I wanted to see if it might list some sort of driver like some other printer I had back when. It does list a lot of stuff about Esc codes and Fonts, what have you but it is Greek to me. I did see which I had bought it though in March 1996!
Thanks you for continued help, Jim
Oh! the PPD said it was 4.3?? by Apple I think?

---

### Post by james_king2 on 2015-02-11
Mike, If you could tell me how to install some snap shots of the local host 631 screen views I will install them so you cans see the installation of the printer. It doesn't print with the setup as it is but, I figure that seeing things as they are is better for you at the moment. Then I will try to go on from there. I downloaded and installed a program called ScreenShot wich I used to grab three of the views for the printer. I have never done anything like this before and don't know the proper way to handle it. I also don't know what this system allows either and don't desire to make folks unhappy with a mistake on my end if possible. Thank You, Jim

---

### Post by Mike_Walsh on 2015-02-11
Hallo again, Jim.

Okay. I take it you need to know how to get the screenshots you took into your post? No problem.

If you go to the Quick Reply box at the bottom of the page, you'll see there's a button below it marked 'Go Advanced'. Click on this.

The next page will have a preview pane at the top if you've typed anything to start with, otherwise you've just got the main editor.....but with a lot more buttons and stuff above it, and a lot of other commands and stuff below it. With me so far?

Just select exactly where in the post you want the pictures to appear (use the cursor...the flashing 'I' thing.). Scroll down below the editor to where it says 'Manage Attachments'. Click on the button, and a window should open up.

You'll see a box at the top, on the right-hand side; 'Add Files'. Click on this. Select your files (obviously, put your screenshots where you know where to find them!) You'll return to the previous page. Click on 'Upload', in the same little box. You'll see the pictures appear, along the bottom of the window, as you upload them. Repeat until you have all your screenshots showing in the 'Attachments' pane at the bottom. 

Then; click on each one in turn, and, bottom right of the window, click on the button marked 'Insert in-line'. Repeat for each one. When you're finished, click 'Done'. Scroll back up to the editor, and you should see the screenshots inserted in the message. And when you've finished your message, just post in the normal way.

Okay?

Hope that helps.


Regards,

Mike.

BTW: DON'T worry about making mistakes at your end.....we've ALL done it. We all had to get the hang of navigating the forums; vBulletin is NOT the most forgiving of software...!  Even the staff aren't too keen on it, apparently... :lol:

---

### Post by james_king2 on 2015-02-12
Mike, I don't know that the screen shots will be any great deal of help but it might give you an idea of sorts. I will give it  a go now and see what happens, Jim.

[ATTACH=CONFIG]259927[/ATTACH][ATTACH=CONFIG]259928[/ATTACH][ATTACH=CONFIG]259929[/ATTACH]


This is the "perfect working" PPD - Adobe: 4.3, created by the Cups PPD Complier v1.2.4, copyright 2007 by Apple Inc. Copyright 1997-2007 by Easy Software Products.

---

### Post by james_king2 on 2015-02-12
Mike, There are a number of things in this PPD that actually are not correct concerning the LQ 570 + printer such as the fan fold size of the paper. Another is about monochrome color instead of black and white. It also seems to be only geared to single 8 x11 paper of the single sheet type rather than tractor fed paper. The printer uses Epson ESC/P printer language rather than PostScript as well. I am thinking that these things are possibley a part of the problem which cause the printer to print garbage non stop unless it is shut down via the off switch. 
I have looked on many forums as well as the Cups site and other places trying to glean things from it all. My problems though as far as trying to even compile something is simply I do not know how to even get things like that started in the first place or, the commands to even try something either. The LocalHost 631 is very limiting as to what it allows you to try to change to se if something could be made to work.
I have printed out a reem and a half of paper on my Brother DCP 7020 printer printing out everything I can get hold of just in the off chnce I might try to work on something. I probably should just give it up but I can't stand quitting on something. That has been one of my life's problems as I don't know when to throw in the towel until I can't stand it any longer. Than you for your help, Jim

---

### Post by Mike_Walsh on 2015-02-12
Hallo, Jim.

Um. Yes. O-k-a-a-a-y. Well, now;

I wouldn't have thought that a printer that old would be capable of using PostScript, in all honesty. But, I have been known to be wrong! Let me do a web search...

Seems I WAS wrong! PostScript was apparently introduced by Adobe way back in 1984, and was first used by Apple in 1985:-

[http://en.wikipedia.org/wiki/PostScript_fonts](http://en.wikipedia.org/wiki/PostScript_fonts)

To be frank, I don't know how you would go about disabling PostScript, so it could use just the ESC/P language. But from what I can understand of it, PostScript is specifically to do with the fonts, whereas ESC/P is all to do with layout, and telling the printer how far to advance the page per line, what size of paper, what type of paper, how much ink to pump through the nozzles in the head on each pass.....etc. So, going by THAT, it seems the two SHOULD run side-by-side; the PostScript being like a 'library' of fonts that the printer can call upon, depending on what you, the user, has selected.

I really don't know quite what else to suggest! I'm like you, in one respect; I also don't give up on things easily.....once I've got the 'bit between my teeth', as it were, I just keep on chipping away at the problem, whatever it is; 99 times out of 100, I get there in the end. From what I can see of it, you don't actually NEED to get the Epson running.....you just WANT to!

Leave it with me, and let me do a bit more research. Keep an eye to this thread; I've no idea HOW long it might take me..... :lol:


Regards,

Mike.

BTW; I think you'll find that 'monochrome' IS black & white. 'Grayscale', on the other hand, renders every shade of colour as a different shade of grey...

---

### Post by james_king2 on 2015-02-12
Mike, I certainly appreciate your efforts as I am at a loss when it comes to the programming stuff. What also throws me somewhat is when I connect the printer to my Windows 7 machine there is absolutely no problems getting it up and running?? Well what do I know? My thoughts had been trying to see how the Windows drivers are put together but, I don't know how to actually get a look at them either. And, you are right about me wanting the Epson to run and, it is a real good printer as well and at $5.50 US per ribbon from Epson, it beats the cost ink carteridges for normal everyday printing unless. you have to have aprint out in seconds, that is. When I am doing documents and because I am not a touch typer, I often do a lot of printing and re-reading to see if I have made a lot of mistakes as well as checking to see if I made any real sense in what I have said. So i do a lot of printing at times due to that as well as memory slippage on my part. 
Thank you. Jim

---

### Post by james_king2 on 2015-02-12
Mike, while I am thinking about this, I saw a lot of posts even on the Linux site wher folks were trying to get this printer to work as well. They are relatively old though and it seems many ended up buying ink jets or laser printer but, even then, many were complaining that those also wouldn't either print or do so correctly. I also had seen mention of complaints about the costs of running the last types of printers as well. 
I have an old HP-IIp laser printer that I had purchased for use with my Mac LC back in the early 90s. It finally gave up. I had paid $850.00 for it back then not counting the Pacific Page add on system to make it work with the Mac. Anyway i searched for a long time for parts and pieces and then rebuilt the printer myself and it worked like new once again. On rare occasions, I still use it too with the old Mac Power pc. In other words, I do most all of my own repairs and upgrades on all this old junk. Jim

---

### Post by Mike_Walsh on 2015-02-13
Hah! Join the club, mate..! I've always done my own repairs on most things around the house. Car, too.....and all the odds and ends in the garage. I appreciate that mechanics, fitters et al have to make a living, but you can get hold of the parts to repair anything, as long as you know where to look. Of course, it does help having friends 'in the trade', as it were.....but I've always been that way inclined. Even as a nipper, I was always taking things apart to find out what made them tick; not so good at putting them back together, though, in those days.

Same with these things; I've only really been into the 'techie' side of computers for the last couple of years, but I'm rapidly finding out that I'm not too bad when it comes to fixing them!

Anyway, like I said, leave this with me; I've got one or two things I'm thinking of getting you to try at your end, but I've got a fair bit more reading up to do as yet.....I like to get my facts absolutely clear before I 'plunge into the deep end...'


Regards,

Mike. :)

BTW: Just so that you know, there are CERTAIN combinations of hardware/software around (more so in Linux still, I'm afraid, but the devs are making HUGE strides in recent years.....I have nowt but praise for them) which just ARE untenable; in other words, they never WILL work, no matter what you do with 'em! Keep your fingers crossed this isn't one of those....

---

### Post by james_king2 on 2015-02-14
Mike, I even have my eyes crossed even though it doesn't help. I also have been reading a lot of "stuff" but for me it is not a great help. I did run across something I would like to try even though it probably will not work but, Maybe!? I just don't know how to get to do it though as the permissions thing is stopping me at every turn thus far. I will go to the advanced reply though to run it by you as I will tell you where the information  came from and what is suggested as well as a screen shot that would tell more than I even know or understand. Thank you, Jim

---

### Post by james_king2 on 2015-02-14
Mike, This is from about 600+ document named " TroubleShooting Cups and Asking for Help, HowTo (A guide for the Desperate) by, Kurt Pfeifle, Danks Deutschland, GMbH. He says that the PPDs for 9 and 24 pin Epson Matrics printers, for Epson Stylus Color and Photo printers, HP Laser Jet and Deskjet printers and Dymo Label printers (PPDs installed along side your Cups installation)  Will enable these printers but will not give you access to specific capacities of the models. (duplex, input tray selection, smaller margins,...)
PPD from printer Mfgs., I will skip most of it but in short he claims that normally, Windows NT versions work flawlessly with Cups. You get them from any MS Windows PC that has the PostScript Driver for this printer installed. Put a copy into your */usr/share/cups/model/ *directory to make it available through the Web Interface. 
I downloaded several of these drivers from a link in the material last night. I tried to copy the NT generic 24 pin Epson into the place he suggested but I can't get it there due to telling me I do not have permission and am not the owner. I am the Admin but it doesn't mean beans concerning this deal. I need to know how to get around this to be able to give this a shot if you or someone could tell me how to get the PPD in that Model Folder? I found a command on anothert thread that says to type in this and it would show the owner. (ls -l / ) It did give a listing and it shows the "root directory" by the looks. Mike I don't know how to clear the duplicates here or in the upload tool but the one for the Terminal is the only one I wanted to inset. Thank you, Jim

---

