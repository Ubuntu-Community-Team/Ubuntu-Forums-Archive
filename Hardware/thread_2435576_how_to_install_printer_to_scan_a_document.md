---
title: "how to install printer to scan a document?"
date: 2020-01-22
forum: Hardware
---

### Post by jamesjosephblack on 2020-01-22
01.22.2020

 
 
 Hi,

 
 
 I recently installed ubuntu 16.04  – side by side with windows xp  and  upgraded to  18.04 (bionic beaver) 


 I would like to use my 4 in 1 printer (HP laserjet M1212nf  MFP)  to scan a document into the ubuntu system.

 
 
  The install CD that came with the printer is for windows & apple.

 
 
 Any suggestions how to do it?

---

### Post by CelticWarrior on 2020-01-22
HP printers work with hplip, usually installed by default. If not, just install it using Software Ubuntu. Also install Xsane for the scanner part.
No other drivers are required. The CD is useless now, even for Windows, you can trow it away. If you need drivers for Windows you can download updated ones from HP.

Off-topic (but extremely important): Windows XP has been out of support since 2014. That almost 6 years without security updates. You definitely don't want that OS around or, at the very least, NEVER use it connected to the internet. Other Windows versions already out of support: Vista and Seven. Do NOT use any Windows older the Windows 8.

---

### Post by jamesjosephblack on 2020-01-22
thanks - i'll google 'software ubuntu' and look for a printer driver there.

---

### Post by tea for one on 2020-01-22
> **CelticWarrior said:**
> HP printers work with hplip, usually installed by default. If not, just install it using Software Ubuntu. Also install Xsane for the scanner part.
No other drivers are required. 

You do not need google right now.

Ensure that your printer is connected to your PC

Settings > Devices > Printers 

Is your printer recognised?

---

### Post by sdsurfer on 2020-01-23
To add to the above, one of the things I **loved** when I first installed Ubuntu was that everything seemed to just ***work.*** No futzing about with drivers or fiddling with driver versions. What I remember most about that is the printer/scanner connections.

If you're connected to the printer and can print, you should be able to scan. Just open the computer search (Ubuntu icon) and type "scan." SimpleScan should come up. It's very basic but does the job.

---

### Post by Autodave on 2020-01-23
*hplip* will need to be installed.  You can probably get this from the Softwear center.  In case you don't see it there, search for and install *synaptic *package manager and then you can find *hplip *there.

---

### Post by jamesjosephblack on 2020-01-23
hi,

my device is recognized and i tried from the dash, "scan, simple scan (ready to scan), Press Scan - and message said, "failed to scan - unable to connect to scanner".

---

### Post by jamesjosephblack on 2020-01-23
hi
i will give this a try.
where is the "software center"?

---

### Post by jamesjosephblack on 2020-01-23
hi,

my device is recognized and i tried from the dash, "scan,  simple scan (ready to scan), Press Scan - and message said, "failed to  scan - unable to connect to scanner".

---

### Post by Autodave on 2020-01-23
*hplip *has to be installed for the scanner to work.

---

### Post by Autodave on 2020-01-23
I just noticed something unrelated to the scanner issue.  You installed Ubuntu on that machine?  How are the specs on that PC?  You may do better by installing a lighter desktop version.

---

### Post by therealdps on 2020-01-25
Hey there, if you're still looking for help, I am here. I work with HP printers in my office, and I have to set this up every time that I reinstall Ubuntu. :). Here is what you are going to want to install, this is the link to download the latest version of ```
hplip
```: [https://developers.hp.com/hp-linux-imaging-and-printing/gethplip](https://developers.hp.com/hp-linux-imaging-and-printing/gethplip)

Go there and select the "select distro's" button, and scroll down and select Ubuntu from the drop down. Then select "download hplip", and wait for it to download.

Once it is finished, open up your file manger, and then go into downloads and right click the "hplip" thing that you just downloaded, go down to the "properties" tab and click it, then slide over to the "permissions" tab and check the box that says "allow to execute" or something like that.

Once you have that done, open a terminal with ```
CTRL+ALT+T
``` and type in ```
cd ~/Downloads
```. Once you're in your downloads directory, via the terminal, type in ```
./hplip-3.19.12.run
```, and then hit enter. Stuff will start to execute, and you will need to pay attention to the terminal and select some options. Read the carefully. After you get through the whole thing, there will be a few different new programs in your programs drawer. One of them is the settings for the printer itself, and a scanner program, and something else ( i cant remember exactly).

Let us know how it goes!

---

### Post by CelticWarrior on 2020-01-27
> **therealdps said:**
> I work with HP printers in my office, and I have to set this up every time that I reinstall Ubuntu.

No, you don't.

HPLIP is already installed. At most you'd need to install 'hplip-gui' as discussed in this very own thread a few posts ago. Nothing else is needed and **it's always recommended to NOT install random stuff from the internet**. The only reason to install a new version directly from HP is if you have a very new HP printer and a very old Ubuntu release which hplip version doesn't support the new HP printer model. Otherwise you're just wasting your time and potentially creating issues in your Ubuntu (the version in the repositories has been tested by the Ubuntu devs, anything from anywhere else obviously was not).

---

### Post by therealdps on 2020-01-27
Not to start an argument but,

Yes, yes I do. "Have" would be the only thing that is up for debate though, as yes, hplip is already installed, but not at its newest version, and also it doesn't come with it's GUI, Xsane, nor a multitude of other dependencies that make it more functional.
When you just stick with the installed version, I cant even change the color settings for my HP OfficeJet Pro 8615. Nor does it give me the option to use the multiplexer (or even detect that it is installed) or "double-sided" printing. I am guessing that it is really just an issue of the one in the repos not coming with certain dependencies or extra stuff that the official one does, because just after installing the official one, I actually have a multitude of extra options in the normal "print" menu's of the various programs in Ubuntu, which I do not have before I install it.

Please, don't try to insinuate that I am in any way shape or form suggesting that someone do something that is of bad practice or shady with your:
> **it's always recommended to NOT install random stuff from the internet**

The link that I posted is straight to the official Hplip website, not some "random" place on the internet.

When you install the official Hplip, from the official Hplip website, you get the most up to date version (and yes, it detects the version of Ubuntu that you are running, it is an interactive installer, and does a great job of setting itself up, the way that it is supposed to).

The whole 
> potentially creating issues in your Ubuntu (the version in the  repositories has been tested by the Ubuntu devs, anything from anywhere  else obviously was not). 		

thing is just invalid at this point. I can vouch for it working exactly the way that it is supposed to, on 7 different machines all running releases between 18.04.3 and 19.10, and all working fine. I can also vouch that it doesn't "conflict" or "create issues" with anything on any of these machines, even ones with development envs setup, with a ton of weird and obscure dependencies installed.

So I am going to stand by what I said, and maybe add to it some: If you want the best experience out of your printer, and if you need things that the "built-in" version of hplip doesn't offer (out of the gate or otherwise), then go ahead and install the official one by HP. If you do not, or donot even have the ability (like your printer doesn't come with the extra features) then I wouldn't worry about it.

---

### Post by slickymaster on 2020-01-27
Thread moved to **Hardware** for a better fit

---

### Post by brian_p on 2020-01-27
> **Autodave said:**
> *hplip *has to be installed for the scanner to work.

Not really, but it would only confuse the OP to explain why the hplip package is not required for scanning. Then again, the information provided by the OP is sparse. Doing ```
scanimage -L
``` is a must and knowing whether it is a USB or network connection wouldn't be out of place.

---

