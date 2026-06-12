---
title: "[printer] canon pixma mp780"
date: 2005-09-16
forum: Hardware &amp; Laptops
---

### Post by stoeptegel on 2005-09-16
I bought myself this printer some months ago, it's a very nice printer. Unfortunately i can't get is to work in kubuntu.

I am hoping someone here can take away my bad dream, and can give me some advise.

Cheers.

---

### Post by David Haas on 2005-09-16
stoeptegel--I don't see a driver (PPD file) listed for your printer in Ubuntu 5.04 at "/usr/share/cups/model/foomatic-ppds/Canon," where most of the PPD files for Canons are located, or at "/usr/share/cups/model/gimp-print/4.2". I also don't see any mention of this model in past Forums--I did a search. You might also try for help in the Kubuntu forum, but the drivers in Kubuntu are probably the same as in Ubuntu. It's well known that Canon provides poor support for Linux, in contrast especially to HP, which provides drivers free to the Linux community. If you can't get help from others here or on the Web, than you might consider switching to an HP printer--but if you do, you might want to check to see whether Kubuntu contains in its distro the driver for it.

Good luck,
David

---

### Post by David Haas on 2005-09-16
I forgot to mention that Turboprint supports Canon printers, and I see that it has one for the Canon PIXMA mp780. These are not, however, free drivers. See their Web site at [http://www.turboprint.de/english.html](http://www.turboprint.de/english.html).
David

---

### Post by stoeptegel on 2005-09-17
It's a shame that turboprint is so expensive for just a printerdriver, :neutral: but on the other hand... at least there's a solution. Hmmm, my experience with HP printers is to bad (lots of broken hardware, ink price) to buy me one again, so  maybe turboprint will do.

Thanks for giving some headmassage David Haas.

---

### Post by megahead13 on 2005-09-17
Hi! Stoeptegel, before you decide to buy drivers from turboprint.de you may try this: [http://www.ubuntuforums.org/showthread.php?t=38995&highlight=pixma](http://www.ubuntuforums.org/showthread.php?t=38995&highlight=pixma) Many guys have said that they managed to get the printing capabilities of their MP780 work. I have the same multifunctional, but haven't succeeded yet. I am working on it. Will let you know, if I have any progress...

---

### Post by new2hoary on 2005-09-17
[QUOTE=stoeptegel]It's a shame that turboprint is so expensive for just a printerdriver, :neutral: but on the other hand... at least there's a solution. Hmmm, my experience with HP printers is to bad (lots of broken hardware, ink price) to buy me one again, so  maybe turboprint will do.

Thanks for giving some headmassage David Haas.[/QUOTE]
 I've used turbo print for a couple of years now first with a Canon i850 and then with a Pixma IP5000. I have nothing but good things to say about it - It is very good.

They have a free version but this doesn't allow you to print at full resolution, but at least you can try it and see if you like it.

I'm not sure if it will support your scanner function. Canon don't support Open software at all. They do supply details for their printers (for a price) to developers like turboprint. However they do not do the same with their scanner technology which they class as trade secrets.
This makes it very difficult for third party driver development.

---

### Post by megahead13 on 2005-09-17
[QUOTE=new2hoary]I've used turbo print for a couple of years now first with a Canon i850 and then with a Pixma IP5000. I have nothing but good things to say about it - It is very good.

They have a free version but this doesn't allow you to print at full resolution, but at least you can try it and see if you like it.

I'm not sure if it will support your scanner function. Canon don't support Open software at all. They do supply details for their printers (for a price) to developers like turboprint. However they do not do the same with their scanner technology which they class as trade secrets.
This makes it very difficult for third party driver development.[/QUOTE]
 Allright! I can now print from my MP780. Found what the problem was. Stoeptegel, follow the instructions from the link I gave you step by step and normally you will print from your multifunctional. Take care

---

### Post by stoeptegel on 2005-09-19
[QUOTE=megahead13]Allright! I can now print from my MP780. Found what the problem was. Stoeptegel, follow the instructions from the link I gave you step by step and normally you will print from your multifunctional. Take care[/QUOTE]

I got stuck at: 
sudo ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml.so.1
ln: `/usr/lib/libxml.so.1': File exists

When i try to print something from kword there's nothing to happen.
I havn't got much time to invest in this though, translating the ubuntuguide cost me much time lately.  :-#

---

### Post by megahead13 on 2005-09-25
[QUOTE=stoeptegel]I got stuck at: 
sudo ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml.so.1
ln: `/usr/lib/libxml.so.1': File exists

When i try to print something from kword there's nothing to happen.
I havn't got much time to invest in this though, translating the ubuntuguide cost me much time lately.  :-#[/QUOTE]
Sorry for my delay in answering. For fixing the libraries you can type:

```
sudo apt-get install libtiff3g
sudo apt-get install libpng2
``` 

instead of 

```
sudo ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml.so.1
```

The guide for Canon drivers found here in ubuntuforums (the link I gave above) is the same with this guide from the Kanotix forum: [http://forum.kanotix.net/viewtopic.php?t=7784](http://forum.kanotix.net/viewtopic.php?t=7784)

The only difference is tha you don't have to type this:
```
# remove module that produces errors with this printer
rmmod ehci_hcd
```

as it is mentioned there. I wish you good printings ;-)

---

