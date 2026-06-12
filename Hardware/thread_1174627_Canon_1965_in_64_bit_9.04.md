---
title: "Canon 1965 in 64 bit 9.04"
date: 2009-05-31
forum: Hardware
---

### Post by Ethelbert2 on 2009-05-31
[COLOR="DarkGreen"][FONT="Tahoma"]I am experimenting with x64 Ubunutu. My printer does not work properly and Googling I found that Gutenprint 5.2.3 is supposed to support it (Canon i965). A download is listed.  I downloaded that but have not done anything with it because I have Gutenprint in the distribution, I think. 

So I am confused, is this the same thing or do I need to download something specific for the Canon i965? When I use the GUI to set up a printer it only lists the Canon i865 and the driver produces weird colours on the 965. 

Could someone help (assuming I have given enough information)  Thank you.

PS I also found Turboprint 2 which claims to do i965.  But that would cost €30 - I could load the trial version (and om only experimenting at present so that is OK) but it I did that would I have to remove or disable other things? [/FONT][/COLOR]

---

### Post by coffeecat on 2009-05-31
Have you looked at the Open Printing site? Have a look at this page:

[http://openprinting.org/show_printer.cgi?recnum=Canon-i965](http://openprinting.org/show_printer.cgi?recnum=Canon-i965)

The download links for the various packages may very well be the same as you have already found, but I guess you need to download the 64-bit deb package if you haven't already. If you look at the "How to Install" link just after the driver links you'll see that you need to install the lsb package first, which is in the Ubuntu repos. The version with Jaunty is 3.2, so you'll have to make sure you download the appropriate deb package to go with this.

---

### Post by Ethelbert2 on 2009-06-01
[COLOR="DarkGreen"][FONT="Tahoma"]Firstly - many thanks.  I had looked at the instructions but being a relative Linux neonate I did not understand fully (mainly could not work out what I had and did not have already installed and what turns up in synaptic that matches the things listed. And whether I had to uninstall anything).

But I think I am going to switch to the 32 bit version. This is a shame because I like Ubuntu when it works and it does quite a lot quite well and better than the last time I tried around version 6.10. 

I finally made Xubuntu work on an older conmputer (using only 8.10 because otherwise I can't get Radeon 7000 video to work - a little limiting) but this installation is for my mainstream big machine and it has an Athlon 4800 x2 64 which seems worth taking advantage of. But I am also struggling to get an Epson 3170 scanner going which is important and Googling that indicates it might be easier with 32 bit.

I shall attempt your advice in 32 anyway. 

I have other questions relating to the scanner and to the video display (a newer Radeon card too) but suspect they are better done as separate posts. 

Thanks again
[I]
PS| Since this was also a 64 bit question should there be a way to link it to that forum thread?[/I][/FONT][/COLOR]

---

### Post by coffeecat on 2009-06-01
[COLOR=Black]One little hint. If I'm reading that "how to install" correctly, you simply install lsb (from the repos - using Synaptic) and then download the appropriate deb package and install that.

The hint is that once you've downloaded the deb package to your desktop, all you do is to double-click on it, type in your password where prompted, and let the magic of gdebi do the rest. (Even easier that Windows. :) ) If there are unmet dependencies it will tell you. Once a package is installed in this way it is listed in Synaptic and if you need to uninstall it, you can use Synaptic for this. Again - easier than Windows. :p

Good luck!
[/COLOR]

---

