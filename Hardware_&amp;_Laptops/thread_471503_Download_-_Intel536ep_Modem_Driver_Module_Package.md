---
title: "Download - Intel536ep Modem Driver Module Package"
date: 2007-06-12
forum: Hardware &amp; Laptops
---

### Post by Sepero on 2007-06-12
.










For the latest releases, please visit-
[http://groups.google.com/group/ubuntu-modems](http://groups.google.com/group/ubuntu-modems)
















Latest Hardy Heron 8.04 download:
[http://www.mediafire.com/?tgpotygcwdg](http://www.mediafire.com/?tgpotygcwdg)

(Or for the LiveCD Kernel 2.6.24-16-generic)
[http://www.mediafire.com/?zcywfm9m8jn](http://www.mediafire.com/?zcywfm9m8jn)





-Jul 17 08-
This release fixes an error that prevents the package from installing on the newest (19-generic) kernel. UNINSTALL the first driver, if you have it installed.
Intel536ep Driver for Hardy Heron Ubuntu Release 3:
[http://www.mediafire.com/?tgpotygcwdg](http://www.mediafire.com/?tgpotygcwdg)


-May 31 08-
This release should work for upgraded kernels 2.6.24-17-generic, and probably all later versions. UNINSTALL the first driver, if you have it installed.
Intel536ep Driver for Hardy Heron Ubuntu Release 2:
[http://www.mediafire.com/?gyw21am21wm](http://www.mediafire.com/?gyw21am21wm)


-May 12 08-
This is the first release for Hardy. It only works for the Kernel 2.6.24-16-generic from the install CD's.
Intel536ep Driver for Hardy Heron Ubuntu Release 1:
[http://www.mediafire.com/?zcywfm9m8jn](http://www.mediafire.com/?zcywfm9m8jn)





Latest Gutsy Gibbon 7.10 download:
[http://www.mediafire.com/?9t1my1njzz5](http://www.mediafire.com/?9t1my1njzz5)


-Dec 04 07-
This release resolves an error preventing the driver from being loaded.
Intel536ep Driver for Gutsy Gibbon Ubuntu Release 2:
[http://www.mediafire.com/?9t1my1njzz5](http://www.mediafire.com/?9t1my1njzz5)


-Nov 21 07-
For everyone that's been dieing for me to release the new driver for Gutsy, it's finally here.
Intel536ep Driver for Gutsy Gibbon Ubuntu Release 1:
[http://www.mediafire.com/?ejedy1dzeun](http://www.mediafire.com/?ejedy1dzeun)





Latest Feisty Fawn 7.04 download:
[http://www.mediafire.com/?exded1lozdw](http://www.mediafire.com/?exded1lozdw)


-Sep 16 07-
For Intel 537ep modem users, driver release #1 is now available.
[http://ubuntuforums.org/showthread.php?p=3372887](http://ubuntuforums.org/showthread.php?p=3372887)


-Aug 30 07-
I have now uploaded the third and hopefully last 536ep release for Ubuntu Feisty. This new driver should correct the issue about not working with older Feisty kernels. This driver should work with all Ubuntu Feisty kernel versions 2.6.20*. For all of those that are ready for the big jump to Gutsy, please hold out a bit. I do not have intentions of switching to Gutsy until it has been officially released for a month or two. Until that time I will not have a Gutsy driver. If anyone has the ability to compile the Gutsy driver themselves and would like to send me a copy of it, I would be willing to release it sooner.
Intel536ep Driver for Feisty Fawn Ubuntu Release 3:
[http://www.mediafire.com/?exded1lozdw](http://www.mediafire.com/?exded1lozdw)


-Jul 16 07-
Some people have reported that the original old Feisty CD's had a different kernel. If you have an install from an original Feisty CD, AND the latest driver package refuses to install on your system, then you may try the test release below. Please report with your results.
Intel536ep Driver for Feisty Fawn Ubuntu Release Test (2.5):
[http://www.mediafire.com/?ftjztpgm1mg](http://www.mediafire.com/?ftjztpgm1mg)


-Jun 17 07-
I've made minor additions/corrections to the original package, mainly improving the included documentation. I'm happy to say that I received zero complaints on the first release.
Intel536ep Driver for Feisty Fawn Ubuntu Release 2:
[http://www.mediafire.com/?b3y01ewghez](http://www.mediafire.com/?b3y01ewghez)


-Jun 12 07-
Hello all.

I've just packaged a binary driver for the Intel 536ep Modem. I currently have it installed on my system and it seems to install and uninstall with no problems.

It requires you use the (default) kernel package:
linux-image-2.6.20-16-generic

Intel536ep Driver for Feisty Fawn Ubuntu Release 1:
[http://www.mediafire.com/?f3rcu1de1ye](http://www.mediafire.com/?f3rcu1de1ye)



keywords:
ubuntu feisty 7.10 8.04 software soft softmodem win winmodem lin linmodem compile precompiled 536 ep

---

### Post by umairsaeed219 on 2007-06-25
How can i use this file after downloading
what commands are needed 
i m using 7.04
plz reply thanks

---

### Post by Sepero on 2007-06-25
Open a file browser window to where ever you downloaded the file. You should be able to install the package by simply clicking on it.

You can also install it on the commandline by typing:```
sudo dpkg -i intel536ep-feisty_2-Philippe.Vouters-23-02-2007_i386.deb
```

---

### Post by umairsaeed219 on 2007-06-25
Dear thanks for reply

i have clicked on the file to install it but package installer tells me an error that is 

**Error;Dependency is not satisifuable;linux-image2.6.20-16-generic**


what this error message is and how to correct it

---

### Post by Sepero on 2007-06-25
> **umairsaeed219 said:**
> i have clicked on the file to install it but package installer tells me an error that is 

**Error;Dependency is not satisifuable;linux-image2.6.20-16-generic**


what this error message is and how to correct itI have specifically set this driver to not install if you do not have the required packages. (linux-image2.6.20-16-generic, grep, and module-init-tools) You appear to not have the default kernel for Ubuntu Feisty 7.04.



Are you sure you're running Ubuntu Feisty 7.04?

Here is the HowTo guide for other versions of Ubuntu:
[https://help.ubuntu.com/community/DialupModemHowto/Intel536EP](https://help.ubuntu.com/community/DialupModemHowto/Intel536EP)



What is the output when you run the following from a shell/terminal?```
uname -r
```

---

### Post by umairsaeed219 on 2007-06-26
2.6.20-15-generic

---

### Post by Sepero on 2007-06-26
I don't know how you got that Kernel? Do you? Did you install from a prerelease Feisty CD?

Can you give me any more information at all?

You can force an install of the driver, but I cannot tell you whether it will work or not:```
sudo dpkg -i --force-all intel536ep-feisty_2-Philippe.Vouters-23-02-2007_i386.deb
```

---

### Post by umairsaeed219 on 2007-06-28
i dont know whether it is pre released or not because i dont have high bandwidth to download so i have got it copied from my friend

---

### Post by Sepero on 2007-06-28
I assume your friend has high-speed internet. You might try to ask him to download you a recent copy of the Feisty CD, then you can install that.

It will be more difficult, but your other option is to try compiling the driver yourself by following the HowTo I posted earlier.

I appreciate you writing in, umairsaeed219.

---

### Post by Sepero on 2007-07-13
Thanks for writing in, rehannasim. It's interesting that you should ask about the 537ep modem, because I had intentions of creating a package specifically for that modem too. Unfortunately, I do not have a 537ep modem, and the person that was supposed to help me create it - basically ceased communication with me.

The 536 driver will very likely not work with 537 modems.

Here is a link on how to build the 537 modem driver:
[https://help.ubuntu.com/community/DialupModemHowto/Intel537EP](https://help.ubuntu.com/community/DialupModemHowto/Intel537EP)


If you need help, please just contact me for assistance. I have sent you my email address and yahooIM ID in a private message to you. After you have the driver built, you may send me a copy of it. I can then package it and save others who are in your current position.

---

### Post by mmichalik on 2007-07-13
Thanks for writing this fix!  I am running Ubuntu 7.04 and I had to do the following to make it work.

1st. I downloaded the intel536ep-feisty_2-Philippe.Vouters-23-02-2007_i386.deb package from your download side.

2nd. I installed the slmodem pacakage via apt-get and it installed the other packages it needed.

3rd. Installed the intel536ep-feisty_2-Philippe.Vouters-23-02-2007_i386.deb

4th. Installed efax and gtk-efax via synaptic 

And the fax modem works!

GREAT help and thanks again!

---

### Post by Sepero on 2007-07-13
To mmichalik:
You're welcome. It's always good to have someone report in with success.
You should be able to run gtk-efax without the slmodem package(s). It runs fine on my system without them.

---

### Post by Turin Turambar on 2007-07-13
I too have a 15-generic version of kernel. I installed from the official Ubuntu feisty CD that got from their ship-it service.

I guess the 16-generic version is an updated one. The "15" is or WAS default.

---

### Post by woody22075 on 2007-07-15
like umairsaeed219 i am experiencing the same error when I try to install the driver package you referenced (have the smae chipset 536EP).  I also have the same kernel version (2.6.20-15-generic).  I obtained my copy of Feisty through the mail directly from Ubuntu.  Any recommendations for proceeding?  I'd apprecaite any advice.

---

### Post by Sepero on 2007-07-16
[size=4]To: woody22075 and Turin Turambar

I have made an experimental driver for you, and posted it here:[/size]
(OLD BROKEN URL DELETED, THIS IS RELEASE TEST 2.5)

```
sudo dpkg -i intel536ep-feisty_test-Philippe.Vouters-23-02-2007_i386.deb
```
[size=4]There is a possibility that this driver will work for you, but I cannot be certain. Please write back!!![/size]

---

### Post by Sepero on 2007-07-16
To: rehannasim

Please do not post in this thread with problems about 537ep modems. You should post in a 537 related thread or begin a new post.

Since you have already posted, I will tell you what MIGHT be an answer:
There is an error like that also caused with 536ep modems, and I have deducted the reason to an option called 'stupid mode'. Only 2 programs that I know of support this option and no other dialer that I know of works with 536ep modems.

The 2 programs are: wvdial and gnome-ppp

Here is a copy of the wvdial.conf from my 536ep driver package:
```
[Dialer Defaults]
#Modem = /dev/modem
Modem = /dev/536ep0
Baud = 115200
Init = ATZ
New PPPD = yes
Stupid Mode = 1
Auto Reconnect = off
#Carrier Check = no
Dial Attempts = 1

# MODIFY THE FOLLOWING 3 SECTIONS FOR YOUR CONNECTION
Phone = 1234567
Username = ExampleName
Password = ExamplePassword
```

---

### Post by Turin Turambar on 2007-07-17
I just wanted to confirm that I was able to install the test driver that Sepero made. :)

---

### Post by damir_1105 on 2007-07-20
Thanks very much. You did great job,

---

### Post by Desigen on 2007-08-08
Hi, it didn't work wit me.

I have an old kernel ( 15 ) not ( 16 ) 

what should I do? 
Do you recommend replacing the kernel with new one ?? 

Can you help me with this. 
Ubuntu without modem worth nothing. 

Another question about building modem driver. How can I do this if I don't have the headers file for the kernel ?? 

Thanks 
Bye

---

### Post by Sepero on 2007-08-08
post deleted

---

### Post by Desigen on 2007-08-11
Thanks a lot. it works. 

But I didn't want to post using Windows. It seems that Ubuntu have slower connection. I will try more and more using Ubuntu. 

I want to ask a question. Now I want to install Ubuntu on my Laptop but I'm afraid of some hardware not work. I did apt-get update and I want to make a backup of the apt application list. Where I can find this ?? 

Also, if I don't have a very fast Internet connection on my laptop I read some where I can use apt-get to generate a script file for the downloaded packages and using apt-zip "I think" to restore those on my laptop. My question. I can't find out how can I use this script when connecting form Windows. 

Sorry for asking.

---

### Post by Sepero on 2007-08-11
Desigen, you should post your questions that aren't related to Intel536 modem in a new thread. You're interest in Ubuntu is really cool and we all wish you the best of luck in discovering a more enlightening operating system.

---

### Post by Desigen on 2007-08-11
Okay, I will. 

Thank you a lot. 
Bye

---

### Post by CD Baric on 2007-08-24
Just  quick note to say Thanks - the driver loaded perfectly and after rebooting I found the modem instantly using minicom.

This was almost easier than using a hardware modem.

You Rock!

CD Baric

---

### Post by Sepero on 2007-08-25
That's a great compliment CD Baric, and I just want to say thanks to you and everyone else who has written in. I have put quite a bit of energy into making this driver package and including all documentation. This driver should install as easily (if not easier) than any Microsoft driver.

(And unlike most Microsoft programs, it should uninstall without leaving any garbage behind.)

---

### Post by mckinbg on 2007-09-17
Help !  Today I received Fiesty Fawn 7.04 in the mail and did a fresh installation.  Then I downloaded and install the Intel 536 ep modem driver module package.  It appeared to install.  I read success.txt and followed the instructions for modifying wvdial.conf and saving the modifications.  When I dial my isp all appears to go OK (using genome ppp) I get the following in the log

-> Sending: ATZ 
ATZ 
OK 
--> Modem initialized. 
--> Sending: ATDT6264000 
--> Waiting for carrier. 
ATDT6264000 
CONNECT 54666 
--> Carrier detected.  Starting PPP immediately. 
--> Starting pppd at Mon Sep 17 14:25:18 2007 
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied 
--> --> PAP (Password Authentication Protocol) may be flaky. 
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied 
--> --> CHAP (Challenge Handshake) may be flaky. 
--> Pid of pppd: 6374 
--> Using interface ppp0 
--> Disconnecting at Mon Sep 17 14:25:20 2007 
--> The PPP daemon has died: Authentication error. 
--> We failed to authenticate ourselves to the peer. 
--> Maybe bad account or password? (exit code = 19) 
--> man pppd explains pppd error codes in more detail. 
--> I guess that's it for now, exiting 
--> The PPP daemon has died. (exit code = 19) 
gary@gary-ubuntu:~$[/COLOR]

Got any suggestions??
mckinbg

---

### Post by Sepero on 2007-09-18
> --> The PPP daemon has died: Authentication error.
--> We failed to authenticate ourselves to the peer.
--> Maybe bad account or password? (exit code = 19)

Make sure you use the correct Username and Password.

---

### Post by ibbiprince on 2007-09-24
Will intel 536ep driver works with intel HaM modem?

---

### Post by Sepero on 2007-09-24
> **ibbiprince said:**
> Will intel 536ep driver works with intel HaM modem?
I've never heard of the "intel HaM" modem. You can tell if you have an intel 536 or 537 modem by running this on the commandline:
lspci | grep -e "537" -e "536"

If that command outputs anything, then yes you have a 536 or 537 modem. If it doesn't output anything, then you don't have one of those modems.

If your modem is 537EP, then get your driver here:
[http://ubuntuforums.org/showthread.php?t=552090](http://ubuntuforums.org/showthread.php?t=552090)

---

### Post by LMiddleton on 2007-09-30
Hello

I have recently installed Freespire Ver 2.0.0 based on Ubuntu Ver 7.04 
I have downloaded and attempted an install of the driver for the Intel536EP modem.
Install has proceeded as far as loading the driver with the modprobe command, when I keep getting this message:
Fatal: Error inserting Intel536DriverFor Feisty (/lib/modules/2.6.20-16-lowlatency/kernel/drivers/char /Intel536DriverFor Feisty.ko): Invalid module format
I have tried several times, and each time end up with the "Invalid module format" message.
Is there a way to proceed past this point to a functioning modem with Freespire?

With regards,

Lindsay

---

### Post by Sepero on 2007-09-30
LMiddleton, the module is the modem driver. If the module can't load, the modem will not work.

The FreeSpire team may have modified the Linux kernel too much from the one Ubuntu uses, or they use an entirely different kernel version.


"Below is a list of the proprietary software found in the regular, complete version of Freespire. All of these drivers, codecs and applications are NOT included in The OSS Edition."
...
"Freespire includes modem drivers for the Intel 536ep/537ep/537 chipsets."
[http://wiki.freespire.org/index.php/Summary_of_Proprietary_Components#Intel_Modem_Drivers](http://wiki.freespire.org/index.php/Summary_of_Proprietary_Components#Intel_Modem_Drivers)

Perhaps you installed the OSS edition of FreeSpire?

---

### Post by lexrexus on 2007-10-25
Hi -

I have downloaded Intel536ep Modem Driver Module package.
Have Dapper.  I learned that that won't work.
Thinking of clean install of later version so can have online access.

Will this modem package get my modem up w/7.10;  or should I send for a 7.04, Feisty disc ?

'

If I'm even more confused than I thought, please help.



'
'
Thank you.

---

### Post by MohammadBoozary on 2007-10-26
Hi All 

I Need intel536ep Driver For Ubuntu Gutsy Gibbon 7.10 please help me ! please :(

thanks !

---

### Post by Sepero on 2007-10-26
The current driver only works for Fiesty Fawn 7.04

I have not yet had time to compile the driver for Gutsy. I may Not have the time to release it for a month or two.

I will make an announcement on this thread when the Gutsy 7.10 driver is released.

---

### Post by lexrexus on 2007-10-30
> **Sepero said:**
> ...

I will make an announcement on this thread when the Gutsy 7.10 driver is released.

    
About how long before Gutsy driver announcement [so I can decide to wait, or to order a feisty disc]?
:popcorn:

---

### Post by Sepero on 2007-10-31
About a month or two

---

### Post by lexrexus on 2007-10-31
> **Sepero said:**
> About a month or two

Thank you for your diligence in keeping up w/this thread!  Fiesty it shall be!

---

### Post by zarej on 2007-11-15
The same driver for fiesty works on gutsy as well, you need to download driver from [http://linmodems.technion.ac.il/packages/intel/Philippe.Vouters/intel-536EP-2.56.76.0_23_02_2007.tgz](http://linmodems.technion.ac.il/packages/intel/Philippe.Vouters/intel-536EP-2.56.76.0_23_02_2007.tgz) and follow the next tutorial for fiesty [https://help.ubuntu.com/community/DialupModemHowto/Intel536EP](https://help.ubuntu.com/community/DialupModemHowto/Intel536EP)

---

### Post by imran saeed on 2007-11-17
hello! nice to see driver for 536 ep for 7.04, i have 536 ep and just installed 7.10 along with win xp dual boot. i now require a driver compatible with 7.10. Thanks

---

### Post by Sepero on 2007-11-18
Thank you for your interest. Unfortunately, the 536EP driver for Gutsy Gibbon 7.10 has not yet been released. I have recently gotten some free time and I am currently upgrading my personal system from Feisty to Gutsy.

Hopefully, I should have the Gutsy 536EP driver ready within the next 2 weeks.

PS.
Usually I release sooner than expected, but I do not like to be too optimistic.

---

### Post by imran saeed on 2007-11-18
Hello! thanks to Zarej problem is solved, the same driver that works for 7.04 also work for gutsy 7.10. Please see thread no. 42
Thanks again zarej And Sepero.

---

### Post by imran saeed on 2007-11-19
Hello! I have installed 7.10 with 536ep modem,using same driver as for 7.04 , it was working fine until the card expired, when i tried to log in with a new card it gives same error massage that is described in thread no.30   Although i am entering correct user name and password. I got massage exit code 19. Mckinbg have you found a solution? please reply. Thanks.

---

### Post by imran saeed on 2007-11-20
Hello! problem is solved, i have to configure networking options on the same lines as genome ppp. online again.

---

### Post by Sepero on 2007-11-21
New driver released for Gutsy. Please see the top of the thread.

---

### Post by cofeelover on 2007-11-23
Hello! thanks sepero cool work using gutsy is really enjoyable, just like a hot nice cup of coffee! isn't ?

---

### Post by Sepero on 2007-11-25
Hope everyone had a happy thanks giving. :)

---

### Post by lexrexus on 2007-11-28
> **lexrexus said:**
> Thank you for your diligence in keeping up w/this thread!  Fiesty it shall be!

THEN
I downloaded and installed successfully 7.04 Feisty.  Downloaded and successfully? installed 2nd vouters Intel536ep driver-package (2 times).  Followed directions in 'success' text.  When terminal 'wvdial' get close to this:

" warning could not modify /etc/ppp/pap-secrets
 pap may be flaky
 chap may be flaky
 using interface ppp0
 authentification error
 maybe bad acct. or password?
 exit code 19
 ppp demon died."    

username and password are  correct.
Does any of that other stuff above mean anything else is off that I might fix?

HELP Thank you!!!=D>

---

### Post by Sepero on 2007-11-29
Here is the output from my system (now Gutsy). Notice that the output is very similar to what you posted.
```
$ wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT8297000
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT8297000
WvDial Modem<*1>: CONNECT 26400
WvDial<*1>: Carrier detected.  Starting PPP immediately.
WvDial<Notice>: Starting pppd at Thu Nov 29 00:03:22 2007
WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky.
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky.
WvDial<Notice>: Pid of pppd: 6575
WvDial<*1>: Using interface ppp0
WvDial<*1>: local  IP address 209.4.45.173
WvDial<*1>: remote IP address 207.22.166.12
WvDial<*1>: primary   DNS address 207.22.166.61
WvDial<*1>: secondary DNS address 207.22.166.2
```


At the end, I was connected (I'm connected right now).

My only suggestion is to double (triple?) check your username and password in your /etc/wvdial.conf file.
```
Username = ExampleName
Password = ExamplePassword
```


I truly hope that helps.

---

### Post by lexrexus on 2007-11-29
> **Sepero said:**
> Here is the output from my system (now Gutsy). Notice that the output is very similar to what you posted.
```
$ wvdial
...
...
At the end, I was connected (I'm connected right now).

My only suggestion is to double (triple?) check your username and password in your /etc/wvdial.conf file.
[code]Username = ExampleName
Password = ExamplePassword
```


I truly hope that helps.

=======

Thank you. 
 Could it be my isp doesn't 'take' wvdial stuff (they haven't returned my call  :  [)?
 
 Or could it be something to do w/my computer-name not being added to some group or groups on my machine  (somewhere during this epic I ran into a reference to something like that but can't find/remember where)??

 My Feisty install is fresh and on a clean hard drive.      


 ???

=======

[-o<[-o<
Lexrexus

---

### Post by Sepero on 2007-11-30
I really feel bad for ya Lex. Unfortunately I don't think it has anything to do with groups or permissions. If you think it's a problem with permissions, then run wvdial as root (because root has unlimited permissions). When you get it sorted out, the you can resume wvdial  as regular user.
$ sudo wvdial

I've never heard of anyone complain about an ISP that doesn't accept wvdial, but I know there are some that exist. Any ISP that requires you to connect using a 'special' program will likely not work with wvdial. (AmericaOnline? NetZero?)

I could only find one piece of valuable difference between your output and my output:
> **lexrexus said:**
> authentification error
 maybe bad acct. or password?

If your ISP doesn't use a 'special' program to connect, then my best guess is an error in name/passwd.

---

### Post by tominsf on 2007-12-04
The gutsy version of the 536ep driver didn't work for  me.  I downloaded the installation package, clicked on it to install it, and eventually got a message that it hadn't installed properly.

After a lot of playing around, this is what I found.  The package installer script (or whatever does the installation - I only half know what I'm talking about, and half is probably a charitable estimate) seems to modprobe Intel536, when in fact it should modprobe Intel536DriverForGutsy.  Likewise, the boot item in /etc/modules is written as Intel536, when it should be Intel536DriverForGutsy.

With that change, the driver now works for me.  I don't see how it could have worked at all for anyone as it was, so I don't understand why there hasn't been any feedback on this here yet.  Anyhow, here's mine.

---

### Post by tominsf on 2007-12-04
I should add that I'm very grateful for this driver, and really appreciate the work that went into it.  The ability to use my fax modem card for receiving the occasional fax was the last thing tying me to Windows in any way.

---

### Post by Sepero on 2007-12-04
Wow tominsf, you're 100% correct. I made a mistake in creating this driver and you're the first to point it out. It shouldn't work for anyone unless they did a modification like you did. I'm upset that no one said anything sooner, but I'm also sorry to everyone for the mistake. I will upload a modified version asap.

---

### Post by Sepero on 2007-12-04
The new package has been uploaded.

---

### Post by PhilJ on 2007-12-16
Sepero.
  thank you for your work with this package. Much appreciated, just what I needed.for my faxing

thanks again

Phil

---

### Post by markdarb on 2007-12-24
I installed the latest package for Gutsy without any problems. I've connected to the Internet with wvconfig, pppconfig/pon and Ubuntu's in-built network manager; however, I haven't been able to download anything through the connection. Firefox just keeps "looking up" websites for ages, and I have a similar problem in the Synaptic Package Manager when trying to load reload the package list: it just sits there and does nothing. So either something's wrong with the connection or the computer doesn't know how to use the conection properly; programmes seems to be sending requests, but don't seem to receive any data in return. Any suggestions on what might be wrong and how to fix it?

By the way, Ubuntu is newly installated on this particular machine. This package is the only one I've installed.

Thanks,
Mark.

(Please note, unless there's a reply in the next few hours I won't be able to reply for another ten days)

---

### Post by markdarb on 2007-12-24
Never mind; I've solved the problem. I have a broadband modem/router which we use for a wireless network. The computer was trying to get to the Internet through the ADSL modem instead of throught the dialup connection. Unplugging the computer from the modem solved the problem, although it's only a temporary fix because I need the computer hooked back into the network.

On another note wvdial initially worked, but now can't authenticate. Ubuntu's builtin dialup programme doesn't work (the computers seem to get caught in some sort of loop while still initially connecting). I'm currently using pppconfig, pon and poff. This isn't ideal (I'm having to put two launchers on every user's desktop) but it does the job for now.

Anyway, thanks for the great package!

---

### Post by Sepero on 2007-12-25
Before I saw your post about the wifi resolution, I was going to say that your modem may be faulty, the _hardware_. Thanks for following up though, it may very well help someone.

As for your wvdial.conf problem- copy, modify, and use the one that I included with the package. /usr/share/doc/intel-gutsy/wvdial.conf Just fill in the 3 slots- phone# username passwd

If you haven't read the /usr/share/doc/intel-gutsy/success.txt file, I suggest you read it. (I made it short as possible.) Gnomeppp might be a better choice for your 'multiuser' needs. Best of luck. :)

---

### Post by biker955 on 2008-02-26
Ok I am having problems installing this using a fresh Gutsy install, I have the 2.6.22-14-386 kernel and tried copying the link to that directory after the install failed, but the modproble fails with :-
FATAL: Error inserting Intel536 (/lib/modules/2.6.22-14-386/kernel/drivers/char/Intel536.ko): Invalid module format


Any help please.

---

### Post by Sepero on 2008-02-27
> **biker955 said:**
> Ok I am having problems installing this using a fresh Gutsy install, I have the 2.6.22-14-386 kernel and tried copying the link to that directory after the install failed, but the modproble fails with :-
FATAL: Error inserting Intel536 (/lib/modules/2.6.22-14-386/kernel/drivers/char/Intel536.ko): Invalid module format


Any help please.
Thanks for writing in. :)

I am thankful because you have proven that my package passes some form of trial testing.

You were using an inappropriate kernel, so you had to -force install. After -force install, the module did not work. If it did work, I would have found that quite surprising.

The reason it will not work is because I compiled the module for the 'generic' only series of kernel.

You now have two options:
1. Compile the module yourself for the '386' kernel.
2. Install (return?) to the default 'generic' kernel, then install the driver package.

I'm sorry that I cannot provide a driver for all possible kernels. If you would be interested in helping out, please let me know.

---

### Post by ikt on 2008-04-04
Any news if this will work with 8.04

---

### Post by Sepero on 2008-04-11
> **ikt said:**
> Any news if this will work with 8.04
It will not.

I will make a new release soon after Hardy 8.04 is released. Bookmark and check back soon.

---

### Post by MohammadBoozary on 2008-04-26
Hi !

I need Intel536EP Driver for Ubuntu 8.04 Hardy Heron, Please Help Me !

Thanks :)

---

### Post by Wolf_45 on 2008-04-30
> **Sepero said:**
> It will not.

I will make a new release soon after Hardy 8.04 is released. Bookmark and check back soon.

Thanks Sepero! Feisty, Gutsy, and now Hardy - your modem drivers have kept me plugging along.  One of these days I'll move into the 'High Speed' world but until then, you da Man!

---

### Post by Sepero on 2008-05-12
The Unofficial Hardy driver is now officially released. ;)

Thanks to everyone who writes in with moral support. Enjoy guys and gals!

---

### Post by Drakelet on 2008-05-12
Does that only work for 32bit then?  Would it work on 64bit?

Either way, AWESOME!  THANKS!  I've spent hours trying to get mine working, nearly bought a new modem.  I want your babies... if it works. :D

---

### Post by Drakelet on 2008-05-12
Sorry, no babies.  Didn't work... quite.

I went back to 32bit, as it didn't work with 64bit.  It all went fine until I tried to do the wvdial stage.  All the details etc were correct.  This is what the Terminal showed:
[img]http://i268.photobucket.com/albums/jj23/JGibbins92/Ubuntu/dialerror.gif[/img]

The wvdialconf.log says:
> Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.



Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.


The strange thing is that it does dial - I can hear the modem beeping it's way along, and the phone line is engaged.  Yet it seems to keep going over the same beeps again, then stopping.  Hard to explain as I don't understand the beeps, but it gets past the dialling stage.

---

### Post by Wolf_45 on 2008-05-12
> **Drakelet said:**
> 

The strange thing is that it does dial - I can hear the modem beeping it's way along, and the phone line is engaged.  Yet it seems to keep going over the same beeps again, then stopping.  Hard to explain as I don't understand the beeps, but it gets past the dialling stage.

Hmmmm...sounds like something isn't getting passed off from wvdial to ppp - my terminal (still on Gutsy) looks pretty much like yours except after "using interface ppp0" mine comes up with local and remote IP's.

In wvdial.conf do you have Modem = /dev/modem commented out and immediately under it, Modem = /dev/536ep0 ?  Noooooo...if your modem is dialing, I don't think that'd do it.  It almost sounds like a simple "username/password not set" problem, but that was probably the first thing you checked.

Let me finish upgrading and then throw it in - $10 says it's a simple "Duh, I forgot to...!" thing.  :-)

---

### Post by Drakelet on 2008-05-12
Yeah username/password is correct.

My wvdial.conf looks like this:
> [Dialer Defaults]
#Modem = /dev/modem
Modem = /dev/536ep0
Baud = 115200
Init = ATZ
New PPPD = yes
Stupid Mode = 1
Auto Reconnect = on
#Carrier Check = no
Dial Attempts = 1000

Then my login stuff below.

So yeah, it is strange.  It dials perfectly normally, but just doesn't succeed.

---

### Post by mssaleh5 on 2008-05-13
Hi there.
I had the same problem but in a totally different context. You only need to run wvdial at least once as a root, with sudo, or you need to configure pppd manually through pppconfig. wvdial uses a running pppd and ppp process. By default it is ppp0, so when you create a new connection with pppconfig, make sure to use ppp0 for the name. You also need to choose CHAP as the authentication method.
Good luck!

---

### Post by Sepero on 2008-05-13
> **Drakelet said:**
> Does that only work for 32bit then?  Would it work on 64bit?
Only 32bit. Unless Intel makes another 64bit release for Linux (which is unlikely), this modem will never work under 64bit.


After installing, there should be a small window that pops up that says to read this file
/usr/share/doc/intel536ep-hardy/success.txt


It should solve wvdial problems, for most people. It will tell you to copy the file 
/usr/share/doc/intel536ep-hardy/wvdial.conf
to
/etc/wvdial.conf


Then to dialout, simply edit the correct info into
/etc/wvdial.conf


So check out that file, I made it short.
/usr/share/doc/intel536ep-hardy/success.txt



> Either way, AWESOME!  THANKS!  I've spent hours trying to get mine working, nearly bought a new modem.  I want your babies... if it works. :D
You never know. Perhaps we can work out a deal. I might sell them to you at a discount. ;-)

---

### Post by Drakelet on 2008-05-13
> **mssaleh5 said:**
> I had the same problem but in a totally different context. You only need to run wvdial at least once as a root, with sudo, or you need to configure pppd manually through pppconfig. wvdial uses a running pppd and ppp process. By default it is ppp0, so when you create a new connection with pppconfig, make sure to use ppp0 for the name. You also need to choose CHAP as the authentication method.
Hmm, OK, I kinda get that.  Not.  Well, I'll copy it down and try some things, I think I understand the problem, and the solution. :)

> **Sepero said:**
> After installing, there should be a small window that pops up that says to read this file
/usr/share/doc/intel536ep-hardy/success.txt


It should solve wvdial problems, for most people. It will tell you to copy the file 
/usr/share/doc/intel536ep-hardy/wvdial.conf
to
/etc/wvdial.conf


Then to dialout, simply edit the correct info into
/etc/wvdial.conf


So check out that file, I made it short.
/usr/share/doc/intel536ep-hardy/success.txt
I can read instructions you know! :P Did all of that but it didn't work. :(

> **Sepero said:**
>  You never know. Perhaps we can work out a deal. I might sell them to you at a discount. ;-)
LOL

---

### Post by Drakelet on 2008-05-13
No luck chuck.  Tried it all but same problem.  Same stuff in the Terminal each time after "sudo wvdial", just with different Pid.

These are my pppconfig settings.  Look OK?
[IMG]http://i268.photobucket.com/albums/jj23/JGibbins92/Ubuntu/pppconfig1.png[/IMG][IMG]http://i268.photobucket.com/albums/jj23/JGibbins92/Ubuntu/pppconfig2.png[/IMG]

I've just downloaded the Gnome-PPP .deb from package.ubuntu.com, I'll try that now.

EDIT1:

Gnome-PPP installed without a hitch.  Plummed in all the details, and... the same as wvdial.  After about 30 seconds or so it reverted back to the dial screen, and the log was identical to that of the wvdial I've posted before (with different Pid of course).

[IMG]http://i268.photobucket.com/albums/jj23/JGibbins92/Ubuntu/gnomeppp1.png[/IMG]

One thing I noticed though - it didn't detect any modems.  Is this normal, or does this suggest the modem is not installed correctly?  I followed the instructions to the letter, and all the files were there.  The 536ep0 file does exist:

[IMG]http://i268.photobucket.com/albums/jj23/JGibbins92/Ubuntu/devfolder.png[/IMG]

Any thoughts?

---

### Post by Sepero on 2008-05-14
Copy the file:
/usr/share/doc/intel536ep-hardy/wvdial.conf
to
/etc/wvdial.conf


Then enter your "username" "password" and DIAL OUT (OUT) "phone number" into
/etc/wvdial.conf


Then go to a commandline and enter
wvdial


If it still doesn't work, send me an exact copy of your /etc/wvdial.conf file in a private message for me to review.

---

### Post by Drakelet on 2008-05-14
> **Sepero said:**
> Copy the file:
/usr/share/doc/intel536ep-hardy/wvdial.conf
to
/etc/wvdial.conf


Then enter your "username" "password" and DIAL OUT (OUT) "phone number" into
/etc/wvdial.conf


Then go to a commandline and enter
wvdial


If it still doesn't work, send me an exact copy of your /etc/wvdial.conf file in a private message for me to review.
I'd done that.  And have done it again.  Nothing.

Is there any reason to PM you the [COLOR=Black]wvdial.conf[/COLOR]?  It is IDENTICAL, except with the phone number, username and password different.  They're in the exact same areas with no spaces etc.

What is ppp btw?  Like ppp0, pppd, pid etc?

EDIT: I'll try putting the username etc in the /usr/ one.  Probably won't make a difference, but hey, worth a try isn't it?  I'll keep a backup of the original don't worry.

---

### Post by Sepero on 2008-05-14
> **Drakelet said:**
> Is there any reason to PM you the [COLOR=Black]wvdial.conf[/COLOR]?  It is IDENTICAL, except with the phone number, username and password different.
The reason is so I can verify that you entered the information correctly.

Also, post the output of when you run wvdial. Either the information you entered is wrong, or your modem is broken.

---

### Post by Drakelet on 2008-05-14
The modem isn't broken.  I'm using it now, just on Windows.

The screenshot of the wvdial results are on page 1 of this thread.
Or, here: [http://i268.photobucket.com/albums/jj23/JGibbins92/Ubuntu/dialerror.gif](http://i268.photobucket.com/albums/jj23/JGibbins92/Ubuntu/dialerror.gif)
It's the same sudo or non-sudo.

I'll PM you the .conf if it'll make you happy. :P

---

### Post by PamBZ on 2008-05-24
Hi - I have been doing a lot of experimenting, researching and communicating and reading posts on the Intel536ep modem for many months.
I was using Ubuntu 7.04 and the driver 2.56.76.0 driver and followed the How to/Intel536ep Dial up Modem instructions.  I connected and was getting good speed (5kb/s).

Then my modem died and I had to get a new one so I bought a new intel536ep modem.  My same driver would not work.  I cried and gave up
for two months.  

Yesterday I updated to Ubuntu 8.04 and downloaded the new driver update (intel536ep-hardy).  The driver installed automatically.  It was great!
And I became Happy again.

I entered the appropriate data into my /etc.wvdial.config but I could
not connect.  So I toyed and researched and read and communicated with my isp provider and others to try to solve the problem. 

 What worked for me was entering information provided by my isp
into the /etc/resolv.conf (the server name and dns addresses) and then entering the username and password in the /etc/ppp/pap-secrets file (at the bottom of the page).

I connect but really slowly.  I tried a few different initialization strings and have gone from 4800 to 7200 connection speed.  That is still unacceptable.  

I don't know what the problem is.  

I am grateful for the driver update and to be able to connect.  And this is all fun.  I get the same messages some of you do ... and I have never been able to get that to resolve no matter what I have tried.

CONNECT 7200
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat May 24 17:29:08 2008
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.

What is neat is that I could never get the network connection to work for me ... but I can now.  It dials out and connects - so cool.  Again entering the dns numbers was what made the difference for me.

I have a pentium intel 111, maximum 512mb ram and 133mhz speed.

It was suggested to me to try a topic chipset modem.  So I will research those.  However how come I was able to run at acceptable speeds before and not now?  Same type of modem, new driver, wvdial ... don't know!

Suggestions welcome!

---

### Post by Jei_El_Key on 2008-05-25
Hello people. (y) I have problem , 1st im install this package for my Ubuntu 8.04 Hardy, and works , but always i restart or shutdown, the system don´t recognize my modem, curiously need to reinstall the package, and works again. :confused: ,What should I do to make it work? I need a quick response. thanks for your attencion  :)

---

### Post by PamBZ on 2008-05-27
Hi

It turned out I have a bad phone line.  I played with different phone line cords
and my connection speed to my isp went from 4800 to 4533.  So things are better but not perfect.

Its noisy and I have to make several attempts before I can connect.  We do have really bad phone lines here.  I am concerned because the modem made these kinds of noises the last time before it kicked the bucket.  But a new modem ... doing this is not good.

I did learn how to silence the modem by putting M0 after AT in the initialization string
M0 silences the modem.  I learned this on linux faq page 5.  I had to edit the /etc/wvdial.conf file as editing the AT string in the chatscripts file did not do it for me.

I still get these messages: don't know why, 

Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue May 27 12:38:13 2008
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.

There is lots to read that is already available and lots of trial and error with my own computer.

I understand now too I could not install the new Hardy driver update because my Ubuntu 7.04 is lacking the appropriate kernel ... 

Thanks for all the posts ... they were all helpful ... and often times I just had to go back and read and reread and find more things to read in readme.txt's, faq's and helpfiles etc .... before I found what works

---

### Post by Pomble on 2008-05-29
I'm completely new to Linux, so please bear with me.  I'm running Ubuntu Hardy 8.04, with kernel 2.6.24-17-generic.  

I've tried to install the package for my 536ep modem, and get as far as the package installer telling me that I should read the "success" text tile.  However, the device doesn't seem to want to install.  Is this to do with my kernel version, or am I doing something else daft?

---

### Post by Sepero on 2008-05-29
deleted

---

### Post by Drakelet on 2008-05-30
How would I get 2.6.24-16-generic?

---

### Post by Sepero on 2008-05-30
> **Drakelet said:**
> How would I get 2.6.24-16-generic?

It should be available on the LiveCD.

---

### Post by Drakelet on 2008-05-30
Cheers Sep.

---

### Post by Sepero on 2008-05-31
A new driver has been uploaded for the newer Hardy Kernel. Check the top of the thread.
[http://ubuntuforums.org/showpost.php?p=2827908&postcount=1](http://ubuntuforums.org/showpost.php?p=2827908&postcount=1)

---

### Post by Drakelet on 2008-05-31
Let's hope this one will work. :D

EDIT: Looks like I had the previous version, just it didn't work.  Obviously just my modem or PC.  Oh well, thanks for all the support and drivers!!

---

### Post by Wolf_45 on 2008-06-07
Hi folks;

Yeah, it's been a while.  :-)

"For the record", I've been using these drivers since Feisty, and I've never gotten any method to work, other than opening a terminal and using wvdial.  Not "sudo wvdial", just plain old wvdial, and once it connects, minimize the terminal, and go my merry way.

And yes, I get the same stuff as well:

wolfeyes@Master:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATM0
ATM0
OK
--> Modem initialized.
--> Sending: ATDT#######
--> Waiting for carrier.
ATDT#######
CONNECT 21600
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Fri Jun  6 18:44:31 2008
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 5878
--> Using interface ppp0
--> local  IP address [www.xxx.yyy.zzz](www.xxx.yyy.zzz)
--> remote IP address [www.xxx.yyy.zzz](www.xxx.yyy.zzz)
--> primary   DNS address [www.xxx.yyy.zzz](www.xxx.yyy.zzz)
--> secondary DNS address [www.xxx.yyy.zzz](www.xxx.yyy.zzz)

Not being able to modify pap-secrets or chap-secrets hasn't had any apparent effect, so I quit looking for reasons a long time ago - if it ain't (apparently) broke, don't fix it!

Ending the connection is as easy as bringing up the terminal window, and hitting <Ctrl+C>.

And yes, I know the connection speed sucks.  My wife (running an Intel536EP modem on Win98SE) doesn't get much better - 26400, 28800 tops on a good day.  Personally, I blame Qwest's phone lines.  :-)

Wolf

---

### Post by Sepero on 2008-06-07
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.


This is normal with Intel536ep. Thanks for helping out Wolf.

---

### Post by Wolf_45 on 2008-06-08
> **Sepero said:**
> --> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.


This is normal with Intel536ep. Thanks for helping out Wolf.

That's what I mean - I've been getting that since Feisty (my first Intel/Ubuntu combination).  I don't know that I'd call it "normal", but it certainly seems to be "routine", and doesn't appear to have a negative effect.

One of these days I hope to "really" be able to help!

---

### Post by DarkW0lf on 2008-06-15
Don't feel bad wolf I have getting those errors since Drake or maybe I think 04.10 (what critter was that one Breezy ?)

But in my case it may be ISP related, I don't think they use any auth other than user/password.

---

### Post by Wolf_45 on 2008-06-16
> **DarkW0lf said:**
> Don't feel bad wolf I have getting those errors since Drake or maybe I think 04.10 (what critter was that one Breezy ?)

But in my case it may be ISP related, I don't think they use any auth other than user/password.

That's possible, DW, I think mine's the same way.  They're certainly making a stink about not using any other kind of secure settings on email!

I believe it's already been mentioned, but if someone is REALLY bugged by seeing those error messages, they CAN be eliminated.  I'm dubious as to the security of it though.

Simply make /etc/ppp/chap-secrets & /etc/ppp/pap-secrets universally read/writeable ( -rw-rw-rw ).  After doing that, here's my "test connect" terminal window:

wolfeyes@Master:~$ wvdial
--> WvDial: Internet dialer version 1.60

--> Initializing modem.
--> Sending: ATM0
ATM0
OK
--> Modem initialized.
--> Sending: ATDT#######
--> Waiting for carrier.
ATDT#######
CONNECT 21600
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Jun 15 21:59:14 2008
--> Pid of pppd: 6805
--> Using interface ppp0
--> local  IP address 199.232.90.7
--> remote IP address 199.232.42.98
--> primary   DNS address 206.192.24.20
--> secondary DNS address 140.186.1.4
Caught signal 2:  Attempting to exit gracefully...
--> Terminating on signal 15
--> Connect time 0.2 minutes.
--> Disconnecting at Sun Jun 15 21:59:29 2008

BINGO!  Computer no gripey :-)  Being paranoid though (and since I've never had problems with it in the first place), I went ahead and changed them back to their original -rw------- settings.

It works fine either way (in spite of the lousy phone service!), so I quit worrying about it a long time ago.

---

### Post by Sepero on 2008-06-18
Ubuntu Forums was a great place for me to start releasing these drivers, but now the thread is becoming long. There are posts that should be deleted to speed finding answers, and I cannot do this because I do not have the privileges.

In an effort to increase benefit to the users, I have created a google group where I should start posting future releases. On this group I wish to maintain a FAQ, which members may help edit. If you wish to find future help, or possibly help others, please join the group.

[http://groups.google.com/group/ubuntu-modems](http://groups.google.com/group/ubuntu-modems)

---

### Post by MohammadBoozary on 2008-07-16
Hi All :)
I'm user of Intel536EP.
I need Source of this modem for Installing That from Source code in
Ubuntu and other distros !
Please Give Me Intel536ep Source driver !

HELP ME PLEASE !

---

### Post by Sepero on 2008-07-16
I sent you an email Mohammad. I hope to hear back from you.

---

### Post by Sepero on 2008-07-17
Hardy driver 3 released

---

