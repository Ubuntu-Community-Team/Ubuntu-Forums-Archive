---
title: "cannot read Dvd's"
date: 2009-06-06
forum: Hardware
---

### Post by blurust on 2009-06-06
Hey guys,

I am sorry for it may sound stupid but i am relatively a new user of linux..im using ubuntu 8.10 desktop edition at the moment..
Everything seems to working fine according to me on my HP laptop. but i cannot mount DVD's of any sort..
I can read and write Cd's though..rather perfectly..
Please help me guys..
Thanks in Advance.

---

### Post by khelben1979 on 2009-06-06
My suggestion here is that you install [dvd+rw+tools]("http://en.wikipedia.org/wiki/Dvd%2Brw-tools") and report back if it did the trick.

```
sudo apt-get install dvd+rw+tools
```

---

### Post by blurust on 2009-06-06
@khelben1979.

Nah bro it did not work..when i run the above command 
it says

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package dvd+rw+tools

---

### Post by khelben1979 on 2009-06-06
[Here you got it]("http://packages.ubuntu.com/jaunty/utils/dvd+rw-tools"). Check out the wiki link above if you have any thoughts about what it does and how it's used.

---

### Post by blurust on 2009-06-07
I think you got it all wrong..oops ...
but anyway my query was that i cant even Read Dvd's of any sort...be it a data or a music or video..:(

---

### Post by khelben1979 on 2009-06-07
Are you sure the drive is supposed to be able to read DVD:s? Some hardware information would be useful in this case.

---

### Post by hansdown on 2009-06-07
Hi blurust.

A few things may need to be installed.

Fist, click system> administration> software sources> Third party software.

Make sure the medibuntu box is checked.

Next, click system> administration> synaptic package manager.

Search for and install ubuntu-restricted extras,and libdvdcss2.

If this doesn't help, post back, because there may be more to install.

---

### Post by Kevbert on 2009-06-07
It may be that you don't have the codecs installed for video.
In terminal enter
```
sudo apt-get install ubuntu-restricted-extras
```
This package is in the multiverse repository.

---

### Post by blurust on 2009-06-12
Sorry guys..these suggestions did not help at all..
i still cannot mount DVD's....
@khelben1979:- yep it is a dvd combo drive...i recently shifted to ubuntu using a ubuntu DVD..so im thinking my hardware can't be kaput..well because isn't the lens for reading any media in a dvd combo drive is same..i mean for reading cd's and dvd's...? because i can easily mount any kind of cd...but not a dvd..

Oh and when i dmesg...it does show me the hardware...

this is what i get when i do:-

dmesg | grep -i dvd



[    4.092630] ata2.00: ATAPI: Slimtype DVD A  DS8AZH, NH61, max MWDMA2
[    4.135334] scsi 1:0:0:0: CD-ROM            Slimtype DVD A  DS8AZH    NH61 PQ: 0 ANSI: 5
[    4.313709] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray

---

### Post by khelben1979 on 2009-06-12
I suspect that your system is lacking installation of required packages for using the DVD drive.

[This page]("http://linux-sxs.org/multimedia/dvdplay.html") describes some of the things that you need. (I'm sure there's better documentation than this available, but I think it's a start)

If you're in real bad luck, then I wouldn't say it's impossible that you may need a better kernel which gives you better drivers for that DVD drive, but I think it's unlikely. The kernel which you're now using is not necessearily the same that was used when you first installed Ubuntu from DVD.

---

### Post by dandnsmith on 2009-06-12
> **blurust said:**
> ..so im thinking my hardware can't be kaput..well because isn't the lens for reading any media in a dvd combo drive is same..i mean for reading cd's and dvd's...? because i can easily mount any kind of cd...but not a dvd..

The lens assembly is, very often, the same (simplified hardware), BUT the frequencies used for the lasers are different - so you can lose ability to read CDs but not DVDs or vice versa (it's happened to me several times)

---

### Post by blurust on 2009-06-13
ermmm i think i did update the kernel while installing the graphic card driver after installing ubuntu...so in that case im quite sure that is not an issue...
still trying to install all these things that you have mentioned..will get back soon...and on the DVD front...no updates...problem still persists...

---

### Post by blurust on 2009-06-13
oh and what if i want to use a Data Dvd.. ?? Xine will not help there will it ?

---

### Post by blurust on 2009-06-13
Hey guys..

Still not solved :(

i installed Gxine and other stuff but i still cant load any movie DVD's..
when i try and open it from Gxine it says 


No input plugin was found.
Maybe the file does not exist or cannot be accessed, or there is an error in the URL.

Read error from:
/dev/dvd


And as far as software source manager is concerned ..in the third party tab...it does not show me Medibuntu..:(

I am confused and im almost giving up...and 
i think this might be an important peice of info...


WHEN THERE IS A DISK IN THE CD TRAY...UBUNTU DOES NOT BOOT...SO DOES IT MEAN IT CAN DETECT IT ??

Ubuntu veterens !! I call for all of you..:)

Peace out..!!

---

### Post by khelben1979 on 2009-06-13
[Ubuntu documentation on Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by dandnsmith on 2009-06-13
> **blurust said:**
> 
WHEN THERE IS A DISK IN THE CD TRAY...UBUNTU DOES NOT BOOT...SO DOES IT MEAN IT CAN DETECT IT ??

That would depend on exactly what happens 
- it could be that the BIOS is trying to boot from the CD
- it could be that the disk order isn't what grub was expecting

Do you get any error messages?

---

### Post by blurust on 2009-06-14
Hey dandnsmith..

No it does not give me any error messages...its just that i was ruling out the possibility of my hardware being kaput...

---

### Post by dandnsmith on 2009-06-14
> **blurust said:**
> Hey dandnsmith..

No it does not give me any error messages...its just that i was ruling out the possibility of my hardware being kaput...

I'm afraid it doesn't quite do that - I envisage the situation where the drive is detected by the BIOS, the drive registers the presence of a DVD or CD, and then Ubuntu won't boot (the presence of the DVD isn't necessary to affect the boot, actually), or the PC won't boot from the CD/DVD (just because it cannot be read).

A historical note: at one stage I had CD drive problems, and I worked out, by experimentation, that the drive could still be registered if the cable was plugged in the wrong way round, but data could not be read successfully from a properly working drive. The drive was faulty, it turned out.

---

