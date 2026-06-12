---
title: "ubuntu 9.10 services-admin application is missing"
date: 2009-10-18
forum: Installation &amp; Upgrades
---

### Post by odror on 2009-10-18
I am in the process of upgrading to ubuntu 9.10

I have noticed that 
System --> Administration --> Services (which is the application 'services-admin')

is missing.

I there any alternative?

-Thanks

---

### Post by johns996 on 2009-10-21
I am looking for this too.  Anyone have ideas?

I noticed that under my Software Center there is an item called *Services* that is installed and this seems to be what I'm looking for but I still can't find it on any menu.  It claims to be integrated with the "new GNOME Control Center" but I don't even see a link to this anywhere.

---

### Post by stlsaint on 2009-10-21
Applications>Ubuntu Software Center>System tools

is this what you are looking for?

---

### Post by odror on 2009-10-23
No I am looking for a gui to manage services (i.e. start, stop etc.)

-Thanks

---

### Post by iruel on 2009-10-23
> **odror said:**
> No I am looking for a gui to manage services (i.e. start, stop etc.)

-Thanks

you could use "bum"
with this command: 
**sudo apt-get install bum**

or you could get it from **Ubuntu Software Center > System Tools > Boot-Up Manager**
:guitar::guitar:

---

### Post by gatos on 2009-10-24
> **iruel said:**
> you could use "bum"
with this command: 
**sudo apt-get install bum**

or you could get it from **Ubuntu Software Center > System Tools > Boot-Up Manager**
:guitar::guitar:

hmmmm.... same problem here. Boot up manager is not what we are looking for. I have been searching for a while now, but no luck

---

### Post by Stebalien on 2009-10-25
The service-admin program was probably removed because Karmic has mostly switched to Upstart. I can't find any program that can manage Upstart services. Bum, service-admin, sysv-rc-conf, etc. only manage System V startup scripts.

Edit: See [this]("http://ubuntuforums.org/showthread.php?t=1272747") thread.

---

### Post by chuckh1958 on 2009-10-29
I'm having the same problem. If services-admin was removed, it should be removed from the system/administration menu too, but it was not. Is there a gui program name in 9.10 to enable/disable services?

---

### Post by shirish_nagar on 2009-10-31
And it's not solved yet?

---

### Post by reinholdmain on 2009-10-31
Is there an alternative to start and stop services without using the shell ? :(

---

### Post by chuckh1958 on 2009-10-31
> **shirish_nagar said:**
> And it's not solved yet?

Not to my knowledge.

I installed bum which is ok for someone who understands the run levels but not as simple as services-admin was for the casual user.

IMO if they are not supporting services-admin anymore it should be removed from the system menu, and some alternative should automatically replace it. I'm not sure where to report this to ensure that Canonical recognizes the problem and addresses it.

---

### Post by rvergara on 2009-11-01
I reviewed Synaptic looking for the Services Manager to no avail. I can not believe it was deprecated without a GUI alternative. Hope somebody finds a solution for this key missing application

---

### Post by Stebalien on 2009-11-01
I just wrote a simple service manager for karmic that should do until a real one is made. You can get it [here]("http://gtk-apps.org/content/show.php?content=114727").

---

### Post by rvergara on 2009-11-02
For the last 4 and half years I have been a strong Ubuntu supporter. However the more i read about this application missing the more I am disappointed about how this was managed. This makes me remember how I was mistreated by red hat when they dropped support to the desktop (RH8).

see the discussion here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/433701](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/433701)

Shouldn't they have kept the old application until a GUI alternative was ready? much worse is the fact that there was no advance notice to the community that the application was being dropped.

Ramiro

---

### Post by brianpatrick on 2009-11-06
Hi,
Do yourselves a giant favor and install Webmin. You can start and stop the services, do network shares, grub, config apache, samba, mysql, nfs, ... I can do all my machines from here!

It is pretty much one stop shopping for system administration. The ubuntu elves sometimes turn into gremlins and scramble the menus, remove useful tools, change interfaces, ... Must be bored. They have yet to break Webmin.

    BrianP

---

### Post by chuckh1958 on 2009-11-06
webmin is not in the karmic repos either.

I fixed the problem by disabling services-admin from the system menu, and installing bum (boot-up manager).

---

### Post by NoSheds on 2009-11-07
> **rvergara said:**
> For the last 4 and half years I have been a strong Ubuntu supporter. However the more i read about this application missing the more I am disappointed about how this was managed.

[SNIP]
 much worse is the fact that there was no advance notice to the community that the application was being dropped.

Ramiro

+1

Perhaps, post upgrade, Ubuntu should show a "What's changed" document, webpage or changelog.
Not enjoying the Karmic experience! :-(

---

### Post by sexyclient2 on 2009-11-09
It figures that after the gui tool was removed samba and cups fail to start automagically using the gui (for me, at least...)  Bravo.

---

### Post by negora on 2009-11-13
**Stebalien:** I had lost control over my Cups and Samba services because I had dis-activated them before upgrading to Ubuntu 9.10. BootUp-Manager couldn't "see" them so I had to manage them by command line. Thanks to your small application I've been able to gain control through a GUI again. Thank you a lot ;) .

---

### Post by demauk on 2009-11-14
Thanks, Stebalien! :biggrin:

---

### Post by ndmaque on 2009-11-14
@stebalian / anyone

i want your app but can't seem to dnload it from launchpad

not sure what i is doing wrong - auto dn fails and there is no link when try manual dnload - it must be me being daft as 200 others have it!

---

### Post by Stebalien on 2009-11-14
You have to click the "View Package Details" link on the PPA page to be able to download the package (I know, confusing).

BTW: Here is a direct link to the current deb: [simple-service-manager_0.003~ppa1_all.deb]("https://launchpad.net/~stebalien/+archive/simple-service-manager/+files/simple-service-manager_0.003~ppa1_all.deb")

You can also just add the ppa "ppa:stebalien/simple-service-manager" to your software sources and install "simple-service-manager" using apt-get, aptitude, synaptic etc.

---

### Post by ndmaque on 2009-11-15
@stebalian sorted cheers !

linux newbie (*|*)

---

### Post by Gyorgy on 2009-11-21
Thanks Stebalien !

Downloaded + installed w/ success.

As I am not much gifted w/ system admin knowldge, pls. forgive my innocence :
- how shall I use this application ?

I wish to do same as w/ previous 'services', in order to start - stop local web server LAMP ( and after this to develope with a cintent manager a web page...).

So all in all : what shall I thick/ un-thick when start the LAMP, and what, when finished ? ( please consider my ignorance).

Thank you very much in advance.

BR
Gyorgy

---

### Post by Stebalien on 2009-11-21
All apache and mysql services should be ticked (as far as I know). DO NOT untick anything that is ticked if you do not know what it is.

---

### Post by yota on 2009-11-24
Hi to everyone,

I did, much like Stebalien, an effort to create a service management tool for karmic, in short this is the result:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=137422&stc=1&d=1259053758[/IMG]

You can find more details here: [http://ubuntuforums.org/showthread.php?p=8376891](http://ubuntuforums.org/showthread.php?p=8376891)

If you find the tool interesting please drop a comment with your opinion and how it can be improved.

---

### Post by arcs123 on 2009-12-01
Got the same question as everyone else and still no answers ???!!!

found other posts that mentioned update-rc.d eg.

sudo update-rc.d -f sendmail remove    would prevent sendmail from starting as a service.

if interesting in service startup and stop relating to boot load time then i also came across the following today;

there is also the well-known "tweaks" by altering symlink names from being prefixed with S to K in /etc/rc.d/rc3.d/ directory (or whatever run level your bootloader refers.

i also installed sysv-rc.conf but agree with above that if using upstart then is this even relevant?

side note: grub2 has replaced grub with ubuntu 9.10 which adds even more confusion in this area because alot of the good resource materials i've found around opting which services to start and stop automaticaly at boot time are relevant only to the grub legacy configurations.....

am a newb with linux and was hoping that ubuntu 9.10 would provide an easier entry level than has so far been the case. particularly annoying when it looks so easy to do using RH / Fedora and chkconfig.

---

### Post by arcs123 on 2009-12-01
**- (Stebalien) -** Thanks alot for your contribution. Easy to install, easy to use!!!

for any other newbs here are the two commands to get this running :

wget [https://launchpad.net/~stebalien/+archive/simple-service-manager/+files/simple-service-manager_0.003~ppa1_all.deb](https://launchpad.net/~stebalien/+archive/simple-service-manager/+files/simple-service-manager_0.003~ppa1_all.deb)

sudo dpkg -i simple-service-manager_0.003~ppa1_all.deb

Then available on desktop under Applications -> System Tools.


One tiny bit of feedback - the Close button on the "About Simple Service Manager" doesn't work.... ;) .

---

### Post by arcs123 on 2009-12-01
Brian Patrick mentioned webmin earlier in this post.

have installed this on Ubuntu 9.10 - yes, it is excellent !!! Thanks for the tip Brian.

easy to install - [http://www.webmin.com/deb.html](http://www.webmin.com/deb.html)

again, use wget [http://sourceforge.net/projects/webadmin/files/webmin/1.490/webmin_1.490_all.deb/download](http://sourceforge.net/projects/webadmin/files/webmin/1.490/webmin_1.490_all.deb/download)

to actually download the .deb file once dependencies installed using:

apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl

However, i cannot see which view in webmin actually gives the services listing.

Can anyone clarify ?

---

### Post by sanfinix on 2009-12-04
Hi to everyone.
 
I'tried this way.
 
The services-admin panel is hidden behind a flag "modalità avanzata" in italian, in Boot up Manager.
 
If you click this flag (advanced mode I presume) the tab named "Services" appear...
 
Try it!
 
I hope this information is useful.
 
Bye and sorry for my english.
 
Enzo

---

### Post by Rytron on 2009-12-10
> One tiny bit of feedback - the Close button on the "About Simple Service Manager" doesn't work.... ;) .

It works for me!

Edit: To clarify; the 'About Box' close button doesn't work but the close button on the main window does work.

---

### Post by Rytron on 2009-12-10
Do you need to be online to use webmin?

---

### Post by bobmct on 2009-12-10
NOPE:  from your browser you would use as a URL http(s)://127.0.0.1:10000

That should get you there.  Good luck.

---

### Post by Rytron on 2009-12-10
> **bobmct said:**
> NOPE:  from your browser you would use as a URL http(s)://127.0.0.1:10000

That should get you there.  Good luck.

Thank you bobmct. ;)

---

### Post by azendal on 2010-02-16
there is service which you can use from the command line
sudo service --status-all to check all the services status
go man service to see the help

---

### Post by SoFl W on 2010-04-21
> **sanfinix said:**
> Hi to everyone.
 I'tried this way.
 The services-admin panel is hidden behind a flag "modalità avanzata" in italian, in Boot up Manager.
 If you click this flag (advanced mode I presume) the tab named "Services" appear...
 Try it!
 I hope this information is useful.
 Bye and sorry for my english.
 Enzo

Yes at the bottom of "boot-up manager" there is an "advanced" check box.  If you click that the services tab appears.

---

### Post by kat_ams on 2010-06-15
It looks like Services-admin is not dead... they just ran out of time to finish it in time for the Lucid release. It's ready just needs testing.

[https://blueprints.launchpad.net/ubuntu/+spec/desktop-lucid-services-settings-window]("https://blueprints.launchpad.net/ubuntu/+spec/desktop-lucid-services-settings-window")

---

### Post by zong1 on 2010-06-26
> **Stebalien said:**
> You have to click the "View Package Details" link on the PPA page to be able to download the package (I know, confusing).

BTW: Here is a direct link to the current deb: [simple-service-manager_0.003~ppa1_all.deb]("https://launchpad.net/~stebalien/+archive/simple-service-manager/+files/simple-service-manager_0.003~ppa1_all.deb")

You can also just add the ppa "ppa:stebalien/simple-service-manager" to your software sources and install "simple-service-manager" using apt-get, aptitude, synaptic etc.


Edited. Found the link here:
```

 wget https://launchpad.net/~stebalien/+archive/simple-service-manager/+files/simple-service-manager_0.003~ppa1_all.deb

```

---

### Post by jefelex on 2010-08-18
Thanks all - bum is kind of what I was looking for - I'll have to play with it for a while and see if it does what I think it will do! :-)

John

---

