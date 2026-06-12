---
title: "Brother MFC-J4710DW in Ubuntu 12.04"
date: 2014-01-11
forum: Hardware
---

### Post by Steve_and_Becky on 2014-01-11
I have tried to download the cups drivers and tried the command lines and all I am doing is going in circles.  I really want to get this printer installed.  Help!

Becky

---

### Post by tomearp on 2014-01-11
I have found [this guide]("http://www.howtogeek.com/169679/how-to-add-a-printer-to-your-raspberry-pi-or-other-linux-computer/") useful for setting up CUPS in Ubuntu.

---

### Post by Steve_and_Becky on 2014-01-11
> **tomearp said:**
> I have found [this guide]("http://www.howtogeek.com/169679/how-to-add-a-printer-to-your-raspberry-pi-or-other-linux-computer/") useful for setting up CUPS in Ubuntu.

It doesn't work for me.  I was so frustrated earlier that I left some information out.  I am trying to install a brother printer, model number MFC-J4710DW.  I went to brother's website, and downloaded what was supposed to be the cups wrapper for it.  The Ubuntu Software Center tried to open it automatically.  The software center popped up a dependency error with it.  I can't even figure out what kind of dependencies it needs.  I have installed ia32-libs and lib32stdc++ like brother's website said I needed to do.  I just don't know what other dependencies I need to install so that this can get done.  If I haven't figured this out before Monday, I will take this thing to our favorite computer recycle shop and ask them to install my printer for me.  GRRR!

---

### Post by tomearp on 2014-01-12
I found a [set of instructions]("http://tinyurl.com/qajazo9") on the brother site that accompany the Linux cupswrapper driver, which refers to an additional LPR driver as well as some "pre-required procedures" that need to be carried out. Have you tried these instructions?

Sorry I can't be of more help, I don't have any experience with this particular model of Brother.

---

### Post by Steve_and_Becky on 2014-01-12
Yes, I did try.  The only dependencies that I could see it needed were the ia32-libs and lib32stdc++ and I already installed those.  I know nothing about command lines and command lines absolutely confuse me.  I wonder if I will need to take it to our favorite linux friendly computer shop and see if they can install it for me.

---

### Post by tomearp on 2014-01-13
Yeah I think it's probably worth taking it to them. I have generally found CUPS to just work, so hopefully it will be something simple!

---

### Post by Steve_and_Becky on 2014-01-14
> **tomearp said:**
> Yeah I think it's probably worth taking it to them. I have generally found CUPS to just work, so hopefully it will be something simple!

Dh and I took it in to our favorite computer shop yesterday.  They were able to do in three hours what I was not able to do in a whole weekend.  The problem was that there are so many different methods to install this printer that I had not stumbled upon the method that this printer needed to be installed.  I am so thankful for our computer shop and thankful that they love Ubuntu as much as I do.  They only charged us $20!

Becky

---

