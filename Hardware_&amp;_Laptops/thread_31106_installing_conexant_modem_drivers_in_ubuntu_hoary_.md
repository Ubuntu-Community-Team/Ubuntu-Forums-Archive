---
title: "installing conexant modem drivers in ubuntu hoary 5.04"
date: 2005-05-01
forum: Hardware &amp; Laptops
---

### Post by unisol on 2005-05-01
itried everything i even moved my modem to a diofferent pci slot no luck i am at my wits end when i try to install driver using dpkg it tells me it cant find the package i tried dselect itried everything no luck anyone have any ideas

---

### Post by 23meg on 2005-05-01
to the best of my knowledge, you need proprietary modem drivers from [http://www.linuxant.com](http://www.linuxant.com) in order to connect at any speed higher than 14440 bps.

---

### Post by unisol on 2005-05-01
i got the drivers but dpkg keeps telling me it cant find the package(hcfpcimodem_1.05full_386.deb)where is it looking for the package where should i put it

---

### Post by 23meg on 2005-05-01
i might be wrong but what you've downloaded should be a source package that dpkg cannot install. you'll have to compile it yourself if this is the case. are you sure it's a binary .deb package?

---

### Post by unisol on 2005-05-01
yes its a .deb package i downloaded .deb and .tar.gz but being new to linux im stuck its not like windows but i dont want to give up

---

### Post by nad on 2005-05-01
If the download is on your desktop, the command: sudo dpkg -i Desktop/hcfpcimodem_1.05full_386.deb  should do the trick. You just need to tell dpkg exactly where to find the file. It doesn't matter where it is.

---

### Post by 23meg on 2005-05-01
check out [this thread](http://www.ubuntuforums.org/showthread.php?t=16200&highlight=conexant+compile) if you haven't already.

---

### Post by unisol on 2005-05-02
[QUOTE=nad]If the download is on your desktop, the command: sudo dpkg -i Desktop/hcfpcimodem_1.05full_386.deb  should do the trick. You just need to tell dpkg exactly where to find the file. It doesn't matter where it is.[/QUOTE]
i tried what you said it tells me Desktop/hcfpcimodem_1.056full_386.deb is not a directory and still cannot find the package. someone else told me i would have to pay for a driver and liscense from lunixant. what goes here

---

### Post by nad on 2005-05-02
Perhaps you could use the Search for Files applet in the Computer pull down menu to find it. Only you know where you downloaded it to. The Desktop directory is the default for firefox.

The free driver is limited to 14400 baud. The $14.95 driver for your modem may be fully compliant with v92.

Upon reading several threads here regarding the installation of the linuxant drivers, the most cost and time effective solution is to purchase a real modem for $30-40.

---

### Post by unisol on 2005-05-02
[QUOTE=nad]Perhaps you could use the Search for Files applet in the Computer pull down menu to find it. Only you know where you downloaded it to. The Desktop directory is the default for firefox.

The free driver is limited to 14400 baud. The $14.95 driver for your modem may be fully compliant with v92.

Upon reading several threads here regarding the installation of the linuxant drivers, the most cost and time effective solution is to purchase a real modem for $30-40.[/QUOTE]
 i downloaded it om my other computer and put it on a floppy disk and copied it to the desktop of my computer running linux. i also burned it onto a cd is there a way to edit sources .lst to include the floppy and cdrom.i think for now ill probably buy the drivers  thanks for all your help

---

### Post by unisol on 2005-05-06
[QUOTE=nad]Perhaps you could use the Search for Files applet in the Computer pull down menu to find it. Only you know where you downloaded it to. The Desktop directory is the default for firefox.

The free driver is limited to 14400 baud. The $14.95 driver for your modem may be fully compliant with v92.

Upon reading several threads here regarding the installation of the linuxant drivers, the most cost and time effective solution is to purchase a real modem for $30-40.[/QUOTE]
thanks for your help i got the driver to install now it wants me to rebuild the source header so im off to try thanks again

---

### Post by unisol on 2005-05-06
[QUOTE=23meg]check out [this thread](http://www.ubuntuforums.org/showthread.php?t=16200&highlight=conexant+compile) if you haven't already.[/QUOTE]
thanks for your help the driver will install i just have to rebuild the source headers off on another adventure

---

### Post by 23meg on 2005-05-06
good luck, and let us know how you fare. i hope an open source driver will surface soon and save us poor conexant owners from the linuxant nightmare. i'm glad that i don't regularly use dialup, but i don't know what i'm going to do to get connected the next time i travel! perhaps buy a $30 usb modem..

---

### Post by GTKpower on 2005-05-06
Hope you get it to work.

I had the same problem.  I didn't even bother to pursue the issue.  A BIG nightmare.

I just went out to a local electronics shop that sells used equipment, and snapped up a US Robotics 56k external hardware modem for 12 bucks.  Plugged the sucker in, GnomePPP recognized it immediately.  It's pretty fast for a 56k, and very stable.  Used hardware modems are everywhere, at rock-bottom proces, and they work nicely.

Couldn't be happier with my dialup.

So, if you want to avoid the headaches, and want a 56k modem that "just works", hunt around a bit for a used external hardware modem.  Shouldn't be expensive at all.  I heartily recommend a US Robotics 56k Faxmodem.  That model is GUARANTEED to work with Linux.  Most Hardware modems work with Linux anyway.

Plus, these days, you've got the option of a sort of high-speed connection without actual high-speed - that is, it's a slower DSL version, I tihnk.  Costs alot less than high speed, but is ALOT faster than dialup.  Try giving that a shot when you get tired of dialup.

Good Luck!

---

### Post by az on 2005-05-06
sudo apt-get install linux-headers-2.6.10-5-386 build-essential

You should be good for the headers.


If you want to use linux, conexant (as well as certain other hardware vendors) will leave a bad taste in your mouth.  Some Hardware vendors care about your freedom, others do not.

Lucent and Intel have better linux support for their modem products.

---

### Post by unisol on 2005-05-06
[QUOTE=23meg]good luck, and let us know how you fare. i hope an open source driver will surface soon and save us poor conexant owners from the linuxant nightmare. i'm glad that i don't regularly use dialup, but i don't know what i'm going to do to get connected the next time i travel! perhaps buy a $30 usb modem..[/QUOTE]
well ive been trying to compile the source headers but every directory i type in it says no modules compiled for hoary i did  a search and im not sure where the kernel is stored please help im running out of time a lot of people told me just install the modem driver its not that simple also im running an alphja of hoary

---

### Post by az on 2005-05-06
sudo apt-get install linux-headers-2.6.10-5-386 build-essential

Do uname -r

Install the version of linux-headers that corresponds to that.  You do not need to compile the headers.  Just install that package.

---

### Post by unisol on 2005-05-10
[QUOTE=23meg]check out [this thread](http://www.ubuntuforums.org/showthread.php?t=16200&highlight=conexant+compile) if you haven't already.[/QUOTE]
  i went out and bought a creative labs usb modem blaster for linux but i still cant get it to work can you please help me out

---

### Post by unisol on 2005-05-11
[QUOTE=23meg]check out [this thread](http://www.ubuntuforums.org/showthread.php?t=16200&highlight=conexant+compile) if you haven't already.[/QUOTE]
i bought a us robitics pro 56k modem its compatible with kernel 2.3 and higher but i still cant get it to work itried wvdial.conf, minicom but no luck if i cant get this one to work i was told the driver might not be loading trying modprobe see what happens

---

