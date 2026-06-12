---
title: "ASUS X83Vm-X1"
date: 2009-01-02
forum: Hardware
---

### Post by cprofitt on 2009-01-02
I purchased [this]("http://www.bestbuy.com/site/olspage.jsp?skuId=9050055&type=product&id=1218012612475") laptop after having two HP dv5-1160us laptops have bad LCD screens... the great part is it was only $794.

The only issue I have had with is to date is running the liveCD... it would boot, but then lock up at random points. I was able to use the install from he liveCD however.

[B]Intel® Core&#8482;2 Duo processor P8400
[/B]Intel® PM45 chipset
**NVIDIA GeForce 9600M GS graphics**
Intel 5100n Wireless Card
Azalia audio chip
LED LCD Screen (1280x800)

If anyone has any other questions... just let me know.

---

### Post by hotweiss on 2009-01-02
> **PrivateVoid said:**
> I purchased [this]("http://www.bestbuy.com/site/olspage.jsp?skuId=9050055&type=product&id=1218012612475") laptop after having two HP dv5-1160us laptops have bad LCD screens... the great part is it was only $794.

The only issue I have had with is to date is running the liveCD... it would boot, but then lock up at random points. I was able to use the install from he liveCD however.

[B]Intel® Core™2 Duo processor P8400
[/B]Intel® PM45 chipset
**NVIDIA GeForce 9600M GS graphics**
Intel 5100n Wireless Card
Azalia audio chip
LED LCD Screen (1280x800)

If anyone has any other questions... just let me know.

Where did you get it at that price? That is a dam hot price for that configuration... Are you having any ACPI issues, like a dim screen?

---

### Post by cprofitt on 2009-01-02
> **hotweiss said:**
> Where did you get it at that price? That is a dam hot price for that configuration... Are you having any ACPI issues, like a dim screen?

My local Best Buy has them on sale... the website has them at $1049, but they are on sale at the local store.  (I would buy the actual ASUS n80 series from New Egg they were not on sale due to the additional 1 year warranty and slightly better video card and processor)

I have a very bright display at this point.

I should add that this model of 9600M GS has 1GB of video ram... which is overkill for Linux.

---

### Post by bettlebrox on 2009-01-03
What is the battery life like?

---

### Post by cprofitt on 2009-01-03
> **bettlebrox said:**
> What is the battery life like?

I was getting roughly 3 hours out of it... I ended up returning it due to issues with lock ups, jerky performance and shutdown issues... while perhaps there are fixes coming... I did not want a $858 (tax) paperweight or to be forced to run Windows.

---

### Post by dslink on 2009-01-14
I ran a live cd of Jaunty (want ext4), a daily build from last week, it worked but the video was screwed up, but that is a problem with most nvidia if not all cards under jaunty at the moment....

Right now i have been running hardy for a few hours and im in the middle of upgrading to intrepid,  at the moment nvidia isnt working but restricted kernel package wasn't installed.  It is currently running JFS, and is pretty fast...  it felt like it was unpacking files faster then my quad q6660 that i just reinstalled again tonight with ext3. (because i screwed up grub2 and the /boot partition for ext4)

Also to note under jaunty live cd,  it said "unknown nvidia card"
I have seen on other forms that this model and the 15.6" inch display one say they have a geforce 9600 GS card in it but people running cpuz and other windows apps say its a GT card not a GS but running "lspci" in hardy says its a 9600 GS.  Just wondering what others have seen

#edit
Other then that it's ok so far besides that the mouse buttons really suck badly on this thing.  I went from a 17" laptop to this 14.1 no problem with the keyboard, and unlike the HP laptops that i had the mouse is in the center of the space bar so you dont really move it while typing.

#edit
got the update and the nvidia drivers working fine in 8.10

---

### Post by ameseisch on 2009-03-24
got this laptop last weekend off of display at best-buy seems like great hardware for what I paid. Had some issues getting Ubuntu to install froze a couple of times at different places in the install process, but finally got it done.

still need to do some testing but it seems like everything works. haven't tested webcam and mic on skype yet, that was an issue on last notebook.

compiz is running but not smoothly. the cube is very jerky at times, which is not cool considering the beefy graphics card this thing has! I also had major issues with Gnome-do in docky mode. the zoom feature was totally bogging down. again a compiz related thing. a stable Gnome do 0.8.1 64bit is pushing what I should expect a bit maybe, but really hoping these graphics issues get sorted out for 9.04.

---

### Post by AlexVader on 2009-03-24
Hi Cprofitt

So You have a nice experience with Asus heh !?

I am posting this because being a Ubuntu user, I already posessed an Asus, the F3JR...

Ubuntu Linux compatibility, just 100%...  no complaints...  but when it comes to hardware reliability...   man...   >-(

So, I bought that piece of crap, and i used it, in the most normal and caring way, It is my work tool, I am an engineer and I do lots of CAD, and simulation for my projects...( its not that i punch and kick my laptops you know... lol  :-)  )

Anyway, the lower case of the lappy just broke, 7 months after i bought it, just like that, out of the blue, in the part where the lcd screen hinge connects with it, maybe due to the repetition of applied moment caused by that hinge, engineers like me call it fatigue loading ( although it is rather weird to happen in a polymer ( material of the lower case )

So all the effort was being transmitted to the other hinge making it more liable, so I sent it to repair shop, It was still covered by warranty.

Had the lappy away for 41 days, and they replaced the defective part.

After approx 5 months after that, THE NEW PART BROKE RIGHT IN THE SAME SPOT....   

So I went there, and demamded either a new lappy of the same brand, or my money back.

Lappy went back to repair shop, for 25 days and do you know what they did...?!

Man... they F**ck*ing replaced the part again...

Meaning that, from the end of the warranty on, I would be supposed to pay for new parts and labor every 6-5 months...  

I WILL NEVER AGAIN GIVE ONE CENT TO ASUS...  as simple as this...

So I bought a HP Dv5 Pavillion 1170, and so far, I have no complaints...

The build of the HP is far more strong than that of the Asus F3JR...

Just posted this here so that users in this forum may find my experience and this information useful..

---

### Post by avilella on 2009-04-05
Since you have access to a laptop with hybrid graphics and have tried to run Linux, please take a moment to provide the DSDT information for the laptop in this link:

[https://bugs.launchpad.net/bugs/312756](https://bugs.launchpad.net/bugs/312756)

DSDT is an acronym for Differentiated System Description Table. This table contains the Differentiated Definition Block, which supplies the information and configuration information about the base system. It is always inserted into the ACPI Namespace by the OS at boot time.

If you've got a laptop with a IGP and a hybrid Nvidia or ATi card, and you have tried to use Linux on it, you may have noticed that there are issues with the hybrid graphics setup. To help improve the Linux hybrid graphics support for this laptop, please attach your DSDT information to this Launchpad bug report specifying your laptop model:

[https://bugs.launchpad.net/bugs/312756](https://bugs.launchpad.net/bugs/312756)

To compile your DSDT information, install if you haven't already the acpidump and iasl tools:
sudo apt-get install acpidump iasl           # on Debian-based systems

Then run the following commands:

sudo acpidump > acpidump.txt
sudo acpixtract acpidump.txt
iasl -d DSDT.dat

This will create a DSDT.dsl file that you can attach to the bug report. This information will allow the developers to fully implement the hybrid graphics features for Linux.

---

