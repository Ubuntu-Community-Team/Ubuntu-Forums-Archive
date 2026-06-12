---
title: "Fujitsu Esprimo Mobile V5535"
date: 2007-11-22
forum: Hardware &amp; Laptops
---

### Post by Jata on 2007-11-22
Hello all. I'm on the verge of buying this laptop and was just wondering if anyone has had any problems installing Ubuntu on it? I've seen a post regarding the V5515 which seems to have gone ok so I'm hoping it will all go smoothly. If anyone has any advice I'd love to hear it!
Thanks in advance...

---

### Post by esplinter on 2007-11-22
I have just installed kubuntu 7.10 on fujitu-siemens esprimo mobile V5515 and ethenet and wifi cards didn´t work. I had to use ndiswrapper and the windows drivers as explained here:

[http://ubuntuforums.org/showthread.php?t=577487&highlight=V5515]("http://ubuntuforums.org/showthread.php?t=577487&highlight=V5515")


graphics cards is with vesa drivers. Right now trying to solve it.

Not sure if V5535 has the same hardware.

hope it helps

---

### Post by Jata on 2007-11-24
Ok, I changed my mind slightly and went for the V5505! I'll get it working come what may. Thanks for the heads up esplinter, I'm sure that link will come in handy when it arrives. Getting excited now :-D

---

### Post by Brian Graham on 2008-01-02
Hi Guys,

I too am suffering with the V5535 graphics issue, I have got it to run in 1200x768 which is good enough and looks ok, but am trying to crack the issue, so, if I have a break through I will let you know!

---

### Post by Mirius on 2008-01-25
To fix graphic problem, yo need to download "[sis_vga_200807_ubuntu_7.04.tgz"]("http://www.badongo.com/file/5319845") then  you have to move sis_drv.* to /usr/lib/xorg/modules/drivers/ and modify your Xorg.conf from vesa to sis, by typing:



$sudo dpkg-reconfigure -phigh xserver-xorg 


Thats all!

---

### Post by geofff on 2008-02-04
I've also been struggling with the v5535 graphics. Sorry Mirius but I wasn't comfortable downloading a file that I didn't know where it came from, especially as 7.10 already has a sis_drv.so driver file. I have however tried modifying Xorg.conf with the dpkg script you gave. I tried vesa and sis drivers with various combinations and tried also from System>Administration>Screens and Graphics. Nothing worked. I kept getting reverted to vesa with plug&play at 800x600. 

I have now had success. I don't recommend anyone doing as I did as I was out of my depth and the reason I'm posting is to let people know a combination that does work well. In the Screens and Graphics Preferences window - graphics card - I have  "vesa - Generic VESA-compliant video cards", In the Screen window I have Model: "LCD Panel 1024x768(wide screen)", resolution: 1280x768 at 60Hz. Having rebooted it works! After all the hassle no-one is more surprised than me. Whether it would have worked had I not switched the machine off in the middle of a "sudo dpkg-reconfigure xserver-xorg" (ie excluding the -phigh), that brought up lots of questions that I didn't know how to answer, I may never know! - I input the above combination immediately after switching back on again. I'd be interested in hearing if anyone has success with this combination without my unconventional method!

Geofff

---

### Post by geofff on 2008-02-04
Oh *****!
I posted too soon! I hadn't rebooted I'd logged out to activate the changes. When I reboot I'm back to the 800x600 again and have to make the changes to Screens and Graphics Preferences window - and log out. But once I do I have a usable machine. All I now have to do is to figure out how to make the changes stick when I reboot. I'm again out of my depth on this one. Any ideas would be welcome.

Update: as this was a fresh install I have now done a complete reinstall, and before messing with anything else amended the graphics settings as above. I am now able to reboot and keep the settings. I have a fully workable machine!

---

### Post by jeff124578 on 2008-04-13
> **Brian Graham said:**
> I too am suffering with the V5535 graphics issue, I have got it to run in 1200x768 which is good enough and looks ok, but am trying to crack the issue, so, if I have a break through I will let you know!

@Brian Graham: Were you successful in using an SIS (as opposed to vesa) graphics driver?  I'd be especially interested if there's a way to kick the resolution above 1280x768.

---

### Post by richyp96 on 2008-04-24
I'm having issues even installing Ubuntu on my Fujitsu Esprimo Mobile V5535. I've tried 7-10 and two other versions (can't remember the numbers now). 2 of them did nothing, and wouldn't boot from the CD, 1 of them would start to boot from the CD, but the screen just went undecipherable, and after a while it did nothing. Any body any ideas? Is this a Vista issue or a hardware issue?

---

### Post by PaulHuygen on 2008-04-25
> **richyp96 said:**
> I'm having issues even installing Ubuntu on my Fujitsu Esprimo Mobile V5535. I've tried 7-10 and two other versions (can't remember the numbers now). 2 of them did nothing, and wouldn't boot from the CD, 1 of them would start to boot from the CD, but the screen just went undecipherable, and after a while it did nothing. Any body any ideas? Is this a Vista issue or a hardware issue?

It looks like a hardware problem or bad cd's. A month ago I installed Gutsy on a V5535 and booting and installation went without problem. Since you by-pass Vista, Vista cannot be the problem.

Paul.

---

### Post by richyp96 on 2008-04-25
It was a CD problem, I burnt it again using Infra Recorder as an image, and at the slowest speed possible. it works now, just need to sort out the screen size.

Thanks.

---

### Post by PaulHuygen on 2008-04-25
> **richyp96 said:**
> It was a CD problem, I burnt it again using Infra Recorder as an image, and at the slowest speed possible. it works now, just need to sort out the screen size.

Thanks.

The graphics resolution remains a problem, at least for me. Fur the Gusty version, the method described in this thread, using the drivers in  
"sis_vga_200807_ubuntu_7.04.tgz", worked for me. However, this does not seem to work with the new version of Ubuntu.

Another problem were the network interfaces. I couldn't get the wireless, not the wired interface to work. Therefore, I use a USB WiFi card.

Paul Huygen

---

### Post by picbits on 2008-04-29
I've just got the wireless working perfectly on my V5535 using the method here:

[http://ubuntuforums.org/showthread.php?t=766529&highlight=atheros](http://ubuntuforums.org/showthread.php?t=766529&highlight=atheros)

In fact I'm using the laptop to type this reply on wireless and 8.04.

Hope that helps

---

### Post by starvingartist on 2008-05-27
> **Mirius said:**
> To fix graphic problem, yo need to download "[sis_vga_200807_ubuntu_7.04.tgz"]("http://www.badongo.com/file/5319845") then  you have to move sis_drv.* to /usr/lib/xorg/modules/drivers/ and modify your Xorg.conf from vesa to sis, by typing:



$sudo dpkg-reconfigure -phigh xserver-xorg 


Thats all!

I'd love to try this (bought a v5535 today), but it doesn't allow me to copy the files to the drivers folder you mention! :(


On a related note: is a similar fix available for Xubuntu 8.04?

---

