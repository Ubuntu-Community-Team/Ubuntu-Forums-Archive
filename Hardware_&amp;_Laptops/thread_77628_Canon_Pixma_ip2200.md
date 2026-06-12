---
title: "Canon Pixma ip2200"
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by Kako on 2005-10-17
Hi everyone,

Is there anyone out there who managed to setup this printer under 5.10 ?
As I'm a complete noob, grateful if you can give details on how to do that.

Best,
Kako

---

### Post by The Mekon on 2005-10-17
[QUOTE=Kako]Hi everyone,

Is there anyone out there who managed to setup this printer under 5.10 ?
As I'm a complete noob, grateful if you can give details on how to do that.

Best,
Kako[/QUOTE]

I don't have the ip2000 but use the ip3000.  When I was tying out Fedora 4 I received advice that I should use the BJC-7000 driver which appears to work quite well under 5.10.

Just select System, Administration, Printing and install your ip2000 using the BJC-7000 driver and try printing a test page.

Brian

---

### Post by Kallewoof on 2006-10-26
A year later, and this one on Edgy, not Breezy...

I have a Canon Pixma ip2200 but I'm unable to make it run under CUPS. I tried both the supplied vendor drivers from Canon themselves, and I tried the BJC-7000 drivers.

When I use the BJC-7000 drivers, the green light on the printer starts blinking when I try to print something, but simply stops after awhile without printing anything. 

When I use the vendor drivers, the blinking doesn't even happen. It just pretends that the printing went fine. CUPS says completed (immediately), while on BJC-7000, CUPS keeps it 'in progress' for a couple of seconds (during which the green light blinks on the printer).

So I know the printer is communicating with CUPS, but it's not printing anything. :/

Ideas?

-Kalle.

---

### Post by Kallewoof on 2006-10-26
I tried the TurboPrint drivers and they worked like a charm. It's pretty annoying to have to buy drivers for a printer when you bought the printer, but hey, at least it works. "Canon" is striked through on my list of printers for the future though, tell you that much. 

-Kalle.

---

### Post by Kallewoof on 2006-10-28
Solution: [https://wiki.ubuntu.com/CanonPixmaIP4200](https://wiki.ubuntu.com/CanonPixmaIP4200)

In my case, I simply had to link libtiff.so.3 -> libtiff.so.4, and after that it all worked flawlessly.

-Kalle.

---

### Post by Marewani on 2006-11-11
I modified the simbolic links as shown in the howto but nothing to do: my Pixma ip2200 doesn't work!!!](*,) 

I get this error message from gnome-cups:
Ready: No %%BoundingBox: comment in header!

And this is error_log:

E [11/Nov/2006:12:48:55 +0100] Filter "pstocanonij" for printer "iP2200" not available: No such file or directory

but where do I get the correct driver if even the ones I got from Canon don't work!!

many thanks

- Marewani

---

### Post by Kallewoof on 2006-11-11
The pstocanonij file is included in "cnijfilter-common". Do you have that file installed? Check dpkg -l "cnij*".

-Kalle.

[edited: My response was completely off.]

---

### Post by DoctorMO on 2006-11-11
If you get your canon printer working consider giving the guys and gals at guten-print a bell. Sascha will be glad to have information about how you got various canon printers working with the 4200 driver and do let them know if you find the colours are correct because they're known to be iffy on some printers.

---

### Post by Kallewoof on 2006-11-11
I did get my Canon Pixma IP2200 working. I have no idea who the guys and gals at guten-print are, though.

And the colors seem fine, though I haven't exactly printed any photos or anything. 

-Kalle.

---

### Post by Marewani on 2006-11-12
yes, cnijfilter-common is on my linux box.
Why do I have a cnijfilter-common-2.60-1.tar.gz on my root directory? It seems to be there after have installed the common pakg. There's a pstocanonij but I've no idea how to manage it (no "# make" from shell because it responses "no target" or "nothing to do")

thanks
Marewani

---

### Post by Marewani on 2006-11-12
Ok! I found my way!
pstocanonij was in th esource package and when I passed cnijfilter-common.src with alien it gave the package with the .tar.gz inside. So I removed the non source packg and then passed with alien the source one: and finally it works!!!!!
(it's been two weeks I'm working on this damned Pixma!!!)

Many thanks
Marewani

---

### Post by Kallewoof on 2006-11-12
You have mistakenly installed the source rpm instead of the binary rpm.

Remove the one you have installed, then copy cnijfilter-common-2.60-1.i386.rpm to a separate directory and do alien cnijfilter-common-2.60-1.i386.rpm there, then install the deb file.

It gets confusing because I don't think it names the src file correctly when alienized.

-Kalle.

[edit: I would delete this (didn't realize you'd fixed it until I posted) but I can't figure out how. Oh well. :)]

---

### Post by mxrv on 2006-11-15
> [Kallewoof: edit: I would delete this (didn't realize you'd fixed it until I posted) but I can't figure out how. Oh well. ]

Do not delete anything. Your last post helped me, so it might help the others too :) thanks

---

### Post by Kallewoof on 2006-11-15
Ah! Good to hear. :)

-Kalle.

---

### Post by rrabio on 2006-11-15
Hi
I've used the repository linked here
[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/)
there are others printers drivers too...
It works! and it seem to be open source... try it if you need...

---

