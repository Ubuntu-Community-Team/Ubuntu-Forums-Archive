---
title: "laptop mode?"
date: 2008-05-04
forum: Hardware
---

### Post by SpinningAround on 2008-05-04
I have read that laptop mode isn't enabled by default, if I have understand it correct will the battery last longer if you enabled it but what is the drawbacks?

I also tried to find some guides in how to use it and similar but have been unable to find and good so far. Also I have read that the best way to fix the Load_Cycle_Count is to use laptop mode but I never seen anything in how you do this.

Thanks in advanced

---

### Post by chunchengch on 2008-05-04
1. run this command

[COLOR="Red"]$ sudo gedit /etc/default/acpi-support
[/COLOR]
2. find the following statement and replace [COLOR="SeaGreen"]**false**[/COLOR] with [COLOR="SeaGreen"]**true**[/COLOR], than save and exit

[COLOR="SeaGreen"]ENABLE_LAPTOP_MODE=false[/COLOR]

3. run this command to activate laptop mode

[COLOR="Red"]$ sudo /etc/init.d/laptop-mode start [/COLOR]


PS: laptop mode causes odd hangs on some machines

---

### Post by chunchengch on 2008-05-04
"...[COLOR="Blue"]the spin down time of the hard disk was limited to 10 minutes. Spinning up/down a normal desktop hard disk every 10 minutes wears it down within 6-8 months.[/COLOR] "

[http://gentoo-wiki.com/HOWTO_HDD_spindown_small_server](http://gentoo-wiki.com/HOWTO_HDD_spindown_small_server)

---

### Post by TheMemphisExperience on 2008-05-04
> **chunchengch said:**
> "...[COLOR="Blue"]the spin down time of the hard disk was limited to 10 minutes. Spinning up/down a normal desktop hard disk every 10 minutes wears it down within 6-8 months.[/COLOR] "

[http://gentoo-wiki.com/HOWTO_HDD_spindown_small_server](http://gentoo-wiki.com/HOWTO_HDD_spindown_small_server)

That's a ... bad downside. If I had more money(and hard disks), maybe I'd use laptop mode. Still...I'd like to use Ubuntu during classes in lieu of Vista. Though I will have to live.

As an aside, how do you think Vista conserves power more efficiently than Ubuntu? At least in my case, Vista can last up to three hours. Linux is limited to about one and a half to two hours. Maybe I just need to play with settings more.

---

### Post by sdennie on 2008-05-05
In the laptop mode config file, you can choose for it to not control the HD spindown time, if that is something you are worried about.  The config file is actually very well documented and can be found at: /etc/laptop-mode/laptop-mode.conf.  The specific option you are looking for is "CONTROL_HD_TIMEOUT".  Setting that variable to 0 should prevent laptop-mode from setting the spindown time of your disk.

Also, linux can do some pretty amazing power management (far beyond what laptop-mode offers by default) but, it's just harder to setup.  Some good places to start are the powertop tool and [www.lesswatts.org](www.lesswatts.org).  To install powertop and run powertop you can do the following from a terminal:

```

sudo apt-get install powertop
sudo powertop

```

---

