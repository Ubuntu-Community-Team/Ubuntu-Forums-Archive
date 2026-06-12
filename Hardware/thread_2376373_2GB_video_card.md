---
title: "2GB video card"
date: 2017-11-02
forum: Hardware
---

### Post by AbdRahim on 2017-11-02
Anyone successfully using a 2GB video card in 16.04? If so which one?

---

### Post by SeijiSensei on 2017-11-02
I have a [card]("https://www.newegg.com/Product/Product.aspx?Item=N82E16814127870") with an NVIDIA GTX 750 and 2GB of memory.  Works as advertised with the proprietary driver.  I think most any NVIDIA card with 2 GB of memory should work fine.

---

### Post by Autodave on 2017-11-02
Just about any Nvivia card made in the last 5 years will work great.

---

### Post by AbdRahim on 2017-11-02
I ask because it seems that some have had difficulty with the newer cards. [https://askubuntu.com/questions/760934/graphics-issues-after-while-installing-ubuntu-16-04-16-10-with-nvidia-graphics](https://askubuntu.com/questions/760934/graphics-issues-after-while-installing-ubuntu-16-04-16-10-with-nvidia-graphics). I am thinking of upgrading from a Nvidia geoforce 510 with 512mb ram. I don't play games and am not sure if this will make a difference or not. i7Cpu, 24 HB ran
m on the board. I am wondering if the newer card would speed up Paige loading on intervened or improve watching videos offline. Any ideas?

---

### Post by Bashing-om on 2017-11-02
AbdRahim; Hello;

I upgraded to a nvidia GTX 710 card with 2 Gigs of ram ., The performance increase over the old graphic's card is phenomenal.
I do use our trusted PPA:
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
for the driver (module) .
Be aware there is no support for new generation cards with nouveua ( open source) in 14.04 .

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by SeijiSensei on 2017-11-03
> **AbdRahim said:**
> I ask because it seems that some have had difficulty with the newer cards. [https://askubuntu.com/questions/760934/graphics-issues-after-while-installing-ubuntu-16-04-16-10-with-nvidia-graphics](https://askubuntu.com/questions/760934/graphics-issues-after-while-installing-ubuntu-16-04-16-10-with-nvidia-graphics). I am thinking of upgrading from a Nvidia geoforce 510 with 512mb ram. I don't play games and am not sure if this will make a difference or not. i7Cpu, 24 HB ran
m on the board. I am wondering if the newer card would speed up Paige loading on intervened or improve watching videos offline. Any ideas?

If you can watch a 1080p video using VDPAU with your current card, I'd say don't bother.  Here's a good test:

[https://www.youtube.com/watch?v=XSGBVzeBUbk](https://www.youtube.com/watch?v=XSGBVzeBUbk)

Some other tests that offer downloadable files are here: [http://www.h264info.com/clips.html](http://www.h264info.com/clips.html)

Try downloading and watching one of these with SMPlayer + mpv using the vdpau driver found under Options > Preferences > General > Video.

---

### Post by because7892 on 2017-11-04
i have nvidia gtx 750 ti with 2GB vram works well with propriety drivers never had a problem, pretty much all nvidia cards form the last 7 years should work fine without any problems. my friend has a nvidia gtx 480 and he says it works fine with no problems.

---

