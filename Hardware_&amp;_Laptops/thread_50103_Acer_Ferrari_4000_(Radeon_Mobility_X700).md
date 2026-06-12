---
title: "Acer Ferrari 4000 (Radeon Mobility X700)"
date: 2005-07-19
forum: Hardware &amp; Laptops
---

### Post by infiltrator on 2005-07-19
I've recently purchased the above laptop and am keen to get X running on the notebook working. Installation goes very well until the X-component starts up.

I'm still pretty new to linux, but have learnt quite a lot in trying to get the X-system to work :) It appears that the X-system is loading on my system as I can hear the audio when I press keys (at the login screen which I can't see :( ). There are also no errors in the xorg logs.

The ATi Mobility Radeon X700 is being picked up correctly, but the display is not being output correctly (don't know if it's got to do with being output on the wrong display type, although I've tried LVDS, CRT, the default DPMS, STV and TMDS). I've been installing various flavours and being getting similar results. Redhat tends to work by using the LVDS but the backlight does not work so you feintly see the X output but it's to dark to even use. I'm going to try Suse 9.3 to see if that works. Since all Linux versions tend to work the same perhaps I can learn from that and apply the settings in one that works to Ubuntu and it may also work.

Anyone with a similar problem on the same graphics card (Radeon Mobility X700) please let me know so we can troubleshoot together, and perhaps show the devs how many of us have this card and want it working :)

I'm thinking it's probably something small that we are overlooking :(

***EDIT***

I have noticed that the card is not supported by xorg (only X600 and X800 are suported - [related page](http://www.x.org/X11R6.8.2/doc/radeon.4.html) 

I'm going to try fiddle with some of the switches in the hope to get it going...

---

### Post by Teroedni on 2005-07-19
Your lucky one   drooooling :roll: 

Do you use Ubuntu Warty or Hoary 5.10

Can you post your xorg.conf?

And last have you tried xfree86?

---

### Post by infiltrator on 2005-07-19
I was using 4.10 but am loading 5.04 as we speak :) I will report back later and post my findings. I will also post my xorg.conf file a little later.

I have not tried XFree86, I will try that later. I can't seem to find a page listing the supported adaptors for XFree86 :( Anyone have a URL?

---

### Post by xkcdmagic8 on 2005-08-04
i have the laptop and i got the X700 working with full acceleration and @ 1680x1050 resolution.

Basic steps are:
1) update ur kernel to highest version (ubuntu provides)
2) get that kernels source
3) make sure ur running the right kernel/source is for same kernel
4) get the new ati drivers from [www.ati.com](www.ati.com) NOT THE INSTALLER
5) get those installed
6) compile them - > should work post errors here
7) install them into your modules ... ill get you the proper commands and more specifics on this whole thing later today
8) and play with your xorg.conf, i know u have to set MonitorLayout "LVDS, NONE" i think and also some bus location to force it to reconise the PCI-E connection - not AGP.

And it will work

im busy right now so asap i will post my xorg.conf here and give u a full list of commands to run....


NOW if someone in the wild world can get ACPI support that would be now -> it doesnt read battery state = useless.

---

### Post by TheViking on 2005-08-05
Hi there

Im also the happy owner off a Ferrari 4000 and is currently fighting to get the X to work.

Do you mind sending me your xorg.conf ? so i can find my mistakes ?

Regards

Nikolaj Steensgaard

---

### Post by KeziahW on 2005-08-11
Hi all,
I just got the same ferarri ;))
it seems pretty cool so far, but I'm having a lot of trouble getting the hardware working (currently no X, no wifi, no bluetooth, a lot of cool stuff untested)
I'm running gentoo on it, so my situation is somewhat different, but the same general solutions should apply to all distros, so I would really like to collaborate on getting better support on these things...

X: I think framebuffer support in the kernel is necessary
It is running without any error messages, but the screen is blank; in my system log it has unrecognized mtrs and weird pci stuff

wifi: I think it can be done with ndiswrappers, but I haven't been able to find a win64 driver; ndisw doesn't like using a 32bit driver

bluetooth: I think it is very similar to setting up a usb controller, probably shouldn't be too difficult once I figure out what kernel support is necessary

Does anyone have this stuff working? if so, please share the details! I can't wait to get this fully functional...

---

### Post by KeziahW on 2005-08-11
Got wifi working!

Get a 64bit driver for ndiswrappers from:
[ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/winxp64bit/](ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/winxp64bit/)
(32bit at [ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/](ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/))
Then extract the zip, cd to BG, and ndiswrapper -i bcmwl5
Then push the wifi button on the front of the lappy, and modprobe ndiswrapper...
That's all you need to get the hardware working; for the software, you'll want to start out with iwlist wlan0 scan, and use iwconfig to set the matching values.

Next goal: X...

---

### Post by KeziahW on 2005-08-11
Bluetooth: apparently it was already working and I just needed to move the mouse farther to wake it up

X: I set Driver to Vesa - I now have a usable X with full resolution and color, but the vesa driver does some strange things and is not accelerated, so I still need to get a nongeneric driver working
Warning: be careful with vesa on this - if one side of your screen starts changing color and it's spreading, get out of X no matter how cool it looks

---

### Post by lakin on 2005-08-12
I have spent the past few days getting Ubuntu working as well as I can with my Ferrari 4005 laptop. 
Here are my notes:

[http://pages.cpsc.ucalgary.ca/~weckerl/ferrari_ubuntu_64.html](http://pages.cpsc.ucalgary.ca/~weckerl/ferrari_ubuntu_64.html)

I would appreciate feedback on this if there are typos or unclear sections.  please continue to use these forums for problems, rather than using my email.

---

### Post by michaelp on 2005-08-13
Could somebody please post their working xorg.conf?

What a rough start to using Ubuntu..

---

### Post by lakin on 2005-08-13
I posted mine on my website.  I do recommend however, that you build your own based off of it.  First off, make sure that you have the same laptop as me, and make sure that you have followed the instructions given on that page so that you have the appropriate drivers.  Otherwise, it won't work.

---

### Post by sreekar on 2005-08-15
Hello all.  

It seems Acer is aware that they shipped the Ferrari 4000 with a buggy BIOS.  They've posted a fix on their Taiwanese website.  This may solve some ACPI problems under Linux.

Check out posts 80 and 85 on 

[http://www.notebookforums.com/showthread.php?t=91771&page=6&pp=15](http://www.notebookforums.com/showthread.php?t=91771&page=6&pp=15)

---

### Post by jewishj on 2005-08-23
[QUOTE=lakin]I have spent the past few days getting Ubuntu working as well as I can with my Ferrari 4005 laptop. 
Here are my notes:

[http://pages.cpsc.ucalgary.ca/~weckerl/ferrari_ubuntu_64.html](http://pages.cpsc.ucalgary.ca/~weckerl/ferrari_ubuntu_64.html)

I would appreciate feedback on this if there are typos or unclear sections.  please continue to use these forums for problems, rather than using my email.[/QUOTE]

I have followed instructions in this site to get my wifi working.  However, it only seems to work with networks without any encryption.  On my home network, I disable wep and it works fine, i reenable and it will prompt me for the key, but then it wont work.

Has anyone gotten this working with wep (128bit encryption)?

Also.. the ACPI fix is not working at all for me.  I followed the instructions to the letter (about six times over I tried) with the exception of just swapping out my initrd.img-2.6.12.5-custom for the one that is patched instead of making a link to it.  I am still getting the same errors as always "Z00I etc. etc." so obviously it's not getting my fixed script.

Thanks

---

### Post by infiltrator on 2005-09-02
I've had to send my ferrari back due to faulty sound (crackling). so I'm picking it up from the couriers tomorrow morning. Will try many of the suggestions mentioned here. I managed to load different versions of Linux it appears some work better in different areas, but then you can normally apply the same or very similar settings to Ubuntu. I'll give it a try and report back soon :) Many thanks for everyone's help.

---

### Post by lakin on 2005-09-21
[QUOTE=jewishj]I have followed instructions in this site to get my wifi working.  However, it only seems to work with networks without any encryption.  On my home network, I disable wep and it works fine, i reenable and it will prompt me for the key, but then it wont work.

Has anyone gotten this working with wep (128bit encryption)?

Also.. the ACPI fix is not working at all for me.  I followed the instructions to the letter (about six times over I tried) with the exception of just swapping out my initrd.img-2.6.12.5-custom for the one that is patched instead of making a link to it.  I am still getting the same errors as always "Z00I etc. etc." so obviously it's not getting my fixed script.

Thanks[/QUOTE]

I have my card working with WPA encryption.  I had to use a HOWTO that I found on Ubuntu's WIKI. [https://wiki.ubuntu.com/WPAHowto](https://wiki.ubuntu.com/WPAHowto)

As for the ACPI, Jordan Steinberg mentioned that he had to do a few extra steps to get the ACPI working on his laptop.  I suspect this may have to do with some differences between the laptops.  I've added his notes to the bottom of my acpi section.

---

### Post by krage on 2005-11-26
I am not getting my wifi card to work i have done as the guids tell me to, and when i type
ndiswrapper -l this i what i get:
bcmwl5  driver present, hardware present

so it looks like it work, but i can't turn it on, no light when i press the button in the front...

Any ideas?

---

### Post by michaelp on 2005-11-29
Has anybody got tv out to work? This is the only thing I am missing to finally be able to delete windows. 
It would be sweet:)

---

### Post by amd-64 on 2005-12-17
[QUOTE=krage]I am not getting my wifi card to work i have done as the guids tell me to, and when i type
ndiswrapper -l this i what i get:
bcmwl5  driver present, hardware present

so it looks like it work, but i can't turn it on, no light when i press the button in the front...

Any ideas?[/QUOTE]

Light only blinks when connected. To see if wireless is on, I press the wireless button and check the log files in /var/log/. You will find the most recent statement in the logs about keycode e055 (which is wireless on) or keycode e056 (wireless off). If it is e056 press again to get e055 (on).  

Check your /etc/network/interfaces
mine has the two following lines related to wlan0 at the end of the file

iface wlan0 inet dhcp
wireless-essid  linksys <or your desired network essid>


restart networking
$  sudo /etc/init.d/networking restart

bring up interface
$ sudo ifup wlan0

Hope some of this helps.

---

