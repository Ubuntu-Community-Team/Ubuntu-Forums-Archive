---
title: "Cups-pdf not working in Intrepid Ibex"
date: 2008-11-17
forum: General Help
---

### Post by chettyk on 2008-11-17
I have just installed Intrepid Ibex and am having difficulty getting cups-pdf to work. My recollection is that Hardy Heron included cups-pdf in the default installation, which made life so much simpler.

So after installing Intrepid Ibex, I searched around for how to install cups-pdf and found the answer in the following thread:
[http://ubuntuforums.org/showthread.php?t=982365&highlight=cups-pdf]("http://ubuntuforums.org/showthread.php?t=982365&highlight=cups-pdf")

After installing the cups-pdf package, I opened the Printing administrator box (System > Administration > Printing) and set the "PDF" printer as the default printer.

But when I use the PDF printer, say to print a web page, no output file appears. I tried restarting cups and subsequently, shutting down and restarting the computer. Still no output file.

I already have a folder by the name PDF in my root directory. In Hardy Heron, that was the folder to which cups-pdf would print.

I opened the printer properties for the PDF printer (System > Administration > Printing > PDF > Properties). When I click the button [Print Test Page], I see that the "Printer State" displays the following: "Idle - /usr/lib/cups/backend/cups-pdf failed".

How do I sort out this problem?

If I can't sort it out, I'll need to go back to Hardy Heron. I need to be able to use cups-pdf

Thanks for any help.

---

### Post by nikgare on 2008-11-17
Possible things to do:

teh PDF folder might have the incorrect permissions - remove cups-pdf, remove the PDF folder, install cups-pdf.  The PDF folder was either automatically created then, or when I printed to PDF on my box here.

Set the log level higher in cups /etc/cups/cupsd.conf and maybe /etc/cups/cups-pdf.conf

---

### Post by bigbrovar on 2008-11-17
i do get that problem some times .. seems some pdf file have this issue. what to do is install xpp which does a good job as printing pdfs

just ```
 sudo apt-get install xpp
```
then put the pdf file in your home directory and```
 xpp name-of-the-pdf-file
```

---

### Post by chettyk on 2008-11-17
Thanks for the suggestions nikgare.

> **nikgare said:**
> Possible things to do:

teh PDF folder might have the incorrect permissions - remove cups-pdf, remove the PDF folder, install cups-pdf.  The PDF folder was either automatically created then, or when I printed to PDF on my box here.


Just tried this out. Doesn't help.


> **nikgare said:**
> 
Set the log level higher in cups /etc/cups/cupsd.conf and maybe /etc/cups/cups-pdf.conf
I am out of my depths here. How do I set the log level higher?

---

### Post by dbulante on 2008-11-18
I have the same problem after installing cups-pdf, and I still don't have a solution for it.

---

### Post by dbulante on 2008-11-18
This is a post from another user, which I am copying below.

Well, i guess cups-pdf is obsolete now. I have no idea why nobody mentioned this to me! arghh...

these two threads kept mentioning a thing called "print to file", but i couldn't figure out what they were talking about until now.

[http://ubuntuforums.org/showthread.php?t=947960](http://ubuntuforums.org/showthread.php?t=947960)
[http://ubuntuforums.org/showthread.php?p=5963209](http://ubuntuforums.org/showthread.php?p=5963209)

..anyway i figured out what is now the equivalent...

Use the "print to file" option instead....

mark this thread as solved if this fixed your problem

---

### Post by nikgare on 2008-11-20
Hey that's reaaly cool - I didn't realise that was there!
I can uninstall cups-pdf now!

---

### Post by chettyk on 2008-11-20
> **dbulante said:**
> This is a post from another user, which I am copying below.

Well, i guess cups-pdf is obsolete now. I have no idea why nobody mentioned this to me! arghh...

these two threads kept mentioning a thing called "print to file", but i couldn't figure out what they were talking about until now.

[http://ubuntuforums.org/showthread.php?t=947960](http://ubuntuforums.org/showthread.php?t=947960)
[http://ubuntuforums.org/showthread.php?p=5963209](http://ubuntuforums.org/showthread.php?p=5963209)

..anyway i figured out what is now the equivalent...

Use the "print to file" option instead....

mark this thread as solved if this fixed your problem
I had noticed the print-to-file option. But, unlike with cups-pdf, not all applications provide a PDF output with the print-to-file option. A case in point is Thunderbird, which is my default email program. So currently when I want to make a PDF from an email in Thunderbird, I use the program's print-to-file option that produces a postscript file. Then the good ole ps2pdf program converts that postscript file into a pdf. The advantage of cups-pdf was that you could directly make a PDF from any program that had a print option.

---

### Post by dinarcon on 2008-11-23
Hey chettyk,

I have the "PDF" folder in my **Home Directory**, *not at root* and works nice for me. Next I describe how I solved the problem:

1.- Go to "System -> Administration -> Synaptic Package Manager"
2.- Search and install "cups-pdf"
   2.1.- I read that "cups-driver-gutenprint" has to be installed as well. In my case, it was already installed.
3.- [by [stinger30au]('http://ubuntuforums.org/showthread.php?t=983808')] Go to your home directory and create a folder named "PDF" (all letters capitalized)

after doing so, and without further configuration, I was able to print to PDF!

The same can be done at the command line as follows:
1.- "sudo apt-get install cups-pdf"
2.- "mkdir ~/PDF"

note: I tried other options before doing as indicated above. One of them (as suggested by [aggiemarine07]('http://ubuntuforums.org/showpost.php?p=6216706&postcount=18')) was using this command:
"sudo chmod 0755 /usr/lib/cups/backend/*"
...not quite sure if it helped as well.

(remark: aggiemarine07 did not include sudo as part of the command, but if not present I hadn't permission to modify the files' attributes)

---

### Post by chettyk on 2008-11-24
**dinarcon:** Thanks so much for your suggestions. Tried them all. But they don't work for me -- the cups-pdf on my machine still does not produce PDFs. :(

Oh well, I suppose I'll just have to live with using the print-to-file option in Firefox to produce PDFs. In Thunderbird, as I stated earlier, I can use the print-to-file to produce postscript files and then use the ps2pdf utility to convert them to PDF. 

Thanks everybody for all your help

---

### Post by alicemoon on 2008-11-27
dinarcon- thanks for the solution - it worked perfectly for me - I installed cups-pdf through synaptic and like you had the gutenprint already. 
I did not need "sudo chmod 0755 /usr/lib/cups/backend/*"

I can now print directly to my PDF folder but if I tick the print to file option I can now name the pdf myself and say which folder I want it printed to which is perfect. This also solves a problem I had in Open Office as decimals were not printing properly using the pdf export button in base forms - so you have given me a perfect solution :)

---

### Post by alicemoon on 2008-11-27
sorry posted twice

---

### Post by omns on 2008-11-28
> **dinarcon said:**
> 1.- Go to "System -> Administration -> Synaptic Package Manager"
2.- Search and install "cups-pdf"
   2.1.- I read that "cups-driver-gutenprint" has to be installed as well. In my case, it was already installed.
3.- [by [stinger30au]("http://ubuntuforums.org/showthread.php?t=983808")] Go to your home directory and create a folder named "PDF" (all letters capitalized)

after doing so, and without further configuration, I was able to print to PDF!
Thank you, this worked for me as well :)

---

### Post by psharboneaux on 2008-12-05
After doing lots of reading on this issue, and getting nowhere, the way I decided to solve this problem with the ".../cups-pdf failed" message was to downgrade cups-pdf to the Hardy version. First you have to uninstall cups-pdf from your system, then go to [http://packages.ubuntu.com/hardy/cups-pdf](http://packages.ubuntu.com/hardy/cups-pdf), and install this version.

Once this is done, go to synaptic, search cups-pdf, highlight it, and from the menu, select Package, Lock version.  This will stop apt from trying to upgrade cups-pdf to the faulty version.

Works like a charm!

---

### Post by blackpearl on 2008-12-10
> **omns said:**
> Thank you, this worked for me as well :)

This works for me also:p

---

### Post by dinarcon on 2008-12-13
glad to read that the alternative/solution I post, is working for others than me!

a quick question** alicemoon**, the print-to-file option you mention is for the cups-pdf printer or the built-in firefox/opera/ubuntu?/linux?*"Print to File"* printer which let's you print to PS and PDF? not really an intelligent question... :-? lol...

---

### Post by darreld on 2008-12-14
I had the same problem and also got the 'cups-pdf failed...' message.  I noticed that I didn't have a PDF directory in my home.  Created it and it works like a dream.

I had installed from the synaptic on Ibex.

-darrel

---

### Post by IllegalCharacter on 2008-12-18
> **psharboneaux said:**
> After doing lots of reading on this issue, and getting nowhere, the way I decided to solve this problem with the ".../cups-pdf failed" message was to downgrade cups-pdf to the Hardy version. First you have to uninstall cups-pdf from your system, then go to [http://packages.ubuntu.com/hardy/cups-pdf](http://packages.ubuntu.com/hardy/cups-pdf), and install this version.

Once this is done, go to synaptic, search cups-pdf, highlight it, and from the menu, select Package, Lock version.  This will stop apt from trying to upgrade cups-pdf to the faulty version.

Works like a charm!

Works perfectly! Thanks!

---

### Post by heatpumpcontrol on 2009-02-26
> **psharboneaux said:**
> After doing lots of reading on this issue, and getting nowhere, the way I decided to solve this problem with the ".../cups-pdf failed" message was to downgrade cups-pdf to the Hardy version. First you have to uninstall cups-pdf from your system......

Once this is done, go to synaptic, search cups-pdf, highlight it, and from the menu, select Package, Lock version.  This will stop apt from trying to upgrade cups-pdf to the faulty version.

Works like a charm!

This is the only one that would work for me. However, I first had to update my sourcelist with this [list for Hardy]("http://ubuntuforums.org/showpost.php?p=4613915&postcount=2")

```
gksudo gedit /etc/apt/sourcelist
```

[COLOR="Red"]**NOTE: Be sure _[SIZE="5"]NOT[/SIZE]_ to select 'Mark All Upgrades' after adding the following list  !!!!!!!!!!!!!!![/COLOR]**

Add this at the bottom, they are not all needed but you're only going to use it to install one program. 

> # Hardy
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner


update your sourcelist so you can have the option of the previous 'cup-spdf' version and select and install. After install lock the version and then go back to you sourcelist (as above) and remove the added list. Press reload and you're done.

):P

---

### Post by BartInTN on 2009-03-31
Fresh install of 8.10... and creating the PDF dir in my home directory was the answer.  Thanks.

---

### Post by *uu on 2009-06-11
For me also installing the older cups-pdf version from the Hardy repositories did the trick. And a new feature: The PDFs thrown into the ~/PDF directory now finally have useful names, apparently taken from the printing application's window title. :D In Intrepid all PDFs hat the name and window title "_stdin_", which was sort of ugly, but well, better than no PDFs.

One thing I noticed, though, when installing the Hardy version of cups-pdf through Synaptic: as a dependency the package named "cupsys" had to be installed with it, though it was taken from the jaunty repos. Jaunty's version of cups-pdf seems not to depend on this package. As a test I removed all cups-pdf and cupsys again and re-installed cupsys additionally to Jaunty's version of cups-pdf, but that didn't change a thing. No PDF would be created, no matter if ~/PDF existed or not. So, now I'm back to Hardy's cups-pdf, which works just fine.

I guess, for some machines they simply broke cups-pdf in Jaunty...

---

