---
title: "hp envy 17 wireless problem"
date: 2010-07-21
forum: Hardware
---

### Post by zero7404 on 2010-07-21
i used to have an xps m1730 and ubuntu ran fine on it more or less.
i got a new laptop, the hp envy 17. i installed 32-bit ubuntu on it, but it did not recognize my wireless (Broadcom 43224AG 802.11a/b/g/draft-n Wi-Fi Adapter). i tried following the help on how to install it, i checked in the terminal and it said this adapter was unclaimed, but my attempts to install the windows driver failed. i think because the windows driver is 64-bit.

i also tried connecting the laptop to wired and ran all the updates thru, but it still gave me an error about installing the broadcom driver.

not sure what i'd need to do at this point to get it up and running.

---

### Post by stf2win on 2010-07-27
windows-drivers most times won't work on any linux afaik.


my notebook has the same type Broadcom Wi-Fi adapter, and I had the same problem that it wasn't recognized. (so I found this thread via google)


**I found a way to solve it**
**1.** go to this site: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) (google: "linux driver site:broadcom.com")

**2.** there u download the 32-bit driver. (I installed x64 Ubuntu so I used the 64-bit driver)

**3.** unpack it into a directory (eg: /home/myusername/Downloads/wlan )

**4.** I opened a Terminal and made those steps (as they are explained in the Readme-file) to install it on my nb:
(you have to have root-access for certain steps, so you may should type **sudo** in front of the commands if it says you have to be root ... like the apt-get)
```
# apt-get install build-essential linux-headers-generic
# cd /home/myusername/Downloads/wlan    *(this is the directory where i unpacked the drivers)*

# make clean
# make

# modprobe lib80211
# insmod wl.ko   *(this one only will work if the 'make'-process finished without any errors)*
```

**5.** if everything went fine u can now connect to any access-point



I hope this helps, as it helped me

---

### Post by Rebajas on 2010-08-13
I loaded up the 64-bit Live CD of 10.04 and found that the driver for WiFi was in restricted drivers - once activated I could connect to WiFi with no issues at all.

Hoping that will also be the case when I install for real - just waiting for an SSD before I find out.

---

### Post by zero7404 on 2010-08-13
thanks for the replies ...

i want to install ubuntu on my machine again, this time i want it to be rock solid. curious, does canonical update the iso's at all or is it the same thing it's been since release ?

i think i'll give 10.04 another stab, this time i need to make sure my hardware will get set up with the installation, broadcomm wireless and ATI graphics.

hopefully, updates have been made to the drivers needed and a fresh install from an updated iso may give me a clean working install without hickups.

if needed, i can get in there and manually install and fix stuff (like the suspend problem due to USB 3.0, broadcomm, etc...), but looking to avoid doing this stuff...

since my last install, i made my primary drive an SSD...should i anticipate issues with gparted during installation ? i normally shrink the windows volume in disk management, then use the unallocated space for ubuntu in gparted. being an SSD, could i just do away with a swap partition ?

---

### Post by pelle.k on 2010-08-14
> **zero7404 said:**
> thanks for the replies ...

i want to install ubuntu on my machine again, this time i want it to be rock solid. curious, does canonical update the iso's at all or is it the same thing it's been since release ?
i think i'll give 10.04 another stab, this time i need to make sure my hardware will get set up with the installation, broadcomm wireless and ATI graphics.
hopefully, updates have been made to the drivers needed and a fresh install from an updated iso may give me a clean working install without hickups.
if needed, i can get in there and manually install and fix stuff (like the suspend problem due to USB 3.0, broadcomm, etc...), but looking to avoid doing this stuff...
An updated ISO will not improve anything over an updated installation. With a system update you will have those updates installed right away anyway.
Do restart the computer after updating it, before you use the restricted drivers manager though. It seems to work better that way.
Anyways, Ubuntu LTS 10.04.1 should be released any day now.

> **zero7404 said:**
> since my last install, i made my primary drive an SSD...should i anticipate issues with gparted during installation ? i normally shrink the windows volume in disk management, then use the unallocated space for ubuntu in gparted. being an SSD, could i just do away with a swap partition ?
Your SSD will work fine with garted. An SSD does not remove the need for swap space, however. Also, without swap space, you will not be able to hibernate your computer.

Also, please do report back and tell us how it went. I'm interested in purchasing one of those notebooks myself, and i'm particulary interested in how stable it is.
Does it ever freeze (kernel panic)? Is suspend/resume fully working (always)? Can you adjust the backlight with Fn keys and gnome backlight settings? Is it running hotter in ubuntu than windows?

---

### Post by zero7404 on 2010-08-14
> **Rebajas said:**
> I loaded up the 64-bit Live CD of 10.04 and found that the driver for WiFi was in restricted drivers - once activated I could connect to WiFi with no issues at all.

Hoping that will also be the case when I install for real - just waiting for an SSD before I find out.

i had problems loading up X during boot up, after installing the restricted ATI drivers. i once got some text on the lower right of the screen about an unrecognized display, it could not be fixed or removed. after a few install attempts to get ubuntu running smoothly on this laptop, i gave up.

i like the idea of having a dual boot configuration, i've ran ubuntu with windows side by side on other machines without many problems, but when x doesn't start up, i get turned off to fixing the problem and instead blow away the ubuntu install.

---

### Post by zero7404 on 2010-08-14
> **pelle.k said:**
> An updated ISO will not improve anything over an updated installation. With a system update you will have those updates installed right away anyway.
Do restart the computer after updating it, before you use the restricted drivers manager though. It seems to work better that way.
Anyways, Ubuntu LTS 10.04.1 should be released any day now.


Your SSD will work fine with garted. An SSD does not remove the need for swap space, however. Also, without swap space, you will not be able to hibernate your computer.

Also, please do report back and tell us how it went. I'm interested in purchasing one of those notebooks myself, and i'm particulary interested in how stable it is.
Does it ever freeze (kernel panic)? Is suspend/resume fully working (always)? Can you adjust the backlight with Fn keys and gnome backlight settings? Is it running hotter in ubuntu than windows?

from what i remember, some work had to go into it in order to suspend properly. the culprit was usb 3.0, i don't recall exactly what i configured, but it was a topic discussed before, where the port would prevent suspend.

i never use hibernate, so if i pass on a swap, would the OS still run fine ?

as for special function keys, etc, i recall the brightness did work, and it ran quite cool.

under windows 7, i've had no stability issues at all. i consider myself an advanced user and am very conciensious of what software i install and use, what i download and what browser i use. between typical windows house cleaning to advanced registry cleaning, the machine is stable and hasn't hickuped hardware-wise.

however i have been experiencing very low volume electrical noise coming from the main board. i sent the unit back and HP claims they replaced my main board, however the noise has resurfaced. a simple infinite loop batch file keeps the cpu somewhat busy and this eliminates the noise, however it heats things up a bit. i may be getting an upgraded unit from HP on the premise this problem is specific to my configuration (core i5) ... if they cannot resolve the noise issue ...

---

### Post by zero7404 on 2010-08-14
btw, why is the bootup/shutdown graphic really lowsy ? ever since 9.10, the render of the splash image has looked glitched/wrong.

---

### Post by pelle.k on 2010-08-15
> **zero7404 said:**
> i had problems loading up X during boot up, after installing the restricted ATI drivers.
It can be that the catalyst driver in ubuntu is too old for you video card. You could try uninstalling it (or not installing it on a new install), and download the official installer (catalyst 10.7) directly from ati.
Also, with new video cards that boot up with a blank screen,yo may try starting ubuntu by adding the options **nomodeset** or **xforcevesa**, to the grub kernel line.
> **zero7404 said:**
> i never use hibernate, so if i pass on a swap, would the OS still run fine ?
Sure, it'll run just fine as long as you've got a lot of ram, and you've got 4GB in that model AFAIK. SSD disks do have an advantage with swap space though - it's damn fast swap space, if you should ever need it :)
> **zero7404 said:**
> however i have been experiencing very low volume electrical noise coming from the main board. i sent the unit back and HP claims they replaced my main board, however the noise has resurfaced. a simple infinite loop batch file keeps the cpu somewhat busy and this eliminates the noise, however it heats things up a bit. i may be getting an upgraded unit from HP on the premise this problem is specific to my configuration (core i5) ... if they cannot resolve the noise issue ...
Ah, that's the WLAN/BT module from what i can gather. Look at this bug report. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/613963](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/613963)
So it's probably a irq conflict or something, but still a software problem, at least in his case.
> **zero7404 said:**
> btw, why is the bootup/shutdown graphic really lowsy ? ever since 9.10, the render of the splash image has looked glitched/wrong.
Probably because KMS (kernel modesetting) doesn't work with your graphics card/driver yet. I bet in ubuntu 10.10 it'll work allright.

---

### Post by zero7404 on 2010-08-17
> **pelle.k said:**
> It can be that the catalyst driver in ubuntu is too old for you video card. You could try uninstalling it (or not installing it on a new install), and download the official installer (catalyst 10.7) directly from ati.
Also, with new video cards that boot up with a blank screen,yo may try starting ubuntu by adding the options **nomodeset** or **xforcevesa**, to the grub kernel line.

Sure, it'll run just fine as long as you've got a lot of ram, and you've got 4GB in that model AFAIK. SSD disks do have an advantage with swap space though - it's damn fast swap space, if you should ever need it :)

Ah, that's the WLAN/BT module from what i can gather. Look at this bug report. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/613963](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/613963)
So it's probably a irq conflict or something, but still a software problem, at least in his case.

Probably because KMS (kernel modesetting) doesn't work with your graphics card/driver yet. I bet in ubuntu 10.10 it'll work allright.

thank you for the detailed answers. it's good to see more ppl speaking up about the noise issue, however i would be cautious about diagnosing the wlan module. although it does sound like it's coming directly from the module, it's strange because i wrote a small infinite loop batch script to keep the cpu under load. when the script is running, the noise is greatly reduced, but the effect of this is increased cpu temps (turning the fan up more often).

this is all happening in windows 7.

with respect to ubuntu, i tried again, for maybe the 5th time, to get a good installation going. after updates and configuring the way i want it, a few restarts later, the computer stops responding on bootup into ubuntu, never reaching the login screen. this occured AFTER a few restarts AFTER all updates were installed.

so, i am really reluctant to try again. don't really need ubuntu, but it's nice to have as a secondary OS in case i have a problem in windows.

then again, i keep my windows install really clean and correct, so i have yet to experience a catastrophic problem for about 2 years now. in the event it does get corrupted, i have a clonezilla routine with periodic images of my primary drive.

---

### Post by Rebajas on 2010-08-18
Typical - did a proper install from the same CD I previewed last week. No wireless or ATI drivers in Restricted drivers.

Will have another look tonight but was slightly disappointed (and confused) as I was expecting the Live CD to be the same experience as the full install.

Will update later.

---

### Post by pelle.k on 2010-08-18
> **zero7404 said:**
> with respect to ubuntu, i tried again, for maybe the 5th time, to get a good installation going. after updates and configuring the way i want it, a few restarts later, the computer stops responding on bootup into ubuntu, never reaching the login screen. this occured AFTER a few restarts AFTER all updates were installed.
Actually, this might not be a problem with your particular computer. When i did update my system just a day or so ago, the nvidia module (driver) was missing. The only way i could get it back was to uninstall, then reinstall the propreitary driver from "hardware drivers manager". Strangely enough, even when it *was* missing, it was apparentöy "active" in "hardware drivers manager". I never did report this as a bug, thinking it was just bad luck on my part.
If your system was defaulting to the free nouveau driver, and KMS wasn't disabled from GRUB, that would result in a black screen indeed. :(

> **Rebajas said:**
> Typical - did a proper install from the same CD I previewed last week. No wireless or ATI drivers in Restricted drivers.

Will have another look tonight but was slightly disappointed (and confused) as I was expecting the Live CD to be the same experience as the full install.

Will update later.
As i said earlier, try rebooting once, after updating the (installed) system fully, and the drivers you are missing may show up. You might need a wired internet connection to do just that though.
BTW, the 10.04.1 ISO was just released.

---

### Post by Rebajas on 2010-08-18
> **pelle.k said:**
> As i said earlier, try rebooting once, after updating the (installed) system fully, and the drivers you are missing may show up. You might need a wired internet connection to do just that though.

Good call - rebooted and found 2 entries in my proprietory drivers listing. Once installed both my Wifi and ATI seem to be running just fine.

Now just got to work out why the default theme is sooo ugly... I was told it was up there with Mac OS X and Windows 7! :)

---

### Post by pelle.k on 2010-08-19
> **Rebajas said:**
> Now just got to work out why the default theme is sooo ugly... I was told it was up there with Mac OS X and Windows 7! :)
IMHO OSX is second to none when it comes to looks out-of-the-box, but neither W7 nor OSX can be themed like a gnome desktop can. ;)

Try this; install ttf-droid (from the package manager), and then open up appearances and change that ugly "sans" to "droid sans". You may shrink it down a bit as well.

Add the faenza icon set ppa, and install it;
```
sudo add-apt-repository ppa:tiheum/equinox
sudo apt-get upgrade && sudo apt-get install faenza-icon-theme
```
If you're really adventuourus, try out the new "ubuntu light" themes. You need both the new murrine engine, and the light-themes deb.
[http://people.ubuntu.com/~stefanor/light-themes/lucid/](http://people.ubuntu.com/~stefanor/light-themes/lucid/)

To top it off, try installing "docky", and replace that bottom panel with a dock (like OSX has).

---

### Post by Rebajas on 2010-08-20
I've just finished setting up the appearance to suit my taste - nothing fancy but then I rarely spend any time looking at the chrome :)

To be honest - I was just a bit taken-aback that the 'out-of-the-box' look was so dull. Doesn't help that they've locked down the login to achieve faster boot times.

I've managed to change login background though, so I have a more seemless experience between login and desktop. It'd be nice if the devs gave an option to set the same image for both when the user alters their desktop background?

These are small details in the grand scheme of things though; I'm just over the moon wifi and video work! I can play with the look & feel forever ;)

---

### Post by boomboom69 on 2010-09-06
I've also got an HP envy with all the upgrades, core i7 840 8gig ram etc... I'm running the beta version of the Ubuntu maverick release and it works great, except issues with the ATI graphics card. If I install the package or the drivers from ati I get black screens at login until I remove them. I suspect issues with the xorg.conf file, but don't know how to fix it. I also have issues with the touchpad. It uses a newer multi touch touchpad similar to Macbooks but for right and left clicks there are touch regions on the bottom. if in the right region and click it's supposed to give a right click to the OS. Works proper in windows, but ubuntu driver doesn't look at it as a multitouch and doesn't allow the two finger drag scrolling nor the touch region clicking. Anywhere on the pad clicking only does left click. Does anybody know of any fixes for these two issues? Currently for the mouse I just enabled the click-hold feature to issue issue right click command.

---

### Post by zero7404 on 2010-09-06
i put my efforts on hold until 10.10 is released. when it's out i will wait another month and see how i feel about installing ubuntu again. it's not very painful to do, but every time i get it working the way i like, something goes wrong and since it's a secondary OS, i would not give it enough energy to troubleshoot and fix.

actually, until wine or another linux-based tool allows me to run my windows-only apps with complete transparency, i don't really have a need for linux. it's been a year and 1/2 that i've been playing with it, testing it out to see if it's a worthy replacement for windows in the long run, but it isn't happening ...

---

### Post by cil_8 on 2010-12-29
Same problem with Ubuntu 10.10 64 bit!!

iwconfig don't detect wlan0

solutions?

---

### Post by desposti on 2012-02-16
Hello guys. I have a strange wireless problem on my new  HP ENVY 17-2180ez , unfortunately I don;t knwo the details of the wifi card, on HP sheet saying Intel but I am not home right now to check. Baiscally wifi seems to work FINE, it connects properly BUT then connection is VERY SLOW , I barely manage to open websites.  IF I connect via ethernet cable is SUPER FAST FORMULA 1. I tried checking onlien did nto find solutions. Maybe I will have to try to look for drivers but Ubutnu not telling me I need any drivers when I check. Any help please?

---

