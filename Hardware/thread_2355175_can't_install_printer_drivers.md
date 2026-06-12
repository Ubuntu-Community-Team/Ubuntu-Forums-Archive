---
title: "can't install printer drivers"
date: 2017-03-09
forum: Hardware
---

### Post by jarp53 on 2017-03-09
i downloaded my drivers from Brothers web site and the instruction says " **Command: bash linux-brprinter-installer-*.*.*-* Brother machine name **[COLOR=#000000][FONT=sans-serif]e.g. bash linux-brprinter-installer-2.1.1-1 MFC-J880DW[/FONT][/COLOR]
but in the terminal i'm told that command not found ; how do i need to write the command to install the driver installer for my printer

---

### Post by kc1di on 2017-03-10
Hello jarp53 and welcome to Ubuntu,

You need to be in the same directory where you downloaded the file. 
if it's in the Download folder you need to "cd" to that folder similar to this:
```
cd /home/<usrname/Downloads
```
Then issue the ls command ```
ls
```
and copy the filename exactly as it is given in the command you issue to exicute it. 

You did not say which Brother printer your trying to set up. It may be that ubuntu repositories already have that driver available and if so
it would be advised to install it from there. 
Good Luck

---

### Post by jarp53 on 2017-03-10
thanks for replying :  ok this i did  
```
 <  jr@jr-Z68X-UD3H-B3:~/Downloads$ bash linux-brprinter-installer-2.1.1-1 MFC-5890CNOnly root can perform this operation. >
```
so then i did  
```
<  jr@jr-Z68X-UD3H-B3:~/Downloads$ sudo install linux-brprinter-installer-2.1.1-1 MFC-5890CN  >
```
and nothing ; and yeah i have an older printer that is why the drivers are not available , the ones that are start for models in the 70.. series and up ; i had no problem installing them in Deepin , well it was easy you just click " Run " so i know this are the right drivers for me. 































mint

---

### Post by pdc on 2017-03-10
Hi jarp;

so if you are "in" the Downloads directory; and [COLOR="#008000"]linux-brprinter-installer-2.1.1-1.gz[/COLOR] is safely there ........ you can tell by typing ```
ls
```  ........ as that command asks your computer to **LIST** what is in that directory ............   ls=LIST ......

then the commands would be

```
gunzip linux-brprinter-installer-2.1.1-1.gz
```      ........ so that unpacks the compressed file you downloaded and

```
sudo bash linux-brprinter-installer-2.1.1-1 MFC-5890CN
```            ...... that should unleash the install script ........ so have your sudo password ready ....... and also be able to tell the script if your printer is usb or network: it will ask you ...... if network, the options it may give you may well be options 10 or 12 or 13 ......

---

### Post by cariboo on 2017-03-10
There are some spaces in the driver name, so you may have use the following command:

```
sudo bash "linux-brprinter-installer-2.1.1-1 MFC-5890CN"
```

Linux doesn't like spaces in a command in a terminal.

---

### Post by pdc on 2017-03-10
thanks cariboo for your comments; this is yet another topic I need to go away and learn about! The reason I quoted it as I did, was that was what Brother puts on their download page; as per the enclosed thumbnail

I understand that if one just issues the command "sudo bash linux-brprinter-installer-2.1.1-1" that the installer merely identifies how many Brother printers are connected; if only one, it asks if that is the one you want installed ...... so the model number is actually optional  .. but I always quote as Brother suggest it

---

### Post by jarp53 on 2017-03-10
thank you all  for your help , I've  got a printer ; unfortunately no scanner , simple scan , and Xsane image scanner can't find the scanner, i check and all the drivers were install , so here as a good lesson for me, how do i type a command to make my printer scan

---

### Post by pdc on 2017-03-11
we have at least one other thread ongoing in this forum; where a Brother MFD will not scan from ubuntu; ........ 

1) please tell us if your connection is usb;

2) if networked, could you paste this command into a terminal please ```
lpinfo -v
``` and if you could copy and paste the result back here please; 

3) and is your system 32bit?

4) can you paste ```
sane-find-scanner
``` and ```
sudo sane-find-scanner
``` and give us the results and 

5) ```
scanimage -L
``` and ```
sudo scanimage -L
```

---

### Post by cariboo on 2017-03-11
I had a look for drivers on the Brother web site, and I found this:

[http://support.brother.com/g/b/downloadlist.aspx?c=ca&lang=en&prod=mfc5890cn_all&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=ca&lang=en&prod=mfc5890cn_all&os=128)

scroll down to the scanner drivers and take your pick.

---

### Post by pdc on 2017-03-11
I guess the hope was cariboo that the "brother installer tool" would install both the printer drivers and the scanner drivers; ....... I am thinking it should ................

when we find out if jarp53 has 32bit; or 64bit; we can find do a ```
dpkg -l brscan*
``` to see what is installed; ...........or if jarp spots this .......... he could just run the command anyway ...............

---

### Post by jarp53 on 2017-03-11
thanks Cariboo i have the correct drivers install for the scanner , i know this because they work when i was running Deepin. 
here you go pdc : yes printer is usb connected 
2-jr@jr-Z68X-UD3H-B3:~$ lpinfo -vnetwork ipps
network ipp
network lpd
network beh
network http
direct hp
network ipp14
serial serial:/dev/ttyS0?baud=115200
network https
network socket
direct usb://Brother/MFC-5890CN?serial=BROE0F358610
direct hpfax
jr@jr-Z68X-UD3H-B3:~$ 


3- no 64bit
4  r@jr-Z68X-UD3H-B3:~$ sudo sane-find-scanner
[sudo] password for jr: 


  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.


  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.


could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
found USB scanner (vendor=0x04f9 [Brother], product=0x01f4 [MFC-5890CN]) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.


  # Not checking for parallel port scanners.


  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
5- 
jr@jr-Z68X-UD3H-B3:~$ scanimage -L


No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
jr@jr-Z68X-UD3H-B3:~$ sudo scanimage -L
[sudo] password for jr: 


No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
jr@jr-Z68X-UD3H-B3:~$

---

### Post by pdc on 2017-03-11
so I was checking through the Brother documentation: [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on)

and we had best try getting you to follow all of Brother's various bits of advice: but if you feel able to open the directories that they should be in; and verify they are already there; (as the installer tool might have placed them):

so from the Brother recommendations, if we do several things:

1) ```
sudo apt-get install libusb-0.1-4
```       [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00107](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00107)

2) ```
sudo cp /usr/lib64/sane/libsane-brother* /usr/lib/x86_64-linux-gnu/sane
```  [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00108](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00108)

3) Copy the following files under /usr/lib64/ to /usr/lib/ [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101)

```
cp /usr/lib64/libbrscandec3.so.1.0.0 /usr/lib
```
```
cp /usr/lib64/sane/libsane-brother3.so.1.0.7 /usr/lib/sane
```
```
cp /usr/lib64/sane/libsane-brother3.so.1 /usr/lib/sane
```
```
cp /usr/lib64/sane/libsane-brother3.so /usr/lib/sane
```
```
cp /usr/lib64/libbrscandec3.so /usr/lib
```
```
cp /usr/lib64/libbrscandec3.so.1 /usr/lib
```

4) download and install the permissions file: it is a very small deb file [http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04) ....... you will be downloading brother-udev-rule-type1-1.0.0-1.all.deb and if you click to download; and select "open" gdebi installer with luck will leap in and install it for you; if not, and it ends up in your Downloads folder, change directory to there (cd Downloads) and install with 

```
sudo dpkg -i brother-udev-rule-type1-1.0.0-1.all.deb
```

....... reboot ........ any joy?

---

### Post by jarp53 on 2017-03-11
i don't understand what happen but i did replay and run all the codes you ask me so i'll do it again ; but right now my system is 64 bit.

jr@jr-Z68X-UD3H-B3:~$ dpkg -l brscan*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  brscan         <none>       <none>       (no description available)
ii  brscan-skey    0.2.4-1      amd64        Brother Linux scanner S-KEY tool
ii  brscan3        0.2.13-1     amd64        Brother Scanner Driver
jr@jr-Z68X-UD3H-B3:~$

when i try to do step 3,  i get this :  jr@jr-Z68X-UD3H-B3:~$ cp /usr/lib64/libbrscandec3.so.1.0.0 /usr/libcp: cannot create regular file '/usr/lib/libbrscandec3.so.1.0.0': Permission denied

---

### Post by pdc on 2017-03-13
so if you get permission denied, best use the sudo prefix so each of those copy commands would start with sudo ........ ie ..............as in 2)

...... Brother were "relaxed" in the copy commands in 3) ....... and I missed it ......... all of those should have sudo at the front of them ...... just like 2) does ............

and 4) is important too ............

---

### Post by jarp53 on 2017-03-13
thank you very much , this was a great experience by giving me an  insight on how to use the Terminal , and of course making my Ubuntu a little more  pleasant .

---

### Post by pdc on 2017-03-13
well done: you did well: enjoy now!

---

