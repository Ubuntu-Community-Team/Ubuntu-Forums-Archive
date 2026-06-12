---
title: "Printer Canon Pixma ip1800 Support"
date: 2007-05-16
forum: Hardware &amp; Laptops
---

### Post by caish5 on 2007-05-16
I have recently brought one, and its not working with fiesty. Does anyone have any ideas, solutions etc.

Thanks

Andy

---

### Post by caish5 on 2007-05-16
Shameless Bump!

---

### Post by bung33 on 2007-05-21
I've having the same problem too, but I'll Google it a little bit more and post a solution if I can find one...

---

### Post by bung33 on 2007-05-21
I found this link... [http://gentoo-wiki.com/Canon_Pixma_Series](http://gentoo-wiki.com/Canon_Pixma_Series). I know it's targeted for the Gentoo platform, but I figured that someone more experienced than I could figure out how to get the same concept working in Ubuntu. I'll take another look at it after work, and post again if I can finally get it working...

---

### Post by caish5 on 2007-06-09
Yeah i found that too. But i'm not THAT familar with linux.
Hopefully someone will come up with something soon, it's a pain having to shuffle files onto my windows pc every time i need to do a printout.

---

### Post by caish5 on 2007-06-12
Ok a little more investigating has led me to...

[http://www.canon.com.au/products/printers/colour_bj_printers/ip1800_support.aspx](http://www.canon.com.au/products/printers/colour_bj_printers/ip1800_support.aspx)

where there are linux drivers for opensuse and fedora. I've tried installing them with alien and it looked like it worked but still no printing.

Can anyone help?

Thanks 
Andy

---

### Post by icampana on 2007-06-19
I downloaded the drivers from the Australian Canon website, tweaking it a little bit with alien and repackaging the driver I got it working on Ubuntu (Feisty), it even has a configuration tool.  It needs a lot of patience till you get it right.

If anyone wants the driver, please let me know, I don't have a website right now to make it public, but at least I could send it through e-mail.  I tried to upload it here, but there is a size limit restriction, the driver is 1.8Mb

:p

Once the drivers are installed you should add the printer through the regular cups configuration, just make sure that you select the proper port (it creates a new one), it should appear as "USB Printer #1 with status readback for Canon IJ"

---

### Post by Pixtu on 2007-06-20
Hi icampana, 

Can you offer any more detail on the tweaking and 'patience' part of your solution. I have been having a similar problem with a Canon iP4300 and think I am close, the jobs get created in the print queue but don't actually print.

I have used Canon drivers from the Australian site, run them through alien to get deb packages and installed these. I can see the printer in System/Administration/Printing and can set up a new printer using the Canon USB (readback) device.

I am assuming that I am either mising a file/link or maybe its a permission problem.

---

### Post by exetera on 2007-07-28
hi icampana,
can you send me your driver please??
My mail address is [email]ninni.crisafi@gmail.com[/email].

Do you know if it works with ubuntu dapper too???

Thanks a lot.

---

### Post by DnLx on 2007-09-21
Hi, if you are looking for the drivers to the Canon Pixma IP1800 for Ubuntu Feisty 

**.DEB**
[cnijfilter-common_2.70-2_i386]("http://www.esnips.com/doc/3e8004c3-710c-4bf4-ac98-81f76e891df7/cnijfilter-common_2.70-2_i386")
[cnijfilter-ip1800series_2.70-2_i386]("http://www.esnips.com/doc/c30d6ff0-9a85-4aaa-8909-0a803d166cd3/cnijfilter-ip1800series_2.70-2_i386")

**.RPM**
[cnijfilter-common-2.70-1.i386]("http://www.esnips.com/doc/c5e483b2-9697-400e-805e-fa03397753bd/cnijfilter-common-2.70-1.i386")
[cnijfilter-ip1800series-2.70-1.i386]("http://www.esnips.com/doc/81c58e88-612f-4f0d-b932-b5d20327bb34/cnijfilter-ip1800series-2.70-1.i386")

**Or visit**
[My web]("http://www.esnips.com/web/jdferrufino-Ubuntu/")

---

### Post by profediego on 2007-09-28
Thanks Those drivers work perfectly with my canon ip1700 :KS

---

### Post by genti on 2007-10-15
Nice job, thanks.
I tried before with the Gentoo patches but it seems I did not install dhe driver but only dhe dependencies.
Now it is all set, printing works fine in Linux too :)

---

### Post by caish5 on 2007-10-20
Can anyone help make this printer work in Gutsy?

---

### Post by caish5 on 2007-10-20
Never mnid. These drivers do work, but for some strange reason i had to press the power button on the printer for it to start working. Now it seems fine.

---

### Post by dekeller on 2007-10-29
I have installed the print driver and everything looks fine until I print a page.  All I can
see is that the ip1800 printer has a job in the print queue but the job is stopped.  I can't
get it to resume.  When I look at the properties of the printer it shows

Status:      Ready: /usr/lib/cups/filter/pstocanonij failed

Any ideas?

Darryl Keller

---

### Post by cabaro on 2007-11-18
Hi

Is this thread still alive?

I've got Canon IP1800 and having problems getting it working,
I'm using Gutsy 64bit.

I tried installing the i386 driver with --force-architecture and i got Canon iP1800 series Ver.2.70 driver to show up, but it's not printing anything.

Could someone make a 64bit deb of this driver?

---

### Post by cabaro on 2007-11-22
Anyone?

Is there a way to get Canon ip1800 working in 64bit Gutsy?

As a temp solution i have winXP installed on Virtualbox and i do my printing through there.
It would be nice though to be able to print from ubuntu natively.

Thanks

/cab

---

### Post by biodiesel-bri on 2007-12-09
Same problem here - Gutsy 64 bit.  

I did some searching around and found a thread describing how to get this to work under AMD64 architecture.  Does anyone know how to pull this off under Ubuntu?
[http://gentoo-wiki.com/Canon_Pixma_Series](http://gentoo-wiki.com/Canon_Pixma_Series)

Thanks!

---

### Post by lupas on 2007-12-14
Someone have a driver for this printer ?

---

### Post by biodiesel-bri on 2007-12-14
32bit or 64bit?  People are reporting success with 32bit, but I and others can't get it to work with 64bit because the folks at Canon compiled for a 32 bit architecture.

I'm still hoping someone has a way around this - I'm dreading having to keep a Windows box around just to print some pictures!

---

### Post by cjhermann on 2007-12-24
I'm having dramas getting an iP1800 to work on Gutsy, 32 bit i386.
I've followed the instructions found here [http://ibr94.blogspot.com/2007/08/canon-pixma-ip1880-printer-in-ubuntu.html](http://ibr94.blogspot.com/2007/08/canon-pixma-ip1880-printer-in-ubuntu.html)

...and they work fine right up until the last step where for some reason I am asked to supply a password for localhost when applying the PPD. I'm not sure this is supposed to happen because I haven't found it mentioned in the instructions anywhere, and entering my password does not work, it simply asks me again and again. If I don't supply any password it says "Not Authorized".

I also get this when I try to delete the printer.

Help?

---

### Post by cjhermann on 2007-12-24
Never mind folks, I have solved my n00b dilemma.
Once I added myself to the lpadmin group it all worked perfectly - no more authorization request. :)

---

### Post by theharshone on 2008-01-10
Hi
I too need a 64bit gutsy driver. I can get the driver to show up and the printer detected, but it just wont print anything. Plz Help cuz now i have to boot into vista evrytime i want to print something and vista takes forever to boot.

---

### Post by 1467 on 2008-01-20
send me the drivers plz.

my email is [email]page1467@hotmail.com[/email]

---

### Post by biodiesel-bri on 2008-01-20
Anyone found 64bit drivers for the ip1800 yet?

---

### Post by biodiesel-bri on 2008-01-20
Doing some digging around I found this thread here:
[http://ubuntuforums.org/showthread.php?p=4173879#post4173879](http://ubuntuforums.org/showthread.php?p=4173879#post4173879)

Anyone know how to do what seemed to work in that thread?

---

### Post by biodiesel-bri on 2008-02-25
Bump!

---

### Post by tooCanad on 2008-03-13
I have two machines one a 32 bit. IP1800 working fine. The other is a 64 bit. Can't get the ip1800 it to work. Any suggestions?

---

### Post by biodiesel-bri on 2008-03-15
That's because Canon only released a driver for 32 bit, so my i1800 is a paperweight right now.  Unless someone out there knows how to get a 32 bit printer driver working under 64 bit?

:(

---

### Post by placa1783 on 2008-03-18
My sister have a low pc p2 6gb hd and 64+32 ram running windows 98. She lovs windows  and buy a Canon Pixma IP1800 with usb wire. the drivers are only 4 XP and i couldnt find a way to install it on win98. A friend told me that try CUPS.
How do i get a cups binari that has the driver of Canon Pixma IP1800 for win 98 or how do i get this driver and plug it to the cups?.
How do i instal cups on win?
THANKS VERY MUCH!! u can post here or send me a mail to [email]placa1783@gmail.com[/email]. If i found by my self the way ill post it here.

---

### Post by tooCanad on 2008-03-21
I got the IP1800 to work on my AMD 64 box the hard way. I installed 32 bit Ubuntu.

Maybe the next release will get us where we need to go.

TC

---

### Post by alex_anthony on 2008-04-19
Can anyone re-package the 32 bit drivers to work in hardy? libglib1.2 doesnt exist anymore

---

### Post by iwansetiawan on 2008-04-22
Thank's DnLx, the driver work perfectly on my feisty and gutsy 32 bit :D

---

### Post by Nhorning on 2008-04-24
Hey, I got it working in Hardy 32 bit by following the instructions in this link: [http://hex1a4.net/xubuntu/howto.php?htid=04](http://hex1a4.net/xubuntu/howto.php?htid=04)

I think in Gnome you don't have to do the cups stuff at the end.  I also had to manually install a couple of other drivers to satisfy dependencies but that may be a temporary issue.

---

### Post by aurelije on 2008-04-25
I have followed those instructions but I could not install cannon driver to Hardy. When I try to install cnijfilter-ip1800_2.70-2_i386.deb, I get message that libglib needs to be upgrade to libglib1.2ldbl (which I needed to remove in order to install libglib1.2).

Then I locked libglib1.2 and installed cnijfilter-ip1800_2.70-2_i386.deb, but package is broken :(

Sorry for my broken English :)

---

### Post by Nhorning on 2008-04-25
I don't know how much this will help, but I should mention that I completely uninstalled all previous versions of the drivers (as I had attempted this many times before)  

and that I only got this to work when I installed them using the command line.  When I did that, the dpkg made it apparent what dependencies were missing, so I was able to manually download and install those using google to get the thing to finally work. 

I also happened to uninstall libglib.2ldbl and a few others that seemed to be related to it before I installed the version of libglib1.2 found on that site.  I don't know whether that helped me or not.

---

### Post by jerryf70 on 2008-04-27
I've made some .debs for Hardy.  I converted RPMs to DEBs on a Hardy machine (which seems to avoid the libglib issue), and have added and adapted the scripts to put in the symlinks automatically (thanks to the person who first did this).

Please follow this link:

[http://home.btconnect.com/jerryf/]("http://home.btconnect.com/jerryf/")

Right clicking on the links and using "save as" should do the trick.

Usual caveats apply, this is my first attempt at making .debs, and was done on a beta Hardy install so your mileage may vary.  It works well for me, please let me know if it works on your install too.

---

### Post by aurelije on 2008-04-27
Thanks jerryf70, this driver works!

But it seems that it does not have all options from driver that I was using in Gutsy. There is no option for printing resolution, only 600 dpi, there is no option for economy, standard or any other printing mod...

---

### Post by jerryf70 on 2008-04-27
Hmmm - I'll take a look and try to work out why that is.  Thanks for the feedback.  Jerry

---

### Post by jerryf70 on 2008-04-28
Think I've sussed it.  The .ppd file needs editing as per the Gentoo link on page 1 of this thread.  I'll try to do this and upload in the next few days.  Jerry

---

### Post by DomZ on 2008-04-29
Cheers Jerry, the provided deb files work perfect on the final hardy release. I look forward to updated ones with the added functions :D

---

### Post by jerryf70 on 2008-04-30
Thanks DomZ.  I've uploaded new files which should allow the different resolutions etc.  In theory you should only need to replace cnijfilter-ip1800series_2.70-3_i386.deb.  I've changed the filenames (now 2.70-3) to make the difference clear.  If people could let me know if they work I'd be grateful.  As before URL is:

[http://home.btconnect.com/jerryf]("http://home.btconnect.com/jerryf")

Again, they work for me but I can make no guarantees as to whether they will work on other machines.  Cheers.  Jerry.

---

### Post by Benzil on 2008-05-16
Thanks Jerry, worked like a charm in 8.04 ;)

---

### Post by danniel on 2008-06-03
Did anyone manage to make it print **grayscale only**? I tried to use the Canon config tool which is installed in *System -> Preferences -> Canon Pixma* but it seems that the changes aren't saved.

Grayscale works fine from OpenOffice, but there are programs which do not have this option. So I need to configure the printer to use only the black cartridge.

---

### Post by biodiesel-bri on 2008-06-08
Thanks Jerry!  Our printer is no longer a paperweight thanks to you.

I just wish we could get it to work under 64 bit.

---

### Post by tet_letigio on 2008-06-24
sir,
thank you so much for the link. i have been searching the internet the whole day.

thanks a lot!
> **DnLx said:**
> Hi, if you are looking for the drivers to the Canon Pixma IP1800 for Ubuntu Feisty 

**.DEB**
[cnijfilter-common_2.70-2_i386]("http://www.esnips.com/doc/3e8004c3-710c-4bf4-ac98-81f76e891df7/cnijfilter-common_2.70-2_i386")
[cnijfilter-ip1800series_2.70-2_i386]("http://www.esnips.com/doc/c30d6ff0-9a85-4aaa-8909-0a803d166cd3/cnijfilter-ip1800series_2.70-2_i386")

**.RPM**
[cnijfilter-common-2.70-1.i386]("http://www.esnips.com/doc/c5e483b2-9697-400e-805e-fa03397753bd/cnijfilter-common-2.70-1.i386")
[cnijfilter-ip1800series-2.70-1.i386]("http://www.esnips.com/doc/81c58e88-612f-4f0d-b932-b5d20327bb34/cnijfilter-ip1800series-2.70-1.i386")

**Or visit**
[My web]("http://www.esnips.com/web/jdferrufino-Ubuntu/")

---

### Post by freddyg on 2008-06-29
thanks...Jerry??
worked like a charm, much much appreciated...now you can count one 70yr old lady (my mother) among the Ubuntu Newbies......I think she's already addicted to all the games Gnome has to offer!

---

### Post by blucht on 2008-07-06
Brilliant! These drivers work for my iP1700 as well.
After much searching and playing with drivers, it seems almost anticlimactic to have the working solution simply be a pair of dpkg -i. Thanks!

---

### Post by HyperHacker on 2008-07-07
> **Nhorning said:**
> Hey, I got it working in Hardy 32 bit by following the instructions in this link: [http://hex1a4.net/xubuntu/howto.php?htid=04](http://hex1a4.net/xubuntu/howto.php?htid=04)

I think in Gnome you don't have to do the cups stuff at the end.  I also had to manually install a couple of other drivers to satisfy dependencies but that may be a temporary issue.This isn't working for my ip1800. The last step fails: "Bad device-uri "cnij_usb:/dev/usb/lp0"!"

---

