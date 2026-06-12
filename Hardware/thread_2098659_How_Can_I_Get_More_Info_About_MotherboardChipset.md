---
title: "How Can I Get More Info About Motherboard/Chipset?"
date: 2012-12-27
forum: Hardware
---

### Post by ohnonot on 2012-12-27
Hello everybody,
i have a somewhat oldish MSI vr601 notebook.
Searching for technical info for this model on the internet, it seems that there's differences from machine to machine, although the model name is the same.

so i wonder if it is possible to get very detailed info about chipset/motherboard capabilities, particularly this:

is there a RAM limitation of 2GB max. or not?
if yes, is it "hardwired" or could that be changed by i.e. udating BIOS?

(it is a 64bit machine)

thanks for reading,
hopefully someone can help.

---

### Post by cmcanulty on 2012-12-27
try these I did the dmidecode one and then copied it to writer and printed it to file as pdf and now it is real nice to read


[http://www.addictivetips.com/ubuntu-linux-tips/how-to-get-ubuntu-hardware-information/]("http://www.addictivetips.com/ubuntu-linux-tips/how-to-get-ubuntu-hardware-information/")

and 

 [https://launchpad.net/ubuntu/+source/hardinfo]("https://launchpad.net/ubuntu/+source/hardinfo")

and

[http://embraceubuntu.com/2007/02/18/find-hardware-specs-details-on-your-computer/]("http://embraceubuntu.com/2007/02/18/find-hardware-specs-details-on-your-computer/")

---

### Post by ohnonot on 2012-12-27
thanks!
dmidecode gives me a lot of info;
i can't really see anything that would say there's a 2GB limit.
however, reading onwards from "Memory Controller", i can see lots of info that seems to relate to my question.
i would be happy if someone could take a look at [the output]("http://codeviewer.org/view/code:2da9").

my situation is this, i got a 2nd memory chip yesterday, so now i have 2 2gb chips, and they each work when alone, but not when put in together.
when put in together, they worked once yesterday, but then the machine froze in the worst possible way, and since then the bios ram check can't get over 1015MB, the machine does not boot.
however i can boot normally with only one chip!! and it doesn't matter in which of the 2 slots it is.

here's the labels of the 2 ram chips:

[FONT=Verdana][SIZE=2]1.

Transcend
2GB DDR2 667 SO-DIMM CL5
508509-4311 RoHS [ED]

2.

hynix
2GB 2Rx8 PC2-64005-666-12
HYMP125S64CP8-S6 AB 0921[/SIZE][/FONT]

meanwhile, i will open the machine again and see if i can find the mysterious 3rd slot...

---

### Post by pardalet on 2012-12-27
Not too hard to work out...

If you look at your output, under the *Base Board Information* section you can see your mobo is an **MSI MS-163C**. Search this in Google to find out whether there's a 2GB RAM limitation.



Spoiler: There is.

---

### Post by ohnonot on 2012-12-27
thanks,
looking at [this]("http://www.msiwhitebook.com/product_spec.asp?model=MS-163C")
it seems that there really is a 2gb limit, however it also says windows vista only and i'm running linux right now!
it also states no bluetooth, but i have bluetooth up and working right now.

sigh.... i know there's only a small chance but i will not mark this as solved yet....
maybe i'll just try to update the bios, see what happens.

ps:
i have been able to further study this behavior- there's some tests during bootup that can be disabled in the bios. if i do that, i can boot with 4gb ram, but inadvertently the system crashes after some time.
if the test is enabled, the bios just hangs there, no booting.

---

### Post by cmcanulty on 2012-12-27
try reversing the chips in the slots sometimes will work

---

### Post by ohnonot on 2012-12-28
thanks, i really tried all possible positions;-)

it just seems so weird to design a 64bit computer that can't take more than 2gb of ram.

---

### Post by Yellow Pasque on 2012-12-28
It's a chipset limitation, so no BIOS hacking is going to fix it. The design decison was probably made to minimize production costs and power consumption.
[http://ark.intel.com/products/29830/Intel-82GL960-Graphics-and-Memory-Controller](http://ark.intel.com/products/29830/Intel-82GL960-Graphics-and-Memory-Controller)

---

### Post by ohnonot on 2012-12-29
thanks temüjin, i will take that for absolute truth and probably save myself lots of trouble.
:rolleyes:

---

