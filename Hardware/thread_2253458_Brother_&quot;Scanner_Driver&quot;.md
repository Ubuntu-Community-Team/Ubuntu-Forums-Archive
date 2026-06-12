---
title: "Brother &quot;Scanner Driver&quot;"
date: 2014-11-19
forum: Hardware
---

### Post by harelb on 2014-11-19
In another thread I got great help for both getting and installing a printer driver, and also even defaults for the new laserprinter( [see here]("http://ubuntuforums.org/showthread.php?t=2252459&p=13165555#post13165555")) 

And eveything works fine even though, following suggestsions on that thread, I've ignored the Brother manual's direction to get from the CD the drivers...the script used instead of their CD (which is for windows) worked great..

Now I'm ready to try out the scanner...And the official Brother user Manual says to install a "scanner driver"...before anyone asks me whether I tried to see if the scanner works already without me installnig anything else, the answer is no (-: maybe I'm too cautious to try to avoid "breaking" anything....

but I did look at the url at brother.com which had the script (the one that the above Ubuntuforums threads pointed me in that direction) and it doesn't have the word "scanner" there, this url [brother page 'driver install tool']("http://support.brother.com/g/b/downloadhowto.aspx?c=gb&lang=en&prod=dcp7060d_all&os=128&dlid=dlf006893_000&flang=4&type3=625") which I had run to successfully get my printer driver installed and my printer printing fine...so I'm guessing it did not install a "scanner driver" and I need to do something separate?

It there another url, maybe also on Brother.com which is parallel/similar to the above, with another script to run, that'll do the job? And equally quick and easy?

**Added Edit:** well another thread on ubuntuforums seems to suggest this more complex beast for both printer? and scanner drivers:

2) [http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=mfcj410w_us&os=128&dlid=dlf006893_000&flang=4&type3=625]("http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=mfcj410w_us&os=128&dlid=dlf006893_000&flang=4&type3=625")

given that I've already ran and installed the printer driver using:

1) [this brother page]("http://support.brother.com/g/b/downloadhowto.aspx?c=gb&lang=en&prod=dcp7060d_all&os=128&dlid=dlf006893_000&flang=4&type3=625")

do I still use 2) after having used 1)?  Or is 1) enough and I'm all done and safe to try using my scanner it I'm just using my printer/scanner (no others, no network etc)? Or am I not done but there's a simpler link than 2) to use for my humble (previous parenthetical comment) needs? Thanks (-:

---

### Post by SuperFreak on 2014-11-19
[http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcj410w_us&os=128]("http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcj410w_us&os=128")

I think directions on how to install the driver are [HERE]("http://support.brother.com/g/s/id/linux/en/index.html?c=us_ot&lang=en&comple=on&redirect=on")

---

### Post by leclerc65 on 2014-11-19
After doing what SuperFreak suggests, have a look at this thread

[http://ubuntuforums.org/showthread.php?t=2253131](http://ubuntuforums.org/showthread.php?t=2253131)

---

### Post by harelb on 2014-11-21
Thanks Superfreak....however I need some more information..please bear with these questions, several things are not clear to me:


i) why is your profided link ("link 3") preferrable to link 2 that I cited in my post?

ii) I also asked if it's ok/safe to use link 2 given that I have already used link 1) to install a printer driver. Same question for your link 3.

iii) In any case do I ignore all drivers except the "scanner driver" in link 3 (or link 2)?

iv) Link 2 which was given to me is much simpler; it has just one "place" to go to...your link 3, has 3 printer driver links, 5 scanner driver links, and much more. Assuming(?) the answer is that your link 3 is best, sub-questions are:

iv-A) Does the following command line response I got, confirm that I do have what I think I have, namely 32bit? I got:
> 
 file /sbin/init
/sbin/init: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=0x07075fcb55b05aeb6286efabba63534fa6ecd213, stripped


iv-B) If the answer to iv-A) is "yes you have 32bit" then obviously(?) I ignore the 2nd and 4th (64bit) links in the Scanner Drivers secdtion of your "link 3" so I click the first, "Scanner driver 32bit (deb package)" and the 3rd, "Scan-key-tool 32bit (deb package)" and what about the 5th? That one says "Scanner Setting file (deb package)"...optional? needed?

iv-C) last but not least, am I now done given that I used link #1 (in my orig post above) to already install the printer driver (and my printer does indeed work) then those two or three (depending on your answer if 5th one is needed) will make me "all set" to use scanner? This is my first scanner that I'd use, so don't assume I know anything (-: I'll just finish trying to follow the printerd user manual, *after* I know for sure I have the scanner drivers inscalled (since I'm ignoring the Manual's "step #1" of using the CD, since I don't have windows and was told on these forums not to even try the CD for that reason)

I think that's it for my questions...hopefully with clarification I know what is safe/what's necessary/vs optonal for my next steps!

(thanks for your post leclerc65....as you can see I'm still trying to comprehend more basic things first but I'll look at your link after I am able to follow superfreak's responses/clarifications)

---

### Post by pdc on 2014-11-21
gosh harelb; 

what about just install the scanner driver: there are two steps:

1) install scanner driver
2) install a udev rule so you as user, can use the scanner

__________
**_Step 1 _**your device is a brscan4; so how about ............ go here ............[http://support.brother.com/g/s/id/linux/en/download_scn.html](http://support.brother.com/g/s/id/linux/en/download_scn.html) and download the debian package that suits your system ..............ie 32bit or 64 bit .......... when you click to download, your system should offer to "open" it ......... that should mean install it .......... so accept that offer ..................

_____________________________________________________

**_Step 2_** if your device is connected by usb cable, guidance is here [http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04) but you may wish to come back for more guidance on this step 2 stage ...................

---

### Post by SuperFreak on 2014-11-21
You should choose from one of the two first scanner drivers in the list of tha link I provided. You need to know if you are usinng a 32 or 64 bit OS. To find this out look [HERE]("http://askubuntu.com/questions/41332/how-do-i-check-if-i-have-a-32-bit-or-a-64-bit-os"). Choose the correct scanner driver. The directions on how to innstall the driver are given in the download, follow carefully. Test with Simple Scan or XSane

---

### Post by kurt18947 on 2014-11-21
There are two installer scripts for Brother machines, 1.xxxx and 2.xxx.  1.xxx installs only the printer, 2.xxx installs both the printer and scanner. Whether you're using a USB or network connection matters too.  If using USB, you must do the udev edit as PDC says. I don't know if that is necessary with a network only machine.  For  networked scanner to be recognized, you may have to run one line in a terminal.  Step 5 on this page:

[http://support.brother.com/g/s/id/linux/en/instruction_scn1b.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_scn1b.html?c=us_ot&lang=en&redirect=on)

There is also this bug. It may be fixed but if you scanner doesn't work, you can check that the correct files are in the correct places.

[http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101)

---

### Post by harelb on 2014-11-23
Learning is a balancing act, as I know both from being a learner and teacher: give the student too much info and they are overwhelmed (Einstein's famous dictum: "Simplify as much as possible; *but not* more than that) give them too little and they come back more confused too (-;

**Superfreak**:  Since I already showed the output I got in step iv-A) I was kind of hoping for either "yes, your output does confirm you have 32bit just as you think" or else "no, your output does not mean that. Since I got neither I gather that either you didn't notice that output or else (though you did not say so explicity, so I'm making an educated guess here!) that you mean to tell me that: "typing ' file /sbin/init' is not a reliable way to answer your question, so you must use "uname" instead.  I did get the impression [elsewhere]("http://askubuntu.com/questions/451404/am-i-running-32-bit-or-64-bit") that either the 'file /sbin/init" OR the "uname -a" are both usable, and I showed everyone the output I got, as Quoted text, in step iv-A). Either way i'm not trying to make things harder just trying to learn (and also to avoid problems later).  I _AM_ now SURE I have _32bit_, since both commands, (and a third one I found elsewhere) a*ll  three point to 32bit*..

..even though it would have been nice to get a clearer picture whether "uname -a" is the *only* reliable way (so I should delete the other commands and not let them clutter up my 'cheat sheet' of ubuntu commands (my memory has the half-life of a ripening banana so I have to write all down...) or whether the "file" command I quoted, is *also* usable...oh well, at least I am now sure I have 32bit so I'm already, gosh, at least 1% done (-;

My printer is connected to my computer with a usb cord, yes.

(you can skip all until last paragraph, Superfreak, on how I'm following on on your directions)

**Kurt** the " 1.xxxx and 2.xxx" explanation was helpful, thanks..and you can ignore the following question since it too is "just me trying to learn, but I already have the right thing installed" but, I used something where I saw neither the "1" nor the "2" you quote (and I'm sure you're right, I'm sure they are there, I must be looking in the wrong place? trying to better understand) but  I had before posting this thread, back when installing printer driver, I had used [this]("http://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=mfcj410w_us&os=128&dlid=dlf006893_000&flang=4&type3=625") which in turn had me do " bash linux-brprinter-installer-*.*.*-* Brother machine name" which I don't see a "1" nor a "2" in....**oh wait!** The directory that the .gz (later uncompressed) file from Brother lives in, has this file "linux-brprinter-installer-2.0.0-1" in it, is that what the "bash" command used? So the "2" there is the same as what you mean by "2.xxx"? That could suggest the eariler script I ran *did* include a scanner driver after all (as I said at the outset I haven't dared try to proceed to scanner directions until I obedietently follow the printed manual that said start with step 1, install all drivers) My entire directory in which the above (this paragraph) linked to Brother.com page ran the "Bash" from has these contents:
> brscan-skey-0.2.4-1.i386.deb            44 KB
brscan4-0.4.2-1.i386.deb                61 KB
cupswrapperDCP7060D-2.0.4-2.i386.deb       14 KB
cupswrapperDCP7060D-2.0.4-2a.i386.deb      13 KB
dcp7060dlpr-2.1.0-1.i386.deb            35 KB
dcp7060dlpr-2.1.0-1a.i386.deb           35 KB
driver-install-info.txt                 2 KB
linux-brprinter-installer-2.0.0-1       90 KB
uninstaller_DCP7060D                    2 KB
uninstaller_brscan-skey                 1 KB
uninstaller_brscan4                     1 KB

For what it's worth.

**pdc**, I appreciate your help...and as I said above, I'm not trying to make things harder, but just to learn...and I do think you can understand why I'd want to *first* confirm 32bit versus 64 bit before jumping in (now I'm sure but now when I started this thread) why I wanted to make sure I don't damage things by running scripts with some (potential) overlap/redundancy, and why I was curious (wanting to better understand) why one expect on ubuntuforums sent me to what I called "link 2" at beginning of this thread while another expert sent me to a different one. Just trying to get bearings straight, to learn a bit, to undestand better and minimize chances for damage (-:

Lastly **Superfreak**, since you said I should use one of the first two links you provided, and since I now have confirmed that I have 32bit, I'll use the very first link (since that's the 32bit one) which is [http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=mfcj410w_us&os=128&dlid=dlf006641_000&flang=4&type3=565]("http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=mfcj410w_us&os=128&dlid=dlf006641_000&flang=4&type3=565") and will report back here what does or doesn't explode in my face (-;  (**Edit:** just noticed in that link that "compatible" list does *not* include "dcp-7060d" but hopefully the "7030" and "7040" listed are close enough..I'll find out soon..)
Thanks..
 (and my smiley are backwards to avoid automatic iconization, I prefer ascii ones to icons)

---

### Post by harelb on 2014-11-23
Superfreak, you said to install one of the first two; is there any reason **not** to also install the third, which is "Scan-key-tool 32bit (deb package)" which says>  "With this tool, you can start a scan by the button on the machine." which I definitely want to be able to do..?

---

### Post by harelb on 2014-11-23
> 1. Download the driver.
 2. Login as a superuser (or use "sudo" option if required) .
 
3. Check if pre-required procedures are completed 
For Debian, Ubuntu
 
4. Install the driver.

    4.1. Turn on your MFC/DCP and connect the USB cable.
    4.2. Open the terminal and go to the directory where the driver is.
    4.3. Install the scanner driver.
    Command (for dpkg) : dpkg -i --force-all  (scanner-drivername)
    4. 4. Check if the driver is installed.
    Command (for dpkg) : dpkg -l | grep Brother

A link in step 3 took me to a page telling me "    sane-utils is required to be installed." and (although I mistakenly thought that "which" or "whereis" from the shell will tell me if something is installed (and those seemed to indicate it's not) I tried the Ubuntu Software Center which told me that "sane-utils" *is* installed)

So that part was/is all well and good too..

Step 4.1-4.3 and in particular 4.3 ran without any complaint:
> 
 sudo  dpkg -i --force-all brscan3-0.2.11-4.i386.deb
Selecting previously unselected package brscan3.
(Reading database ... 1051970 files and directories currently installed.)
Unpacking brscan3 (from brscan3-0.2.11-4.i386.deb) ...
Setting up brscan3 (0.2.11-4) ...

In step 4.4 I ran  " dpkg -l | grep Brother" and got>  

ii  brscan-skey                              0.2.4-1                                 Brother Linux scanner S-KEY tool
ii  brscan3                                  0.2.11-4                                Brother Scanner Driver
ii  brscan4                                  0.4.2-1                                 Brother Scanner Driver
ii  cupswrapperdcp7060d                      2.0.4-2                                 Brother DCP7060D CUPS wrapper driver
ii  dcp7060dlpr                              2.1.0-1                                 Brother DCP-7060D LPR driver
ii  printer-driver-ptouch                    1.3-3ubuntu0.1                          printer driver Brother P-touch label printers

I hope this output **also** translates into "all is well"(?)

As I said this is my first ever scanner so I still need to learn how to use it...so _unless_ I hear back here when I check in again  Sunday late afternoon or night that something's "amis",, I'll (i) go and read the printed Brother manual...(after (ii) possibly installing the other package " "Scan-key-tool 32bit (deb package)"") and

(iii) I'lll try to learn about what the heck Simple Scan and XSane are so I can at least dutifully follow "Test with Simple Scan or XSane" and try my first scan ever (well in 1994 or so I remember using OCR with a scanner at the university computing lab...but that was probably the last time I've done so, and either my brain was faster then, or things were more streamlined and simpler, or probably both (-; Anyway my first scanner at home that I've had (or admitted to myself I had and actually tried *using* )

..and then I'll be reach to (iv) take on nice home-declutting projects and scan in i.e. digitize stuff happily ever after

---

### Post by SuperFreak on 2014-11-23
> **harelb said:**
> 

**Superfreak**:  Since I already showed the output I got in step iv-A) I was kind of hoping for either "yes, your output does confirm you have 32bit just as you think" or else "no, your output does not mean that. Since I got neither I gather that either you didn't notice that output or else (though you did not say so explicity, so I'm making an educated guess here!) that you mean to tell me that: "typing ' file /sbin/init' is not a reliable way to answer your question, so you must use "uname" instead.  I did get the impression [elsewhere]("http://askubuntu.com/questions/451404/am-i-running-32-bit-or-64-bit") that either the 'file /sbin/init" OR the "uname -a" are both usable, and I showed everyone the output I got, as Quoted text, in step iv-A). Either way i'm not trying to make things harder just trying to learn (and also to avoid problems later).  I _AM_ now SURE I have _32bit_, since both commands, (and a third one I found elsewhere) a*ll  three point to 32bit*..

..even though it would have been nice to get a clearer picture whether "uname -a" is the *only* reliable way (so I should delete the other commands and not let them clutter up my 'cheat sheet' of ubuntu commands (my memory has the half-life of a ripening banana so I have to write all down...) or whether the "file" command I quoted, is *also* usable...oh well, at least I am now sure I have 32bit so I'm already, gosh, at least 1% done (-;

I have to say I have only used uname command to find OS bit, so I can't comment on the other method you used

> **harelb said:**
> 
Lastly **Superfreak**, since you said I should use one of the first two links you provided, and since I now have confirmed that I have 32bit, I'll use the very first link (since that's the 32bit one) which is [http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=mfcj410w_us&os=128&dlid=dlf006641_000&flang=4&type3=565]("http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=mfcj410w_us&os=128&dlid=dlf006641_000&flang=4&type3=565") and will report back here what does or doesn't explode in my face (-;  (**Edit:** just noticed in that link that "compatible" list does *not* include "dcp-7060d" but hopefully the "7030" and "7040" listed are close enough..I'll find out soon..)
Thanks..
 (and my smiley are backwards to avoid automatic iconization, I prefer ascii ones to icons)


Looking at the link ([HERE]("http://support.brother.com/g/b/downloadend.aspx?c=ca&lang=en&prod=dcp7060d_all&os=128&dlid=dlf006645_000&flang=4&type3=566") there is a drop down menu which shows which printers are compatible for that method, I believe yous is in the list.


EDIT: It looks like my first link was for the wrong printer, my apologies. Check the link in this post

---

### Post by harelb on 2014-11-28
**SuperFreak**, Sorry for the delay getting back here, and thanks, but that link is for 64bit, not 32bit...This link I just found by google searching "site:brother.com Scanner driver 32bit (deb package)" which I came up with using the title of link in your last post but with "32"  and eventually (not directly unfortunately but through other brother pages which led to it) found
[this link]("http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=dcp7060d_all&os=128&dlid=dlf006646_000&flang=4&type3=565") which does list 7060-D. I assume "deb" will work...

(and in case this helps others in the future the Brother website organizes *also* by printer model so: [http://support.brother.com/g/b/producttop.aspx?c=us&lang=en&prod=dcp7060d_all]("http://support.brother.com/g/b/producttop.aspx?c=us&lang=en&prod=dcp7060d_all") is there "7060-D" page.)

I'm hoping it will not mess up anything if I have two drivers or what have you..so long as the right one is there..last but not least I am still not clear, after I install this driver on Friday, do I still want to separately install that "tool" for "scanning directly from scanner"? Earlier post in this thread cited it but you omit mention of it..? I'm referring to my earlier,

> **harelb said:**
> Superfreak, you said to install one of the first two; is there any reason **not** to also install the third, which is "**Scan-key-tool 32bit (deb package)**" which says which I definitely want to be able to do..?
thanks,
-HB

P.S. wow, it was really hard logging into ubuntuforums! Previously when I log in it takes me to the front page instead of back to this thread, which is a hasstle but I go Back in the browser and Reload...not this time..even when I copy/pasted the url
[urlhttp://ubuntuforums.org/showthread.php?t=2253458&page=2&[/url]
into the url box AFTER logging in, it thinks I'm not yet logged in (proof: I click "advanced reply" and it say Admin requirees me to register...after I was logged in!) Finally trying to be creative I cut the url off here
[http://ubuntuforums.org/showthread.php?t=2253458&page=2](http://ubuntuforums.org/showthread.php?t=2253458&page=2)
which I think still failed once but then allowed me, finally, to get to this page (AFTER having logged in) without the page thinking I'm "not yet logged in" just because I had been on this page (bookmarked) before logging in...whew!) As far as I know I have not told Firefox to nix cookies or anything like that since my previous posts....

PPS: notes to myself, after just now installing scanner driver for "7060D" did step 4: "Check if the driver is installed.
Command (for dpkg) : dpkg -l | grep Brother" and output of this "grep" is:
> 
   Brother Linux scanner S-KEY tool
ii  brscan3                                  0.2.11-4                                Brother Scanner Driver
ii  brscan4                                  0.4.2-4                                 Brother Scanner Driver
ii  cupswrapperdcp7060d                      2.0.4-2                                 Brother DCP7060D CUPS wrapper driver
ii  dcp7060dlpr                              2.1.0-1                                 Brother DCP-7060D LPR driver
ii  printer-driver-ptouch                    1.3-3ubuntu0.1                          printer driver Brother P-touch label printers

which like last time I assume means "all is well" but *gee it would be nice* if Brother.com had another sentence in the step 4 directions saying what the output *should* look like when the "check if..installed" is successful.

Last update tonight, did first 4 of 5 steps of "Scan-key-tool 32bit (deb package)" install, up to "use grep" step to check if installed, output:
>  dpkg -l  |  grep  Brother
ii  brscan-skey                              0.2.4-1                                 Brother Linux scanner S-KEY tool
ii  brscan3                                  0.2.11-4                                Brother Scanner Driver
ii  brscan4                                  0.4.2-4                                 Brother Scanner Driver
ii  cupswrapperdcp7060d                      2.0.4-2                                 Brother DCP7060D CUPS wrapper driver
ii  dcp7060dlpr                              2.1.0-1                                 Brother DCP-7060D LPR driver
ii  printer-driver-ptouch                    1.3-3ubuntu0.1                          printer driver Brother P-touch label printers

...leaving 5th step "un scan-key-tool and try the test scanning." till tomorrow, bedtime now (-:

---

### Post by SuperFreak on 2014-11-28
Yes deb file is what you need as Ubuntu will install that.
I don't use the "scan from scanner tool" so I can't tell you if it will work
I don't think there will be any problems having the driver from the wrong model in addition to the right one but [HERE]("http://askubuntu.com/questions/482375/how-to-completely-delete-and-reinstall-a-printer-driver") is a link to help you get rid of the old driver

---

### Post by harelb on 2014-11-29
thanks...apparently, Xsane does not support any Brother printer...if I'm reading correctly this link: [http://sane-project.org/sane-mfgs.html#Z-BROTHER]("http://sane-project.org/sane-mfgs.html#Z-BROTHER") but that's ok (assuming Simple Scan works for me) since I was leaning towards that simpler interface...I will try to go through the manual and try a test scan with Simple Scan...

---

### Post by SuperFreak on 2014-11-29
> **harelb said:**
> thanks...apparently, Xsane does not support any Brother printer...if I'm reading correctly this link: [http://sane-project.org/sane-mfgs.html#Z-BROTHER]("http://sane-project.org/sane-mfgs.html#Z-BROTHER") but that's ok (assuming Simple Scan works for me) since I was leaning towards that simpler interface...I will try to go through the manual and try a test scan with Simple Scan...

I use XSane a great deal and use a Brother MFC 5490
But if Simple Scan works for you then go with that

EDIT: looks like the reference in the link was to specific models of Brother printers. I don't thik your printer was listed

---

### Post by harelb on 2014-11-29
Of course it would be too simple to expect things to work right away :(   so simple scan doesn't...

Two other questions are, 1) in hindsight, how could Xsane possibly not be compatible with any printer, so long as you have installed the scanner driver, anyway? (I'm sure this is a very *naive* question since obviously if what I'm suggestiong were true, then they wouldn't have a list of "supported devices"..but I don't see why it should be a violation of the laws of physics for "user has installed a scanner driver" to be a *sufficient condition* to "universally" interface with xSane..but it obviously violates something..)

2) Re your comment "I use XSane a great deal and use a Brother MFC 5490" does the fact that they don't list your model type, which *does* work with Xsane, mean their page [http://sane-project.org/sane-mfgs.html#Z-BROTHER]("http://sane-project.org/sane-mfgs.html#Z-BROTHER") is out of date or in error? (in fact as you can see they list only 4 models, and ALL four say "unsupported", so not sure what to make of that..)
[B]
Back to my main question/problem[/B] - I get "failed to scan" and "failed to connect to scanner"... (then I tried to confirm my printer was still connected right by USB...it didn't print...I was ready to smath my head into my desk when I found out that after you click "close" on simple scan it, I guess the right word might be, "releases" the printer and I can print again..) but when I try to scan again, same error..

Am currently trying to follow the many and varietd suggestions and approaches (all of which are unfamiliar) at the thread [http://ubuntuforums.org/showthread.php?t=2235276]("http://ubuntuforums.org/showthread.php?t=2235276") and hope at least one is both not over my head, and simultaneously and crucially, also works...

---

### Post by SuperFreak on 2014-11-29
[http://ubuntuforums.org/showthread.php?t=2235276]("http://ubuntuforums.org/showthread.php?t=2235276")
Posts #2 & #4 may help you get configured so both XSane and/or Simple scan work.

---

### Post by harelb on 2014-11-29
UPDATE:

Just  launching xsane for the first time (not even trying a "scan
command" but just launching) I got an error dialog box which said (I hope
I transcribed this exactly, since for some reason I can't copy/paste
from ubuntu error dialog boxes is that not possible?) said:

> Failed to open device 'brother4:bus5;dev3': Invalid argument

Also found very interesting six step "to do" list that for this user, SOLVED the problem, [here]("http://ubuntuforums.org/showthread.php?t=2235276") and** step number 5 ** jumps out at me since I don't think the brother.com nor the advice on this thread so far (as far as I could follow it) told me to carry out this step 5...

> Problem solved...
"1. For the Scanner
2. Download the 64-bit brscan3 drivers
([http://welcome.solutions.brother.com...nload_scn.html](http://welcome.solutions.brother.com...nload_scn.html))
3. Install them (we don't need to force this time!) (dpkg -i [driver])
4. Check to make sure it worked [dpkg -l | grep Brother]
5. Use the brother tool for adding a new scanner (brsaneconfig3 -a
name=SomeName model=MFC-NOLOWERCASELETTERSALLOWEDHERE
ip=xxx.xxx.xxx.xxx)
6. Open your favorite scanning program and try it out!"
([http://ubuntuforums.org/showthread.php?t=1601221&page=2](http://ubuntuforums.org/showthread.php?t=1601221&page=2))

See I downloaded the scanner drivers (only 32bit for my computer) and installed and did the grep (and posted results of grep above; hope they are ok) 

I think I do have "brsaneconfig3" installed since typing that word by itself at shell does *not* say "command not found" but asks for arguments...


_** My Two questions:**_

1) Since my "grep" above included "ii brscan3 0.2.11-4 Brother Scanner Driver
ii **brscan4** 0.4.2-4 Brother Scanner Driver" do I still want to use "brsaneconfig_3_" and not some kind of "brsaneconfig_4_"? For example some driver was called "brscan_4_-0.4.2-4.i386.deb" on my hard drive....

I just want to make sure there aren't other "translations" (like 64 bit to 32 bit) that I need to perform before taking the directions "verbatim".....)

(**EDIT**: "brsaneconfig5: command not found" but if I type "brsaneconfig4" **OR** "brsaneconfig3" at the command line (just an effort to see which is installed as a command...before I get my last question below answered) and BOTH the "3" and "4" give me a "USAGE:...." reply so BOTH are installed..[I].so do I keep the "3" in "brsaneconfig3" in the above directions or change it to "4" given my .deb etc scripts that installed drivers some have 3 some have 4...

PLUS the Xsane error message above starts with "brother4" so I'm thinking I need to use a "4" not "3" in the command, as in "**brsaneconfig_4_**"..would that be right?[/I]) 

2) Most importantly what exactly do I type in verbatim, meaning what do I translate:

> a name=SomeName model=MFC-NOLOWERCASELETTERSALLOWEDHERE ip=xxx.xxx.xxx.xxx

(notice I deleted the close-parenthesis they had at the end...I assume that's right...) what do I translate the above into??

I take it "SomeName" can be made anything I want....*For the rest though is unclear to me*...I own a DCP-7060D, and the .deb files are as in this thread and the one just quoted if that's relevant. 

including, for the answer I'm requesting help for, for the above: *What do I put for "ip address"? * 

(i.e. how do I find out the answer...I am using USB physical connection, not network, again, in case that's relevant)

Hoping light at the end of the tunnel and not a train is that little white dot I see ;)

---

### Post by SuperFreak on 2014-11-29
Try
```
gksudo gedit /lib/udev/rules.d/40-libsane.rules
```

Then add:
> # Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
to bottom of device list before "LABEL="libsane_rules_end"". 


Reboot
Try XSane or Simple Scan

I think all the information to make this all work is on the Brother web site including what I gave you and the above

---

### Post by harelb on 2014-11-30
Superfreak, I appreciate your trying to help (really!) and I would understand your gently suggesting I use info already-cited on page, however, please notice that:  1. the [thread]("http://ubuntuforums.org/showthread.php?t=2235276") with this info, has Webmanoffesto (who asked the original question) saying they had trouble using the advice..)YES, it looks like they just didn't know about "gksudo") but:  _2. something else WORKED for Webmanoffesto_ nameluy this "brsaneconfig" thing (instead of the "gksudo gedit.." or else in *addition* to it, either way I need this "brsaneconfig" to follow what *workd* for him/her) 3. that "brsaneconfig" thing does not require editing with sudo power, a file (which seems a more risky approach in terms of potentially causing damage...yes I have managed to cause serious damage in the past so I'm once burned, 10 times shy..!)

Whether or not I'm right on item 3 (that it's riskier to edit a file I don't understand) surely you can understand my wanting to use the method that **did** work for Manoffesto, it being short and sweet and which WORKED for him, you can surely undersatnd my trying to reproduce that once I undestand how the line translates...

It is for these reasons, that I'm hoping you can therefore (or someone else) understand and help me understand how to use what *did* work for webmanoffesto, which is not the gksudo but this:

>  5. Use the brother tool for adding a new scanner (brsaneconfig3 -a
name=SomeName model=MFC-NOLOWERCASELETTERSALLOWEDHERE
ip=xxx.xxx.xxx.xxx) 

I'm just asking how to translate model and the "ip address" into what's approprpriate for me..help on this please?

[**EDIT**: I surrender to your wisdom and experinece SuperFreak, *I've edited just as you told me..and am about to reboot.*.hope no major damage results...if it doesn't work, I still need to find out how to implement the above-quoted ("**brsaneconfig**" with "ip" address etc...since webmanoffesto *claimed* that is what was necessary to get things working for them..! rebooting now and will be back..)

---

### Post by harelb on 2014-11-30
I wrote earlier:
> 
    [EDIT: I surrender to your wisdom and experinece SuperFreak, I've edited just as you told me..and am about to reboot..hope no major damage results...if it doesn't work, I still need to find out how to implement the above-quoted ("brsaneconfig" with "ip" address etc...since webmanoffesto claimed that is what was necessary to get things working for them..! rebooting now and will be back..) 

Guess "surrendering" was the right thing do to this time because.._success_! Many thanks for sticking with this, SuperFreak! 

That thread you  pointed too with webmanoffesto sure *sounded* like the "brsaneconfig" was possibly a sufficient and definitely a *necessary* step from what webmaneffesto wrote there..

..so I tried to understand that  (brsaneconfig3 -a name=SomeName model=MFC-NOLOWERCASELETTERSALLOWEDHERE
ip=xxx.xxx.xxx.xxx)  but I guess for me it was *not* necessary after all :-)

I suspect I may be back here (or a new thread..this one's long already...) if/when I'm ready to tackle automatic document feeder for multiple copies -- either webmanoffesto or another said that they had trouble with that...but for the next little while I'll happily try to learn all the preferences for one-page-at-a-time scanning, which should keep me busy for a few days (at least) until I'm ready to tackle major "digitizing old stuff" projects that *will* probably require the [auto document feeder]("http://ubuntuforums.org/showthread.php?t=2235276&p=13079693#post13079693") to work which it might not per link..but I'm not ready to try that yet..

So no more "newbie" questions from me for tonight and next few days, just another:_ THANK YOU SUPERFREAK!_ :-D

---

### Post by SuperFreak on 2014-11-30
Your welcome

---

