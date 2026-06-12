---
title: "Best integrated laptop video for Compiz?"
date: 2011-01-22
forum: Hardware
---

### Post by javyn999 on 2011-01-22
I'm in the market for a laptop, and unfortunately, the nicer models with the discrete Nvidia cards are out of my price range.

Would anyone be able to tell me which would be better to choose, a laptop with ATI or Intel graphics as far as Compiz effects go; cube, scaling, wobbly windows, etc?

How easy is it to install the drivers?  I've only used Ubuntu on computers with Nvidia before so all I've ever had to do is go to the proprietary drivers option and enable it.  Will the ATI and Intel be the same or will it be more complicated to get 3d effects to work?


I'm specifically considering Radeon HD 550v versus Intel Series 5 integrated graphics.  Thanks.

---

### Post by eshant_engineer on 2011-01-22
I have also subscribed to this thread..

in india Dell Inspiron 15R is coming with this graphics card i.e ATI 550v

---

### Post by javyn999 on 2011-01-22
bump?

---

### Post by cascade9 on 2011-01-23
By "Intel Series 5 integrated graphics" I'm guessing you mean a H55/H57 chipset. The video should run out of the box with that chipset ('sandy bridge' chipsets, aka H67 aka 'intel wants to push everybody to a new socket purely for profit reasons' wont run well out of the box on 10.10, you need to get the newest drivers with those chipsets). 

ATI HD550v (aka 'HD 4650' downclocked) should run compiz effects out of the box as well, but it would run better with an ATI/AMD GPU than an intel video chip. 

The driver install process should be the same for ATI/AMD as it was for nVidia. Because its a 'rebadged' chip, I cant be sure if it will run on the 4XXX drivers (most likely) or 5XXX drivers, or simply has no linux support at all. 

Lame choice, between a downclocked, crippled chip with a misleading name, and intels traditionally horrible video chips.....

---

### Post by sandy8925 on 2011-01-23
Intel graphics cards should be fine for Compiz. I have an old laptop with Intel GML 910/915 and Compiz advanced effects work fine on that(OK so the cube is jerky) and I was able to play 720p HD video. Anyway, newer Intel graphics cards would work better. Also, Intel cards work out of the box, you don't need to do anything.

Regarding ATI, my laptop has an ATI card as well but it's an older one. Compiz works fine and so does video playback. For newer cards like the 4xxx and 5xxx series, not all features are fully supported by the open source drivers, so I'm not sure about what works and doesn't but Compiz should work fine.

The ATI card will most likely have better performance than the Intel card.

Flash 10.2 supposedly supports hardware acceleration for video playback on Linux, but only using VDPAU which is right now usable only on Nvidia cards with the proprietary drivers.

---

### Post by javyn999 on 2011-01-24
Thanks for the help guys.  As luck would have it, I found something with a discrete Nvidia card in my budget.

15.6" widescreen
Core-i5 2.26ghz turbo up to 2.53
4 gig DDR3 1333 mhz
320 gig SATA 7200 rpm
8x dual layer DVD 
802.11 b/g/n
6-cell battery
512MB NVIDIA Geforce 310M discrete video
Integrated 1.3M Pixel Webcam

Ordered this off Dell Outlet as a refurb and along with a 15% online coupon for Vostros, came out to less than $600 with tax and shipping included.

Pretty much made all my concerns moot, and the harmony of an all Nvidia household has not been jeopardized lol.

edit:  Sandy, can you tell me how to enable hardware acceleration w/ flash?

---

### Post by Yellow Pasque on 2011-01-24
> can you tell me how to enable hardware acceleration w/ flash?
You need to be running 32-bit Ubuntu, the nvidia blob/binary driver and a Flash beta: [http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

---

### Post by javyn999 on 2011-01-24
ah, 64 bit here

---

### Post by cascade9 on 2011-01-25
> **javyn999 said:**
> Thanks for the help guys.  As luck would have it, I found something with a discrete Nvidia card in my budget.

15.6" widescreen
Core-i5 2.26ghz turbo up to 2.53
4 gig DDR3 1333 mhz
320 gig SATA 7200 rpm
8x dual layer DVD 
802.11 b/g/n
6-cell battery
512MB NVIDIA Geforce 310M discrete video
Integrated 1.3M Pixel Webcam


Vostro 3400? Guess what, you've just been caught by the nvidia 'optimus' trap. nVidia doesnt offer any support for optimus with linux, and unless you have a BIOS with an option to 'force' the nvidia GPU, you are stuck with intel graphics.

---

### Post by mastablasta on 2011-01-25
> **sandy8925 said:**
> Regarding ATI, my laptop has an ATI card as well but it's an older one. Compiz works fine and so does video playback. For newer cards like the 4xxx and 5xxx series, not all features are fully supported by the open source drivers, so I'm not sure about what works and doesn't but Compiz should work fine.
 .
 
they should have proprietary driver support.
 
aslo i think inspiron 15 used to be shipped with ubuntu. i am not sure if this is still the case...

---

### Post by javyn999 on 2011-01-27
> **cascade9 said:**
> Vostro 3400? Guess what, you've just been caught by the nvidia 'optimus' trap. nVidia doesnt offer any support for optimus with linux, and unless you have a BIOS with an option to 'force' the nvidia GPU, you are stuck with intel graphics.

Hmmm thanks I'll look when I get home from work.  I got a Vostro 3500, nowhere do I remember it saying "Optimus"?

---

### Post by rocthrttle on 2011-01-27
[http://www.frostbitesystems.com/](http://www.frostbitesystems.com/)

---

### Post by javyn999 on 2011-01-27
Well, according to my bios, the only video option available is Nvidia 310M, no option for Intel integrated.

But...when I was installing the drivers in Windows, the 310 M discreet drivers wouldn't install, had to get the 310M/Intel Switch drivers from Dell.

And in my Windows Device Manager, I have two displays one for Intel and one for Nvidia.  :(

No idea what's going on here.  This laptop's specs made no mention of Optimus and listed graphics as Nvidia 310M discreet.  If that's not the case I'm going to be upset.

---

### Post by Yellow Pasque on 2011-01-28
You're screwed. Switchable graphics won't work in Linux. If you have no BIOS option to switch off the Intel GPU, then you can only use the Intel GPU.

---

### Post by realzippy on 2011-01-28
There is a chance to be able to switch off the nvidia card on the dell vostro laptop (to save power):
[https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)
..but afaik it is not possible to use the nvidia card with the NVIDIA prop.
driver;using nouveau makes no sense since the 3D Intel sandybridge performance is
surprisingly good,compiz cube smoothly...
Anyway,do not buy NVIDIA Optimus without BIOS switch unless you want to run
W7.
Save the money and pick a laptop with intel graphics only..

**DO NOT BUY OPTIMUS !**
...unless they give us a switch.[AaronP : ]("http://www.nvnews.net/vbulletin/showthread.php?t=153321")!

*"We currently do not have plans to support display on Optimus systems where the display is connected to the Intel hardware.."*

---

### Post by javyn999 on 2011-01-28
This is a refurb laptop, not Sandy Bridge, but whatever came before it.

Thing is, I specifically paid more to get this with Nvidia over Intel video because I thought it would work better with compiz.  

If I return this lappy, I'm going to have eat a 15% restocking fee :(

Sigh.

Oh well, my fault for assuming Nvidia would just work in Linux.  I've been a loyal Nvidia customer for 10 years now for this reason.  Had I not been such a hardcore Nvidia fan, I surely would have opted for AMD/ATI since I hate Intel so much.  I should have stuck to my guns..

---

### Post by javyn999 on 2011-01-28
Zippy, I can't seem to find the info in that link with instructions on how to completely switch off the Nvidia GPU...

Do you have a more direct link?

---

### Post by realzippy on 2011-01-28
> **javyn999 said:**
> Zippy, I can't seem to find the info in that link with instructions on how to completely switch off the Nvidia GPU...

Do you have a more direct link?

From [https://launchpad.net/~hybrid-graphics-linux:](https://launchpad.net/~hybrid-graphics-linux:)

[I]You can try it by installing the module and calling it like this:
[/I]
```
git clone http://github.com/mkottman/acpi_call.git
cd acpi_call
make
sudo insmod acpi_call.ko
./test_off.sh

```
[I]If you see a "works!" message, it's working. On an unplugged laptop, clicking on the battery indicator before and after running the test.sh script, should show a difference of about an extra 1-3 hours battery life.
[/I]

As I understand the situation,you need at least kernel 2.6.35-24 for this.

Also have look at this [thread]("http://ubuntuforums.org/showthread.php?t=1676243")

..and follow the links given on launchpad:
[http://airlied.livejournal.com/74176.html](http://airlied.livejournal.com/74176.html)
[http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)
[http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)

---

### Post by javyn999 on 2011-01-28
Thanks!

---

