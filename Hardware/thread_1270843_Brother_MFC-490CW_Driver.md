---
title: "Brother MFC-490CW Driver"
date: 2009-09-20
forum: Hardware
---

### Post by ajackson on 2009-09-20
Does anyone know where I can download the driver for this printer from, I've tried the Brother site but it keeps looping back to the support welcome page (presumably does that when it can't find the page in question).

---

### Post by mathfeel on 2009-09-20
[http://solutions.brother.com/linux/en_us/download_prn.html#MFC-490CW](http://solutions.brother.com/linux/en_us/download_prn.html#MFC-490CW)

---

### Post by ajackson on 2009-09-20
> **mathfeel said:**
> [http://solutions.brother.com/linux/en_us/download_prn.html#MFC-490CW](http://solutions.brother.com/linux/en_us/download_prn.html#MFC-490CW)

Thanks but as I said I tried that site but it keeps looping back to the solutions welcome page.

---

### Post by mathfeel on 2009-09-20
There's your problem:
```
$ wget http://solutions.brother.com/Library/sol/printer/linux/dlf/mfc490cwcupswrapper-1.1.2-2.i386.deb
--2009-09-20 04:35:32--  http://solutions.brother.com/Library/sol/printer/linux/dlf/mfc490cwcupswrapper-1.1.2-2.i386.deb
Resolving solutions.brother.com... 204.2.160.233
Connecting to solutions.brother.com|204.2.160.233|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-09-20 04:35:32 ERROR 404: Not Found.
```

Why do you need the driver? I never needed to download anything for my MFC-7820N.

---

### Post by ajackson on 2009-09-20
> **mathfeel said:**
> Why do you need the driver?
Because Ubuntu didn't manage to set up my MFC-490CW for me, so I need to do it manually. It did try as a MFC-465CN but it won't print the test page (even though the printer shows it is receiving the data).

> **mathfeel said:**
> I never needed to download anything for my MFC-7820N.
Good for you, shame I don't have a MFC-7820N isn't it :)

Edit: I knew I was getting a not found (404) error - that is why I asked if anyone knew an **alternate** download site for the driver.

---

### Post by skep on 2009-09-21
Hello,

I have the same problem with a different Brother Driver. I too get the 404 error, so there seems currently no way to get the driver files one need :/

---

### Post by longreach on 2009-09-21
I am having the same problem. The "right click, save as" doesn't work either. I havn't been able to find anywhere that mentions this problem.

---

### Post by dt78 on 2009-09-21
Maybe if enough of us complain, they will fix the dang web site.

[https://secure6.brother.co.jp/LinuxContactUs/contact/Linuxform.html](https://secure6.brother.co.jp/LinuxContactUs/contact/Linuxform.html)

There was a post once that linked to the brother FTP site. I've tried very hard to find it again. I was successful downloading the drivers before from there.

If anyone knows the address of the Brother FTP site PLEASE post it.

Thanks!

---

### Post by skep on 2009-09-21
Found the .deb Files on the japanese brother support website. It's not that hard to find the correct driver there:
[http://solutions.brother.co.jp/support/os/linux/index.html](http://solutions.brother.co.jp/support/os/linux/index.html)

---

### Post by dt78 on 2009-09-21
From [EMAIL="linuxsupport@brother.com"]linuxsupport@brother.com[/EMAIL]
> "We are currently experiencing problems with our linux downloads on our
website.  I have notified our web group of the issue and expect for it
to be resolved in the near future.

Best regards,

Brother Linux Support"

---

### Post by dt78 on 2009-09-21
> **skep said:**
> Found the .deb Files on the japanese brother support website. It's not that hard to find the correct driver there:
[http://solutions.brother.co.jp/support/os/linux/index.html](http://solutions.brother.co.jp/support/os/linux/index.html)


I couldn't find the MFC-490**CW** drivers anywhere on there.

If you did find them, post specific URLs for the download.

---

### Post by ajackson on 2009-09-21
Well for printing the following worked for me
[http://solutions.brother.co.jp/support/os/linux/dlf/mfc490cncupswrapper-1.1.2-2.i386.deb](http://solutions.brother.co.jp/support/os/linux/dlf/mfc490cncupswrapper-1.1.2-2.i386.deb)
[http://solutions.brother.co.jp/support/os/linux/dlf/mfc490cnlpr-1.1.2-2.i386.deb](http://solutions.brother.co.jp/support/os/linux/dlf/mfc490cnlpr-1.1.2-2.i386.deb)

For scanning (follow the instructions on the English site) use
[http://solutions.brother.co.jp/support/os/linux/dlf/brscan3-0.2.6-1.amd64.deb](http://solutions.brother.co.jp/support/os/linux/dlf/brscan3-0.2.6-1.amd64.deb) or
[http://solutions.brother.co.jp/support/os/linux/dlf/brscan3-0.2.6-1.i386.deb](http://solutions.brother.co.jp/support/os/linux/dlf/brscan3-0.2.6-1.i386.deb)

It prints just fine, scan only works with sudo but that might be down using Karmic and udev being a bit wonky at the moment.

Haven't tried the fax side.

I'm guess the only difference between a MFC-490CW & MFC-490CN is that the CW supports wireless connection but I'm not 100% certain on that.

---

### Post by dt78 on 2009-09-21
Did you get the 490CN drivers working with the printer via wireless or USB?

---

### Post by ajackson on 2009-09-22
> **dt78 said:**
> Did you get the 490CN drivers working with the printer via wireless or USB?
Via USB.

---

### Post by dt78 on 2009-09-22
Damn. I need drivers to work with a wireless.  My Ubuntu is running on a laptop.

---

### Post by ajackson on 2009-09-22
It might work wirelessly, I haven't tried it.

---

### Post by dt78 on 2009-09-24
> Our website issues have been corrected.  You may download the
appropriate Linxu drivers from our support site located at:  [http://solutions.brother.com/linux/en_us/](http://solutions.brother.com/linux/en_us/)

Best regards,

Brother Linux Support

So it works now. Try it.

[http://solutions.brother.com/linux/en_us/download_prn.html#MFC-490CW](http://solutions.brother.com/linux/en_us/download_prn.html#MFC-490CW)

---

### Post by JBabz on 2009-09-26
How do you get the i836 .debs to run in amd64 comp?
i know there is something called ia32-libs that should help, how do i do this???

---

### Post by rchar66 on 2009-09-27
Hi Guys,

I have the MFC-490CW and I downloaded the files I needed to get it setup as a network printer and scanner. It was pretty easy to get setup and if you need the drivers, send me a private message and we can exchange e-mail address and I can send them to whoever needs them.

By the way, there was a different section for the Linux drivers. It has really good instructions and also examples of what you should see when you run the commands.

Richard

---

### Post by rchar66 on 2009-09-27
Here's the web page that I downloaded the drivers from. I just checked everything and all the links are working.

**[COLOR="Red"]CLICK HERE-->[/COLOR]** [[COLOR="Blue"]http://solutions.brother.com/linux/en_us/index.html[/COLOR]]("http://solutions.brother.com/linux/en_us/index.html") **[COLOR="Red"]<--CLICK HERE[/COLOR]**

Click on the download section for the printer driver. The MFC-490CW is the 4th one down in the center column of the MFC section.

I downloaded the .deb CUPS drivers since that's what I'm using.
Make sure you download the LPR driver and the cupswrapper driver. You need both.

Go back to the very first page and click on the download section for the Scanner Driver / Scan-Key-Tool section.

Click on the link for the for brscan3 models since that is where the driver is for the MFC-490CW.

You need to download the .deb brscan3 driver, but you'll need to decided if you need the 32 bit or 64 bit.

You may want to download the scan-key-tool if you want to use the scanner with GIMP. I chose not to set mine up that way since I'm using XSane for my scanner needs.

The install instructions are at the bottom of that section for the scanner.

Tha's pretty much it. Just follow the instructions for both and pay close attention to what they tell you to do.

If you have any questions, just let me know.

Richard

---

### Post by rchar66 on 2009-09-27
Guys, I think there is some confusion on how to download the drivers.

You need to left click on the link. It opens another page that you have to click on a 'License Agreement'.

When you click to agree, it will pop up a download box with your driver.

Hope that helps.

Richard

---

### Post by ajackson on 2009-09-28
> **rchar66 said:**
> Guys, I think there is some confusion on how to download the drivers.
No the problem was that the files weren't on the server so you were being redirected to a catch-all 404 page. Now that the files are back on the server getting and installing the files is easy as you can just follow the instructions.

---

### Post by hybrid83 on 2009-10-16
Hi...I'm still having trouble installing these drivers. I keep getting the i386 wrong architecture code. Im running a 64 bit vers of ubuntu...what am I missing?

---

### Post by charliewhizbeez on 2012-05-12
Anyone have Natty advice for this?

---

### Post by charliewhizbeez on 2012-05-12
Nevermind, use Cupswrapper packages on site.

---

