---
title: "How to install canon pixma ip 1600 ??"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by blunile on 2006-10-29
Hello . i have dapper and i cant install my printer ( canon pixma ip 1600)

Ubuntu detect it fine but its driver is not present in its driver database.
the only driver present of pixma line is of ( pixma ip 4000)

Can anybody help me ???

---

### Post by galileon on 2006-10-29
[http://www.turboprint.info/](http://www.turboprint.info/)

its a demo and prints in low-res without banner, and hires but adds a banner on it...

(you can "improve" it by modifying some of the files in it, so that the low-res option prints hires ;)

---

### Post by blunile on 2006-11-01
I tried the turboprint but it doesnt get to work ,  when i try to install it it pop up this:

ERROR
xtpsetup must be run in root mode

I'm a newbie and i dont know what that means ??!!:-?

---

### Post by galileon on 2006-11-02
hmmm...xtpsetup...means you have already installed turboprint? anyway i'll give you the complete instruction here:

download the latest [http://www.turboprint.info/turboprint-1.94-4.tgz](http://www.turboprint.info/turboprint-1.94-4.tgz)

save it in your home directory.

open a terminal, antd type:

tar -xvzf turboprint-1.94-4.tgz
cd turboprint-1.94-4/
sudo ./setup

follow the instructions, and it wil suggest to run xtpsetup (it will run with root priviledge, and you shouldn't get the error you got above...) if you do get the same error, issue this from the terminal:

sudo xtpsetup

this will bring a graphical interface where you can Add a printer (its quite intuitive from here)...

hope this works...

---

### Post by blunile on 2006-11-02
work like a charm ,


Thank u very much galileon and God bless you :-D

---

### Post by galileon on 2006-11-02
cheers, but be aware turboprint drivers only do 300dpi for free, and 600dpi includes a banner...however, the 300dpi on my canon pixma mp150 looks like 150dpi from the same printer in windoze...

---

