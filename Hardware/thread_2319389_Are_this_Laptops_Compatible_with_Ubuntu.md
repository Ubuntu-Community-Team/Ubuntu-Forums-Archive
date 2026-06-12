---
title: "Are this Laptops Compatible with Ubuntu?"
date: 2016-04-03
forum: Hardware
---

### Post by liron3 on 2016-04-03
I'm planning to purchase a new laptop tomorow (mostly for studies and general use) and I'm wondering if any of this are compatible with Ubuntu.

1) There is this Asus model which is published at this store as one of number of models but they specify the hardware included in it (It's mostly Hebrew website but you can see the important parts in English):

[http://ksp.co.il/?uin=28465](http://ksp.co.il/?uin=28465)

2) There is this Lenovo Model which looks alright but I read online that the screen is bit weak and tend to break, still will it support Ubuntu? :
* Intel-N:
[http://ksp.co.il/?uin=27735](http://ksp.co.il/?uin=27735)

* Intel i3:
[http://ksp.co.il/?uin=29404](http://ksp.co.il/?uin=29404)

3) Next one is a model from company called Fujitsu which I'm not familiar with so if any of you had one of their laptops I'll appreciate your input:
[http://ksp.co.il/?uin=26480](http://ksp.co.il/?uin=26480)


___________________________________

Whichever model I'll pick I plan to move the HDD into the DVD-RW spot (replace it) and install an SSD (probably 120GB should suffice) instead for the OS.

First time I'm purchasing a laptop specifically for Linux and I could really use some help to pick the correct one.

Any of those are compatible with Ubuntu? if does which one will you recommend?

Thanks

---

### Post by Frogs Hair on 2016-04-03
I'm sure there are others not on this list.

[http://www.ubuntu.com/certification/desktop/models/?category=Laptop&vendors=Lenovo](http://www.ubuntu.com/certification/desktop/models/?category=Laptop&vendors=Lenovo)

---

### Post by oldfred on 2016-04-03
Best to choose at least i3.

 Bay Trail freeze need boot parameter: intel_idle.max_cstate=1 or patches, see comments
[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)
Many Intel Bay Trail Devices Have Been Borked On Linux For The Past Year - Mar 2016
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail)

---

### Post by liron3 on 2016-04-03
I heard someone recommends in order to make sure the laptop is 100% linux compatible is to purchase a chromebook or a Laptop which comes with linux pre-installed and then install and distro I want. sounds like solid advice?

---

### Post by X-RED_Tech on 2016-04-03
Regarding pre-installed of course it's solid advice. Not so with chromebooks where you need to void the warranty to install anything other than their original Chrome OS.

---

### Post by liron3 on 2016-04-04
ok thanks.

---

### Post by mastablasta on 2016-04-05
HP Probook versions are good and support Linux (they might come SUSE preloaded). we bought one for my dad. built well, works well, replaced SUSE with Kubuntu LTS.

Regarding Fujitsu - they are very good laptops and well made. but unfortunately I am not sure their support for Linux is good. they are oriented a lot towards windows. we use Fujitsu (desktops and laptops) at work and one of our subsidiaries is selling them (representative). many of my colleagues bought them for home use and are pleased with them. the only complaint is price. they are a bit more expencive here.

if you need it primarily for writing and web surfing then Pentium N is good enough. these are similar in power to some old i3 models I think. but if you have the money definitely go with i3.

Next laptop I am getting I will check:
screen
how well and sturdy it's built
battery life
GPU

---

### Post by liron3 on 2016-04-05
update,
in the end I've found some workaround.

I've bought the Asus X555L for family member of mine and took his old Laptop.

The Laptop I've taken and used for Ubuntu install is Lenovo Ideapad z560 (4GB RAM, i5, Intel pack).

Ubuntu works smoothly out of the box everything 100% working.

only change I've made to the laptop is installing 120GB SSD drive (Sandisk) for the OS and boot partitions and I've installed the HDD instead of the optical drive using a caddy. 

Thanks for the help.

---

### Post by Bucky Ball on 2016-04-05
Sounds like a nice laptop, especially with the mods.

Thanks for marking as solved and have fun. ;)

---

