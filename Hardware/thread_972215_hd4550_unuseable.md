---
title: "hd4550 unuseable?"
date: 2008-11-05
forum: Hardware
---

### Post by veganbikepunk on 2008-11-05
I just ordered an ATI Radeon HD4550, and it hasn't come yet (should come later today), but I've been googling around and now I'm worried it won't work in Ubuntu.

---

### Post by JohnSearle on 2009-01-07
Did you manage to get the drivers working for the 4550? I just purchased one, and now I'm kind of regretting it.

If anyone knows of a good drivers solution, then I'm all ears :)

- John

---

### Post by Kubunteando on 2009-01-16
I have the HD 4550 working in Intrepid 8.10.
It works fine with the ATI proprietary drivers 8.12 released on December 2008.

Go to [http://ati.amd,com](http://ati.amd,com) and in the support are download the Linux driver installer. And run it with the proper parameters to create the .deb packages for your version.

It works quite well, although if you use compositing (compiz or KDE4) still there are the video flickering issues. But with no compositing it works quite well.

---

### Post by marcgh on 2009-01-16
> **Kubunteando said:**
> I have the HD 4550 working in Intrepid 8.10.
It works fine with the ATI proprietary drivers 8.12 released on December 2008.

Go to [http://ati.amd,com](http://ati.amd,com) and in the support are download the Linux driver installer. And run it with the proper parameters to create the .deb packages for your version.

It works quite well, although if you use compositing (compiz or KDE4) still there are the video flickering issues. But with no compositing it works quite well.



I fully agree with that, I was using same HD4550 and now i am using the Radeon 4850. Works well with the drivers from the ATI site, there is even a PDF file available: How to install / configure.
Only problem is : it is or Compiz or video. Both together results in flickering.

---

### Post by sc0tt10 on 2009-01-16
it should be usable, but a word of warning: Don't try a graphics card from Ati or nVidia with 8***/9*** or HD3***/HD4*** in Hardy Heron 8.04, they just run awful.

---

### Post by Yashiro on 2009-01-16
The above post is incorrect.

---

### Post by nick09 on 2009-01-16
Thats because Hardy was released with(or without) drivers that were needed. With Ibex you would have the drivers but newer graphic card models might not be supported.

---

### Post by markbuntu on 2009-01-16
If you have a newer card from nvidia or ati you need the proprietary drivers no matter what version of linux/Ubuntu you are using. If you use these drivers you will get great performance and it will only get better since both companies are now racing to get thier linux drivers comparable to thier windows drivers.

---

### Post by Kubunteando on 2009-01-24
I had it working in Intrepid 8.10.
But now it is not working any more.

I don't know if it is because of some of the updates, but I am not able to make it work again. The fglrx module does not load and complains that cannot allocate memory...

---

### Post by hawkies16 on 2009-02-12
> **JohnSearle said:**
> Did you manage to get the drivers working for the 4550? I just purchased one, and now I'm kind of regretting it.

If anyone knows of a good drivers solution, then I'm all ears :)

- John

 Did you find any drivers for the HD 4550 yet? I installed eAR OS just as a media center and have a 4550 installed and can't get the HDMI working right!! It's doing my head in! feel like just installing Vista just for the media center as all the drivers will work!!!

If you know a way of solving this problem I would much appreciate it mate!!

hawkies16

---

### Post by RGPerson on 2009-02-13
Please someone tell us if we should take our 4550 back.  We have a few weeks to do so.  Then tell us what we should get.

Ubuntu plays fine through our monitor, but we want it through our HD TV.  We have a DVI to HDMI adaptor.  But we get a black screen.

In lspci it only shows 

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc. Unknown device [1002:9540]

Can anyone help with the card we have or do we take it back?

Gabrielle

---

### Post by Yashiro on 2009-02-13
If you want HDMI video & audio working with no hassles install Windows.

You can get it to work on Ubuntu but it's probably beyond the effort you're willing to put into it.

---

### Post by RGPerson on 2009-02-13
> **Yashiro said:**
> If you want HDMI video & audio working with no hassles install Windows.

You can get it to work on Ubuntu but it's probably beyond the effort you're willing to put into it.

We have Windows computers. We want Linux for this.

Gabrielle

---

### Post by Yashiro on 2009-02-13
With which drivers are you attempting this?

---

### Post by RGPerson on 2009-02-13
> **Yashiro said:**
> With which drivers are you attempting this?

That's part of the question. I don't think we have any drivers at the moment.  I think it's just using a generic vga driver.

I don't know where to find a Linux driver for the 4550.  Ati's site has drivers for linux but they don't list the 4000 series.  They list 4800 and 3xxx but not 4000 or 4500 or 4550.  So I don't know if any of those would be safe for this 4550.

What if we returned it and got an NVidia.  Which one would be recommended? 

Gabrielle

---

### Post by Yashiro on 2009-02-13
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_91_linux.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_91_linux.pdf)
[http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)

Latest driver supports your card.

---

### Post by eanbowman on 2009-02-23
It's still pretty unusable for me.

I get great, fast display except that overlays flicker all the time.

As well, with my 8600 Geforce I was at least able to play Left 4 Dead. With this card I can't even get the main game menu to display options. It just shows the background video (flickering badly) and no menu.

This card has been an epic fail on all fronts so far. :C

8.10 using the most recent (just downloaded them now from ATI) catalyst proprietary driver. It gives the exact same results as the one in the repository.

Any ideas?

---

### Post by RGPerson on 2009-03-01
> **hawkies16 said:**
> Did you find any drivers for the HD 4550 yet? I installed eAR OS just as a media center and have a 4550 installed and can't get the HDMI working right!! It's doing my head in! feel like just installing Vista just for the media center as all the drivers will work!!!

If you know a way of solving this problem I would much appreciate it mate!!

hawkies16

We got ours working with the drivers from ATI web site. We used the 9-1-x86.x86_64.  I think that's how it's called.  We're up and running with our HDTV as our monitor.  Got some other kinks to work out with networking and audio cd's but video is working fine.

Gabrielle

---

