---
title: "Looking for a motherboard with 8 sata ports"
date: 2008-10-26
forum: Hardware
---

### Post by shunthemask on 2008-10-26
Hi,

I'm looking for a motherboard with 8 sata ports that has good Ubuntu compatibility.  Does anyone have any recommendations?

Thanks kindly.

---

### Post by Lord Xeb on 2008-10-26
First off, How much ram do you want it to support? What form factor? What kind of board: AMD or Intel? How many PCI Express slots do you want? Do you want to use ATI, or Nividia? Do you plan to do Crossfire or SLI?

---

### Post by shaggy999 on 2008-10-26
I don't know about Ubuntu compatability, but if you go to newegg you can search and set the search parameters to 8 sata ports (as well as any other restrictions you want) to see what's available. Then write down those motherboards and search with google to see if they work with Ubuntu.

I'm assuming so many sata ports are because you are building a large file server? If so, are you installing the motherboard into a server chassis? If so, make sure the motherboard is designed to fit into server cases.

---

### Post by Lord Xeb on 2008-10-26
Intel: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131295](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131295)

I cannot find an AMD board that supports 8 SATA ports

---

### Post by starcannon on 2008-10-27
Heres a list of newegg boards (some Asus ones even) with 8 sata ports.
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010200280+1296819456&Configurator=&Subcategory=280&description=&Ntk=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010200280+1296819456&Configurator=&Subcategory=280&description=&Ntk=&srchInDesc=)

Have fun.

---

### Post by shunthemask on 2008-10-27
Thanks all for the ideas.  I now realize that I was a bit sparse on the details when I first posted.  What I am looking to do is to build a media/file/torrent server based on an Nvidia card and Intel 775 chip and keep mirrors of all my data. That's why I am looking for so many ports.  Nvidia is my choice because it's well-supported.

I would be adding a tuner card to the setup, but I have yet to research them.  I figure that anything P35 or newer would do the trick because it would have any PCI or PCI Express port that I would need.  I probably wouldn't add any expansion cards except for the video, tuner and possibly a NIC.  I have read the reviews on Newegg and they say that all of the motherboards there don't have the best Ubuntu compatibility (they're P43 and p45 based).  I would probably be adding DDR2 800 memory to the setup because it's cheap.  A gig or two would probably do just fine.

As far as a case goes, I have an [Antec SLK3800]("http://www.antec.com/usa/productDetails.php?lan=us&id=93800&type=1") mid tower hanging around that has 5 internal 3.5" bays and 2 external.  That plus a sata DVD would use up all 8 sata ports if I maxed out on disks.  Thus, I am looking for an ATX form factor.

If Ubuntu had good P45 support, then I wouldn't even be asking this question.  Perhaps I should just bide my time until 8.10 comes out and then read some reviews.

Thanks again for the consideration.

---

### Post by shaggy999 on 2008-10-27
I find it surprising that the P43/45 would not work under Hardy, as Intel has GREAT support for Linux with all their chipsets. I just did a search and it appears that P43/45 chipsets work just fine under Ubuntu as long as you set your SATA drives to AHCI in the BIOS, otherwise it won't see them. Other than that, there does not appear to be any major issues with these chipsets as far as I can tell.

Also it appears that you should stay away from low-end P43/45-based Asus boards, as they seem to be having some issues or anything with a JMicron controller in it.

---

### Post by shunthemask on 2008-10-27
Thanks shaggy999.  I think that I am going to go for the  GIGABYTE GA-EP45-UD3R ([link]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128359")) ([link]("http://www.gigabyte.com.tw/Support/Motherboard/BIOS_Model.aspx?ProductID=2921")).  For some reason newegg didn't list this board with 8 ports and the price is right!  Anyone have any experience?

---

### Post by jsc3 on 2009-01-05
I can say that I am typing this from a GA-EP45-UD3R right now, running Hardy Heron (8.04) 64-bit SMP, with an Intel Q9550 processor.  

I had to go into the BIOS "Integrated Peripherals" and set all the SATA controllers to AHCI, and set SATA Port0-3 Native Mode to Enabled - before I did that, the hard drive on Intel SATA port 0 was not visible.

Using these settings, I was able to install from a PATA DVD.

I would also note that Intrepid Ibex (8.10) was able to see the hard drive even before I set them to AHCI.  I want to run VMware Server 2.0, and that is officially supported on Ubuntu 8.04 but not 8.10.

I am using an ASUS Nvidia 9600GT card, and I did have to install the Nvidia drivers with 8.04, as there was no support for this card.  An 8800 should be fine.

---

