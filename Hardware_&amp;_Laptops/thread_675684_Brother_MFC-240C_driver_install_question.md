---
title: "Brother MFC-240C driver install question"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by AgentZ86 on 2008-01-22
Hi all

I'm trying not to break my system.

According to the Brother site for my 32bit installation I should do as follows to install my Printing capabilities for my Brother MFC-240C ? Please confirm ?


[LIST]
So I should [[COLOR="Blue"]download[/COLOR] [COLOR="Blue"],save to disk and install[/COLOR]]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc240clpr-1.0.0-9.i386.deb&lang=English_lpr") the LPR printer driver, installing with this command:
dpkg -i --force-all --force-architecture xxxx.deb*  (my note: do I need the * or is that just something on the brother site indicating important ??)
[/LIST]
[LIST]
Ignorable error message:
If you see error message "/var/spool/lpd/ the folder or file doesn't exist". Please ignore it. [/LIST]
[LIST]
This will install the Brother printer driver onto your computer and configure it to use the USB interface. [/LIST]
[LIST]
Note to users of product with "*" mark: (my note: the MFC-240C has a * mark fyi)
In some distributions, LPD needs to be installed before installing the CUPS wrapper driver. If you have a problem installing the driver, create a temporary symbolic link to link the file "/etc/init.d/cups" or "/etc/init.d/cupsys" to "/etc/init.d/lpd".

ln -s /etc/init.d/cups /etc/init.d/lpd
ln -s /etc/init.d/cupsys /etc/init.d/lpd  (my notes: I believe this is the one I want ?)

After the installation, remove the symbolic link.[/LIST]
[LIST]
[[COLOR="Blue"]Download and install the CUPS wrapper driver[/COLOR]]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/mfc240ccupswrapper-1.0.0-10.i386.deb&lang=English_gpl")[/LIST]
[LIST]
Remove symbolic link as indicated above = means to simply delete it, I think ?[/LIST]

Please advise on this subject, I hope this is correct. Unless there is something else I should know about my installation of 7.10 Gutsy.
:popcorn:

---

### Post by AgentZ86 on 2008-01-22
So far with step one I'm getting this message

I login with su user
pass ???
then this command below

-desktop:~$ dpkg -i --force-all --force-architecture mfc240clpr-1.0.0-9.i386.deb
dpkg: operation requires read/write access to dpkg status area

Please define this subject for me and why this might happen ? 

I've also tried sudo dpkg -i --force-all --force-architecture mfc240clpr-1.0.0-9.i386.deb and get other error, but not exactly the same, but still no access types of errors or file not found etc. 

Anyhow I basically clicked on the .deb file and a program popped up and ask me to install with gecko or something I clicked yes and something installed, with the error mentioned below: /var/spool/lpd/ the folder or file doesn't exist
my synaptic still works nothing seems to be broken at this point.

So now I have create a sym link to the LPR, but I can't find the LPR so how can I make a link to it ?? so that I can installed the cups wrapper. ??

I searched the etc/init.d folder and there is not lpd folder/file and so I'm afraid to do a symbolic link to that location to install the cups wrapper driver. 

I need some advise on how to proceed or should I go back to the begining and try to get the first command to run properly as instructed ?

Please advise

Thanks

---

### Post by AgentZ86 on 2008-01-24
Ok, I would like to summerize my status

I am looking at the instructions and the brother site to try and figure this all out.

It appears there is mention of  LPR and LPD and I don't understand LPD

Brother indicates to install LPR before cups, but in some printers with the (*) mark that LPD would have to be installed first before the cups wrapper also ??? so I'm confused about this.

Please advise on this topic please

---

### Post by AgentZ86 on 2008-01-24
Update status:

I've read and read some more, here is the status.

[LIST]
I've installed the LPR simply by clicking on .dep archive which was downloaded and the installation appears to have went as expected and  with the errors as indicated by brother, and directed to ignore[/LIST]
[LIST]
After reading and searching about LPD and LPR I could determine that the installation of the LPR has created a folder for user/local/Brother/Printer/mfc240c[/LIST]
[LIST]
further file searches found the lpd file listed twice, once in the user/lib/cups/backend, and in the user/lib/cups/backend-available[/LIST]
[LIST]
I was very tempted to create symbolic link to one of those location instead of this location as suggested in the brother instructions (ln -s /etc/init.d/cupsys /etc/init.d/lpd)[/LIST]
[LIST]
So I leaned in the direction of the brother directions and did this(sudo ln -s /etc/init.d/cupsys /etc/init.d/lpd) instead not sure if this really effected anything but at least my synaptic and add/remove package manager still works etc. no problems there[/LIST]
[LIST]
I can now go to the printers section and add new printer and my printer now appears in the brother list, however no test page has printed as of yet.[/LIST]

So I'll keep working on this but I think I'm making a little progress.

I just hope that my symbolic link was proper and also hoping that it was necessary to do the symbolic link as I really don't know for sure.

Anyhow any help would be great, thanks.

---

### Post by AgentZ86 on 2008-01-24
Cups is saying printer is busy will try in 5 sec. it may only be because the printer needs a yellow ink cartridge I may have to post back on this once I replace the cartridge just to be sure that the only reason it won't print a test page.

---

### Post by AgentZ86 on 2008-01-25
Windows printing doesn't work currently either and indicates that when ink is low it will not print, so I'm guessing that it the problem, now.

Once I test again with new ink I'll post back the conclusion and the actual install instruction for Gutsy

---

### Post by weeorphan on 2008-01-25
Agent: I'm faced with a similar horrendous problem of trying to install Brother MFC 7420 model. For the life of me, I can't understand why they (whoever 'they' is) make this so damn complex. One  failure after another for hours, enough to drive me crazy. I finally have the cups driver installed in a Synaptic Program called Brother, but can't get the LPR or LPD installed though it sits on my desktop. My Printer test fails without it. So how to get that LPR into play.:lolflag:

Part of the problem here is the utter lack of consideration on the part of  the Brother tech writers who assume people are fluent in coding lingo. Any painless and understandable instructions would be appreciated.

---

### Post by AgentZ86 on 2008-01-26
> **weeorphan said:**
> Agent: I'm faced with a similar horrendous problem of trying to install Brother MFC 7420 model. For the life of me, I can't understand why they (whoever 'they' is) make this so damn complex. One  failure after another for hours, enough to drive me crazy. I finally have the cups driver installed in a Synaptic Program called Brother, but can't get the LPR or LPD installed though it sits on my desktop. My Printer test fails without it. So how to get that LPR into play.:lolflag:

Part of the problem here is the utter lack of consideration on the part of  the Brother tech writers who assume people are fluent in coding lingo. Any painless and understandable instructions would be appreciated.

I'll research this now and post back but I'm not sure you have to install the LPD, that only on some distros, and I don't belive Ubuntu is one, and also for some models, I'll read up on this model and post back.

And I do agree it's a real pain to understand, I had trouble also but just kept reading and reading. But most people don't have the time to read this much stuff to install a simple printer.
I use to think I was pretty smart LOL but not anymore :)

---

### Post by AgentZ86 on 2008-01-26
Here is the LPR you need

Just download to desktop then click on it and a open with dialogue thing should open, asking you to install with gdebi-  or something just install it.

ignore var/spool error messages etc.

Then from here create a symbolic link:
Open the terminal and past this into your terminal:
sudo ln -s /etc/init.d/cupsys /etc/init.d/lpd

Then download cups wrapper to desktop
click on it and open with gdebi select ok to install

Then remove the symbolic link.
I forgot where it puts the symbolic link but anyhow you have to delete after you install the cups wrapper

Then you should be able to select your printer from in the system/administration/printing menu section at the top of your ubuntu

I hope this helps


Then click on it and open

---

### Post by weeorphan on 2008-01-26
Agent:Thanks to you, I got the MFC7420 Brother printer to work. Not sure about email, fax etc, yet, but at least it prints the test page. Where did you get the line command: sudo ln -s /etc/init.d/cupsys /etc/init.d/lpd. Also, I have NO idea how to remove the temporary splice or whatever it's called. The fact is the printer is working without removing it.:popcorn::guitar:

---

### Post by weeorphan on 2008-01-26
AGENT: I can FAX and Copy but can't scan to the PC. It just reads connecting to PC and does nothing more after I push the Start button. The MFL Pro Suite on Windows was available for managing such but doesn't seem available on Ubuntu.7.10.IF you can get your scan to work to file or image or email, let me know. Thanks:confused:

---

### Post by AgentZ86 on 2008-01-26
> **weeorphan said:**
> Agent:Thanks to you, I got the MFC7420 Brother printer to work. Not sure about email, fax etc, yet, but at least it prints the test page. Where did you get the line command: sudo ln -s /etc/init.d/cupsys /etc/init.d/lpd. Also, I have NO idea how to remove the temporary splice or whatever it's called. The fact is the printer is working without removing it.:popcorn::guitar:

Thats great.

As far as the fax goes I'll research that a bit more too, it's going to be a similar procedure, but  probably a fax lpr or fax cups driver of some type.

And regarding the command  (sudo ln -s /etc/init.d/cupsys /etc/init.d/lpd), well, that is listed on the brother site

[http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html)

Basically when you get to the brother solutions center at [http://solutions.brother.com/](http://solutions.brother.com/)

then you click the country / map location
then another screen ask for country language etc. for me it's US - english
then there is a huge list of printer types etc. 
then I click mfc at the top of the page
then there is another list of specific mfc printer, so I click on ?? whatever printer you have
then that takes you to a page with all kinds of resources for your printer like manuals drivers etc. and a link that says solutions/linux
click on linux and then that takes you to the info about how to install all the linux stuff
and specific to each printer
with a link to the info on LPR stuff
And just below a link to Cups wrapper driver stuff
If you click on the Cups wrapper stuff that takes you to a page with install notes
just a little ways down there is the notes: about some distros may need to create symbolic links

So after trial an error ubuntu never would let me install the LPR with this command as instructed on the brother site:
dpkg -i --force-all --force-architecture xxxx.deb
I was getting permission trouble and so after reading about how ubuntu works and how you don't really have root login when you login with your root pass.
They have a sort of sudu command for root and I decided to try that.
I'm not 100% sure this is the way to do it, or if there are other ways, but I've not had any dependency problems with doing the sudo method so I'll stick with the sudo method for some commands. The symbolic link commands may very well work as regular user I don't know that either.
But this is just what I continued to try and finally got something working, and I believe I understand the brother site now and how to install the brother drivers.
There is sooo much info there because there are soooo many distros with soooo many folder locations all different so they put all the info there I get it now. But also another stumbling block for me is I'm sort of a intermediate newbie with linux commands. So that don't help me much.

Sorry for the long winded thread LOL I'll see what I can dig up on the fax. 

And as far as removing the symbolic link I'm quite sure it's in the /etc/init.d folder you will see it with a sort of arrow next to it, that means symbolic link or link to someplace else. There should not be any other symbolic links in there unless you put them there or some other program you installed has done this. So basically there may only be one symbolic link in the /etc/inti.d folder so it should be easy to find


Hope this helps

---

### Post by AgentZ86 on 2008-01-26
Ok, here is the link about the fax stuff so you fax/scan to image etc.

[http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html)

According to this first you have to install the scanner driver before installing the scan key tool or whatever they call it.

Your model MFC-7420 is the bscan2 driver 2.4 is what you want For Deb. installation.

There is a long list so I'll read some more tomorrow, but it looks like it's all there just may have to modify the commands a little so I can make em run on my Ubuntu Gusty 7.10 install,

Also not there is 64bit and 32 bit drivers for Deb just fyi there lots to read on that darn sight thats for sure.

Anyhow I'll post back tomorrow sometime
Happy hacking.

---

### Post by AgentZ86 on 2008-01-27
OK , weeorphan

My scanner is working, and here is what I did for the MFC-240C
These downloads are for the MFC-240C you can use similar instructions for your MFC type scanner but will need to download the proper bscan2 and scan key for your model from the Brother site.

I'll post instruction or confirm installation instruction for the MFC-7420 scanner today sometime once I get this send fax worked out also and I'll post send fax instruction on that also.

Scanner instructions for the MFC-240C Scanner Driver here: For Gutsy and 2.6 kernel
For 2.4 kernel the command is a little different just FYI

[LIST]
First Download and install bscan2 version 2.4
[Download bscan2 click here]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/sane_debian/brscan2-0.2.4-0.i386.deb&lang=English_sane")
Just download to desktop or if asked to install with gdebi- Select OK[/LIST]
[LIST]
Then regarding fstab:
If the line which starts with "none /proc/bus/usb" or "usbfs /proc/bus/usb" does not exist in the /etc/fstab file, run the following command:
echo 'none /proc/bus/usb usbfs auto,devmode=0666 0 0' >> /etc/fstab
With my Ubuntu 7.10 this line does not exist so I have run that command[/LIST]
[LIST]
NOTE: here is what I get
I get permission denied when trying this command:
echo 'none /proc/bus/usb usbfs auto,devmode=0666 0 0' >> /etc/fstab 
so in this case you have to sudo su first, then run the command:
echo 'none /proc/bus/usb usbfs auto,devmode=0666 0 0' >> /etc/fstab
So open the terminal and type sudo su, then when asked type password, then run the command. 
This will solve the permission denied problem
for kernel 2.6 users.[/LIST]
[LIST]
Then modify usb  access control: (i believe sudo su on this too, I've forgotten)
[LIST]
$ umount /proc/bus/usb    
( I get something saying it's not mounted (just ignore it)[/LIST]
[LIST]
$ mount /proc/bus/usb[/LIST]
[LIST]
$ mknod -m 666 /dev/usbscanner c 180 48[/LIST]

[LIST]
OK, Now that the driver is installed you can install the Scan Key Tool

[Download the scan key tool click here]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/s-keytool/brscan-skey-0.2.1-1.i386.deb&lang=English_lpr") and click on install with gdebi- or download to destkop then click and install with gdebi either way.[/LIST]

How to run the tool:
You can run the tool both manually and automatically.
Running the tool manually.
NOTE: I have not figured out how to run as a user yet I'll post that back once I do, so just run as root to test for now.[/LIST]
[LIST]
Open a TERMINAL, type sudo su, then type "brscan-skey", and press Enter.
This program will return to the command prompt immediately but will stay working in the background. Your PC is now registered to the Brother machine as the Scan-key target PC.
" Scan to Image", "Scan to File" and "Scan to E-mail" functions will be activated.
[/LIST]
[LIST]
If you don't have xsane installed I would install it for testing,I just used the applications/add/remove feature in ubuntu, and since your scanner is working now as root, then you will have to run your scanning programs as root also or at least I'm pretty sure about that.Otherwise I think you will get some errors like I did. I'll post back about getting it working as a regular user once I get that figured out[/LIST]
[LIST]
Anyhow install xsane or some scanning program for testing out your scanner
Then you can type sudo su, then password, then type xsane now you can test out your scanner at least to see if it's scanning etc.[/LIST]
[LIST]
Then I'll have to work on how to scan to pdf and scan to image and things, not sure if the button on the scanner will work until I get it working as regular user, but the scan key tool is installed and working at this point, but just not as regular user. Anyhow I'll post back some more info as I get it.[/LIST]

Here is something about running the tool automatically etc. I've not gotten that far yet, but someone might have fun with it.
Once I get all the info in one place I'll post full instructions from the begining to end for all the feature printer/scanner/fax etc. Anyhow here is some more instructions below about automatically running the tool.

For GNOME Users (Below is an example of Ubuntu 6.10):

(1) Open the "System" menu and select "Preference".
(2) Select the "Sessions" item in the "Preference" sub menu.
(3) Select the the "Startup" tab.
(4) Click the the "Add" button.
(5) type "brscan-skey" in the "Startup command" window.
(6) Click the "OK" button.

Now I can work on getting the fax part working


[/LIST]

---

### Post by weeorphan on 2008-01-27
They say growing old is not for sissies. I just turned 66 today, and all this wretched coding stuff is not for the senile of mind or faint of heart. I shall bravely trek with Agent Z86 where no man has gone before into Ubuntu7.10 cyberspace

---

### Post by AgentZ86 on 2008-01-27
> **weeorphan said:**
> They say growing old is not for sissies. I just turned 66 today, and all this wretched coding stuff is not for the senile of mind or faint of heart. I shall bravely trek with Agent Z86 where no man has gone before into Ubuntu7.10 cyberspace

LOL, you can say that again :lolflag:

I'll work on this some more tonight and maybe I'll learn a little about making a script that will do all this in one step to make things easier for myself and others.

Well, Keep on Trekin

---

### Post by AgentZ86 on 2008-01-28
To make it all work as normal user
[LIST]
Open the file "/etc/udev/rules.d/45-libsane.rules" with an editor.
I used gedit and you need to be root, so I did sudo gedit, then password
While in gedit select open and browse to your /etc/udev/rules.d/45-libsane.rules and it will open in the editor so that you can add a line to the bottom of the file[/LIST]
[LIST]
#brother
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="018c", MODE="666", GROUP="scanner"
NOTE: the 04f9 and the 018c entry? this is specific for my printer/scanner so to find your vendor and product ID's open a terminal and type this command (lsusb)
This will show your printer vendor and product ID
Just replace the 04f9:018c with your vendor and product ID that you just found.[/LIST]
[LIST]
Anyhow
You will see an entry all the way at the end of the /etc/udev/rules.d/45-libsane.rules file which says:
LABEL="libsane_rules_end" (do you see it?)[/LIST]
[LIST]
Your entry will go just above that.
and will include your vendor and product ID and will looks something like this:

#Brother MFC-240C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="01ab", MODE="666", GROUP="scanner"

LABEL="libsane_rules_end"[/LIST]
[LIST]
Once you have your entry correct, then select save, then exit
exit your terminal by typing exit, theN hit enter,[/LIST]

Then restart the OS

Scanning should now work well as a regular user.
I've tested with Xsane, and scan2pdf and more as regular user

Now I can work on getting the fax part working

---

### Post by weeorphan on 2008-01-28
AgentZ86: I haven't had a chance to muddle my way through the instruction you gave. Attached, I hope, is a response from Brother Solutions in Japan. Haven't tried it either. 

By the way, I noticed I couldn't copy the email from Japan and paste to this post. I had to copy, paste and save in Windows, then access through a browse window  my Windows drive from Ubuntu. Seems to me like a flaw or omission in Ubuntu. When you get a chance check it out.

---

### Post by weeorphan on 2008-01-28
Here is the Japanese version a a scan solution. Notice the improper Japanese syntax of English writing. Strike 1.

---

### Post by weeorphan on 2008-01-28
Agentz86: I apologize for not being more versed in operating UBUNTU, I couldn't get past your first paragraph. I did manage to open the gedit page, and found myself typing /etc/ udev..... into a search bar, pressing Enter on my keyboard, and seeing absolutely nothing happen. Tried several ways but couldn't get to anything to add to. I guess I''m stuck on 'browse', but I did see a Brother file and tried (tired) opening that with no luck.

---

### Post by AgentZ86 on 2008-01-28
> **weeorphan said:**
> Here is the Japanese version a a scan solution. Notice the improper Japanese syntax of English writing. Strike 1.

That is a similar instruction that is found on the brother solutions site, however the instruction for adding as regular user is not right, and doesn't work properly: it's a bit outdated but also noted for ubuntu 6.06 or later, but here is there reference from that document you attached.

[http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html#6](http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html#6)

also reference to the sane-utilities ? I did not do that because I figured I had the latest install with ubuntu 7.10 and I'm fully updated using the ubuntu update feature so I figured I was good there also.

Also their reference to :
[http://solutions.brother.com/linux/sol/printer/linux/sane_install.html](http://solutions.brother.com/linux/sol/printer/linux/sane_install.html)
I've been all over that site and saw this too, however that command does not work without sudo so that is where I added the root instruction for us newbies etc.

But in anycase, the Brother solutions site does mostly have everything there it's just that it's not 100% clear on some topics and also the command can be slightly different or if the their script lacks certain things that are not present with ubuntu then it may get errors that is what I ran into in the begining by just following their instructions exactly. But after experimenting a bit and makeing minor changes I've sort of stuck with the more clickety methods  for some of the stuff.
Anyhow working on fax now, then I'll post the final rundown step by step.

And yes I can copy and paste from that document to the forum no problem Just FYI

The zip attachement opened automatically in open office and I could copy and paste anything

---

### Post by AgentZ86 on 2008-01-28
> **weeorphan said:**
> Agentz86: I apologize for not being more versed in operating UBUNTU, I couldn't get past your first paragraph. I did manage to open the gedit page, and found myself typing /etc/ udev..... into a search bar, pressing Enter on my keyboard, and seeing absolutely nothing happen. Tried several ways but couldn't get to anything to add to. I guess I''m stuck on 'browse', but I did see a Brother file and tried (tired) opening that with no luck.

Ok I'll revise:

It's understandable I don't have the search down either, I have to use the search from the Places/Search For Files I don't know why my other searches don't seem to work right it's probably some other setting needs to be tweeked or something. Anyhow

Basically you can browse to the folder, just go to Places then Home folder,this will open the home folder, then click the UP button twice which will take you to your main  /file folder. where you will see the etc folder, inside the etc folder you'll see the udev folder,inside the udev folder you'll see the rules.d folder, and inside the rules.d folder you will see the file 45-libsane.rules And you can just click on it and it will open in an editor.

You can also do this in the terminal, open terminal and type cd /etc/udev/rules.d
then type dir and you see all the files in that directory.
 
The problem is that you need to edit this as root,
And I like the clickety method so I do this.

Open the terminal and type sudo gedit then password when asked.
This will open an unsaved document, anyhow click the Open button, then at the upper part of the screen you will see some boxes a small mini box , home , and a box which is your user folder, click on the mini box which takes you to your /files directory
Then you can navigate from there to etc folder, then udev folder, then rules.d folder and then open the 45-libsane.rules file.

Then at this point you can edit as you like and save it. 

I'm going to revise the whole instruction and make it easier to understand. 
I hope this helps

---

### Post by weeorphan on 2008-01-29
weeorphan@weeorphan-desktop:~$ sudu gedit
bash: sudu: command not found
weeorphan@weeorphan-desktop:~$ sudu gedit
bash: sudu: command not found
weeorphan@weeorphan-desktop:~$ 

As you can see above, we're not dealing with a full deck in this Unbuntu7.10.Often it fails my password authentication also. It's bad enough to climb a steep learning curve, but to have these multiple operation problems is unbearable. I will try editing per Home pathway:

---

### Post by weeorphan on 2008-01-29
weeorphan@weeorphan-desktop:~$ susb
bash: susb: command not found
weeorphan@weeorphan-desktop:~$ 1susb
bash: 1susb: command not found
weeorphan@weeorphan-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0d3d:0001 Tangtop Technology Co., Ltd 
Bus 001 Device 001: ID 0000:0000  
weeorphan@weeorphan-desktop:~$ 


I tried to find the scanner code for my mfc7420. Best I could do. Obviously, not waht we want here. Maybe i have the wrong command.

---

### Post by weeorphan on 2008-01-29
weeorphan@weeorphan-desktop:~$ su
Password: 

su: Authentication failure
Sorry.
weeorphan@weeorphan-desktop:~$ 
weeorphan@weeorphan-desktop:~$ su 
Password: 
su: Authentication failure
Sorry.
weeorphan@weeorphan-desktop:~$ 

Can't even get into terminal. My password is simple and unmistakable. Ubuntu 7.10 has some bugs and flaws that are impeding my progress.

---

### Post by AgentZ86 on 2008-01-29
> **weeorphan said:**
> weeorphan@weeorphan-desktop:~$ su
Password: 

su: Authentication failure
Sorry.
weeorphan@weeorphan-desktop:~$ 
weeorphan@weeorphan-desktop:~$ su 
Password: 
su: Authentication failure
Sorry.
weeorphan@weeorphan-desktop:~$ 

Can't even get into terminal. My password is simple and unmistakable. Ubuntu 7.10 has some bugs and flaws that are impeding my progress.

su won't work cause there is no root password/access with Ubuntu so you need either sudo or sudo su, and then your pass will be your user password

usually if you just type su, you have to put the user name after so like so: su username  and hit enter, and it will ask for pass, but that is the user login so sudo su should work with everything



Try sudo su, then hit enter, and then type password and see what happens

Ubuntu 7.10 I don't think is the problem this is very strange and not typical of Ubuntu 7.10

---

### Post by AgentZ86 on 2008-01-29
> **weeorphan said:**
> weeorphan@weeorphan-desktop:~$ susb
bash: susb: command not found
weeorphan@weeorphan-desktop:~$ 1susb
bash: 1susb: command not found
weeorphan@weeorphan-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0d3d:0001 Tangtop Technology Co., Ltd 
Bus 001 Device 001: ID 0000:0000  
weeorphan@weeorphan-desktop:~$ 


I tried to find the scanner code for my mfc7420. Best I could do. Obviously, not waht we want here. Maybe i have the wrong command.

No thats the correct command lsusb, however I don't see your printer scanner or anything

Tangtop Technology Co, is that a USB paperport scanner ?? or something

And I"m assuming your plugged into a USB port and not the parallel port ? right ?

---

### Post by AgentZ86 on 2008-01-29
> **weeorphan said:**
> weeorphan@weeorphan-desktop:~$ sudu gedit
bash: sudu: command not found
weeorphan@weeorphan-desktop:~$ sudu gedit
bash: sudu: command not found
weeorphan@weeorphan-desktop:~$ 

As you can see above, we're not dealing with a full deck in this Unbuntu7.10.Often it fails my password authentication also. It's bad enough to climb a steep learning curve, but to have these multiple operation problems is unbearable. I will try editing per Home pathway:

Ok sudo, not sudu  see your commands from above FYI

so like this ( sudo gedit )

---

### Post by Shazaam on 2008-01-29
The problem with Brother is they mainly use rpm's for files and document accordingly and basically add .deb stuff as an afterthought. Unfortunately this can be confusing to new Ubuntu users. What you can do is go to Synaptic and find/install alien which will handle rpm's. But, you MAY run into dependency problems so use it as a last resort.
I run an MFC420CN on 6.06 (Dapper) and I can remember the mess I had trying to get the drivers installed. It looks like I will run into the same problems with Gutsy.

---

### Post by AgentZ86 on 2008-01-29
> **Shazaam said:**
> The problem with Brother is they mainly use rpm's for files and document accordingly and basically add .deb stuff as an afterthought. Unfortunately this can be confusing to new Ubuntu users. What you can do is go to Synaptic and find/install alien which will handle rpm's. But, you MAY run into dependency problems so use it as a last resort.
I run an MFC420CN on 6.06 (Dapper) and I can remember the mess I had trying to get the drivers installed. It looks like I will run into the same problems with Gutsy.

The drivers for brother stuff and .deb packages are all on the brother site, same as the rpm's , but rpm's overwrite things that might easily break other stuff, not to knock rpm's they are easy enough and I like the concept better, but the've always broken my stuff and dependencies weren't always met, but it intalled anyhow,

Thanks for the info, and I think Ubuntu has alien by default or at least I thought it did.

Anyhow the brother drivers are simple enough, basic concept is to install the LPR driver, then make symbolic link for Gutsy, then install the Cupswrapper driver, then remove the symbolic link

If you have a MFC or such type printer, then it's time to get the scanner working
Install the sane, / scanner driver which will either be the bscan2 or bscan, no need to update sane, but you can if you like, then edit the fstab file with the proper line item. 

Then modify usb  access control:
$ umount /proc/bus/usb    
( I get something saying it's not mounted)
$ mount /proc/bus/usb
$ mknod -m 666 /dev/usbscanner c 180 48

And thats it, really, but if you want the scanning buttons on the device to work then you have to install the scan key tool, then make it work as root, but modifying the 45-libsane.rules file, 

So yes it's a bunch of reading on the brother site, but I don't see how the rpm's take away any of those steps, you still have to make the proper entries. and if your distro uses rpm's but renames file or moved things around, then those components might not be there and the rpm won't tell you anything about that.

It's always been a tough call on .deb vs rpms or other package management. pros and cons.
Anyhow, I'll post the complete simple install instructions on this soon.

Once I get the faxing thing worked out, with xsane etc.

---

### Post by AgentZ86 on 2008-02-08
I'm going to post my Brother install instructions so just search the forums for brother mfc

---

### Post by weeorphan on 2008-02-12
Agent z86: This may have nothing to do with your excellent post, but when I try to enter Terminal, I can't print out my Password. The keys print blanks as 
below, when I try to remove the temp command.
.
weeorphan@weeorphan-desktop:~$ sudo rm/etc.init.d/lpd
[sudo] password for weeorphan:
Sorry, try again.
[sudo] password for weeorphan:
sudo: rm/etc.init.d/lpd: command not found
weeorphan@weeorphan-desktop:~$ 

I'm sure of the password, so something else is going on here..

---

### Post by AgentZ86 on 2008-02-13
> **weeorphan said:**
> Agent z86: This may have nothing to do with your excellent post, but when I try to enter Terminal, I can't print out my Password. The keys print blanks as 
below, when I try to remove the temp command.
.
weeorphan@weeorphan-desktop:~$ sudo rm/etc.init.d/lpd
[sudo] password for weeorphan:
Sorry, try again.
[sudo] password for weeorphan:
sudo: rm/etc.init.d/lpd: command not found
weeorphan@weeorphan-desktop:~$ 

I'm sure of the password, so something else is going on here..

password might be correct, but your getting command not found, so you have to type exactly or past exactly as my instructions says, rm(space)/etc.init.d/lpd like this:
sudo rm /etc/init.d/lpd

and that should remove the sybmolic link

Also when typing the password you won't see anything typing thats normal for Ubuntu

Anyhow
Not sure if I've posted this but here is my latest instructions I've also posted in the tutorial section as well.

[www.iclbiz.com/brothermfc](www.iclbiz.com/brothermfc)

I hope this helps

Let me know I'll try to help some more, but these instructions should be pretty straight.

P.S
Also I've not tested the scankey functionality yet, so I may have to regroup a bit on that, but the printer/scanner/fax section is good and should work as direct:popcorn:ed.

---

