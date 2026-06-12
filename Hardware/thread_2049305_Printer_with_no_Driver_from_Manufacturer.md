---
title: "Printer with no Driver from Manufacturer"
date: 2012-08-28
forum: Hardware
---

### Post by CrusaderAD on 2012-08-28
How would one go about getting a printer working that has zero support on linux? Are there packages of generic drivers one can try to see if it will communicate? Any ideas?

---

### Post by sam1948 on 2012-08-28
first best step is google with printer manufacturer and model + linux version (name number or both) 
if you won't find anything post that data here.

---

### Post by CrusaderAD on 2012-08-28
I think the first thing anyone does is Google it... :confused:

---

### Post by sam1948 on 2012-08-28
> **CrusaderAD said:**
> I think the first thing anyone does is Google it... :confused:

i guess u do, sorry.

what is the printer and linux version info?

any how you can start here:
[http://www.openprinting.org/printers](http://www.openprinting.org/printers)

---

### Post by ratcheer on 2012-08-28
Yes, there are very good "generic" open source driver sets available. One is called gutenprint. You should be able to find the Ubuntu package easily.

Once you get the gutenprint drivers installed, add your printer with CUPS. It should lead you right through the process.

Tim

---

### Post by CrusaderAD on 2012-08-28
> **sam1948 said:**
> i guess u do, sorry.

what is the printer and linux version info?

any how you can start here:
[http://www.openprinting.org/printers](http://www.openprinting.org/printers)

Thanks for the link, looks like a good resource, but this printer doesn't seem to be on the list. The printer itself doesn't have any serial numbers or anything. It's sort of a custom built one designed with a packaging system. Does anyone know if it's possible to pull this data from the command line? Model # and such? It's connected via LP1.

---

### Post by sam1948 on 2012-08-28
> **CrusaderAD said:**
> Thanks for the link, looks like a good resource, but this printer doesn't seem to be on the list. The printer itself doesn't have any serial numbers or anything. It's sort of a custom built one designed with a packaging system. Does anyone know if it's possible to pull this data from the command line? Model # and such? It's connected via LP1.

this is a long shot but if you can look under the hoods of that printer and see some chips, it is most probably it is based on a known chip set of some other printer. look for numbers and names etc there and google them. if it leads to specs of other printers try to install their drivers and then using cups try to install that printer. good luck it is not obvious to get it working but it looks like a nice challenge.

---

### Post by ratcheer on 2012-08-28
Time for a new printer?

Sorry, I hate buying printers, too. My son took his fairly modern Canon MP620 to college and last week, so I connected a 10-year old Brother monochrome laser printer. Then I went to CUPS, found the gutenprint driver for it, and it worked right away.

But if you don't know what driver to look for, that makes it really difficult.

Tim

---

### Post by aikishugyo on 2012-08-28
> **CrusaderAD said:**
> Thanks for the link, looks like a good resource, but this printer doesn't seem to be on the list. The printer itself doesn't have any serial numbers or anything. It's sort of a custom built one designed with a packaging system. Does anyone know if it's possible to pull this data from the command line? Model # and such? It's connected via LP1.

Do you know the manufacturer and/or reseller? Do you know anything about the specifications? What media types it takes, what type of print mechanism there is (inkjet, micro-dry, dot matrix, laser, etc.).

---

### Post by CrusaderAD on 2012-08-29
> **aikishugyo said:**
> Do you know the manufacturer and/or reseller? Do you know anything about the specifications? What media types it takes, what type of print mechanism there is (inkjet, micro-dry, dot matrix, laser, etc.).

I found out it's a Data Max printer.

---

### Post by CrusaderAD on 2012-08-29
Someone is suggesting that I send the printer raw DPL data, is this possible?

---

### Post by CrusaderAD on 2012-09-10
Does anyone know if I were to install the printer on a windows machine, and then share it to a Ubuntu one, will it be able to print since it's "shared" from windows and not installed on the Ubuntu machine?

---

### Post by sam1948 on 2012-09-20
> **CrusaderAD said:**
> Does anyone know if I were to install the printer on a windows machine, and then share it to a Ubuntu one, will it be able to print since it's "shared" from windows and not installed on the Ubuntu machine?

hi,
i m not sure but i think you need the driver in the linux machine.
there is a feature in chrome browser of sharing printers with yourself might be they solved it somehow.

[http://www.google.com/cloudprint/learn/](http://www.google.com/cloudprint/learn/)

good luck

---

### Post by GeForce 9500GT on 2012-09-20
> **CrusaderAD said:**
> I found out it's a Data Max printer.
 
Does Ubuntu see the printer? Open a terminal and type the following commands:
```
sudo lsusb
```
```
sudo lspci
```
 
Put both the output's here.

---

