---
title: "Laptop with good Ubuntu support?"
date: 2005-07-29
forum: Hardware &amp; Laptops
---

### Post by Donshyoku on 2005-07-29
I am in the market for a laptop just to do some general stuff like surf the web, read email and RSS feeds, and use standard office documents.  I don't need anything super fast or super expensive.  I am aiming at a laptop sub-$1000 in price.  And I want strong support for GNU/Linux, mainly Ubuntu.  Another must is a large capacity battery like a 12-cell and well optimized parts (no P4s or A64s here) to reduce power consumption.  Since I can handle lower speeds, I am sure this will not be a problem.

But, where do I look?  I hear a lot about HP and Ubuntu (even an optimized version!), but it seems to be mainly targeted to Europe and I am in the USA.  Do they reuse many of the chips so that the HP Ubuntu would still recognize most of my parts?  Or should I look for a different manufacturer for stronger support?

Thanks in advance for any and all help! :)

---

### Post by Sam on 2005-07-29
You can find useful informations on [linux-laptop.net](http://www.linux-laptop.net/).

---

### Post by matthew on 2005-07-29
Take a look here to see what sorts of success people have had running Ubuntu on specific laptops.

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptops](https://wiki.ubuntu.com/HardwareSupportMachinesLaptops)

---

### Post by stevenincleelum on 2005-07-29
The averatec 6100 series in my opinion is awesome. I have a P4 model personally, but have a friend with a 6100 with the semperon and he loves it. My p4 is 100% linuc compatable with the exception of the sd card reader which I am told I just need to find the drivers, and that they are there. Every time I have called customer care it has been a pleasant experience.

Have fun, btw time to boot on mine -       XP 1:30           Ubuntu - 0:48

---

### Post by Donshyoku on 2005-07-29
I have fiddled with some Averatec models at stores before and they seem to be pretty sturdy.  Did your Averatec work out of the box.  I have a mild understanding of Linux, but I am not too found of tarballs and source to install things.  I can usually handle .deb, apt-get, and shell scripts for install though.

I am really looking for somethign that will work well out of the box, or have minimal hassle settign up.

Thanks for the links too, I will check them out!

---

### Post by Donshyoku on 2005-07-29
I would like to try the HP-Ubuntu.  It sounds like a wonderful idea for the company and they have some very competitive products.  However, I am in the US and do not have access to the same models of products as Europe does.

Do you think they share some chips (i.e. US and EU use the same motherboard/chipset, sound chip, or LAN chip)?  If this is true, I could buy a US model and install the HP-Ubuntu fine, right?

I guess the other question would be, does anyone know where I can look to see the exact sound, LAN, etc. chips they use in their models?  Would they be able to tell me over email or the phone?

Thanks again!

---

### Post by fredricsolstad on 2005-08-28
Hi

Well.. I'm running Ubuntu "out of the box" on my laptop wich is a ACER TravelMate 2355LC (a "light" version of TM2350) and I haven't had any problems so far. 

So, I recommend the Acer TravelMate 2355LC, I got mine with 512 MiB RAM, 40 GB HD, intelchipset and a Celeron at 1.4 GHz. 

Cheers!

---

### Post by Manny C on 2005-08-28
I've had really good support for Compaq Presario 2267ap.

* Hibernate works out of the box
* Suspend works by uncommenting a line in /etc/default/acpi-support (see my file attached
* Wireless works out of the box. WPA support via [this](http://www.ubuntuforums.org/showthread.php?t=26623&highlight=ipw2200+wpa) HOW-TO
* Volume keys on side of laptop work out of the box
* Touchpad works (almost) perfectly. The scroll pad doesn't work when the laptop comes out of suspend. Doesn't bother me as I use external mouse.

Can't wait for Breezy to come out with better power management features due to [gnome-power](http://gnome-power.sf.net) package.

---

### Post by basketcase on 2005-08-28
[QUOTE=Donshyoku]I am in the market for a laptop just to do some general stuff like surf the web, read email and RSS feeds, and use standard office documents.  I don't need anything super fast or super expensive.  I am aiming at a laptop sub-$1000 in price.  And I want strong support for GNU/Linux, mainly Ubuntu.  Another must is a large capacity battery like a 12-cell and well optimized parts (no P4s or A64s here) to reduce power consumption.  Since I can handle lower speeds, I am sure this will not be a problem.

But, where do I look?  I hear a lot about HP and Ubuntu (even an optimized version!), but it seems to be mainly targeted to Europe and I am in the USA.  Do they reuse many of the chips so that the HP Ubuntu would still recognize most of my parts?  Or should I look for a different manufacturer for stronger support?

Thanks in advance for any and all help! :)[/QUOTE]
 I've got a Dell Inspirion 6000, and it has worked very well out of the box.  It could be had for under $1k.

---

### Post by gravestone on 2005-08-29
I've got Kubuntu running on a new Dell Inspiron 6000 and also a Toshiba Satellite 1400. The Dell only has a non functional SD memory card reader, which I don't use, and the Toshiba's software modem doesn't work, which I can't be bothered fixing. It just needs a module for it.

I was most surprised that the Dell worked straight out of the box. I recieved the laptop, deleted Windows and installed Kubuntu, and was up and running straight after the install.

---

### Post by sneax on 2005-08-29
I have an M120W - it's a barebone from Clevo so they are sold by different kinds of brands (Sager had my model, but it's off the website, mine's a 'Promedion' sold in the netherlands). Ubuntu has full support for everything this laptop has to offer.

I'd say, if you go for a modern Centrino laptop with integrated graphics (gaming is not your thing right?) you'd be safe. Even my internal webcam is automaticaly detected by UBuntu!

---

### Post by vtec on 2005-08-30
I just got a compaq v2000. Works great. Just like Manny C said in his earlier post everything pretty much works out of the box. My only problem so far is I don't think there are any drivers for the memory card reader.

---

### Post by bearbigears on 2005-08-30
i have a used dell inspiron 8200, 1ghz of memory, 80ghz hardrive. had to buy new batteries for it when i got it. installed ubuntu with ease. had some problems but it was not the laptop,but my inexperience with linux etc. right from the start i had a good time.

---

### Post by zgoda on 2005-09-02
HP nx6110 are advertised by HP as "linux-ready", but I found two (to date) strange problems with default stock Ubuntu installs on these machines: CPU frequency scaling doesn't work (powernowd reports, that this model doesn't support frequency throttling while I know that Celeron-M 360J supports it in rather wide range) and suspend-to-ram after closing laptop lid doesn't work if you run XFCE desktop environment (works with GNOME, though).
There is customized version of Ubuntu made specially for newer HP laptops (incl. nx6110), but I didn't try this one and I don't know if they solved any of the above problems.

---

### Post by npaladin2000 on 2005-09-02
[QUOTE=zgoda]HP nx6110 are advertised by HP as "linux-ready", but I found two (to date) strange problems with default stock Ubuntu installs on these machines: CPU frequency scaling doesn't work (powernowd reports, that this model doesn't support frequency throttling while I know that Celeron-M 360J supports it in rather wide range) and suspend-to-ram after closing laptop lid doesn't work if you run XFCE desktop environment (works with GNOME, though).
There is customized version of Ubuntu made specially for newer HP laptops (incl. nx6110), but I didn't try this one and I don't know if they solved any of the above problems.[/QUOTE]

Actually, CPU throttling is disabled in Celery-M processors....I fell for that too, with this Gateway laptop.  There's no way to get it to work under any OS...Intel comes out and says so. (Funny thing, AMD's Sempron supports PowerNow throttling...why is ti AMD's budget CPUs are always better than Intel's?)

Anyway, I'm running Ubuntu on an IBM Thinkpad T42p and it works great (only the stinky modem that no one uses anymore doesn't work).  Before that it ran Fedora Core 4 perfectly, right out of the box.  If you have Centrino, you're using the ipw wireless drivers....both Fedora and Ubuntu really need to download updated firmware and drivers.  If you have an A/B/G non-Centrino wireless it's likely Aethros and you need the madwifi packages for either distro (in Ubuntu they're in the Restricted modules package).

---

### Post by zgoda on 2005-09-02
[QUOTE=npaladin2000]Actually, CPU throttling is disabled in Celery-M processors....I fell for that too, with this Gateway laptop.  There's no way to get it to work under any OS...Intel comes out and says so.[/QUOTE]

Strange, as former models (i.e. CM330, as in HP nx9020) support this feature. I saw it even working under Warty on my friend's laptop.

---

### Post by FLeiXiuS on 2005-09-02
Works on just about any IBM series.

---

### Post by odin on 2005-09-02
I'm running ubuntu on my samsumg x05 labtop and everything work fine from the begining.

Sound,internet(wifi and wired),dvd even usb.Everything is working.

---

### Post by mlord on 2005-09-03
Buy a ThinkPad.  They work perfectly with Linux, and have awesome battery life too.

---

### Post by npaladin2000 on 2005-09-04
[QUOTE=zgoda]Strange, as former models (i.e. CM330, as in HP nx9020) support this feature. I saw it even working under Warty on my friend's laptop.[/QUOTE]

Possible some slipped through the cracks or something, but Intel comes right out and says in their spec sheets that there is NO throttling on the Celerons. Can't even get it to work in Windows..the speed it comes in is the speed it stays at. Believe me, I worked on it a LOT before throwing in the towel. You'd think it WOULD work, but Intel's always in the habit of over-disabling their Celerons...with the Celeron M you lose bus speed and throttling support (theoretically you lose cache too but you're going down to 512k cache with is still quite decent).

Honestly, battery life on the Celery-M isn't bad despite the lack of throttling.  The lower bus speed and less cache must compensate. 

Anyway, back to the subject...I used to stick with IBM, HP, and Dell laptops. Now ThinkPads are no longer IBM, so I'm a little hazy on going long term with them (the current Lenovo ThinkPads are carryovers from the IBM days though, and should be safe bets).  

I'm almost ready to ditch HP as a recommendation (despite their support of Debian and Ubuntu) because they had so much trouble getting the nc8230 out of the gate; and now that they finally did it only has 400 MHz single-channel RAM.  The Dell Latitude D810 has 533 MHz RAM and can be had in dual-channel form for less $ than the HP. It's also MUCH more configurable than the HP nc8230 (The tradeoff is a little under a pound of additional weight).

HP's home (Pavilion line) doesn't really impress me outside of the zd8000 (which is a monster) but their Compaq division has some nice models. And their AMD Sempron-M chips DO have CPU throttling, where the similarly priced Intel Celeron-M doesn't (meaning for budget go with Sempron, performance should probably be the Intel, since OSes and software can't really make use of the full AMD Turion-64 capabilities yet). 

Considering that Dell pays expensive Americans to manufacture and handle support, while HP offshores it to cheap Indian call centers and what not (Not making any value judgement other than pay scale, mind you) the fact that Dell comes out with a better configured, better featured laptop for less than HP AND supports the American economy makes me want to recommend Dell.   What can I say? I'm an American IT guy and would like to support my own economy. Those in other countries, feel free to support your own economy if you wish...fair is fair. :)

---

### Post by Kaso_Da_Zmok on 2005-09-04
I was Able to Install per Wireles (Disabled WPA and WEP on my Wifi access points)
Sound worked
AtI 9000 work witg FGLRX (needed to recompile the module using external agpgart)

now glxgears around 1100 FPS 
AND fgl_gears around 160 FPS

but thats fine for the Ati 9000

Also reconfigured sound so esd uses ALSA instead of OSS.

Tried to install ut2004, and it was working but after i join a map the sound gets messy and the game really slow ,,,, kills me, and than i kill gdm to get to normal...

Other openGL is running fine, Lid works and lock with screensaver.

I had few locks (3 times ) during a week i had to kill the machine by button. Dont know exactly .... Did also Gentoo Stage 3 and than Stage 1 on this laptop. (dont try  gentoo stage1 here :-))) ](*,)

---

### Post by zgoda on 2005-09-08
[QUOTE=npaladin2000]Possible some slipped through the cracks or something, but Intel comes right out and says in their spec sheets that there is NO throttling on the Celerons. Can't even get it to work in Windows..the speed it comes in is the speed it stays at. Believe me, I worked on it a LOT before throwing in the towel. You'd think it WOULD work, but Intel's always in the habit of over-disabling their Celerons...with the Celeron M you lose bus speed and throttling support (theoretically you lose cache too but you're going down to 512k cache with is still quite decent).[/QUOTE]
I think we are on two different subjects. While Celeron-M clearly doesn't support Centrino-style frequency throttling by means of voltage adjustment, it perfectly supports "normal" frequency scaling, as with older "M" models from Chipzilla (P3M, P4M). In fact, I got it finally working, although the solution I used (and the overall result) doesn't amuse me.

As cpufreq-detect doesn't detect Celeron-M's (it is basing on entries from /proc/cpuinfo), it can not load proper kernel module for frequency scaling, you have to do it manually, i.e. by adding module entry (p4-clockmod) to /etc/modules. Then the only thing you have to do is to select scaling governor, that will manage frequency adjustment. This can be done using 
```
echo "ondemand" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

If all this is worth all headaches, it's another story. I spent few days trying various settings only to discover, that the power consumption with frequency scaling enabled is marginally lower than without it, so I decided to turn it off.

---

### Post by betamax on 2005-09-08
I'd go with the Thinkpad vote,

My T23 runs great, had a few problems with APCI, but once it was tweaked its running wonderful.

You can also pick them up cheap.
......................

---

### Post by FatherDale on 2005-09-09
[QUOTE=Donshyoku]
But, where do I look?  I hear a lot about HP and Ubuntu (even an optimized version!), but it seems to be mainly targeted to Europe and I am in the USA.  Do they reuse many of the chips so that the HP Ubuntu would still recognize most of my parts?  Or should I look for a different manufacturer for stronger support?

Thanks in advance for any and all help! :)[/QUOTE]

I run an Averatec 3225HS. Ubuntu installed first time, no hitches. I ran ndiswrapper on the Ralink radio until the latest batch of native drivers came out of the Sourceforge RT2400 project. They work wonderfully (Ralink has released the driver source to the community). There is even an Ubuntu installation wiki for it at [https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/) . Bang for buck is wonderful.

---

