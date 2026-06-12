---
title: "Install Hp Deskjet F4180"
date: 2007-09-29
forum: Hardware &amp; Laptops
---

### Post by markk1994 on 2007-09-29
I need help installing this printer any suggestions?

---

### Post by aashay on 2007-09-29
Have you tried System->Administration->Printing and then Adding the new printer?

---

### Post by markk1994 on 2007-09-29
BTW: Im using Kubuntu

---

### Post by DarkStarAeon on 2007-09-29
You can get it to print, but I have yet to get it to scan anything. I don't think it's supported yet by either xsane or hplip.

I don't know the method for Kubuntu though, sorry.

---

### Post by Hisstareia on 2007-09-30
> **DarkStarAeon said:**
> You can get it to print, but I have yet to get it to scan anything. I don't think it's supported yet by either xsane or hplip.

I don't know the method for Kubuntu though, sorry.

I was able to get it to scan fine using current gutsy repository of xsane. You have to initiate the scan from within xsane, and not from the printer itself. As for kubuntu, I'm unfortunately also out of information since I'm not familiar :(. Least I can tell you is print, scan, and copy work fine in ubuntu for me, and I would assume the same for you since u/k/xbuntu use CUPS. Try this website and see if it helps:
> 
[http://printing.kde.org/](http://printing.kde.org/)
Good luck!

---

### Post by DarkStarAeon on 2007-09-30
well that's cool to know it will work with Gutsy! can't wait!

---

### Post by losmurfs on 2007-10-11
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html) fully supports the HP Deskjet F4180 as a printer, if you download hplip-2.7.9.run (HPLIP Installer) when you run first "chmod +x hplip-2.7.9.run" then run "sudo ./hplip-2.7.9.run"  This will automatically install all of the packages that are required to install and print the F4180 and during the install it will prompt you to unplug the printer if it is already plugged in, then it will prompt you to plug it in, and then it prints.  However, when I tried to scan all of the printer's lights flashed and the copy display displayed an E.  So I don't know if it didn't scan because I didn't restart sane after the installer updated sane or if the scan feature just isn't supported yet via hplip.

---

### Post by losmurfs on 2007-10-11
Turns out that if you install from the link provided in my previous post, it scans just fine.  I had tried to test it using Gimp, I clicked Acquire... then XSane... and then I clicked on my printer (that does not work), if instead you click Acquire... then XSane... and then click Device Dialog... it sans perfectly.

---

### Post by DarkStarAeon on 2007-10-11
Well, something isn't right then, because HPLIP is already installed, has been, and it won't scan. I'll have to go through a process of elimination I guess to figure out what the problem is.

---

### Post by DarkStarAeon on 2007-10-11
Haha, the something wasn't right was my eyeballs. I thought I had the same version number as the one you said to download, I looked again and yeah, I had an older version. lol

Thanks for the tip, much appreciated. :)

---

### Post by Lorenz on 2007-10-14
Did everything work for you then at the end?
I plan to buy one as well,  but only if it works for sure!

---

### Post by DarkStarAeon on 2007-10-14
Sorry, yes, everything works great. Prints, Scans, Copies nicely. Not hard at all to get going.

I will say one thing though. We had the F4180 hooked up to XP first, and the print quality was slightly higher on lower quality paper. For some reason the print quality is the same on higher quality paper.
But as I said, it was a slight difference. Still looks good.

---

### Post by Lorenz on 2007-10-15
Thanks for the answer!
I bought a slightly different version today, a C4280. 

Everything works without any problems, a fine printer/scanner/copier for a reasonable price.
I wish more manufacturers (I assume HP is involved in hplib) would support Linux as nicely as that!

---

### Post by DarkStarAeon on 2007-10-15
No problem :)

I saw that model, I'm thinking of replacing my other printer for that one. Good to know it works!

Yeah I've had great luck with HP everything. Two of my desktops are HP's, one of my laptops, both my printers, and my digital camera. Although, I avoid the integrated graphics and opt for Nvidia.
If HP starts selling Ubuntu on it's desktops and laptops I would definitely be a customer.

---

### Post by eheyl on 2007-10-28
the 4180 is great. One button copy seems to work and it prints just fine. I'm wondering if anyone knows how to get the one button scan working? Scanning works fine through xsane but it would be nice to just push the button too :)

---

### Post by wireless on 2007-10-28
Now Lets be nice and send HP "Thank You" Letters for being so generous  to the OPEN SOURCE COMMUNITY and releasing Open Source Drivers for its products :)

---

### Post by eheyl on 2007-10-28
interesting thing though, I assumed that I would need the hplip to enable all this. and I didn't which is good as it wouldn't install the required packages. But I'd still love the one touch scan and do wonder why the one touch copy works..??Not at all complaining..No no no. just wanting to dig into it a bit deeper. you know I think I will shoot off the HP Linux team and thank you email!

---

### Post by wireless on 2007-10-28
if im not mistaken the hplip is build-in the kernel since feisty. I once took a ps c6180 pluged it in to feisty and it just worked. This printer is hell to install in m$...
the copy button works coz for copying you dont need a pc. The scan button requires interaction from the pc side. To identify the button was press and to stat the scanning software. Anyway its a minor thing I guess...isn't it..?:)

---

### Post by barbedsaber on 2008-02-09
can someone please tell me if the scanner on the Hp DeskjetF4180 is a flat bed scanner, and the cost of the ink cartriges, particulalrly if they are the XL cartiges, I have been eying off this printer for a little while, but it is really hard to find this infomation on the internet (maybe that is just a sign of my abysmal searching skill) anyway, all help would be apprecciated, thanks.

---

### Post by 11hjpphty76lkjj on 2008-02-26
The DeskJet F4180 is a flat bed scanner.  You can find some pictures and more specs by doing a google (or other) search.

And thanks for the kind words about HPLIP.  I'll be sure to pass them to the rest of the team.  

Sorry for the delay, I'm a bit behind on my forums.

All the best,

Aaron

---

### Post by FokkerCharlie on 2008-02-29
HPLIP is indeed a nice bit of software.

Is it likely that 1-touch scanning will be supported in the future?  It's about the only feature missing.

Cheers
Charlie

---

### Post by 11hjpphty76lkjj on 2008-02-29
Charlie,

We are king to provide this at some point in the future.  I can't give any ETA but it's on our  todo list for a future release.

Thanks for your support!

Aaron

---

### Post by Stephen Shellard on 2008-03-02
I followed the  Manual Build and Install Instructions for Ubuntu  until stage 5 when instructed to enter the command Make in the Terminal.  It said
  IMPORTANT You want to run make as a regular user, NOT as root.  I didn't really understand the implications of this at all.  Decide to run the make command any way as stated but was returned an error:  no target specified;  no make file found.  This didn't altogether suprise me though when I open the hplip directory on my desktop, it does have a makefile.am (locked) and a makefile.in

Don't quite know what to do next.

---

### Post by 11hjpphty76lkjj on 2008-03-02
It's best to use the automatic installer with Ubuntu, it will walk you through the install and you'll have less problems.

A

---

### Post by bradleyds75 on 2008-05-28
i got the printer to work with the autoinstaller from the link you recommended..now if I can get my scanner to work!

---

### Post by 11hjpphty76lkjj on 2008-05-29
The scanner should work with HPLIP.

If you run 

xsane

and try and scan it doesn't work?  What does it do?

A

---

