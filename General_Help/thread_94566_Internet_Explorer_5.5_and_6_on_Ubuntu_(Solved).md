---
title: "Internet Explorer 5.5 and 6 on Ubuntu? (Solved)"
date: 2005-11-24
forum: General Help
---

### Post by sander marechal on 2005-11-24
Hello,

I am a webdeveloper and as such I am faced with making my websites compatible with MS Internet Explorer. I know, it's sad but I have to (or my clients won't pay). My questions:

Is there any way to get Internet Explorer running on Ubuntu? Through Wine? How do I do that?

More daunting:
Is there a way that I can run two different versions of Internet Explorer side-by-side on Ubuntu? Ideally I would like to run IE 5.5 and 6.0 besides eachother, since those are the versions I need to support (I dropped support for all other versions, including IE 5.5 for Mac).

Thanks for any help you guys can give me!

---

### Post by soulestream on 2005-11-24
I find it interesting that people take the time to ask a question, but dont bother using google for 3 seconds:confused: 

[link]("http://patrick.spacesurfer.com/ie_wine_install.html")

as far as both i would imagine you could as they dont actually "bind" themself into the system


if that link doesnt help I got about 15000 hits on google with "wine internet explorer"


soule

---

### Post by aysiu on 2005-11-24
[QUOTE=soulestream]
if that link doesnt help I got about 15000 hits on google with "wine internet explorer"[/QUOTE] A total beginner wouldn't know to Google "wine internet explorer." What's "wine"? [The search for *internet explorer linux*](http://www.google.com/search?hl=en&q=internet+explorer+linux&btnG=Google+Search) is a bit less fruitful and obvious, so please give our new users a break.

That said, I'd highly recommend [IEs4Linux.](http://www.tatanka.com.br/ies4linux/). It'll take a few steps, but it gives you the option to install three different versions of IE, and the script is totally automated:

1. Follow the instructions in the first link of my sig.
2. Open up a terminal: Applications > Accessories > Terminal
3. Type this command in ```
sudo apt-get update
sudo apt-get install cabextract wine
```
4. Download IEs4Linux
5. Double-click and then click *Extract*
6. Open up the newly extracted (unzipped, if you're familiar with Windows) folder and double-click on ies4linux.
7. Choose to "run in terminal." You'll be given the options there (see screenshot).

---

### Post by soulestream on 2005-11-24
while i would agree many new users would not know about wine

he/she asked about using wine in the question.

thats why i suggested searching for it

soule

---

### Post by aysiu on 2005-11-24
[QUOTE=soulestream]while i would agree many new users would not know about wine

he/she asked about using wine in the question.

thats why i suggested searching for it[/QUOTE] Ah, good point. Nevertheless, it's not so obvious how to get 5.5 and 6 on at the same time. I tend to give users with a post count of less than 50 the benefit of the doubt. Maybe I'm wrong to do that, but I do.

---

### Post by sander marechal on 2005-11-24
@soulestream: The reason I asked was that AFAIK wine just provides Windows API's. I doubt it also provides the Windows bugs and internal hacks that allow you to run different IE's next to eachotrher on Windows through the IEXPLORE.EXE.local trick. Also, wine supports IE 5.5 (according to their website) and I didn't see IE 6 in the gold or silver lists. 

@aysiu: Thank you very much :) I'll go try that out immediately!

---

### Post by YanH on 2005-11-24
I've just installed it and it works a treat. :D . It'll save me from having to boot up a windoze machine just to check my sites work in IE, webdesigning can now be 100% m$ free!

---

### Post by cdsboy on 2005-11-24
another thing you can do is get [CrossOver]("http://www.codeweavers.com/") and install internet explorer threw that. I know from experiance that it runs just like in windows. You do have to pay for the program but it isn't a big fee and i wouldn't see that being a problem since you are using this program for clients

---

### Post by jordan on 2005-11-24
You may also consider using one of the following websites--browsershots and iecapture are free--browsercam costs money.

[Browsershots]("http://browsershots.org/")
[ieCapture]("http://www.danvine.com/iecapture/")
[Browsercam]("http://www.browsercam.com/")

---

### Post by sander marechal on 2005-11-24
Thanks aysiu. It worked great! I now have IE5, IE5.5 and IE6 running. :)

---

### Post by ekravche on 2005-11-25
This is pretty cool. I didn't know that it's that easy to install ie on ubuntu :)

---

### Post by jnoreiko on 2006-01-10
I'm getting timeouts when the script tries to download  [http://activex.microsoft.com/controls/vc/mfc40.cab](http://activex.microsoft.com/controls/vc/mfc40.cab)

---

### Post by 504harry on 2006-01-10
[QUOTE=aysiu]Ah, good point. Nevertheless, it's not so obvious how to get 5.5 and 6 on at the same time. I tend to give users with a post count of less than 50 the benefit of the doubt. Maybe I'm wrong to do that, but I do.[/QUOTE]
Thanks aysiu from another Newbie.
I don't think I want to touch IE5 again but your "Know-how-to" is being added to my list of **50 Good things to know for the Newbie**
so that when I have the time I can trial them and report back. etc. 
So Is this truely IE under Wine or is it something that behaves like IE - since I understood IE is one of Microsoft's flakey concoctions.
thanks

---

### Post by jackdirt on 2006-01-11
Thanks this is great solution, some odd glitches in IE 6 with flash and overlapping and lack of transparency but otherwise great.

---

### Post by dcstar on 2006-01-12
[QUOTE=YanH]I've just installed it and it works a treat. :D . It'll save me from having to boot up a windoze machine just to check my sites work in IE, webdesigning can now be 100% m$ free![/QUOTE]
There is also an "ieview" extension for Firefox to open a page in IE - and it works in Linux (with a little script from the developer's homepage).

---

### Post by briancurtin on 2006-01-12
[QUOTE=jnoreiko]I'm getting timeouts when the script tries to download  [http://activex.microsoft.com/controls/vc/mfc40.cab](http://activex.microsoft.com/controls/vc/mfc40.cab)[/QUOTE]
that would be a problem with the maker of the link, or your internet connection...

---

### Post by aysiu on 2006-01-12
[QUOTE=504harry]
So Is this truely IE under Wine or is it something that behaves like IE - since I understood IE is one of Microsoft's flakey concoctions.[/QUOTE] It's truly IE under Wine. The whole point of Wine is the ability to use Windows applications in a Linux environment--they are the *actual* Windows applications, not imitations.

---

### Post by viscount on 2006-01-12
This is really fantastic, installing right now, hope it works :)
I know it's not really new technology after all I can remember
using IE on Linux with wine years and years ago, but its cool 
that you can just do IE by itself and have it "just work" so easily.

Great twist on an old idea.

---

### Post by kenweill on 2006-01-15
I can't install with the following errors:

Downloading everything we need ...
--13:47:19--  [http://download.microsoft.com/download/d/1/3/d13cd456-f0cf-4fb2-a17f-20afc79f8a51/DCOM98.EXE](http://download.microsoft.com/download/d/1/3/d13cd456-f0cf-4fb2-a17f-20afc79f8a51/DCOM98.EXE)
           => `/home/kenweill/.ies4linux/downloads/DCOM98.EXE'
Resolving download.microsoft.com... failed: Temporary failure in name resolution.
--13:47:19--  [http://activex.microsoft.com/controls/vc/mfc40.cab](http://activex.microsoft.com/controls/vc/mfc40.cab)
           => `/home/kenweill/.ies4linux/downloads/mfc40.cab'
Resolving activex.microsoft.com... failed: Temporary failure in name resolution.
--13:47:19--  [http://download.microsoft.com/download/win98SE/Update/5072/W98/EN-US/249973USA8.exe](http://download.microsoft.com/download/win98SE/Update/5072/W98/EN-US/249973USA8.exe)
           => `/home/kenweill/.ies4linux/downloads/249973USA8.exe'
Resolving download.microsoft.com... failed: Temporary failure in name resolution.
--13:47:19--  [http://www.mirror.ac.uk/mirror/ftp.evolt.org/ie/32bit/6.0/ie60.exe](http://www.mirror.ac.uk/mirror/ftp.evolt.org/ie/32bit/6.0/ie60.exe)
           => `/home/kenweill/.ies4linux/downloads/ie60.exe'
Resolving [www.mirror.ac.uk](www.mirror.ac.uk)... failed: Temporary failure in name resolution.
--13:47:19--  [http://fpdownload.macromedia.com/get/flashplayer/current/swflash.cab](http://fpdownload.macromedia.com/get/flashplayer/current/swflash.cab)
           => `/home/kenweill/.ies4linux/downloads/swflash.cab'
Resolving fpdownload.macromedia.com... failed: Temporary failure in name resolution.

---

### Post by kenweill on 2006-01-15
I have just solved my problem.

It was on my apt-get configuration.

> 
Setting up apt-get to use a http-proxy

gedit ~/.bashrc

add these lines to the bottom of your .bashrc file

http_proxy=http://yourproxyaddress:proxyport
export http_proxy

Save the file. Close your terminal window and then open another terminal window

Test proxy with sudo apt-get update and whatever networking tool you desire. I use firestarter to see active connections.

If you make a mistake and go back to edit the file again, remember to close the terminal and reopen it. It will not function with the new settings until you do. 


---

### Post by JimS on 2006-01-15
...
Glad you were able to solve your problem.

My question is: If your works look right Mozilla and Opera,
won't they also look right in IE?  I know the reverse is not
always true.

I do understand your need to make sure that they look
right in IE.  It would be nice if all writers would check
their works with at least 3 major browsers.

[COLOR="Blue"]JimS[/COLOR]
Prostate Cancer Aware
...

---

### Post by jnoreiko on 2006-01-15
[QUOTE=briancurtin]that would be a problem with the maker of the link, or your internet connection...[/QUOTE]

The maker of the link is the installations script....

---

### Post by sander marechal on 2006-02-07
[QUOTE=JimS]...
My question is: If your works look right Mozilla and Opera,
won't they also look right in IE?  I know the reverse is not
always true.[/QUOTE]

No. IE is a shoddy non-complient product. If you design on FireFox you can be pretty sure it runs well on Opera, Konqueor and a whole other group of browsers, but not IE. Same if you design on Opera, Safari, etcetera. The reverse is also true: If you design on IE you can be pretty sure that it will notr display properly on any non-IE browser (or any other IE version for that matter).

I did quite a few checks on the IE's that ies4linux provides. All the little CSS bugs, hacks, gotcha's and other webdesigner nightmare's are faithfully reproduced under Wine, so it's great for webdevelopment in Linux. I only noticed some discrepancies when using large, bloated DHTML libraries but since I do not use those anyway (and neither should any webdevloper IMHO) it's no biggie.

---

