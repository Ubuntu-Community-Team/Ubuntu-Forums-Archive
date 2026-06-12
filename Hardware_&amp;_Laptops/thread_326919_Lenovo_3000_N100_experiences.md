---
title: "Lenovo 3000 N100 experiences?"
date: 2006-12-28
forum: Hardware &amp; Laptops
---

### Post by Jbloudg20 on 2006-12-28
I just ordered the machine, and I was wondering what your experiences with this machine and Edgy are. Can you get Beryl running? How about that fingerprint reader?

I have been debating on whether to use Ubuntu or Fedora. Any experiences on which will run better?

P.S. I wont have my machine until mid January so I'm researching in the meantime. Thanks for your help.

---

### Post by tinytony on 2006-12-29
you cant use beryl dont know about fingerprint id as havent bothered trying yet.am using now with edgy mighty have problems with wifi took a little time to setup

---

### Post by cwest on 2006-12-29
I'm running aixgl+beryl on a Lenovo 3000 N100, in fact this very laptop. Stop spreading lies ;)

The builtin webcam in some of the models will be supported soon (the driver is currently under development, I would guess ~Q1 2007). Fingerprint reader is supported to basicly work (driver+bindings+simple instructions exist). Some small problems with the multicard-reader as of the current Ubuntu (you have to boot with a card inserted for it to work - reported fixed elsewhere so will probably work in next release at least ;)), clone mode to the vga connector works if booting with external monitor connected. Builtin speakers aren't disabled when external output is used - haven't investigated this any further but I guess it should be easy to fix.

As far as I am concerned, the hardware is currently 95% supported, and only the builtin modem would exclude it from 100% support.

Wlan, NIC, Graphics, Sound, Bluetooth - everything works out of the box. It has NEVER booted Windows ;-)

---

### Post by tinytony on 2006-12-29
i stand corrected and will give myself 40 lashes

---

### Post by Jbloudg20 on 2006-12-29
I knew it would run Beryl, but what driver do I need to use?

I know you need to sue the i810 driver, but does that support 3d acceleration right away? What else needs to be done?

Thanks for the info. I did some more digging and I feel pretty confident about it, you just made me feel a bit better.

BTW: Tracking shows I *should* recieve my computer today! :)

---

### Post by cwest on 2006-12-29
Standard i810 drivers, yup. DRI right away, although you need '855resolution' to get 1280x800 :)

---

### Post by Jbloudg20 on 2006-12-29
Fantastic, thanks.

I'm looking forward to my first beryl experience :)

---

### Post by uhajo on 2007-01-15
> **cwest said:**
> I'm running aixgl+beryl on a Lenovo 3000 N100, in fact this very laptop. Stop spreading lies ;)

The builtin webcam in some of the models will be supported soon (the driver is currently under development, I would guess ~Q1 2007).

Hi cwest,

any more info on this? Where did you hear about this? I googled and just couldn't find anything. I hope the developers come up with a driver for Lenovos external webcam as well.

Happy to hear more details,
uhajo

---

### Post by medz on 2007-01-17
yes i also have this laptop

but my version is with the geforce 7300-64mb

model type:0768-6XG

is this laptop fully supported,,,i really want to put ubuntu on it..but im holding back really until fiesty is released or i hear or read somewhere.. that all hardware is supported

the concerns i have are the
card reader
intergrated camera
finger print reader

---

### Post by LunatikOwl on 2007-05-15
Beware! i tried Feisty on my n100 0768flg model and about to give up on trying to make my sound work.

after trying just about everthing i found on the net i'm starting to doubt whether i'll ever get sound on this box.....

---

### Post by zanjabeel5 on 2007-05-15
@Lunatic
look here
[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG)

---

