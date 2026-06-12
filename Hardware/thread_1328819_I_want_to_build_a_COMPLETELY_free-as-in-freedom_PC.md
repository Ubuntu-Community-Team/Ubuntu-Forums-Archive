---
title: "I want to build a COMPLETELY free-as-in-freedom PC - what hardware?"
date: 2009-11-16
forum: Hardware
---

### Post by youbuntu on 2009-11-16
Hi all. I want to build a COMPLETELY liberated PC, which ONLY uses free software - *no* non-free software installed *whatsoever*, and than includes *no* non-free drivers (I expect my graphics accelerator would need to be an Intel for this).

Can someone recommend the best manufacturers/parts for the job?. I wish to detach myself from depending on proprietary *anything* - NO NON-FREE SOFTWARE *OR* DRIVERS.

If anyone can help me in my quest, I'd love to hear back from you.

Thankyou :)

---

### Post by whoop on 2009-11-16
For your hardware check:
[http://www.fsf.org/resources/hw/](http://www.fsf.org/resources/hw/)

gNewSense could be your best distribution (especcially when coming from ubuntu), but there are other options.

Examples of free distributions:
[http://www.dragora.org/dokuwiki/doku.php](http://www.dragora.org/dokuwiki/doku.php)
[http://www.dynebolic.org/](http://www.dynebolic.org/)
[http://www.gnewsense.org/](http://www.gnewsense.org/)
[http://io.debian.net/~tar/gnustep/](http://io.debian.net/~tar/gnustep/)
[http://www.kongoni.co.za/](http://www.kongoni.co.za/)
[http://www.musix.org.ar/](http://www.musix.org.ar/)
[http://trisquel.info/](http://trisquel.info/)
[http://www.ututo.org/web/](http://www.ututo.org/web/)

---

### Post by youbuntu on 2009-11-16
> **whoop said:**
> For your hardware check:
[http://www.fsf.org/resources/hw/](http://www.fsf.org/resources/hw/)

gNewSense could be your best distribution (especcially when coming from ubuntu), but there are other options.

Examples of free distributions:
[http://www.dragora.org/dokuwiki/doku.php](http://www.dragora.org/dokuwiki/doku.php)
[http://www.dynebolic.org/](http://www.dynebolic.org/)
[http://www.gnewsense.org/](http://www.gnewsense.org/)
[http://io.debian.net/~tar/gnustep/]("http://io.debian.net/%7Etar/gnustep/")
[http://www.kongoni.co.za/](http://www.kongoni.co.za/)
[http://www.musix.org.ar/](http://www.musix.org.ar/)
[http://trisquel.info/](http://trisquel.info/)
[http://www.ututo.org/web/](http://www.ututo.org/web/)

Thankyou so much. Yes, I have GnewSense already as an ISO.

---

### Post by mivo on 2009-11-16
I wouldn't recommend an ATI video card to anyone, except you. ;) Currently, the open source ATI drivers aren't really very suitable for any sort of gaming or more demanding tasks, but they are progressing nicely, so in a year or so they should have improved. They currently work acceptably for normal desktop use. This is a better choice than an Intel integrated video chipset.

---

### Post by youbuntu on 2009-11-17
> **mivo said:**
> I wouldn't recommend an ATI video card to anyone, except you. ;) Currently, the open source ATI drivers aren't really very suitable for any sort of gaming or more demanding tasks, but they are progressing nicely, so in a year or so they should have improved. They currently work acceptably for normal desktop use. This is a better choice than an Intel integrated video chipset.

I need Compiz etc, and this is not a matter of convenience to me - I wish to run a system using 100% free software, but with good 3D effects performance, and so I shall be going the Intel way I think.

---

### Post by mivo on 2009-11-17
How well does the open source driver for Intel video chipsets work for 3D and demanding tasks? I didn't know there was a usable one, actually.

---

### Post by whoop on 2009-11-17
> **mivo said:**
> How well does the open source driver for Intel video chipsets work for 3D and demanding tasks? I didn't know there was a usable one, actually.

I have never found one that worked well, that's why I concur with your previous statement. Although I have to say I have not been using any intel video chipsets for some time, so I can't say that my experiences with them are still  an accurate representation of there functionality.

---

### Post by youbuntu on 2009-11-17
> **whoop said:**
> I have never found one that worked well, that's why I concur with your previous statement. Although I have to say I have not been using any intel video chipsets for some time, so I can't say that my experiences with them are still  an accurate representation of there functionality.

Define "3D" - do you mean 3D as-in games, or Compiz?. "3D" is a VERY broad term.

---

### Post by cascade9 on 2009-11-17
> **whoop said:**
> I have never found one that worked well, that's why I concur with your previous statement. Although I have to say I have not been using any intel video chipsets for some time, so I can't say that my experiences with them are still  an accurate representation of there functionality.

They arent much better than the old days. A little faster, but still very slow compared to anything Ati or nVidia churn out. 

There is hope though, maybe larrabee with its odd x86 based GPU will have open source drivers-

[http://en.wikipedia.org/wiki/Larrabee_(GPU](http://en.wikipedia.org/wiki/Larrabee_(GPU))

---

### Post by baytuni on 2009-11-17
Intel drivers are now in a stage of building smth. new and that's why they suck at the moment. There were a bus load of problems in Jaunty, they're better now in Karmic but not fully optimized. Still a lot of X problems. But it will get better sooner or later.

---

### Post by whoop on 2009-11-17
> **glossywhite said:**
> Define "3D" - do you mean 3D as-in games, or Compiz?. "3D" is a VERY broad term.

Well when I tinkered with them compiz worked but was choppy...

---

### Post by Yellow Pasque on 2009-11-18
ATI open-source 3D is available in Karmic with a little tweaking. It's not full 3D (limited support for OpenGL 2.x), but it runs Compiz well.

1. Remove proprietary driver (not applicable if you've never installed Catalyst): [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)
2. Install latest 2.6.32 kernel: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
3. Boot into that kernel
4. Install the xorg-edgers PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=karmic](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=karmic)
5. Update to the packages in the xorg-edgers PPA (using Update Manager)

---

### Post by Digikid on 2009-11-18
> **glossywhite said:**
> I need Compiz etc, and this is not a matter of convenience to me - I wish to run a system using 100% free software, but with good 3D effects performance, and so I shall be going the Intel way I think.


That is a contradiction there.

There are ATI free drivers out there and the ATI route is way better then anything Intel puts out.

---

### Post by megamania on 2009-11-18
> **glossywhite said:**
> *no* non-free software installed *whatsoever*
I don't think that's really possible, if you're taking it literally (and you probably are, considering your signature). 

Just think of the BIOS and all other on-board proprietary chips.

---

### Post by whoop on 2009-11-18
> **megamania said:**
> I don't think that's really possible, if you're taking it literally (and you probably are, considering your signature). 

Just think of the BIOS and all other on-board proprietary chips.

He can always try OpenBIOS ([http://www.openfirmware.info/Welcome_to_OpenBIOS](http://www.openfirmware.info/Welcome_to_OpenBIOS)) ;)

---

### Post by D-Sider on 2009-11-18
Don't you know Freedom isn't Free? It costs $1.05

---

