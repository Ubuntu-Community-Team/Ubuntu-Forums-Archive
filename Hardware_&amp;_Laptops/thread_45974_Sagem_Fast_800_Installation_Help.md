---
title: "Sagem Fast 800 Installation Help"
date: 2005-07-02
forum: Hardware &amp; Laptops
---

### Post by fedemw on 2005-07-02
hi to everyone!

i had ubuntu installed on my amd64 3000+ ;-)

i had troubles for install my modem adsl SAGEM FAST 800 with Wanadoo access in spain.

Can someone describe me which packages i should install to configure it? (please step by step, i dont know how to use well apt-get) 

And drivers? i downloaded a tar from web but i dont know how to open, etc

thanks a lot for your help

---

### Post by alastair on 2005-07-02
I would always advise anyone using Linux (or XP for that matter), to always use an external ethernet based ADSL modem/router. No Linux config necessary - less pain.

In  this case - a google search :

[http://www.google.co.uk/search?hl=en&q=SAGEM+FAST+800+adsl+linux&btnG=Google+Search&meta=](http://www.google.co.uk/search?hl=en&q=SAGEM+FAST+800+adsl+linux&btnG=Google+Search&meta=)

Leads me to :

[http://www.linuxcompatible.org/Newbie_Sagem_Fast_800_modem_ADSL_wont_work_t27801.html](http://www.linuxcompatible.org/Newbie_Sagem_Fast_800_modem_ADSL_wont_work_t27801.html)

or

Tutorial for connecting Wanadoo(France) with Sagem Fast 800
[http://www.mepis.org/node/3211](http://www.mepis.org/node/3211)

Or

download the Linux driver here :

[http://www.sagem.com/support/site/modele_fax.php?page=driver](http://www.sagem.com/support/site/modele_fax.php?page=driver)

i.e. [http://www.sagem.com/support/site/driver/Fast8x0_3-0-6.tgz](http://www.sagem.com/support/site/driver/Fast8x0_3-0-6.tgz)

1) Unpack :

tar xvfz Fast8x0_3-0-6.tgz

2) cd eagle-usb

READ the "readme"

3) Make sure you also install a compiler and kernel headers i.e.

sudo apt-get install build-essential
sudo apt-get install linux-headers-2.6.10-5-386  (*)

(*) For the headers - choose the right package for your kernel. Open "synaptic" - search for "linux-headers" and choose the headers that match your kernel. You can find your kernel by typing : "uname -r"  in a shell.

4) Compile :

./configure
make
sudo make install

5) Try :

eagleconfig

Then :

startadsl

Anything?

There are web links in the "readme" file - and maybe Google can help.

Good luck.

---

### Post by coolclassic on 2005-07-03
If you used the search facilities in ubuntu forums you will find this topic well covered. Just type sagem in the box.

---

### Post by fedemw on 2005-07-03
hi friends, thanks a lot for you help. I can configure the modem right now, but the problem is i can´t surf.

take a look:


CONNECTION PROBLEMS

root@lenin:/home/federico # eaglestat
eagle-usb status display
-------------------------------------------------------------
Driver version 2.0.0     Chipset: Eagle0
Vendor ID : 0x1110     Product ID : 0x9021   Rev: 0x500b
USB Bus : 001    USB Device : 004        Dbg mask: 0x0
Ethernet Interface : eth1
MAC: 00:60:4c:4e:79:ed
Tx Rate         128  Rx Rate         512
FEC               0  Margin           25  Atten            41 dB
VID-CPE           0  VID-CO           28  HEC               0
VPI               8  VCI              35  Delin          GOOD
Cells Tx        272  Cells Rx        174
Pkts Tx         226  Pkts Rx         174
OAM               0  Bad VPI           0  Bad CRC           0
Oversiz.          0

Modem is operational

(light of sincronization is turned ON)



root@lenin:/home/federico # eaglediag
Diagnostic (1.13 2004/08/29) driver eagle-usb 20050703235319
# System Information
Linux lenin 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux
3.1
Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005
gcc versión 3.3.5 (Debian 1:3.3.5-8ubuntu2) used : 3.3.4 (Debian 1:3.3.4-9ubuntu5)
# module loaded ?        [ OK ]
# modem operational ?    [ OK ]
# Config vpi/vci/encapsulation/isp : 8 23 6 (pppoa) ES03
# pppd launched ?        [ KO ]
# ping IP ?              [ KO ]
# test DNS resolution ?  [ KO ]
Complete diagnostic has been saved on /var/log/eagle-usb/eagle_diag_20050703235319.txt
Please keep only relevant data and remove personal informations.


--> i think pppd is not launched. ¿what can i do?


See configuration files:


more /etc/eagle-usb/eagle-usb.conf

#POTS FOR EAGLE
OPTN0=80020066
# OPTN2=23700000
# OPTN3=00000000
OPTN4=00000000
# OPTN5=00000000
# OPTN6=00000000
# OPTN7=02CD8044
# OPTN15=09090909
VPI=00000008
VCI=00000023

#The following values are valid for encapsulation :
#MPOA_MODE_BRIDGED_ETH_LLC ----> 1
#MPOA_MODE_BRIDGED_ETH_VC  ----> 2
#MPOA_MODE_ROUTED_IP_LLC   ----> 3
#MPOA_MODE_ROUTED_IP_VC    ----> 4
#MPOA_MODE_PPPOA_LLC       ----> 5
#MPOA_MODE_PPPOA_VC        ----> 6
Encapsulation=00000006

Linetype=00000001
RatePollFreq=00000009
</eaglectrl>
STATIC_IP=none
ISP=ES03
LANG=es
ASYNCHRONOUS_START=1



root@lenin:/home/federico # more /etc/resolv.conf
62.36.225.150
62.37.228.20
nameserver 62.36.225.150
nameserver 62.37.228.20
root@lenin:/home/federico #




Thanks a lot for your help I hope i can surf from ubuntu next connection! :grin:

---

### Post by coolclassic on 2005-07-03
You have a permission problem with the following files /etc/ppp/chap-secrets and /etc/ppp/pap-secrets you will need to change there permissions
The following commands should help
"sudo chmod 751 /etc/ppp/pap-secrets"
and then chap-secrets

---

### Post by fedemw on 2005-07-03
hi

permissions changed, rebooted but i still i can't browsing.

waiting for help! thanks!

---

### Post by coolclassic on 2005-07-04
I forgatten to add that you now have to make sure that these two files read the same. Where it says:

"adsl@adsl" * "adsl" *
"Your login" * "your password"

Cut and paste from pap to chap

and save

Every thing should now work.

---

### Post by fedemw on 2005-07-05
hi coolclasic, thanks a lot for your help. THIS IS MY FIRST POST FROM UBUNTU !!!

i make that changes in the files and now i am logged in.

If anyone needs help about it, just contact me.

Bye !

---

### Post by frosty36 on 2006-01-31
> 
2) cd eagle-usb



What do you mean by this ... put it on the CD ; where abouts ?

---

### Post by coolclassic on 2006-01-31
cd means change directory. When you uncompressed the file you created a new directory called eagle-usb (this dir has all the files for compiling), you need to enter this directory before you can compile the software.

---

### Post by frosty36 on 2006-02-01
and where should I put it :-k

---

### Post by coolclassic on 2006-02-01
Where ever you want.

I put all self compiled software in a folder called Software some people put it into opt or other directory.

---

### Post by ace2005 on 2006-02-03
Ok well here is a mini guide
Go and download the driver from here:

[http://sourceforge.net/project/showfiles.php?group_id=81588](http://sourceforge.net/project/showfiles.php?group_id=81588)

File: eagle-usb-2.3.2.tar.bz2

Go into synaptic and install:

build-essential
linux-kernel-headers

Now in konqueror:

Go to the location where you downloaded the file,
Right Click on the file > Extract > To Here
Go into the New Directory Created by Arc 
Press F4

Konsole will now open in the directory that you were working on in konqueror

./configure
make
sudo make install
sudo eagleconfig

Give the Location, Username, Password (typing not shown) the module will be loaded, 

sudo startadsl

This will Start the connection and when you restart the computer by the time your at the desktop your internet connection would have already connected

---

### Post by ace2005 on 2006-02-03
[QUOTE=coolclassic]Where ever you want.

I put all self compiled software in a folder called Software some people put it into opt or other directory.[/QUOTE]

Should we keep stuff we compiled? if so whats the point? i just keep the archives they came in

---

### Post by coolclassic on 2006-02-03
If you have compiled from the archive then you would want to keep the compiled software. The archive you can delete at you leasure.

Now that is my understanding if I am wrong someone please correct me.

---

### Post by x3sw on 2006-02-07
[FONT="Comic Sans MS"][SIZE="4"]I installed Ubuntu on my second hard drive at the end of 2005 and all went well, except I could not get my Sagem Fast 800 modem to work.  It was recognised by the system, but was obviously missing the right driver.  I found drivers on both the Sagem and  the Ubuntu packages sites, but could not get these to install - errors every time.  The error messages only referred to missing commands which did not mean much to me.

The post by Alastair 7/2/05 in this thread finally helped.  Running the "./configure", followed by "make" highlighted that I had downloaded and installed  version 4.0 of compiler gcc, whereas I need 3.4. After rerunning all the commands again the modem ADSL light came on and the rest was a piece of cake.

Anyway, many thanks to all who have treid to help us new-comers to Linux.

My message to the numbers who have posted in other threads that the Sagem Fast 800 insn't compatible with Ubuntu is that it will work!
[/SIZE][/FONT]

---

### Post by x3sw on 2006-02-10
[FONT="Comic Sans MS"][SIZE="1"]I have to add a footnote to my post above.  Having got my modem working with my original kernel (2.6.12-9-386), I downloaded a different version - 2.6.12-9-k7 as it seemed to suit my set up better (AMD Athlon 1.6 / 512gB).  However, the modem driver, although appearing to install OK, refused to work.  Eagleconfig worked but startadsl failed with a message that I needed to send a DNS to the modem which also failed.  Fortunately, I've still got the original kernel available and all is OK with this, execpt that Synaptic Package cannot get the repositories form the web.  Both Firefox and e-mail work OK.

It seems to me that whether the driver works or not depends on which version of the kernel one is using.[/SIZE][/FONT]

---

### Post by Helen on 2006-03-05
[QUOTE=x3sw]
Running the "./configure", followed by "make" highlighted that I had downloaded and installed  version 4.0 of compiler gcc, whereas I need 3.4. After rerunning all the commands again the modem ADSL light came on and the rest was a piece of cake.
[/QUOTE]

Hello everyone
I'm new to Linux/Ubuntu. I basically have the same problem. Do you mean i have to install gcc-3.4? If so, how do i do this? I can access the internet from Windows XP but not from Linux.

Any help very much appreciated.

---

### Post by jerrykenny on 2006-03-09
helen, type in a terminal

sudo apt-get install gcc-3.4

---

### Post by Geoneil on 2006-05-12
[QUOTE=x3sw][FONT="Comic Sans MS"][SIZE="1"]I have to add a footnote to my post above.  Having got my modem working with my original kernel (2.6.12-9-386), I downloaded a different version - 2.6.12-9-k7 as it seemed to suit my set up better (AMD Athlon 1.6 / 512gB).  However, the modem driver, although appearing to install OK, refused to work.  Eagleconfig worked but startadsl failed with a message that I needed to send a DNS to the modem which also failed.  Fortunately, I've still got the original kernel available and all is OK with this, execpt that Synaptic Package cannot get the repositories form the web.  Both Firefox and e-mail work OK.

It seems to me that whether the driver works or not depends on which version of the kernel one is using.[/SIZE][/FONT][/QUOTE]

I'm using the k7 kernel as I also have an AMD Athlon XP 2200+ 1.8GHz and in the end I gave up on the Sagem and am now using a Speedtouch 330 that Virgin.net sent me for the short while I was with them (after I ditched Tiscali, even though I carried on using the Sagem up until now.  I use the Speedtouch for both OSs)

---

### Post by Mogski on 2006-05-29
I installed linux ubuntu 5.10, and have had endless problems with getting tiscali broadband (with sagem f@st 800 modem) [uk] to work. I have read through various threads on this forum, but any solutions I try, I hit a wall at some point. What makes it difficult is that I can't get online AT ALL, and have ended up reinstalling windows :o( until I have solved the problem. I should make clear that I am a linux newbie. I started off making sure that I had installed all the networking and compiling packages from the cd, suggested by various people on this forum. I could only get the ethernet connection to become active, but not the modem, and of course the sagem is not an ethernet connection, so inevitably "startadsl" didn't work. After a while I found out that I had the wrong version of gcc, and downloaded 3.4.5 in order to get eagleusb 2.3.3 working. Because I haven't been able to get online at all, I have had to download these from someone else's computer, burn them to disc and work from there. So far, I haven't even had any luck unpacking these- I heard that this could be something to do with the directory that they are in, but I have absolutely NO IDEA where the terminal would be looking for them. Forgive my lack of clarity on this matter- my head is in a pickle- I have lost sleep over it! I am now thinking that this is perhaps all a little out of my depth, and really, to learn more about using linux, I need to be online...so I thought of buying a router (which apparently will solve my problems)...can someone tell me if it's ok to use either an ADSL one OR an ethernet one (I was thinking ethernet, because I got the ethernet connection working-maybe ADSL goes into ethernet port? I don't know). You have a very confused linux newbie on your hands, should you wish to help, Thanks. :o)

---

