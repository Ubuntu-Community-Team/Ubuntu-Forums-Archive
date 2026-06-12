---
title: "How to install Canon Pixma MX 522 Multifunction? (Ubuntu 12.04 Precise)"
date: 2014-01-22
forum: Hardware
---

### Post by Wadcutter on 2014-01-22
Been chasing my tail in circles trying to find drivers that will make a brand-new Canon Pixma MX522 multifunction unit print and scan on my wife's 12.04 system. We have Win7 installed inside Oracle's Virtual Box and the printer works on that system. But she uses Ubuntu 95% of the time and would prefer the printer work therein and not have to boot up Windows any time she wants to print something. It's a 4 or five year old Dell workstation with Intel Xeon E5335 chip. Other than not finding drivers for the printer, Precise has been working 100%.

I've tried to load some drivers from an Australian Canon site but can't because of missing dependencies. Also tried some advice from an old tutorial post here on these forums, but the info was 6 years old and the suggested software also was defunct.

I'm about one step beyond newbiehood, so might need some detailed advice if any advice is available. My own computer installed an old HP 1210xi printer in about 20 second flat with no problems whatsoever, so I wasn't prepared for the nighmare it has become with my wife's shiny new ink-drinker.

---

### Post by Wadcutter on 2014-02-16
UPDATE: My error entirely for buying a Canon based upon every other consideration than the availability of Linux drivers. So we now have to consider Plan B, C or D. 

Plan B: I would appreciate any opinions about a CURRENTLY available for sale alternative make/model/brand multifunction that plays well with Ubuntu 12.04 based upon experience. It should print photos well, too. If I can find one, I'll donate this monster to my vol fire dept which needs a new multifunction unit and runs entirely on Windows.
Plan C: Turboprint for $41.05. Anyone have any experience here?
Plan D: Whatever happened to the paperless office? Why am I letting a printer keep me awake and ruin my digestion? My wife can print her photos under Windows or send them to Costco.

---

### Post by aikishugyo on 2014-02-16
I recommend to use gutenpprint, 5.2.10 pre-release now available from the website. See thread on MG2520 on how to install:
[http://ubuntuforums.org/showthread.php?t=2204685&page=2](http://ubuntuforums.org/showthread.php?t=2204685&page=2)
Although your time also seems quite limited, please help with testing, the only way open-source drivers will improve.

---

### Post by Wadcutter on 2014-02-17
Thank you. I looked at the thread but about 85% of the terminology is beyond my comprehension. I may be able to figure it out by breaking down into small pieces and taking one careful step at a time, but it isn't going to be a fast process.  Plan B or C may actually be a more cost-effective use of my time vs money. I'm happy to help others in any way I can, but my limited knowledge of how Ubuntu works will more likely make me a taker of the time/energy of others rather than a giver.

---

### Post by jason68 on 2014-03-05
> **aikishugyo said:**
> I recommend to use gutenpprint, 5.2.10 pre-release now available from the website. See thread on MG2520 on how to install:
[http://ubuntuforums.org/showthread.php?t=2204685&page=2](http://ubuntuforums.org/showthread.php?t=2204685&page=2)
Although your time also seems quite limited, please help with testing, the only way open-source drivers will improve.

I just bought the MX522 and it was a breeze:

1) Download this printer driver [http://gdlp01.c-wss.com/gds/5/0100005155/01/cnijfilter-mx520series-3.90-1-deb.tar.gz](http://gdlp01.c-wss.com/gds/5/0100005155/01/cnijfilter-mx520series-3.90-1-deb.tar.gz)
2) Download this scangear program [http://gdlp01.c-wss.com/gds/4/0100005184/01/scangearmp-source-2.10-1.tar.gz](http://gdlp01.c-wss.com/gds/4/0100005184/01/scangearmp-source-2.10-1.tar.gz)
3) Extract scangear to folder:  **$ tar -zxvf scangearmp-mx520series-2.10-1-deb.tar.gz**/
4)Open folder**: cd  scangearmp-mx520series-2.10-1-deb.tar.gz**/
5) Install:  **./install.sh** #scangearmp to start program when connected via USB
6) Extract to mx520 series driver to  folder:  **$ tar -zxvf cnijfilter-mx520series-3.90-1-deb/**
7) Open folder: **cd** ** [B]cnijfilter-mx520series-3.90-1-deb/**[/B]
8) Install: **./install.sh**
9) *Follow the setup instructions

So far I'm happy with everything about this printer.

---

### Post by Wadcutter on 2014-03-09
Thanks for the info, Jason68. There are a lot of gaps in my knowledge of Ubuntu such as:
1) What folder would I extract the scanning program to? An existing one named ?????? or a new one that I create and name whatever I want.
2) Where would this folder go? Under "Home" or in another folder such as etc or ??
3) Same questions for the printer driver. I'm guessing it needs to be in a different folder from the scan program.
Maybe I'm thinking like a Windows user, but isn't it important that the drivers go in a correct particular place?

I'm not real familiar with terminal commands, but think you may have given me enough that if I know the answers to the above questions, I can manage to extract and install
the scangear and printer driver. If not, I'll be asking more questions. I did give it all a good 3 hour try on my own but have to admit I'm still pretty much a noob and am easily baffled.

---

### Post by pdc on 2014-03-09
Hi wadcutter; can I suggest some commands to copy and paste to help you get the driver from Canon installed?

..........when you paste into a terminal, I suggest using the top line menu of the terminal .........ie using the mouse go from File top left along to Edit and down to Paste .....as Control+V does not work for a terminal......it is Shift+Control+V 

if you go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100515502.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100515502.html)

and click on the download button, you will be downloading [COLOR="#008000"]cnijfilter-mx520series-3.90-1-deb.tar.gz[/COLOR]

the commands to copy and paste into a terminal; (and hit the enter key after each paste) ..would be

> [COLOR="#FF0000"]cd Downloads[/COLOR] ..........because the default should be downloads get downloaded there ............

then 

> [COLOR="#FF0000"]tar -zxvf cnijfilter-mx520series-3.90-1-deb.tar.gz[/COLOR]        and that unpacked the compressed file from Canon and creates a cnijfilter-mx520series-3.90-1-deb directory

then 

> [COLOR="#FF0000"]cd cnijfilter-mx520series-3.90-1-deb[/COLOR]

then 

> [COLOR="#FF0000"]sudo ./install.sh[/COLOR] and you will be asked for your sudo password and when you enter that, the install script will run and the printer driver will install, and you should be able to print

if you close the terminal after this; and re-open it when you download ScanGearMP

______________-

ScanGearMP runs the scanner side of things: install the same way

get it from here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100517902.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100517902.html)

commands are

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf scangearmp-mx520series-2.10-1-deb.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd scangearmp-mx520series-2.10-1-deb[/COLOR]

> [COLOR="#FF0000"]sudo ./install.sh[/COLOR]

and that should install ScanGearMP for you

to run it, paste

> [COLOR="#FF0000"]scangearmp[/COLOR]

into a terminal........if it all goes well a launcher will help you launch it in future..........we can give you some how-tos for that

---

### Post by Wadcutter on 2014-03-11
I can't think of the right words to express my gratitude for the help I've received here. A big THANK YOU doesn't seem adequate.

Both the printer and scanner are working great now. That's a 100% improvement because up to 20 minutes ago, we had nothing.

I really appreciate your walking me through it,"pdc". I used to be quite familiar with DOS commands and used them regularly in the old computer days. But in recent years I've used a lot of graphical interfaces and had forgotten exactly how to get around with keyboard commands. I was making the task more difficult than it needed to be. Once I got into it, it all made sense and I didn't need to over-think it. Instead of closing the terminal and starting over to install the scangear, I just hit [cd ..] without thinking and was back to Downloads where I needed to be. Using terminal commands is one thing, but knowing what they are is something else. I need to educate myself.

Since this is all for my wife's computer, a scan launcher icon would be great for her since she has zero experience with DOS or terminal commands. Or is there some way to activate Simple Scan? I use it regularly on my computer and I love its simplicity. If not, I can help her bring up Scangear. Plugging a one-word command into terminal is not rocket science.

Thank you, again  "pdc" and "jason 68". You guys are lifesavers.

---

### Post by pdc on 2014-03-11
Hi wadcutter; thanks very much for your kind words and delighted to hear it is working well for you; and your wife! 

_________

[COLOR="#008000"]*I just hit [cd ..] without thinking and was back to Downloads where I needed to be*[/COLOR]

..........great work .........just like a pro!! 

____________________

to set up a launcher

[http://www.codemarvels.com/2012/05/create-shortcut-launcher-on-desktop-on-ubuntu-12-04/](http://www.codemarvels.com/2012/05/create-shortcut-launcher-on-desktop-on-ubuntu-12-04/)

this would suggest the commands

> [COLOR="#FF0000"]sudo apt-get install gnome-panel[/COLOR]

and then 

> [COLOR="#FF0000"]gnome-desktop-item-edit ~/Desktop/ --create-new[/COLOR]

that opens an application box that you complete ......

the command that you fill in; in the box that comes up when you do the above; needs to be > [COLOR="#0000FF"]scangearmp[/COLOR] but you can call the application it what you want, and you can choose the icon from the offered list; or link the launcher to one of your choosing.............eg for one of ours I used a JPEG from our photo file

__________________-

Neither SimpleScan nor Xsane will work; but scangearmp seems to work fine for us on our MG3100 series

best wishes

__________

PS "[COLOR="#008000"]Plugging a one-word command into terminal is not rocket science[/COLOR]."

but also

....check on the terminal on your wife's computer ...........if she does not use the terminal ........pressing the up arrow will likely bring back the last command....so opening a terminal...pressing the up arrow....and bringing up the command scangearmp ...hitting the ENTER key should active scangearmp

---

