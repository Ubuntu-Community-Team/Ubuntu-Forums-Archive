---
title: "Liteon CD/DVD drive with Lightscribe technology"
date: 2008-02-17
forum: Hardware &amp; Laptops
---

### Post by denham2010 on 2008-02-17
Hi,

A good news story for those in the market for a new CD/DVD drive.

I recently just built a brand new computer, and without even thinking about it, I bought a Liteon LH-20A CD/DVD drive - this particular model has Lightscribe technology - uses special Lightscribe discs so you can flip it over and burn a label to the disc.

Now being the cynic I am, I didn't really bother too much with the labelling side of the drive, as always, the supplied software only works with those M$ operating systems.

Tonight, I finally got around to checking out the possibilities of software for Linux that may be able to use the labelling technology of these drives, and to my surprise, Lightscribe already supports Linux, with software available on the Lacie website.

[http://www.lacie.com/au/products/product.htm?pid=10803]("http://www.lacie.com/au/products/product.htm?pid=10803")

On this page you will find links at the bottom to download the software. The software will work on any x86 Linux distribution with a 2.6 Kernel.

```
LightScribe Host Software v1.4.113.1 for Linux
LaCie LightScribe Labeler for Linux 
```

They are RPM packages, and you do need to download both. Also, clicking the documentation tab on the page will give you a link to download the manual in PDF form. This is not absolutely necessary though, as the manual is included in the package.

Once you have downloaded the files, open up a terminal and change to the directory the files are in.

Now we need to convert the RPM packages to DEBs so we can install them in our chosen flavour of *buntu or any other Debian based distro. To do this, you will need the package ALIEN.

```
sudo apt-get install alien
```

Once alien is installed, we can convert the downloaded programs.

```
sudo alien -d -c lightscribe-1.8.15.1-linux-2.6-intel.rpm
```

and

```
sudo alien -d -c 4L-1.0-r6.i586.rpm
```

You will now have 2 DEB packages you can install on your system either using GDEBI (in Thunar / Nautilus just right click the DEB and select the option "Open with Gdebi package manager") or just install from the command line.

```
sudo dpkg -i lightscribe_1.8.15.1-1_i386.deb
```

and (I rarely install using dpkg from the command line - please let me know if my code is wrong here! Thanks.)

```
sudo dpkg -i 4l_1.0-1_i386.deb
```

Install the lightscribe package first, as this contains the drivers for label burning that the 4L package needs.

To run, use:

```
4L-gui
```

or create a menu entry for it.

There is also a command line option which will check your drives and media to see if they are compatible.

```
4L-cli
```

The manual is very good to follow through after installation to ensure firstly your Lightscribe enabled drive is properly recognised, and that the software and drive can correctly detect your media.

NOTE: You must use Lightscribe CDs and DVDs to use the labelling functions.

Happy Labelling, and I must say, it's great seeing another hardware vendor supporting Linux!

---

### Post by adityakavoor on 2008-02-17
Thank You for this.

What is the differencs between a Lightscribe CD and a normal CD ??

---

### Post by denham2010 on 2008-02-18
No problem.

A Lightscribe CD is just a brand of CD like Sony and TDK etc.

The Lightscribe ones have a special laser sensitive coating on the label side which is what creates the label with the L4 labelling software.

---

### Post by GoCool on 2008-03-01
> **denham2010 said:**
> Hi,
...
...
The manual is very good to follow through after installation to ensure firstly your Lightscribe enabled drive is properly recognised, and that the software and drive can correctly detect your media.
...
...


I tried to install it, but my 4L is not recognizing my media. Do you have any idea on why? Or atleast where I can get this manual which you were mentioning. Please any help on this would be highly appreciated.

I got a new VISTA machine and after trying all the features, I just formated it and went UBUNTU. So far so good, except for my lightscribe. I did the install but its not showing my drive.

---

