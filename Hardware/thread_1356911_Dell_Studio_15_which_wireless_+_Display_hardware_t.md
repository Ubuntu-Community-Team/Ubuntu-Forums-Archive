---
title: "Dell Studio 15 which wireless + Display hardware to choose"
date: 2009-12-16
forum: Hardware
---

### Post by CaveManx on 2009-12-16
Hello people,

I wanna buy a Dell Studio 15 [http://www1.euro.dell.com/uk/en/home/Laptops/laptop-studio-1555/pd.aspx?refid=laptop-studio-1555&s=dhs&cs=ukdhs1](http://www1.euro.dell.com/uk/en/home/Laptops/laptop-studio-1555/pd.aspx?refid=laptop-studio-1555&s=dhs&cs=ukdhs1)

Which video chipset is the best supported by Ubuntu? The Intel 4500MHD or the [FONT=arial][SIZE=1]512 MB ATI Mobility RADEON HD 4570?

[/SIZE][/FONT]En which wireless is the best supported by Ubuntu?
[FONT=arial][SIZE=1]1. [/SIZE][/FONT][FONT=arial][SIZE=1]Dell Wireless 1397 (802.11 b/g)
2. [/SIZE][/FONT][FONT=arial][SIZE=1] Dell Wireless 1510 (802.11n)
3. [/SIZE][/FONT][FONT=arial][SIZE=1]Intel WiFi Link 5300 (802.11 a/g/n) (Centrino)
4. [/SIZE][/FONT][FONT=arial][SIZE=1]Intel WiFi Link 5100 (802.11 a/b/g/n 1x2)

I can't find what sound chipset the Studio 15 has, does anyone knows if the sound on that laptop is working in Ubuntu?

And what is your general opinion about the Dell Studio 15? Is it good supported by Ubuntu?

Thanks.
[/SIZE][/FONT]

---

### Post by clevertomato on 2009-12-29
Several folks have a Studio 15 with Ubuntu. I've read different experiences. I just got mine a few days ago and can tell you my thoughts.

I got the 512 MB ATI Mobility Radeon 4570 GPU. With the open source drivers for ATI, the brightness Fn keys work but resume comes back to a black screen. With the proprietary ATI drivers activated with System/Administration/Hardware Drivers the Fn keys for screen brightness stop working, but resume works.

I've tried adding "noapic", "acpi=off", and "acpi=force" by themselves and in combination with no success (some others claim this helps them). I can't live without suspend & resume, but the brightness keys are handy too, so I want both to work. I also really want/need to be able to have the system recognize when the lid is closed. Still hoping for answers.

Otherwise, I like the laptop except for there are NO status LEDs of any kind (except AC adapter / charging status). So there's no easy way to know if CAPS-LOCK and WiFi is on. Also no way to know hard disk drive access. Also no numberpad overlay on this keyboard. Crazy to leave these off, but I'll learn to live without them I guess.

Forgot to answer your other questions. I went with Intel 5300 wireless and have no problems. Also i went for the basic option of "HD Audio" and it works out of the box.

I'm running Karmic.

---

### Post by jml on 2009-12-29
If you are not absolutely set on getting a Dell, consider buying a laptop from System 76.  

[http://system76.com/index.php](http://system76.com/index.php)

This is a company based in Denver Colorado and they specialize in selling laptops, desktops and servers with Ubuntu preinstalled.  This is all they do.  They make sure that all of the laptop's functionality works out of the box.  I have purchased three computers (two laptops, and one netbook,) from them over the years and I have been very satisfied with all of them.  Their support both before and after the purchase is great.  They even administer a subforum on this site.  And no, I am not employed by them.  ;-)

Joe

---

### Post by SeePU on 2009-12-29
CaveManx,
Get the ATI card and the Intel 5300 wifi card.  The Intel 5300 wifi one is supported way better than the others.  It's also the one with the best wifi reception, supposedly.

I guess recommending the ATI card is more of a 'no choice' kind of thing but the ATI card will offer better options, allegedly.  If Dell could offer a Nvidia card instead, I'd say that one.

Which brings me to my question to the Dell owner:  Can you get 3D enabled on your Studio 15 and if so, with the fglrx driver or the radeon?   Which works better?

Is your worst problems, the hibernate/suspend issue?  

Thanks for any answers.  I was considering the same laptop with the same options but I really don't know if I want to take a chance on an ATI card.  Especially one in a laptop in which you're stuck with it.

---

### Post by clevertomato on 2009-12-29
@SeePU: The choice it gave me in System / Administration / Hardware Drivers is the fglrx drivers so that's what I tried. After installation the ATI Catalyst screen told me "software version: 8.66.10". I am not familiar with separate Radeon drivers for this. Where would I learn about that or get those?

I haven't run anything 3D but presumably I could with the fglrx ATI drivers. Catalyst settings all seemed to look ready to go.

I haven't yet had opportunity to test bluetooth, e-SATA, firewire, memory card reader, card expansion slot, HDMI, VGA. All the basic stuff (optical drive, sound, wifi, etc) seems to work fine out of the box, so for now, the suspend / resume issue does seem to be my worst Ubuntu-related problem.

I was hesitant to go with ATI too after reading on the forums, but I also read that ATI drivers (esp open source) are "coming of age" quickly. I also read posts from other Studio 15 owners who said theirs worked perfectly. I don't know why they apparently aren't experiencing same problems I am.  Anyway, I guess the open source ATI coming of age process isn't finished for what I need.

I got a bluray rewritable optical drive in mine so I was afraid to get the integrated GPU thinking it may be weak playing bluray or other HD stuff. As is, the laptop is certainly very functional, but I won't be super happy until I can resume, use the brightness keys, AND have lid closure awareness all at the same time with the same drivers.

---

### Post by SeePU on 2009-12-29
Don't use the 'restricted drivers' utility.  It will install older ATI drivers.

Go here and follow the instructions for 'Linux':
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Doing that will install the latest ATI proprietary (aka fglrx) driver:

If you want to switch and try the open source driver, I think you can edit xorg.conf and change the driver setting to 'radeon' (from 'fglrx') and it should switch automatically.  I haven't had a system yet in which I had ATI hardware that could switch so you're better off asking someone who has such hardware.  I have more experience with Nvidia drivers and Nvidia cards.

You can check 'Synaptic Package Manager, too, and do a search for 'radeon' or 'ATI.'  Then see what ati-based packages it has installed.  You should have 'radeon' already selected but it will override that driver if you have the proprietary driver installed and then X.Org will use that driver unless you switch to the radeon driver.

I think your features will be most optimized with the fglrx driver so I suggest trying the install I mentioned above.

If you have any problems or think there is any chance of any, use an editor and look at your xorg.conf file and see what is there now.  Alternatively, you can look at it with an Ubuntu live CD.  It's not 'officially' there unless you edit xorg.conf so just go to /etc/X11/xorg.conf with an editor.   Gedit... or use Nano.

I recommend you copy and past the current one (one you are currently using and what works sufficiently...for now) to an editor or Notes or OpenOffice doc etc.  Then copy the text and email it to yourself.  That way, you can always edit xorg.conf and restore your video settings.  There might be an easy or more 'automatic' fix with ATI drivers but again, not my area of expertise.

---

### Post by clevertomato on 2009-12-30
FYI, I just tried the ATI fglrx drivers from the ATI website, Catalyst v 9.12. I tried the package generation first but it failed. Then I installed using the Automatic uption. It installed, but didn't fix anything I needed to be fixed. Fn keys for brightness don't work and system is unaware of lid close (and does nothing when that event occurs).  UGH! I'm quite frustrated now.

---

### Post by SeePU on 2009-12-30
Did you choose the right drivers for your system?  There are 64-bit and 32-bit drivers for the respective Linux package.

If so, I am sorry that it didn't work for you but I assure you that ATI users have done that process.  I know because I am sure I have read of users doing it that way.  Sorry I couldn't be of help but like I said, ATI drivers installs are not my forte.  I am not familiar with the Catalyst/fglrx ATI install as I don't have a newer ATI card.

My laptop card is an older ATI mobile card which isn't even supported by the fglrx driver anymore.  Even when I use the open source radeon driver, I have to edit xorg.conf to obtain 3D capability in Ubuntu 9.10!

I suspect if you keep reading the thread or search in the forums, you will find some ATI owners who have gone through the same trials and eventually, there will be a procedure that ultimately works.  Sorry, again, that my suggestions didn't help.

---

### Post by clevertomato on 2009-12-30
I'm running Karmic amd64. I downloaded:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-12-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-12-x86.x86_64.run)

ran it according to instructions, and chose the automatic option. (First I tried the package generation option. It failed, so then I opted for automatic and it installed.)

I may try the 2.6.32 kernel. I hear it may solve the issues I'm having.

Thanks for trying to help me, SeePU. It sure beats silence ...  *cricket*

---

### Post by SeePU on 2009-12-31
Use these pages to install your driver.  The nvidia install works better but it does install the ATI driver and it works in Ubuntu, too.

[http://smxi.org/docs/](http://smxi.org/docs/)

[http://smxi.org/](http://smxi.org/)

[http://smxi.org/docs/sgfxi-manual.htm]("http://smxi.org/docs/sgfxi-manual.htm")

---

### Post by clevertomato on 2009-12-31
Thanks, SeePU, I'll have a look. I'm also in contact with a couple Studio owners who may help me with either recompiling my kernel or using a newer kernel.

Thanks.

---

