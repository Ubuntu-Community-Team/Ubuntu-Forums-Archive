---
title: "Running Ubuntu from a USB Pen"
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by the lemming on 2009-05-21
Hello

I'd like to experiment installing and running Ubuntu from a spare 1GB USB Pen.

No idea how to go about it but am willing to give it a try.

Any help or advice would be very much appreciated.

Cheers

---

### Post by wpshooter on 2009-05-21
> **the lemming said:**
> Hello

I'd like to experiment installing and running Ubuntu from a spare 1GB USB Pen.

No idea how to go about it but am willing to give it a try.

Any help or advice would be very much appreciated.

Cheers

I tried doing this same thing from/on a 2gb USB thumb drive.  I can tell you that unless you do some type of bare mimimum installation, a 1gb or even 2gb of space is not enough.

I tried doing it by installing from the the ALTERNATE CD version of Ubuntu to a 2gb USB thumb drive.  Installation went fine but when I got to the point of trying to download and install the available updates over and above what was installed from the Ubuntu CD, I ran out of USB thumb drive space.

I believe that you might be able to get this to work with a 4gb USB thumb drive but an 8gb drive would probably be a good bit better.

I have not had the opportunity to try this on a thumb drive over 2gb in size.  

If you can try it on a larger USB thumb drive and get it to work properly, please let us know.

Thanks.

---

### Post by the lemming on 2009-05-21
I take it that I will have to use a smaller distro like Puppy or DSL then?

---

### Post by snowpine on 2009-05-21
Ubuntu will run fine on a 1gb pen drive (though there won't be much room left for your files). You don't install it as you would install to a hard drive (this takes up more space and is bad for the flash memory); rather, use the "Create a USB Startup Device" utility in the Ubuntu system menu (8.10 or newer). 

There is also a utility called Unetbootin that accomplishes the same thing, except that it is not "persistent" meaning your changes are lost when you shut down (just like a Live CD). Unetbootin works in Windows or just about any Linux distro: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by wpshooter on 2009-05-21
> **snowpine said:**
> Ubuntu will run fine on a 1gb pen drive (though there won't be much room left for your files). You don't install it as you would install to a hard drive (this takes up more space and is bad for the flash memory); rather, use the "Create a USB Startup Device" utility in the Ubuntu system menu (8.10 or newer). 

There is also a utility called Unetbootin that accomplishes the same thing, except that it is not "persistent" meaning your changes are lost when you shut down (just like a Live CD). Unetbootin works in Windows or just about any Linux distro: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I don't think either of these 2 methods accomplishes the same thing as actually installing Ubuntu to the USB device as if it were just another "hard drive".  Affects on the USB drive, probably depends on exactly what programs, etc. you wind up running on/from it.  If I were running Ubuntu from a USB thumb drive, I would not be overly concerned about the affects on the USB, because this would probably be just done for demo purposes, mostly - not a critical installation of Ubuntu.

---

### Post by snowpine on 2009-05-21
> **wpshooter said:**
> I don't think either of these 2 methods accomplishes the same thing as actually installing Ubuntu to the USB device as if it were just another "hard drive".  Affects on the USB drive, probably depends on exactly what programs, etc. you wind up running on/from it.  If I were running Ubuntu from a USB thumb drive, I would not be overly concerned about the affects on the USB, because this would probably be just done for demo purposes, mostly - not a critical installation of Ubuntu.

That is a good point, but does not help the OP squeeze Ubuntu onto his/her 1gb pen drive. :)

---

### Post by wpshooter on 2009-05-21
> **snowpine said:**
> That is a good point, but does not help the OP squeeze Ubuntu onto his/her 1gb pen drive. :)

I had already said that 1gb was not sufficient, to consider 4 or 8.

---

### Post by snowpine on 2009-05-21
> **wpshooter said:**
> I had already said that 1gb was not sufficient, to consider 4 or 8.

Both methods I described in post #4 will work with a 1gb drive.

---

