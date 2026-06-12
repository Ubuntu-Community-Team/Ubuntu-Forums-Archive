---
title: "Trying to get my scanner to work (Brother MFC-J4510DW)"
date: 2014-04-07
forum: Hardware
---

### Post by sandino1 on 2014-04-07
Hi, I recently installed Ubuntu 12.04 and I'm trying to get my Brother MFC-J4510DW printer/scanner working on it.

I went to the manufacturer's website and they have a great install program for linux, so everything went fine and the printer is working fine now. I can't figure out how to get the scanner to work though.

Simple Scan just says "failed to scan", although I have my scanner selected in preferences under "scan source".
Xsane says "failed to start scanner: Invalid argument".

I was following advice I found in [this thread]("http://www.linuxquestions.org/questions/linux-hardware-18/brother-mfc-j4510dw-scanner-problem-4175439814/"), so that typing "groups" in terminal now says this:
```
user1 adm lp cdrom sudo dip plugdev scanner lpadmin sambashare
``` 

That fixed it for the OP in the other thread, but nothing's chaged for me.

---

### Post by gifford on 2014-04-07
Did you install the scanner drivers? Is this USB or network connection?
Here is the link for instructions on how to install: [http://support.brother.com/g/s/id/linux/en/instruction_scn1.html?c=us&lang=en&prod=mfcj4510dw_us_eu_as&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_scn1.html?c=us&lang=en&prod=mfcj4510dw_us_eu_as&redirect=on)

---

### Post by kurt18947 on 2014-04-07
Those are good links.  There's one more, though.  The 4th section here
[http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us&lang=en&prod=mfc6490cw_all&redirect=on](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us&lang=en&prod=mfc6490cw_all&redirect=on)
talks about the fix, copying files from /usr/lib64/  to  /usr/lib/.

For anyone new to linux & the command line, spaces upper/lower case and punctuation matter, they must be spot on.  On a previous install, I added the lines in Udev.  I typed them, saved the file, restarted and ....... NO SCANNER.   Huh?  I went back and checked every .... wait, what's this?  I forgot one set of quote marks.  Fixed that, rebooted and away we went.  That's why copy/paste for terminal operations is not a bad idea, particularly for someone whose native language doesn't use the western alphabet.

---

### Post by Stephen_Willmer on 2014-09-29
Ok, imagine the MOST clueless Ubuntu user. There is no simple sentence in these fora he cannot fail to understand. That he installed Ubuntu on a Windows pre-installed machine is little short of a miracle. Have you got that person in your mind's eye?

Hi! 

PLEASE HELP!

I bought an MFC-J4510DW Brother printer/scanner/copier which is in principle perfect for me. As far as I can tell from this forum, it can be got to work with Ubuntu, but I confess that having read the threads dealing with the subject, I am neither better informed nor wiser. 

I bunged the CD-Rom into my computer, it seems to have saved various files to the computer - although not so far as I can see in my downloads folder - but there these files stay, doing nothing but telling me but telling me they cannot be read, or that an error occurred while loading the archive.

Mean anything to anyone?

---

### Post by pdc on 2014-09-29
so Stephen: do you know how to open a terminal? 

(hint: search for it in the dash search function .........)

.............*a few lines down...........I'm going to list some commands for you to paste into a terminal..........to get your printer working* ...................

[COLOR="#EE82EE"]To paste a command into it, use your mouse; and the menu at the top of the terminal: ie start at File (top-left) and move right to Edit and down to paste[/COLOR] ............

________________________________________________

OK

go here [http://support.brother.com/g/b/downloadend.aspx?c=au&lang=en&prod=mfcj4510dw_us_eu_as&os=128&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadend.aspx?c=au&lang=en&prod=mfcj4510dw_us_eu_as&os=128&dlid=dlf006893_000&flang=4&type3=625) and click to download and **SAVE** the [COLOR="#0000FF"]Brother installer tool
[/COLOR]
It should (if you selected SAVE) end up in your Downloads directory: now **copy the commands that are listed below**; and paste them; **line by line**; into the terminal and hit the **ENTER** key after each paste .............

[COLOR="#FF0000"]cd Downloads 
gunzip linux-brprinter-installer-2.0.0-1.gz
sudo bash linux-brprinter-installer-2.0.0-1 MFC-J4510DW[/COLOR]

that should start the installer script; and if the printer is usb-connected the scanner function should work too

---

### Post by Stephen_Willmer on 2014-09-29
pdc, thank you but (and, yes, I really am this ignorant) what is and where do I find the dash search function?

---

### Post by Stephen_Willmer on 2014-09-29
the good news is the Brother installer tool seems now to be in my downloads directory...

---

### Post by Stephen_Willmer on 2014-09-29
Dash search function: the icon at the top left of the screen - a white circle punctuated by three dots and a smaller circle within?

---

### Post by pdc on 2014-09-29
[http://www.linuxuser.co.uk/news/5-problems-with-ubuntu-12-04-part-1-unity-dash-usability-issues/attachment/ubuntu-12-04-open-the-dash](http://www.linuxuser.co.uk/news/5-problems-with-ubuntu-12-04-part-1-unity-dash-usability-issues/attachment/ubuntu-12-04-open-the-dash)

shows the dash .......... then type terminal from inside it .........

_____________________________________

or Keyboard Shortcut: Ctrl + Alt + T 

as here [https://help.ubuntu.com/community/UsingTheTerminal#In_Unity](https://help.ubuntu.com/community/UsingTheTerminal#In_Unity)

_____________________________________

---

### Post by Stephen_Willmer on 2014-09-30
Thanks, pdc ... progress so far is that I've gone to [http://support.brother.com/g/b/downl...ng=4&type3=625]("http://support.brother.com/g/b/downloadend.aspx?c=au&lang=en&prod=mfcj4510dw_us_eu_as&os=128&dlid=dlf006893_000&flang=4&type3=625"), where I clicked "Agree to the EULA & Download". I then saved it when the dialogue box emerged on the screen, and it seems to be in my Downloads folder.

I then opened a terminal by pressing Ctrl+Alt+T (doesn't seem to work when I type it in to the dash search), and copied and pasted the commands you've listed above, pressing ENTER after each line.

The following is the result:

sequipadalianism@sequipadalianism-Aspire-V5-431:~$ cd Downloads
bash: cd: Downloads: No such file or directory
sequipadalianism@sequipadalianism-Aspire-V5-431:~$ gunzip linux-brprinter-installer-2.0.0-1.gz
gzip: linux-brprinter-installer-2.0.0-1.gz: No such file or directory
sequipadalianism@sequipadalianism-Aspire-V5-431:~$ 
sequipadalianism@sequipadalianism-Aspire-V5-431:~$ sudo bash linux-brprinter-installer-2.0.0-1 MFC-J4510DW
[sudo] password for sequipadalianism: 
bash: linux-brprinter-installer-2.0.0-1: No such file or directory
sequipadalianism@sequipadalianism-Aspire-V5-431:~$ 

Nothing else has happened...

---

### Post by pdc on 2014-09-30
OK Stephen

you don't seem to have the directory that is called [COLOR="#0000CD"]Downloads[/COLOR] by default when a standard distro is set up

you did really well to open the terminal; if you do it again and type > [COLOR="#FF0000"]ls[/COLOR]

.........that is asking your system to list what directories you have ......... can you copy and paste back what you get please?

_____________________________________

if you close the terminal; and then re-open it, and type > [COLOR="#FF0000"]cd Desktop[/COLOR] and then > [COLOR="#FF0000"]ls[/COLOR] ...........that is asking your system to list what is on your Desktop .........is the brother installer there?

________________________________________________________________________________

as you are also learning so much Stephen: paste this command into the terminal > [COLOR="#FF0000"]locate linux-brprinter-installer-2.0.0-1.gz[/COLOR]

.....it should be another way of helping  you find out where [COLOR="#008000"]linux-brprinter-installer-2.0.0-1.gz[/COLOR] ended up ...................

---

### Post by Stephen_Willmer on 2014-10-01
Thanks, pdc. This is what I get by typing and entering 'ls':

sequipadalianism@sequipadalianism-Aspire-V5-431:~$ ls
Desktop  Documents  fontconfig  opt  usr
sequipadalianism@sequipadalianism-Aspire-V5-431:~$

When I type and enter 'cd Desktop', then 'ls', I get: 

sequipadalianism@sequipadalianism-Aspire-V5-431:~$ cd Desktop
sequipadalianism@sequipadalianism-Aspire-V5-431:~/Desktop$ ls
sequipadalianism@sequipadalianism-Aspire-V5-431:~/Desktop$ 

And when I type and enter the final command, this is what I get:

sequipadalianism@sequipadalianism-Aspire-V5-431:~$ cd Desktop
sequipadalianism@sequipadalianism-Aspire-V5-431:~/Desktop$ ls
sequipadalianism@sequipadalianism-Aspire-V5-431:~/Desktop$ locate linux-brprinter-installer-2.0.0-1.gz
/home/sequipadalianism/Documents/Practice/Downloads/linux-brprinter-installer-2.0.0-1.gz
sequipadalianism@sequipadalianism-Aspire-V5-431:~/Desktop

---

### Post by pdc on 2014-10-01
well Stephen: I had understood that a default install created a directory called [COLOR="#0000FF"]Downloads[/COLOR] ...... yours interestingly is inside a directory called Practice that is inside your Documents directory !! 

> /home/sequipadalianism/[COLOR="#0000FF"]Documents[/COLOR]/[COLOR="#008000"]Practice[/COLOR]/[COLOR="#EE82EE"]Downloads[/COLOR]/[COLOR="#008000"]linux-brprinter-installer-2.0.0-1.gz[/COLOR]

...... so that is where your download of linux-brprinter-installer-2.0.0-1.gz has ended up:

so we amend the earlier commands a little: but as before, paste each one line by line and hit enter after each paste ............

[COLOR="#FF0000"]cd Documents/Practice/Downloads
gunzip linux-brprinter-installer-2.0.0-1.gz
sudo bash linux-brprinter-installer-2.0.0-1 MFC-J4510DW[/COLOR]

...... hopefully that will start the install script running .........

---

### Post by Stephen_Willmer on 2014-10-01
Did all that... Then it asked me for my password, which it accepted at the third time of asking, now it wants to know if I'd like to specify a proxy server. Good question.&#55357;&#56866;

---

### Post by pdc on 2014-10-01
are you able to disclose some things about your system? ie many folks have their printer connected by usb cable to a standalone computer ............ so how is your system setup .......... ?

here are a couple of things about proxy servers

[http://www.webopedia.com/TERM/P/proxy_server.html](http://www.webopedia.com/TERM/P/proxy_server.html)

[http://en.wikipedia.org/wiki/Proxy_server](http://en.wikipedia.org/wiki/Proxy_server)

______________

have you any idea why your system would ask this of you?

---

### Post by Stephen_Willmer on 2014-10-02
I was hoping to use the printer wirelessly. At the moment it is not physically connected to the computer. Re proxy servers, I sometimes use secure email, and generally speaking I use my computer for work, sometimes from home, sometimes from work. I access the internet from at least two different wireless routers (if that's the word I want!). Overall things like privacy and confidentiality matter in my use of this computer, but no more than for most people. Don't know if that assists. Feel free to ask away...

---

### Post by pdc on 2014-10-02
if you want to use wireless, the system should find your printer 

"12 For wireless connection:- 'Add' – 'Find Network Printer -enter the ip address (ie192.168.1.50 in my case) – click 'find' – 'select 'jet direct' and 'LPD/LPR PASSTHROUGH' – follow 'forward' – 'Apply'"

[http://ubuntuforums.org/showthread.php?t=1921644](http://ubuntuforums.org/showthread.php?t=1921644)

....................so you need the ip address for your printer ............... if all too hard, I suggest a usb cable and get all things working; then set up an alternate wireless install; (also with usb, the scanner will work well ...... wireless scanning is more tricky......)

does it show up here [http://localhost:631/printers/](http://localhost:631/printers/)

---

### Post by Stephen_Willmer on 2014-10-02
Thanks, pdc, am now at work so will try this when I get home: but please can you clarify what "12 For wireless connection....etc." means? Do I enter this into the Terminal?

What impact if any does your last comment have on the Terminal's enquiry as to whether I want to specify a proxy server?

You've been very kind.

---

### Post by pdc on 2014-10-02
Hi Stephen;

______________

I am guessing the script worked till the point it asked for the now infamous proxy server; 

so I am wondering if it installed the printer drivers: let's check with the command > [COLOR="#FF0000"]dpkg -l | grep Brother[/COLOR] and also let's look for scanner drivers: > [COLOR="#FF0000"]dpkg -l | grep brscan[/COLOR]

___________________-

if you got something for the Brother enquiry: likely with two separate files: with the phrases lpr and a cupswrapper; then the printer driver should be installed: 

.......................if so..............


watch this short video [https://www.youtube.com/watch?v=FBZARGgTAfY](https://www.youtube.com/watch?v=FBZARGgTAfY)

use the printer "ADD PRINTER" option 

ideally it will find your printer and do the work for you .........

_____________

............ if no Brother drivers installed we will need to re-run the script; post here before doing that

---

### Post by Stephen_Willmer on 2014-10-02
Hokay, so I entered the first command, and this is how it looks:

dpkg -l | grep Brother
ii  printer-driver-ptouch                                 1.3-8                                               amd64        printer driver Brother P-touch label printers
sequipadalianism@sequipadalianism-Aspire-V5-431:~/Documents/Practice/Downloads$ 

I tried the second command, and this is how it looks:

dpkg -l | grep brscan
sequipadalianism@sequipadalianism-Aspire-V5-431:~/Documents/Practice/Downloads$ 

Incidentally, I tried answering the proxy server query with a 'N', and that didn't do anything so I tried a 'y', and ditto:

->N
Unable to get the server information. Please check the network settings.
sequipadalianism@sequipadalianism-Aspire-V5-431:~/Documents/Practice/Downloads$ y
y: command not found

Btw, if you're ever in England and you need legal help, google me, I'd be delighted to return the favour.

---

### Post by pdc on 2014-10-02
thanks Stephen: I will bear in mind your kind offer:

so the install script didn't install the driver;

_______________________________________________

Stephen: the other basic we need to go back and check over is............it seems all printers have to be "seen" by the router ..............before a connection is made from the computer to the printer .............

so watch this video: [https://www.youtube.com/watch?v=P_9nVXCqSoo](https://www.youtube.com/watch?v=P_9nVXCqSoo) and at about 50 secs he talks about how to connect the printer to your router .............because I am not sure if you have done this ..... our Epson was set up the same recently when we got it............ printer talks to router and then computer finds printer and with printer drivers installed, all is happy and well

so if you tell me about all that before we move on .................

and can you paste this command > [COLOR="#FF0000"]/usr/sbin/lpinfo -v[/COLOR] into a terminal, and paste back what you get ......

-_

---

### Post by Stephen_Willmer on 2014-10-07
hi, pdc, am back online, sorry for the hiatus. I pasted the command as you suggested:

sequipadalianism@sequipadalianism-Aspire-V5-431:~$ /usr/sbin/lpinfo -v
network socket
network lpd
network http
network https
network ipp
network ipps
network smb
network ipp14
direct hp
direct hpfax
network dnssd://Brother%20MFC-J4510DW._ipp._tcp.local/
network dnssd://Brother%20MFC-J4510DW._printer._tcp.local/
network lpd://BRW9CD21E554F14/BINARY_P1
sequipadalianism@sequipadalianism-Aspire-V5-431:~$ 

I watched the you tube video you recommended, and got my router (which is my 'phone) hooked up to the printer, just as my computer is, so I suppose it can be said there is a network, but got nowhere after that. I also acquired an A to B USB cable and tried connecting the computer to the printer that way. Well, physically, I got them connected, but nothing happened.

Is any of this making sense?

---

### Post by Stephen_Willmer on 2014-10-08
mirabile dictu! somehow I got the printer to work using a USB cable and entering:

[COLOR=#FF0000]cd Documents/Practice/Downloads
gunzip linux-brprinter-installer-2.0.0-1.gz
sudo bash linux-brprinter-installer-2.0.0-1 MFC-J4510DW

[/COLOR]pressing ENTER at the end of each line. the terminal just lit up, and hundreds of lines of code started scrolling down the page! every now and again I was asked to y/N something, usually just to agree to a proposition, and that, after a few minutes, was that.

Still won't scan, though....

---

### Post by pdc on 2014-10-08
well done Stephen: we were away for a day and I have just seen your post;

for the scanner, Brother used to advise to download this small file [http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04) that is [COLOR="#008000"]brother-udev-rule-type1-1.0.0-1.all.deb
[/COLOR]
....I would have thought the install script would have taken care of that; but if you download the file; and double-click on it; it should offer to install itself for you; and with that installed; .........the scanner should be seen and work for you

__________________

if you were to choose the SAVE option when you downloaded it, it would end up in your [COLOR="#0000FF"]Downloads[/COLOR] directory and the commands in a terminal would be:

[COLOR="#FF0000"]cd Documents/Practice/Downloads
sudo dpkg -i brother-udev-rule-type1-1.0.0-1.all.deb[/COLOR]          the last command uses **sudo** so you need your password and uses the debian package manager (**dpkg**) to install ([COLOR="#0000FF"]-i[/COLOR]) the programme that ends in [COLOR="#0000FF"].deb[/COLOR]

any joy?

---

### Post by Stephen_Willmer on 2014-10-09
Hi, pdc, I clicked on the link you provided and was taken to the page with the download ([COLOR=#008000]brother-udev-rule-type1-1.0.0-1.all.deb), [/COLOR][COLOR=#000000]so I clicked on that link and was taken to a page headed 'Licence Agreement'. But it doesn't seem to have loaded properly: at the bottom of the script are two boxes - or so there should be, i can see boxes, which are plainly supposed to be links, and which work as links[/COLOR], but neither box tells me what it is meant to be. A couple of paragraphs above is the script, "**Note:**
Please click on "I Accept" while holding down "Shift" or right click on "I Accept" and select "Save Target As,,," from the menu.", so I tried that to the letter, but nothing happened. Below all of this is gobbledegook which at first glance looks like code, but I think is in fact just random symbols.

I did all of this while the USB cable was plugged in. The long and short of it is that, once again, nothing has happened. I don't think I've got the point where I've downloaded the file and so can double-click on it. 

How do you know all of this, btw? Are you a programmer?

---

### Post by pdc on 2014-10-09
I use Chrome as a browser and when I click on the "I accept" then Chrome goes ahead and downloads it and saves it in our [COLOR="#0000FF"]Downloads[/COLOR] folder

if you have a look in your Downloads folder and see if it is there .............

if you open a terminal and paste these commands

> [COLOR="#FF0000"]cd Documents/Practice/Downloads[/COLOR] .........hit ENTER .........

> [COLOR="#FF0000"]ls[/COLOR]    ..........that asks the computer to list what is there ..............do you see [COLOR="#008000"]brother-udev-rule-type1-1.0.0-1.all.deb[/COLOR] listed there ?? (the [COLOR="#FF0000"]ls[/COLOR] command asks the computer to *list* what is there )

If you do, install it with > [COLOR="#FF0000"]sudo dpkg -i brother-udev-rule-type1-1.0.0-1.all.deb[/COLOR]

---

### Post by kurt18947 on 2014-10-10
> **pdc said:**
> I use Chrome as a browser and when I click on the "I accept" then Chrome goes ahead and downloads it and saves it in our [COLOR=#0000FF]Downloads[/COLOR] folder

if you have a look in your Downloads folder and see if it is there .............

if you open a terminal and paste these commands

 .........hit ENTER .........

   ..........that asks the computer to list what is there ..............do you see [COLOR=#008000]brother-udev-rule-type1-1.0.0-1.all.deb[/COLOR] listed there ?? (the [COLOR=#FF0000]ls[/COLOR] command asks the computer to *list* what is there )

If you do, install it with

Hi PDC

Do you know if the above .deb file addresses this issue about copying certain files to the correct location?

[http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101)

---

### Post by pdc on 2014-10-10
> Do you know if the above .deb file addresses this issue about copying certain files to the correct location?

No

```
dellist=''
cpscanlibmodules(){
  for file in $1
  do
    lib64mod=/usr/lib64/$file
    libmod=/usr/lib/$file

    if [ -f $lib64mod ];then
      if [ -d /usr/lib ];then
        if [ ! -f $libmod ];then
           cp $lib64mod  $libmod 2> /dev/null
           if [ -f $libmod ];then
             dellist2=$(echo $dellist $libmod)
             dellist=$dellist2
           fi
        fi
      fi
    fi
  done
}
```

there are references such as this; I guess if we wait for Stephen to get back to us and one can always recommend the above link: as it referred to 11.10 I am not sure if it is still a necessary step

---

### Post by kurt18947 on 2014-10-11
> **pdc said:**
> No

```
dellist=''
cpscanlibmodules(){
  for file in $1
  do
    lib64mod=/usr/lib64/$file
    libmod=/usr/lib/$file

    if [ -f $lib64mod ];then
      if [ -d /usr/lib ];then
        if [ ! -f $libmod ];then
           cp $lib64mod  $libmod 2> /dev/null
           if [ -f $libmod ];then
             dellist2=$(echo $dellist $libmod)
             dellist=$dellist2
           fi
        fi
      fi
    fi
  done
}
```

there are references such as this; I guess if we wait for Stephen to get back to us and one can always recommend the above link: as it referred to 11.10 I am not sure if it is still a necessary step

I'm not certain either whether this problem has been fixed. It's easy enough to get the list of required files and their locations and check.

---

### Post by Stephen_Willmer on 2014-10-11
Hi, pdc, so I pasted the commands you suggested into the terminal and [COLOR=#008000]brother-udev-rule-type1-1.0.0-1.all.deb[/COLOR] isn't there.

I suspect it doesn't matter, but I did this while unplugged from the printer (i.e. no USB cable plugged in).

---

