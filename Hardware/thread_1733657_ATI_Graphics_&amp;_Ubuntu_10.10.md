---
title: "ATI Graphics &amp; Ubuntu 10.10?"
date: 2011-04-19
forum: Hardware
---

### Post by TheCadaver on 2011-04-19
I recently purchased the HIS ATI Radeon HD 4670 Graphics Card off of newegg for the computer I had recently built, but upon arrival, the back of the box stated, under system requirements, that it's for windows (said no such thing under the description of the purchase, which is why I bought it). 

So, is there any kind of compatibility between ATI Graphics Cards and Ubuntu (10.10)? Is it compatible by default, or is there software to be added for compatibility, or any work with the terminal? First time on posting on this forum and all, and yeah, please post your replies :p

---

### Post by marin123 on 2011-04-19
> **TheCadaver said:**
> I recently purchased the HIS ATI Radeon HD 4670 Graphics Card off of newegg for the computer I had recently built, but upon arrival, the back of the box stated, under system requirements, that it's for windows (said no such thing under the description of the purchase, which is why I bought it). 

So, is there any kind of compatibility between ATI Graphics Cards and Ubuntu (10.10)? Is it compatible by default, or is there software to be added for compatibility, or any work with the terminal? First time on posting on this forum and all, and yeah, please post your replies :p

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

find your driver, install it and enjoy :)

---

### Post by TheCadaver on 2011-04-19
> **marin123 said:**
> [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

find your driver, install it and enjoy :)

hmm, I built the computer with all intel parts, none were amd.

---

### Post by marin123 on 2011-04-19
ati graphics card? as in amd ati?

---

### Post by TheCadaver on 2011-04-19
Radeon ATI. Doesn't mention amd or intel anywhere i read, and I've seen intels with Radeon, so..

---

### Post by qamelian on 2011-04-19
> **TheCadaver said:**
> Radeon ATI. Doesn't mention amd or intel anywhere i read, and I've seen intels with Radeon, so..
AMD owns ATI. They bought them out quite a while ago.

---

### Post by coffeecat on 2011-04-19
Just stick the ATI/AMD card in your computer and boot up a live CD of Ubuntu 10.10. It will work with the default driver.

---

### Post by TheCadaver on 2011-04-19
Thanks, I'm trying coffeecat's idea now. does it have to be a live cd, or could a normal 10.10 system upgrade directly from the computer work?

I tried to use the graphics card's istallation CD provided in the box, but, being a windows device it obviously didn't work normally. How necessary is this...?

---

### Post by coffeecat on 2011-04-19
I only suggested a live CD because you didn't post any details of any installed OS that you have. Live CDs are a useful way of seeing how compatible your hardware is with out-of-the-box drivers. You can forget installation CDs. That's a Windows thing. If the default open source driver is not adequate for your needs, you can install the proprietary driver for ATI cards from the Ubuntu repositories.

---

### Post by marin123 on 2011-04-20
@coffecat, he was asking about ubuntu 10.10 so we know what os he has or will have..

and about drivers for your graphics: you will have a working ubuntu without proprietary drivers but if you need 3d acceleration you will have to install proprietary drivers.

if you get over the fact that your card was manufactured at amd, you can click the link that i posted and choose your card and download driver. i also have ati radeon card in my laptop and i downloaded drivers from that link...

---

### Post by coffeecat on 2011-04-20
> **marin123 said:**
> @coffecat, he was asking about ubuntu 10.10 so we know what os he has or will have..

> **coffeecat said:**
> [SIZE=4]installed[/SIZE] OS

The OP was talking about an upgrade in their previous post. It wasn't clear whether they already had an [SIZE=4]installed[/SIZE] earlier version of Ubuntu. :wink:

---

### Post by TheCadaver on 2011-04-20
Yeah, i put it in my computer and all, i'm not sure if it's working. it's detected by my system, but doesn't really give me any benefit from when i was using integrated graphics, and when tested on things like youtube, there's not much of a change.

When i type in glxgears in the terminal, i get "segmentation fault". when i type in "glxinfo | grep rendering" and press enter, it just takes me to the next line and doesn't do anything. finally, when i type in "lspci | grep VGA", i get "01:00.0 VGA compatible controller: ATI Technologies Inc RV730XT [Radeon HD 4670]", which is the name of my graphics card, and yeah, it's a recognized and, under "additional drivers", it says it's been tested by ubuntu devlopers and all.

---

### Post by marin123 on 2011-04-20
> **TheCadaver said:**
> Yeah, i put it in my computer and all, i'm not sure if it's working. it's detected by my system, but doesn't really give me any benefit from when i was using integrated graphics, and when tested on things like youtube, there's not much of a change.

When i type in glxgears in the terminal, i get "segmentation fault". when i type in "glxinfo | grep rendering" and press enter, it just takes me to the next line and doesn't do anything. finally, when i type in "lspci | grep VGA", i get "01:00.0 VGA compatible controller: ATI Technologies Inc RV730XT [Radeon HD 4670]", which is the name of my graphics card, and yeah, it's a recognized and, under "additional drivers", it says it's been tested by ubuntu devlopers and all.

you can install drivers from Additional drivers menu, but on ati's website are newer... i didnt see any difference from the two.
if you install those drivers you will see improved graphics performance..

---

### Post by Yellow Pasque on 2011-04-20
Can you post /var/log/Xorg.0.log?

> and about drivers for your graphics: you will have a working ubuntu without proprietary drivers but if you need 3d acceleration you will have to install proprietary drivers.
False. Open-source drivers are 3D-accelerated as well.

---

### Post by TheCadaver on 2011-04-20
> **marin123 said:**
> you can install drivers from Additional drivers menu, but on ati's website are newer... i didnt see any difference from the two.
if you install those drivers you will see improved graphics performance..

Alright, I did that, but when I click on it, it says I need to open it using an application. Now what? Sorry, I've been an ubuntu user for 4 years, but I'm kind of a noob at it.

Also, on the additional drivers screen, it says my graphics card is proprietary.

---

### Post by Yellow Pasque on 2011-04-20
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)

---

### Post by TheCadaver on 2011-04-20
I followed the link above and while reading found this section than warns me about the drivers to be installed from the driver page as they offer the catalyst 9-3 Driver which doesn't support maverick? I've already installed from their driver page, though. I can't tell if the warning is for the drivers listed above it, or for the driver list overall.

The warning: 

[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx)

---

### Post by marin123 on 2011-04-20
if you mean how to install ati driver, you need to make it executable (right-click -> Properties -> Permissions -> Allow to execute) and double-click and choose Run.

if its not compatible with maverick, it wont install (it detects kernel version).

@Temujin: i didnt know that open source drivers have 3d, but i couldnt play Hive Rise with open source drivers, i had to install fglrx...

---

### Post by TheCadaver on 2011-04-20
> **marin123 said:**
> if you mean how to install ati driver, you need to make it executable (right-click -> Properties -> Permissions -> Allow to execute) and double-click and choose Run.

if its not compatible with maverick, it wont install (it detects kernel version).

@Temujin: i didnt know that open source drivers have 3d, but i couldnt play Hive Rise with open source drivers, i had to install fglrx...

Right click what, on where? there's nothing i can right click on the additional drivers screen.

---

### Post by Yellow Pasque on 2011-04-20
> **TheCadaver said:**
> I followed the link above and while reading found this section than warns me about the drivers to be installed from the driver page as they offer the catalyst 9-3 Driver...

Since your card is not on that list, the big red warning does not apply to you... More specifically, start here: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

---

### Post by Kal Sho on 2011-04-20
[This link]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") should help you out.

---

### Post by Yellow Pasque on 2011-04-20
Your link points to my link. Linky linky.

---

### Post by TheCadaver on 2011-04-20
followed temujin's link, and it seems to have worked, as now i can put my visual effects to the maximum, and 1080p runs great on youtube (i have multiple hdmi cables, yet don't have an hdmi monitor yet, but i'm looking towards it, but either way it looks great.) Except, on games, the fps still isn't the greatest. People with the same graphics card that i've bought have told me of very high frame rates with this card (40+). Is the frame rate an issue of the graphics card, or of the internet connection? that should be the final question of this thread before all my questions are answered :)

---

