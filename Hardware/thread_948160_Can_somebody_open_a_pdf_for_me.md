---
title: "Can somebody open a pdf for me?"
date: 2008-10-14
forum: Hardware
---

### Post by shaggy999 on 2008-10-14
So I just got a brand new motherboard in (brand new to me anyway, got it used off of ebay) but I have no idea which pins the power and reset switch and stuff connect to. The motherboard I have is an MSI MS-6333 which apparantly only a few big box builders used. I can't find a manual for it but I did find the manual for the MS-6334 which looks almost exactly like my board and has almost all the same features (minus onboard video). So I went to download the manual and low and behold the PDF is stored inside a windows executable!!! This sucks for me because I have no Windows machine and my system doesn't even have graphics anyway (typing this in elinks). So I'm stuck for the moment unless someone that has Windows would be willing to go to MSI's website and download the MS-6334 manual (which for some reason is listed as an "815M Pro" under their archive section and is willing to type out the diagram for me so I can get this system up and running. Would anyone be willing to do this?

---

### Post by pytheas22 on 2008-10-15
Yes, it is sad that everyone these days feels a compulsion to pack stuff into .exe files even when it makes no sense to do so.

Fortunately, however, if [this]("http://www.motherboards.org/mobot/manuals/MSI/MS-6334%2B815M%2BPro/") is the manual you're referring to, I was able to crack it open by using 'unzip' on the .exe file (no luck with cabextract).  It contains six pdf files.  I packed them back into a tarball that I'll attach here.

I'm assuming you have some way to open the pdfs in your environment (why don't you run X in any way, are you crazy?), but if you really need the diagram typed out, let me know and I'll do it (but probably not till tomorrow).

---

### Post by shaggy999 on 2008-10-15
I use fbgs which can render pdf files to the framebuffer. :)

Yes, that was the manual I was looking for. Unfortunately, it looks like it has a completely different pin configuration (mine has 10 pins while the 6334 as 15).

Man, this sucks.

---

### Post by shaggy999 on 2008-10-15
Oh, and this system is a PII 333 MHz w/ 160 MB RAM. Running X is too slow.

Now I've got a PIII 1.33 Ghz w/ 896 MB RAM sitting here but can't get the motherbord to power up. :(

---

