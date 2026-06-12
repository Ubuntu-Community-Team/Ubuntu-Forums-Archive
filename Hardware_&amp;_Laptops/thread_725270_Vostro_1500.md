---
title: "Vostro 1500"
date: 2008-03-15
forum: Hardware &amp; Laptops
---

### Post by Stealth1081 on 2008-03-15
This is how I got my Dell Vostro 1500 working

For gutsy gibbon

Installation as standard

Wireless

The way I configured my wireless card was to connect to my router first using an ethernet cable and install:	

                [B]ndisgtk
		ndiswrapper-common
		ndiswrapper-utils-1.9[/B]

From synaptic package manager.

To find it just search for ndiswrapper all three should show up.

After that you can run ndisgtk it is found under
System/ Administration/ Windows Wireless Drivers

Go to [http://support.euro.dell.com/support/downloads/download.aspx?c=uk&cs=ukbsdt1&l=en&s=bsd&releaseid=R151517&SystemID=VOS_N_1500&servicetag=&os=WW1&osl=en&deviceid=8043&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=202136](http://support.euro.dell.com/support/downloads/download.aspx?c=uk&cs=ukbsdt1&l=en&s=bsd&releaseid=R151517&SystemID=VOS_N_1500&servicetag=&os=WW1&osl=en&deviceid=8043&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=202136)

and download the drivers to you desktop.

Once you have the file use the second mouse button and click on open with other application.
Click on Archive Manager then open.
Then extract the driver folder to your desktop.

Open Windows Wireless Drivers if asked, put your password in.
Click on install new driver.
Click on the box that says none.
Navigate to your desktop.
Double click on driver
Double click on the only .inf file.
After that click on install.

Now it should say hardware present.

Close the program

Wait about 30 seconds then
Left click on the network settings. You wireless network shouldnow be available to connect to. (If your network isn't hidden.)
If not you will have to do a manual configuration.
That i can't help you with as it will differ depending on your router setup.


As of now your wireless is working but will not work after reboot for that your have to open up terminal and input these two lines of code.

**sudo modprobe ndiswrapper**

After that.

**echo 'ndiswrapper' | sudo tee -a /etc/modules**

If anyone knows if you can skip the first step please let me know.

After reboot it should start automatically.

For your sound card 
Wile you are still in terminal type.

**sudo apt-get install linux-backports-modules-generic**

Then just reboot.


This is how i got my vostro working, it may or may not work for you.

If anyone has anything they wish to add please do so.

---

### Post by philliprobert on 2008-03-18
I instaleld gutsy gibbon on the same laptop as a fresh install, picked up the wireless with no problem whatsoever. Other then updates since, i havent changed anything, so if there is anything you would like me to check on mine, please let me know (and how to do so, as im still new to this!)

---

### Post by Stealth1081 on 2008-03-18
Hi there
Thanks for your interest.

I am new to this to as only been using linux for about a month.
The only reason i started this post is because there was not an easy to follow how to guide  on this laptop for a complete beginner i hope i have succeed as you are the first to reply. 

I would be interested to know how you got your wireless working as i had a hell of a job getting mine working and could not do it without the ndiswrapper gui.

I haven't found any more problems with mine like other people have been reporting. fans don't seem to work but the machine never really gets very hot either.

---

