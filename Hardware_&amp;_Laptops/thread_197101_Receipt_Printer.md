---
title: "Receipt Printer"
date: 2006-06-15
forum: Hardware &amp; Laptops
---

### Post by Linuturk on 2006-06-15
I've setup a nice Point of Sale system using Xubuntu 6.06. It's all web based, and works like a dream.

I need help finding a receipt printer that will work with Xubuntu (printing from firefox),

and

the receipt printer has to be able to kick out our MS Cash Drawer. (EP-125KL)

What receipt printer do you use? I've been to [www.linuxprinting.org](www.linuxprinting.org) , but I can't seem to find any receipt printers on there.

Thanks a lot.

---

### Post by randlieb on 2006-08-25
just saw your post. have just installed ubuntu at work to use with a pos system (phppos) and have it all set to go except for the same situation. have a agp cash drawer. want to know what receipt printer will work with ubuntu. also any code that will open the drawer upon printing the receipt.

---

### Post by Linuturk on 2006-08-26
I'm using the same POS system actually ;p

Star receipt printers work the best with Ubuntu. Check their page for what specific models work with linux. 

I hope your cash drawer can be kicked out by a receipt printer, because that's the easiest way to get it to work automatically. The codes are built into the receipt printer, but be sure the receipt printer and cash drawer are compatible as well. it's a three way compability that limits your choices, so research it carefully.

---

### Post by randlieb on 2006-08-27
small world!

thanks for the info. had just come across star printers in my searching when i checked my email and found a link to your latest post. it looked right so it was nice to get a confirmation. was then able to find the driver for the tsp series, downloaded and installed it on my home ubuntu to make sure it installed ok into the cups database. it did. hooray!

seems like the only variable left is does the printer kick out my cash drawer. guess we'll just have to buy one to find out.

thanks again.

---

### Post by g_rael on 2006-08-28
I made a printer controller for a thermal print head some years ago. Used an Atmel AT90S8535 microcontroller for the stepper motor control and to pump out the relavent character scan information to the thermal head buffer which was almost 600 pixels wide, and a stepup switch mode boost regulator to generate it's 24 volts from the PC's 12 volt rail. I didn't go as far as many of the major printer manufacturers do, and put proximal heating control in.... where you have a dark spot that is also a thermal hotspot ! for full optimisation and maximum print speed, you have to take such things into account. I browsed the web for a nice fixed width font and broke it into assembler pixel listings with my VB6 that I used for front ends. Also made a test program for the finished assembly.

We didn't control the cash draw from it, another company was doing software for the shop front end in visual C++, and they already had something sorted.

They had serious memory leak issues which my customer tried to resolve with more memory in pure desperation, although the C++ developers never admitted responsibility to my knowlege, it was most likely a microsoft component of the version 5 C++ code that had a documented memory leak on the serial driver !

I suggest you check on your recipt printers, most likely one of the serial port output signals from the PC will be spare, and you can tap into it to get a cash drawer control input.\\:D/

---

### Post by Rick Z on 2007-08-03
Hi I am new in ubuntu/linux.  I am looking to setup a cashier register system as well.  I found this forum there.  I think it's an excellent explanation. Randlieb, can you tell me what kind of cashier drawer you purchased?

---

