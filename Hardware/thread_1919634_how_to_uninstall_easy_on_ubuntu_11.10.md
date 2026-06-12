---
title: "how to uninstall easy on ubuntu 11.10"
date: 2012-02-03
forum: Hardware
---

### Post by Johannes1395 on 2012-02-03
hi im new and yhea i want to unisntall softwares and programs easy whith a other program that is not ubuntu sofware center cus every times i randomly its reloading the software page :S sp i get really mad for that but it is so i dont know what programs i can unisntall so if there where any programs that i can install or somthing likely and do so its unisntall every thing on the computer 'but' ceeps every program that you have when you have been isntalling ubunut thx for the help you are all nice ;):D:popcorn:

---

### Post by madvinegar on 2012-02-03
You can try to do so by Synaptic Package Manager.

Find (through search) the software that you want to uninstall, right-click it and select it for removal, and then click apply.


You can also do that through terminal.

```
Sudo apt-get remove name-of-software
```

---

### Post by Johannes1395 on 2012-02-03
> **madvinegar said:**
> You can try to do so by Synaptic Package Manager.

Find (through search) the software that you want to uninstall, right-click it and select it for removal, and then click apply.


You can also do that through terminal.

```
Sudo apt-get remove name-of-software
```

thx gonna try that out but it wasnt really that i mean i mean more in the end of the topic so i can "like" reisntall ubuntu but whithout using windows or somthing :P more like unistnall every single software i have been sitnalling since i have been using ubuntu form the first time ever so if you can be kinmd and recomend somthing like that? thx EDIT: the synpatic package manager craches every time i starting it ;(

---

### Post by Mark Phelps on 2012-02-06
I strongly recommend against going through and uninstalling everything you don't think you will need.  This is not MS Windows, where every app brings with it its own custom libraries; this is Linux, where lots of apps reuse the same libraries.

If you just charge through, uninstalling right and left, you run the risk of removing something that another app or service relies upon.  And, in the end, you can break Ubuntu to the degree that it won't work anymore.

If what you really want is a "minimalist" install of a Linux distro that installs very little stuff, then you need to consider switching distros to something like Lubuntu.

---

### Post by mastablasta on 2012-02-06
or use mini.iso and build from the base during system install, selecting desktop environment and programmes you need.

---

