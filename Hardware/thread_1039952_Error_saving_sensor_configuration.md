---
title: "Error saving sensor configuration"
date: 2009-01-15
forum: Hardware
---

### Post by zika on 2009-01-15
today I've installed lm-sensors and sensors-applet and enabled Hardware_monitor_(lm-sensors) in my System->Admin->Services. I've added Hardware_sensors_monitor (sensors-applet 2.2.1) to my panel. If I want to change preferences I get the following error:"Error saving sensor configuration". what should I do to correct that?

---

### Post by phorque on 2009-11-30
I've got the same problem with a fresh install of Ubuntu 9.10 on a Macbook Pro 5,4... Been wanting to keep an eye on the core temps because there's supposed to be issues with the sensors in Karmic.

---

### Post by Robbyx on 2009-12-01
Same problem

---

### Post by sr40150 on 2010-01-15
Hi,

I found it and it work for me :

you have to delete the non-printable characters in the preferences

sensors-applet -> tab Sensors -> field Label

of the hard disk labels; otherwise the settings won't be saved when I log out and then log in again. 

But as I mentioned in my first comment, it is rather a hddtemp bug: hddtemp should not show non-printable characters. This bug can be closed in my opinion.

source: [http://bugs.archlinux.org/task/9379](http://bugs.archlinux.org/task/9379) 

Bye

---

### Post by phorque on 2010-01-15
> **sr40150 said:**
> Hi,

I found it and it work for me :

you have to delete the non-printable characters in the preferences

sensors-applet -> tab Sensors -> field Label

of the hard disk labels; otherwise the settings won't be saved when I log out and then log in again. 

But as I mentioned in my first comment, it is rather a hddtemp bug: hddtemp should not show non-printable characters. This bug can be closed in my opinion.

source: [http://bugs.archlinux.org/task/9379](http://bugs.archlinux.org/task/9379) 

Bye

Ah you legend. I also had screwy characters (in my HD labels).

Thank you!!

---

### Post by Robbyx on 2010-01-15
Thanks for the explanation. I think the error messages have now gone.

---

### Post by zika on 2010-01-15
It is exactly a year after I had posted original question... Not that I'm complaining, just a coincidence. I do not have sensors installed in Lucid right now, so, I can not test the solution. But, nevertheless, thank You.

---

### Post by hawkril on 2010-04-29
I tested the solution in Lucid this morning and it works. So thank you and have a nice release day ;)

hawkril

---

