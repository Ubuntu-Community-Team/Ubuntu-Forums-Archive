---
title: "[SOLVED] can i import archives from xp?"
date: 2008-07-12
forum: General Help
---

### Post by linuxn006 on 2008-07-12
I can't connect to the internet from my desktop(hardy heron installed).Can i download the .gz/tar etc. for video/audio codecs and run them on desktop after importing them from my laptop.Please post the download links as well :-)

---

### Post by boblemur on 2008-07-12
yes you can but im not sure what the link would be... 

download ubuntu-restricted-extras

but yes you can cause they are just .deb files

but im not sure exactly where you would get them from...

are you unable to get network(cant configure it)?? or do you not have a cable or something like that?

---

### Post by TenPlus1 on 2008-07-12
or you could simply goto [www.videolan.org](www.videolan.org) and download the latest version of VLC Player (the hardy .deb file) which will let you play all and any files without the need for separate codec downloads...

---

### Post by boblemur on 2008-07-12
thing is then you are still missing things like flash etc.. which are in ubuntu-restricted-extras, also java (dono if ud need this however)

---

### Post by jonlemur on 2008-07-12
Dude, your name is awesome bob.  I love it.

---

### Post by linuxn006 on 2008-07-13
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables


this is the error i get when i try using 

 ./config

So how do i fix the compiler issue

---

### Post by hyper_ch on 2008-07-13
vlc should be installed through the package manager

---

### Post by coffeecat on 2008-07-13
> **linuxn006 said:**
> I can't connect to the internet from my desktop(hardy heron installed).Can i download the .gz/tar etc. for video/audio codecs and run them on desktop after importing them from my laptop.Please post the download links as well :-)

Have a look at [Medibuntu]("http://www.medibuntu.org/") - a good place for codecs, multimedia stuff and other things. Have a look around the site. Don't bother with trying to add medibuntu to your sources.list - without internet connectivity that wouldn't help. Find the bit about downloading packages. You can download the .deb files, transfer them to your Ubuntu box onto your Desktop and install them simply by double-clicking on them.

Until you've had more experience with Linux, I suggest you **do not** try to install from tar.gz files. These are source-code and are provided for developers. You need the developer package to be able to compile and install them (which is not installed by default on Ubuntu) which is why you came up with the error message when you tried ./configure. The developer package for Ubuntu is 'build-essential'.

Your real problem seems to be the lack of internet connectivity in Ubuntu. If you had that you could download and install most of the apps you need from the Ubuntu repositories. No need to compile from source. What's the problem there? Can anyone help?

---

### Post by linuxn006 on 2008-07-13
Thanks for the tip coffeecat,i know adding to sources.list wont help.Yes, the real prob is that i cant connect to internet in ubuntu.But,i have searched and i could not find a solution for connecting with my "Starcom UT 330-r2u" ,others have connected via ethernet instead of USB but i dont have ethernet port,hence the prob remains.No hope it seems.

But i cant go around the "compiler cant create executables error" you mean?I was trying to configure the vlc .

---

### Post by coffeecat on 2008-07-13
Erroneous post removed - need to do some more research. Back in a bit. :)

---

### Post by coffeecat on 2008-07-13
**linuxn006**, sorry about that. I posted something that was misleading and needed to check something first.

Anyway, I strongly suggest you scrap that vlc tar.gz file for now. You're not going to be able to compile it without the developer tools and without ethernet you can't install them from the repository. Well, you can, but it's fiddly. And besides, if you do manage to compile vlc from source, it won't be optimised for Ubuntu, it may not appear in your menu and all sorts of other problems. The Ubuntu package for vlc has been compiled by the Ubuntu devs to 'just work' in Ubuntu.

I've had a look on the vlc site that TenPlus1 pointed you to. Unfortunately, you can't download a .deb file from there (not that I could find anyway). It merely tells you what to do with your package manager, for which you need internet.... :(

For the time being I suggest you go to the Medibuntu site I linked. You can't get vlc there, but you can get mplayer which is almost as good - perhaps better in some circumstances. You can also get the w32codecs package which will give you a lot of needed codecs.

Lastly, you say you do not have an ethernet port. Do you mean on your computer or on the router? There may be ways round your problem. Post details of why you can't connect with ethernet. No promises here but there might be solutions.

---

### Post by linuxn006 on 2008-07-13
Thanks a lot,for looking into this issue.Router has ethernet port,my comp does not.So,I connect via USB.The manufacturer only provides drivers for windows(.exe and .dll) .I haven't encountered anyone connecting via USB with  this modem in Ubuntu.Thanks again , but the only way around i found,was to connect via ethernet port,cant do that :-P

---

### Post by coffeecat on 2008-07-13
> **linuxn006 said:**
> Router has ethernet port,my comp does not.

I thought it might be something like that. I don't know what budget you have, but you can get USB > ethernet adaptors fairly cheaply. Most if not all work out of the box with Linux.

I bought one two or three years ago for an old (now defunct) laptop without ethernet that I was trying Linux out on. I was fairly new to Linux then and was somewhat dismayed to find a Windows driver CD in the box when I got home. Thinking I'd probably wasted my money I plugged it into the laptop (with Ubuntu Dapper) and with an ethernet cable to the router and I was connected to the internet without having to do anything else - just like that, no configuration at all. Lucky old me. :)

If you can find one and you can afford it, suggest you google for it first - add Linux to your search - and see if anyone else has had success with it. That might solve your problem.

---

### Post by linuxn006 on 2008-07-16
> **linuxn006 said:**
> i have searched and i could not find a solution for connecting with my "Starcom UT 330-r2u" ,others have connected via ethernet instead of USB but i dont have ethernet port,hence the prob remains.No hope it seems.

Like I said,i've searched for it,and instead of getting a usb > ethernet got myself a lan card :-) .So the package problem is now SOLVED. Thanx coffee cat for being a help .Check out this one too...:p

[http://ubuntuforums.org/showthread.php?t=857098](http://ubuntuforums.org/showthread.php?t=857098)

---

