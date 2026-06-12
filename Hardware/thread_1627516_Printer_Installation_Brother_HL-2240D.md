---
title: "Printer Installation Brother HL-2240D"
date: 2010-11-21
forum: Hardware
---

### Post by olekoho on 2010-11-21
Does anyone know how to install the printer Brother HL-2240D? In Ubuntu 10.04 it does not come up under the list of printers and searching for the printer did not get any result either. I went through Brother's website instructions, but without success :( Brother;

---

### Post by mrinvader on 2010-11-29
The **2240** and **2240D** are amazing printers that are*** stupid cheap***! A great purchase!

This guide is for Ubuntu 8.04 and later 32bit/ GNOME environment, covering the **HL-2240**. **HL-2240D** is a little different in the printer config dialog after install.

all other models are linked from 

[Brother Drivers for Linux® distributions http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html")

[HL-2240]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2240")

and 

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html")


1) **Set up hardware and connect to power** as outlined in the **quick start guide**... you can leave all CDs and other items in the bag. I found the bag a great place to attach the silica gel dessicant (DO NOT EAT lol!) and the pieces of packing tape.. you'll need em if you move to pack the printer for transport.
 

2)** Get the prerequisites out of the way..**

From [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#002]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#002")
> **_# Pre-required Procedure (2)_**
    Related distributions
    Ubuntu8.04/8.04.1, Ubuntu8.10, Ubuntu9.04
    Related products/drivers
    cupswrapper printer/PC-FAX drivers
    Requirement
    1. "**```
sudo aa-complain cupsd
```**" command is required before the installation.
    2. "**```
sudo mkdir /usr/share/cups/model
```**" command (as it is) is required before the installation.

**_# Pre-required Procedure (3)_**
    Related distributions
    Debian, Ubuntu, openSUSE, Redhat
    Related products/drivers
    Printer drivers for *[a bunch of models]*
    Requirement
    Creating a symbolic link is required before the installation (superuser authorization is required to run the command)

    For Debian based distributions earlier than Ubuntu8.10, Debian5:
    "sudo ln -s /etc/init.d/cupsys /etc/init.d/lpd"

    For Redhat based distributions and [B]Debian base distributions greater than Ubuntu8.10, Debian5:
    "sudo ln -s /etc/init.d/cups /etc/init.d/lpd"[/B] 

**Step 3 above** may be unnecessary but I did it anyway.

3) **Prerequisites *continued...***

from [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#005]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#005")

> 
    Requirement
    csh or tcsh is required to be installed.
Perform **"```
sudo apt-get install tcsh csh
```"**


4) **Plug in USB cable.** printer detection should occur and whine that it cant find a driver..

5) **Go to your model's link**: [2240]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2240") or [2240**D**]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2240")

**Install the** |*LPR driver*| and the |*cupswrapper driver*| in the pertinent  section.. 

NOTE: If you get

```
**lpadmin: The printer or class was not found.**
```

Verify that your printer shows up in ```
**lsusb**
```

**```
Bus 001 Device 021: ID 04f9:0045 Brother Industries, Ltd
```**

**ID** will likely be different

6) **Go to ***System* --> *Administration* --> **Printing**

Verify that a printer has been added referencing the model you have.

verify that the driver is correct.

print a test  page.

**[COLOR="Red"]:guitar: It should now work.:guitar:[/COLOR]**

---

### Post by twiggy_trippit on 2011-03-11
I just followed the steps above to install the drivers for my new Brother HL-2240D, I'm running into an issue. When installing the cupswrapper driver, I get the following message that you mentioned above:

lpadmin: The printer or class was not found.

This happens even though the Brother printer does show up when I run lsusb (and there's no other Brother printer in the house :P ). Apparently, the installation if the driver is not complete: the package installer does not list the package as being already installed afterwards. 

If I go into System > Administration > Printing, no printer is installed. If I click Add, however, the printer shows up, but there's no driver for that model.

Any suggestions?

Thanks,

---

### Post by sloggerkhan on 2011-03-17
I have Ubuntu 10.10 64 bit and I've successfully used this printer with the following drivers:

[LIST]
[*]Generic > PCL 5e Printer > Generic PCL 5e Printer Foomatic/hpijs-pcl5e [en]
[*]Generic > PCL 6/PCL XL Printer > Generic PCL 6/PCL XL Printer Foomatic/hpijs-pcl5e [en]
[*] dpkg --install --force-architecture for both the lpr and then the cupswrapper debs from here: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2240D](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2240D) (printer shows up magically in printer control panel after, no need to add.)
[/LIST]

In general I have no idea if PCL 5 vs PCL 6 makes a difference when the both use hpijs-pcl5e as both seem to result in the same output.

So far as pcl5e vs the brother driver, the quality on both is livable, and darn near identical for black text, but gradients are a bit streakier with the pcl driver than the brother driver.

I didn't seem to need to do the symlinking/mkdir stuff in the provided instructions here.
The brother driver will co-exist with a PCL driver as separate printers on the same system, so it's easy to try both.

---

### Post by puetti004 on 2011-03-27
Hello everybody, 

I managed to get the printer work (Debian unstable amd64 system - not *buntu) following the instructions on Brother's website.

1. purged cups (apt-get remove --purge cups)
2. installed cups (apt-get install cups)
3. checked if ia32-libs and lib32stdc++ were up to date (apt-get install ia32-libs lib32stdc++6)
4. installed lpr driver (forced install) (dpkg -i --force-all hl2240dlpr-2.1.1-1.i386.deb)
   (Download at: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html))
5. installed cups driver (forced install) (dpkg -i --force-all cupswrapperHL2240D-2.0.4-2.i386.deb)
6. checked installation (dpkg  -l  |  grep  Brother)
# ii  cupswrapperhl2240d                         2.0.4-2                              Brother HL2240D CUPS wrapper driver
# ii  hl2240dlpr                                 2.1.1-1                              Brother HL-2240D LPR driver
7. checked cups web interface ([http://localhost:631/printers](http://localhost:631/printers))
# printer was properly installed

Installation only worked after removing (purged) cups.

Best regards, 

puetti

---

### Post by posthuman on 2011-05-08
Hello everybody,

i tried to install the drivers for HL2240D on Kubuntu 10.10, but the step
dpkg -i --force-all cupswrapperHL2240D-2.0.4-2.i386.deb
fails, with the message that libc6 (>= 2.3.4-1 ) is required and the package will remain unconfigured. Libc6 is installed in version 2.13-0ubuntu13 (also libc6-dev, libc6-i386, libc6-i386-dev).
I also tried dpkg with --triggers and --ignore-depends=libc6, but nothing works.

Any ideas?

---

### Post by PurpleFool on 2011-05-31
> **posthuman said:**
> Hello everybody,

i tried to install the drivers for HL2240D on Kubuntu 10.10, but the step
dpkg -i --force-all cupswrapperHL2240D-2.0.4-2.i386.deb
fails, with the message that libc6 (>= 2.3.4-1 ) is required and the package will remain unconfigured. Libc6 is installed in version 2.13-0ubuntu13 (also libc6-dev, libc6-i386, libc6-i386-dev).
I also tried dpkg with --triggers and --ignore-depends=libc6, but nothing works.

Any ideas?

I had a similar problem trying to install on a 64 bit box.  I believe the issue is a packaging one, but I didn't look closely enough to confirm.  While the following will not melt your install, be aware you're being guided by the blind. ;)

In a directory with the .deb package but without a directory called temporary-bodge:

```
ar x cupswrapperHL2240D-2.0.4-2.i386.deb  control.tar.gz
mkdir temporary-bodge
cd temporary-bodge
tar xzf ../control.tar.gz
```

Now edit the file called "control" and remove the line that names the dependency.  Then:

```
tar czf ../control.tar.gz .
cd ..
cp cupswrapperHL2240D-2.0.4-2.i386.deb cupswrapperHL2240D-hack-2.0.4-2.i386.deb
ar r cupswrapperHL2240D-hack-2.0.4-2.i386.deb control.tar.gz
sudo dpkg -i --force-depends-version,architecture cupswrapperHL2240D-hack-2.0.4-2.i386.deb
rm -r temporary-bodge
```

After this I found the printer installed as expected when I fired up a browser and pointed it to the link in Brother's instructions.  I'm glad I did this as it adds a couple of options that are not provided, unsurprisingly, by the generic driver.

---

### Post by oldmankit on 2011-07-13
Awesome.  Thanks so much for this mini-tutorial.  It was helpful for me in deciding whether to buy the printer, and now that I've got it, made setting it-up easy.

---

### Post by neodac on 2011-08-13
Trying to install my Hl-2240 (not the d) on a fresh linux install of Ubuntu 11.4 tried all this and it didnt work it did work on my other install of 11.4 on my laptop.. possibly since its an upgrade started at 9 i think... but it also has the house MFC-9320CW on it it still took me some playing around to get the new printer installed on it but it worked i've been messing with this one for over an hour now.. it says it installs i get no error messages and the print que says everything printed but nothing has apparently gotten through to the printer help please?

---

### Post by pertz on 2011-11-12
> **sloggerkhan said:**
> I have Ubuntu 10.10 64 bit and I've successfully used this printer with the following drivers:

[LIST]
[*]Generic > PCL 5e Printer > Generic PCL 5e Printer Foomatic/hpijs-pcl5e [en]
[*]Generic > PCL 6/PCL XL Printer > Generic PCL 6/PCL XL Printer Foomatic/hpijs-pcl5e [en]
[*] dpkg --install --force-architecture for both the lpr and then the cupswrapper debs from here: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2240D](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2240D) (printer shows up magically in printer control panel after, no need to add.)
[/LIST]

In general I have no idea if PCL 5 vs PCL 6 makes a difference when the both use hpijs-pcl5e as both seem to result in the same output.

So far as pcl5e vs the brother driver, the quality on both is livable, and darn near identical for black text, but gradients are a bit streakier with the pcl driver than the brother driver.

I didn't seem to need to do the symlinking/mkdir stuff in the provided instructions here.
The brother driver will co-exist with a PCL driver as separate printers on the same system, so it's easy to try both.

That was really helpful!

I first used the official 2240D drivers from brother but duplex/two-sided printing didn't work on my ubuntu 11.10. With the generic PCL5e driver you posted it did!

Thanks a lot!

---

### Post by AVStudio on 2011-12-16
I've tried installing based on this thread and all i get now if i try to do any package management is:

E: The package hl2240dlpr:i386 needs to be reinstalled, but I can't find an archive for it.

I'm running a core install of oneiric 64bit with gnome.  I have the x86 libraries and cups.  
How do I purge this stuff and try again?

---

### Post by nikephorous on 2012-02-19
Hi,

I have recently bought one of these printers.

I was initially only able to find and install drivers for the non-duplex model. 

It worked fine.

I have recently located the duplex drivers and installed them. 

Of course now the darned thing will not go. :confused:

I am NOT a technical user - so most of the command variations are completely lost on me. Most of the answers I see posted in forums assume a level of competence far higher than I have.

How do I:

1) Uninstall EVERYTHING to do with this printer to give me a clean slate.
2) Install this beast in PLAIN language - remember I struggle to find Terminal - let alone use it.

The frustration level is high now - so much so I am even considering going back to windows simply because the support level is far higher.

I am currently running 11.10. 

Cheers

John

---

### Post by mörgæs on 2012-02-19
Moved to the hardware forum.

---

### Post by 6541984 on 2013-04-09
I know everyone here is being very helpful, but these interjections and suggestions from everyone is messy!  I'm not a programmer, and I've just wasted 40 minutes on this already running back and forth between the two boxes.  Is there a way we can get these 6 command lines in order and have a firm answer for the rest of us non-programmers?  It's 2013.  This thread was back in 2010?

---

### Post by pdc on 2013-04-09
so you want to install a Brother HL-22240D?

Brother provide an install script; it does the work for you:

[http://ubuntuforums.org/showthread.php?p=12342527#post12342527](http://ubuntuforums.org/showthread.php?p=12342527#post12342527)

if you go to post #5 here, 

mambo describes in great detail I think what he did; and what worked for him;

do let us know how it goes for you

you can subscribe to a thread: top-right; thread tools; that helps you keep in touch if you need continued support

best wishes

---

### Post by Remy_Vanherweghem on 2014-01-17
Since I've struggled for a long time trying everything here and just ending up with a half functioning printer - not printing at all OR printing an infinite amount of blank pages OR, for no apparent reason, working perfectly well for a couple of hours and then spitting all the blank paper in the world - I decided to post here my own solution:

1 - Install the printer as a Brother HL-2170W Foomatic/hpijs-pcl5e
2 - At this point it fails with a missing Filter error; start the terminal and install hpijs (sudo apt-get install hpijs).

That's it. Good luck with yours!

---

### Post by Flix_Rousseau on 2014-02-26
> **puetti004 said:**
> Hello everybody, 

I managed to get the printer work (Debian unstable amd64 system - not *buntu) following the instructions on Brother's website.

1. purged cups (apt-get remove --purge cups)
2. installed cups (apt-get install cups)
3. checked if ia32-libs and lib32stdc++ were up to date (apt-get install ia32-libs lib32stdc++6)
4. installed lpr driver (forced install) (dpkg -i --force-all hl2240dlpr-2.1.1-1.i386.deb)
   (Download at: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html))
5. installed cups driver (forced install) (dpkg -i --force-all cupswrapperHL2240D-2.0.4-2.i386.deb)
6. checked installation (dpkg  -l  |  grep  Brother)
# ii  cupswrapperhl2240d                         2.0.4-2                              Brother HL2240D CUPS wrapper driver
# ii  hl2240dlpr                                 2.1.1-1                              Brother HL-2240D LPR driver
7. checked cups web interface ([http://localhost:631/printers](http://localhost:631/printers))
# printer was properly installed

Installation only worked after removing (purged) cups.

Best regards, 

puetti

That definitely worked ! You are amazing, thank you !!!

---

### Post by Crantag on 2014-05-06
I am using this printer for a while with the following driver from the pre-installed options:

Brother HL-2030 Foomatic/hl1250 (recommended)


Everything seems fine.

---

