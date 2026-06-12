---
title: "Uninterruptible Power Supply - Soft shutdown with an auto boot"
date: 2010-11-29
forum: Hardware
---

### Post by JumpForJoy on 2010-11-29
Hi, I was looking at buying an Uninterruptible Power Supply for my Ubuntu Server.  I've had some troubles with losing data when my server crashes before.  An Uninterruptible Power Supply will fix this problem, but instead of letting my computer hang on a bit longer, I'd like to find a UPS that would soft shutdown my server.  It would also be great if it could reboot my server when the power comes back on, but if that isn't possible that's fine.  I've read in some places that a auto-boot when the power comes back on can be accomplished by configuring your bios, but how would this effect my UPS.  Also, what size UPS should I be looking at if all I want to do is have enough power to shutdown my server?

Thanks for all the help,
Jump For Joy

---

### Post by oldsoundguy on 2010-11-29
Check the APC line .. they have a software driven shutdown that will do the job for your un-attended equipment .. and they are the cleanest of the UPS units as far as the output power.  BUT, they are not CHEAP and the batteries need to be replaced about once every 3 years or so and THOSE ALSO are not cheap. An APC 1400 will deliver almost 1 KVA for an hour before it runs out of go juice .. if you have the shutdown set up .. that is plenty of time to run your programs out and soft shut down.

---

### Post by JumpForJoy on 2010-11-30
Awesome, thanks.  I'm looking at the _[APC Back-UPS ES 8 Outlet 550VA 120V]("http://www.apc.com/products/resource/include/techspec_index.cfm?base_sku=BE550G&total_watts=200")_.  It looks solid and like it will last long enough.  I'm a little worried that I won't be able to run the software correctly on ubuntu though.  I found the _[apcupsd]("https://help.ubuntu.com/community/apcupsd")_ package for ubuntu that should take care of the soft shutdowns and reboots.  But I'm not sure if configuring my UPS on a windows computer (via the software APC provides to adjust max voltage and the alarm settings) would allow it to stay configured when working with Ubuntu.  I was also wondering if the warning messages (low power and battery problems) could be broadcasted across my Ubuntu server, seeing as how that feature is added by the software that only runs on Windows and Mac OSX.

Thanks for you help,
JumpForJoy

---

### Post by JumpForJoy on 2010-12-03
Ok.  I've bought the UPS from APC.  It everything works great except rebooting after the power goes out.  I charged the UPS then unplugged it.  After letting the battery die and watching the server shut itself down, I waited.  No matter how long I waited though, my server never rebooted.  I've set my bios to turn my computer on after A/C power dies, but my UPS shutsdown via halt.  I'm also using apcupsd to run all this stuff.

---

### Post by CharlesA on 2010-12-03
That is normal. It won't power the machine back on after an outage automatically because the battery needs to charge. If the power went out again while the battery was changing, the machine could power off unexpectedly.

The BIOS setting only makes the machine power on if it was on when the power went out.

---

### Post by JumpForJoy on 2010-12-03
Hm, ok.  How would one go about allowing it to reboot after the power comes back on.  I set "RETURNCHARGE 15" which I though is all I needed to do to allow the UPS to restart the computer when it has a charge of 15%.  Is there something else that has to be set up?  Also, _[Ubuntu help]("https://help.ubuntu.com/community/apcupsd")_ says: ```
Optionally, if you want your computer to reboot after a power fail, you must edit the /etc/init.d/halt due a bug that it has. You must change the poweroff="-p" with poweroff=""
```
but removing the -p causes halt to not work and instead leave my computer with half the stuff turned off, ie. the power light and monitor on with the harddrives spun down.

Thanks for your help,
Jump for Joy

---

### Post by CharlesA on 2010-12-03
Not sure. If the machine supports Wake on LAN, you could use that to wake it up, but you'd have to do it manually.

I've never had the machine power itself back on automatically after a power outage. I've always had to turn it on myself.

The reason for that is the same as my previous post: It can't check to see if the power is back on when the PC is powered off, since there is no communication between the UPS and the PC.

---

### Post by JumpForJoy on 2010-12-03
ah ok.  I'll take a look into wake on LAN, but the line from the Ubuntu apcupsd help page makes me think that it can be done.  Anyone else have any suggestions, I'm puzzled?

Thanks,
JumpForJoy

---

### Post by CharlesA on 2010-12-03
Keep in mind that sometimes the help pages, or wiki have outdated info. 

Check out the manual over here: [http://www.apcupsd.com/](http://www.apcupsd.com/)

---

### Post by JumpForJoy on 2010-12-03
Hm, ok.  That website also give similar information [here]("http://www.apcupsd.org/manual/manual.html#arranging-for-reboot-on-power-up").  I've gone through all those steps except the remove -p one, which crashes halt.  Perhaps I'm missing something with how to remove -p?  Do you know which line you remove it from in /etc/apcupsd/apcupsd.conf?

Thanks for the help,
JumpForJoy

---

### Post by CharlesA on 2010-12-03
Judging from the instructions, you'd have to edit something in the init script, but I don't know what you'd edit or what effect it would have if you wanted to do a normal shutdown.

---

### Post by JumpForJoy on 2010-12-03
Hm, ok.  Playing around with -p's in halt didn't help much.  But when I tried to run apctest, I got some errors:
```
JumpForJoy@server1:~$ apctest 


2010-12-03 20:04:39 apctest 3.14.6 (16 May 2009) debian
Checking configuration ...
Attached to driver: usb
sharenet.type = DISABLE
cable.type = USB_CABLE

You are using a USB cable type, so I'm entering USB test mode
mode.type = USB_UPS
Setting up the port ...
apctest FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
apctest error termination completed
```

Does this mean that I set the config up incorrect?  My UPS connects to my server by a data (looks like ethernet port) to a usb on my computer?

Thanks for the help,
JumpForJoy

Edit: I can also get information from my UPS by using apcaccess.  So I doubt that the cable is the problem.

Edit: Well I got it to work!  I adjusted the grace time to 20 seconds and the returncharge to 00.  Thanks for your help CharlesA!!

---

### Post by CharlesA on 2010-12-03
Did you get it to power on the machine after the UPS shut it down?

---

### Post by JumpForJoy on 2010-12-03
Yep, once the power comes back on, the UPS turns back on which then turns my computer back on.  And thanks for all your help!

---

### Post by CharlesA on 2010-12-04
Could you post yer /etc/apcupsd/apcupsd.conf file, so I can compare it to mine.

Thanks. :)

---

### Post by sidcypher on 2011-02-02
I would like to see that conf file as well. though I have not reached the testing phase of powering off... as I currently have a error I am trying to resolve...

---

