---
title: "Lexmark Z2420 Z2400 Series"
date: 2010-03-29
forum: Hardware
---

### Post by outleradam on 2010-03-29
I bought my Lexmark Z2420 printer at walmart for $50 for my girlfriend's homework assignments.  I've read around that the printer is a paperweight.  I have it running on my ubuntu computer.  Here's how:
Allow me to revise this for the newer methods

**For Wired Printing:**
1.  Download:[http://www.downloaddelivery.com/downloads/cpd/lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz](http://www.downloaddelivery.com/downloads/cpd/lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz)
2. Double-click the download, then drag the file to the Desktop
3. open a terminal and type the following
```
cd ~/Desktop
sudo ./lexmark-08z-series-driver-1.0-1.i386.deb.sh

```run through the easy setup.
**Congratulations!  You now have wired printing enabled**

** For Wireles Printing:**
An alternate method for getting printing to work is to search for the   wireless printer (HP Setup or something), then connect up and find your   printer's wireless setup page.  Then instruct it to connect to your   wireless network.  This requires some understanding of how to find IP   addresses on a network.  The lexmark begins it's out-of-box life with an  ad-hoc network.  You can figure it out if you want to. Keep reading for the windows method.

You will need Windows or Mac for this method.  Since I own a few  windows XP keys, I created a windows Virtual machine.   I used my  Windows  XP Virtual Machine.
On Windows:
1. Insert CD-ROM.
2. Run through easy setup
-set wireless network and password
3. Open your router, Usually [http://192.168.1.1]("http://192.168.1.1/") or 192.168.0.1.  read  documentation to set static IP address to your printer
4. Unplug router and printer for 60 seconds to reset IP addresses.
Then on Ubuntu:
5. Click System>Administration>Printing
6. In the Printing window, click the +Add button
7. Expand Network Printer>AppSocket/HP JetDirect
8. Type in the Host name(IP ADDRESS) and press forward
9. Select Lexmark from the manufacturer list and click next
10. Select Z2400 (recommended) from the list  and cick next
11. Do happy dance again as your test page prints out.
**Congratulations!  You now have a wireless printer!**

You will now have two printers.  My_Lexmark_Z2400_Series which is for  wired printing and Lexmark-Z2400 which is for wireless printing.   

If this helps, The quick pro way to set up a printer is through cups, It's easy when  you have your IP address and your Printer information.
Install lexmark drivers [http://www.downloaddelivery.com/downloads/cpd/lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz](http://www.downloaddelivery.com/downloads/cpd/lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz)
Navigate to [http://127.0.0.1:631/admin/](http://127.0.0.1:631/admin/)
Add printer, run through setup
Here's the information which I need to set up my printer:
socket://192.168.1.104:9100
Lexmark  Z2400 1.0 (EN)

Original DIY guide without instructions for wireless printing.:
> 
1. Download lexmark-08z-series-driver-1.0-1.i386.deb.sh from here 
[http://support.lexmark.com/index?page=answers&startover=y&locale=en&userlocale=EN_US&productCode=LEXMARK_X5650&segment=DOWNLOAD&question=z2420#2](http://support.lexmark.com/index?page=answers&startover=y&locale=en&userlocale=EN_US&productCode=LEXMARK_X5650&segment=DOWNLOAD&question=z2420#2)

2. Create a root account by opening a terminal and typing sudo passwd root  then enter your password and the root password

3.  Run lexmark-08z-series-driver-1.0-1.i386.deb.sh and enter the root password

4. Open CUPS [http://127.0.0.1:631/admin/](http://127.0.0.1:631/admin/)

5. Click "Add Printer"

6. Choose "Lexmark Z2400 Series (Lexmark Z2400 Series)"  and click continue

7. Set the printer name and location, then click continue

8. Select Lexmark Z2400 Series, 1.0(en) and add printer

9. Set your default options and you're done

10. Click Print Test Page and do happy dance.

---

### Post by wjbite on 2010-04-25
I tried your procedure above and at step number 3 here is what I got (help please - and thankyou)
wjbite@KarmicDeskTop:~/Desktop$ run lexmark-08z-series-driver-1.0-1.i386.deb.sh
No command 'run' found, did you mean:
 Command 'zrun' from package 'moreutils' (universe)
 Command 'runq' from package 'exim4-daemon-heavy' (main)
 Command 'runq' from package 'sendmail-bin' (universe)
 Command 'runq' from package 'exim4-daemon-light' (main)
 Command 'grun' from package 'grun' (universe)
 Command 'qrun' from package 'torque-client' (multiverse)
 Command 'lrun' from package 'lustre-utils' (universe)
 Command 'rn' from package 'trn' (multiverse)
 Command 'rn' from package 'trn4' (multiverse)
 Command 'rup' from package 'rstat-client' (universe)
 Command 'srun' from package 'slurm-llnl' (universe)
run: command not found

I also tried it without the "run".
I also tried it with "rn".

Walt

PS
Never mind - I found that by double clicking on the icon of the script on the desktop, it opened the box that asked (amoung other things) do you want to "run"  -viola!
It seems that the root permissions were still enabled.

Thanks for posting the solution.
Walt

---

### Post by outleradam on 2010-06-11
Wireless printing is up and running in 10.04


Here's how

1. install using methods above
2. select system>Administration>Printing
3. click Add
4. expand the "Network Printer" option and select AppSocket/HP JetDirect
5. Type in the Host name(IP ADDRESS) and press forward
6. Select Lexmark from the manufacturer list and click next
7. Select Z2400 (recommended) from the list  and cick next
8. Do happy dance again as your test page prints out.




Settings:
Description Lexmark Z2400
Device URI: socket://192.168.1.104:9100
Make and Model: Lexmark Z2400 Series, 1.0



:guitar:

---

### Post by Jim1804 on 2010-06-12
Thanks for posting this info - I'm a linux newbie, and just got the Z2420 today (a few months after you guys). It's working fine on my Windows machine, and it works when connected via USB on my Ubuntu (Karmic) machine, but I can't get it to work wirelessly with Ubuntu. On your instructions above - how do I figure out the Host name? Any other help would be appreciated!

---

### Post by outleradam on 2010-06-13
Hostname = IP address.  I just updated the above post.  

See your router documentation to assign Static IPs to devices on your network.

The other option is to assign a static IP through the printer itself, but the DHCP Server, centrally managed router option is a much cleaner method.

---

### Post by outleradam on 2010-06-13
Allow me to revise this for the newer methods
If you want to do it through CUPS, it's 


1.  Download:[http://www.downloaddelivery.com/downloads/cpd/lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz](http://www.downloaddelivery.com/downloads/cpd/lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz)
2.Double-click the download, then drag the file to the Desktop
3.open a terminal and type the following
```
cd ~/Desktop
sudo ./lexmark-08z-series-driver-1.0-1.i386.deb.sh

```run through the easy setup.
Congratulations!  You now have wired printing enabled

Now for wireless:

An alternate method for getting printing to work is to search for the  wireless printer (HP Setup or something), then connect up and find your  printer's wireless setup page.  Then instruct it to connect to your  wireless network.  This requires some understanding of how to find IP  addresses on a network.  The lexmark begins it's out-of-box life with an ad-hoc network.  You can figure it out if you want to. 

You will need Windows or Mac to get this working.  Since I own a few windows XP keys, I created a windows Virtual machine.   I used my Windows  XP Virtual Machine.
On Windows:
1. Insert CD-ROM.
2. Run through easy setup
-set wireless network and password
3. Open your router, Usually [http://192.168.1.1](http://192.168.1.1) or 192.168.0.1.  read documentation to set static IP address to your printer
4. Unplug router and printer for 60 seconds to reset IP addresses.

Then on Ubuntu:
5. Click System>Administration>Printing
6. In the Printing window, click the +Add button
7. Expand Network Printer>AppSocket/HP JetDirect
8. Type in the Host name(IP ADDRESS) and press forward
9. Select Lexmark from the manufacturer list and click next
10. Select Z2400 (recommended) from the list  and cick next
11. Do happy dance again as your test page prints out.

You will now have two printers.  My_Lexmark_Z2400_Series which is for wired printing and Lexmark-Z2400 which is for wireless printing.   



The quick pro way to set up a printer is through cups, It's easy when you have your IP address and your Printer information.
Install lexmark drivers
Navigate to [http://127.0.0.1:631/admin/](http://127.0.0.1:631/admin/)
Add printer, run through setup
Here's the information which I need to set up my printer:
socket://192.168.1.104:9100
Lexmark  Z2400 1.0 (EN)

---

### Post by MizzouDude on 2010-07-05
I am new to Ubuntu and have been trying to get my Lexmark 2470 to print, without success. I tried the above tips with no luck. In the terminal after typing in your suggested command, I get "command not found".  Double clicking the desktop icon, I "opened" and "extracted" but got a prompt "could not open the file...gedit has not been able to detect the character encoding..."

Any suggestions/help would be greatly appreciated.

MD

---

### Post by anglican on 2010-07-06
> **MizzouDude said:**
> I am new to Ubuntu and have been trying to get my Lexmark 2470 to print, without success. I tried the above tips with no luck. In the terminal after typing in your suggested command, I get "command not found".  Double clicking the desktop icon, I "opened" and "extracted" but got a prompt "could not open the file...gedit has not been able to detect the character encoding..."

Any suggestions/help would be greatly appreciated.

MD
You need to give a bit more information here I think. Which command, exactly as you typed it, didn't work?

H

---

### Post by teknoclash on 2010-07-08
Thanks for the post! I tried installing before I looked here and it would accept my password. Used this method and worked like a Mac ;) Thanks

---

### Post by outleradam on 2010-07-09
OH NO!!! By working like a mac I take it you mean that it did not repsect DHCP rules and crashed your network, when you touch the antenna it looses signal, and it only gave you 2 options the whole time :lolflag:

---

### Post by outleradam on 2010-07-09
> **MizzouDude said:**
> I am new to Ubuntu and have been trying to get my Lexmark 2470 to print, without success. I tried the above tips with no luck. In the terminal after typing in your suggested command, I get "command not found".  Double clicking the desktop icon, I "opened" and "extracted" but got a prompt "could not open the file...gedit has not been able to detect the character encoding..."

Any suggestions/help would be greatly appreciated.

MD
The only thing in the terminal is the installation program... 

The installation works as printed above, here is an alternat method for installing the drivers.

```
 wget http://www.downloaddelivery.com/downloads/cpd/lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz
sudo chmod +x ./lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz
sudo ./lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz
```

---

### Post by cammino on 2010-07-12
Maybe I'm over-thinking here, but will this process work with a direct wireless connection to the computer or must a wireless network (ie router) be in place. I'm looking at using this printer for wireless printing from a laptop and only have a wired network at the moment. Once again, apologize if this is redundant.

---

### Post by outleradam on 2010-07-18
I'd give it a go. It worked under windows.  I don't know about how Linux would handle it.

---

### Post by MizzouDude on 2010-07-31
Reply to H:

The command I used was:

sudo ./lexmark-08z-series-driver-1.0-1.i386.deb.sh

Terminal response: command not found.

Thx.

MizzouDude

---

### Post by MizzouDude on 2010-07-31
> **outleradam said:**
> The only thing in the terminal is the installation program... 

The installation works as printed above, here is an alternat method for installing the drivers.

```
 wget http://www.downloaddelivery.com/downloads/cpd/lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz
sudo chmod +x ./lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz
sudo ./lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz
```
Outleradam #11:  

As I said, I am totally new to this process. Thank you for your patience. Could you give me a complete step by step on how you got this to work for you?

MD

---

### Post by outleradam on 2010-08-03
click the ubuntu menu > Accessories > terminal 

Then copy and paste this into the terminal window

```

 wget http://www.downloaddelivery.com/downloads/cpd/lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz
sudo chmod +x ./lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz
sudo ./lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz
```

Then run through the menus as they pop up and follow the instructions I gave before.  It's all menus after the bit in the terminal

---

### Post by recoush on 2011-08-25
[SIZE=2]i have an issue with ubuntu 11.04 i get the following error while trying to install the lexmark driver see screen shots i either get a floating point exception or this pogo error i have tried sudo gksudo and gksu all end in similar results any [/SIZE]help much appreciated

---

