---
title: "HowTo Install the Citrix ICA client"
date: 2008-08-15
forum: General Help
---

### Post by mgmiller on 2008-08-15
This is useful for gotomeeting.com and Citrix presentations.

Edit:  I have discovered that this is **not** useful for gotomeeting.com presentations.    ](*,)  After discussing the problem with the gotomeeting people, who are owned by Citrix, but didn't know the Citrix Linux ICA even existed, I was told their software people would "look into" including a Linux capable version for a future build.  Since they now do a mac version that doesn't use active-x, this shouldn't be too big a stretch.  Hopefully they can do it before pigs learn to fly.  In the meantime, for this type of thing, Yugma is Linux, Mac and Windows friendly.  For groups of up to 10, it's free and for larger groups is less expesive than gotomeeting.   [www.yugma.com]("http://ubuntuforums.org/www.yugma.com")

That being said, it's still good for Citrix, so, on with the show.....

The following HowTo is a synopsis of a video presentation available here:

[http://community.citrix.com/display/~ruiguoy/2008/06/19/How+to+install+and+use+Citrix+ICA+client+on+Linux]("http://community.citrix.com/display/%7Eruiguoy/2008/06/19/How+to+install+and+use+Citrix+ICA+client+on+Linux")

I am sure some of these steps could be more efficiently performed from the terminal, but I wanted to create mostly gui instructions to make it as noob friendly as possible.

It is also possible that getting the .rpm version of the file and converting it to a .deb using alien, might be easier, but I found some online discussions where people had problems with the install when doing it that way, so I am using the tar.gz instructions here.

So, here we go....

First step is to get the tar.gz file from here:

[http://www.citrix.com/English/ss/downloads/details.asp?downloadId=3323&productId=186](http://www.citrix.com/English/ss/downloads/details.asp?downloadId=3323&productId=186)

IMPORTANT!
You want the en.linuxx86.tar.gz one with x86 client - requires OpenMotif 2.2.x 

Save it to your desktop.

Extract en.linnuxx86.tar.gz by double clicking it.
Click the Extract button at the top.
Click create folder and in the blue field that says "Type name of new folder"
put in "icainstall" (without the quotes) hit enter and then click the Extract button in the lower right corner.

You will now have a folder on your desktop named icainstall.

Open a terminal and cd to the icainstall directory.
```
cd Desktop/icainstall/
```type the following command:
```
sudo ./setupwfc
```Give it your regular password when requested.

It should look like this:
```
Select a setup option:

 1. Install Citrix Presentation Server Client 10.6
 2. Remove Citrix Presentation Server Client 10.6
 3. Quit Citrix Presentation Server Client 10.6 setup

Enter option number 1-3 [1]: 
```Enter the default of 1, then at the following prompts for default location and integration with gnome and kde also use the defaults.

At the end it will present with the setup options choices again, just choose #3 to exit.

At the command prompt, enter the following:
```
sudo apt-get install libmotif3
```Close the terminal.

Alternatively, using the gui, you can install the  libmotif3 package from synaptic.  But since the terminal was already open, I figured, what the heck.  

All Done!!!

You will now have the entries... Applications > Internet > Citrix CNA and Citrix Presentation Server Client.  You will also have ICA enabled in Terminal Services Client and the Citrix plugin should be in Firefox.

---

### Post by ds[de] on 2008-08-15
Sweet, thanks a lot :o)

Earlier today I reminded myself to install the client so I can access my office from my notebook, too.

Glad I found your thread.

Regards,
ds[de]

---

### Post by mgmiller on 2008-08-16
You're welcome.

I have a gotomeeting.com thing coming up next Friday, so I needed to figure this out.  

Since I couldn't find anything in our forums, I decided to make the HowTo for future reference for everyone.

Glad it helped you.

---

### Post by shutslar on 2008-08-30
Thank you so much.  This HowTo is so easy to follow that my 13 y.o. daughter actually installed the client for me while I was doing a Honey-Do for her mother.

I really appreciate it.
Best Regards!

---

### Post by mgmiller on 2008-08-31
You're welcome.  I try to make my instructions as clear and unambiguous as possible.  Since your 13 y.o. daughter followed them easily, I feel I was successful this time.


All clicks on the gold star in the lower right corner of my HowTo to give me another thank you point are cheerfully accepted.

---

### Post by sphillips53 on 2008-09-11
I followed the instructions and installed the Citrix client and libmotif3. The Citrix applications show up in the Gnome menu and on the plugin page for Firefox, but when I try to run an ICA link form a website the client does not run. If if run wfcmgr in a terminal window I get multiple errors about loading fonts ending with "segmentation fault".  If I run wfica in the terminal I get the error message: 
Error: 12 (E_MISSING_INI_ENTRY)
Please refer to the documentation.
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Error: Aborting: no fontset found
All I can find in the documentation is that this indicates there is a problem with the configuration file, but not how to correct it.
Do you have any idea how to fix this?

---

### Post by mgmiller on 2008-09-11
Make sure you have multiverse enabled in your repositories. 
System > Administration > Software Sources

I suspect you need to add the msttcorefonts package, but a better solution might be just to install the ubuntu-restricted-extras which will give you those and lot more stuff that is handy.

So, for everything:
```
sudo apt-get install ubuntu-restricted-extras
```

Or, just for the fonts:
```
sudo apt-get install msttcorefonts
```

---

### Post by sphillips53 on 2008-09-11
Thanks for the suggestion.  Unfortunately it did not help.

---

### Post by mgmiller on 2008-09-11
You may find some useful tips here:
[http://forums.citrix.com/thread.jspa?threadID=86630](http://forums.citrix.com/thread.jspa?threadID=86630)

There may also be some help here:
[http://sudan.ubuntuforums.com/showthread.php?t=376735&page=4](http://sudan.ubuntuforums.com/showthread.php?t=376735&page=4)

---

### Post by ozzyprv on 2008-11-02
Thank you,it worked great for me!

---

### Post by elanning on 2008-11-28
Greetings,

I was able to download and install the Citrix ICA client, as far as I can tell it went fine.  However when I start up firefox, I am able to login to my work's website that shows me my applications, but when I click on one, FireFox asks if I want to download the file or to open it, but it doesnt know what to open it with.  From what I have been reading, if the install was truly successful there should be something Citrix related in the "Plug-ins" area of FireFox?

I used these instructions for my installation, accepting the default install location:  [https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)

Please advise.

---

### Post by ericesque on 2008-11-28
yeah, it should open with wifica.sh

a default installation should put wifica.sh in the following location:
~/ICAClient/linuxx86/wifica.sh

Try browsing to the file when you're prompted to 'open with'.  Also make sure the permissions are set correctly and that wifica.sh is executable in the file's properties.

Working from home is awesome!

---

### Post by elanning on 2008-11-28
You were right, it turned out to be a permissions issue.  Thanks for the info on that file, I had no idea what it actually opened with.

---

### Post by Zorael on 2008-12-14
It installed nicely for me but I get an error message when I try to connect via the Firefox plugin.

> *Dynamic resources are not supported in this version of the Web Client. The resource will be ignored. (5030112)*

It continues to load after that, but trying to open up any resources via the web interface just ends up at another login screen, whereas if I log out and move to an adjacent Windows machine and retrace the steps it works without a hitch. Again, the presentation client itself is spawning the error message, so the application is properly evoked and ends with above error message output. :<

Any ideas?

---

### Post by jlh on 2008-12-20
I am trying to install the Citrix client using the Citrix .rpm file converted using alien to the .deb file.  When I do that, I get the following error immediately after 

Setting up icaclient (10.6.2):

[: 1943: ==: unexpected operator

Can anyone tell me what that means and how to fix whatever is blocking the installation.

Running Ubuntu 8.04 on a Thinkpad T30.

Thanks.

---

### Post by mgmiller on 2008-12-20
> I am trying to install the Citrix client using the Citrix .rpm file converted using alien to the .deb file. 

If you refer back to my original instructions in the howto, you will note that I mentioned the rpm to deb installs have some known issues.  Did you try doing the install with the tar.gz file as I outlined at the beginning of this thread?

---

### Post by jlh on 2008-12-20
I sure did.  That was unsuccessful, and that's why I opted to try the .rpm to .deb approach.

---

### Post by mgmiller on 2008-12-20
When I wrote the howto, I was running 8.04.  

What problems did you run into with the tar.gz instructions?

---

### Post by jlh on 2008-12-20
The client application did not launch.  If I tried at the command line, if recollection serves, I got a message relating to the lack fonts.

The instructions themselves were clear, and I did not detect any installation problem.

---

### Post by mgmiller on 2008-12-21
There was one other person who mentioned a fonts problem with the tar.gz install.  I suggested he try looking through the following links for possible help.  He did not write back afterward to say if he was successful.

 			
 			 			 		   		 		 		You may find some useful tips here:
[http://forums.citrix.com/thread.jspa?threadID=86630](http://forums.citrix.com/thread.jspa?threadID=86630)

There may also be some help here:
[http://sudan.ubuntuforums.com/showth...=376735&page=4]("http://sudan.ubuntuforums.com/showthread.php?t=376735&page=4")

---

### Post by dspisak on 2008-12-24
Hello.  I was able to install ICA Client and use it with Firefox 3.0.4, x86_64.  Since then there has been an automatic update to 3.0.5 x86_64, but ICA Client no longer works.  From the Citrix website I downloaded Linux ICA Client Version 10.6, the file named en.linuxx86.tar.gz (which is the version I used previously).  I extracted the file to my desktop. When I try to run setupwfc in a terminal either as root or as a user, the following is returned:
/home/spisaks/Desktop/linuxx86/hinst: 236: /home/spisaks/Desktop/linuxx86/echo_cmd: not found
/home/spisaks/Desktop/linuxx86/hinst: 237: /home/spisaks/Desktop/linuxx86/echo_cmd: not found
/home/spisaks/Desktop/linuxx86/hinst: 238: /home/spisaks/Desktop/linuxx86/echo_cmd: not found
/home/spisaks/Desktop/linuxx86/hinst: 239: /home/spisaks/Desktop/linuxx86/echo_cmd: not found
/home/spisaks/Desktop/linuxx86/hinst: 4011: /home/spisaks/Desktop/linuxx86/echo_cmd: not found
/home/spisaks/Desktop/linuxx86/hinst: 4027: /home/spisaks/Desktop/linuxx86/echo_cmd: not found
/home/spisaks/Desktop/linuxx86/hinst: 4043: /home/spisaks/Desktop/linuxx86/echo_cmd: not found
/home/spisaks/Desktop/linuxx86/hinst: 4043: /home/spisaks/Desktop/linuxx86/echo_cmd: not found
/home/spisaks/Desktop/linuxx86/hinst: 4043: /home/spisaks/Desktop/linuxx86/echo_cmd: not found
/home/spisaks/Desktop/linuxx86/hinst: 4043: /home/spisaks/Desktop/linuxx86/echo_cmd: not found.

hinst and echo_cmd are in the linuxx86 folder.  I do not know what the numbers 236, 237, etc. mean.  This problem did not happen with the first installation. In the first installation setupwfc ran and installed ICA Client with out a problem.

What have I done wrong, or what should i do?  Thank you for your help.

My system:
CPU - AMD Athlon 64
OS - ubuntu 8.10 amd64
Browser - Firefox 3.0.5 x86_64.

Dan

---

### Post by mgmiller on 2008-12-24
Did you make sure the extracted files are executable?

---

### Post by dspisak on 2008-12-25
I checked the Properties/Permissions for setupwfc, echo_cmd, hinst, npica.so, wfcmgr, and wfica.  They are all marked "Allow executing file as program".  Is this correct?  Thanks.

---

### Post by mgmiller on 2008-12-26
You said you tried to "run setupfwc".  Did you precede  the command with "./" as in:
```
./setupfwc
```Also, when you run it from terminal, make sure your terminal is in the directory where the executable fies are.  In this case, make sure you have cd'd to your linuxx86 folder on the desktop in terminal before executing:
```
cd ~/Desktop/linuxx86/
```Then execute:
```
./setupwfc
```Since the permissions are correct and the file is there, it should run.

---

### Post by dspisak on 2008-12-28
Citrix Client is back up and running.  I re-installed ia32-libs and Citrix installed successfully.

Thank you for your help.

---

### Post by omnialive on 2009-01-14
I have been successful in installing the citrix ica client on ubuntu 8.04. the only twinge of a problem is that for some reason when I access our nfuse server via FireFox, it doesn't "detect" that I have a Citrix client installed. This only means I have to click an extra link to by-pass some custom detection that my company has in place.

The reason I'm posting this is that I had citrix ica installed before I had to reinstall ubuntu (i fouled up the graphical desktop tweaking my video card drivers) and at that time, it detected my ica client fine. Now, after the reinstall, I have to keep clicking that annoying extra link to bypass detection.

Any thoughts? At least it is working fine other than that minor thorn!

---

### Post by dspisak on 2009-01-14
Hi.  This worked for me.
Install Citrix Client 32-bit on ubuntu 8.10 amd64 for Firefox 3.0.5.
(ia32-libs must be installed.  The nspluginwrapper package must be installed AFTER Flash Player is installed, see above.)
1.	Download en.linuxx86.tar.gz from [http://www.citrix.com/English/ss/downloads/index.asp?ntref=hp_util_US](http://www.citrix.com/English/ss/downloads/index.asp?ntref=hp_util_US).
2.	Save the .tar.gz file to your Desktop and wait for the file to download completely.
3.	Unpack/Extract the file.  The extracted files will appear on your Desktop.
4.	Open a terminal and cd to the Desktop directory: cd /Desktop/.
5.	Type the following command: sudo ./setupwfc.  Give your regular password when requested.
6.	Select a setup option, then follow the prompts

---

### Post by Cheddardip on 2009-01-17
I installed citrix fine.  How do I give the site Trusted Secure Certificate Authority?

---

### Post by dspisak on 2009-01-17
Sorry Cheddardip, but I can't help you with this.  I have no idea what Trusted Secure Certificate Authority is.  Apparently it is not required or it is granted automatically when I log on to my company's network from home.

---

### Post by Cheddardip on 2009-01-17
Thanks for the reply. It seems to be some kind of permission.

---

### Post by Cheddardip on 2009-01-17
The Message I get is "**you have not chosen to trust "Trusted Secure Certificate Authority", the issuer of the server's security Certificate (ssl error 61)**"

In windows a screen pops up That lets you give permission. I did not get that pop up. What do I need to do in Ubuntu Firefox?

---

### Post by dspisak on 2009-01-17
When I was using xpPro I seem to recall that a screen appeared at the first attempt to log on.  It did not appear since then.

Have you contacted your IT folks to open a subscription?  Your company might require one.

FWIW, I log on using SecurID not SmartBadge.

Check your Certificate Validation in Preferences, I'm using OSCP.

---

### Post by stefangr1 on 2009-01-17
> **Cheddardip said:**
> The Message I get is "**you have not chosen to trust "Trusted Secure Certificate Authority", the issuer of the server's security Certificate (ssl error 61)**"

In windows a screen pops up That lets you give permission. I did not get that pop up. What do I need to do in Ubuntu Firefox?


You go to:
Edit -> preferences -> advanced -> encryption
and then add the certificate.

---

### Post by stefangr1 on 2009-01-17
By the way: does anybody know how to renew the 100-day license after it has stopped working? I'm actually using a windows computer just for some teleworking applications from work that needs the Citrix client.

---

### Post by cbahimsa on 2009-04-11
> **Cheddardip said:**
> The Message I get is "**you have not chosen to trust "Trusted Secure Certificate Authority", the issuer of the server's security Certificate (ssl error 61)**"

In windows a screen pops up That lets you give permission. I did not get that pop up. What do I need to do in Ubuntu Firefox?

Go to: [http://www.emielmolenaar.com/2008/12/installing-the-citrix-presentation-server-client-under-ubuntu-810/#comment-304](http://www.emielmolenaar.com/2008/12/installing-the-citrix-presentation-server-client-under-ubuntu-810/#comment-304). It solved that problem for me.

---

### Post by christopherbalz on 2009-04-30
Aside from the usual instructions, I needed to fix the X11 fontset path, per [a key comment on an Ubuntu forums page]("http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=4306794&postcount=82").

---

### Post by KaiO on 2009-05-05
If you get an error message like:
"You have chosen not to trust "BLA BLA BLA", the issuer of the server's security certificate."
the solution is simple enough:
Copy the requested cerificate (like "ThawteRoot.crt") and put this (as root) into:
/usr/lib/ICAClient/keystore/cacerts.

---

### Post by Julian David Pitt on 2009-06-18
I have just installed as per mrmiller's instructions and all I now seem to have installed is Citrix Receiver, whatever that is and does. I downloaded the correct client from [http://www.citrix.com/English/ss/downloads/details.asp?downloadId=3323&productId=186#top]("http://www.citrix.com/English/ss/downloads/details.asp?downloadId=3323&productId=186#top") and also installed libmotif3. When I try to start Citrix receiver I get absolutely nothing happening? Any ideas please?

---

### Post by robert shearer on 2009-06-21
> When I try to start Citrix receiver I get absolutely nothing happening?

Correct so far. The Citrix Receiver will launch once a connection is established.

Open Firefox and enter into the address bar the address given to you by your IT dept for access.

If this connection is made and the certificates are correct(should happen automatically) then the Citrix receiver will launch and you should be presented with a logon screen.

---

### Post by slinkeey on 2009-09-08
I was able to install the client on my AMD64 System running Ubuntu 9.04

I can open the ICA files by doing an open with and using the fat client. (/usr/lib/ICAClient/wfica) 

It works pretty good... A little slow.

My problem is that the Firefox Plugin appears to not like the 32 / 64 bit mixed environment...

LoadPlugin: failed to initialize shared library /usr/lib/ICAClient/npica.so [/usr/lib/ICAClient/npica.so: wrong ELF class: ELFCLASS32]

Thanks,
Jeff

---

### Post by baconn on 2009-10-04
MGMiller --- thank you very much.  I thought I had a prime-working machine until my wife borrowed this to do some online nursing training and it would not allow access to her Citrix server for the coursework.  I did all you had instructed except, when extracting the Linuxxx86.tar.gz file, it extraced the contents of the folder to all separate files on the desktop.  I dragged them back into the icainstall folder and it worked perfectly!   
Thanks again!

---

### Post by Trubbel on 2009-10-16
The instructions worked for me on 9.04 64-bit after I applied a security certificate.

Here's how to get the security certificate for Equifax (among others):
[URL="http://www.madox.net/blog/2009/05/04/citrix-linux-client-64bit-amd64-for-ubuntu-jaunty-904/comment-page-1/"]
http://www.madox.net/blog/2009/05/04/citrix-linux-client-64bit-amd64-for-ubuntu-jaunty-904/comment-page-1/[/URL]


Also afterwards I got an error message that said:

> The socks 5 handshake failed (SSL error 29)

Information about this error is found at the official Citrix site:
[http://support.citrix.com/article/CTX122965]("http://support.citrix.com/article/CTX122965")

That is most likely a server side error that can occur with newer version of the server gateway. I tested this with an older server and it works perfectly.

---

### Post by thomi_ch on 2012-10-22
Heyy all

Yeah, an old thread but still needed and i think we need to update it..

Installing Citrix icaclient on ubuntu, specially 64bit, isn't easy...

Upgraded yesterday from 12.04 to 12.10 and icaclient (12.0) won't work :(

/opt/Citrix/ICAClient/wfica -desc "TEST"
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.

(wfica:19103): Gdk-CRITICAL **: IA__gdk_error_trap_pop: assertion `gdk_error_traps != NULL' failed
Segmentation fault (core dumped)

I tried then to install latest icaclient v12.1 amd64 and needed to get a patched version, check this:
[http://askubuntu.com/questions/147156/dpkg-reports-error-on-package-icaclient](http://askubuntu.com/questions/147156/dpkg-reports-error-on-package-icaclient)

Installation of icaclient was success, but still same arrer (see above).

Here some information:

apt-cache policy icaclient 
icaclient:
  Installed: 12.1.0
  Candidate: 12.1.0
  Version table:
 *** 12.1.0 0
        100 /var/lib/dpkg/status


apt-cache policy libmotif4
libmotif4:
  Installed: 2.3.3-5ubuntu2
  Candidate: 2.3.3-5ubuntu2
  Version table:
 *** 2.3.3-5ubuntu2 0
        500 [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) quantal/multiverse amd64 Packages
        100 /var/lib/dpkg/status


I tried some stuff from [https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo) but without success.

Maybe some of you can help, give a hint.

Thanks a lot

Cheers
thomi

---

### Post by wildmanne39 on 2012-10-22
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

