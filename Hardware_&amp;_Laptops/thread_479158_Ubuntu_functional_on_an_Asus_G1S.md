---
title: "Ubuntu functional on an Asus G1S?"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by (chubbstar) on 2007-06-20
Hi all, 

I'm looking to buy a wonderful new Asus G1S laptop and I want to know what level of Ubuntu compatibility it has. I'm obviously thinking about buying this laptop so as to have gaming as an option but I dont want to use XP any more than I have to.

So, in short, do things like wireless and bluetooth work? The built in camera? Is the top end nVidia GeForce 8600MGT video card fully unleashed? If anyone knows the answers to these questions or knows where I may be able to find them I would be very grateful.




For convenience, the specs for the Asus G1S:
[HTML]http://ca.asus.com/products.aspx?l1=5&l2=61&l3=416&l4=0&model=1674&modelmenu=2[/HTML]

---

### Post by (chubbstar) on 2007-06-21
does this lack of response mean that the question is stupid or that no one knows?

---

### Post by Krischi on 2007-06-25
This thread indicates that it is at least possible to get the laptop to work:

[http://ubuntuforums.org/showthread.php?t=471311](http://ubuntuforums.org/showthread.php?t=471311)

 Keep in mind that this laptop is still very new, so there are probably going to be a lot of warts. You will definitely have to compile some stuff yourself. The good news is that hardware support is bound to improve very quickly - for instance, NVidia recently released drivers that support the GeForce 8xxx M series, and Intel  is actively developing the wireless driver for the 4965 chipset (search for iwlwifi).

A friend of mine is expecting to receive this laptop in around 10 days from now, and I plan to get it myself once I return to the USA in July. If I find time, I will report then.

---

### Post by shil on 2007-06-25
i have sucessfully installed gentoo linux on the asus g1s with great performances using the latest nvidia driver(11.000 fps with glx gears before composite and 7500 after) and wifi working (with a couple hickups but working), today i'm trying ubuntu and will report here later

---

### Post by Krischi on 2007-06-25
That is excellent news. I actually switched to Kubuntu from Gentoo, because I got fed up with the long maintenance cycles, but if all else fails, this would at least tide me over.

---

### Post by Adamal on 2007-06-25
> **shil said:**
> i have sucessfully installed gentoo linux on the asus g1s with great performances using the latest nvidia driver(11.000 fps with glx gears before composite and 7500 after) and wifi working (with a couple hickups but working), today i'm trying ubuntu and will report here later

Have you gotten the CD/DVD Rom drive to work.  Mine currently does not mount.  I was able to install from it, but for whatever reason it no longer works.

---

### Post by Syke on 2007-06-26
> **Adamal said:**
> Have you gotten the CD/DVD Rom drive to work.  Mine currently does not mount.  I was able to install from it, but for whatever reason it no longer works.

I have a new Asus laptop very similar to the G1S. Text-mode installer works, but live cd doesn't. And after Ubuntu is installed to the hard drive,  it cannot access the cd-rom. Did you use a text-based installer?

---

### Post by Adamal on 2007-06-26
> **Syke said:**
> I have a new Asus laptop very similar to the G1S. Text-mode installer works, but live cd doesn't. And after Ubuntu is installed to the hard drive,  it cannot access the cd-rom. Did you use a text-based installer?

Yes I used the text based installer and the same thing happened.

---

### Post by Syke on 2007-06-26
Woot, found the fix for my model. I bet it works on yours too.

[http://ubuntuforums.org/showpost.php?p=2883308&postcount=11](http://ubuntuforums.org/showpost.php?p=2883308&postcount=11)

Add:

piix

to /etc/modules

Now I can read CDs and DVDs. I haven't tried burning yet, but I expect it'll work.

---

### Post by Krischi on 2007-06-26
My understanding is that this is a kernel bug, so it probably won't be necessary to keep this line in /etc/modules in the next release of Ubuntu.

---

### Post by shil on 2007-06-26
well the installation didn't go as well as i hoped, had problems at the beginning and had to follow [this link's]("http://ubuntuforums.org/showthread.php?t=421588&highlight=tty+job+control") instructions to get in the livecd and what to do after the install (it's important otherwise it won't boot correctly)
then had to run in safe graphics mode because the nv driver doesn't support the graphics card for that i'll probably have to install [envy](http://www.albertomilone.com/nvidia_scripts1.html) and the latest drivers

had pretty much everything working with a couple big exceptions, ethernet adaptor (i think i will need to modprobe r8169, this is the module i use in Gentoo and it must be the same for Ubuntu) and the wireless 4965 adaptor, which i wasn't expecting to work out of the box because it will either need the lastest iwlwifi, iwlwifi-ucode and mac80211 releases that are pretty recent and unstable (at least with NetworkManager) or ndiswrapper to install windows drivers.

post for iwlwifi: [http://ubuntuforums.org/showthread.php?p=2873289](http://ubuntuforums.org/showthread.php?p=2873289)

post for ndiswrapper: [https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty](https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty)

there are a couple things that worked flawlessly in Ubuntu, the keyboard was fully supported including the multimedia keys, i've been struggling a lot for these in Gentoo. and the rest of normal features we get with Ubuntu.

i had to delete the partition so i would not be tempted to fix all of the above, i'm currently in exams and can't afford to do more than just a sneak peak, but i believe Ubuntu or any of the other flavors fully support the Asus G1S by following a couple howtos, which i'll do after my exams.

@Krischi i have to disagree with you on the long maintenance cycles... actually that's something that doesn't exists in Gentoo as far as i know, everything is installed individually ,and not limited by that release's repository, and works pretty good with excellent performances as a whole, Ubuntu and other distributions have major releases from time to time with limits what can be installed but by doing that they guarantee to a certain point that everything that is on that release's repository works.
i'm not tired of gentoo, i just miss the gnome desktop and ubuntu has the best tweaking for it. So instead of installing it on Gentoo i'll have a different distribution sharing my home directory

PS: post to get the nvidia 8600 working with envy [http://ubuntuforums.org/showpost.php?p=2898390&postcount=3](http://ubuntuforums.org/showpost.php?p=2898390&postcount=3)

---

### Post by (chubbstar) on 2007-06-29
thanks alot for your input shil. im still quite low on the linux-tweaking totem pole so i dont know how much manual maintenance ill be able to successfully complete for sometimes even simple walkthroughs screw up on my ancient dell (most likely due to a user error). heh. 

nonetheless, i am still going to buy me this laptop knowing full well that eventually there will be great support for it. ill check back frequently to check the progress on that. im still going to install ubuntu and do what i can with it because frankly, i DO NOT want to even touch vista. 

as a side, and i know this will be entirely speculative, but how long do you think it will be until support for the asus g1s is in full force?

---

### Post by Adamal on 2007-06-29
> **(chubbstar) said:**
> thanks alot for your input shil. im still quite low on the linux-tweaking totem pole so i dont know how much manual maintenance ill be able to successfully complete for sometimes even simple walkthroughs screw up on my ancient dell (most likely due to a user error). heh. 

nonetheless, i am still going to buy me this laptop knowing full well that eventually there will be great support for it. ill check back frequently to check the progress on that. im still going to install ubuntu and do what i can with it because frankly, i DO NOT want to even touch vista. 

as a side, and i know this will be entirely speculative, but how long do you think it will be until support for the asus g1s is in full force?

My money would be on Ubuntu 7.10

---

### Post by shil on 2007-06-30
yes 7.10 will probably get a nice support out of the box as the drivers for the wireless adapter became stable, the same applies with the graphics card, but that doesn't necessary mean that you will have to wait till october, i've used "daily releases" before and never got any problems wink

---

### Post by Adamal on 2007-06-30
> **shil said:**
> yes 7.10 will probably get a nice support out of the box as the drivers for the wireless adapter became stable, the same applies with the graphics card, but that doesn't necessary mean that you will have to wait till october, i've used "daily releases" before and never got any problems wink

As of right now the 8600 GT is not supported on the latest alpha of Gusty.  The wireless doesn't work and the CD doesn't work.  The same thing as 7.04

---

### Post by ehmdjii on 2007-07-01
i also tried to run the live cd with the hint given above.
however it then says it cant run the x server cause its not set up correctly and brings me to a console.

how can i set it up correctly or how can i start this safe graphics mode?

---

### Post by ehmdjii on 2007-07-01
ok, i got it running now, also the envy nvidia drivers work fine!

only thing that remains are the wifi drivers. does anyone have any successful experiences with wifi on an asus g1s? if so, which driver did you install? ndiswrapper or iwifi?

thanks!

---

### Post by shil on 2007-07-01
good news about the graphics card, i've got the wireless iwlwifi in gentoo, after their latest update it's working pretty good (at least with WEP Networks) and the process to install it in ubuntu doesn't seem to be very complicated. 

how long did you take installing the nvidia drivers? and did you encounter any problems?

---

### Post by ehmdjii on 2007-07-08
no graphics card installation went fine without any problems.

still no luck with the wifi meanwhile. and an even more serious problem: the normal ethernet also suddenly seemed to stop working. probably the module isnt loaded. does anyone know the name of the module?

edit: has anyone tried the new 35 build from intellinuxwireless.org ?

---

### Post by Adamal on 2007-07-08
> **ehmdjii said:**
> no graphics card installation went fine without any problems.

still no luck with the wifi meanwhile. and an even more serious problem: the normal ethernet also suddenly seemed to stop working. probably the module isnt loaded. does anyone know the name of the module?

edit: has anyone tried the new 35 build from intellinuxwireless.org ?

The Ethernet problem occurred for me as well after trying to install the wireless drivers.  Re-installing the OS fixed it, although I'm sure there is a better way.

---

### Post by ehmdjii on 2007-07-09
the problem is, that the card may be run in power-safe mode. so you have to disable power-safe mode in windows and then it will work in ubuntu again!

---

### Post by mrbandersnatch on 2007-07-10
Have any of you installed dual boot with Vista? 

I was following this guide [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first#comment-35242](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first#comment-35242) with the help of the recommendations linked to from here but when I reach the final step the Migration Assistant/Manager (?) doesnt show Vista as being installed.

I cant aford to lose my Vista partition at the moment so have been holding off installing...any advice anyone?

---

### Post by Adamal on 2007-07-10
> **mrbandersnatch said:**
> Have any of you installed dual boot with Vista? 

I was following this guide [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first#comment-35242](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first#comment-35242) with the help of the recommendations linked to from here but when I reach the final step the Migration Assistant/Manager (?) doesnt show Vista as being installed.

I cant aford to lose my Vista partition at the moment so have been holding off installing...any advice anyone?

I'm dual booting with vista and ubuntu.  I didn't use any migration utility, but grub was able to see both my vista install and my recovery partition.

---

### Post by mrbandersnatch on 2007-07-10
Cheers Adamal. Indeed even though it wasnt displayed as I had expected in screen 7/7 the system installed fine and I am able to boot Ubuntu and Vista.

Now to try and get the wireless card working....without a wired network :/

---

### Post by mrbandersnatch on 2007-07-10
> **ehmdjii said:**
> the problem is, that the card may be run in power-safe mode. so you have to disable power-safe mode in windows and then it will work in ubuntu again!

Managed to run a wired connection and yup, it wouldnt work until I changed this via computer management for the 8168 network adapter. Also needed modprobe r8169 to get it up and running. 

Anyone any more tips?:popcorn:

---

### Post by mrbandersnatch on 2007-07-11
So, so far my major problems are :

 - On boot I STILL get thrown to a BusyBox prompt. Just exiting out allows the lappy to boot but its annoying.
 - Sleep/Hibernate seem to work but the laptop wont resume (NvidiaLaptopBinaryDriverSuspend)?
 - /var/log/messages is being filled with messages concerning the high speed USB adaptor being reset.
 - I tried to install the intel wifi driver but, probably due to a mistake I made in the initial patching of the headers, I cant get it to compile. Im loathe to go the ndiswrapper route but will probably have to.
 - The network adaptor needs power management disabled in Vista in order to work. If I shutdown rather than suspend Vista I cant get the adaptor to work.
 - The webcam doesnt work.
 - In Beryl I cant get the decorators to display which severly resticts its usefulness as a windows manager. Ive tried most of the suggested fixes for this so suspect its a driver issue/bug.

The most major of these are the wireless adaptor, USB and suspend/resume problems. If anyone finds fixes for these (probably one of the Gutsy releases later than Tribe II) it would be great if you could share :)

---

### Post by mrbandersnatch on 2007-07-17
Has anyone got the iwlwifi drivers working when connecting to an access point "secured" via WEP? And if so what version of kernel/drivers/microcode?

Using the latest versions (17/07/07 Gutsy, mac80211 9.0.2, iwlwifi 0.0.41, 4.44.17 microcode ) I can get the wireless card operating and seeing wireless networks but if I try to connect to a secured one (which means any since I dont have any unsecured atm) my laptop hardlocks :(

---

### Post by ehmdjii on 2007-07-18
i got the very same problem. the laptop hardlocks as soon as i try to connect.

people in this thread
[http://ubuntuforums.org/showthread.php?t=493095](http://ubuntuforums.org/showthread.php?t=493095)
say, its because of version 9 of mac80211.

but i couldnt try it yet, because i have only WLAN here :)

---

### Post by mrbandersnatch on 2007-07-19
Ahhh its a pity re the wireless since its so almost there :(

As a quick aside to those who are trying Tribe III Ive been able to successfully install with the live CD with more stuff working out of the box. You will need modprobe ata_piix rather than piix and possible modprobe ide_generic as well.

Be careful about upgrading to the latest linux driver on Gutsy - it works however Compiz isnt playing nicely with it atm so get a hard lock after loging in.

---

### Post by mrbandersnatch on 2007-07-23
Has anyone got any tips on getting the webcam functional?

---

### Post by mrbandersnatch on 2007-07-25
Well to answer my own question :with uvcvideo and vfl2 installed Ekiga was able to pick the webcam up without issue. Ive had issues with most of the other capture apps though however I suspect its a configuration issue since I was also able to get luvcview to work via 'luvcview -f yuv'. Seems to be working perfectly with those drivers.

---

### Post by shil on 2007-07-25
> Driver is available here: [http://syntekdriver.sf.net](http://syntekdriver.sf.net). It doesn't work perfectly, but it is possible to get video in some applications.

(this quote is taken from a Asus G1 Howto, the camera didn't get an upgrade so it should work with G1S)

there's already a thread about the driver and how to install it here

[http://ubuntuforums.org/showthread.php?p=2699093](http://ubuntuforums.org/showthread.php?p=2699093)



about the wireless drivers, i just updated the kernel in Gentoo to 2.6.22 which already has the new wireless stack (mac80211) and the drivers for the iwl4965 are already in the "main repository" so it's just a matter of time before someone creates a package for ubuntu if there isn't one already

---

### Post by shil on 2007-07-25
> **mrbandersnatch said:**
> 
- /var/log/messages is being filled with messages concerning the high speed USB adaptor being reset.


you should submit a bug report for this, i experienced the same problem and the kernel upgrade solved it, but i believe the's a workaround for Gentoo that should work with Ubuntu

> There is patch available. Simple fix is to run command during every boot (5-7 might be something different - check your dmesg output!):

# echo -n 5-7 >/sys/bus/usb/drivers/usb/unbind


here's Gentoo's bug report: [http://bugzilla.kernel.org/show_bug.cgi?id=8432](http://bugzilla.kernel.org/show_bug.cgi?id=8432)

(i know i keep refering Gentoo a lot but i still don't have time to install ubuntu and support all the hardware, maybe next week (i hope))

---

### Post by marcop13 on 2007-07-28
I wanted to disable the lightning Asus on the oled LCD...
I've found this driver project : [https://launchpad.net/asusoled]("https://launchpad.net/asusoled")
Actually it doesn't work for me without rmmod usbhid, but I can switch off the lcd at startup:

rmmod usbhid
asusoled -d
modprobe usbhid

That's a first step...

---

