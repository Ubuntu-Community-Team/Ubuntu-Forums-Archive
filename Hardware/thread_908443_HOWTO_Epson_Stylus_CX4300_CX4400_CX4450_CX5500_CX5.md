---
title: "HOWTO: Epson Stylus CX4300 CX4400 CX4450 CX5500 CX5600 DX4400 on Ubuntu 8.04"
date: 2008-09-02
forum: Hardware
---

### Post by Dogmeat on 2008-09-02
This howto describes the steps necessary to use the Epson Stylus CX5600 all-in-one with Ubuntu 8.04 (Hardy Heron) as of September 2008. The used kernel versions are 2.6.24-19. The other Epson all-in-ones in the title should work in a similar way.


The scanner was relatively easy to set-up, and the printer is auto-detected, however there is a nasty bug, at least on the CX5600: when the printer enters stand-by mode (after an hour or so), the next time you try to print the printer will stop working and shut down. The next time you turn it on, it wastes a lot of ink. I created a workaround this bug which is covered in this howto.


Another issue is the scanner and printer permissions. On similar howtos, authors either suggest chmodding the printer 777 or having sane change the printer group from 'lp' to 'scanner'. The first suggestion is clumsy as you have to do it every time you restart your computer, and is also a security risk. The second one creates another problem: after you scan something, you get permission denied because sane changes the printer group to 'scanner', and you have to change the printer back to group 'lp' to be able to print again. After this howto you should be able to scan and print at will, no chmodding involved. We may need some packages, so start by typing the following:


```
sudo apt-get install sane-utils sane xsane alien
```The all-in-one drivers are available on the [Japanese vendor's site]("http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do"). Scroll down until you see Image Scan! for Linux & Photo Image Print System.

Choose Epson Stylus CX4300/CX4400/CX4450/CX5500/CX5600/DX4400/DX4450.

In distribution, select Other and distribution version Other.

Fill out the small questionnaire and submit the form. You are directed to a download page. You should download these files: iscan-2.10.0-1.i386.rpm and iscan-plugin-cx4400-2.0.0-0.c2.i386.rpm.
Now you need to convert the packages to the .deb format in order to install them:

Open a terminal and go to the folder where you downloaded the iscan rpms. Then type:

```
sudo alien --scripts iscan-2.10.0-1.i386.rpm
```You should see: iscan_2.10.0-2_i386.deb generated

```
sudo alien --scripts iscan-plugin-cx4400-2.0.0-0.c2.i386.rpm
```You should see: iscan-plugin-cx4400_2.0.0-1_i386.deb generated

To install the generated .deb packages we use dpkg:

```
sudo dpkg -i iscan_2.10.0-2_i386.deb
sudo dpkg -i iscan-plugin-cx4400_2.0.0-1_i386.deb

```Now plug in and switch on the all-in-one. lsusb must show the scanner:

```
lsusb
```My CX5600 shows the following:
[...]
Bus 002 Device 002: ID 04b8:083f Seiko Epson Corp.
[...]

Now it is necessary to edit a file, and search for a line starting with epson.

```
sudo gedit /etc/sane.d/dll.conf
```Comment epson and enable epkowa, it should look like this:

```
[...]
epkowa
#epson
#epson2
[...]
```Using sane-find-scanner you can check whether Sane finds the device. At the moment only root has access to the scanner, so we're using sudo for now.


```
sudo sane-find-scanner -q
```My CX5600 shows the following:

found USB scanner (vendor=0x04b8 [Language Error], product=0x083f [Language Error]) at libusb:002:002


Write down the vendor id (in my case, 0x04b8 and product id (again in my case, 0x083f). We'll need them later. Don't worry about the language errors.


With scanimage -L you can find out if the driver is properly installed.


```
sudo scanimage -L
```I get: 

device `epkowa:libusb:002:002' is a Epson Stylus CX4300/CX4400/CX5500/CX5600/DX4400 flatbed scanner


To allow ordinary users to access the scanner, they must be members of the scanner group. You also need to restart the udev daemon. Obviously replace your_username with your username:

```
sudo adduser your_username scanner
```Should output:
Adding user `your_username' to group `scanner' ...
Adding user your_username to group scanner
Done.

Now you should logout of your account and login again to make the altered group membership effective.

After this, if you type:
```
groups
```You should see scanner among the groups. If not, restart your computer and it should work.

Now we'll make the all-in-one avaliable to both the user 'lp' (responsible for printing) and users in the group 'scanner' (users that may scan)

```


sudo gedit /etc/udev/rules.d/45-libsane.rules

```Rembember I told you to write down the vendor and product ids? Now it's the time to use them. Replace your_vendor_id and your_product_id below with the numbers you wrote down. Replace your_model with your printer model. If you have a similiar entry on that file, delete it, and add this instead:


```
# Epson your_model
SYSFS{idVendor}=="your_vendor_id", SYSFS{idProduct}=="your_product_id", MODE="664", OWNER="lp", GROUP="scanner"
```My file looks like this:


```
# Epson CX5600
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="083f", MODE="664", OWNER="lp", GROUP="scanner"
```Save and exit. Now udev should be restarted:

```


sudo /etc/init.d/udev restart

```You should see this:

 * Loading additional hardware drivers...                                [ OK ]


You should now be able to scan images with xsane.

Type

```
xsane
```To try it out!

Now lets fix the printer standby problem. I assume Ubuntu autodetected your printer and you're using the Stylus CX5600 (or your own printer's) Gutenprint driver. If not, you can add it in System->Administration->Printers.

If you turn the printer on and the green led is not blinking, you should be able to print normally. However, at least on the CX5600, after the printer enters standby mode it will stop working, and you have to turn it on again, which wastes ink and is inconvenient. I fixed this by 'pinging' the printer constantly with a scanner command so it never enters standby mode. For me it was more important to have the printer working all the time than saving a little power, and if you read this far I assume you share the same opinion. So here's how to do it:

```
sudo gedit /etc/crontab
```Append the following to the end of the file, replacing your_model with your printer model (mine is CX5600):

```
# Keep Epson Stylus your_model awake
*/5 *   * * *   root    scanimage -n
```According to scanimage's manual, scanimage -n only sets the options provided by the user but doesn&#8217;t actually perform a scan. It is repeated every 5 minutes to keep the printer always on.

Credits go to these howtos:
[http://uellue.de/blog/single.php?date=1192278660](http://uellue.de/blog/single.php?date=1192278660)
[http://www.ubuntu-es.org/index.php?q=node/69308](http://www.ubuntu-es.org/index.php?q=node/69308)
[http://ubuntuforums.org/showthread.php?t=627471&highlight=cx5600](http://ubuntuforums.org/showthread.php?t=627471&highlight=cx5600)

Please share any thoughts or improvements and i'll update this howto.

---

### Post by braddcadd on 2009-07-07
Hi:

I am trying to install a CX4400 (printing capability only) in Ubuntu9.04.  It auto-detects the printer and starts to print the first test page but gets stuck at 20%.  The light continually blinks and it never finishes.  When I delete the print in the ques and try another, it thinks the printer is busy.

lsusb gives the following (notice the incorrect model number):
> 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 008: ID 04b8:083f Seiko Epson Corp. Stylus DX4450
Bus 003 Device 002: ID 03f0:050c Hewlett-Packard 5219 Wireless Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


So then I try to change the model number in the settings to DX4450, reboot the printer, start another test page, then only goes to 10% (although printer never moves), and light starts blinking again.

Any ideas?

---

### Post by stoppage on 2009-08-15
Great guide Dogmeat, much obliged..I finally got sad old DX4400 scanning. One question..what's the quality of your scanned images like? My PDF scans are dismal quality. Trying various settings, any tips?

---

### Post by MichelangeloF536 on 2009-08-22
Thanks, Dogmeat--I've been beating on this scanner for a couple days trying to figure out what I needed to get it working. Now it's running perfectly!

---

### Post by stoppage on 2009-08-28
Scanned PDF files are a huge size in memory, even with using "gscan2pdf" on serious (jpg) compression. And the quality of coloured scans is, at best, mediocre

---

### Post by Norabunny on 2009-09-20
Thanks Dogmeat! This guide got my DX4400 scanning perfectly, aye the scanned files are big - only when the quality is set high.

I am however still having trouble printing, It won't even print a test page for me, it gets stuck at 20%. The red ink light is constantly on (even though the cartridges are full) and the green light flashes all the time. I tried the pinging script but it doesn't help. Any ideas anyone?

---

### Post by RomanM on 2009-10-18
Got my CX5900 scanner working right away after installing deb 64bit from DL page, but printer driver which used to be autoinstalled in 8.04 is obviously missing for amd64 in 9.04. Gutenscan, btw ;)

---

### Post by KEIII on 2009-11-07
Hi. Epson Stylus CX4300 scanner don't work after install Ubuntu 9.10 (In 9.04 its work). Does anybody have the same problem ?

---

### Post by RomanM on 2009-11-10
No, scans fine, though printer driver doesn't want to install anymore :/

---

### Post by terry_gardener on 2009-12-14
found getting the scanner working for the dx4400 was easy. 

went to the website of the above guide and then downloaded the 2 deb files under the scanner section for my printer. 

installed the deb files and then i was able to scan. simple

only one issue is that it disables the printer after it installs but really easy to re-enable it. just goto system-administration-printing right click the printer and click enable thats it. 

hope this helps someone.

---

### Post by jampe on 2010-09-16
This guide is very thorough, I must say.

It didn't work for me, though.
Here's what's wrong in my case (I'm on Ubuntu 10.4):

1: There was no "/etc/udev/rules.d/45-libsane.rules"
[INDENT]- but there was a "/lib/udev/rules.d/40-libsane.rules"[/INDENT]

2: After typing in "sudo /etc/init.d/udev restart" (or just "sudo restart udev" nowadays), I just received the message "udev start/running, process [process number]"

3: After ignoring those little kinks, I tried to start up xsane, but it crashes immediately. I have searched for hours to try and find the command that lets me see why it does that, but it's completely lost on me.

It works just fine in Windows 7 and Mac OS 10.6, so it's not a hardware incompatibility issue. Please help. My brain is melting.

---

### Post by LMB on 2010-11-06
For the file: there are now .deb files on the Japanese website, so alien is not necessary (it's not necessary anymore to use alien to convert rpm to deb)

---

### Post by johnmartindavies on 2010-12-31
Thank you
Very clear and detailed instructions. I'm still using Ubuntu 9.04 on my Eee pc 901 with Epson DX4450. Scans fine thanks to you. Critical for me as my Vista desktop hard drive has crashed so loaded that up with Ubuntu 10.04 and some flash drives and SD cards.
Still trying work out ink levels and wizard for changing inks.
Any ideas?

---

