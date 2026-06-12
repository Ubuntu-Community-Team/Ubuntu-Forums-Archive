---
title: "Canon Pixma iP1500 installer script"
date: 2005-11-21
forum: Hardware &amp; Laptops
---

### Post by mr_niceguy on 2005-11-21
**Update: New drivers released for Canon printers!**

Thanks go to Takushi Miyoshi.

Instructions here: [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon]("http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon")

When installing the printer you may get better results using the cups web interface rather than the Gnome print menu. You can open the cups web interface on your machine at [http://localhost:631](http://localhost:631)

You should be able to use your usual administrative username and password to log in.


Note: The script formerly available at this URL has been removed since it installs an inferior driver to the one available above.

---

### Post by bradroger on 2005-11-23
Awesome!  I've been using the bastardized demo version of turboprint which is flaky and only lets me print at 300dpi.  I used the install script and added the printer using the wizard but when I print to it, the job shows up in the job manager thing, then disappears a second later with nothing happening.  I've printed from different applications, I've printed test pages...all the same thing.  I think the printer blinks once but that's it...no response.
Any help would be great!

Thanks,
Brad

---

### Post by bradroger on 2005-11-23
Sorry...I just tried to reinstall again and I noticed this message:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libtsn1
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libpng
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libtiff
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libxml

It installed alien fine but the rest of these aren't there.  I've got the multiverse and universe repositories enabled...etc.  Is there another one I need?  Do you think this is the problem?

---

### Post by mr_niceguy on 2005-11-24
[QUOTE=bradroger]Do you think this is the problem?[/QUOTE]

Sorry about your woes, lets find a way to fix this. I don't think this is the issue though. 

Originally I had some symlinking in the script for Fedora Core 4 but didn't think it was necessary with Ubuntu. I'll re-insert the linking and then we'll try running apt-get to fix everything. Give me a few minutes and I'll post back...

---

### Post by mr_niceguy on 2005-11-24
I think the latest version of the script should fix it. First try removing the printer from the print dialogue:

System > Administration > Printing (right click on the printer and select "Remove")

and removing the bjfilter packages:

```
sudo apt-get remove bjfilter*
```

Then could you download the latest script and post back how it works for you?

---

### Post by bradroger on 2005-11-25
haha!  you're amazing!  it works great....

it's funny, I looked everywhere for drivers - are these new?  Good script, thanks a lot for the extra help.

If you're an ubuntu newbie like it says under your name....you're a fine addition to the ubuntu community!

Thanks a ton,
Brad

---

### Post by veelivar on 2005-12-03
@mr_niceguy
Thanks alot for posting this script.  Not being able to use my printer was one of the big issues I was having with Ubuntu(Linux in general).  I'd tried a few of the previous fix's that had been posetd but none worked.

After a alittle fiddleing* this one worked, so thank you very much.

*I had to run the script twice as there were soem dependence issues that I needed to fix (just by updating) after teh first attempt.  A quick remove and run the script again and it worked fine :)

Just another quick question, I guess I'm never satisfied :( is it possible to get a higher resolution than 600dpi?  Dosen't really matter is not but it would be nice.

Thanks again,
Dan.

---

### Post by mr_niceguy on 2005-12-03
I didn't get more than 600dpi either :???:

BTW - thanks for the feedback. Glad to know the script is helpful. If someone has improvements, post them here too.

---

### Post by newuser111 on 2005-12-04
any chance this will work for the canon MP130?

---

### Post by mr_niceguy on 2005-12-05
[QUOTE=newuser111]any chance this will work for the canon MP130?[/QUOTE]

This driver is pretty specific so unfortunately you will need to find that elsewhere. Would be nice if Canon gave a rip about Linux drivers. HP is pretty good that way and my next printer purchase will likely reward them for that.

---

### Post by newuser111 on 2005-12-06
Mr niceguy, good job! i tried the script and I can now print using my canon MP130 printer it just printed a test page in black and color, in fact the ip1500 driver installed with your script works perfectly and may work for other canon pixma printers not supported officially by canon

---

### Post by fast orange on 2005-12-06
Thanks for making this, you are great...but i'm still not getting it to work.  The installation was smooth, and the driver was added, but i'm not getting a response from the printer yet.  I'm going through the USB port, though i'll netwrk it later once i know it works.  The status goes to printing one page temporarily, and then back to ready with no error identified.  Any Ideas?

---

### Post by mr_niceguy on 2005-12-06
[QUOTE=newuser111]I can now print using my canon MP130 printer[/QUOTE]
Cool!
[QUOTE=fast orange]but i'm not getting a response from the printer yet[/QUOTE]
D'oh! I notice that GTK apps (Gnome programs) are a lot more responsive for me than other programs. I would have liked to install the driver through the browser based cups menu ([http://localhost:631](http://localhost:631)) but alas, Ubuntu is a little heavy handed in protecting us from ourselves and won't allow it.

The bad news here is that I have no expertise in this area at all; I just kludged together a script to automate some steps I gleaned from a number of other sources - sources which were, in contrast, competent in their understanding of the subject matter.

The good news is that Linux also allows printer options to be set via the command line (what can't be set via command line?) so someone with enough time, reseach and testing may well be able to figure out how to improve the printer support. Please post results here if any of you fall into that category and we'll add it to the script.

---

### Post by newuser111 on 2005-12-07
i managed to get cups working after reading this thread [http://ubuntuforums.org/showthread.php?t=48286&highlight=CUPS+login](http://ubuntuforums.org/showthread.php?t=48286&highlight=CUPS+login)

---

### Post by fast orange on 2005-12-07
i followed your link to get cups working.  and installing it over that instead of the ubuntu system worked great.  Thanks you guys, you're amazing.

---

### Post by fast orange on 2005-12-07
so i was able to use the ip1500 directly through a usb cable.  Now i'm trying to connect to one on a windows computer.  Is there any reason why this wouldn't work, or am i just not configuring things correctly.  i'm able to do things like share files over the network...

---

### Post by raid996 on 2005-12-26
[QUOTE=fast orange]i followed your link to get cups working.  and installing it over that instead of the ubuntu system worked great.  Thanks you guys, you're amazing.[/QUOTE]

How did you do that? could you please post me the steps here? i managed to get to "Add device" but i'm not on the computer plugged to the printer (it's my girlfriends comp) so i dont get anything there... could you please help me out?
I installed ubuntu to her pc cause she had virus problem with windows (classic...) but she cant use printer and cell phone so she's basically blaming me for it... PLEAAAASEEEE SAVE MEEEEEEE ... women's rage is unstoppable :rolleyes: :rolleyes: :rolleyes: :rolleyes:

---

### Post by mr_niceguy on 2005-12-26
[QUOTE=fast orange]so i was able to use the ip1500 directly through a usb cable.  Now i'm trying to connect to one on a windows computer.[/QUOTE]

Not sure if I mentioned this before but Windows can share printers with Unix systems so I think the standard practice in a mixed environment is to set up the printer on the Windows box (using the Windows driver of course :rolleyes:) and then share it with the Linux box. I saw an article on it before but don't recall where. You will find info if you Google it.

---

### Post by mr_niceguy on 2005-12-26
[QUOTE=raid996]women's rage is unstoppable[/QUOTE]

Oh dear, if it's life and death you can always resort to [Turboprint](http://www.turboprint.de/english.html) which frankly I use myself with good results, but I wanted to post the install script for those folks who wanted a free driver.

That being said I think the thread on installing the printer through cups is working for most people as long as you install the drivers first.

---

### Post by raid996 on 2005-12-29
Oh... I was just joking... anyway if i got it rght i have to:

1. install the drivers here posted
2. enter cups server with my browser and choose it in the device list

and thats it??

---

### Post by mr_niceguy on 2005-12-29
You have it right :) Just close the Gnome printer menu when it pops up and use your browser to access the cups server instead.

---

### Post by louis_nichols on 2006-01-26
Hi! Thanks for the script! Worked just fine installing the printer

The only thing is I can't print from openoffice or acroread. Firefox doesn't work wither, but at least it shows me a message that there is a problem with the printer, though I don't know what that might be. The jobs tray icon shows for a moment, then disappears. Gedit works ok. Any ideas?

---

### Post by raid996 on 2006-01-27
Ok, now it works, the only problem is that it prints only in A5 format from openoffice even if i set it up in cups server and in ooo for A4 size page, anyone knows how to solve this problem?

---

### Post by lemmy999 on 2006-01-29
Tried this with my ip1000. Got the following error message

** (gnome-cups-manager:15330): WARNING **: connect = 'usb://Canon/iP1000'

Anyone know what this means? and how i sort it out?

---

### Post by tiho on 2006-02-27
First I would like to thank you mr_niceguy for the scprit for ip1500 installation.
Second I ask you for a help: is there any chance for manual duplex printing, whith these drivers, from any application (i.e. Evince 0.4.0)? Thanks in advance.

---

### Post by mr_niceguy on 2006-02-27
I'm afraid I haven't heard of people using this driver for manual duplex printing. There is a good website for general printing issues at [http://linuxprinting.org]()

---

### Post by tiho on 2006-03-01
thank you, mr. I'll look there.

---

### Post by deepwave on 2006-03-02
OK... I recently got my printer (Canon MP130) running thanks to the script, but I can't seem to print anything with the exception of the test pages from the gnome-cups-manager or the web interface for cups.

I tried adding shadow to cupsys group, and adding myself to both the lp and lpadmin groups, to no avail.  I set up the printer using gnome-cups-manager, and I can see it in KDE's print manager.  When I try to print something, I don't get any error messages, and I can see the job being added to the queue both in gnome-cups-manager and in KPrint.  The job is never printed though, and just sits there.  And there is no response from the printer itself.

I'm running Kubuntu 5.10, which I don't know if that makes a difference.  Any help would be greatly appreciated.

---

### Post by raid996 on 2006-03-05
Still missing that problem solution, when i try to print on open office or other it prints in A5... any1 soilved this problem???

---

### Post by Manzmann on 2006-03-10
Hi there,
Was delighted when I found this script for my printer, but when I attempt to run the script in Terminal, I get the follwing.

Installing Canon PIXMA iP1500 driver

Downloading files...


--12:13:30--  [http://linux.cergynux.net/canon/bjfilter-common_2.50-3_i386.deb](http://linux.cergynux.net/canon/bjfilter-common_2.50-3_i386.deb)
           => `bjfilter-common_2.50-3_i386.deb.1'
Resolving linux.cergynux.net... 82.236.72.193
Connecting to linux.cergynux.net|82.236.72.193|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 28,870 (28K) [application/x-debian-package]

100%[====================================>] 28,870        27.64K/s

12:13:32 (27.60 KB/s) - `bjfilter-common_2.50-3_i386.deb.1' saved [28870/28870]

--12:13:32--  [http://linux.cergynux.net/canon/bjfilter-pixmaip1500_2.50-3_i386.d](http://linux.cergynux.net/canon/bjfilter-pixmaip1500_2.50-3_i386.d) eb
           => `bjfilter-pixmaip1500_2.50-3_i386.deb.1'
Resolving linux.cergynux.net... 82.236.72.193
Connecting to linux.cergynux.net|82.236.72.193|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,911,412 (1.8M) [application/x-debian-package]

100%[====================================>] 1,911,412     98.68K/s    ETA 00:00

12:14:10 (70.92 KB/s) - `bjfilter-pixmaip1500_2.50-3_i386.deb.1' saved [1911412/ 1911412]

--12:14:10--  [http://linux.cergynux.net/canon/bjfilter-pixmaip1500-lprng_2.50-3_](http://linux.cergynux.net/canon/bjfilter-pixmaip1500-lprng_2.50-3_) i386.deb
           => `bjfilter-pixmaip1500-lprng_2.50-3_i386.deb'
Resolving linux.cergynux.net... 82.236.72.193
Connecting to linux.cergynux.net|82.236.72.193|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 90,702 (89K) [application/x-debian-package]

100%[====================================>] 90,702        97.51K/s

12:14:11 (97.29 KB/s) - `bjfilter-pixmaip1500-lprng_2.50-3_i386.deb' saved [9070 2/90702]

dpkg: requested operation requires superuser privilege
resolving dependencies...
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied )
E: Unable to lock the list directory

Restarting Unix Printing Service
Please wait...
 * Restarting Common Unix Printing System: cupsd start-stop-daemon: Unable to open pidfile `/var/run/cups/cupsd.pid' for writing:  Permission denied (Permission denied)

Then, When I go through the Gnome Printer wizard the Driver is not there.
I am not sure what I'm doing wrong.
Any help would be greatly appreciated.
Thanks

---

### Post by deepwave on 2006-03-16
You need to sudo the script...

sudo ./install-iP1500

I still have not figured out how to print non-test pages, though...  Also whenever I plug the USB cable in I get a whole slew of USB kernel messages... 

sdb: Unit Not Ready, sense:
[4332063.753000] : Current: sense key: No Sense
[4332063.753000]     Additional sense: No additional sense information
[4332064.517000] sdb : READ CAPACITY failed.
[4332064.517000] sdb : status=1, message=00, host=0, driver=08
[4332064.517000] sd: Current: sense key: No Sense
[4332064.517000]     Additional sense: No additional sense information
[4332064.774000] sdb: test WP failed, assume Write Enabled
[4332064.774000] sdb: assuming drive cache: write through
[4332065.024000] ioctl_internal_command: <4 0 0 0> return code = 8000002
[4332065.024000]    : Current: sense key: No Sense
[4332065.024000]     Additional sense: No additional sense information
[4332065.758000] sdb: Unit Not Ready, sense:
[4332065.758000] : Current: sense key: No Sense
[4332065.758000]     Additional sense: No additional sense information
[4332066.546000] sdb : READ CAPACITY failed.

---

### Post by superchar42 on 2006-04-02
**This really needs to be put in the HOWTO: section, updated so it has the extra info and everything. **

Just to let everyone know, I installed it (in sudo) and the test page worked, so did printing from firefox and OO writer. Basically worked "out of the box" - I just had my printer plugged in and on. Plus, I got my first page jam with this! 

Canon Pixma MP130. 

This was seriously helpful because the only other way I found to get this printer to work was TurboPrint, and that's out of my current price range. 

I can now completely switch to Linux now that my printer has followed! This is so exciting.

---

### Post by deepwave on 2006-04-04
I completely agree with the HOWTO... I'll write one up, if I can get to coax my printer to print something more than the test pages.

---

### Post by superchar42 on 2006-04-05
Are you using the iP1500 or the MP130?

---

### Post by deepwave on 2006-04-08
I have a MP130.

I used the install-iP1500 script though.

---

### Post by wh0rd on 2006-04-09
** (gnome-cups-manager:11705): WARNING **: IPP request failed with status 1030

** (gnome-cups-manager:11705): WARNING **: IPP request failed with status 1030

** (gnome-cups-manager:11705): WARNING **: IPP request failed with status 1030

** (gnome-cups-manager:11705): WARNING **: IPP request failed with status 1030

** (gnome-cups-manager:11705): WARNING **: IPP request failed with status 1030

** (gnome-cups-manager:11705): WARNING **: IPP request failed with status 1030

** (gnome-cups-manager:11705): WARNING **: IPP request failed with status 1030

** (gnome-cups-manager:11705): WARNING **: IPP request failed with status 1030

** (gnome-cups-manager:11705): WARNING **: IPP request failed with status 1030

** (gnome-cups-manager:11705): WARNING **: IPP request failed with status 1030

I have no idea what that means, can anyone shed some light?

---

### Post by susanne on 2006-04-16
Hi!
thank you for the installation-script!!! 
I installed Kubuntu 3 weeks ago, before I used Suse 9.2 and my printer was running with the demo version of Turboprint, wich I had a lot of problems with....
Now my printer works fine with your script!
Susanne

---

### Post by macro on 2006-04-19
Anyone managed to get this working on an AMD64 setup? I've tried using the --force-architecture command within the script, but it doesnt seem to work. Anyone got it working, or know of a (free) alternative/alternative working drivers? looks like I'll have to use keep dipping in and out of windows to get it working until I can get a amd64 version working :-(

I've been trying to compile the sources from this page:
[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/canon-pixus25.html]("http://mambo.kuhp.kyoto-u.ac.jp/~takushi/canon-pixus25.html")
But theres all sorts of problems making those

Thanks guys

---

### Post by mr_niceguy on 2006-04-26
[QUOTE=deepwave]I still have not figured out how to print non-test pages, though...[/QUOTE]

Did you install through the Gnome menu or the cups menu over [http://localhost:631](http://localhost:631) ?

---

### Post by mr_niceguy on 2006-04-26
[QUOTE=raid996]...it prints only in A5 format from openoffice even if i set it up in cups server and in ooo for A4 size page...[/QUOTE]

I got exactly the same problem. I finally reverted to the free driver from Turboprint :-?

---

### Post by raid996 on 2006-04-27
[QUOTE=mr_niceguy]I got exactly the same problem. I finally reverted to the free driver from Turboprint :-?[/QUOTE]

The one that prints the logo in alla the pages you need to print.... horrific!!!!!
:???: :???: :???: :???: 
Anyway I just told my gir:???: friend to export the files as pdf and then print form that... better than having that logo all over your printed pages.

---

### Post by mr_niceguy on 2006-04-27
[QUOTE=raid996]The one that prints the logo in alla the pages you need to print.... horrific!!!!![/QUOTE]

Actually if you fire up ```
xtpconfig
``` you can select the printer and set "Quality" to "Draft" which is 300 dpi and the logo goes away. You only need to purchase a key to print at higher resolutions.

---

### Post by raid996 on 2006-05-04
Really??? thx for the tip ;)
Whenever I'll have some time to work on it on her ubuntu box I'll try it on. Thx anyway for the help ;)

---

### Post by sheepeatingtaz on 2006-05-14
Hi there,

Trying to use the script to install an ip1500 under dapper. I *believe* this will be an ongoing problem, and wondered if anyone had found a solution yet:
```

Selecting previously deselected package bjfilter-common.
(Reading database ... 169039 files and directories currently installed.)
Unpacking bjfilter-common (from bjfilter-common_2.50-3_i386.deb) ...
Selecting previously deselected package bjfilter-pixmaip1500.
Unpacking bjfilter-pixmaip1500 (from bjfilter-pixmaip1500_2.50-3_i386.deb) ...
Selecting previously deselected package bjfilter-pixmaip1500-lprng.
Unpacking bjfilter-pixmaip1500-lprng (from bjfilter-pixmaip1500-lprng_2.50-3_i38 6.deb) ...
Setting up bjfilter-common (2.50-3) ...
dpkg: dependency problems prevent configuration of bjfilter-pixmaip1500:
 bjfilter-pixmaip1500 depends on libpng10-0 (>= 1.0.18); however:
  Package libpng10-0 is not installed.
 bjfilter-pixmaip1500 depends on libxml1 (>= 1:1.8.14-3); however:
  Package libxml1 is not installed.
dpkg: error processing bjfilter-pixmaip1500 (--install):
 dependency problems - leaving unconfigured
```

As far as I can tell, dapper had libpng12-0, and the driver needs libpng10-0. Any Ideas?

---

### Post by obzone on 2006-05-15
[QUOTE=mr_niceguy]This is such a cheap and popular printer I am grateful to those who made the drivers for it. This is just a quick and dirty script I put together to install the drivers for the Canon Pixma iP1500. 

Instructions are in the enclosed README file.[/QUOTE]
I tried to run the script (using sudo) but got a couple of messages that didn't look good:

E: could not open lock file /var/lib/apt/lists/lock - open ( 13 permissions denied)
E: unable to lock the list directory

The printer setup dialog box allowed me to set up the printer (offering ip1500 as an option that wasn't there before) but when I tried to print a test page, it listed it in the job list for a few second and cleared. But nothing arrived at the printer (no led flashing or anything)

Any suggestions?

---

### Post by raid996 on 2006-05-17
[QUOTE=mr_niceguy]Actually if you fire up ```
xtpconfig
``` you can select the printer and set "Quality" to "Draft" which is 300 dpi and the logo goes away. You only need to purchase a key to print at higher resolutions.[/QUOTE]

I'm having problems with the turboprint drivers, i downloaded the tar.gz file then extracted it and installed it. The process went perfect and i found two files on my desktop one with root access only permissions.
I opened xtpconfig like you said and set the quality to draft then told him to print a test page but the printer is dead.

I opened localhost:631 with my browser and set the printer with the turbprint drivers, then asked it to print some test pages from cups server but still the printer shows no sign of life.

Everything seems ok, but the printer wont print, whenever i send the server a job it outputs in the printer status "job processing 20%" then the job disappears. Anyone could tell me how to setup/install decently the turboprint drivers so it can work??
:-k :-k

---

### Post by wh0rd on 2006-06-04
Hi I had this driver working on a Canon PIXMA MP130 in Fedora Core 5, but I'm having some issues with it on Ubuntu Dapper Drake. Everytime I run the script and add the printer, the Synaptic Update Manager kicks in and asks to do a:

 > sudo apt-get install -f

This actually removes the driver.

---

### Post by mdurham on 2006-06-04
I too had it working on a MP130 on Breezy, but it doesn't work on Dapper. The comercial TurboPrint (I think that's what it's called) doesn't work either. What have they done? Maybe that's the 'polish' with the 6 week delay!

---

### Post by HardCoder on 2006-06-13
[QUOTE=sheepeatingtaz]Hi there,

Trying to use the script to install an ip1500 under dapper. I *believe* this will be an ongoing problem, and wondered if anyone had found a solution yet:
```

Selecting previously deselected package bjfilter-common.
(Reading database ... 169039 files and directories currently installed.)
Unpacking bjfilter-common (from bjfilter-common_2.50-3_i386.deb) ...
Selecting previously deselected package bjfilter-pixmaip1500.
Unpacking bjfilter-pixmaip1500 (from bjfilter-pixmaip1500_2.50-3_i386.deb) ...
Selecting previously deselected package bjfilter-pixmaip1500-lprng.
Unpacking bjfilter-pixmaip1500-lprng (from bjfilter-pixmaip1500-lprng_2.50-3_i38 6.deb) ...
Setting up bjfilter-common (2.50-3) ...
dpkg: dependency problems prevent configuration of bjfilter-pixmaip1500:
 bjfilter-pixmaip1500 depends on libpng10-0 (>= 1.0.18); however:
  Package libpng10-0 is not installed.
 bjfilter-pixmaip1500 depends on libxml1 (>= 1:1.8.14-3); however:
  Package libxml1 is not installed.
dpkg: error processing bjfilter-pixmaip1500 (--install):
 dependency problems - leaving unconfigured
```

As far as I can tell, dapper had libpng12-0, and the driver needs libpng10-0. Any Ideas?[/QUOTE]Had the same problem as you had, solved it by getting libpng10 from here:
[http://ftp.debian.org/debian/pool/main/libp/libpng/libpng10-0_1.0.18-1_i386.deb](http://ftp.debian.org/debian/pool/main/libp/libpng/libpng10-0_1.0.18-1_i386.deb)
then from a terminal window:
sudo dpkg -i libpng10-0_1.0.18-1_i386.deb

And last but not least
sudo apt-get -f install

Cheers! :)

---

### Post by strach on 2006-07-04
Yeah, thanks (big) to **mr_niceguy** and **HardCoder** my Canon Pixma ip1500 works wery well on Kubuntu 6.06. Just download
[http://ftp.debian.org/debian/pool/main/libp/libpng/libpng10-0_1.0.18-1_i386.deb]("http://ftp.debian.org/debian/pool/main/libp/libpng/libpng10-0_1.0.18-1_i386.deb")
...and install it with sudo dpkg --install, then use **niceguy**'s Driver Kit and you're done.

Thanks, guys! Now I can finally uninstall my Windows XP to increase space for my new /home ;)

---

### Post by Ryan H on 2006-07-11
I ran the file in as Root in the terminal, but what happened?
```

Installing Canon PIXMA iP1500 driver

Downloading files...


--18:05:33--  http://linux.cergynux.net/canon/bjfilter-common_2.50-3_i386.deb
           => `bjfilter-common_2.50-3_i386.deb'
Resolving linux.cergynux.net... 82.236.72.193
Connecting to linux.cergynux.net|82.236.72.193|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 28,870 (28K) [application/x-debian-package]

100%[====================================>] 28,870        43.35K/s

18:05:35 (43.23 KB/s) - `bjfilter-common_2.50-3_i386.deb' saved [28870/28870]

--18:05:35--  http://linux.cergynux.net/canon/bjfilter-pixmaip1500_2.50-3_i386.deb
           => `bjfilter-pixmaip1500_2.50-3_i386.deb'
Resolving linux.cergynux.net... 82.236.72.193
Connecting to linux.cergynux.net|82.236.72.193|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,911,412 (1.8M) [application/x-debian-package]

100%[====================================>] 1,911,412     32.75K/s    ETA 00:00

18:06:39 (29.22 KB/s) - `bjfilter-pixmaip1500_2.50-3_i386.deb' saved [1911412/1911412]

--18:06:39--  http://linux.cergynux.net/canon/bjfilter-pixmaip1500-lprng_2.50-3_i386.deb
           => `bjfilter-pixmaip1500-lprng_2.50-3_i386.deb'
Resolving linux.cergynux.net... 82.236.72.193
Connecting to linux.cergynux.net|82.236.72.193|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 90,702 (89K) [application/x-debian-package]

100%[====================================>] 90,702        17.40K/s    ETA 00:00

18:06:45 (17.37 KB/s) - `bjfilter-pixmaip1500-lprng_2.50-3_i386.deb' saved [90702/90702]

dpkg: error processing bjfilter-common_2.50-3_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing bjfilter-pixmaip1500_2.50-3_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing bjfilter-pixmaip1500-lprng_2.50-3_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 bjfilter-common_2.50-3_i386.deb
 bjfilter-pixmaip1500_2.50-3_i386.deb
 bjfilter-pixmaip1500-lprng_2.50-3_i386.deb
resolving dependencies...
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Restarting Unix Printing Service
Please wait...
 * Restarting Common Unix Printing System: cupsd                         [ ok ]


Launching Gnome Printer Manager
Please ignore the following text...

(gnome-printer-view:5773): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(gnome-cups-add:5811): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

** (gnome-cups-add:5811): WARNING **: Two ppds have driver == 'foo2oak (recommended)'
        ->linuxprinting.org-gs-builtin/Generic/Generic-OAKT_Printer-foo2oak.ppd (Generic OAKT Printer Foomatic/foo2oak (recommended)[1]) and
        ->Generic-OAKT_Printer.ppd.gz (Generic OAKT Printer Foomatic/foo2oak (recommended))[1]

** (gnome-cups-add:5811): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
        ->linuxprinting.org-gs-builtin/Generic/Generic-ZjStream_Printer-foo2zjs.ppd (Generic ZjStream Printer Foomatic/foo2zjs (recommended)[1]) and
        ->Generic-ZjStream_Printer.ppd.gz (Generic ZjStream Printer Foomatic/foo2zjs (recommended))[1]

** (gnome-cups-add:5811): WARNING **: model named 'designjet 5500ps (recommended)' doesn't have a recognized structure

** (gnome-cups-add:5811): WARNING **: Two ppds have driver == 'foo2oak (recommended)'
        ->linuxprinting.org-gs-builtin/HP/HP-Color_LaserJet_1500-foo2oak.ppd (HP Color LaserJet 1500 Foomatic/foo2oak (recommended)[1]) and
        ->HP-Color_LaserJet_1500.ppd.gz (HP Color LaserJet 1500 Foomatic/foo2oak (recommended))[1]

** (gnome-cups-add:5811): WARNING **: Two ppds have driver == 'foo2hp (recommended)'
        ->linuxprinting.org-gs-builtin/HP/HP-Color_LaserJet_2600n-foo2hp.ppd (HP Color LaserJet 2600n Foomatic/foo2hp (recommended)[1]) and
        ->HP-Color_LaserJet_2600n.ppd.gz (HP Color LaserJet 2600n Foomatic/foo2hp (recommended))[1]

** (gnome-cups-add:5811): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
        ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_1000-foo2zjs.ppd (HP LaserJet 1000 Foomatic/foo2zjs (recommended)[1]) and
        ->HP-LaserJet_1000.ppd.gz (HP LaserJet 1000 Foomatic/foo2zjs (recommended))[1]

** (gnome-cups-add:5811): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
        ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_1005-foo2zjs.ppd (HP LaserJet 1005 Foomatic/foo2zjs (recommended)[1]) and
        ->HP-LaserJet_1005.ppd.gz (HP LaserJet 1005 Foomatic/foo2zjs (recommended))[1]

** (gnome-cups-add:5811): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
        ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_1020-foo2zjs.ppd (HP LaserJet 1020 Foomatic/foo2zjs (recommended)[1]) and
        ->HP-LaserJet_1020.ppd.gz (HP LaserJet 1020 Foomatic/foo2zjs (recommended))[1]

** (gnome-cups-add:5811): WARNING **: Two ppds have driver == 'Standard'
        ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3030-Postscript.ppd (HP LaserJet 3020 3030 Postscript (recommended)[1]) and
        ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3020-Postscript.ppd (HP LaserJet 3020 3030 Postscript (recommended))[1]

** (gnome-cups-add:5811): WARNING **: Two ppds have driver == 'Standard'
        ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3200m-Postscript.ppd (HP LaserJet 3200 Postscript (recommended)[1]) and
        ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3200-Postscript.ppd (HP LaserJet 3200 Postscript (recommended))[1]

** (gnome-cups-add:5811): WARNING **: Two ppds have driver == 'Standard'
        ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3310_MFP-Postscript.ppd (HP LaserJet 3300 Series Postscript (recommended)[1]) and
        ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3300_MFP-Postscript.ppd (HP LaserJet 3300 Series Postscript (recommended))[1]

** (gnome-cups-add:5811): WARNING **: Two ppds have driver == 'Standard'
        ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3320_MFP-Postscript.ppd (HP LaserJet 3300 Series Postscript (recommended)[1]) and
        ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3310_MFP-Postscript.ppd (HP LaserJet 3300 Series Postscript (recommended))[1]

** (gnome-cups-add:5811): WARNING **: Two ppds have driver == 'Standard'
        ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3320N_MFP-Postscript.ppd (HP LaserJet 3300 Series Postscript (recommended)[1]) and
        ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3320_MFP-Postscript.ppd (HP LaserJet 3300 Series Postscript (recommended))[1]

** (gnome-cups-add:5811): WARNING **: Two ppds have driver == 'Standard'
        ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3330_MFP-Postscript.ppd (HP LaserJet 3300 Series Postscript (recommended)[1]) and
        ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_3320N_MFP-Postscript.ppd (HP LaserJet 3300 Series Postscript (recommended))[1]

** (gnome-cups-add:5811): WARNING **: Two ppds have driver == 'Standard'
        ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_4350-Postscript.ppd (HP LaserJet 4300 Series Postscript (recommended)[1]) and
        ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_4300-Postscript.ppd (HP LaserJet 4300 Series Postscript (recommended))[1]

** (gnome-cups-add:5811): WARNING **: Two ppds have driver == 'Standard'
        ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_9050_MFP-Postscript.ppd (HP LaserJet 9040 9050 MFP Postscript (recommended)[1]) and
        ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_9040_MFP-Postscript.ppd (HP LaserJet 9040 9050 MFP Postscript (recommended))[1]

** (gnome-cups-add:5811): WARNING **: Two ppds have driver == 'Standard'
        ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_9065_MFP-Postscript.ppd (HP LaserJet 9055 9065 MFP Postscript (recommended)[1]) and
        ->linuxprinting.org-gs-builtin/HP/HP-LaserJet_9055_MFP-Postscript.ppd (HP LaserJet 9055 9065 MFP Postscript (recommended))[1]

** (gnome-cups-add:5811): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
        ->Minolta-Color_PageWorks_Pro_L.ppd.gz (Minolta Color PageWorks/Pro L Foomatic/foo2zjs (recommended)[1]) and
        ->linuxprinting.org-gs-builtin/Minolta/Minolta-Color_PageWorks_Pro_L-foo2zjs.ppd (Minolta Color PageWorks/Pro L Foomatic/foo2zjs (recommended))[1]

** (gnome-cups-add:5811): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
        ->Minolta-magicolor_2200_DL.ppd.gz (Minolta magicolor 2200 DL Foomatic/foo2zjs (recommended)[1]) and
        ->linuxprinting.org-gs-builtin/Minolta/Minolta-magicolor_2200_DL-foo2zjs.ppd (Minolta magicolor 2200 DL Foomatic/foo2zjs (recommended))[1]

** (gnome-cups-add:5811): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
        ->Minolta-magicolor_2300_DL.ppd.gz (Minolta magicolor 2300 DL Foomatic/foo2zjs (recommended)[1]) and
        ->linuxprinting.org-gs-builtin/Minolta/Minolta-magicolor_2300_DL-foo2zjs.ppd (Minolta magicolor 2300 DL Foomatic/foo2zjs (recommended))[1]

** (gnome-cups-add:5811): WARNING **: Two ppds have driver == 'foo2zjs (recommended)'
        ->Minolta-magicolor_2430_DL.ppd.gz (Minolta magicolor 2430 DL Foomatic/foo2zjs (recommended)[1]) and
        ->linuxprinting.org-gs-builtin/Minolta/Minolta-magicolor_2430_DL-foo2zjs.ppd (Minolta magicolor 2430 DL Foomatic/foo2zjs (recommended))[1]
Selected ppd file = linuxprinting.org-gs-builtin/Canon/Canon-BJ-100-bj200.ppd
Selected ppd file = linuxprinting.org-gs-builtin/Canon/Canon-imageRunner_330s-lj4dith.ppd
Selected ppd file = linuxprinting.org-gs-builtin/Canon/Canon-imageRunner_330s-ljet4.ppd
Selected ppd file = linuxprinting.org-gs-builtin/Canon/Canon-imageRunner_330s-lj4dith.ppd

```

And the Add Printer box came up, like you said. When I clicked to add a new printer my Printer was detected, but the driver wasn't there. There was only the PIXMA iP 1400, not the 1500. Any ideas?

-Ryan H

---

### Post by JoeyG on 2006-07-29
> dpkg: error processing bjfilter-common_2.50-3_i386.deb (--install):
 package architecture (i386) does not match system (amd64)

That tells you that you are running on a AMD64, and the drivers are for an i386. Unfortunately, the FTP site doesn't have AMD64 drivers.

I have this problem myself; does anyone know where I can find drivers for a Canon iP1500 on a AMD64?

---

### Post by neepster on 2006-10-17
Doing the below, plus downloading and installing with sudo -dpkg --install  

This file:
[http://ftp.debian.org/debian/pool/main/libx/libxml/libxml1_1.8.17-14_i386.deb](http://ftp.debian.org/debian/pool/main/libx/libxml/libxml1_1.8.17-14_i386.deb)

Then running the script  sudo ./install-iP1500


Fixed my problems and now my printer works... took a while to print the first time though... wasn't sure it was gonna work, but it did!  Yay!


> Yeah, thanks (big) to mr_niceguy and HardCoder my Canon Pixma ip1500 works wery well on Kubuntu 6.06. Just download
[http://ftp.debian.org/debian/pool/ma....18-1_i386.deb](http://ftp.debian.org/debian/pool/ma....18-1_i386.deb)
...and install it with sudo dpkg --install, then use niceguy's Driver Kit and you're done.

Thanks, guys! Now I can finally uninstall my Windows XP to increase space for my new /home 

---

### Post by neepster on 2006-10-19
For what it's worth, this works, but then Synaptic complains that 2 packages are broken.  It "fixes" them when you update anything else, which then breaks the printer again... argh!!!

I will have to try another way.

---

### Post by alan.brdigestone on 2006-10-28
:p This worked for me without too much pain

[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/canon-pixus25.html](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/canon-pixus25.html)

Ciao Alan

---

### Post by mr_niceguy on 2006-11-02
> **alan.brdigestone said:**
> :p This worked for me without too much pain

[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/canon-pixus25.html](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/canon-pixus25.html)

Ciao Alan

Agreed! This is worthy of its own thread if you haven't done so already. The only caution I have is permanently adding this third party repository to the apt sources list.

:)

---

### Post by chownsb on 2006-11-25
Thank you so much!  I was able to install the ip1500 driver for my MP130 printer.  I used the instructions from [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/]("http://mambo.kuhp.kyoto-u.ac.jp/~takushi/") because the installer script hasn't worked since I upgraded to Edgy.  It runs fine but the driver doesn't show up in the list.

---

### Post by mseney on 2006-12-11
Worked great for me and I am connecting to the printer via a Windows Workgroup share.

Edgy Eft 6.10

$sudo vi /etc/apt/sources.list
add this line “deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./” and save with “wq!”
$sudo apt-get update
$sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj
System > Administration > Printing, Add Printer, Select from List

---

### Post by wh0rd on 2006-12-16
> **mseney said:**
> Worked great for me and I am connecting to the printer via a Windows Workgroup share.

Edgy Eft 6.10

$sudo vi /etc/apt/sources.list
add this line &#8220;deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./&#8221; and save with &#8220;wq!&#8221;
$sudo apt-get update
$sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj
System > Administration > Printing, Add Printer, Select from List

These steps were really simple and fast, thanks! [B]For Canon Pixma MP130 choose iP1500 driver!
[/B]

---

### Post by rakeen on 2007-02-04
Hi all !

Thanks mr_niceguy, it works fine for me ! :cool:

Printer : Canon MP130 (using IP1500 driver). I'm now able to print in color.

System : Ubuntu Edgy 6.10

---

### Post by Lucifiel on 2007-05-21
I just tried this again on a fresh install of Feisty final. 

It works very well. :)

---

### Post by whorush on 2007-09-30
> **Lucifiel said:**
> I just tried this again on a fresh install of Feisty final. 

It works very well. :)

great to hear.  but how did you do it?

i'm running amd64 7.04.

i can't seem to convert the rpm's to debs.

this is my output for just one deb, i guess, i need to do it for all 4. i don't really get what its saying.

please help . thanks!

i also posted this here ([http://ubuntuforums.org/showthread.php?t=248745&highlight=pixma+ip1500&page=2](http://ubuntuforums.org/showthread.php?t=248745&highlight=pixma+ip1500&page=2))

-----

brad@amd64:~/Desktop/iP1500$ sudo alien bjfilter-common-2.50-2.i386.rpm
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
xargs -0 -r -i cp -a {} debian/bjfilter-common
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: could not find any packages for libcups.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path libcups.so.2, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpopt (soname 0, path libpopt.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libcups.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path libcups.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libcups.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path libcups.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libcups.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path libcups.so.2, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpopt (soname 0, path libpopt.so.0, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: bjfilter-common-2.50: No such file or directory

---

### Post by kiroshopa on 2007-10-15
Hi!
Everything is OK! with script.
Thanks a lot!
Canon Pixima iP1500 work perfectly with my ubuntu 7.04 and that's great.
Thanks again!

PS: Only one question: why i can't change intensity of ink and where i can find a tool for this job?

---

### Post by dratmooz on 2007-12-28
Confirmed working on 7.10 with a IP1500 using the following procedure:

> **mseney said:**
> Worked great for me and I am connecting to the printer via a Windows Workgroup share.

Edgy Eft 6.10

$sudo vi /etc/apt/sources.list
add this line “deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./” and save with “wq!”
$sudo apt-get update
$sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj
System > Administration > Printing, Add Printer, Select from List

---

### Post by unbutu on 2008-02-16
I'm trying to get my Canon iP1500 to work with 7.10 (on an x86-64 architecture).  I tried the procedure in the previous post and everything worked fine until this:

$ sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libcnbj-2.5
$

Has something changed in the last six weeks?

---

### Post by FPtje on 2008-02-25
> **dratmooz said:**
> Confirmed working on 7.10 with a IP1500 using the following procedure:
How to save with " wq!" ?
I am ubuntu noob

---

### Post by FPtje on 2008-02-25
I really want to know now!

---

### Post by mr_niceguy on 2008-02-25
> **FPtje said:**
> How to save with " wq!" ?
I am ubuntu noob

"vi" is a common editor for *nix systems and while it is feature rich it is not especially noob friendly. You can use "gedit" (graphical editor) or "nano" if you want to use a terminal based editor. So to translate - open a terminal and type: (follow terminal commands with the "enter" key)


sudo gedit /etc/apt/sources.list


Add this line: 


deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./


Save the file and close gedit.

---

### Post by FPtje on 2008-02-25
I still get this:
E: Couldn't find package libcnbj-2.5

I removed the printer and that line sudo apt-get remove bjfilter*
doesn't work: couldn't find libcbnj or something :(

---

### Post by FPtje on 2008-02-25
How to fix this?

---

### Post by FPtje on 2008-02-25
Halp meh plz!

---

### Post by FPtje on 2008-02-26
Please I really need help :(
I need to print something :(

---

### Post by unbutu on 2008-02-27
> **unbutu said:**
> I'm trying to get my Canon iP1500 to work with 7.10 (on an x86-64 architecture).  I tried the procedure in the previous post and everything worked fine until this:

$ sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libcnbj-2.5
$

Has something changed in the last six weeks?

Still can't find package libcnbj-2.5.  Are FPtje and I doing something wrong, or has something genuinely changed?

---

### Post by unbutu on 2008-03-04
Today I was forced to dig up my old Windows 98 machine just so I could print.  This is very disappointing.  There appears to be a way to get a Canon iP1500 to work under Ubuntu, and others were able to do it, but the instructions given either were incomplete or no longer work.  Either way, I'm not sure this problem can be considered "solved".

Just to be clear, here are the results of following the instructions [quoted here]("http://ubuntuforums.org/showpost.php?p=4030859&postcount=64").

First, I added a line to /etc/apt/sources.list:

```
deb http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu ./
```

Second, I updated the package information, and searching for "mambo" in the output of "sudo apt-get update" gives:

```
Ign http://mambo.kuhp.kyoto-u.ac.jp ./ Release.gpg
Ign http://mambo.kuhp.kyoto-u.ac.jp ./ Translation-en_US
Ign http://mambo.kuhp.kyoto-u.ac.jp ./ Release
Ign http://mambo.kuhp.kyoto-u.ac.jp ./ Packages
Hit http://mambo.kuhp.kyoto-u.ac.jp ./ Packages
```

Third, I tried to install the appropriate packages, but "sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj" gives:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libcnbj-2.5
```

And that's as far as I can go.  For completeness, I'm using Ubuntu 7.10 on an x86-64/amd64 architecture.

---

### Post by unbutu on 2008-03-06
I noticed today that there is a [parallel thread]("http://ubuntuforums.org/showthread.php?t=487890") to this one on the "tutorials" section of the forums, advocating the same solution that I've been trying.  That thread has many people with the same problem as me (unable to find the appropriate packages).  [Bad news for x86-64/amd64 people]("http://ubuntuforums.org/showpost.php?p=3831756&postcount=34"):

> Unfortunately the way the packages were built they do not support 64-bit Ubuntu. I have a laptop that is 64-bit and I couldn't even get the printer to work either so I just use 32-bit Ubuntu.

The other set of instructions to get the printer to work (see the [wiki]("https://wiki.ubuntu.com/CanonPixmaIP1500")) involves using alien on some rpm's, and that also won't work on the 64-bit architecture (see [earlier in this thread]("http://ubuntuforums.org/showpost.php?p=3454043&postcount=62"), for example).  

So it seems that there is no way to get the Canon PIXMA iP1500 to work on an x86-64/amd64 architecture.  I guess it's time to get a new printer.

---

### Post by mr_niceguy on 2008-03-07
> **unbutu said:**
> So it seems that there is no way to get the Canon PIXMA iP1500 to work on an x86-64/amd64 architecture.

That's really unfortunate. I wonder if Mandrake has drivers?

> **unbutu said:**
> I guess it's time to get a new printer.

I know I'll be voting with my wallet for hardware which supports open source. We need to send these guys a message.

---

