---
title: "Monitoring Printer Ink Levels ?"
date: 2005-08-30
forum: Hardware &amp; Laptops
---

### Post by 5-HT on 2005-08-30
Hi,newbish question i'm struggling with:

I'm just wondering if it's normal to not be able to check the ink level status of a printer.

I tried two different printers and used the drivers recommended on [www.linuxprinting.org](www.linuxprinting.org). 
One rated as only working partially working in linux , while the other, an Epson C60, was described as working perfectly in linux, but I can not check the ink level of either through 'printer properties'.

After some searching, people have mentioned getting MTInk to gauge ink levels, but I was just wondering if linuxprinting.org describes the printer as working perfectly in linux with a certain driver...should'nt that allow me to access all the options/properties of that printer such as the ink levels? 

If not does anyone have any suggestions as to any other good program for displaying ink levels?


Thanks for any help/info.

---

### Post by Adam Lee on 2005-08-31
I own an Epson and I check the ink level by typing 
```
sudo escputil -i -r /dev/usb/lp0

```
in the terminal.

And the output looks something like this 

```
Ink color    Percent remaining
                Cyan     56
             Magenta     57
              Yellow     57
         Matte Black     54
```

If you haven't installed escputil, I highly suggest you to do wo because it's really helpful. 
Once you install it, you can read the manual and figure out how to make it useful.
well, I'm a newbie also, I wish I help you more.

---

### Post by autocrosser on 2005-08-31
Well-The printer driver is just that--it runs the printer--In Linux (& MAC OSX) the Ink level--head cleaning--etc is a seperate program.

I use mtink--download it from Synaptic & then use Smeg to create a launcher--Name it what you want (I used Epson Printer Utility--how original:-?)--then add whatever info you want--link it to mtink & choose a icon--your done.

It seems harder at first to do it this way--but you get to customize YOUR system YOUR way--not the "default" way someone else "thinks" your system should look.

If you have any probs--just ask--there are quite a few of us that are willing to help.

---

### Post by 5-HT on 2005-08-31
Thanks for the help Adam Lee & autocrosser.
Never knew that that the printer driver doesn't deal with maintenance (ink levels,head cleaning, etc).

I mentioned the Epson because it reportedly works great in Linux, but I pulled it out of storage (been there for a few years) and I read that the print heads on Epsons aren't in the cartridges so if they get clogged up (such as from inactivity) it's a real hassle to get them cleaned. 
The cartridges on it are empty now, and instead of going ahead a buying some more with the possibility that the heads are clogged and it may not even function, I'd like to stick with my current Canon  printer (too bad they're not as well supported- but it does work alright for b&w text).

From the looks of it, escputil is an Epson-specific utility, so I'll try Mtink and see if that works well.

Thanks again for the help.

---

### Post by 5-HT on 2005-08-31
Ha, well it seems that Mtink is also an Epson specific utility.

I'd really like to use my Canon S520 if possible...anyone know of any utilities for checking ink levels on Canon's (I've done some searching but haven't come up with anything)?

---

