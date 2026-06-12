---
title: "ubuntu 12.04 canon pixma 4200 printer not working"
date: 2012-11-06
forum: Hardware
---

### Post by alaphonse on 2012-11-06
Newbie - Installed ubuntu 12.04. Canon pixma 4200 printer not working.  Drivers installed, printer enabled and recognized by system, simply hangs in Processing - just sits there with green light flashing, Have to unplug to turn off. 
Similar threads not resolved or helpful. 

I need help with THIS printer not some other model of Canon. It works fine in Windows on other laptop so its NOT the printer.

Can anyone answer this question in PLAIN ENGLISH

---

### Post by alaphonse on 2012-11-08
Bump

---

### Post by royph on 2012-11-08
Go to the following site to solve your problem.
[http://www.iheartubuntu.com/2012/02/install-canon-printer-for-ubuntu-linux.html](http://www.iheartubuntu.com/2012/02/install-canon-printer-for-ubuntu-linux.html)

After you install "sudo add~apt~repository ppa.michael~gruz/canon" Change your Software Sources (Update Manager > Settings...) on tab "Other Software"
Edit PPA /michael~gruz/canon/ubuntu main and main (Source Code) Change Distribution from "precise" to "oneiric".
After that you can "sudo apt~get update.

should work fine after that.

---

### Post by BicyclerBoy on 2012-11-08
You don't need to mangle the ppa distro target..there is a new ppa for precise..

[https://launchpad.net/~michael-gruz/+archive/canon-trunk?field.series_filter=precise](https://launchpad.net/~michael-gruz/+archive/canon-trunk?field.series_filter=precise)

Then install cnijfilter-ip4200series package..

---

### Post by royph on 2012-11-09
Sorry, I didn't know the site had been updated.

---

### Post by BicyclerBoy on 2012-11-09
No need to be sorry..no harm done & you're helping someone..

I used the old ppa with precise-->oneiric--> trick for awhile..

---

### Post by alaphonse on 2012-11-17
Many Thanks

Driver appears to be installed, printer recognized and test page prints  but nothing else. It just hangs in Processing. I've tried everything I  can think of of - basics: paper, ink etc. Switching printer off and on  to clear - simply doesn't want to print anything but test page.

Any suggestions? I appreciate your patience.

Alain

> **BicyclerBoy said:**
> You don't need to mangle the ppa distro target..there is a new ppa for precise..

[https://launchpad.net/~michael-gruz/+archive/canon-trunk?field.series_filter=precise](https://launchpad.net/~michael-gruz/+archive/canon-trunk?field.series_filter=precise)

Then install cnijfilter-ip4200series package..

---

### Post by BicyclerBoy on 2012-11-18
Did you add the suggested canon ppa ?

If you had been messing with other drivers etc...I would unplug printer & open "printers" program/dialogue & delete all printers..

Then I would replug printer & turn it on..
Then I would click the add printer icon..

---

### Post by col48 on 2013-05-06
This hasn't been marked as solved, so here is my 2p worth.  As I'm not the OP, I won't mark it solved myself!

I have Precise Pangolin 12.04 64bit v3.2.0-41 and a Canon PIXMA MG4250

The generic drivers found through trying to set up the printer via the system tools did not work and there is nothing specific to the 4200 series.

However, the instructions in the following link did the trick - the site says it works for any printer in the 4200 series, not just the 4250:

[http://robert.penz.name/532/a-howto-for-using-a-canon-pixma-mg4250-under-ubuntu/]("http://robert.penz.name/532/a-howto-for-using-a-canon-pixma-mg4250-under-ubuntu/")

The only correction was that the tar options needed a prefixed -

In case the site disappears, these are the terminal commands shorn of all but minimal commentary:

# Go to these two web addresses and take the downloads - one is for printing and the other for scanning - and yes, these are ASIA sites because the material is not on the European or American sites:
[http://support-asia.canon-asia.com/contents/ASIA/EN/0100470302.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100470302.html)
[http://support-asia.canon-asia.com/contents/ASIA/EN/0100466802.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100466802.html)
# extract the contents of the downloads
tar -xzf cnijfilter-mg4200series-3.80-1-deb.tar.gz
tar -xzf scangearmp-mg4200series-2.00-1-deb.tar.gz
# go to the newly created folders and perform the installation
cd cnijfilter-mg4200series-3.80-1-deb
./install.sh
#  in the course of the installation you will be asked
#        (1) to connect and turn on the printer
#        (2) choose whether it is a USB or network connection (which must be on the same subnet, apparently)
#                mine is network, so it then hunted for the printer and found it on the second attempt (after I'd switched the printer off and back on)
#        (3) whether you want this to be the default printer
# and then (maybe this has to be done after the previous installation)
cd scangearmp-mg4200series-2.00-1-deb
./install.sh
# no questions here

Scanning is then initiated via the terminal command scangearmp and it prompts you to update the scanner list every time (well, it does for me!).
One not very obvious feature is that the scan does not start until the 'scan' button (which is neither right at the top nor right at the bottom) is pressed on the next screen.

---

### Post by Bryant777 on 2013-07-05
> **BicyclerBoy said:**
> You don't need to mangle the ppa distro target..there is a new ppa for precise..

[https://launchpad.net/~michael-gruz/+archive/canon-trunk?field.series_filter=precise](https://launchpad.net/~michael-gruz/+archive/canon-trunk?field.series_filter=precise)

Then install cnijfilter-ip4200series package..

How does a beginner install cnijfilter-ip4200series package?  

Thanks for detailed explanation - I have a Canon Pixma MG3220.  So how do I install package for it?

Thanks again!

---

### Post by pdc on 2013-07-06
Your canon MG3220 is part of the 3200 series that canon make

so go here

[http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG3240.aspx?DLtcmuri=tcm:14-994543&page=1&type=download](http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG3240.aspx?DLtcmuri=tcm:14-994543&page=1&type=download)

and download the [COLOR="#008000"]cnijfilter-mg3200series-3.80-1-deb.tar.gz[/COLOR] 

the commands to install; if you copy and paste them into a termina; use the top line of terminal: File........across to Edit and down to Paste ........

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf cnijfilter-mg3200series-3.80-1-deb.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd cnijfilter-mg3200series-3.80-1-deb[/COLOR]

> [COLOR="#FF0000"]sudo ./install.sh[/COLOR]

.......that should get the printer side working .....................

______________________________________________________

Canon supply ScanGearMP to run the scanner component

go here

[http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG3240.aspx?DLtcmuri=tcm:14-994543&page=1&type=download](http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG3240.aspx?DLtcmuri=tcm:14-994543&page=1&type=download)

and download [COLOR="#008000"]scangearmp-mg3200series-2.00-1-deb.tar.gz[/COLOR]

[COLOR="#EE82EE"]**close and open** the terminal[/COLOR]; then commands are

> [COLOR="#FF0000"]cd Downloads[/COLOR] 

> [COLOR="#FF0000"]tar -zxvf scangearmp-mg3200series-2.00-1-deb.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd scangearmp-mg3200series-2.00-1-deb[/COLOR]

> [COLOR="#FF0000"]sudo ./install.sh[/COLOR]

........that should install scangearmp and to run it, issue the command

> scangearmp

...........to set it up to open from an icon, do as described here

[http://www.codemarvels.com/2012/05/create-shortcut-launcher-on-desktop-on-ubuntu-12-04/](http://www.codemarvels.com/2012/05/create-shortcut-launcher-on-desktop-on-ubuntu-12-04/)

> [COLOR="#FF0000"]sudo apt-get install gnome-panel[/COLOR]

and 

> [COLOR="#FF0000"]gnome-desktop-item-edit ~/Desktop/ --create-new[/COLOR]

and command must [COLOR="#FF0000"]scangearmp[/COLOR] ...............

---

