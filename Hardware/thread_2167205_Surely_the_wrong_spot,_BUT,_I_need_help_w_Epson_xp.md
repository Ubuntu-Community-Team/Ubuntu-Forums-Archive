---
title: "Surely the wrong spot, BUT, I need help w Epson xp-200 printer and ubuntu 12.04"
date: 2013-08-12
forum: Hardware
---

### Post by rob10 on 2013-08-12
Hi, brand new here & I apologize if this query could have been better placed. 

I am using ubuntu 12.04 with a google chromebook c7 & I just bought an Epson xp-200 printer. I'm really hoping I can get this working, but I haven't the first idea where to begin.

Any thoughts?

Thank you.

---

### Post by ibjsb4 on 2013-08-12
I do not have one, but sounds like all you need is the drivers.

[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

[http://ubuntuforums.org/showthread.php?t=1671378](http://ubuntuforums.org/showthread.php?t=1671378)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Epson+xp-200&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Epson+xp-200&sa=Search&cof=FORID:9)

---

### Post by rob10 on 2013-08-12
Yes, I need the drivers. Apparently I've already downloaded them from the Espon site, but what do I do with them?  It looks to me like it's file after file after sub-file of stuff that I don't have any idea what to do with. In my ignorance, I was hoping to download a driver, find an 'install' button and be guided through the set-up. No such luck.

Please advise.

Thanks.

---

### Post by ibjsb4 on 2013-08-12
Ok see what you mean :)

Do you have ubuntu 32 or 64 bit installed?

The package for 32 bit is "i386.deb"

And for 64 bit its "amd64.deb"

You just need one of those two packages.  After you download it, just double click on it and the software center should take over.  Please post back if you have more questions.

---

### Post by QIII on 2013-08-12
*Moved to **&#8203;Hardware***

---

### Post by rob10 on 2013-08-13
Thanks for the advice.

So close! I tried the[COLOR=#000000] "i386.deb" download and at first it really seemed to be responding, but last minute I got "[/COLOR]Package operation failed - The installation or removal of a software package failed." Then, when I close that report, I get "Items can not be installed or removed until the package catalog is repaired. Do you want to repair it now?"
I will hit yes here and get - Failed to satisfy all dependencies (broken cache).

Any ideas?

Thanks.

---

### Post by rob10 on 2013-08-13
Anybody there? I'm wondering if I should return this printer. Might 'Wine Windows Program Loader' help at all? Is there another brand of printer that would suit Ubuntu better?
Really need help. Thanks.

---

### Post by ibjsb4 on 2013-08-13
Try the generic tar.gz package.

[ATTACH=CONFIG]245346[/ATTACH][ATTACH=CONFIG]245347[/ATTACH]

---

### Post by rob10 on 2013-08-13
Thanks for the suggestion.

I downloaded that version, but it's behaving the same way as my first attempts. When I open it, it's simply a huge list of folders, such as:

debian
lib
lsb
m4
ppd
src

and then
 tons of text files. 

There is one exception; an icon entitled "INSTALL", but it also turns out to be a very long text file.

I am stuck.

---

### Post by ibjsb4 on 2013-08-13
Ok, I have played with this .deb file and found a way to load it.

Place the .deb folder in your home directory and run the following [command in terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal").

```
sudo dpkg -i epson-inkjet-printer-escpr_1.2.3-1lsb3.2_i386.deb
```

I am assuming this is the same .deb package you downloaded.

I cannot tell from that point on what will happen since I do not have an epson printer or cups installed on this box.

Hope that helps :)

Edit:  Again I ask, are you running 32 bit ubuntu?  If not sure, you can check in terminal.

```
uname -a
```

---

### Post by rob10 on 2013-08-15
Thanks, ibjsb4
[COLOR=#DD4814][COLOR=#000000]
I tried that, but no avail. 

What I did do was finally go back and just try more of the driver they had to offer. It turns out I needed on of the 64 bit drivers, and thanks to you I was able to figure this out. 

All good now. 

Thanks!
[/COLOR][/COLOR]

---

### Post by rob10 on 2013-08-28
Sooooo. All WAS good, then I upgraded to 13.04 and now I have lost all connection between my printer and computer. SHould this make sense?

---

### Post by QIII on 2013-08-28
Hello!

It may make sense, depending on how you finally managed to install the driver before.

When you upgraded to 13.04, you got a new kernel.  There is a way to carry forward all of your previously installed packages if you save a list of them first, but I don't know if you did that.  And I'm not sure this particular one would have been included in that anyway.

Be that as it may...

Have you tried reinstalling the driver as you did before?

---

### Post by eternal243 on 2013-08-28
Actually, have you tried just installing cups? About a year ago I setup a printing server on my home network using cups and samba, and cups had loads of pre-installed drivers, even for my printer that didn't have an official linux driver from the manufacturer. It might make your job much easier. =)

**EDIT: **When you unpacked the tar.gz file earlier, there was a PPD file, this is the actual driver file, and it can be imported directly into cups if cups doesn't have your driver pre-installed!

---

