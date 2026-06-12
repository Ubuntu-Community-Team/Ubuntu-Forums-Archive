---
title: "printer driver and  windows application issue"
date: 2007-03-17
forum: Hardware &amp; Laptops
---

### Post by robertrej on 2007-03-17
I installed ubuntu 6.10  than  Wine  , and Turbocash - Windows app. But
when I install the printer driver for my hp 1020 laserjet Turbocash stops
running or a least will not start. Without the printer driver installed it works
fine but of course will not print.   
                                                         ----------Any ideas ?----------------
                                                          Thanks  / Bob
                                                            [email]bjohnson1394@yahoo.ca[/email]

installation instructions:

sudo apt-get install build-essential
$ wget -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)
$ tar -zxvf foo2zjs.tar.gz
$ cd foo2zjs
$ sudo make uninstall
$ make
$ ./getweb 1020
$ sudo make install install-hotplug

---

### Post by robertrej on 2007-03-24
It seems all I had to do was set the printer I added in : system/administration/printer
to   'default'    printer very simple .Both Turbocash  and Altrex accounting software
work just fine now and I can even printer using both apps. I would like to point
out that I did update Wine to the most recent version  0.9.33  so that may have
helped  the issue as well. I am unable to save reports as a PDF file format
although I can save reports as  a RTF and use Openoffice writer to print high quality
reports so that saves the day . When I print using Turbocash the quality is ok but
not perfect.

Turbcash is free   Atrex is a $299 program.

Some times the solution is very simple in life!
                                                                                    Good day:) 
                                                                                    Bob

---

