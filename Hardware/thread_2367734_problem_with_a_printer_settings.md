---
title: "problem with a printer settings"
date: 2017-08-02
forum: Hardware
---

### Post by oldsoundguy on 2017-08-02
Running 16.04 and have an HP Color Laser Printer model 2840.  It has a "manual duplex" setting.  I go to the printer setup and click on the "manual duplex" but the "apply" button is greyed out and will not allow completion. ... sure would like to be able to get that working.

Any clues??

---

### Post by vocx on 2017-08-02
> **oldsoundguy said:**
> Running 16.04 and have an HP Color Laser Printer model 2840.  It has a "manual duplex" setting.  I go to the printer setup and click on the "manual duplex" but the "apply" button is greyed out and will not allow completion. ... sure would like to be able to get that working.

Any clues??

Are you sure you are using HPLIP to install and configure your printer? I think many laser printers use a generic driver, so many users can use their printer immediately in Ubuntu, although they may not be able to use every function without HPLIP.

The HP website lists it as "supported", although "not recommended". I guess this means the printer is an old model, so it may work, but maybe not with all options.
[http://hplipopensource.com/hplip-web/models/color_laserjet/hp_color_laserjet_2840.html](http://hplipopensource.com/hplip-web/models/color_laserjet/hp_color_laserjet_2840.html)

See here for information on using HP printers
[https://ubuntuforums.org/showthread.php?t=2364149&p=13658387#post13658387](https://ubuntuforums.org/showthread.php?t=2364149&p=13658387#post13658387)

If you are already using HPLIP and it's working correctly, then I don't know what else to suggest. Maybe the HPLIP drivers really don't support that function.

---

### Post by Bucky Ball on 2017-08-03
As above. You need to install HPLip if you haven't already, then reboot. You can find it in 'Ubuntu Software' (the default Ubuntu package manager, not sure what that's called now as I use Xubuntu and Synaptic Package Manager). NO NEED to install from the HP website or any other third-party site. If an apps in the official repository, best to go for that unless you have very good reasons not to (extremely new hardware that won't work with the default driver in the repo, for instance).

After reboot it may be an idea to open 'Printers', delete the printer you have created in there and add your printer again. You should find the correct driver for the 2840 when you get to that part of adding the printer.

---

### Post by oldsoundguy on 2017-08-03
Thanks .. but have had hplip installed for a while.   I go into HP device manager and it gives me all kinds of options for the fax.  I go into Sundry-Printers-local host right click and select the specific printer and get the printer properties.  That gives me sub categories.  I select the options and that screen has finishing options for manual duplex.  I tick it and it SHOULD un-grey the apply button, but it DOES NOT.

HPLIP device manager is mostly instructions on the fax plus cups, a link to HP support and a help page.

The printer works fine.  The fax works fine. The scanner works fine. the UTILITIES work fine (get read outs on toners, etc).  

It is just that APPLY button!


BTW .. all of my printers (I have 3) are on a hub on a home network ... An HP Color Laser 2840 AIO (default printer, copier, fax), an Epson Stylus PRO 3800 (photography .. large bed, multi media) and an old HP Photo Smart 1215 (inkjet) (equipped with duplexing attachment) as a back up.  
The net is 2 home brew (basically HP guts) Main box running Ubuntu 16.04 LTS, Photo box running XP (yea, I KNOW ... but I have about 3 grand tied up in Photo processing/editing programs that will NOT migrate to a newer OS) .. and I have my Laptop running Win7.  The XP box keeps losing contact with the network printers(had been using it as means of printing instruction manuals for electronics equipment that I refurbish) (does not tie up the machines I do my WORK ON) .. this last time was the last straw .. hence the need to get Ubuntu to work with all of the features of the printers

---

### Post by oldsoundguy on 2017-08-05
Managed to mess around and get the activate button where I could click on it.  But the printer ignores the instructions or it is not GETTING the instructions .. I go to the printer after it has been selected to print and the instructions are THERE for all to see ... except the printer doesn't see the same thing.  This should not be that difficult.  There has to be something I am missing here.  

Ubuntu has proven to be an easy OS to work with .. IE> I installed a WiFi dongle in about two minutes with all of two clicks and type in the network password.  Getting this printer to work as intended and as it is being TOLD to do should not require a day and a half under the hood. (yes, I remember those days not too fondly).

---

### Post by vocx on 2017-08-06
> **oldsoundguy said:**
> Thanks .. but have had hplip installed for a while
You should have mentioned this in your initial post just so we don't unnecessarily recommend it again.

> **oldsoundguy said:**
> Managed to mess around and get the activate button where I could click on it.  But the printer ignores the instructions or it is not GETTING the instructions...
I would contact HP and ask them for further advice while explaining your problem like you do here.

---

### Post by oldsoundguy on 2017-08-06
It turns out that the problem is in the repository version of HPLIP.  There is a slightly different version available FROM HP.  BUT, my copy/paste into terminal gets me NOWHERE.  Been a VERY long time since I have been under the Linux hood, and I can't seem to get anywhere.  (first issue is that my downloads do not go to my desktop.  They go to my Download Folder!!)

When you get up to my age, takes a lot of effort to prowl around inside the brain to "find things".

Weeeeellll .... after putsing with this all afternoon and installing something from HP (hplip -3.17.7) .. still no joy!!

---

### Post by Bucky Ball on 2017-08-07
What is the problem you are having with the version of hplip in the repositories, if you wouldn't mind elaborating? The fact that it is not picking up your printer and installing the drivers for it automatically? Are you finding the correct driver for it when you open 'Printer> Add Printer' and get to the driver install section?

---

### Post by oldsoundguy on 2017-08-07
In doing a bit of research, it was recommended that I use the HPLIP from the HP site as it would, most likely solve the issue.  Turns out it did NOT solve the problem, but everything else works just fine .. there has to be a "trick" somewhere to get the manual duplex setting to work.  At a loss right now.  I would really like to get this working as I do print a lot of manuals to accompany the items I refurbish and sell. (saves a lot of eMail exchanges!!) Some of those manuals are nearly 100 pages.  I DO have my back up printer that has a mechanical duplex on it .. but it is a jet and is slooooooooow.

---

### Post by gsahli on 2017-08-10
manual duplex "might be" found in the cups web page settings. If you've never done that, try following:
[https://docs.oracle.com/cd/E23824_01/html/821-1451/gllhj.html](https://docs.oracle.com/cd/E23824_01/html/821-1451/gllhj.html)

---

### Post by oldsoundguy on 2017-08-10
found this on HPLIP site:

Manual Duplex feature is not yet supported through HPLIP. HPLIP supports only Auto Duplex feature as of now.

Thanks,
Sanjay

So all of the time wasted on that was to no avail.
Will explore the cups option.

---

### Post by Bucky Ball on 2017-08-10
As above. Try the CUPS web interface. Open a web browser and in the address bar type 'localhost:631' and hit return.

That should take you to the CUPS page. If you need to login, use your Ubuntu username and password. You will be able to adjust your printer there.

If 'localhost:631' throws an error and doesn't take you to CUPS, please post that error here.

* You beat me to it with your last post. I see.

> **oldsoundguy said:**
> 
So all of the time wasted on that was to no avail.
Will explore the cups option.

These things happen. We live and learn. :) Yes, try the CUPS route.

---

### Post by oldsoundguy on 2017-08-12
got some time to work on this for the next couple of days.

made sure CUPS got installed, but when I go to localhost:631 to verify .. nothing happens!  No error message

---

### Post by gsahli on 2017-08-12
try localhost:631/admin

---

### Post by oldsoundguy on 2017-08-12
nor does  localhost:631/admin  .. same story

---

### Post by gsahli on 2017-08-13
run this in Terminal, then try again:
sudo cupsctl WebInterface=Yes

---

### Post by oldsoundguy on 2017-08-13
no joy on that one either!!  I KNOW I am missing something here.

I took some time and un-installed and re-installed CUPS .. that was not the answer, but at least I KNOW for sure that the whole program is on the hard drive.

---

### Post by gsahli on 2017-08-14
Try 127.0.0.1:631
If no go, show us your /etc/hosts file.

---

### Post by oldsoundguy on 2017-08-14
llowing lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by gsahli on 2017-08-14
Your hosts file is for IPv6 Only. It is missing the IPv4 portion. So, I think, it's missing the correct localhost info. I'm not really an expert here, but I think this is your problem.
Here's mine:
127.0.0.1	localhost
127.0.1.1	trireme  #(my machine's hostname)

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

---

### Post by Bucky Ball on 2017-08-15
Just throwing this in: you do NOT need 'localhost:631/admin'. No need. 'localhost:631' is it and if that doesn't get you a log in pop up, something is amiss.

---

### Post by vocx on 2017-08-15
> **Bucky Ball said:**
> Just throwing this in: you do NOT need 'localhost:631/admin'. No need. 'localhost:631' is it and if that doesn't get you a log in pop up, something is amiss.
Why exactly is this required, again?

I've never accessed the CUPS webserver. Pretty much like oldsoundguy, I cannot actually do it. My system doesn't find the address. Nevertheless, I've never had a problem printing or scanning. I'm using HPLIP and an HP printer. So, basically, I have no problems, I just find it curious that people are suggesting this. I didn't even knew such webserver existed.

In my system there seem to be two services for CUPS. Maybe they need to be restarted.
```

sudo service cups restart
sudo service cups-browsed restart

```

---

### Post by gsahli on 2017-08-15
The cups admin webpage is an alternative to all the other preference setting applets for printing. It's only used when you don't get results with other applets. It's also useful for setting different "defaults" from usual. Example, setting A4 as default paper.

---

### Post by wildmanne39 on 2017-08-15
Please do not create duplicate posts, if you want to add more information just edit your original post.

Thanks

---

### Post by oldsoundguy on 2017-08-16
OK ... got into cups  it is [http://localhost:631](http://localhost:631).  
tried a second install of the printer and it will not allow manual duplexing ... I see another suggestion that I will follow.  
Right now have to break from this and get out and stock up as this town is in the process of becoming a ZOO .. it is called "Solar Eclipse" and the traffic is already getting out of hand.

---

### Post by Bucky Ball on 2017-08-16
> **gsahli said:**
> The cups admin webpage is an alternative to all the other preference setting applets for printing. It's only used when you don't get results with other applets.

This is not really accurate. Some people ONLY use CUPS and never use other apps. Not because they have to, but because they want to. I used to install and configure all my printers using CUPS only. Didn't have a printer app installed. (I used to only install the Ubuntu minimal install and build it up from there, so didn't add 'Printers'. No need.)

Server people use it to communicate remotely with printers, regular users use it to install and configure printers. No way is it a 'last resort' for everyone, but if your printer is not showing in CUPS, then something's amiss. So yes, in that respect, you can certainly use it to troubleshoot. ;)

@OP: Great you managed to get somewhere with CUPS. Just wondering; what's so special about a solar eclipse, apart from the fact that those are special? Why the zoo in the streets?

---

### Post by oldsoundguy on 2017-08-16
I live in Salem, Oregon.  and the "path" literally bisects my back yard!  Predicted that there will be 1,000,000+ people with their cars visiting the state and they need to have a place to stay and eat .. yet alone any problems.  Governor Kate has called out The National Guard to assist.  We have a two bridge east west crossing of the Willamette river (5 lanes on each bridge) and they are going to shut them down and turn it over to pedestrians.  Motel rooms are all filled up, so they opened all of our city parks for camping. (those motel rooms went for an average price of $700.00!!)

as to the CUPS issue .. it did not allow duplexing .... so, that pretty well shuts things down there .. I still can use the printer, but not all of the features.

---

