---
title: "Printer Installations, Canon MX892 &amp;Brother HL-L2380DW"
date: 2015-03-14
forum: Hardware
---

### Post by bonzo2 on 2015-03-14
[SIZE=3]Greetings:

I'm new to Linux and have continued to struggle with printers for several months.  Despite researching it, I don't understand what CUPS is or why I need it.  Do I need it?  My set up is for personal home use. I'd like to connect via wired and wireless methods. 

I have a Canon PIXMA MX892 that will not connect via wifi nor while directly plugged in.  Apparently, Canon does not support Linux/Ubuntu for this model. I tried untrusted ppas without success.  So now I'm throwing in the towel on the MX892 and wish to buy a multi-function (all-in-one) monochrome machine that is compatible with Ubuntu 14.04.  I've looked at some lists on Ubuntu-compatible machines, but they seem obsolete. I remain (embarrassingly) confused about how to select an Ubuntu 14.04-compatible printer and then install it. :oops:

I'm considering purchasing a Brother HL-L2380DW, but frankly, I don't even understand what I'm reading on Brother's site about Linux compatibility[/SIZE][SIZE=4]:  [http://support.brother.com/g/s/id/linux/en/index.html?c=us&lang=en&prod=hll2380dw_us_as&redirect=on](http://support.brother.com/g/s/id/linux/en/index.html?c=us&lang=en&prod=hll2380dw_us_as&redirect=on)[/SIZE].

[SIZE=3]Could someone please tell me if the above-mentioned printer is compatible with Ubuntu (and whether I must use CUPS)?   If it's not compatible, does anyone have a suggestion for a reasonably-priced monochrome multi-function machine?  

Thank You 
(Really. Thanks. I'm so frustrated.:frown:  I just want to stop perennially installing printers and actually use one! ;))



[/SIZE]

---

### Post by gifford on 2015-03-14
The Brother printer you referenced is indeed compatible and yes, you will have to use CUPs. 
Really the easiest and least troublesome way is to follow step by step the instructions Brother
has on the site you linked. If you encounter any problems or have questions, just post back
here as we are glad to help.

---

### Post by JeQhdMD on 2015-03-14
ok bonzo2,

There are MANY printers very compatible with Linux and Ubuntu.   These printers should take an average of maybe 10 minutes to install (but can be done in about 2 minutes if experienced):

Firstly . . . . Any HP Printer that is has been on the market for at least a few months (so the setup is included in the Ubuntu version you've installed).   My HP120 Envy did not really even require installation.   When plugged in using the USB cable (plug in first time/initially before booting up Ubuntu).   Then just use the "add printer" dialog in the Ubuntu Settings Manager (the one with the gear symbol).   Ubuntu will see the printer and lead you through a couple quick steps and setup is done.   No loading of drivers, no loading of CUPS (common unix printing system/server).    Actually (hplip is already installed - or will install when Ubuntu sees the printer).

Secondly . . . . . Almost any EPSON printer that has been on the market for at least a few months . . . . ditto above OR get the drivers from "Open Printing.org".   The Epson "Workforce" printers are especially well supported and fast as heck (although noisy).   The Epson Workforce 645 is my second printer - - - works great, does everything.

Canon and Brother printers are a distant 3rd and 4th regarding ease of install - - more geared at least for intermediate or business users, that may have an admin or IT person to support the linux installations.

Be sure to install "Simple Scan" also for those functions.

PS:   You might be able to get the HP Envy 120 at closeout either online or at a Staples, Office Max or Office Depot for a really good price.   IF available, I highly recommend it although the Workforce Printers are cheaper to print large quantities (having indiv. color ink carts).

---

### Post by bonzo2 on 2015-03-14
Hi Gifford,

Thanks for your feedback! :-)

I realize that I can call brother after purchasing a machine for installation help, but I don't want to purchase a machine that's not very easily compatible with Ubuntu.  

I have looked at the "instructions" on the page I linked below, and they are  inordinately vague (to me, anyway) :-0).  They are simply a series of links to about a dozen drivers with no instructions that I can see on which drivers to install. Am I supposed to install all of them on machine?  Is  that to be expected with Linux distros? Prior to installing drivers, the firmware must be updated but the site provides updates only for other OSs, not Ubuntu.

Am I expecting too much to find an Ubuntu-compatible multi-function laser printer that actually has step-by-step instructions on how to install it?  I'm hoping the fact that I'm not knowledgeable enough to determine whether my distro has "csh or tcsh by default" won't prevent my installing a printer under Ubuntu 14.04.  

Thanks again!


FYI: This is what the instructions look like:

Instruction:

[LIST] 
[*]Printer (CUPS) :    [Driver Install]("http://support.brother.com/g/s/id/linux/en/instruction_prn1.html")  |  [Print Command]("http://support.brother.com/g/s/id/linux/en/instruction_prn2.html")   |  [More Information]("http://support.brother.com/g/s/id/linux/en/instruction_prn5.html")  |  
[*]Printer (LPR) :    [Driver Install]("http://support.brother.com/g/s/id/linux/en/instruction_prn3.html")  |  [Print Command]("http://support.brother.com/g/s/id/linux/en/instruction_prn4.html")   |  [More Information]("http://support.brother.com/g/s/id/linux/en/instruction_prn6.html")  | 
[*]Scanner     :      [Driver Install]("http://support.brother.com/g/s/id/linux/en/instruction_scn1.html")   |  [More Information]("http://support.brother.com/g/s/id/linux/en/instruction_scn2.html")   |    
[*]ADS     :      [ADS Driver Install]("http://support.brother.com/g/s/id/linux/en/instruction_scn1d.html")   | 
[*]Scan-key-tool :      [Tool Install]("http://support.brother.com/g/s/id/linux/en/instruction_scn3.html")   |  [Use scan-key-tool]("http://support.brother.com/g/s/id/linux/en/instruction_scn4.html")   |  [More Information]("http://support.brother.com/g/s/id/linux/en/instruction_scn5.html")   |  
[*]PC-FAX (CUPS) :    	[Driver Install]("http://support.brother.com/g/s/id/linux/en/instruction_pcf1.html")   |  [Use PC-FAX(Command/GUI)]("http://support.brother.com/g/s/id/linux/en/instruction_pcf2.html")   |  [More Information]("http://support.brother.com/g/s/id/linux/en/instruction_pcf5.html")   | 
[*]PC-FAX (LPR) :      [Driver Install]("http://support.brother.com/g/s/id/linux/en/instruction_pcf3.html")   |  [Use PC-FAX(Command)]("http://support.brother.com/g/s/id/linux/en/instruction_pcf4.html")   |  [More Information]("http://support.brother.com/g/s/id/linux/en/instruction_pcf6.html")   |    
[*]FAX-modem :       [Driver Install]("http://support.brother.com/g/s/id/linux/en/instruction_fmd1.html")   |  [Use FAX-modem(Command)]("http://support.brother.com/g/s/id/linux/en/instruction_fmd2.html")   |     
[*]P-touch, QL/TD-Printer (CUPS) :      [Driver Install]("http://support.brother.com/g/s/id/linux/en/instruction_esp1.html")   |  [Use P-touch/QL-Printer]("http://support.brother.com/g/s/id/linux/en/instruction_esp2.html")   |  [More Information]("http://support.brother.com/g/s/id/linux/en/instruction_esp4.html")   |    
[*]P-touch, QL/TD-Printer (LPR) :      [Driver Install]("http://support.brother.com/g/s/id/linux/en/instruction_esp3.html")   |  [More Information]("http://support.brother.com/g/s/id/linux/en/instruction_esp6.html")    | 
[*]PJ-Printer (CUPS) :      [Driver Install]("http://support.brother.com/g/s/id/linux/en/instruction_esp8.html")   | 
[*]PJ-Printer (LPR) :      [Driver Install]("http://support.brother.com/g/s/id/linux/en/instruction_esp7.html")   | 
[*]Get IP information :      [BRAdminLight]("http://support.brother.com/g/s/id/linux/en/instruction_bra1.html")   |  [More Information]("http://support.brother.com/g/s/id/linux/en/instruction_bra2.html")   | 
[/LIST]

[LIST]FAQs & TroubleShooting
 
[*][Printer]("http://support.brother.com/g/s/id/linux/en/faq_prn.html") 
[*][Scanner / ADS / Scan-Key-Tool]("http://support.brother.com/g/s/id/linux/en/faq_scn.html") 
[*][PC-FAX / Fax-modem ]("http://support.brother.com/g/s/id/linux/en/faq_pcf.html") 
[*][P-touch, QL/PJ-Printer]("http://support.brother.com/g/s/id/linux/en/faq_esp.html") 
[/LIST]
  
[LIST]Other Information 
[*][Evaluation information]("http://support.brother.com/g/s/id/linux/en/evaluation.html") 
[/LIST]

Brother Drivers for Linux® distributions 
     [Before the Installation]("http://support.brother.com/g/s/id/linux/en/before.html")
 
    [HR][/HR]

---

### Post by bonzo2 on 2015-03-14
> **JeQhdMD said:**
> ok bonzo2,

There are MANY printers very compatible with Linux and Ubuntu.   These printers should take an average of maybe 10 minutes to install (but can be done in about 2 minutes if experienced):   

What a relief! 

> **JeQhdMD said:**
>  Firstly . . . . Any HP Printer that is has been on the market for at least a few months (so the setup is included in the Ubuntu version you've installed).   My HP120 Envy did not really even require installation.   When plugged in using the USB cable (plug in first time/initially before booting up Ubuntu).   Then just use the "add printer" dialog in the Ubuntu Settings Manager (the one with the gear symbol).   Ubuntu will see the printer and lead you through a couple quick steps and setup is done.   No loading of drivers, no loading of CUPS (common unix printing system/server).    Actually (hplip is already installed - or will install when Ubuntu sees the printer).  

I'm going to look for an HP today.  Could you please tell me: Is CUPS included in every Linux distro and may I simply ignore/uninstall it if I use the "add printer" function in Ubuntu Settings Manager?

> **JeQhdMD said:**
> Canon and Brother printers are a distant 3rd and 4th regarding ease of install - - more geared at least for intermediate or business users, that may have an admin or IT person to support the linux installations.
I can see why they trail HP in popularity.  Brother makes some great MFC machines but not worth the headache for this newby.

> **JeQhdMD said:**
> Be sure to install "Simple Scan" also for those functions.
I do not understand what this means. Please clarify for me. Thanks.

> **JeQhdMD said:**
> PS:   You might be able to get the HP Envy 120 at closeout either online or at a Staples, Office Max or Office Depot for a really good price.   IF available, I highly recommend it although the Workforce Printers are cheaper to print large quantities (having indiv. color ink carts).  Just looked at the HP Envy 120. Good looking machine, for sure.

Thanks!  I'm less crabby now. ;)

---

### Post by bonzo2 on 2015-03-14
[SIZE=3]Hi Again JeQhdMD,

I'm looking at theHP LaserJet Pro MFP M127fw, which was reveiwed by PCMag in July of 2014.  I don't know when it went on the market. May I assume that Ubuntu 14.04 LTS includes the necessary software/drivers for this machine? Is there somewhere within Ubuntu 14.04 LTS where I could look to ensure the presence of the software/drivers for that printer and others I'm considering?

Thanks again,
Bonzo2
[/SIZE]

---

### Post by Vladlenin5000 on 2015-03-14
Most if not all HP printers are supported via HP drivers already present or easily installed (HPLIP).

---

### Post by bonzo2 on 2015-03-14
[SIZE=3][FONT=arial]Hi Vladlenin5000,

Thanks Vlad.  You and JeQhdMD are certainly correct about HP printers.  I was looking for definitive confirmation on specific models, and this link provides it, in case anyone is else is interested:

[http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html)[/FONT]

Appreciate your feedback,
Bonzo2[/SIZE]

---

### Post by pdc on 2015-03-15
Canon provide linux drivers for this, and all the inkjet printers they now supply;

to get a printer working, one usually needs three steps

1) establish a connection
2) install the drivers
3) register the printer (register the ppd with the print spooler)

1) Canon UK provide an excellent reference file [http://www.canon.co.uk/support/consumer_products/pixma_printer_wireless_connection_setup/](http://www.canon.co.uk/support/consumer_products/pixma_printer_wireless_connection_setup/) on how to connect wirelessly and this is the link for the MX890series device [http://www.canon.co.uk/support/consumer_products/pixma_printer_wireless_connection_setup/](http://www.canon.co.uk/support/consumer_products/pixma_printer_wireless_connection_setup/)

2) Canon provide linux drivers in 3 separate packages:[COLOR="#EE82EE"] rpm[/COLOR], [COLOR="#B22222"]debian[/COLOR] and [COLOR="#FF0000"]source code[/COLOR]; each of this is issued as 32bit and 64bit; 
3) using the Canon install script that they provide, the script does part 3) and registers the printer with lpadmin ...........so all done for one automatically............ 
____________

how to do steps 2) and 3) ??

go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100412202.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100412202.html) and click to download and save [COLOR="#008000"]cnijfilter-mx890series-3.70-1-deb.tar.gz [/COLOR]

__________

Ubuntu removed [COLOR="#0000FF"]libtiff4[/COLOR] that the MX890 needs so go here [ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/](ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/) and go either 14 or 17 down the list and choose either the 64bit or 32bit variant; as one needs;click to download and left software manager install 

_____

OK: back to getting the drivers installed

Open a terminal and please paste in these commands; please ask for help if needed for how to do this

```
cd Downloads
```

```
tar -zxvf cnijfilter-mx890series-3.70-1-deb.tar.gz
```

```
cd cnijfilter-mx890series-3.70-1-deb
```

```
./install.sh
```

that last command will ask for the user's sudo password; and will run the install script

________

for the scanner, Canon provide [COLOR="#0000FF"]ScanGearMP[/COLOR] from here; [http://support-asia.canon-asia.com/contents/ASIA/EN/0100413402.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100413402.html) it comes down and installs in the format above; crucially, it is first run by typing ```
scangearmp
``` and then setting up a launcher

[COLOR="#0000FF"]ScanGearMP[/COLOR] is DIFFERENT from Xsane and Simple Scan.................... as in ..........the keys of a Honda don't work for a Toyota .........

---

### Post by bonzo2 on 2015-03-15
Hi pdc,

I do not have time today to attempt what you've outlined, but I wanted to acknowledge your post and thank you for your time in writing great step-by-step instructions.  Combined with your link to "foreign" Canon sites, your instructions have already been more fruitful than my conversation with Canon was. I would be thrilled to have my PIXMA MX892 running under Ubuntu. Your instructions look to be above my skill level, but as you've been  kind enough to write them out, I shall try them and report back. :-) 

IIRC, I did go to the European and Asian Canon sites months ago in search of Linux drivers as my research had revealed that Linux drivers were better supported in those areas. Access to me was blocked, perhaps due to geographic location. I can't remember the reason. (FYI: Previously, I did have success installing the MX892 under a different OS using the instructions to which you linked.)  

As I stated above, I was looking for a newby-friendly install.  I do not doubt that it's possible, especially given great instructions, to install Canon under Ubuntu, but as stated by JeQhdMD upthread, Canons may be more of an advanced undertaking than other more Linux-friendly brands.Having spoken with other MX892 owners, this has been my impression. I had brief success with one of the available untrusted Canon ppas, but it broke. As a newby, I cannot say why such repositories exist, but it seems that they must be created of necessity, yes?

Cheers to you, pdc! 
Bonzo

---

### Post by pdc on 2015-03-15
thanks; we wait to hear back when you do the steps and get it all done:

it should really be easy: copy and paste: 

1) open a terminal by holding the control and alt and t keys all at once ......... practice it a few times ......... open .........close .......

2) paste into the terminal is again 3 keys: shift and control and v ............again practice it a few times ............. it is when you hit the ENTER key the action is carried out .......I think you will be pleasantly surprised how easy it is .....................

---

### Post by bonzo2 on 2015-03-15
Hi pdc,):P

I was excited to try your instructions so I started attempting the install today.  I have some questions I hope you'll answer: 

QUESTIONS:

1. I set up wireless printing first.  Which steps do I repeat to also set myself up for wired (DSL or USB) printing? 

2. When I got the the "scangearmp" command, nothing happened.  I can see the file scangearamp-mx890series-1.90-1.deb.tar.gz in my downloads.  I  selected scan on the printer screen, but nothing popped up on my computer screen (as it used to under another OS).

This is great progress.  Thanks so much :-)


**Here is the terminal output:**

                        bonzo@2:~$ cd Downloads 
 bonzo@2:~/Downloads$ tar -zxvf cnijfilter-mx890series-3.70-1-deb.tar.gz 
 cnijfilter-mx890series-3.70-1-deb/ 
 cnijfilter-mx890series-3.70-1-deb/packages/ 
 cnijfilter-mx890series-3.70-1-deb/packages/cnijfilter-common_3.70-1_i386.deb 
 cnijfilter-mx890series-3.70-1-deb/packages/cnijfilter-mx890series_3.70-1_i386.deb 
 cnijfilter-mx890series-3.70-1-deb/packages/cnijfilter-mx890series_3.70-1_amd64.deb 
 cnijfilter-mx890series-3.70-1-deb/packages/cnijfilter-common_3.70-1_amd64.deb 
 cnijfilter-mx890series-3.70-1-deb/resources/ 
 cnijfilter-mx890series-3.70-1-deb/resources/printer_zh_utf8.lc 
 cnijfilter-mx890series-3.70-1-deb/resources/printer_ja_utf8.lc 
 cnijfilter-mx890series-3.70-1-deb/resources/printer_fr_utf8.lc 
 cnijfilter-mx890series-3.70-1-deb/install.sh 
 bonzo@2:~/Downloads$ cd cnijfilter-mx890series-3.70-1-deb 
 bonzo@2:~/Downloads/cnijfilter-mx890series-3.70-1-deb$ ./install.sh 
 [sudo] password for bonzo: 
 ================================================== 
  
 Canon Inkjet Printer Driver 
 Version 3.70 
 Copyright CANON INC. 2001-2012 
 All Rights Reserved. 
  
 ================================================== 
 Command executed = sudo dpkg -iG ./packages/cnijfilter-common_3.70-1_amd64.deb 
 dpkg: will not downgrade cnijfilter-common from 3.90-76~ubuntu14.04.1 to 3.70-1, skipping 
 Command executed = sudo dpkg -iG ./packages/cnijfilter-mx890series_3.70-1_amd64.deb 
 dpkg: will not downgrade cnijfilter-mx890series from 3.90-76~ubuntu14.04.1 to 3.70-1, skipping 
 status: Unknown job: cups 
 /sbin/ldconfig.real: Can't create temporary cache file /etc/ld.so.cache~: Permission denied 
  
 #=========================================================# 
 #  Register Printer 
 #=========================================================# 
 Next, register the printer to the computer. 
 Connect the printer, and then turn on the power. 
 To use the printer on the network, connect the printer to the network. 
 When the printer is ready, press the Enter key. 
 > 
 #=========================================================# 
 #  Connection Method 
 #=========================================================# 
  1) USB 
  2) Network 
 Select the connection method.[1]2 
  
 Searching for printers... 
  
  
 #=========================================================# 
 #  Select Printer 
 #=========================================================# 
 Select the printer. 
 If the printer you want to use is not listed, select Update  
 [0] to search again. 
 To cancel the process, enter [Q]. 
 ----------------------------------------------------------- 
  0) Update 
 ----------------------------------------------------------- 
 Target printers detected (MAC address  IP address) 
 1) Canon MX890 series (xx-xx-xx-xx-xx-xx xx.x.x.xxx) 
 ----------------------------------------------------------- 
 Currently selected:[1] Canon MX890 series (xx-xx-xx-xx-xx-xx xx.x.x.xxx) 
 Enter the value. [1]1 
  
 #=========================================================# 
 #  Register Printer 
 #=========================================================# 
 Enter the printer name.[MX890LAN]MX890-wifi 
 Command executed = sudo /usr/sbin/lpadmin -p MX890-wifi -m  
 canonmx890.ppd -v cnijnet:/xx-xx-xx-xx-xx-xx xx.x.x.xxx 
  
 #=========================================================# 
 #  Set as Default Printer 
 #=========================================================# 
 Do you want to set this printer as the default printer? 
 Enter [y] for Yes or [n] for No.[y]n 
  
 #=========================================================# 
 Installation has been completed. 
 Printer Name : MX890-wifi 
 Select this printer name for printing. 
 #=========================================================# 
 bonzo@2:~/Downloads/cnijfilter-mx890series-3.70-1-deb$ scangearmp 
 scangearmp 
  


Thanks,
Bonzo2

---

### Post by pdc on 2015-03-15
You are doing real well there 

> I set up wireless printing first. ...........and I am assuming your printer prints out what you want !! ??

________________

> Which steps do I repeat to also set myself up for wired (DSL or USB) printing?  ........ **you need to spell out to me what you envisage doing** ........... most folks would be happy that the MX890 works wirelessly ............ 

________________

> When I got the the "scangearmp" command, nothing happened. I can see the file scangearamp-mx890series-1.90-1.deb.tar.gz in my downloads.

One needs to install it as you did the printer: so open a terminal ........by the way very well done at your copy and paste before .........the terminal commands are

```
cd Downloads
```

```
tar -zxvf scangearamp-mx890series-1.90-1.deb.tar.gz
```

```
cd scangearamp-mx890series-1.90-1.deb
```

```
./install.sh
```

.........that should do the install ..........

.............to run it ............... ```
scangearmp
``` ........and if all good, one sets up a launcher 

___________

If we see if scangearmp runs ok for you and I can give you some commands for a launcher?

---

### Post by bonzo2 on 2015-03-16
Hi again, pdc! 

My wireless print jobs look marvelous! You are a fabulous teacher. Yay! \\:D/

Also, I got my scanner to work, but there are GLib-CRITICAL errors in the terminal, which I've pasted below. If you're still willing to assist me, I'd love to learn how to make a launcher for the scanner if we can resolve the errors first.  I tried creating a launcher myself but had no success.  

Finally, are we able to also set up wired printing with the MX890? Of course I am thrilled that you have helped me get this far already and am very appreciate of your guidance.:biggrin:

THANKS!
Bonzo2

                        bonzo@2:~$ scangearmp 
  
 (scangearmp:17532): GLib-CRITICAL **: Source ID 4294967168 was not found when attempting to remove it 
  
 (scangearmp:17532): GLib-CRITICAL **: Source ID 570 was not found when attempting to remove it 
  
 (scangearmp:17532): GLib-CRITICAL **: Source ID 601 was not found when attempting to remove it 
  
 (scangearmp:17532): GLib-CRITICAL **: Source ID 606 was not found when attempting to remove it 
  
 (scangearmp:17532): GLib-CRITICAL **: Source ID 1119 was not found when attempting to remove it 
  
 (scangearmp:17532): GLib-CRITICAL **: Source ID 1212 was not found when attempting to remove it 
  
 (scangearmp:17532): GLib-CRITICAL **: Source ID 1427 was not found when attempting to remove it 
  
 (scangearmp:17532): GLib-CRITICAL **: Source ID 1658 was not found when attempting to remove it 
  
 (scangearmp:17532): GLib-CRITICAL **: Source ID 1686 was not found when attempting to remove it 
  
 (scangearmp:17532): GLib-CRITICAL **: Source ID 1839 was not found when attempting to remove it 
  
 (scangearmp:17532): GLib-CRITICAL **: Source ID 2107 was not found when attempting to remove it 
  
 (scangearmp:17532): GLib-CRITICAL **: Source ID 2344 was not found when attempting to remove it 
 
 bonzo@2:~$ (scangearmp:17532): GLib-CRITICAL **: Source ID 4294967168 was not found when attempting to remove it 
 bash: syntax error near unexpected token `:' 
 bonzo@2:~$  
 bonzo@2:~$ (scangearmp:17532): GLib-CRITICAL **: Source ID 570 was not found when attempting to remove it 
 bash: syntax error near unexpected token `:' 
 bonzo@2:~$  
 bonzo@2:~$ (scangearmp:17532): GLib-CRITICAL **: Source ID 601 was not found when attempting to remove it 
 bash: syntax error near unexpected token `:' 
 bonzo@2:~$  
 bonzo@2:~$ (scangearmp:17532): GLib-CRITICAL **: Source ID 606 was not found when attempting to remove it 
 bash: syntax error near unexpected token `:' 
 bonzo@2:~$  
 bonzo@2:~$ (scangearmp:17532): GLib-CRITICAL **: Source ID 1119 was not found when attempting to remove it 
 bash: syntax error near unexpected token `:' 
 bonzo@2:~$  
 bonzo@2:~$ (scangearmp:17532): GLib-CRITICAL **: Source ID 1212 was not found when attempting to remove it 
 bash: syntax error near unexpected token `:' 
 bonzo@2:~$  
 bonzo@2:~$ (scangearmp:17532): GLib-CRITICAL **: Source ID 1427 was not found when attempting to remove it 
 bash: syntax error near unexpected token `:' 
 bonzo@2:~$  
 bonzo@2:~$ (scangearmp:17532): GLib-CRITICAL **: Source ID 1658 was not found when attempting to remove it 
 bash: syntax error near unexpected token `:' 
 bonzo@2:~$  
 bonzo@2:~$ (scangearmp:17532): GLib-CRITICAL **: Source ID 1686 was not found when attempting to remove it 
 bash: syntax error near unexpected token `:' 
 bonzo@2:~$  
 bonzo@2:~$ (scangearmp:17532): GLib-CRITICAL **: Source ID 1839 was not found when attempting to remove it 
 bash: syntax error near unexpected token `:' 
 bonzo@2:~$  
 bonzo@2:~$ (scangearmp:17532): GLib-CRITICAL **: Source ID 2107 was not found when attempting to remove it 
 bash: syntax error near unexpected token `:' 
 bonzo@2:~$  
 bonzo@2:~$ (scangearmp:17532): GLib-CRITICAL **: Source ID 2344 was not found when attempting to remove it 
 bash: syntax error near unexpected token `:'

---

### Post by pdc on 2015-03-16
thanks; glad it is all going well

> GLib-CRITICAL **: Source ID 1839 was not found when attempting to remove it

[http://stackoverflow.com/questions/23199699/glib-critical-source-id-xxx-was-not-found-when-attempting-to-remove-it](http://stackoverflow.com/questions/23199699/glib-critical-source-id-xxx-was-not-found-when-attempting-to-remove-it)

my first foray into google suggests this is > It's actually just a warning that g_source_remove() was called to disconnect a certain event handler that was already disconnected, in this case, in code that is part of gtk.

____________________

launcher [http://www.codemarvels.com/2012/05/create-shortcut-launcher-on-desktop-on-ubuntu-12-04/](http://www.codemarvels.com/2012/05/create-shortcut-launcher-on-desktop-on-ubuntu-12-04/)

I always suggest this ```
sudo apt-get install gnome-panel
``` and ```
gnome-desktop-item-edit ~/Desktop/ --create-new
``` and that will open a dialogue box where the command must be ```
scangearmp
``` and the rest can be what you choose

__________

for a wired connection.............I guess you just plug in a cable; and try ```
system-config-printer
``` and when the dialog box opens click on the ADD button and click the URI and network areas to activate the search function of this box: it should find a wired MX890 and if you give it a name that makes it clear it is wired ............ I think you can call it anything ....... it is between you and your computer ............

---

### Post by bonzo2 on 2015-03-17
Hi there, pdc :-)

I'm printing wirelessly without issue. Still happy about that. ;) 

I'm stuck on the scanner launcher.  If you're still inclined to help, there are a few questions below.  Either way,[COLOR=#ff0000][/COLOR]**[COLOR=#ff0000] I really appreciate your time. [/COLOR]**

 
**TERMINAL VIA COPY-AND-PASTE:**

sudo apt-get install gnome-panel
gnome-desktop-item-edit ~/Desktop/ --create-new

**DIALOG BOX **

TYPE: application (this was filled out for me)
NAME: scangearmp (I entered via copy-and-paste)
COMMAND: I entered various combinations of CTRL+ALT+____.  I also also tried "scangear" and "scan," but launcher did not seem to accept any of them. 


[LIST=1]
[*]What are the parameters for launch commands?
[*]Was I instead supposed to enter a path to where Ubuntu installed the scanner?  If so, how do I find it?
[*]How can I delete the non-functioning launcher from my desktop?
[/LIST]

Bonzo

---

### Post by pdc on 2015-03-17
Hi Bonzo; the only thing you didn't try for the COMMAND seemed to be ```
scangearmp
``` and that is what one would use in the terminal........so it is the command for the launcher .......

> How can I delete the non-functioning launcher from my desktop? .........what about you right-click on it; select PROPERTIES and change the command to what I quote above; and see if it now works ................

____________

whereas COMMAND must be ```
scangearmp
```, the NAME can be whatever: eg Bonzo's scanner or whatever................

---

### Post by bonzo2 on 2015-03-18
Greetings, pdc: 

Actually, I did try "scangearmp" several times as a command before the launcher became unresponsive.  I just didn't list every command I tried in my last post because I tried a lot.  
 :lolflag:

By the magic of rebooting my PC, the launcher became responsive.  \\:D/

Thank you so much for your patience and time.  This poor printer hasn't had a break all day!!!


Bonzo2

---

### Post by pdc on 2015-03-18
that's great Bonzo; you have climbed a big hill getting all this done: you said you had done months of research but using the Canon install script for both the printer and scanner sides of the MX892 has worked quickly and well; well done; enjoy the printer!!

---

### Post by bonzo2 on 2015-03-18
Thanks again, pdc.  You've made my life easier and now I feel like an Ubuntu Ninja!

---

