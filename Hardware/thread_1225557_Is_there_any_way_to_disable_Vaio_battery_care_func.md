---
title: "Is there any way to disable Vaio battery care function in Ubuntu?"
date: 2009-07-28
forum: Hardware
---

### Post by baz.g on 2009-07-28
I have recently installed Ubuntu 9.04 on my Vaio laptop, i remembered to back everything up before i formatted the hard drive but i forgot to disable the battery care function. now my battery still only charges to 50% even in ubuntu, is there any easy way to disable this? is it possible if i install virtualbox in ubuntu and use my vaio's vista license key to install vista into the vb and download vaio control centre into it?

many thanks :)

---

### Post by regrug on 2009-11-11
I am missing the battery care function too, not to disable but to use it!
I searched a lot, but did not find a thing for vaios, whereas the kernel module "tp_smapi" does it since years for thinkpads.
Cant the charger be accessed thru "Sony Notebook Control"?

There has to be someone working on it somewhere :confused:

It could improve battery lifespan for so many users. Maybe the problem is, that most of the vaio owners dont use this function or even dont know it exists.

I kept vista on my hd for that only reason, but got tired of starting an OS just to toggle one switch and then deleted it too. Luckily i switched to 100% before ;)

So, did anyone try virtualbox, did it work?

---

### Post by SAntonio on 2010-03-19
> **regrug said:**
> I am missing the battery care function too, not to disable but to use it!
I searched a lot, but did not find a thing for vaios, whereas the kernel module "tp_smapi" does it since years for thinkpads.
Cant the charger be accessed thru "Sony Notebook Control"?

There has to be someone working on it somewhere :confused:

It could improve battery lifecycle for so many users. Maybe the problem is, that most of the vaio owners dont use this function or even dont know it exists.

I kept vista on my hd for that only reason, but got tired of starting an os just to toggle one switch and then deleted it too. Luckily i switched to 100% before ;)

So, did anyone try virtualbox, did it work?
I've also been experiencing similar problems with my Sony Vaio netbook. Is there any way I can disable the 50% charging option. Please help me... I'm loosing y head over this...

---

### Post by sam.reader on 2010-03-19
I have never heard of the function battery care in my dell laptop.
What exactly is this?
As the name suggests, if its a battery care function why do you want to disable it?
Can you explain in detail?

---

### Post by regrug on 2010-04-04
> Can you explain in detail?Well, in most notebooks the battery charging unit works independently and can not be accessed via the operating system, whereas on thinkpads and some vaios it has a software interface, that enables the user to lower the maximum charging percentage.
Sony calls this simple feature "Battery Care Function" since charging the battery the last few percents stresses it by far the most. 
This is because the needed voltage/current and therefore the heat generation in the cells rise according to the charged percentage.

Obviously, using this function has the disadvantage of not having the entire capacity available. 
So, what you want is to lower the value for everyday use and max it occasionally when you know you´ll need the full power. 

The problem is:
Once changed by a piece of software (in this case the "vaio control center" for windows) this value will remain until changed back software-wise. It is not possible to reset it any other way, as it is persistently stored in the hardware of the charging unit.

---

### Post by SuperXDE on 2010-04-28
So , did anyone discover how to fix it?

---

### Post by SuperXDE on 2010-04-28
Sorry for double post , but can this help ? [http://www.ubuntugeek.com/ibam-the-intelligent-battery-monitor-for-laptops.html](http://www.ubuntugeek.com/ibam-the-intelligent-battery-monitor-for-laptops.html) ( IBAM )

Moderator , please merge it with the one over it :)

---

### Post by eotakos on 2010-12-02
Well... I'm truly sorry that this post didn't come to my attention earlier. I could have saved you some time searching...

So, the thing is that even though you cannot enable the battery care function through ubuntu... you can disable it by just taking off the battery :-). It seems that it is a hardware thing. Whenever you take off the battery, the memory that keeps the information about that feature is erased, and the battery gets again to the default 100% charge setting.

I very much like this option and it is a pitty there is no software for it under ubuntu. This is the only reason - well that and gaming- for which I still keep my installation of windows :-|

edit:
> It is not possible to reset it any other way, as it is persistently stored in the hardware of the charging unit.
this is not the case for my laptop - it is a VGN-CS11Z

---

