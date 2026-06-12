---
title: "HP LaserJet P1005: install ok, no printing output though"
date: 2009-03-10
forum: Hardware
---

### Post by Ankersman on 2009-03-10
Just in case some of you have had this problem, after about 5 hours found the solution at:

[http://forums.linux-foundation.org/read.php?20,4643](http://forums.linux-foundation.org/read.php?20,4643)

Scroll down to post by JuanC, in particular note

" ...
5. Install
sudo make install

[B]6. Turn off the printer. Then turn it on.

7. Upload firmware to the printer
cat /usr/share/foo2xqx/firmware/sihpP1005.dl > /dev/usb/lp0
[/B]
The printer's LED should show a red light for some seconds. Wait until it becames green again.


8. Restart spooler
make cups

9. Now configre the printer (with the cups web interface,or whatever method). Make sure you select the proper driver.

10. Test it. It should work."  

works nicely!

---

### Post by dyingsun on 2009-03-21
Thanks for that Ankersman.
I'm having one little problem though:

This is the output from doing the cat in step 7:

bash: /dev/usb/lp0: Permission denied


Yes I switched it off and on again. I also tried it when it was switched off but of course the usb device wasnt found then. But at least I know its looking in the right place.

Any ideas how I can get permission? Tried with sudo too, btw.

---

### Post by dyingsun on 2009-03-22
Hi all, I fixed my problems, just had to tweak a couple of things. End result: My HP LaserJet P1005 is working perfectly on my Hardy installation, thanks to Ankersman's direction, and JuanC's of course!

Here's what I had to add:

After switching the power back on, I had to change ownership of lp0:

```
sudo chown damien /dev/usb/lp0
```

(substitute your userName in place of "damien", of course)
(Note: if you switch the printer off during the install process, you will have to repeat the chown command after turning it back on, as it wont remember.)

Then did the cat /usr/share/foo2xqx/firmware/sihpP1005.dl > /dev/usb/lp0

Also when making cups, had to do it with sudo.

```
sudo make cups
```

It also helps to make sure you're in the right directory when youre trying to do a make! (ie the one where you unzipped all your foo2zjs files.)
EDIT:   And make sure you've got ALL the orange packaging material removed - it turns up in some surprising places! If you can, run the little demo on the install CD, it shows you where everything is. I missed one spot, and the red light just kept flashing until I found the offending packaging.

Anyway, obviously I'm still a Linux noob, but if there's others like me trying to install one of these, that might help fill in the missing blanks. Hope it helps someone, would be nice to give back to this community in some small way :)

---

### Post by sunfire on 2009-03-24
I had same proplem that printer didn't do nothing. But it was recognised by Kubuntu 8.10.


Solved by:

"sudo hp-setup" and press enter untill install is done :p


hp-setup will update firmware..
Downloading firmware to device hp:/usb/HP_LaserJet_P1005?serial=BC0JV5J...
Firmware download successful.

---

### Post by altonbr on 2009-04-18
I can't seem to get it working...

Output of /var/log/cups/error_log> $ cat error_log 
E [18/Apr/2009:15:04:03 -0400] [CGI] Unable to scan "@LOCAL"!
E [18/Apr/2009:15:06:53 -0400] [CGI] Unable to scan "@LOCAL"!
E [18/Apr/2009:15:08:33 -0400] [CGI] Unable to scan "@LOCAL"!
E [18/Apr/2009:17:43:14 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [18/Apr/2009:17:43:19 -0400] PID 3975 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!
E [18/Apr/2009:17:43:39 -0400] [Job 1] Job stopped due to filter errors.
E [18/Apr/2009:17:44:35 -0400] cupsdAuthorize: Local authentication certificate not found!
E [18/Apr/2009:17:44:35 -0400] cupsdAuthorize: Local authentication certificate not found!
E [18/Apr/2009:17:44:35 -0400] cupsdAuthorize: Local authentication certificate not found!
E [18/Apr/2009:17:44:36 -0400] PID 4088 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!
E [18/Apr/2009:17:44:36 -0400] cupsdAuthorize: Local authentication certificate not found!
E [18/Apr/2009:17:44:36 -0400] cupsdAuthorize: Local authentication certificate not found!
E [18/Apr/2009:17:44:56 -0400] [Job 2] Job stopped due to filter errors.
E [18/Apr/2009:17:44:56 -0400] cupsdAuthorize: Local authentication certificate not found!
E [18/Apr/2009:17:45:15 -0400] cupsdAuthorize: Local authentication certificate not found!
E [18/Apr/2009:17:45:15 -0400] cupsdAuthorize: Local authentication certificate not found!
E [18/Apr/2009:17:55:07 -0400] PID 3504 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!
E [18/Apr/2009:17:55:27 -0400] [Job 3] Job stopped due to filter errors.

---

### Post by jigme on 2009-06-06
I just visited 
[http://forums.linux-foundation.org/read.php?20,4643](http://forums.linux-foundation.org/read.php?20,4643)

After installing HPLIP, you bust out the command

sudo hp-setup

Follow the yellow brick road to happiness.

Printer is now printing. And it feels goooood baby. It feels REAL good.

Sammy

---

### Post by storskogen on 2009-08-30
How do i know which driver to pick? I have several of them :(
I installed the foo2zjs driver

EDIT: Never mind, I installed the wrong printerdriver, i choose 1005 without P, with the right one it's working

---

### Post by santhust on 2009-11-01
hi,
first of all thanks a ton:guitar:

my printer is hp laserjet p1008. using ubuntu 9.10
it was not printing before, now it is. i followed the following steps:

1. went to link: [http://foo2xqx.rkkda.com/](http://foo2xqx.rkkda.com/)

followed the instructions there. everything went fine but: $ sudo gnome-cups-manager
didn't work,then

2. did: $ sudo hp-setup 
and follwed the instructions(just clicking: next->...)

and lo! it worked.

again thanks a ton:p:D

---

### Post by dedovoto on 2011-11-06
Hi Guys,

I've installed UBUNTU 11.10 recently and tried to install my HP 1005.

Here is what I found on the HP support site :
[B][SIZE=2]Ubuntu 11.04 supplies HPLIP 3.11.5 and it does support your printer.

As  the version of HPLIP supplied with your operating system supports your  printer, you may continue to use that version of HPLIP.[/SIZE][/B]

I performed the installation but the printer does not have an output, the message from HPLIP device status is output job completed...but nothing on paper though:(
Any ideas?
Thank you in advance!

---

### Post by jesewi on 2013-01-10
I've had the exact same issue with my HP LaserJet 1005 und Ubuntu 12.04.

Calling
[INDENT]     sudo hp-setup
[/INDENT]also solved it for me. It just wasn't working with the systems printer dialogue.

Thank you Sammy, following the yellow brick road to happiness
feels damn good indeed! ;)

Winni

---

