---
title: "Crossing the Black Chasm (537EP modem)"
date: 2006-04-26
forum: Hardware &amp; Laptops
---

### Post by Coburn on 2006-04-26
I'm trying to set up an Intel 537 EP softmodem.

Driver does not compile but exits <make 537> with errors.  [http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)
](*,)

<apt-get install build-essential linux-headers 'uname -r'> returns that build-essential is already there, linux-headers is not installed, and no such file as uname -r exists.  I used Synaptic to install build-essential and linux-headers off the CD.  Using dual boot WinME, so any other source of files beyond the CD is complicated, and sometimes beyond my knowledge. 

Plus I have gcc 3.4, per the Ubuntu Dialup modem HowTo, _and_ 4.0 (default) installed.

I am assuming I don't have to actually use the kernel_source, since the headers are on the 5.10 install CD.  But then again 537 won't compile.

(Rant:  I'm kind of wierded out by all this.  Something as basic as an Intel softmodem, especially considering that Ubuntu is aiming at the international (read "broke") market, should be maximally supported, i.e. it should Just Work.  And/or the documentation should give the Ubuntu Way.  Not at all the case.  

In fact, I am finding myself gradually, inexorably driven into a wilderness where I had no wish to go, viz., compiling from source, downloading using my dual boot WinMe, reading bad documentation by Leroy Brown, looking at kernel configuring, etc.  I am quite confused, and though new at Linux, I have been tinkering with computers since the TRS-80.)

In short, why can't I get the driver to compile by following the instructions in the Ubunto HowTo?  

Basic background:
5.10 Breezy on one 40G drive, WinMe on the other.
AMD 2Gig chip
Intel 537EP modem using about 28.8 dialup (through Windows only)
Got Breezy ISO on my neighbor's cable connection.  Also now have shipped CD's.
Experience w/ TRS-80 BASIC, 8086 assembler commands, Apple IIe, Windows 3.1, 95, Me, 2K, and XP, and WinWord/OOo in-depth use.  Wannabe Linux user since this year.




Coby

---

### Post by chuckman78 on 2006-07-09
Hi, Coburn.

I hope this helps:

[http://www.ubuntuforums.org/showthread.php?t=210405&highlight=537ep]("http://www.ubuntuforums.org/showthread.php?t=210405&highlight=537ep")

Regards,

Carlos.

---

### Post by Coburn on 2006-08-20
Thanks.  Your HowTo is helpful (see my post).  This whole thing of having to program my way onto the Internet has been a baptism of fire for me.  Now I am quite comfortable with using terminal to get my way.  Not real sure why it has to be that way, but it has its plusses.  God is nice to me.

Thanks

---

### Post by enopepsoo on 2006-08-20
> **Coburn said:**
> I'm trying to set up an Intel 537 EP softmodem.
<apt-get install build-essential linux-headers 'uname -r'> returns that build-essential is already there, linux-headers is not installed, and no such file as uname -r exists.  

Hello, welcome to the wonderful world of dial up modems in linux!

Your error here is caused by using single quotes, like this ', instead of back quotes, like this `.

That's the one at the top - left of the keyboard.  Using that will put in the output of the command.

Happy compiling.

---

