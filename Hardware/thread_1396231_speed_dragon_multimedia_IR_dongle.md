---
title: "speed dragon multimedia IR dongle"
date: 2010-02-01
forum: Hardware
---

### Post by violetdream on 2010-02-01
I got a cheap bluetooth/irda combo device. When I lsusb I get this:

Bus 002 Device 006: ID 0e55:110a Speed Dragon Multimedia, Ltd 

After further searching it seems like it's the mcs7780 drive from Moschip. I looked at the site here:

[http://www.moschip.com/mcs7780_downloads.php](http://www.moschip.com/mcs7780_downloads.php)

I also tried a couple of other sites with perhaps updated drivers, including:

[http://web.pdx.edu/~mendyke/ip7780.html]("http://web.pdx.edu/%7Emendyke/ip7780.html")
[http://readlist.com/lists/vger.kernel.org/linux-kernel/22/114409.html](http://readlist.com/lists/vger.kernel.org/linux-kernel/22/114409.html)

I keep getting errors that look like this:

mcs7780.c:562: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;

They all seem to be build for older kernels.

Out of curiosity, I also just tried modprobe mcs7780 but nothing happened (but no error)..anything I have to do after that?

Edit: Now I think the chipset is a Tanic S110 based on the name in the driver CD. No luck with that either since I don't know what to choose in LIRC.
second edit: according to this site: [http://www.newegg.com/Product/Product.aspx?Item=N82E16833328107](http://www.newegg.com/Product/Product.aspx?Item=N82E16833328107) either chipset can be used (although the poster didn't have luck with the moz drivers). So I just need help compiling the moz drivers

---

