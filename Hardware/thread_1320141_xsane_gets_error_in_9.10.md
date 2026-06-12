---
title: "xsane gets error in 9.10"
date: 2009-11-08
forum: Hardware
---

### Post by Lary Grant on 2009-11-08
I was using xsane fine for scanning on my Brother MFC210C in Ubuntu 9.04.  After doing a fresh install on the same machine to 9.10 and reinstalling the Brother drivers, xsane no longer works (although printing is fine).  When I click Scan, I get:

failed to start scanner: invalid argument

What now?

---

### Post by newbymick on 2009-11-09
Same here - xsane fails to be found :mad:

---

### Post by manolomanolo on 2009-11-11
Same problem.

After upgrading from Ubuntu 9.04 to 9.10, the scanner stoped working.
Then I removed the previous version of brscan3 e brscan-skey and installed the newer versions, just downloaded them from the Brother official website.

I'm still unable to access to my scanner, getting the same error I got before updating the scanner drivers:

[INDENT]Failed to start scanner: Invalid argument[/INDENT]

Any suggestion, please?
Thank you.

---

### Post by ADBrown85 on 2009-11-11
I was having a similar problem with XSane yesterday.  According to Oliver Rauch, the author of XSane, the SANE team has changed some things in the latest release of the backends that breaks compatibility.  This was posted on the XSane web site in February...

 "If you experience any problems with XSane and sane-backends with a version number greater than 1.0.19 then this may be caused by an incompatible development of sane-backends.  In this case it may be worth to try sane-backends-1.0.19 or earlier.  XSane is and will keep compatible to the original SANE-1.0 standard. I will not spend any time for incompatible things that will mess up everything."

 Indeed if you look at the version numbers in Jaunty libsane is 1.0.19, whereas the one in Karmic is 1.0.20, so I suppose this kind of makes sense.

 I went into Synaptic and removed xsane and its dependencies, then installed older versions from source.  Now things are working again with my Canon scanner!

 Download from:
    [http://www.sane-project.org/source.html](http://www.sane-project.org/source.html)
    [http://www.xsane.org/xsane-download.html](http://www.xsane.org/xsane-download.html)

 Hope that helps you guys too!

---

### Post by manolomanolo on 2009-11-11
I removed xsane, libsane and their dependencies then installed the older versions from here:

[http://packages.ubuntu.com/jaunty/libsane]("http://packages.ubuntu.com/jaunty/libsane")

Notice that page has a search field on the right-upper part and you can also choose your OS version (jaunty, in our case).

Unfortunately, the poroblem has not been solved.

---

### Post by DWM1 on 2009-11-13
[FONT=Courier New]Hello,

I have just abandoned Windows Vista in favour of Ubuntu and I must say it is a revelation. My system is now quick!

By moving from Windows, it seems, I am trading off supportability for my Epson Stylus SX400 All in One printer.

The printer works fine but the scanner does not. Epson do not offer any support.

I have followed the advice at the Ubuntu 9.10 Scanning web page; [https://help.ubuntu.com/9.10/printing/C/scanning.html](https://help.ubuntu.com/9.10/printing/C/scanning.html)

From that resource I have determined that my scanner or printer is not supported and a manual installation has not been successful either. I am aware that there might be some workaround from other internet resources like the following one that I have used without success;

[http://blog.bluemonki.net/2009/03/28/ubuntu-epson-sx400-all-in-one-making-it-work/](http://blog.bluemonki.net/2009/03/28/ubuntu-epson-sx400-all-in-one-making-it-work/)

My lack of success has led me to this forum.

My computer is an HP G70 laptop, I can supply the output from the lshw command if necessary.

When I run 'xsane' (ver. 0.996), a dialogue box pops up with a top line menu- File/Preferences/View/Window/Help. I click 'Scan' and get the following error message;

"Failed to start scanner: Invalid argument".

I have not specified any arguments when running the application from xwindows.

When I run the application from a terminal, I get the following;

WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

(xsane:3472): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

The last line repeats many many times before the terminal becomes available to use again and 'xsane' runs from the xwindows system.

Please can anyone help as I urgently need to scan, email and fax some documents to friends and colleagues?

Thank you in advance, I apologise for my newness to Ubuntu and in the event that this issue has been resolved elsewhere through the forums.

Duncan Moore.








[/FONT]

---

### Post by manolomanolo on 2009-11-13
Hi Dunkan.

Unfortunately I'm not the best person to give you help: my problems with xsane persist.
Just a comment: no need to write you need an urgent solution. No one will delay in case he/she knows how to help.;)

On the other hand, it could be more useful to get possibly the threat "up" every now and then providing more infos about your tests.

Have a nice day :KS

---

### Post by AlexDudko on 2009-11-13
After upgrading to Ubuntu-9.10 I also suffered this problem, but following the instructions from [brother site]("http://solutions.brother.com/linux/en_us/instruction_scn1c.html#u9.10") it was solved.

---

### Post by manolomanolo on 2009-11-13
Each time I look for infos on Brother web site I always ask how come I'm unable to find the requestion information they publish. I wonder whether they take in account the usability of websites...

That solution posted by **AlexDudko** didn't worked for me anyway.

**@AlexDudko**: which version of **libsane** and **brscan** are you using?

**@DWM1**: does that solution work for you?

Thank you.

---

### Post by DWM1 on 2009-11-13
Hello,

I'm sorry to manolomanolo if me saying that I urgently needed to scan caused any offence. I said it just because it's true and not because I feel more important or by virtue of trying to attain a quick response.

Having said that, you guys are quick aren't you? It's my first time on the forum.

Thanks to AlexDudko, my problem is solved!

I added the following lines to the 'rules' file as suggested, then rebooted and 'xsane' started working straight away! Wow!

# Epson SX400 scanner
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="084a", ENV{libsane_matched}="yes"

I got the vendor and product attributes from the terminal output of command 'sane-find-scanner', but you knew that already.

I gather therefore that the 'rules' file is a set of parameters for the enablement/recognition of the hardware at the time the universal device library is loaded into sofware and when 'xsane' runs and calls it's dependencies!?!?!?

Thank you all very much, my problem is solved!

Kind Regards,

Duncan Moore.

---

### Post by manolomanolo on 2009-11-13
After trying to make it work adding the line suggested by AlexDudko, I decided to extend it in the form as shown by DWM1, so that finally the line at the bottom of /lib/udev/rules.d/40-libsane.rules at the moment is:

```
# Brother scanners
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0206", ENV{libsane_matched}="yes"
```

But it still doesn't work.
By the way, my device is Brother DCP-145c (multifunction, printer and scanner).

---

### Post by manolomanolo on 2009-11-13
Also, I had no group named "scanner" on my system: I added it and also I added my user to that group but the problem persists.

Also:

```
 scanimage -L
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
device `v4l:/dev/video0' is a Noname Acer Crystal Eye webcam virtual device
```

---

### Post by DWM1 on 2009-11-13
[FONT=Courier New]Hello again,

I have not exactly worked out why I got it working but I can say how.

From my original post, I did all of the activities in blue monkey and then the ubuntu help links and in that order. I also installed and reinstalled xsane a few times from the ubuntu software centre and terminal, with associated reboots. Then I followed AlexDudko's advice and it worked.

I am not sure how relevant the last few steps are of the blue monkey link, where the shell script is created. This might be my ignorance.

Might I suggest you regress your system back to the very beginning and start again?

Best of luck,

Duncan.[/FONT]

---

### Post by manolomanolo on 2009-11-13
Well, the blue monkey link is Epson related (my scanner is Brother).
Also, that page from Ubuntu Help is quite old. the list of supported scanner is still the one when Ubuntu "Edgy" was released (some years ago...)

So, at the moment, no solution for me.

Thank you all.

---

### Post by AlexDudko on 2009-11-13
> **manolomanolo said:**
> Well, the blue monkey link is Epson related (my scanner is Brother).
Also, that page from Ubuntu Help is quite old. the list of supported scanner is still the one when Ubuntu "Edgy" was released (some years ago...)

So, at the moment, no solution for me.

Thank you all.

Can you use your scanner if started by administrator?
> sudo xsane

P. S. I use default packages installed with the OS.

---

### Post by manolomanolo on 2009-11-13
CASE A) This is what happens when I press CANCEL when the program advices "run xsane as root at your own risk":

```
manolo@manolo-laptop:~$ sudo xsane
/usr/share/themes/Dust Sand/gtk-2.0/gtkrc:289: Invalid symbolic color 'selected_fg_color'
/usr/share/themes/Dust Sand/gtk-2.0/gtkrc:289: error: invalid identifier `selected_fg_color', expected valid identifier

```

CASE B) On the other hand, when pressing on the "CONTINUE AT YOUR OWN RISK" button the program starts. Then after pressing on the SCAN button I get the error "Failed to start scanner: invalid argument". That thing seems quite normal to me, since on the title bar of xsane it reads "xsane 0.996 Acer Crystal Eye". Notice: Acer Crystal Eye is my webcam... not my scanner! So I quit xsane.
That's the output on terminal during all of the operations described on this CASE B)

```
[sudo] password for manolo: 
/usr/share/themes/Dust Sand/gtk-2.0/gtkrc:289: Invalid symbolic color 'selected_fg_color'
/usr/share/themes/Dust Sand/gtk-2.0/gtkrc:289: error: invalid identifier `selected_fg_color', expected valid identifier
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

(xsane:3643): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3643): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:3643): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

[INDENT]*[the same warning message is repeated 24 times more]*[/INDENT]
manolo@manolo-laptop:~$ 
```

---

### Post by AlexDudko on 2009-11-14
I saw a thread where a webcam was recognized as a scanner but unfortunately don't remember the workaround and can't find the thread. Try using search.

---

### Post by manolomanolo on 2009-11-18
Still no suggestion?

---

### Post by manolomanolo on 2009-11-18
Purged the previously installed driver and re-installed them from scratch.

After following the installation options, the result is:


```
lsusb | grep Brother
Bus 008 Device 004: ID 04f9:0206 Brother Industries, Ltd
```

```
dpkg  -l  |  grep  Brother
ii  brscan-skey         0.2.1-3     Brother Linux scanner S-KEY tool
ii  brscan3             0.2.7-1     Brother Scanner Driver
ii  dcp145ccupswrapper  1.1.2-2     Brother CUPS Inkjet Printer Definitions
ii  dcp145clpr          1.1.2-2     Brother lpr Inkjet Printer Definitions
```

```
brscan-skey -l
             
```


Notice, the ***brscan-skey -l*** command gave an empty result.

---

### Post by manolomanolo on 2009-11-19
SOLVED.

Brother technical support center suggested to follow the instructions at the following link:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#6]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#6")

Now I can see my scanner, even if I suppose I've been following those advices some days ago with no success.
Anyway, now I can scan with Xsane.

```
brscan-skey -l

 DCP-145C          : brother3:bus2;dev1  : USB                  Not registered

scanimage -L
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
device `brother3:bus2;dev1' is a Brother DCP-145C USB scanner
device `v4l:/dev/video0' is a Noname Acer Crystal Eye webcam virtual device

```

Thank you

---

### Post by Cresho on 2009-12-01
I was getting segmentation fault with the xsane packages installed from karmic.  I removed libsane, xsane, xsane-common and installed the ones from hardy and they work.  I havent tried jaunty like some of you guys have.


libsane_1.0.19-1ubuntu3_i386.deb
xsane_0.995-1ubuntu1_i386.deb
xsane-common_0.995-1ubuntu1_all.deb

from

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Haxor on 2009-12-11
Hey Cresho,

I will be trying your fix, but I am not sure if the problem is xsane or sane.
Any clues?
I have a Benq 5000 scanner with the correct firmware.

Do you know if this has been already posted as a bug?

Warper

---

### Post by raunhar on 2010-03-27
How to know if the firmware is correct or need updation.

Also how to update the firmware.

---

### Post by AOB on 2010-06-06
I am new to Ubuntu 10.04 and trying to setup my BROTHER DCP145C multi-printer/scanner/copier so that I could try and use it. Any A-Z help from you experts will be much appreciated.

---

### Post by AlexDudko on 2010-06-08
Have you tried to use google/forum search before posting? Have you read anything like this:
[http://ubuntuforums.org/showthread.php?t=1090274](http://ubuntuforums.org/showthread.php?t=1090274) ?

---

### Post by luigi_mb on 2010-06-08
There is a very relevant and useful article in the July 2010 issue of Linux Journal ("Adventures in Scanning" by Dirk Elmendorf", p28). 

/luigi

---

### Post by AOB on 2010-06-13
Mind telling me what have you done step by step. I just bought DCP145C and installed Ubuntu 10.04 and would like to connect my printer up. Best email me at [email]alexong2005@yahoo.com.sg[/email]

---

