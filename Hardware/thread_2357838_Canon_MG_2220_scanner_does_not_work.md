---
title: "Canon MG 2220 scanner does not work"
date: 2017-04-06
forum: Hardware
---

### Post by raleigh3 on 2017-04-06
I have a Canon MG 2220 printer and scanner.

Simple scan can not take a scan.

All it does is blink 3 dots like it is trying to do a scan.

What can I check ?

---

### Post by pdc on 2017-04-06
......... if you can paste some commands into the terminal please; ask for help if you need help on that

```
sane-find-scanner
```

```
scanimage -L
```

```
sudo sane-find-scanner
```

```
sudo scanimage -L
```

____________

Canon provide scanner drivers for this printer; you could install those whilst attempting to get the open source driver going ..... Simple Scan uses the open source software; Canon writes their own

get the Canon driver from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100469701.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100469701.html) and click to download and SAVE what will be [COLOR="#008000"]scangearmp-mg2200series-2.00-1-deb.tar.gz[/COLOR]

open a terminal and paste in each command that is below; one by one; and hit the ENTER key after each paste ........

cd Downloads
tar -zxvf scangearmp-mg2200series-2.00-1-deb.tar.gz
cd scangearmp-mg2200series-2.00-1-deb
sudo ./install.sh

_**the key thing is that to run it you need to type or paste**_ ```
scangearmp
``` into the terminal ...... if all good we can show you how to set up a launcher to click on for repeated use

---

### Post by raleigh3 on 2017-04-06
```
found USB scanner (vendor=0x04a9 [Canon], product=0x1760 [MG2200 series]) at libusb:002:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

scanimage -L
device `pixma:04A91760_A17530' is a CANON Canon PIXMA MG2200 Series multi-function peripheral

found USB scanner (vendor=0x04a9 [Canon], product=0x1760 [MG2200 series]) at libusb:002:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

sudo scanimage -L
device `pixma:04A91760_A17530' is a CANON Canon PIXMA MG2200 Series multi-function peripheral
```

I installed the driver.

Simple scan still does not scan.

I can manually scan using the scanner, but would prefer to do it via software.

---

### Post by pdc on 2017-04-07
```
I installed the driver.
```        .......... you mean you installed the Canon driver ......... and when you typed ```
scangearmp
``` ....... in a terminal; and hit the Enter key .......... it didn't load the programme called ScanGearMP

________

for some reason, your system can see the scanner; sane should be able to drive it; but it is not doing so; Simple Scan uses sane; 

so the commands you did were just "asking questions" commands; they should not make sane start working;

__________

The Canon driver only works when you issue the command ```
scangearmp
```            ........ sort of like petrol and diesel ........... they don't make and generally you don't put diesel into petrol engines and vice versa ..............

______

sane (the open source scanning software that should be working); has two releases:

1) the standard
2) development

the development would be worth installing; go to this link [https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git](https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git) and these are the guys that maintain sane; and add new code as new devices are released;

follow the instructions to install it: as I see it, the commands are

```
sudo add-apt-repository ppa:rolfbensch/sane-git
```

```
sudo apt-get update
```

and then your software checker should tell you there is a new version of sane for you to install; or just go to Software Manager to find it and select it ....... if you install it, you could reboot and see if things are any better

---

### Post by raleigh3 on 2017-04-07
In more original post, I did not mention that "Simple Scan" used to work.

Why it stooped working is "one of those mysteries." 

I get "Cannot find available scanners."

Cable may be disconnected blah blah etc.

> **pdc said:**
> ```
I installed the driver.
```        .......... you mean you installed the Canon driver ......... and when you typed ```
scangearmp
``` ....... in a terminal; and hit the Enter key .......... it didn't load the programme called ScanGearMP

________

for some reason, your system can see the scanner; sane should be able to drive it; but it is not doing so; Simple Scan uses sane; 

so the commands you did were just "asking questions" commands; they should not make sane start working;

__________

The Canon driver only works when you issue the command ```
scangearmp
```            ........ sort of like petrol and diesel ........... they don't make and generally you don't put diesel into petrol engines and vice versa ..............

______

sane (the open source scanning software that should be working); has two releases:

1) the standard
2) development

the development would be worth installing; go to this link [https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git](https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git) and these are the guys that maintain sane; and add new code as new devices are released;

follow the instructions to install it: as I see it, the commands are

```
sudo add-apt-repository ppa:rolfbensch/sane-git
```

```
sudo apt-get update
```

and then your software checker should tell you there is a new version of sane for you to install; or just go to Software Manager to find it and select it ....... if you install it, you could reboot and see if things are any better

Please try to keep it simple. :-)

If my scanner used to work, why did it stopped working ??

I made no changes to my Operating System.

So, I can see no reason why my scanner stopped stopped working.

I am very,very pleased with Ubuntu_Mate.

It has had very,very few hardware issues.

---

### Post by raleigh3 on 2017-04-08
> **pdc said:**
> ```
I installed the driver.
```        .......... you mean you installed the Canon driver ......... and when you typed ```
scangearmp
``` ....... in a terminal; and hit the Enter key .......... it didn't load the programme called ScanGearMP

________

for some reason, your system can see the scanner; sane should be able to drive it; but it is not doing so; Simple Scan uses sane; 

so the commands you did were just "asking questions" commands; they should not make sane start working;

__________

The Canon driver only works when you issue the command ```
scangearmp
```            ........ sort of like petrol and diesel ........... they don't make and generally you don't put diesel into petrol engines and vice versa ..............

______

sane (the open source scanning software that should be working); has two releases:

1) the standard
2) development

the development would be worth installing; go to this link [https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git](https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git) and these are the guys that maintain sane; and add new code as new devices are released;

follow the instructions to install it: as I see it, the commands are

```
sudo add-apt-repository ppa:rolfbensch/sane-git
```

```
sudo apt-get update
```

and then your software checker should tell you there is a new version of sane for you to install; or just go to Software Manager to find it and select it ....... if you install it, you could reboot and see if things are any better

Sorry, I am a little slow sometimes.

Simple scanner does not work, but scangearmp is it's own scanner program.

Thanks a lot. I made a script for it and find a scanner icon.

---

