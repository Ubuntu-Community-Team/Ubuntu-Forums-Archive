---
title: "Problems with G85 Officejet on 6.10 livedisk"
date: 2007-01-24
forum: Hardware &amp; Laptops
---

### Post by newaustralian on 2007-01-24
My good old G85 "all in one" works fine under XP so I thought I would try it with the live CD version of Ubuntu 6.10.

Configuring the printer seems to work fine.  When I print to the G85 the queue shows a job but nothing prints and the queue clears with no error messages so the system thinks it all works. 

Checking the forum it appears others have had problems with G85's too. I have tried several driver combinations and several acpi=off/on etc but same result.  Also tried switching printer on and off after configuration and prior to printing as I have to do this when I return to XP before the printer will work under XP.

Had the same problem with knoppix as well.

Any help appreciated

---

### Post by newaustralian on 2007-01-27
After searching the forums and guides and experimenting with both the Gnome configuation and using "hplip" I have finally solved this one. Steps are:

1 Select System-Admin-Printing under Gnome

2 Add printer and go Forward

3 Select Local, then 'Select Use another printer by specifying port', then select the USB OfficeJet G85 with a serial number corresponding to your printer (in my case this was second in list), go Forward

4 Select HP and OfficeJet G85 which will bring up the hpijs driver and 'Apply' to complete configuration

5 Set OfficeJet G85 as default printer

Now come the crucial steps

6 Switch off and Switch on the printer

7 Restart the 'cups' system by typing "sudo /etc/init.d/cupsys restart" in a terminal window

and all is ready for printing.

Hope this may help others.  Those old OfficeJet G85's still have life in them yet.

---

### Post by bradshoults on 2007-01-28
[http://ubuntuforums.org/images/smilies/icon_biggrin.gif](http://ubuntuforums.org/images/smilies/icon_biggrin.gif)
This worked for me!  Thank you!  I have a hp g55 all-in-one, by the way.

---

### Post by robbie9gallagan on 2007-02-23
Worked for me also..

was about to give up on printing and go back to pen and paper..

I have an Officejet G85..

---

### Post by sieg on 2007-02-26
This solved my problem with ubuntu! Thanks! What a stuggle it has been!

Does anyone have any insights as to what the actual problem is that is being solved here?

Im asking because I'm hoping to get some insights as to how to solve the problem with other distros such as UnSlung 6 and fedora 6.

Unslung 6 has the exact same symptoms but, of course, no such option (to select G85 with a serial number corresponding to your printer). I think Knoppix also has these symptoms.

Fedora Core 6 prints, but there is a  5 minute delay before it prints.

Thanks so much!
Siegfried

---

### Post by pirothezero on 2007-03-01
I have to say same thing. G55 wasn't working and then it was.

Anyone have issues follow post #2.

---

### Post by marc_paquin on 2007-03-25
Evening all,

  Sorry to report that this little tip failed to work.  Using 6.10 and an HP G85, followed the steps religiously but a test page will not print.  Neither will a print from Firefox.  The error log yields this: 
[25/Mar/2007:20:57:11 -0400] cupsdAuthorize: Local authentication certificate not found!

Being a noob, I'm fumbling as I go.  What info can I supply you that would lead to a solution?

Thanks,

M

---

### Post by newaustralian on 2007-03-27
I put together my solution without really understanding the source code logic so i cannot repy on fundamentals.  I did consult the Hewlett Packard linux  site which offers support for all their printers.  Suggest you try a post on their forum and maybe you may get a more definitive response.  To me it seemed logical that if you had to restart the printer itself by switching it on and off then you may also need to restart the cups system as well.

Once i moved from the live disk to a full installation the problem disappeared. In addition, the scanner application SANE worked perfectly.

Hope this helps:popcorn:

---

### Post by SonicSteve on 2007-04-18
I was just given one of these G85's. I just posting to report that it works very well with Ubuntu 6.10. Both printing and scanning are functioning well.

---

### Post by lewisharvey on 2007-04-22
I just got this work in the new Ubuntu "Fiesty Fawn". I am using a G85.

---

### Post by jkzubu on 2007-05-01
Great help.  By the way, anyone else with the G85 having problems scanning using the adf?  My adf scanns the first page and continues to scan the first page without cycling through to consecutive pages.  Need a fix. (Feisty).

---

