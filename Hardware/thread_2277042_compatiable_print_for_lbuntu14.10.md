---
title: "compatiable print for lbuntu14.10"
date: 2015-04-25
forum: Hardware
---

### Post by joe103 on 2015-04-25
I am having a problem tring to get my new hp envy printer to print in lubuntu when i click print it the printer dose noting but on the little screen on the printer it says it is now printing. what is the problem.

---

### Post by joe103 on 2015-05-06
i have a 8 year old pentium 4 pc running lubuntu 14.10 on it i want to which printer would the best compatiable for a computer like my.

---

### Post by dino99 on 2015-05-06
if your mobo have an usb port, then you can choose the hp printers (might be the most supported brand)

---

### Post by joe103 on 2015-05-07
i have a hp envy 4500 and i am having problems trying to get it to print.

---

### Post by QIII on 2015-05-07
Hello!

Is it a networked printer or attached to you machine directly?  How is it attached?  Have you installed a driver for it?  hplip? What have you tried in your attempts to get it to work?

The more information we have, the greater the chances that we can help.  As it is, we can only make stabs in the dark, which would be frustrating for you and for us.

---

### Post by mörgæs on 2015-05-07
When using new hardware it's always a good foundation to use the newest software available. 

Lubuntu 15.04 has an updated hplip so it's worth a try to install this one. 14.10 is soon out of support anyway.

---

### Post by cariboo on 2015-05-07
If you want a Ubuntu compatible printer, stay away from the very inexpensive consumer grade printers. Spend a few dollars more on an office printer, and at least be guaranteed that it will work with your system.

I have a Brother HL-5250dn and an Epson R340 both were easy to set up and easy to use.

---

### Post by Bucky Ball on 2015-05-07
Threads merged.

You might save yourself some cash by attempting to get the HP Envy working. Consequently, I have merged your threads as things are starting to drift toward that anyway, the thrust of your original post a week ago.

HP are generally very Linux friendly so I would advise either a Brother or HP anyhow, but you already have a HP, so let's see if we can get somewhere with that.

PS: If you don't receive support on a thread, give it some time (we operate across many time-zones) then simply 'bump' it. Just post 'bump', or better still, bump the thread by posting about what you have been trying to get things working and an update of where you're now at with it ... 

Good luck.

---

### Post by pdc on 2015-05-07
Hey Joe;

____________

my attempt at offering you help:   ................. so HP provide hplip to make HP printers work on linux [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

____________________

according to HP, you need version [SIZE=4][COLOR="#0000FF"]3.13.6[/COLOR][/SIZE] for your HP Envy 4500 ..................and as 14.10 had [SIZE=4][COLOR="#FF0000"]3.14.6[/COLOR][/SIZE] you will be fine with 14.10

____________________

they provide a troubleshooting page to help folks [http://hplipopensource.com/node/224](http://hplipopensource.com/node/224)

and on its basic page [http://hplipopensource.com/node/332](http://hplipopensource.com/node/332) HP suggest you open a terminal: *how to do that .............. well ............. hold down the control and alt and t keys all at once* 

..............once that is done ........................  type ```
hp-check
``` in the terminal and hit your ENTER key and read what it says .................

then open your PRINTERS box from the main ubuntu menu............ and see if there is an entry that has been created for your Envy 4500; if there is no entry, HP suggest you type ```
hp-setup
``` and again hit ENTER and let hplip works its magic 

_____________

how are things going so far after this?

---

### Post by joe103 on 2015-05-11
the printer is conected directly by usb i am not sure if is networked  dose it have to be on a single computer. i have tryed to reinstall the drivers 6 times i did have one problem trying to plug my usb in one of my usb slots an a pieace broke off in my usb connnector i wonder if the conector on the wire is ok. on the printer there is a small screen  an when i click print in my computer the little screen on the printer say it is now printing but nothing happens.

---

### Post by pdc on 2015-05-11
Hey Joe; have a read at the post just above yours: there are a few suggestions there; 

if you can learn how to open a terminal, that is really useful .............some of us think ............................

..........hold down 3 keys together ...................they are ...............the control and the alt and the t keys .............. when the terminal opens, .............make sure your printer is plugged in; and turned on; and connected 

.............................then type in ```
lsusb
```

..............is it showing your HP printer as being there? If so type ```
lpinfo
``` ...............and if all is going well; copy the result; and paste it back here

---

