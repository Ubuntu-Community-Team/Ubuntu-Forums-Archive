---
title: "n00b Req: help with Speedtouch 330"
date: 2005-05-23
forum: Hardware &amp; Laptops
---

### Post by Double-X on 2005-05-23
Hi, i'm a n00b when it comes to Ubuntu.

I tried to install it at a friends place and he has a Alcatel Speedtouch 330 USB (Ruby Red one)
I tried to follow the instructions on [linux-usb.sourceforge.net](http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/warty.html)  

Downloaded all the files, but since I'm a n00b I can't manage  :???: 

I hope someone can help this n00b out, I copied and paste some of the instructions below.
I think it's writen for someone who has at least some experience in Ubuntu, not a n00b like me.

Thanks in advance..

```
The Linux Kernel Speedtouch Driver for Ubuntu Warty Warthog
To get online with the Speedtouch modem you will need at least two things. A copy of the firmware and a copy of modem_run. They're both quite small files and will fit on one floppy disk. It might be wise to save this page on the floppy as well, then you can open it with Firefox to copy and paste the commands highlighted. You don't have to use a floppy disk, you could use another partition of your hard drive or a flash memory stick or something.
Before you go into that offline environment, consult this table and note whether your ISP uses PPPoATM or PPPoE. You'll also need to know the VPI/VCI numbers for your country/ISP. 

If your ISP uses PPPoE you will need an extra package, br2684ctl. Save it on the floppy along with the firmware, modem_run and this page. 

When you've rebooted into Ubuntu you'll need to mount the floppy disk. Start by opening a root terminal. On the top toolbar click Applications> System Tools> Root Terminal and then enter your password, put the floppy in, then enter 

modprobe floppy 
Keep the root terminal open as you'll need it again in a minute. 

On the top panel click Computer> Disks> double click on the floppy disk. That should mount the floppy and put a little icon on your desktop. Again on the top panel click Applications> Internet> Firefox. That should open Firefox. In the top left corner of Firefox Click File> Open File...and navigate to /media/floppy to open this page.
Right click on your desktop and open a terminal. Enter these commands to copy everything from the floppy disk into your home and unzip the firmware. In your user (not root) terminal enter this (copy and paste to avoid typos) 

cp -r /media/floppy/* . &&
unzip SpeedTouch330_firmware_3012.zip 
What Revision?
Different versions of the modem use different firmware. To find out what revision your modem is, use the command 

cat /proc/bus/usb/devices | grep -B 1 THOMSON
cat /proc/bus/usb/devices | grep -B 1 ALCATEL 
At the end of the first line it should say Rev= X.00
X is the version of the modem you have. 

The rest of the commands should be run in the root terminal 

The Firmware
Copy the firmware somewhere convenient. /etc/ppp works for me. If you have a revision 4 modem copy the ZZZL_3.012 file 

cp ZZZL_3.012 /etc/ppp/mgmt.o 
Otherwise, use the KQD6_3.012 file 

cp KQD6_3.012 /etc/ppp/mgmt.o 
modem_run
Now put modem_run somewhere convenient in root's $PATH 

install -m 744 modem_run /usr/sbin 
Secrets
Now you need to make a file called either chap-secrets or pap-secrets. If you don't know whether your ISP uses chap or pap authentication then just create both files. It won't do any harm. In the root terminal enter 

gedit /etc/ppp/{pap-secrets,chap-secrets} 
That will open gedit with chap-secrets in one tab and pap-secrets in the other. Add just one line to the end each file 

"username@isp" * "password" 
Change username@isp for the username your ISP gave you and change password for the password you chose when you set up your account with your ISP.
Now you need to configure ppp by editing a few text files. If your ISP is PPPoE skip down to the PPPoE section 

PPP Over ATM
If your ISP uses PPP over ATM put this in /etc/ppp/peers/speedtch. You'll need to be root to write there so run gedit with the root terminal 

gedit /etc/ppp/peers/speedtch 
Copy and paste this into gedit but change username@isp for the username your ISP knows you by. Often (but not always) it has an @isp bit at the end. It may be @bt, for example. Also, change the 0.00 at the bottom for the VP/VC values for your country/ISP.


lcp-echo-interval 10
lcp-echo-failure 3
noipdefault
defaultroute
user "username@isp"
noauth
noaccomp
nopcomp
noccp
novj
holdoff 4
persist
maxfail 25
updetach
usepeerdns
plugin pppoatm.so
0.00 
If you're interested to know more about what each of those options does (perhaps you want to tweak them?) open a shell and type man pppd 

Tidying Up
Now you just need to tidy up some loose ends. Make a symbolic link to sort out domain nameserver lookups. In the root terminal enter 

rm -f /etc/resolv.conf &&
ln -s ppp/resolv.conf /etc/resolv.conf 
You'll need to ensure some modules are loaded to be able to connect with ppp. Open /etc/modules with a text editor 

gedit /etc/modules 
Add these two entries to /etc/modules so they will be loaded during the boot process 

ppp_generic
pppoatm 
To connect on boot you'll need to make a bootscript. These commands will 

Put a bootscript called dial in /etc/init.d 
Make it executable 
Make a symbolic link pointing at it from /etc/rc2.d so that it gets run during the boot process. 
Copy and paste this into the root terminal. 

cat > /etc/init.d/dial << "EOF"
#!/bin/bash
modem_run -k -f /etc/ppp/mgmt.o &&
pppd call speedtch
EOF
chmod 744 /etc/init.d/dial &&
ln -s ../init.d/dial /etc/rc2.d/S95dial 
And that's it, reboot and you should be online.
Edit /etc/apt/sources.list as you like, run apt-get update and then you can install all sorts of new things off the internet. For more details read 

man apt-get 
Please report any SpeedTouch problems to the mailing list 
--------------------------------------------------------------------------------

PPPoE
If your ISP uses PPPoE then things are a bit more complicated. Copy and paste this into the root terminal 

alien -i br2684ctl_20040226-1_i386.deb 
Open gedit with the root terminal 

gedit /etc/ppp/peers/speedtch 
Copy and paste this into gedit, change username@isp for the username your ISP knows you by. It often has an @isp bit at the end (it might be @bt, for example) 

lcp-echo-interval 10
lcp-echo-failure 3
noipdefault
defaultroute
user "username@isp"
noauth
noaccomp
nopcomp
noccp
novj
holdoff 4
persist
maxfail 25
updetach
usepeerdns
plugin rp-pppoe.so
nas0 
If you're interested to know more about what each of those options does (perhaps you want to tweak them?) open a shell and type man pppd 

Tidying Up
Now you just need to tidy up some loose ends. Make a symbolic link to sort out domain nameserver lookups. In the root terminal enter 

rm -f /etc/resolv.conf &&
ln -s ppp/resolv.conf /etc/resolv.conf 
You'll need to ensure some modules are loaded to be able to connect with ppp. In the root terminal enter 

gedit /etc/modules 
Add these three entries to /etc/modules and they will be loaded during the boot process 

ppp_generic
pppoatm
br2684 
To connect on boot you'll need to make a bootscript. With the root terminal open gedit 

gedit /etc/init.d/dial 
Copy and paste this into gedit. Change VP.VC for the VPI/VCI numbers for your country/ISP. For example in Spain it's 8.32


#!/bin/bash
modem_run -k -f /etc/ppp/mgmt.o &&
sleep 10 &&
br2684ctl -b -c 0 -a VP.VC &&
sleep 20 &&
pppd call speedtch


Those sleeps add thirty seconds delay whist booting, which is not ideal. You can try using lower values, but you might not get online at all.
Make that script executable and make a symbolic link pointing at it from /etc/rc.d so that it gets run during the boot process. Copy this into the root terminal 

chmod 744 /etc/init.d/dial &&
ln -s ../init.d/dial /etc/rc2.d/S95dial 
Reboot and you should be online.


gedit /etc/apt/sources.list 
Chang it to your taste and then run 
apt-get update 
Then you can install all sorts of new things off the internet. For more details read 
man apt-get
```

---

