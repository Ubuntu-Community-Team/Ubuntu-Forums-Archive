---
title: "Brother MFC-465CN"
date: 2008-10-04
forum: Hardware
---

### Post by Robor on 2008-10-04
**** Thank you to froy02 and AgentZ86 for the original assistance thread ****

Just picked up one of these all-in-one units and tried to get it working.  It was detected fine but the driver wasn't available so I did some searching and found this helpful thread:  [**_LINK_**]("http://ubuntuforums.org/showthread.php?t=678407")  

I'll expand on it a bit to include my experience...

1.  Went to  [http://solutions.brother.com/linux/en_us/index.html]("http://solutions.brother.com/linux/en_us/index.html")  and downloaded the appropriate driver and wrapper files.

2.  Navigated to where the LPR driver file was saved and issued the following command:

```
sudo dpkg -i --force-all --force-architecture mfc465cnlpr-1.0.1-1.i386.deb
```

That resulted in a path related error below

> mkdir: cannot create directory `/var/spool/lpd/mfc465cn': No such file or directory
chown: cannot access `/var/spool/lpd/mfc465cn': No such file or directory
chgrp: cannot access `/var/spool/lpd/mfc465cn': No such file or directory
chmod: cannot access `/var/spool/lpd/mfc465cn': No such file or directory


3.  Navigated to /var/spool and created a 'lpd' directory to correct the missing path then re-ran the driver install successfully.

```

cd /var/spool
sudo mkdir lpd
```

4.  Navigated back to where the LPR driver file was saved and repeated the command in Step 2 and it was successful (no path error).


5.  Navigated back to where the wrapper file was saved and issued the following command:

```
sudo dpkg -i --force-all --force-architecture mfc465cncupswrapper-1.0.1-1.i386.deb
```

This resulted in another path error.

> /usr/local/Brother/Printer/mfc465cn/cupswrapper/cupswrappermfc465cn: 70: cannot create /usr/share/cups/model/brmfc465cn.ppd: Directory nonexistent
/usr/local/Brother/Printer/mfc465cn/cupswrapper/cupswrappermfc465cn: 274: cannot create /usr/share/cups/model/brmfc465cn.ppd: Directory nonexistent
chmod: cannot access `/usr/share/cups/model/brmfc465cn.ppd': No such file or directory
cp: cannot stat `/usr/share/cups/model/brmfc465cn.ppd': No such file or directory
chmod: cannot access `/usr/share/ppd/brmfc465cn.ppd': No such file or directory
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
lpadmin: Unable to copy PPD file!

6.  Navigated to /var/spool and created a 'lpd' directory to correct the missing path then re-ran the driver install successfully.

```

cd /usr/share/cups
sudo mkdir model
```

7.  Navigated back to where the wrapper file was saved and repeated the command in Step 5 and it was successful (no path error).

8.  Ran printer install procedure (System | Administration | Printing) and the Brother MFC-465MVC driver was available and worked.

I haven't tried the scanner portion yet.  Will do and if there are any differences outside of the original thread at the top I'll follow up and edit this post.

---

### Post by 007casper on 2010-05-04
awesome!  Thank you so much.  Printer works without a problem.

Thank you again

---

### Post by 007casper on 2010-05-22
on MFC-465CN I cant get the scanner to work.  I tried Simple Scan, and the XSane Image Scanner.  

Simple Scan says> 
No Scanners detected
Please check your scanner is connected and power on

Failed to scan
No scanners available.  Please connect a scanner.

XSane Image Scanner says 

> no device available

However, it does print, so it is connected.

?

Please, advise.  Thank you.

---

### Post by migs73 on 2010-05-24
007,
Did you download the scanner drivers from Brother as well?
If you follow the instructions on their website it should work (I did it couple of weeks ago for my MFC-255CW on Lucid and it worked fine). The only thing I would say you should do is check the prerequisites for your distro (listed on the brother site), but I think the only pre requisite is that sane-utils is required to be installed.
Once you have checked/done this download the scanner driver (brscan2 and the scan-key-tool for your machine I think). 
When you go to the download page it states to right click and save as, then you have to cd into the directory and move it to the right one etc.,, I found if you just download it (just click on the I Accept button)ubuntu asks if you want to open it with Gdebi installer. Just click yes and it puts it in the right place anyway (this worked for the printer drivers too, but you still have to manually make two directories before hand).
Then follow the instructions from step 5.

---

### Post by wojox on 2010-05-24
> **migs73 said:**
> 007,
Did you download the scanner drivers from Brother as well?
If you follow the instructions on their website it should work (I did it couple of weeks ago for my MFC-255CW on Lucid and it worked fine). The only thing I would say you should do is check the prerequisites for your distro (listed on the brother site), but I think the only pre requisite is that sane-utils is required to be installed.
Once you have checked/done this download the scanner driver (brscan2 and the scan-key-tool for your machine I think). 
When you go to the download page it states to right click and save as, then you have to cd into the directory and move it to the right one etc.,, I found if you just download it (just click on the I Accept button)ubuntu asks if you want to open it with Gdebi installer. Just click yes and it puts it in the right place anyway (this worked for the printer drivers too, but you still have to manually make two directories before hand).
Then follow the instructions from step 5.

Really they have different drivers for the scanner?

---

### Post by migs73 on 2010-05-24
Now,now, there is no need for that!!

I have to ask, mainly because if you try to follow the Brother website, you can end up going round in circles. It is a great resource, but the links are difficult to follow, and the prerequisite part is easy to miss (I did at first, I just bashed on and downloaded the drivers).

---

### Post by YMS_1975 on 2011-12-18
I'm in the same predicament. Running Ubuntu 11.10, and can't get my MFC-465CN's instructions to a tee. The printer works just fine but the scanner gives the following error message something to the effect of : ""Failed to open dvice `brother2:bus3;dev1': Invalid argument".

I've seen this error message somewhere else on this site but it never lead to a solution. Any........ways, can someone help?

Has this been resolved?

---

### Post by tcchris on 2011-12-18
The printer drivers are in the repo , no need for downloading at the brother site

---

### Post by mörgæs on 2011-12-18
Though old the thread still seems valid. Moved to Hardware and Laptops.

---

### Post by YMS_1975 on 2011-12-21
> **tcchris said:**
> The printer drivers are in the repo , no need for downloading at the brother site

Perhaps I'm misunderstanding how the "repo" works. If its in the repo, shouldn't it just be a matter of going to the software centre, installing it and having it run straight out of the box? (relatively speaking).

---

### Post by 007casper on 2012-02-21
does Brother MFC-465CN driver from the repo doesnt include the scanner driver?

because I loaded Brother MFC-465CN from the repo.  And then I installed xsane.  It doesnt work.  I clicked on help.

> 
no devices available
Possible reasons
1- There really is no device that is supported by SANE
2- Supported devices are busy
3- The permissions for the device file do not allow you to use it-try as root
4- the backend is not loaded by sane(man sane-dll)
5- the backend is not configured correctly (man sane-"backendname")
6- possibly there is more than one sane version installed


1- MFC-465CN is not on the list of unsupported ???
[http://www.sane-project.org/sane-mfgs.html#Z-BROTHER](http://www.sane-project.org/sane-mfgs.html#Z-BROTHER)

2- device isnt busy

3- permissions are approved

4- ?
5- downloaded from repo ?
6- no other sane version installed

????

how can I use the scanner?

---

### Post by 007casper on 2012-02-21
> puter@puter-laptop:~$ dpkg  -l  |  grep  Brother
ii  brother-cups-wrapper-common            1.0.0-10-0ubuntu5                          Common files for Brother cups wrapper packages
ii  brscan                                 0.2.4                                      Brother CUPS Printer Definitions
ii  brscan-skey                            0.2.1-3                                    Brother Linux scanner S-KEY tool
rc  mfc465cnlpr                            1.0.1-1                                    Brother lpr Inkjet Printer Definitions
ii  ptouch-driver                          1.3-0ubuntu11                              CUPS/Foomatic driver for Brother P-touch label printers
puter@puter-laptop:~$ brscan-skey  -l

puter@puter-laptop:~$ brscan-skey
puter@puter-laptop:~$


??

---

### Post by 007casper on 2012-02-21
> puter@puter-laptop:~$ brscan-skey -l

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn3.html#config2](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn3.html#config2)

it doesnt see the scanner

??

trying to make the scanner work on 11.10

---

### Post by YMS_1975 on 2012-02-21
That's the exact same problem I'm having. Printer works fine, but scanner not recognized at all.

:-(

---

### Post by plucky on 2012-02-21
> **007casper said:**
> [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn3.html#config2](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn3.html#config2)

it doesnt see the scanner

??

trying to make the scanner work on 11.10

You need to download and install the brscan2 deb file from the Brother website.Follow the installation instructions on the website.

The Scan-key tool is only used when you press the Scan Button on your printer will cause the scanner software to launch.

Good Luck

---

### Post by 007casper on 2012-02-21
I did load brscan2.

I launched xsane.  I got

```
Failed to open device 'brother2:bus2;dev1'
Invalid argument

```

```

puter@puter-laptop:~$ dpkg -l | grep Brother
ii  brother-cups-wrapper-common            1.0.0-10-0ubuntu5                          Common files for Brother cups wrapper packages
ii  brscan                                 0.2.4                                      Brother CUPS Printer Definitions
ii  brscan-skey                            0.2.1-3                                    Brother Linux scanner S-KEY tool
ii  brscan2                                0.2.5-1                                    Brother Scanner Driver
rc  mfc465cnlpr                            1.0.1-1                                    Brother lpr Inkjet Printer Definitions
ii  ptouch-driver                          1.3-0ubuntu11                              CUPS/Foomatic driver for Brother P-touch label printers
puter@puter-laptop:~$ brscan-skey -l

 MFC-465CN         : brother2:bus2;dev1  : USB                  Not registered
puter@puter-laptop:~$ 

```

---

### Post by plucky on 2012-02-21
Did you edit the file "/lib/udev/rules.d/40-libsane.rules"

See [Here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10)

Also install sane-utils.

Then reboot and try Simple Scan.

Good Luck

---

### Post by 007casper on 2012-02-21
Awesome!  Thank you!  Thank you so much.

Now scanner works.

---

