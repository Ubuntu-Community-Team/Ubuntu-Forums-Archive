---
title: "Lexmark P3150"
date: 2005-12-22
forum: Hardware &amp; Laptops
---

### Post by debernardis on 2005-12-22
Owners of this combo printer should be aware of [http://users.cybercity.dk/~dko12479/](http://users.cybercity.dk/~dko12479/) where a working driver can be downloaded.
Just convert rpm packages in deb packages with alien, and don't forget to set inkset as cmy instead of cymk, otherwise you'll get bad printouts.
According to the coder, should work also for Z700, Z705, Z708, P706, Z707.

---

### Post by debernardis on 2005-12-26
Bad luck - no native driver for P3150 scanner yet.
So, a viable solution is:
1) install vmware player as per [http://www.ubuntuforums.org/showthread.php?t=84275&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=84275&highlight=vmware)
2) install your favourite windows flavour (I used an old copy of win 98 )
3) connect your p3150 to your pc's usb port (NOT to an hub - in my hand that doesn't work)
4) under the 'device' menu of vmplayer you are going to find three P3150 related usb devices. I had good results enabling two out of three, apparently identical, 'Lexmark 3100 series' devices, and leaving disabled the third, but this might be due to some problems in my setup, so be prepared to experiment. Apparently, you cannot enable more than two usb devices at a time.
5) download your driver from [Lexmark.com]("http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:402:0:0&emeaframe=&target=http://downloads.lexmark.com/cgi-perl/downloads.cgi&target=http://downloads.lexmark.com/cgi-perl/downloads.cgi&&req=:::::"), according to the guest OS you chose, and install it.
6) hopefully you're done!

When I shut down my virtual machine and then fire it up again, it appears I need also to disconnect-reconnect the printer's usb cable, otherwise the usb connection is not recognized by vmware.

Snapshot attached (win98 vmware machine with lexmark control center on kubuntu desktop).

---

### Post by debernardis on 2006-01-12
In this fascinating thread on P3150 printers, I am the only inhabitant. Where are you, o my Friday?

All of a sudden my printer stopped working. 
I started fiddling with CUPS with very scarce results and soon lost all my hopes of a printing ubuntu.

Reading [this open-source horror story]("http://www.catb.org/~esr/writings/cups-horror.html") made my blood freeze and my knees tremble. I saw time-hungry CUPS-daemons all around me, feeding of my efforts (I only wanted to print a page, and hours and hours of messing inside the belly of my operating system were doomed to my misery...)

Then **metoo** saved my day  --> [here]("http://www.ubuntuforums.org/showthread.php?p=651070#post651070") and with his magic spell my laptop restarted printing again. 

Now, how comes that the permissions of usb lprinters got trashed overnight? Yesterday the damn' thing printed like a charm, and today needs the number of the beast or what the hell read/write or ownership change is it?
Do Linux system degrade themselves spontaneously just like windows ones, or like a piece of cheese left alone in a drawer?

---

### Post by nick_hagen on 2007-01-20
you are an absolute life saver, i thought for sure that my P3150 was useless for ever, I will have to try this once I get home.  Please keep up the good work and know that your efforts have not gone unnoticed.

Nicholas Hagen

---

### Post by TuRiSOft on 2007-03-11
Really , really thank you from southern italy too !!!!
Finally got my P3150 working !!! Is there a way to make the embedded scanner work too ??? Thanks for all your efforts , bye !!!

---

### Post by pjman on 2007-05-07
I installed both files from the link after converting them to deb using alien. z700 is not an option to choose from. What am I doing wrong?

---

### Post by pjman on 2007-05-15
Any ideas?

---

### Post by thedevilisbad on 2007-05-16
> **debernardis said:**
> Owners of this combo printer should be aware of [http://users.cybercity.dk/~dko12479/](http://users.cybercity.dk/~dko12479/) where a working driver can be downloaded.
Just convert rpm packages in deb packages with alien, and don't forget to set inkset as cmy instead of cymk, otherwise you'll get bad printouts.
According to the coder, should work also for Z700, Z705, Z708, P706, Z707.

I'm a beginner so this really confuzzes me. I'm not sure how to use alien.

---

### Post by Pollywoggy on 2007-05-16
> **thedevilisbad said:**
> I'm a beginner so this really confuzzes me. I'm not sure how to use alien.

'sudo alien packagename.rpm' usually does it for me but sometimes I have to use the -c option:
'sudo alien -c packagename.rpm'

You then find the deb in your working directory.  Caution: debs created with alien do not always work.
I made one yesterday and the postinstall and removal scripts came out wrong.  I had to edit the scripts in order to remove the deb.  It helps to install the equivs package for when you can't get a package removed because of a problem in the scripts.

---

