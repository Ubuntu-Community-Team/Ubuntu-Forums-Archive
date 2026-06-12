---
title: "linux printing slower than winxp printing"
date: 2005-04-06
forum: Hardware &amp; Laptops
---

### Post by iomicifikko on 2005-04-06
i use to work with 2 prints (epson stylus color 680 and c20ux) i have no problems printing in linux couse i usually have to prinf little things in usual ways but i always notice that the printing process in linux is really slower than tying to do it with windows. not just that: there are really a few options in print properties (for example "economy" or more pages in one etc).

is there any kind of program to config a little bit better print options ?

thanks anyone!

bye

---

### Post by dcraven on 2005-04-06
Unfortunately I don't think so. This stuff is, I believe, driver specific and since Epson doesn't provide Linux drivers we need to make due with what is implemented in the drivers that are so kindly provided by our open source friends. Unless someone decides to append further functionality to the gimp-print drivers (I'll assume that is what you are using), they are what they are. We as Epson owners can at least say that our printers work in Linux. That's more than some other folks can say.. heh

It wouldn't hurt to send off a quick email to our friends at Epson to show that there is some interest on the Linux front however :). If more people began doing that then we may see some movement in that direction. Especially with companies like Epson. I just noticed yesterday that Linux isn't even listed as a "Compatible platform" for their printers which is a shame. I could understand if it said "Supported platform", but I'd say they are compatible.

Cheers,
~djc

---

### Post by iomicifikko on 2005-04-06
[QUOTE=dcraven]Unfortunately I don't think so. This stuff is, I believe, driver specific and since Epson doesn't provide Linux drivers we need to make due with what is implemented in the drivers that are so kindly provided by our open source friends. Unless someone decides to append further functionality to the gimp-print drivers (I'll assume that is what you are using), they are what they are. We as Epson owners can at least say that our printers work in Linux. That's more than some other folks can say.. heh

It wouldn't hurt to send off a quick email to our friends at Epson to show that there is some interest on the Linux front however :). If more people began doing that then we may see some movement in that direction. Especially with companies like Epson. I just noticed yesterday that Linux isn't even listed as a "Compatible platform" for their printers which is a shame. I could understand if it said "Supported platform", but I'd say they are compatible.

Cheers,
~djc[/QUOTE]
 about gimp-print drivers, i just read about it today searching about my prints at [www.linuxprinting.org](www.linuxprinting.org). to tell u the truth it is the first time i heard it;) and i dont understand really well what exactly is (how to associate to cups etc) but doing a little reasearch in my synaptic i've found that "foomatic-db-gimp-print", libgimpprint1, ijsgimpprint are present while cupsys-driver-gimpprint, upsys-driver-gimpprint-data not, do u think i have to install them? (im using openoffice for docs etc)

thanks for your reply, bye

---

### Post by dcraven on 2005-04-06
To be honest, I cannot say that I really know the difference in each of these packages and what they provide. I'm still struggling with the Debian package philosophy myself as a recent newcommer. I can tell you however that I have every one of those packages installed (including foomatic-db-gimp-print) and the driver is provided in the GNOME cups interface. I can see this in System -> Administration -> Printing, right clicking on my printer and selecting "Properties", then selecting the "Driver" tab. This provides a list of printer manufacturers and models of which mine is present (Epson, Stylus CX-5400) as is both of your models. The selected driver at the bottom is "High Quality Image (GIMP-Print)(gimp-print)(Suggested)".

I've never printed on this printer using Windows, but it works well in Linux using this driver. I'd assume that since the Windows driver comes from the manufacturer that it would be optimized better than the OSS one, although I'm quite happy with its performance.

HTH,
~djc

---

### Post by iomicifikko on 2005-04-07
[QUOTE=dcraven]To be honest, I cannot say that I really know the difference in each of these packages and what they provide. I'm still struggling with the Debian package philosophy myself as a recent newcommer. I can tell you however that I have every one of those packages installed (including foomatic-db-gimp-print) and the driver is provided in the GNOME cups interface. I can see this in System -> Administration -> Printing, right clicking on my printer and selecting "Properties", then selecting the "Driver" tab. This provides a list of printer manufacturers and models of which mine is present (Epson, Stylus CX-5400) as is both of your models. The selected driver at the bottom is "High Quality Image (GIMP-Print)(gimp-print)(Suggested)".

I've never printed on this printer using Windows, but it works well in Linux using this driver. I'd assume that since the Windows driver comes from the manufacturer that it would be optimized better than the OSS one, although I'm quite happy with its performance.

HTH,
~djc[/QUOTE]
 thank u man, i installed the last 2 missing packages and the "high quality.." driver option appeard (suggested) :). coming back home ill try it to see if i find differences in the printing process. according to synaptic the foomatic package is just the database of all supported prints and related drivers but the actual drivers are those 2 missing files. its strange that those packages are not in the default distro, usually ubuntu is cool in these kind of things;)

well, thanks again for ur support, byez!

---

### Post by dcraven on 2005-04-07
I'm curious to hear whether or not you ended up with any boost in performance.

Cheers,
~djc

---

