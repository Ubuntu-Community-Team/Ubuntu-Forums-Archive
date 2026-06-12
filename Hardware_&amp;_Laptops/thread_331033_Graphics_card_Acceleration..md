---
title: "Graphics card Acceleration."
date: 2007-01-04
forum: Hardware &amp; Laptops
---

### Post by justin_c18 on 2007-01-04
I'm running a Compaq Pentium III 1.0ghz Deskpro EN ENS/P1,0/20e/6/128cn US
I'm not too sure what type of graphics card it has, nor can I find out in BIOS. Would anyone know what graphics card it has, and if I can get acceleration out of her? 

When I first got it, it had XP on it, and it ZIPPED! Now that I have Linux, metacity/bulky icons, it's not so fast anymore. I can't really even move around XMMS too much, because the acceleration isn't there and XMMS follows the pointer. So please, if you know anything about this old computer, let me know hardware specs, etc... Is there a program that I can run that'll tell me all about my hardware so I can find out, if no one replies on situation I am having?

It's a small form factor computer(desktop) ANother question, would the same type of sdram in my emonster 600mhz computer work in this computer? I don't know anything about hardware so I'd appreciate all the information given. I thank you in advance!

-J

[CENTER]_*on this episode of this old computer, it's justin_c18....*_[/CENTER]
Norm Abram, ROCKED/s!

---

### Post by 23meg on 2007-01-04
Look in System / Administration / Device Manager and see what your graphics device is listed as.

---

### Post by justin_c18 on 2007-01-04
Thanks for the reply;

If it's the chipset graphics controller im suppose to be looking at, it is a 

Intel Corporation
82815 CGC [Chipset Graphics Controller]
Status
PCI
device type Unknown
capabilities Unknown

If that's not the right thing, let me know, please.

---

### Post by zgornel on 2007-01-04
It's the right thing.

---

### Post by justin_c18 on 2007-01-04
K, what kind of card is it then, can I accelerate it?

I've found more information I think;

Intel® 815 Chipset Family: 82815 Graphics and Memory Controller

WIll I be able to install a driver on this machine by following

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

I've installed drivers on my other machine, just not on this one. I just don't want to mess anything up.

I'm not sure if it's an  ATI card, or nVidia.

Thanks in advance.

---

### Post by dannyboy79 on 2007-01-04
you don't have nvidia or ati, you have an intel onboard graphics card. I am not sure how well opengl will work if even at all but I jhust did a gogle search using linux drivers for 82815 intel and i returned this website which looks promising:
[http://www.intellinuxgraphics.org/index.html](http://www.intellinuxgraphics.org/index.html)
you can really help yourself by using either gogle or the search function within this forum prior to posting a thread. good luck

---

### Post by dannyboy79 on 2007-01-04
> **justin_c18 said:**
> K, what kind of card is it then, can I accelerate it?

I've found more information I think;

Intel® 815 Chipset Family: 82815 Graphics and Memory Controller

WIll I be able to install a driver on this machine by following

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

I've installed drivers on my other machine, just not on this one. I just don't want to mess anything up.

I'm not sure if it's an  ATI card, or nVidia.

Thanks in advance.

unforutunately you pointed this guy toward a how-to that isn't even for his graphics chipset. you can really make a newbie not like ubuntu by making him go thru a super long tutorial which won't even work to begin with. I would suggest if you're going to help people that you ACTUALLY HELP instead of just "trying to help" by providing suggestions that you aren't even sure if they work. 

the link you provided specifically states: 
How to install Graphics Driver (Intel) 
Note: This driver is for Intel® 82830M, 82845G, 82852GM, 82855GM, 82865G, and 82915G/GM graphics controller-based products **only**

and no where does it state 82815.

---

### Post by zgornel on 2007-01-04
Try *glxinfo |grep direct* to see if direct rendering is enabled. The i810 X driver should be used.

---

### Post by justin_c18 on 2007-01-05
> **dannyboy79 said:**
> unforutunately you pointed this guy toward a how-to that isn't even for his graphics chipset. you can really make a newbie not like ubuntu by making him go thru a super long tutorial which won't even work to begin with. I would suggest if you're going to help people that you ACTUALLY HELP instead of just "trying to help" by providing suggestions that you aren't even sure if they work. 

the link you provided specifically states: 
How to install Graphics Driver (Intel) 
Note: This driver is for Intel® 82830M, 82845G, 82852GM, 82855GM, 82865G, and 82915G/GM graphics controller-based products **only**

and no where does it state 82815.

It was me that replied back to the thread, just to see if anyone could reference from it. I thought maybe i815 would be the same because of the 82"**815**" in the number.

---

### Post by justin_c18 on 2007-01-05
> **zgornel said:**
> Try *glxinfo |grep direct* to see if direct rendering is enabled. The i810 X driver should be used.

Thanks, I'll try that out.

---

### Post by Amaroq on 2007-01-08
I've been searching for information about this card myself, and came upon this thread. It sounds like me and justin_c18 have exactly the same card. An 82815. The series is, indeed, the 815 series, not the 810.

I tried *glxinfo | grep direct* like zgornel suggested, and here's what I got.

[b][i]direct rendering: No
OpenGL renderer string: Mesa GLX Indirect[/i][/b]

I'm running an IBM Netvista 6648-TAU

EDIT: Uh oh. I found out from someone that this card can only do acceleration when you have it set to 16 bit color.

---

### Post by Axcess on 2007-01-17
I am also looking at one of these cards. I have a Gateway Profile 3, which is pretty much non upgradable, however it makes an excelent machine for saving space. it has the intel 815e chipset in it.
specs:
[http://support.gateway.com/support/manlib/Profile/Profile3/8508183/8508183.htm](http://support.gateway.com/support/manlib/Profile/Profile3/8508183/8508183.htm)

intel driver i found the provided rpm does not seem to be too useful.
[http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=N&ProductID=797&DwnldID=2702&strOSs=&OSFullName=&lang=eng](http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=N&ProductID=797&DwnldID=2702&strOSs=&OSFullName=&lang=eng)

---

### Post by Axcess on 2007-01-17
heres what i did, i downloaded the intel package, and then i used alien to convert it to a deb file. after that i unpacked it and restarted. nothing

---

### Post by laxmanb on 2007-01-20
Yeah... can anybody give instructions on how to turn direct rendering on... i have the same card... but even screensavers render horribly right now!

---

### Post by cefn on 2007-01-30
Isn't the xserver-xorg-driver-i810 package, available through aptitude a suitable package.

I think you can install this simply with...

sudo aptitude install xserver-xorg-driver-i810

...but I'm in the middle of the Edgy upgrade so can't test any acceleration out with my  Intel 82815 CGC.

I have the same card in my Hewlett Packard Vetra box. I don't think the card is especially capable, but I'll let you know if I get any 3D or direct rendering out of it after the driver is installed.

---

### Post by Amaroq on 2007-02-06
I just tried that, but it had no effect for me. The card can only direct render on 16 bit color though... maybe setting it to that will make a difference.

Oh, and forget what I said about i815. I tried changing my xorg.conf to make i810 i815... the results weren't pretty. It couldn't load the xorg.conf. Believe me, it's pretty scary when that happens. I had to figure out how to undo the change I made before I could use my system in anything other than a terminal mode.

How do you reduce your bitrate from 24 to 16 anyway?

EDIT: Someone told me in #ubuntu IRC room.

sudo dpkg-reconfigure xserver-xorg

Run that, and keep all of the settings the way they are, but when you get to the 16 or 24 option for the color depth, set it to 16, log out and then log back into your system. You should have direct draw then.

---

### Post by texasjim on 2007-04-14
16 bit color worked for my intel 82810 adapter.  Have had my head caught in GLXGEARS for 2 days, running reconfig and taking all defaults except 16-bit color unjammed me. 
  Thanks
 Jim

EDIT: Got my red progress bar back, been gone since I started monkeying with X.

---

