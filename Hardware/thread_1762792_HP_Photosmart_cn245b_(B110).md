---
title: "HP Photosmart cn245b (B110)"
date: 2011-05-19
forum: Hardware
---

### Post by Matt__ on 2011-05-19
Purchased [two of these wireless printers]("http://www.amazon.com/HP-Photosmart-Wireless-CN731A-B1H/dp/B003JME93K/ref=sr_1_1?ie=UTF8&qid=1308210699&sr=8-1") for use on Ubuntu, Mint and Win7 ([UK Amazon listing]("http://www.amazon.co.uk/s/ref=nb_sb_noss?url=search-alias%3Daps&field-keywords=HP+Photosmart+cn245b+%28B110%29&x=0&y=0"))

I was expecting some difficulty getting 100% functionality with Linux but imagined it would work eventually. 

The actual outcome was that using HPLIP via apt-get to get the latest version (terminal commands below) the Linux machines were up and running in under 5 minutes..100% scan/print/wireless.
Setting up the printer itself using the colour screen took a few minutes, it detected my wireless and accepted the wpa key and auto allocated itself an IP (can be changed from preferences menu).
Both simple scan and xsane find the scanner instantly (installed on mint Julia, Ubuntu 10.4 and 10.10[COLOR=Blue] (//edit: works in 11.04 ubuntu too, see post No#8  )[/COLOR]).

```
sudo add-apt-repository ppa:hplip-isv/ppa 
sudo apt-get update
sudo apt-get install hplip
```+ install GUI toolbox from software center and add printer..

Windows took considerably longer (win7 home premium & ultimate), over an hour on home premium with the install software very slow and crashing several times..requiring removal and reinstall, ultimate was ok. It also had several of what I consider "trash" applications to tweak photos/purchase HP items/solution centre, though I'm sure someone will make use of them (but NOT on my network). 

Print quality seems first class in both windows and Linux from the few tests I've run, scan is a little slow at higher DPI on both Linux and windows, but very good quality. 
It also has a print by mail function so you can email a doc or picture directly to the printer from anywhere which works quickly and faultlessly.
Settings can be changed with the printers own screen, hp toolbox and via web page. 

This printer has been said by others to be very noisy too...I don't agree with this, it is no worse than many I've owned of various makes. 

Ink seems quite cheap at [£22.74 for a full set on amazon.]("http://www.amazon.co.uk/gp/product/B0039NY19G/ref=ox_sc_act_title_1?ie=UTF8&m=A1B90OV4PZ8ZAU")

A final word..this is a large printer as the scanner is flat across the top, and even larger once you open the front paper tray.

---

### Post by hollowhead on 2011-06-25
I found your post and bought this printer.  Everything works apart from head cleaning.  This is rather vital and I doubt if John Lewis will give me my money back on the basis that I am using an unsupported operating system.  Although ink levels don't work either they are reported on the printers screen, is there any way to clean print heads using the printer control panel?

---

### Post by hollowhead on 2011-06-25
Sorry I found the instructions online, the ones that came with the printer are very basic to put it mildly.  I can clean the printheads using the printer itself.  But my first question still stands can you do it from ubuntu?

---

### Post by nomko on 2011-06-25
I've got the HP ePhotosmart Ba and the only thing i did to get it worked properly was updating the HPLIP driver. Just download it from this site: [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html) and install the driver. It's very easy to do!

---

### Post by hollowhead on 2011-06-25
I did as you suggested and removed the repository above but now the clean and print test page buttons are greyed out....  Thanks its liveable with.

---

### Post by createdcreature on 2011-06-25
I have had 0 problems with this printer. I downloaded HPLIP from the official website as a .run script.

---

### Post by nomko on 2011-06-25
What version of Ubuntu you're using now? I'm using 10.04.2 and have no problems at all. Like i said, i downloaded and installed the latest version of HPLIP.

---

### Post by Matt__ on 2011-07-13
The latest kernel update on 11.04 (2.6.38-10) breaks hplip and its toolbox as the printer is supported in cups. It appears from terminal output that there is a conflict due to the python libraries being newer than the ones required for hplip in the ubuntu repo which over rides the ppa?!?! 
Printer is perfectly useable like this, but lacks some functionality afforded by the hp-toolbox.

solution: [Download the auto-installer]("http://hplipopensource.com/hplip-web/install_wizard/index.html") which resolves dependencies/conflicts and restores your toolbox and panel icon if you want it.

Just select your distro/version/printer, download the run file and follow the easy instructions.


and sorry Hollow, didnt see that you had posted here until today. (too many forums and posts in my life lol) and yes you can clean heads from hp-toolbox

---

### Post by nomko on 2011-07-14
> **Matt__ said:**
> solution: [Download the auto-installer]("http://hplipopensource.com/hplip-web/install_wizard/index.html") which resolves dependencies/conflicts and restores your toolbox and panel icon if you want it.

 
Which is the regular HPLIP driver i'm talking about. The HPLIP driver installation should come up with a list of missing dependencies. Normally HPLIP should download them, but in some cases HPLIP can't find the missing dependencies. If this occures, then the only solution is to install them "by hand", meaning looking for the missing packages in synaptic or searching for it on the web (package archive of Ubuntu).

---

### Post by Matt__ on 2011-07-16
nomko
The errors I received where due to python being of a newer version than HPLIP was looking for, even removing and purging HPLIP and reinstall didnt resolve it.
The Older depends would also not install without removing the newer version, unless I wanted the trouble of creating a second install of python libraries and messing around with file paths.
so HPLIP .run was by far the easiest solution.

Perhaps it was my constant tinkering and modifications (I had maverick repos via PPA for hplip as there was nothing in the natty repo for HPLIP when 11.04 was released).
anyway, as long as it all works, and is easy to do, what matters the method :)

---

### Post by grey1beard on 2012-10-08
Hi Matt,
Following your #8 post I'm attempting the installation of the latest hplip(3.12.10) and have got as far as restarting, then running hp-setup again as per their instructions.
However, the Step 2 of 5 page is not responding. 
I've tried selecting the printer in the window, and hitting Next, but nothing happens.
I brought the terminal window to the front and found the last line reading **"ValueError: need more than 1 value to unpack"**

I cancelled everything and tried again, with the usb unplugged, checked the printer was on, then plugged in when requested, but it made no difference. It still froze at the same point.

Any help greatly appreciated.

John

HP Photosmart B110 into Toshiba Satellite, 11.04

---

### Post by grey1beard on 2012-10-08
Added the printer as a usb printer, and that worked ok.
tried to print with the wireless installed printer, but not surprisingly, as it had not installed properly, it didn't work.
Deleted all printers and started again, but it stalled at the same step, with the terminal window and the gui window at the same as before.

---

