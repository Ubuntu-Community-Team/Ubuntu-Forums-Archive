---
title: "pairing the bluetooth mouse"
date: 2009-04-28
forum: Hardware
---

### Post by wolfyy on 2009-04-28
well I have my bluetooth mouse which I cant find with command "hcitool scan".

i find it under BT manager, but I still cant connect to it :(


I just installed fresh ubuntu 9.04 and I cant believe. I had same problem in 8.04, but in 1 hour of trying it finally find my mice. but now I am trying for 4 hours and no succeed. :(

this is my mouse [http://www.trust.com/products/product.aspx?artnr=15351]("http://www.trust.com/products/product.aspx?artnr=15351")

tnx for help

---

### Post by wolfyy on 2009-04-28
you guys definitely rulz :lolflag::guitar:

I just post this post and my mouse come alive.

now there is another problem :confused::confused:

I am going by this guide [http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html]("http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html") 

but this command does not exist "sudo hidd --search"

so how can I pair the device in ubuntu 9.04:confused:

edit: problem solved. after I find mac address of mice and setup it into "sudo gedit /etc/bluetooth/hcid.conf"...I just have to go in BT manager and click connect lol :)

---

