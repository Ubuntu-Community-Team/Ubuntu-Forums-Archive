---
title: "Ubuntu 10.04 Canon IP2600 Printer How-To"
date: 2010-05-24
forum: Hardware
---

### Post by MillDaKill on 2010-05-24
**Summery:**
If you are like me and you own a Canon IP2600 printer you have probably found out that Ubuntu 10.04 does not set it up automagically.  After doing a little reading and some trial and error I have figured out how to get it to work and I wanted to share  my solution with you all.  There is a good chance that if there are other Canon IPXXXX printers that are not supported in Ubuntu 10.04 that following steps similar to the ones I am giving for the IP2600 will work (YMMV and not tested).

**Notes:**
1.) I have only followed these steps on Ubuntu 10.04

2.) The computer I did it on was a 32bit machine

3.) Do not follow these steps on any kind of mission critical or production machine, spend the money and get a better supported printer.

4.) It is probably wise to make sure you have a backup of important files on your computer.  This guide worked for me but it has not been rigorously tested by any means.

**How-To:**
0.) Read all 10 steps listed below before you start.  If you are a trusting person, there is a shortcut on step 3 that can save you 10-20 minutes worth of work.

1.) Download the Canon IP2600 drivers from [**HERE**]("http://software.canon-europe.com/software/0034312.asp?model=").  The file should be called iP2600_debiang.tgz .

2.) Unzip and un-archive iP2600_debiang.tgz

3.) Now the fun part...  The .deb files included in the iP2600_debiang.tgz were built for an older version of ubuntu which reference a package called "cupsyslib2".  This old package has been since renamed to "cupslib2" so we will have to re-build the .deb packages.  There is a good guide on how to re-create the .debs [**HERE**]("http://ubuntuforums.org/showthread.php?t=110458") .  Follow the guide in the link and when you edit the list of dependencies replace all "cupsyslib2" with "cupslib2".  If you are a trusting person and you do not want to re-build your own .deb files I have uploaded the files I customized to mediafire.

[**cnijfilter-common_2.90-1_i386_1004customized.deb**]("http://www.mediafire.com/?nmzgan1mnqz")

[**cnijfilter-ip2600series_2.90-1_i386_1004customized.deb**]("http://www.mediafire.com/?x1jnuztgo5y")


4.) Install customized "common" deb 
```
sudo dpkg -i cnijfilter-common_2.90-1_i386_1004customized.deb
```

5.) Install customized "ip2600series" deb  
```
sudo dpkg -i cnijfilter-ip2600series_2.90-1_i386_1004customized.deb
```

6.) Chown /usr/lib/cups/filter/pstocanonij to root:root
```
sudo chown root:root /usr/lib/cups/filter/pstocanonij
```

7.) Restart your computer

8.) Install the printer in Gnome via the menus at the top of your screen "System -> Administration -> Printers"

9.) Print a test page

10.) If you follow this guide, please let me know if it worked for you

---

### Post by Palanthas on 2010-06-09
Do you have a 64bit howto as well? lol, I was/am all excited about getting my iP2600 working and had all the files ready to go (used your's btw) but when I ran the first command it comes back with...

```
david@david-server:~$ sudo dpkg -i cnijfilter-common_2.90-1_i386_1004customized.deb
dpkg: error processing cnijfilter-common_2.90-1_i386_1004customized.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 cnijfilter-common_2.90-1_i386_1004customized.deb
david@david-server:~$ 

```

---

### Post by Ellio-pc on 2010-06-11
Thank you Milldakill I can now use my printer. I have so far only printed a test page but everything installed and worked flawlessly. Many thanks.

---

### Post by issachan on 2010-06-12
Oh thank you for the instructions! My printer is working finally! I was beginning to think I had a giant paper weight and would have to buy a new printer right away. 

The only problem I have with the printer is that it doesn't recognize that it has paper so it's constantly stopping and complaining it has no paper. 

Anyway, thank you so much!! You're awesome!  =D>

---

### Post by nickytchao on 2010-06-15
I all!
first, I wanna thank issachan fot his post and his files!
Then I want to bring a good new for Palanthas and all the others that have a 64 bits machine with an ip2600.
to be simple, just take the files and use dpkg -i --force-architecture to install the .deb!
That's all!

Excuse me fot my english and thank you again!

---

### Post by headmower on 2010-06-22
Many thanks to MillDaKill, I  used the download links for my canon ip2600 printer. First I saved the downloads and in stalled them with the g-deb installer and then used the sudo root command you supplied and my printer works just fine. This was the easiest install on ubuntu so far.   [email]headmower@gmail.com[/email]:guitar:):P

---

### Post by Pete051 on 2010-07-30
I found I was getting an "insecure cups filter" warning that refused to allow it to print but this turned out to be the files 
/usr/lib/cups/filter/pstocanonij
and 
/usr/lib/cups/backend/cnij_usb
had the wrong group and owner, this was solved by:
sudo chgrp root /usr/lib/cups/backend/cnij_usb
sudo chown root /usr/lib/cups/backend/cnij_usb
sudo chgrp root /usr/lib/cups/filter/pstocanonij
sudo chown root /usr/lib/cups/filter/pstocanonij

and now it works :)

---

### Post by rubini on 2010-08-25
Hello,

I did the repackaging and installed the drivers successfully. I checked the links with ldd cifip2600 and linked the libs that were missing. And I chmoded the cups directories like indicated.

But unfortunately my Canon IP2600 is still not printing.
When sending a job to the printer the printer's green light flashes once and cups tells me that it has printed: (from /var/log/cups/access.log)
```
"POST /printers/iP2600-series HTTP/1.1" 200 205766 Print-Job successful-ok

```

the /var/log/cups/error.log is not showing any errors.

Is there any kind person who could help me troubleshooting this?

Thank you,
Rubén

---

### Post by Anissita on 2010-08-27
Thanks!.
It saved me a lot of work.

---

### Post by roboghast on 2010-08-29
moosh@moosh-desktop:~$ sudo dpkg -i cnijfilter-common_2.90-1_i386_1004customized.deb
dpkg: error processing cnijfilter-common_2.90-1_i386_1004customized.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 cnijfilter-common_2.90-1_i386_1004customized.deb
moosh@moosh-desktop:~$ sudo dpkg -i cnijfilter-ip2600series_2.90-1_i386_1004customized.deb
dpkg: error processing cnijfilter-ip2600series_2.90-1_i386_1004customized.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 cnijfilter-ip2600series_2.90-1_i386_1004customized.deb
moosh@moosh-desktop:~$ 

your solution fails

---

### Post by maraballerina on 2010-08-31
Thank you so much for this!  I was able to install it on my 64-bit using the force-architecture and it worked flawlessly!

---

### Post by steevven1 on 2010-09-09
THANK YOU SO MUCH. This worked flawlessly. I used your pre-compiled deb files from mediafire.

This printer has been driving me crazy for weeks.

---

### Post by jlangholzj on 2010-09-13
worked with my lucid!!!

thank you sir for your hard work and effort!):P

---

### Post by colski on 2010-09-17
Worked flawlessly for me on 32 bit lucid.

Thanks!

---

### Post by Sixdown on 2010-09-24
Thank you! :)  Works perfectly in x64.  Used uploaded files and just had to force-architecture.

4.) ```
sudo dpkg -i --force-architecture cnijfilter-common_2.90-1_i386_1004customized.deb
```

AND

5.) ```
sudo dpkg -i --force-architecture cnijfilter-ip2600series_2.90-1_i386_1004customized.deb
```

Make sure you're in the same directory as the two files.

---

### Post by welshmike on 2010-10-11
MillDaKill,

Thank you very much.
I followed your instructions and downloaded your customized deb files.
My Canon iP2600 is now printing.

Mike

---

### Post by -TopGun- on 2010-10-19
> **Palanthas said:**
> Do you have a 64bit howto as well? lol, I was/am all excited about getting my iP2600 working and had all the files ready to go (used your's btw) but when I ran the first command it comes back with...

```
david@david-server:~$ sudo dpkg -i cnijfilter-common_2.90-1_i386_1004customized.deb
dpkg: error processing cnijfilter-common_2.90-1_i386_1004customized.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 cnijfilter-common_2.90-1_i386_1004customized.deb
david@david-server:~$ 

```

It works using --force in the syntax for both the steps [MillDaKill  ]("http://ubuntuforums.org/member.php?u=113367")explained in the best way possible in points 4 and 5
[]("http://ubuntuforums.org/member.php?u=113367") 				 				 			
 
```
dpkg -i --force-architecture cnijfilter-ip2600series_2.90-1_i386_1004customized.deb

```same commands adding --force-architecture

It works very good under Debian Squeeze Amd64.

---

### Post by fourstringin on 2010-11-02
Worked great

---

### Post by sporez on 2010-11-21
Is there some reason that these drivers would not work with 10.10?  I was successful in getting my IP2600 printer working in 10.04 but cannot in 10.10.

---

### Post by -TopGun- on 2010-11-21
> **sporez said:**
> Is there some reason that these drivers would not work with 10.10?  I was successful in getting my IP2600 printer working in 10.04 but cannot in 10.10.

May be this is due to an another change in lib name?
You have to verify this.

---

### Post by sporez on 2010-11-21
> **-TopGun- said:**
> May be this is due to an another change in lib name?
You have to verify this.

Well, they install fine, but when I go to add the printer it acts as if there have been no drivers installed.

---

### Post by -TopGun- on 2010-11-21
> **sporez said:**
> Well, they install fine, but when I go to add the printer it acts as if there have been no drivers installed.

Try doing some steps back, and check it all again.
May be you have done a mistake in the installation process.

keep in touch. :)

---

### Post by sporez on 2010-11-21
> **-TopGun- said:**
> Try doing some steps back, and check it all again.
May be you have done a mistake in the installation process.

keep in touch. :)

Okay, I just uninstalled both packages and then reinstalled.  I rebooted and then tried to add the printer.  It does a quick search for drivers and then brings up a "choose driver" page, as if no driver was installed.

---

### Post by -TopGun- on 2010-11-21
> **sporez said:**
> Okay, I just uninstalled both packages and then reinstalled.  I rebooted and then tried to add the printer.  It does a quick search for drivers and then brings up a "choose driver" page, as if no driver was installed.

At Moment I'm on Debian Amd 64 (squeeze) and I'm really fine with this drivers.
I don't know what's up. I think there is a change in the name libs, as it happens in the past.

You could send a pvt to MillDakill, he is surelly the best user to ask help in this issue.

---

### Post by sporez on 2010-11-21
> **-TopGun- said:**
> At Moment I'm on Debian Amd 64 (squeeze) and I'm really fine with this drivers.
I don't know what's up. I think there is a change in the name libs, as it happens in the past.

You could send a pvt to MillDakill, he is surelly the best user to ask help in this issue.

okay i will send a message to MillDakill.

Wouldn't I get some kind of error when installing them if the name of libs had changed?

---

### Post by -TopGun- on 2010-11-21
> **sporez said:**
> okay i will send a message to MillDakill.

Wouldn't I get some kind of error when installing them if the name of libs had changed?


I don't know.
He repacked the drivers for this reason, the cuplibs2 changed name.

---

### Post by nemoskull on 2010-12-05
nope, didnt work for me. just sits there. ubuntu says 'job submitted as job 10" and does absolutly nothing. it back to 'paperweight' for me.
waste of time......

---

### Post by welshmike on 2010-12-12
MillDaKill,

Thank you very much again.
I followed your instructions after I had to reinstall 10.04 and then downloaded your customized deb files.
My Canon iP2600 is now printing.

---

### Post by gwfran on 2010-12-30
> **MillDaKill said:**
> **Summery:**
If you are like me and you own a Canon IP2600 printer you have probably found out that Ubuntu 10.04 does not set it up automagically.  After doing a little reading and some trial and error I have figured out how to get it to work and I wanted to share  my solution with you all.  There is a good chance that if there are other Canon IPXXXX printers that are not supported in Ubuntu 10.04 that following steps similar to the ones I am giving for the IP2600 will work (YMMV and not tested).

**Notes:**
1.) I have only followed these steps on Ubuntu 10.04

2.) The computer I did it on was a 32bit machine

3.) Do not follow these steps on any kind of mission critical or production machine, spend the money and get a better supported printer.

4.) It is probably wise to make sure you have a backup of important files on your computer.  This guide worked for me but it has not been rigorously tested by any means.

**How-To:**
0.) Read all 10 steps listed below before you start.  If you are a trusting person, there is a shortcut on step 3 that can save you 10-20 minutes worth of work.

1.) Download the Canon IP2600 drivers from [**HERE**]("http://software.canon-europe.com/software/0034312.asp?model=").  The file should be called iP2600_debiang.tgz .

2.) Unzip and un-archive iP2600_debiang.tgz

3.) Now the fun part...  The .deb files included in the iP2600_debiang.tgz were built for an older version of ubuntu which reference a package called "cupsyslib2".  This old package has been since renamed to "cupslib2" so we will have to re-build the .deb packages.  There is a good guide on how to re-create the .debs [**HERE**]("http://ubuntuforums.org/showthread.php?t=110458") .  Follow the guide in the link and when you edit the list of dependencies replace all "cupsyslib2" with "cupslib2".  If you are a trusting person and you do not want to re-build your own .deb files I have uploaded the files I customized to mediafire.

[**cnijfilter-common_2.90-1_i386_1004customized.deb**]("http://www.mediafire.com/?nmzgan1mnqz")

[**cnijfilter-ip2600series_2.90-1_i386_1004customized.deb**]("http://www.mediafire.com/?x1jnuztgo5y")


4.) Install customized "common" deb 
```
sudo dpkg -i cnijfilter-common_2.90-1_i386_1004customized.deb
```5.) Install customized "ip2600series" deb  
```
sudo dpkg -i cnijfilter-ip2600series_2.90-1_i386_1004customized.deb
```6.) Chown /usr/lib/cups/filter/pstocanonij to root:root
```
sudo chown root:root /usr/lib/cups/filter/pstocanonij
```7.) Restart your computer

8.) Install the printer in Gnome via the menus at the top of your screen "System -> Administration -> Printers"

9.) Print a test page

10.) If you follow this guide, please let me know if it worked for you


Thanks MillDaKill!  You saved me a ton of time and effort!

---

### Post by The Other Steve on 2011-01-15
> **MillDaKill said:**
> If you follow this guide, please let me know if it worked for you
Yes, it worked for me.  On a 64-bit system.  Thank you for posting.

For whatever reason(s), I was not able to modify/rebuild the deb files myself.  Among the slew of annoying errors was a permissions problem I could not overcome.

But the downloaded files worked.  Thank you for those (Dear God, I hope I have not just installed a keylogger. :-) )

I believe there is a typo in the directions, Step 3.  The files you mention are "cupsyslib2" and "cupslib2".  I believe the correct filenames are "libcupsys2" and "libcups2".

It's very nice to get the ip2600 working.  Thank you.  What I need now is a better print-manager, though.  The Windows manager provided options for color/greyscale/draft, and so on.

---

### Post by The Other Steve on 2011-01-15
> **roboghast said:**
> 
dpkg: error processing cnijfilter-common_2.90-1_i386_1004customized.deb (--install):
 cannot access archive: No such file or directory

You may get that error if the directory you are working in does not contain the files.

---

### Post by chefmikeb on 2011-01-23
Thank you.  This, along with your clear instructions helped me get my printer up and running.  I've installed xubuntu on an older Dell Desktop and getting everything set up for my niece.  This was a huge help.  Thank you for spending the time to do this.

---

### Post by Selaro on 2011-02-16
Thanks a million, after hours of searching and trying different solutions yours worked!!!!!! One note, I copied your files to desktop and then in terminal I changed the directory to desktop cd Desktop. Great job...

---

### Post by stmcc on 2011-03-31
> **MillDaKill said:**
> **Summery:**
If you are like me and you own a Canon IP2600 printer you have probably found out that Ubuntu 10.04 does not set it up automagically.  After doing a little reading and some trial and error I have figured out how to get it to work and I wanted to share  my solution with you all.  There is a good chance that if there are other Canon IPXXXX printers that are not supported in Ubuntu 10.04 that following steps similar to the ones I am giving for the IP2600 will work (YMMV and not tested).

**Notes:**
1.) I have only followed these steps on Ubuntu 10.04

2.) The computer I did it on was a 32bit machine

3.) Do not follow these steps on any kind of mission critical or production machine, spend the money and get a better supported printer.

4.) It is probably wise to make sure you have a backup of important files on your computer.  This guide worked for me but it has not been rigorously tested by any means.

**How-To:**
0.) Read all 10 steps listed below before you start.  If you are a trusting person, there is a shortcut on step 3 that can save you 10-20 minutes worth of work.

1.) Download the Canon IP2600 drivers from [**HERE**]("http://software.canon-europe.com/software/0034312.asp?model=").  The file should be called iP2600_debiang.tgz .

2.) Unzip and un-archive iP2600_debiang.tgz

3.) Now the fun part...  The .deb files included in the iP2600_debiang.tgz were built for an older version of ubuntu which reference a package called "cupsyslib2".  This old package has been since renamed to "cupslib2" so we will have to re-build the .deb packages.  There is a good guide on how to re-create the .debs [**HERE**]("http://ubuntuforums.org/showthread.php?t=110458") .  Follow the guide in the link and when you edit the list of dependencies replace all "cupsyslib2" with "cupslib2".  If you are a trusting person and you do not want to re-build your own .deb files I have uploaded the files I customized to mediafire.

[**cnijfilter-common_2.90-1_i386_1004customized.deb**]("http://www.mediafire.com/?nmzgan1mnqz")

[**cnijfilter-ip2600series_2.90-1_i386_1004customized.deb**]("http://www.mediafire.com/?x1jnuztgo5y")


4.) Install customized "common" deb 
```
sudo dpkg -i cnijfilter-common_2.90-1_i386_1004customized.deb
```

5.) Install customized "ip2600series" deb  
```
sudo dpkg -i cnijfilter-ip2600series_2.90-1_i386_1004customized.deb
```

6.) Chown /usr/lib/cups/filter/pstocanonij to root:root
```
sudo chown root:root /usr/lib/cups/filter/pstocanonij
```

7.) Restart your computer

8.) Install the printer in Gnome via the menus at the top of your screen "System -> Administration -> Printers"

9.) Print a test page

10.) If you follow this guide, please let me know if it worked for you

Thank you very much. This worked for me on Ubuntu 10.10 I had been fighting it for weeks.stmcc

---

### Post by Alathald on 2011-05-10
Thanks for the help, got the printer up and running fine. 

Only thing I suggest doing differently is instead of forcing the architecture, just change the DEBs to work with any architecture [like so]("http://fmatic.tumblr.com/post/3978818809/convert-32bit-deb-package-to-work-in-64bit-system").

Doing that lets you use gdebi, which is *SO* much more convenient.

---

### Post by Wrathlon on 2011-05-18
Thank you mate , another happy user thanks to your input. 

Using 11.04 32 bit and your instructions and modified files worked a charm . 

Once again thanks for ending my frustration. 

Daniel

---

### Post by linuxlalala on 2011-07-06
Thank you very much!!!!!!!!!!!

---

### Post by Alexiy on 2011-10-15
Thanks to author, I managed to install my ip2600. I'd like to add for noobs like me  that steps 4 and 5 must be executed at the directory you had the packages downloaded. I have Xubuntu and printer worked just after 7th step.

---

### Post by Elfy on 2011-10-16
I just installed this in 11.10 - didn't though do any of repackaging of the downloaded .debs

Used this dummy and all went fine - [http://packages.debian.org/lenny/all/libcupsys2/download](http://packages.debian.org/lenny/all/libcupsys2/download)

Found the information here 

[http://ubuntuforums.org/showpost.php?p=10935581&postcount=4](http://ubuntuforums.org/showpost.php?p=10935581&postcount=4)
[http://technostripe.com/getting-the-canon-pixma-ip2600-to-work-on-ubuntu/](http://technostripe.com/getting-the-canon-pixma-ip2600-to-work-on-ubuntu/)

---

### Post by lapratho on 2011-12-17
> **MillDaKill said:**
> **Summery:**
If you are like me and you own a Canon IP2600 printer you have probably found out that Ubuntu 10.04 does not set it up automagically.  After doing a little reading and some trial and error I have figured out how to get it to work and I wanted to share  my solution with you all.  There is a good chance that if there are other Canon IPXXXX printers that are not supported in Ubuntu 10.04 that following steps similar to the ones I am giving for the IP2600 will work (YMMV and not tested).

4.) Install customized "common" deb 
```
sudo dpkg -i cnijfilter-common_2.90-1_i386_1004customized.deb
```5.) Install customized "ip2600series" deb  
```
sudo dpkg -i cnijfilter-ip2600series_2.90-1_i386_1004customized.deb
```6.) Chown /usr/lib/cups/filter/pstocanonij to root:root
```
sudo chown root:root /usr/lib/cups/filter/pstocanonij
```7.) Restart your computer

8.) Install the printer in Gnome via the menus at the top of your screen "System -> Administration -> Printers"

9.) Print a test page

10.) If you follow this guide, please let me know if it worked for you


Greetings!

This worked like a charm! Thank you! 
This saved me a ton of time trying to figure out how to build .deb packages, because I wasn't making progress there after editing the control files 

lapratho

---

### Post by welshmike on 2012-06-01
MillDaKill,

Thank you very much again.
I followed your instructions and downloaded your customized deb files.
My Canon iP2600 is now printing on Ubuntu 12.04 Unity.

---

### Post by stmcc on 2012-06-05
> **MillDaKill said:**
> **Summery:**
If you are like me and you own a Canon IP2600 printer you have probably found out that Ubuntu 10.04 does not set it up automagically.  After doing a little reading and some trial and error I have figured out how to get it to work and I wanted to share  my solution with you all.  There is a good chance that if there are other Canon IPXXXX printers that are not supported in Ubuntu 10.04 that following steps similar to the ones I am giving for the IP2600 will work (YMMV and not tested).

**Notes:**
1.) I have only followed these steps on Ubuntu 10.04

2.) The computer I did it on was a 32bit machine

3.) Do not follow these steps on any kind of mission critical or production machine, spend the money and get a better supported printer.

4.) It is probably wise to make sure you have a backup of important files on your computer.  This guide worked for me but it has not been rigorously tested by any means.

**How-To:**
0.) Read all 10 steps listed below before you start.  If you are a trusting person, there is a shortcut on step 3 that can save you 10-20 minutes worth of work.

1.) Download the Canon IP2600 drivers from [**HERE**]("http://software.canon-europe.com/software/0034312.asp?model=").  The file should be called iP2600_debiang.tgz .

2.) Unzip and un-archive iP2600_debiang.tgz

3.) Now the fun part...  The .deb files included in the iP2600_debiang.tgz were built for an older version of ubuntu which reference a package called "cupsyslib2".  This old package has been since renamed to "cupslib2" so we will have to re-build the .deb packages.  There is a good guide on how to re-create the .debs [**HERE**]("http://ubuntuforums.org/showthread.php?t=110458") .  Follow the guide in the link and when you edit the list of dependencies replace all "cupsyslib2" with "cupslib2".  If you are a trusting person and you do not want to re-build your own .deb files I have uploaded the files I customized to mediafire.

[**cnijfilter-common_2.90-1_i386_1004customized.deb**]("http://www.mediafire.com/?nmzgan1mnqz")

[**cnijfilter-ip2600series_2.90-1_i386_1004customized.deb**]("http://www.mediafire.com/?x1jnuztgo5y")


4.) Install customized "common" deb 
```
sudo dpkg -i cnijfilter-common_2.90-1_i386_1004customized.deb
```

5.) Install customized "ip2600series" deb  
```
sudo dpkg -i cnijfilter-ip2600series_2.90-1_i386_1004customized.deb
```

6.) Chown /usr/lib/cups/filter/pstocanonij to root:root
```
sudo chown root:root /usr/lib/cups/filter/pstocanonij
```

7.) Restart your computer

8.) Install the printer in Gnome via the menus at the top of your screen "System -> Administration -> Printers"

9.) Print a test page

10.) If you follow this guide, please let me know if it worked for you
Thank you very much. It worked great on my 32bit ubuntu 10.10

---

### Post by stmcc on 2012-09-17
> **MillDaKill said:**
> **Summery:**
If you are like me and you own a Canon IP2600 printer you have probably found out that Ubuntu 10.04 does not set it up automagically.  After doing a little reading and some trial and error I have figured out how to get it to work and I wanted to share  my solution with you all.  There is a good chance that if there are other Canon IPXXXX printers that are not supported in Ubuntu 10.04 that following steps similar to the ones I am giving for the IP2600 will work (YMMV and not tested).

**Notes:**
1.) I have only followed these steps on Ubuntu 10.04

2.) The computer I did it on was a 32bit machine

3.) Do not follow these steps on any kind of mission critical or production machine, spend the money and get a better supported printer.

4.) It is probably wise to make sure you have a backup of important files on your computer.  This guide worked for me but it has not been rigorously tested by any means.

**How-To:**
0.) Read all 10 steps listed below before you start.  If you are a trusting person, there is a shortcut on step 3 that can save you 10-20 minutes worth of work.

1.) Download the Canon IP2600 drivers from [**HERE**]("http://software.canon-europe.com/software/0034312.asp?model=").  The file should be called iP2600_debiang.tgz .

2.) Unzip and un-archive iP2600_debiang.tgz

3.) Now the fun part...  The .deb files included in the iP2600_debiang.tgz were built for an older version of ubuntu which reference a package called "cupsyslib2".  This old package has been since renamed to "cupslib2" so we will have to re-build the .deb packages.  There is a good guide on how to re-create the .debs [**HERE**]("http://ubuntuforums.org/showthread.php?t=110458") .  Follow the guide in the link and when you edit the list of dependencies replace all "cupsyslib2" with "cupslib2".  If you are a trusting person and you do not want to re-build your own .deb files I have uploaded the files I customized to mediafire.

[**cnijfilter-common_2.90-1_i386_1004customized.deb**]("http://www.mediafire.com/?nmzgan1mnqz")

[**cnijfilter-ip2600series_2.90-1_i386_1004customized.deb**]("http://www.mediafire.com/?x1jnuztgo5y")


4.) Install customized "common" deb 
```
sudo dpkg -i cnijfilter-common_2.90-1_i386_1004customized.deb
```

5.) Install customized "ip2600series" deb  
```
sudo dpkg -i cnijfilter-ip2600series_2.90-1_i386_1004customized.deb
```

6.) Chown /usr/lib/cups/filter/pstocanonij to root:root
```
sudo chown root:root /usr/lib/cups/filter/pstocanonij
```

7.) Restart your computer

8.) Install the printer in Gnome via the menus at the top of your screen "System -> Administration -> Printers"

9.) Print a test page

10.) If you follow this guide, please let me know if it worked for you
Do you have a customized for a amd 64 bit intstallation?
MAC

---

