---
title: "Ubuntu Studio 14.04 &amp; Epson L300 Printer"
date: 2014-07-02
forum: Hardware
---

### Post by Anggoro_Yudho_N on 2014-07-02
Dear All,

I am an absolute beginner in Linux / Ubuntu Stuio. For the past 20 years, I always use WIndows (85, 2000, XP, 7). A few days ago, I decided to turn into Ubuntu Studio 14.04.
I managed to install the Ubuntu to my laptop. 

However, I'm stuck with printer installation. My printer is Epson L300. 

From Setting -> Printer -> Add -> Epson L300 -> Than there is driver that I need to download from Seiko Epson. I click forward, then I was asked for Password. I give my password.
It then says installing 
*************** 
Installing driver epson-inkjet-printer-201207w
installing
****************
But it stays there for a very long time, without any progress.

I try to restart the laptop, start all over again .... but it doesnt go anywhere only to that stage.

What should I do?

Thank you very much.

Anggoro Yudho N

---

### Post by xc3RnbFO8P on 2014-07-02
Does this help?
[http://ubuntuforums.org/showthread.php?t=2110977]("http://ubuntuforums.org/showthread.php?t=2110977")

---

### Post by pdc on 2014-07-03
Hi Anggoro; welcome to the Ubuntu forums and we hope you will end up enjoying Ubuntu;

so I am not clear what Ringi is pointing you to: s/he is a very experienced poster; [http://ubuntuforums.org/showthread.php?t=2110977](http://ubuntuforums.org/showthread.php?t=2110977) but I am not clear what the message is there; (I am having a slow day);

_________________________

my take on the L300 is to go here ..to the Epson linux download site ... [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) and type in **L300** and I get to here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18787&DSCCHK=cd4ad419e3805cfac26d6492d12e38fc7da11822](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18787&DSCCHK=cd4ad419e3805cfac26d6492d12e38fc7da11822)

the issue there is there are rpm and debian packages; and they come in 32bit and 64bit flavours;

so for a **32bit** system; you need the [COLOR="#008000"]epson-inkjet-printer-201207w_1.0.0-1lsb3.2_i386.deb[/COLOR] and for **64bit** you need [COLOR="#008000"]epson-inkjet-printer-201207w_1.0.0-1lsb3.2_amd64.deb[/COLOR]

_____________

when you click to download the correct one, is Ubuntu Software Center leaping in and offering to install for you?

_____________________________________

if it is holding up on this Software Center area ......................

[http://ubuntuforums.org/showthread.php?t=2222940&highlight=epson](http://ubuntuforums.org/showthread.php?t=2222940&highlight=epson)

this post had a similar problem;

they did > [COLOR="#FF0000"]sudo apt-get install gdebi[/COLOR] and installed using gdebi installer; that will give you an icon to click in your system; called Gdebi Package Installer; 

____________________

so have a look in your Downloads folder: did the correct package arrive there from Epson? If not, click again to download the correct package from Epson; choose to SAVE it when it is downloaded; and then open Gdebi and in its File menu at the left select the open option; and "open" the epson file that should be in your Downloads directory

---

### Post by xc3RnbFO8P on 2014-07-03
>  I am not clear what Ringi is pointing you to: s/he
 don't mind me/he :)

---

### Post by lammergeir on 2014-07-06
Hi Anggoro, welcome to Ubuntu.  I made the change about 8 yrs ago, and really haven't looked back.
My Epson L300 mis-behaved after upgrade to 14.04.  I've just uninstalled and re-installed the software and it prints a perfect test page.
Switch on your printer. Download the file as pdc suggests.( [http://download.ebz.epson.net/dsc/du...2e38fc7da11822](http://download.ebz.epson.net/dsc/du...2e38fc7da11822)).  Extract it to a suitable folder (I made a folder called "printer" and moved the download into that.) Open 201207w_1.0.0-1lsb3.2 folder and you get: DEBIAN and opt.  Open opt, double-click epson-inkjet-printer-201207w.  I get 6 folders. Choose the ppds and open that. Open Epson. You should get a whole bunch of Epson-driver.ppd.gz.  Extract the one for L300. You should get Epson-L300_Series-epson-driver.ppd.
Now in a browser type "localhost:631". Under Administration select "add printer". You'll be asked for your laptop login user name and password. Follow the prompts after selecting your printer. Go to "Or add PPD file" and browse to the ppd file you extracted.
Close your browser, and in Software centre search for Epson L300. Install the Epson Injet Printer Drive (It's a filter file.)
You should be able to print test page from System Settings: Printer.
Hope this helps.  I'm running Ubuntu 14.04 x64, but it should be the same process.

---

