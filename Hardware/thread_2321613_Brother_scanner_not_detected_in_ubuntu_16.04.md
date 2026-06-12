---
title: "Brother scanner not detected in ubuntu 16.04"
date: 2016-04-23
forum: Hardware
---

### Post by cartafilus on 2016-04-23
brother scanner no detected in ubuntu 16.04.Drivers from vendor installed,all configured and seem to be ok.But when trying to scan says scanner not detected. Neither usb nor network.System says everythink is ok but apps don't detect scanner.Any help please?

davidoff@baloo:~$ sudo dpkg -l | grep Brother
[sudo] contrasenaya per a davidoff: 
ii  brother-udev-rule-type1                              1.0.0-1                                             all          Brother udev rule type 1
ii  brscan3                                              0.2.13-1                                            amd64        Brother Scanner Driver
ii  printer-driver-brlaser                               3-3build1                                           amd64        printer driver for (some) Brother laser printers
ii  printer-driver-ptouch                                1.4-1                                               amd64        printer driver Brother P-touch label printers
davidoff@baloo:~$ brsaneconfig3 -q | grep 9120
 27 "MFC-9120CN"
  0 9120                "MFC-9120CN"        I:192.168.1.50
davidoff@baloo:~$ ^C
davidoff@baloo:~$

---

### Post by gifford on 2016-04-23
Is this a new install of 16.04 or an upgrade?
Check in usr/local/brother/sane in file brsanenetdevice3.cfg to make sure the address is the same. If your router somehow changed the address it is not always reflected in the config file and the applications will not find the scanner.

---

### Post by cartafilus on 2016-04-24
i's a new install,thanks

---

### Post by cartafilus on 2016-04-24
The adress of the scanner is static.,the file brsanetdevice3.cfg  is DEVICE=9120 , "MFC-9120CN" , 0x4f9:0x21d , IP-ADDRESS=192.168.1.50 .The scanner is not detected by usb either.The printer works fine by net and by usb.Thanks for your reply

---

### Post by SuperFreak on 2016-04-24
I have the same issue with a Brother MFC-5490CN printer. Tried the Brother install tool, tried manually installing Brother software with Brother's instructions and tried using Scanner settings as set out by Brother ([http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&prod=mfc5490cn_all&comple=on&redirect=on#u13.04](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&prod=mfc5490cn_all&comple=on&redirect=on#u13.04))
> Ubuntu 10.10, 11.4, 11.10, 12.04, 12.10, 13.04, 13.10
    1. Click here to download the file.(brother-udev-rule-type1-1.0.0-1.all.deb, ver.1.0.0-1, 2KB)
    2. Run the command.
    Command: dpkg -i brother-udev-rule-type1-1.0.0-1.all.deb
They don't have updated instructions

---

### Post by jfeole on 2016-04-24
> **SuperFreak said:**
> I have the same issue with a Brother MFC-5490CN printer. Tried the Brother install tool, tried manually installing Brother software with Brother's instructions and tried using Scanner settings as set out by Brother ([http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&prod=mfc5490cn_all&comple=on&redirect=on#u13.04](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&prod=mfc5490cn_all&comple=on&redirect=on#u13.04))

They don't have updated instructions

Yes, same issue here with a MFC-7840W.  Loaded drivers and can print fine via network, as I have the printer installed on the network., but the scanner
will not be recognized?

Thanks,
John Feole

---

### Post by Ruhani04 on 2016-04-24
Same problem here - always was able to find a solution in previous versions but not in 16.04.
I have a brother MFC-240c which prints fine but somehow the scanner can't be accessed even though it is found with sane-find-scanner command.
I have updated all the udev rules but still no success. :confused:
Any support would be greatly appreciated. ](*,)

---

### Post by SuperFreak on 2016-04-25
I sent an email to Brother telling about the issue and what I tried to do to install the scanner. Perhaps if enough people write to them they will update the drivers or install tool

---

### Post by him610 on 2016-04-25
I just finished reading all of the non-op problems posted on this page. I am running Xubuntu 16.04 and have a Brother laser MFC7360N, that's a black & white laser printer, scanner, fax, copier machine. I have not yet faxed anything, but all of the other functions work fine. I downloaded the drivers from the Brother support website, followed the instructions found on Brother's pages, and have experienced no problems. 

I just now used Simple Scan to scan a document then print it out. I have never made any tweaks or mods - it all just worked. You all need to make sure you complete the setup in system-config-printer utility (that is what it is called in Xubuntu) correctly. If you don't, your system may not find the the device.
Are you guys sure you are following the install instructions to the letter?

BTW, I have two other machines running Ubuntu 14.04 that use the same MFC7360N without any issues.

---

### Post by SuperFreak on 2016-04-25
> **him610 said:**
> I just finished reading all of the non-op problems posted on this page. I am running Xubuntu 16.04 and have a Brother laser MFC7360N, that's a black & white laser printer, scanner, fax, copier machine. I have not yet faxed anything, but all of the other functions work fine. I downloaded the drivers from the Brother support website, followed the instructions found on Brother's pages, and have experienced no problems. 

I just now used Simple Scan to scan a document then print it out. I have never made any tweaks or mods - it all just worked. You all need to make sure you complete the setup in system-config-printer utility (that is what it is called in Xubuntu) correctly. If you don't, your system may not find the the device.
Are you guys sure you are following the install instructions to the letter?

BTW, I have two other machines running Ubuntu 14.04 that use the same MFC7360N without any issues.

I have installed Brother printer/scanner drivers on Ubuntu 10.10,12.04 and 14.04 this is the first time I couldn't get the scanner to work

---

### Post by SuperFreak on 2016-04-25
Great

I have it working. Looks like with 64-bit Ubuntu you have to copy /usr/lib64/sane to /usr/lib/sane for it to work.
see [http://ubuntuforums.org/showthread.php?t=2043258]("http://ubuntuforums.org/showthread.php?t=2043258")

---

### Post by him610 on 2016-04-25
@SuperFreak
I wonder why the Brother drivers do not work for you, but the Brother drivers work successfully for me. You have successfully installed the drivers several times before which indicates you have been around the block a couple of times. Maybe, if we put our heads together we can figure something out. If one can work, they both should work.

My MFC7360N has a static IP address (192.168.1.99) on the LAN. All of the applicable 64bit deb drivers were downloaded from the Brother support website, and the linux-brprinter-installer-2.0.0.1 script. I did not know if I actually needed the *.deb files or not in the same directory, but I figured it wouldn't hurt, then I executed the installer script, linux-brprinter-installer-2.0.0-1
Here is a list of the files I downloaded from the Brother website...(of course, it won't be mfc7360n, but your model designation)
```
-rw-rw-r-- 1 hugh hugh 29308 Mar 31 15:51 brmfcfaxcups-1.0.0-1.i386.deb
-rw-rw-r-- 1 hugh hugh 25716 Mar 31 15:52 brmfcfaxlpd-1.0.0-1.i386.deb
-rw-r--r-- 1 root root 73704 Dec 16 01:41 brscan4-0.4.3-3.amd64.deb
-rw-r--r-- 1 root root 50852 Sep  5  2013 brscan-skey-0.2.4-1.amd64.deb
-rw-r--r-- 1 root root 11040 Mar 31 15:18 cupswrapperMFC7360N-2.0.4-2a.i386.deb
-rw-r--r-- 1 root root 13248 May 24  2013 cupswrapperMFC7360N-2.0.4-2.i386.deb
-rw-r--r-- 1 root root 26264 Mar 31 15:18 mfc7360nlpr-2.1.0-1a.i386.deb
-rw-r--r-- 1 root root 35820 May 24  2013 mfc7360nlpr-2.1.0-1.i386.deb
-rw-rw-r-- 1 hugh hugh 92056 Mar 31 15:14 linux-brprinter-installer-2.0.0-1
-rwxr-xr-x 1 root root   46 Mar 31 15:39 uninstaller_brscan4
-rwxr-xr-x 1 root root   50 Mar 31 15:39 uninstaller_brscan-skey
-rwxr--r-- 1 root root 1285 Mar 31 15:39 uninstaller_MFC7360N
```

I have another machine with  Ubuntu 16.04 installed on it that I have yet to set up with the MFC7360N which I will try to complete sometime tomorrow, keeping a log of all actions/responses. I will post it in this thread when I finish.

---

### Post by him610 on 2016-04-25
@SuperFreak
> Looks like with 64-bit Ubuntu you have to copy /usr/lib64/sane to /usr/lib/sane for it to work.

Mine does not have /usr/lib/sane however it has a link  (I never quite understood links)
```
hugh@SN68Sx:~/Downloads/Brother$ ls -l /usr/lib64/sane
total 156
lrwxrwxrwx 1 root root     37 Nov 23 18:58 libsane-brother4.so -> /usr/lib64/sane/libsane-brother4.so.1
lrwxrwxrwx 1 root root     41 Nov 23 18:58 libsane-brother4.so.1 -> /usr/lib64/sane/libsane-brother4.so.1.0.7
-rwxr-xr-x 1 root root 158304 Nov 23 18:58 libsane-brother4.so.1.0.7

```

---

### Post by Ruhani04 on 2016-04-26
Followed everything by brother and installed everything without problems but scanner cannot be accessed by sane -xsane.
Printer works fine. Had similar problems in the past but normally it was just a question of access rights. So far sudo xsane always worked but no longer.
Sane finds : found USB scanner (vendor=0x04f9, product=0x01ab) at libusb:001:005
???????????

---

### Post by Ruhani04 on 2016-04-26
Thx for your suggestion but after following it still failed - xsane says failed to open device - invalid argument for scanner.

per sane scanner finder : found USB scanner (vendor=0x04f9, product=0x01ab) at libusb:001:002

However after manually configuring sane xsane shows the scanner at bus4:dev7 and of course claims invalid argument.

At this point I can only assume that sane is unable to find the correct bus/dev which may be mobo related.

---

### Post by him610 on 2016-04-26
> I have another machine with Ubuntu 16.04 installed on it that I have yet to set up with the MFC7360N which I will try to complete sometime tomorrow, keeping a log of all actions/responses. I will post it in this thread when I finish.

My activities related to the Brother linux-brprinter-installer script download, installation, and setup can be found here...
[http://ubuntuforums.org/showthread.php?t=2322192]("http://ubuntuforums.org/showthread.php?t=2322192")

Maybe it will help someone.

---

### Post by jfeole on 2016-04-26
Thank you SuperFreak and him10..

1)  I removed(uninstalled) my failed install from last weekend, using the uninstall scripts that are generated when you attempt to install.

2)  Then, I used him10's post#16 above,  to make certain I was installing correctly.

3)  And lastly, i used SuperFreak's suggestion to copy the contents AFTER installing of: /usr/lib64/sane 
to /usr/lib/sane
**note that there wasn't a sane directory in /usr/lib, and I had to create it in terminal:
$ sudo mkdir /usr/lib/sane
$ sudo cp /usr/lib64/sane/* /usr/lib/sane

(i seem to remember having to do this lib copy in earlier rev's of Ubuntu for my brother mfc-7840w,
but didn't think it was still necessary..)

Anyways, thanks for the help..now i can install it to my desktop and laptop after updating to 
16.04.

JFeole

---

### Post by glacoon on 2016-04-27
Hi all,

Here is my short experience on a fresh 16.04 Kubuntu installation (64 bits) with a DCP-7055 connected through USB:

1/ I ran Brother script ([http://support.brother.com/g/s/id/linux/en/faq_prn.html?c=us_ot&lang=en&redirect=on#f00104](http://support.brother.com/g/s/id/linux/en/faq_prn.html?c=us_ot&lang=en&redirect=on#f00104))
==> printing was OK but scanner not detected

Next, following this page ([http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on))
2/ I installed **[FONT=courier new]brother-udev-rule-type1-1.0.0-1.all.deb[/FONT]**[COLOR=#000000][FONT=Arial]
==> nothing changed for scanner

3/ I added the following two lines at the end of [/FONT][/COLOR]**[FONT=courier new][COLOR=#000000]/lib/udev/rules.d/40-libsane.rules [/COLOR][/FONT]**[COLOR=#000000][FONT=Arial](Before the line "[FONT=courier new]*# The following rule will disable ...*[/FONT]")[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][FONT=courier new][I]# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

[/I][/FONT][COLOR=#000000][FONT=Arial]And finally, I could scan with normal user (before, it worked only with root).

[/FONT][/COLOR]

---

### Post by Fred Le Rouge on 2016-04-28
@glacoon: I did all of this but the scanner of my DCP-195C still is not detected by xsane...

@SuperFreak: By the way, what email address did you use to warn Brother of this problem?

---

### Post by Ruhani04 on 2016-04-29
I contacted Brother but I am not sure if they will fix the problem. The reply was that they tested their install software and they also were not able to scan and that they would inform their technicians.
All I did was send an email under their support section.

---

### Post by david_brown6 on 2016-04-29
Me 2, unfortunately.  I've previously had difficulties installing Brother DCP-J315W in last two versions of Ubuntu but got there eventually after lots of pain & hours.  

This time, 16.04 upgrade failed so I was forced into another re-install.  I followed the usual process, installed drives etc, printer works, sane-find-scanner sees the beast, but sudo xsane says "no devices available".  Suffice to say simple-scan fails.

The only difference in the install process I noticed was 40-libsane.rules may now be named 60-libsane.rules but I've edited the new file as usual and still no joy.  Interestingly, I was sure I edited 40-libsane.rules yesterday, early in the process but when I went looking for this file today, could only find 60-libsane.rules and it needed editing again???? Huh, I could only think that some updates came through and reset that file.  Something weird and wonderful happened there. 

I'm in contact with Brother in Oz and they say nothing has changed - just follow the old installation process.  I'm calling BS but will have to wait till Monday before I can phone them.  

Far from happy and hoping to see some good advice from others on this thread.

OOPS - hadn't seen the solution on page of thread.......  I did the cp -r /usr/lib64/sane /usr/lib/sane thingee and it worked for me too.  Yeh, cheers, champagne.




Cheers
Dave[IMG]http://ubuntuforums.org/images/icons/icon8.png[/IMG]

---

### Post by braderhart on 2016-04-30
Found this to be incredibly helpful:

```

export SANE_DEBUG_DLL=128
scanimage -L

```

```

[dll] load: searching backend `brother3' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-brother3.so.1'
[dll] load: couldn't open `/usr/lib/x86_64-linux-gnu/sane/libsane-brother3.so.1' (No such file or directory)
[dll] load: trying to load `/usr/lib/sane/libsane-brother3.so.1'
[dll] load: couldn't open `/usr/lib/sane/libsane-brother3.so.1' (No such file or directory)
[dll] load: couldn't find backend `brother3' (No such file or directory)

```

Per the previous suggestion, you must copy the files or create a link.

---

### Post by Fred Le Rouge on 2016-05-01
I think I have a solution! For those who can read French, here is the [link]("https://forum.ubuntu-fr.org/viewtopic.php?id=1988903").
For the others, I will tell you what I did (Arsène Leiris is my pseudonym in the French forum).

This works for the Brother DCP-195C, but I guess it will work for other models.

First I installed the brother pilots thanks to the automated script given by Brother [here]("http://support.brother.com/g/b/downloadend.aspx?c=fr&lang=fr&prod=dcp195c_all&os=128&dlid=dlf006893_000&flang=4&type3=625").
Then I used another [script]("http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04") given by Brother to resolve the permissions issue.
I edited **/lib/udev/rules.d/40-libsane.rules** by adding ```
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
```
before the line "# The following rule will disable".
Finally I followed the instructions [here]("http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&comple=on&redirect=on#f00101"). But instead of copying some of the files to **/usr/lib/sane **, I copied them to **/usr/lib/x86_64-linux-gnu/sane** (I use Ubuntu 16.04 64 bits). If you use the 32 bits version, copy the files to **/usr/lib/i386-linux-gnu/sane** .
Here is what I did specifically:

```
sudo cp /usr/lib64/libbrscandec3.so.1.0.0 /usr/lib
sudo cp /usr/lib64/sane/libsane-brother3.so.1.0.7 /usr/lib/x86_64-linux-gnu/sane
sudo cp /usr/lib64/sane/libsane-brother3.so.1 /usr/lib/x86_64-linux-gnu/sane
sudo cp /usr/lib64/sane/libsane-brother3.so /usr/lib/x86_64-linux-gnu/sane
sudo cp /usr/lib64/libbrscandec3.so /usr/lib
sudo cp /usr/lib64/libbrscandec3.so.1 /usr/lib
```

I tested a whole bunch of "solutions" one after the other so maybe one should start by copying the files in the directories that are indicated [here]("http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&comple=on&redirect=on#f00101"). I am not sure if all these steps are necessary, but it eventually worked for me ^^' Thanks a lot to ares who gave me a solution!
To put things into context, the scanner of my multifunction Brother printer DCP-195C was not detected by xsane (as explained extensively in the [French forum]("https://forum.ubuntu-fr.org/viewtopic.php?id=1988903")).

Pass the solution around!

---

### Post by krisbeazley on 2016-05-01
This did the trick.  Thank you for your answer. 

I had to: 
sudo mkdir /usr/lib/sane
sudo cp * /usr/lib64/sane/* /usr/lib/sane/

Scanner now works.

---

### Post by klaus15 on 2016-05-08
Thank you for the help.
I had to do both: 

sudo mkdir /usr/lib/sane
sudo cp * /usr/lib64/sane/* /usr/lib/sane/

and

sudo cp /usr/lib64/libbrscandec3.so.1.0.0 /usr/lib
sudo cp /usr/lib64/sane/libsane-brother3.so.1.0.7 /usr/lib/x86_64-linux-gnu/sane
sudo cp /usr/lib64/sane/libsane-brother3.so.1 /usr/lib/x86_64-linux-gnu/sane
sudo cp /usr/lib64/sane/libsane-brother3.so /usr/lib/x86_64-linux-gnu/sane
sudo cp /usr/lib64/libbrscandec3.so /usr/lib
sudo cp /usr/lib64/libbrscandec3.so.1 /usr/lib

After that Simple Scan and Xsane workt worked perfectly fine with my MFC-9840CDW (networked) on my amd64 installation.
On two other systems with i386 installation I just needed to follow the instructions on the Brother site to make it work.

---

### Post by manny14 on 2016-05-16
My FIX

My Brother DCP-J140W wifi printer+scanner stopped working after a 16.04  install. The Brother Installer complained about some unknown  directories, bad file descriptors, etc. I eventually reinstalled CUPS  then re-ran installer. Now printer + scanner working. As follows:

apt-get purge
apt-get install cups
sudo bash linux-brprinter-installer-2.0.0-1 DCP-J140W

Hope this helps

---

### Post by wanderer3 on 2016-05-16
> **SuperFreak said:**
> Great

I have it working. Looks like with 64-bit Ubuntu you have to copy /usr/lib64/sane to /usr/lib/sane for it to work.
see [http://ubuntuforums.org/showthread.php?t=2043258](http://ubuntuforums.org/showthread.php?t=2043258)

Thank you so much for that. Had tried all sorts but that works.

---

### Post by roger_1960 on 2016-05-24
This

sudo mkdir /usr/lib/sane
sudo cp * /usr/lib64/sane/* /usr/lib/sane/

Solved the scanner not working issue under 16.04 for me with my DCP-J315W (having already followed Brother's instructions which worked for 14.04)

Many thanks to those who enlightened us!

---

### Post by Gary_C_Bellaire on 2016-06-04
This worked for me with a brsane type 3 printer.  

In viewing this thread and noticing that some people had problems, while others did not, I found that the problem may actually be tied to specific Brother brsane drivers, not to all of them.

Brother's Linux page shows 4 brsane drivers, each of which supports certain specific Brother scanner models.  

I have 2 Brother scanners - an MFC-7440N, which uses brsane3, and an MFC-J430W, which uses brsane4.  The MFC-J430W installed cleanly under Ubuntu 16.04 by following the Brother Linux documentation.  No special copying was needed.  The MFC-7440N, however, uses brsane3, and that's the scanner that caused me fits until I tried the solution quoted below.  

FYI.



> **klaus15 said:**
> Thank you for the help.
I had to do both: 

sudo mkdir /usr/lib/sane
sudo cp * /usr/lib64/sane/* /usr/lib/sane/

and

sudo cp /usr/lib64/libbrscandec3.so.1.0.0 /usr/lib
sudo cp /usr/lib64/sane/libsane-brother3.so.1.0.7 /usr/lib/x86_64-linux-gnu/sane
sudo cp /usr/lib64/sane/libsane-brother3.so.1 /usr/lib/x86_64-linux-gnu/sane
sudo cp /usr/lib64/sane/libsane-brother3.so /usr/lib/x86_64-linux-gnu/sane
sudo cp /usr/lib64/libbrscandec3.so /usr/lib
sudo cp /usr/lib64/libbrscandec3.so.1 /usr/lib

After that Simple Scan and Xsane workt worked perfectly fine with my MFC-9840CDW (networked) on my amd64 installation.
On two other systems with i386 installation I just needed to follow the instructions on the Brother site to make it work.

---

### Post by rbbwana on 2016-06-20
I barely know what I am talking abou t --but I had same problem several years ago with another ubuntu distro--found this then and saved it. I just installed brother drivers for my MFC7420. Printer worked, scanner not recognized.   The fix I found previous was added and it worked both in simple scan and in gimp /xsane. It is for a usb printer. so if you have a USB, maybe try it. If you are not usb-- I wouldn't attempt it.  Either way, make a back up.   modify you udev 50 rules . lib/udev/ 50 udev default rules---- it may over ride this next time you boot--- I don't know as I have kept computer on.  add the following after this  SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"  

 then add this :  SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", ENV{ID_USB_INTERFACES}=="", IMPORT{program}="usb_id --export %p"
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", ENV{ID_USB_INTERFACES}==":0701*:", GROUP="lp", MODE="0666"

I then went back to the subsytem and change 0664 to 0666.

I really don't know what I am doing ---but this has worked for me twice  --- once with 9.10 and now for 16.04

hope it helps

---

### Post by maugarta on 2016-07-22
Thanks, it works for me.
I think that instead of copy files its better link files. For example:
sudo ln -s /usr/lib64/libbrscandec3.so.1.0.0 /usr/lib
sudo ln -s /usr/lib64/sane/libsane-brother3.so.1.0.7 /usr/lib/x86_64-linux-gnu/sane
sudo ln -s /usr/lib64/sane/libsane-brother3.so.1 /usr/lib/x86_64-linux-gnu/sane
sudo ln -s /usr/lib64/sane/libsane-brother3.so /usr/lib/x86_64-linux-gnu/sane
sudo ln -s /usr/lib64/libbrscandec3.so /usr/lib
sudo ln -s /usr/lib64/libbrscandec3.so.1 /usr/lib

---

### Post by anders650 on 2016-08-29
> **krisbeazley said:**
> This did the trick.  Thank you for your answer. 

I had to: 
sudo mkdir /usr/lib/sane
sudo cp * /usr/lib64/sane/* /usr/lib/sane/

Scanner now works.

I don't understand why you have the first "*" in the cp command. This will just cause all files in the current directory to be copied, which is not what I think you intended. 
The correct command is:

```
sudo mkdir /usr/lib/sane
sudo cp /usr/lib64/sane/* /usr/lib/sane/

```

---

### Post by EnkiduinNZ on 2016-08-30
> **SuperFreak said:**
> Great

I have it working. Looks like with 64-bit Ubuntu you have to copy /usr/lib64/sane to /usr/lib/sane for it to work.
see [http://ubuntuforums.org/showthread.php?t=2043258]("http://ubuntuforums.org/showthread.php?t=2043258")

Excellent! My scanner now works. However, I did **not** copy the directory, I merely created a link in /usr/lib/sane.

```
sudo ln -s /usr/lib/sane64 /usr/lib/sane
```

---

### Post by hackerkitty on 2016-09-05
[COLOR=#000000][COLOR=#000000][FONT=ubuntubeta][FONT=arial]
3/ I added the following two lines at the end of [/FONT][/FONT][/COLOR][/COLOR][B][FONT=&quot][COLOR=#000000]/lib/udev/rules.d/40-libsane.rules [/COLOR][/FONT][COLOR=#000000][FONT=arial](Before the line "[FONT=&quot]*# The following rule will disable ...*[/FONT]")[/FONT][/COLOR][COLOR=#000000][FONT=arial]
[/FONT][/COLOR][FONT=&quot][I]# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
[/I][/FONT][/B]This solved my problem. THANKS:D The printer was Brother MFC-J870DW.

---

### Post by emmortsade59 on 2016-09-07
Same problem with my MFC-465N with usb connection which worked fine in 14.04.  I did all the requested options of the forum. The printer works fine. 
sane-find-scanner  find it
scanimage -L   failed
And xsane nor Simple-scan fails to find it.

---

### Post by aubreymcfato on 2016-10-25
Hi, I have the same issue (printer works, not scan).
BUT, I *don't* have nor ```
/usr/local/lib64
``` nor ```
/usr/local/lib
```. 
How is this possible?

---

### Post by SuperFreak on 2016-10-25
> **aubreymcfato said:**
> Hi, I have the same issue (printer works, not scan).
BUT, I *don't* have nor ```
/usr/local/lib64
``` nor ```
/usr/local/lib
```. 
How is this possible?
The folder you are looking for is
```
/usr/lib64/sane
```
copy that to
```
/usr/lib/sane
```

---

### Post by Paulgirardin on 2016-10-25
I had trouble with this in 16.10:

dll] sane_get_devices
[dll] load: searching backend `brother' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-brother.so.1'
[dll] load: couldn't open `/usr/lib/x86_64-linux-gnu/sane/libsane-brother.so.1' (No such file or directory)
[dll] load: trying to load `/usr/lib/sane/libsane-brother.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-brother.so.1'
[dll] load: dlopen() failed (libusb-0.1.so.4: cannot open shared object file: No such file or directory)
[dll] load: searching backend `xerox_mfp' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-xerox_mfp.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-xerox_mfp.so.1'
Segmentation fault (core dumped)

I also had to install libusb-0.1-4

---

### Post by hallamjeff on 2016-10-28
** for network scanners **

I tried all of the solutions in this thread but the one that helped was this instruction from the Brother site:

[COLOR=#000000][FONT=Arial][B]Command  :  brsaneconfig3  -a  name=(name  your  device)  model=(model  name)  ip=xx.xx.xx.xx


[/B][/FONT][/COLOR]

---

### Post by patrick61 on 2016-11-08
> **Paulgirardin said:**
> I had trouble with this in 16.10:

I also had to install libusb-0.1-4

This fixed a networked MFC-L2740DW for me on 16.10.  Thanks!

---

### Post by chessplayer on 2016-11-18
Hi everyone,

a network install worked for me with an MFC-7360N. However, the same install on another machine using another such printer/scanner connected via USB produced the problem that scanning was not possible. So I tried linking /usr/lib/sane to /usr/lib64/sane to no avail. Finally, what did the trick for me I found [here]("http://linuxwelt.blogspot.de/2016/01/verbindung-zum-scanner-konnte-nicht.html"). In short, I had to do:

**sudo chmod o+wr /dev/bus/usb/00*/***

---

### Post by svanpoeck on 2016-11-19
> **Paulgirardin said:**
> 
I also had to install libusb-0.1-4

This fixed it for me on Ubuntu 16.10 for a networked Brother MFC-J5320DW.

Thanks Paul!

---

### Post by mintynz on 2016-11-20
Same here with Linux mint 17.3 Rosa in the last few weeks an update must of unsettled the system for Brother ...Again. This is the 3rd time that brother fails to survive a "rattle".

Im running a Laser Brother MFC-7420 and MFC-j430w ink jet. Digging out my info on the fix again is just another down time for processing Film scans from a family History Album but it ... has .. to be done.
I'll keep thread on my watch and if time permits will post feedback on my fix.

Cheers
Chris - NZ

---

### Post by eddie552 on 2016-12-03
> **Paulgirardin said:**
> I had trouble with this in 16.10:

I also had to install libusb-0.1-4

Im running Ubuntu Mate 16.10 and am using a Brother MFC-L2700DW on a network

I used the brother script and the printer worked great but the scanner was not recongized by the Simple Scan

I tried this

**Command : brsaneconfig4 -a name=(name your device) model=(model name) ip=xx.xx.xx.xx**

[COLOR=#000000][FONT=sans-serif]Confirm network scanner entry[/FONT][/COLOR]
**Command : brsaneconfig4 -q | grep (name of your device)**

AND i tried
**1. Open "/lib/udev/rules.d/40-libsane.rules" file.**[B][B]2. Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
If there is "LABEL="libsane_rules_end"", add the following 2 lines before "LABEL="libsane_rules_end"". 

The lines to be added---------------------------[/B][/B][B][B]
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"[/B][/B]
Nothing worked...

The only thing that made this INSTANTLY work was 

sudo apt-get intsall libusb-0.1-4

Thanks again

---

### Post by daniel-muller on 2017-01-08
> **Paulgirardin said:**
> I had trouble with this in 16.10:

I also had to install libusb-0.1-4

This solved the issue for me in 16.10. Thanks Paul.

---

### Post by FrankThuis on 2017-01-15
Same here. Samsung C460 DID work with 16.04 but not with 16.10. 
sudo apt-get install libusb-0.1-4 did the job for 16.10. Thanks!

---

### Post by timmzahn on 2017-01-21
Bingo! sudo apt-get install libusb-0.1-4 did the trick in Ubuntu 16.10.

Thanks to the three folks ahead of this reply, as it was their posts that helped me find this via a Google search.

---

### Post by pazystamas2 on 2017-02-02
Tried everything listed here, nothing helped to run **dcp-j152w on ubuntu 16.10**. Then, noticed that my printer/scaner should use **brscan4** instead of **brscan3**.
Solution: **brsaneconfig4 -a name=dcp-j152w model=dcp-j152w ip=192.168.0.4**   <---your ip
List of model/config version: [http://support.brother.com/g/s/id/linux/en/download_scn.html](http://support.brother.com/g/s/id/linux/en/download_scn.html)

---

### Post by win5000mac on 2017-03-26
[B]Successfully installed printer and scanner MFC-1911NW
[/B]follow all the steps from Brother support website and FAQ.
******************************************************************************************
I'm using Ubuntu 16.10. I cannot scan from my Brother Machine. 


Install the "libusb-0.1-4". 


Command : sudo apt-get update


Command : sudo apt-get install libusb-0.1-4

******************************************************************************************

I followed all the tips from all the ubuntu user's from this thread.  My printer got detected easily but I was facing problems with the scanner. Installed it properly as said by BrotherSupport but got stuck at the scanner. Used various copy commands. but missed the 'sudo apt-get install libusb-0.1-4' command. All the packages showed no scanner detected. Xsane, SimpleScan, GScan2pdf. And also 'scanimage -L' command showed segmentation error. The sane command to find the scanner 'sane-find-scanner' showed that the scanner is detected but was not working in xsane. 

Now, installed libusb-0.1-4 and it worked smoothly.

Thank you
Hope it helps somebody

Using Ubuntu 16.10

---

### Post by Paulgirardin on 2017-04-16
I just installed 17.04.

/lib/udev/rules.d/40-libsane.rules no longer exists.
It is now:
/lib/udev/rules.d/60-libsane.rules

add
 ```
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
```
to this file

---

### Post by coverup1128 on 2017-04-16
I resolved issues with my MFC-9330 scanner by installing using the Driver Install recommended by the Brother Technical support. The website is a little confusing, and when I first downloaded drivers from there, the scanner did not work. I contacted the technical support, and they recommended the install tool which solved the problem:        

[http://support.brother.com/g/b/downloadend.aspx?c=au&lang=en&prod=mfc9330cdw_us_eu_as&os=128&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadend.aspx?c=au&lang=en&prod=mfc9330cdw_us_eu_as&os=128&dlid=dlf006893_000&flang=4&type3=625)

The quality of technical support was great.

---

### Post by sp40140 on 2017-04-19
I have MFC-240C and printer works but scanner doesn't get detected on 64bit 17.04 Ubuntu. I have tried everything mentioned in this thread and then some.
I gave me lots of trouble on 16.10 as well but I had it working somehow. (I did wipe and clean install as I put in new SSD). Those steps didn't help with 17.04!
Now banging my head on wall.

---

### Post by pdc on 2017-04-19
you deserve your own thread; these ones get to be a jumble:

please start a new thread and let's see if we can get your brscan2 MFC working

---

### Post by lsutiger on 2017-05-08
I wanted to add that I got my Brother MFC-240C scanner working. I took all of the steps in this thread but I would still get a No Scanner Found message from SimpleScan and two permission errors from xsane. When I ran xsane with sudo, I was able to scan. I googled the exact error I received from xsane alone with ubuntu 16.04 and found that the permissions needed to be changed on the dev folder.
```
 lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0951:1625 Kingston Technology DataTraveler 101 II
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f9:01ab Brother Industries, Ltd MFC-240C
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
sudo chmod a+w /dev/bus/usb/003/002

```

---

### Post by Tanker Bob on 2017-05-24
> **Paulgirardin said:**
> I had trouble with this in 16.10:

I also had to install libusb-0.1-4

I could not get my Brother HL-2280DW scanner recognized by sane in Kubuntu 17.04. The printer works great with the Brother driver and sane-find-scanner would find the scanner every time, but not xsane or simple scan. I tried everything on Brother's website to the letter, copied the /user/lib64/sane to /user/lib/sane, and everything else suggested in this thread. Installing libusb-0.1-4 finally got xsane to recognize the scanner. Many thanks to everyone who contributed. 

It really shouldn't be this hard.

---

### Post by jukingeo on 2017-05-25
Hello All,

I am having a similar problem with a Brother MFC-7440N.  Using the Brother install tool, I can get the printer to work via the network connection...however, I could only get the scanner to work via the USB connection.  I would like to fix this so the scanner will work across the network too so this way I do not have two wires to hook up to my computer.

I am using 64 bit Ubuntu Studio 16.04.

Any assistance would be appreciated.

---

### Post by sp40140 on 2017-05-26
> **jukingeo said:**
> Hello All,

I am having a similar problem with a Brother MFC-7440N.  Using the Brother install tool, I can get the printer to work via the network connection...however, I could only get the scanner to work via the USB connection.  I would like to fix this so the scanner will work across the network too so this way I do not have two wires to hook up to my computer.

I am using 64 bit Ubuntu Studio 16.04.

Any assistance would be appreciated.
There is very good documentation on Brother site, but it's scattered all over (as other kind spirit here told me).
So, What have you tried so far (other than running the install tool)? Example: have you installed correct version of libusb? Have you updated the 40-libsane.rules/60-libsane.rules? Have you tried xsane? Or "gksudo simple-scan"?

---

### Post by jfeole on 2017-05-27
I found this website useful in trying to debug scanner issues with Brother equipment:

[https://wiki.ubuntuusers.de/Scanner/Brother/](https://wiki.ubuntuusers.de/Scanner/Brother/)

---

### Post by kurt18947 on 2017-05-27
> **jukingeo said:**
> Hello All,

I am having a similar problem with a Brother MFC-7440N.  Using the Brother install tool, I can get the printer to work via the network connection...however, I could only get the scanner to work via the USB connection.  I would like to fix this so the scanner will work across the network too so this way I do not have two wires to hook up to my computer.

I am using 64 bit Ubuntu Studio 16.04.

Any assistance would be appreciated.[INDENT]
Have you performed this step?

[/INDENT]
Step 5. Setting for your network scanner[HR][/HR] *****Use brsaneconfig (for brscan models), brsaneconfig2 (for brscan2  models), brsaneconfig3 (for brscan3 models) or brsaneconfig4 (for  brscan4 models) accordingly.**[HR][/HR]5-1. Add network scanner entry Command  :  brsaneconfig2  -a  name=(name  your  device)  model=(model  name)  ip=xx.xx.xx.xx
 [Example]("http://support.brother.com/g/s/id/linux/en/instruction_scn1b.html?c=us_ot&lang=en&redirect=on#config1")

5-2. Confirm network scanner entry Command  :  brsaneconfig2  -q  |  grep  (name  of  your  device) 
[Example]("http://support.brother.com/g/s/id/linux/en/instruction_scn1b.html?c=us_ot&lang=en&redirect=on#config2")[INDENT]
[/INDENT]

---

### Post by jukingeo on 2017-05-29
> **sp40140 said:**
> There is very good documentation on Brother site, but it's scattered all over (as other kind spirit here told me).
So, What have you tried so far (other than running the install tool)? Example: have you installed correct version of libusb? Have you updated the 40-libsane.rules/60-libsane.rules? Have you tried xsane? Or "gksudo simple-scan"?

In question order:

I believe so, Yes, No and yes.

It works with USB ONLY with simple-scan.  I want it to work over the network connection.

---

### Post by jukingeo on 2017-05-29
> **jfeole said:**
> I found this website useful in trying to debug scanner issues with Brother equipment:

[https://wiki.ubuntuusers.de/Scanner/Brother/](https://wiki.ubuntuusers.de/Scanner/Brother/)


Uhh, yeah.  Is there an English version of that?

---

### Post by jukingeo on 2017-05-29
> **kurt18947 said:**
> [INDENT]
Have you performed this step?

[/INDENT]
Step 5. Setting for your network scanner[HR][/HR] *****Use brsaneconfig (for brscan models), brsaneconfig2 (for brscan2  models), brsaneconfig3 (for brscan3 models) or brsaneconfig4 (for  brscan4 models) accordingly.**[HR][/HR]5-1. Add network scanner entry Command  :  brsaneconfig2  -a  name=(name  your  device)  model=(model  name)  ip=xx.xx.xx.xx
 [Example]("http://support.brother.com/g/s/id/linux/en/instruction_scn1b.html?c=us_ot&lang=en&redirect=on#config1")

5-2. Confirm network scanner entry Command  :  brsaneconfig2  -q  |  grep  (name  of  your  device) 
[Example]("http://support.brother.com/g/s/id/linux/en/instruction_scn1b.html?c=us_ot&lang=en&redirect=on#config2")[INDENT]
[/INDENT]



I followed the instructions on this page:

[https://sites.google.com/site/easylinuxtipsproject/15](https://sites.google.com/site/easylinuxtipsproject/15)

---

### Post by sp40140 on 2017-05-30
> **jukingeo said:**
> In question order:

I believe so, Yes, No and yes.

It works with USB ONLY with simple-scan.  I want it to work over the network connection.

Does that mean that your scanner works currently on linux? (using USB port though)?
And you are just trying to share the scanner over network and that part is giving you trouble?

---

### Post by kurt18947 on 2017-06-03
> **jukingeo said:**
> I followed the instructions on this page:

[https://sites.google.com/site/easylinuxtipsproject/15](https://sites.google.com/site/easylinuxtipsproject/15)

I did not study that site carefully but at first glance it seems much more involved than I've found necessary. I just run the Brother installer script and answer the questions as required. It's been some time since I've done a new install requiring a Brother scanner install so don't remember if it was necessary to run the brsaneconfig command after the Brother installer script or not.

---

### Post by jukingeo on 2017-06-20
> **sp40140 said:**
> Does that mean that your scanner works currently on linux? (using USB port though)?
And you are just trying to share the scanner over network and that part is giving you trouble?

Yes, it does work using the USB port, but it doesn't work over the network.  The printer part though DOES work over the internet.

> **kurt18947 said:**
> I did not study that site carefully but at first glance it seems much more involved than I've found necessary. I just run the Brother installer script and answer the questions as required. It's been some time since I've done a new install requiring a Brother scanner install so don't remember if it was necessary to run the brsaneconfig command after the Brother installer script or not.

I ran the Brother Install Tool and it was pretty straight forward, but as I mentioned above, only the printer works over the internet connection, while the scanner DOES work, it only works on the USB connection ONLY.

Thanx,

Geo

---

### Post by sp40140 on 2017-06-21
Since you are trying to share the scanner over the network, this might not be the correct thread.
Having said that, how are you sharing the scanner over network? (what utility / software are you using?)

---

### Post by jcolton on 2017-07-14
> **sp40140 said:**
> Since you are trying to share the scanner over the network, this might not be the correct thread.
Having said that, how are you sharing the scanner over network? (what utility / software are you using?)

I think that replacing/installing libusb-0.1 will do the trick.  Doing that verified for me to get the scanner detected on the wireless network.

196     sudo  dpkg -r  brscan-skey
197     sudo  dpkg -r  sane-utils
198     sudo  dpkg purge brscan4-0.4.4-3.amd64.deb
203     sudo apt install libusb-0.1
204     sudo  dpkg -i  brscan4-0.4.4-3.amd64.deb
210     brsaneconfig4  -a name="myPrinter" model=MFC-J450DW ip=192.168.0.14
211     xsane

---

### Post by miohr on 2017-09-05
> **SuperFreak said:**
> Great

I have it working. Looks like with 64-bit Ubuntu you have to copy /usr/lib64/sane to /usr/lib/sane for it to work.
see [http://ubuntuforums.org/showthread.php?t=2043258](http://ubuntuforums.org/showthread.php?t=2043258)

This fixed it on my side too!
Printer: Brother MFC-7320
OS: Elementary

---

### Post by Hamburgian on 2017-09-28
I tried all of this and more - nothing worked. In the end I opted to uninstall EVERYTHING to do with sane via SYNAPTIC - choosing the compete uninstall option, wiping the configuration files as well, reinstalled (didn't log out, reboot or anything, then reinstalled the printer and scanner together using the Brother Printer install tool from their website [http://support.brother.com/g/b/countrytop.aspx?c=de&lang=de]("http://support.brother.com/g/b/countrytop.aspx?c=de&lang=de") - 20 minutes from beginning to end.

---

### Post by Glasairman on 2017-10-04
> **him610 said:**
> @SuperFreak


Mine does not have /usr/lib/sane however it has a link  (I never quite understood links)
```
hugh@SN68Sx:~/Downloads/Brother$ ls -l /usr/lib64/sane
total 156
lrwxrwxrwx 1 root root     37 Nov 23 18:58 libsane-brother4.so -> /usr/lib64/sane/libsane-brother4.so.1
lrwxrwxrwx 1 root root     41 Nov 23 18:58 libsane-brother4.so.1 -> /usr/lib64/sane/libsane-brother4.so.1.0.7
-rwxr-xr-x 1 root root 158304 Nov 23 18:58 libsane-brother4.so.1.0.7

```

just do: 

cp -r  /usr/lib64/sane   /usr/lib/

---

### Post by bripoole on 2017-11-10
> **him610 said:**
> I just finished reading all of the non-op problems posted on this page. I am running Xubuntu 16.04 and have a Brother laser MFC7360N, that's a black & white laser printer, scanner, fax, copier machine. I have not yet faxed anything, but all of the other functions work fine. I downloaded the drivers from the Brother support website, followed the instructions found on Brother's pages, and have experienced no problems. 

I just now used Simple Scan to scan a document then print it out. I have never made any tweaks or mods - it all just worked. You all need to make sure you complete the setup in system-config-printer utility (that is what it is called in Xubuntu) correctly. If you don't, your system may not find the the device.
Are you guys sure you are following the install instructions to the letter?

BTW, I have two other machines running Ubuntu 14.04 that use the same MFC7360N without any issues.

Hi

I am new to this Forum, I have the same printer as you, but i cannot scan, it finds the scanner, but it cannot scan
[ATTACH=CONFIG]277479[/ATTACH]

---

### Post by heiko_s on 2018-01-10
Ran into a problem with the Brother MFC-L2700DN - Simple Scan wouldn't recognize the scanner. The printer worked fine, though. As suggested earlier here, all it needed was a link:

```
sudo ln -s /usr/lib64/sane /usr/lib/sane
```

No need to copy the files (as suggested in this thread), just create the link and all is fine.

Thanks!

---

