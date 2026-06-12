---
title: "Intel GME 82852/82855 resolution hack"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by Aahz on 2006-11-02
Hello! Before I dig into the problem, let me say that this is the first time ever in my life on a linux system, and so I'm a real, real newbie.

I installed Ubuntu on my Acer Travelmate 660 laptop just fine. Ubuntu even detected the graphics controller, which is an Intel 82852/82855 chip. However, Ubuntu is not letting me change the resolution that the LCD supports natively, which is a 1400x1050. The highest I can get by default is 1280x1024.

So while reading through [www.ubuntuguide.org](www.ubuntuguide.org) I found this:

>  How to Correct the Graphics Resolution (Intel)

    * Read #How to enable Large Widescreen Support if you have a larger (>20") monitor 

    * Intel 915g, 945g, etc. graphics chipsets only have a limited set of resolutions initially installed, despite the correct driver being detected.
    * Install the resolution altering tool: 

sudo apt-get install 915resolution


Bingo - I thought! The programm installed itself just fine, and through the lots of junk that the console spit at me I noticed this line:" Changed mode L6 to 1400x1050". "Wow - smart cookie, this program" -  I thought. 

The next step in the guide is as follows:

>     * Run the following to see the availible modes: 

915resolution -l


I paste 915resolution -l command into the terminal, and I get the following message:

"Intel 800/900 Series VBIOS Hack : version 0.5.2

Unable to obtain the proper IO permissions: Operation not permitted"

I figure there is some sort of user rights problem, but as a *nix newbie, I've got absolutely no clue how to change the rights to a program. If anyone could help, it would be greatly appreciated!!

~Aahz.

---

### Post by endersshadow on 2006-11-03
```
sudo 915resolution -l
```

When prompted, just enter in your normal password.  Sudo is the command to have root privileges.  Welcome to the wild world of Linux!

---

