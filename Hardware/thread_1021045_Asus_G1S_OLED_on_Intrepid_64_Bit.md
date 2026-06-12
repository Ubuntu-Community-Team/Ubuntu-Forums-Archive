---
title: "Asus G1S OLED on Intrepid 64 Bit"
date: 2008-12-24
forum: Hardware
---

### Post by noahTHEpurdy on 2008-12-24
Hey all. I have searched and searched and I tried both the "lonewolf" scripts and a few other things to get the OLED on my G1S running but I just can't seem to.

For those that have, can you give me the step by step? Thanks.

-------------------------------------------------------------------------------------------------

Thank you Costin for updating the script to work in Intrepid and the tip on getting it to start at boot. Solution can be found here: [http://ubuntuforums.org/showpost.php?p=6497623&postcount=15](http://ubuntuforums.org/showpost.php?p=6497623&postcount=15)

---

### Post by noahTHEpurdy on 2008-12-25
Bump. Anyone?

---

### Post by noahTHEpurdy on 2008-12-28
Bump. :'(

---

### Post by noahTHEpurdy on 2008-12-29
Pwease!?

---

### Post by noahTHEpurdy on 2009-01-02
Bump.

---

### Post by hotweiss on 2009-01-03
Have you tried this solution:

[http://monalisa.cern.ch/blog/2008/09/16/ubuntu-on-asus-g50v/](http://monalisa.cern.ch/blog/2008/09/16/ubuntu-on-asus-g50v/)

and this solution:

[http://asusg1s.wikidot.com/ubuntu-7-10](http://asusg1s.wikidot.com/ubuntu-7-10)

and this solution:

[http://wiki.archlinux.org/index.php/Asus_G1](http://wiki.archlinux.org/index.php/Asus_G1)

---

### Post by noahTHEpurdy on 2009-01-03
Thank you hotweiss;

I followed the instructions at the bottom of the page of the following site:

[http://asusg50oled.sourceforge.net/](http://asusg50oled.sourceforge.net/)

I get to this point:

```
# ./start.sh
# utils/install.sh
```

When I run the start.sh file, my OLED display displays like it correctly should, however when I run the install.sh file in the utils directory I get the following:

```
Found acpid as /etc/init.d/acpid, installing event handlers in /etc/acpi
 * Reloading ACPI services...                                            [ OK ] 
Installing Ubuntu/Debian startup script
update-rc.d: warning: /etc/init.d/asusg50leds.sh missing LSB style header
 System startup links for /etc/init.d/asusg50leds.sh already exist.
```

When I restart my system, the OLED does not load the drivers / script automatically and just displays the standards ASUS logo. I tried adding the start.sh script to my sessions list, but that didn't work and doesn't seem like the correct thing to do.

Any ideas?

PS: Zeitgeist was an excellent movie.

---

### Post by hotweiss on 2009-01-04
> **noahTHEpurdy said:**
> Thank you hotweiss;

I followed the instructions at the bottom of the page of the following site:

[http://asusg50oled.sourceforge.net/](http://asusg50oled.sourceforge.net/)

I get to this point:

```
# ./start.sh
# utils/install.sh
```

When I run the start.sh file, my OLED display displays like it correctly should, however when I run the install.sh file in the utils directory I get the following:

```
Found acpid as /etc/init.d/acpid, installing event handlers in /etc/acpi
 * Reloading ACPI services...                                            [ OK ] 
Installing Ubuntu/Debian startup script
update-rc.d: warning: /etc/init.d/asusg50leds.sh missing LSB style header
 System startup links for /etc/init.d/asusg50leds.sh already exist.
```

When I restart my system, the OLED does not load the drivers / script automatically and just displays the standards ASUS logo. I tried adding the start.sh script to my sessions list, but that didn't work and doesn't seem like the correct thing to do.

Any ideas?

PS: Zeitgeist was an excellent movie.

Did you try following these instructions from that page:

>     *  # We have to work as root
    * sudo su -
    * # Make sure all the required packages are installed
    * apt-get install sun-java6-bin subversion make gcc smartmontools netcat
    * update-alternatives --set java /usr/lib/jvm/java-6-sun/jre/bin/java
    * # Get the latest version of asus_oled and install it
    * cd /usr/src/
    * svn co svn://svn.berlios.de/lapsus/asus_oled/trunk asus_oled
    * cd asus_oled
    * make
    * make install
    * # Load asus_oled before usbhid (2.6.28 will contain the fix for this)
    * rmmod usbhid
    * modprobe asus_oled
    * modprobe usbhid
    * dmesg | grep asus-oled

      [   23.216917] asus-oled 4-4:1.0: Attached Asus OLED device: G50 [width 256, pack_mode 1]
      [   23.216933] usbcore: registered new interface driver asus-oled

    * # Get and install the daemon
    * cd /opt/
    * wget [http://asusg50oled.sourceforge.net/download/asusg50oled.tgz](http://asusg50oled.sourceforge.net/download/asusg50oled.tgz)
    * tar -xzf asusg50oled.tgz
    * cd asusg50oled
    * ./start.sh
    * utils/install.sh
    * # See how to configure the daemon and the notifications
    * less README

I don't have a G50, so I can't troubleshoot this problem on my side.

---

### Post by noahTHEpurdy on 2009-01-04
Yes. I have a G1S, not a G50. 

I did those instructions. The ./start.sh runs perfectly and it displays on the OLED, but when I do install I get the error that I listed above. (Second code box I posted.)

---

### Post by hotweiss on 2009-01-04
> **noahTHEpurdy said:**
> Yes. I have a G1S, not a G50. 

I did those instructions. The ./start.sh runs perfectly and it displays on the OLED, but when I do install I get the error that I listed above. (Second code box I posted.)

What about just copying start.sh into your /etc/init.d directory so it simply starts when Ubuntu starts?

---

### Post by noahTHEpurdy on 2009-01-04
> **hotweiss said:**
> What about just copying start.sh into your /etc/init.d directory so it simply starts when Ubuntu starts?

No dice. :(

---

### Post by hotweiss on 2009-01-04
> **noahTHEpurdy said:**
> No dice. :(

At this point I would try to download the latest version:

> * # We have to work as root
* sudo su -
* # Make sure all the required packages are installed
* apt-get install sun-java6-bin subversion make gcc smartmontools netcat
* update-alternatives --set java /usr/lib/jvm/java-6-sun/jre/bin/java
* # Get the latest version of asus_oled and install it
* cd /usr/src/
* svn co svn://svn.berlios.de/lapsus/asus_oled/trunk asus_oled
* cd asus_oled
* make
* make install* # We have to work as root
* sudo su -
* # Make sure all the required packages are installed
* apt-get install sun-java6-bin subversion make gcc smartmontools netcat
* update-alternatives --set java /usr/lib/jvm/java-6-sun/jre/bin/java
* # Get the latest version of asus_oled and install it
* cd /usr/src/
* svn co svn://svn.berlios.de/lapsus/asus_oled/trunk asus_oled
* cd asus_oled
* make
* make install
* # Load asus_oled before usbhid (2.6.28 will contain the fix for this)
* rmmod usbhid
* modprobe asus_oled
* modprobe usbhid
* dmesg | grep asus-oled
* # Load asus_oled before usbhid (2.6.28 will contain the fix for this)
* rmmod usbhid
* modprobe asus_oled
* modprobe usbhid
* dmesg | grep asus-oled

---

### Post by noahTHEpurdy on 2009-01-04
I have just tried everything from scratch. I am getting an error saying that the startup script it generates and puts into /etc/init.d is missing an LSB style header.

Any idea on that?

---

### Post by hotweiss on 2009-01-04
> **noahTHEpurdy said:**
> I have just tried everything from scratch. I am getting an error saying that the startup script it generates and puts into /etc/init.d is missing an LSB style header.

Any idea on that?

Those kind of errors are out of my league...

---

### Post by costing on 2009-01-05
Please download again [http://asusg50oled.sourceforge.net/download/asusg50oled.tgz](http://asusg50oled.sourceforge.net/download/asusg50oled.tgz) , it now contains the proper headers and should work fine in 8.10 as well.

Or you could edit /etc/rc.local and add (above "exit 0"):
/etc/init.d/asusg50leds.sh start

Cheers,

.costin

---

### Post by noahTHEpurdy on 2009-01-05
> **costing said:**
> Please download again [http://asusg50oled.sourceforge.net/download/asusg50oled.tgz](http://asusg50oled.sourceforge.net/download/asusg50oled.tgz) , it now contains the proper headers and should work fine in 8.10 as well.

Or you could edit /etc/rc.local and add (above "exit 0"):
/etc/init.d/asusg50leds.sh start

Cheers,

.costin

Costin; thank you so much. This got it working. For your reference though redownloading it and re-running the install.sh script did not get it to work. I receieved the following and upon restart it did not automatically start up:

```
Found acpid as /etc/init.d/acpid, installing event handlers in /etc/acpi
 * Reloading ACPI services...                                            [ OK ] 
Installing Ubuntu/Debian startup script
 System startup links for /etc/init.d/asusg50leds.sh already exist.
```

However adding ```
/etc/init.d/asusg50leds.sh start
``` to /etc/rc.local worked just fine.

> **hotweiss said:**
> Those kind of errors are out of my league...
Thank you so much for your help regardless! It is greatly appreciated!

---

### Post by costing on 2009-01-05
Yes, before re-trying you should've:
# rm /etc/init.d/asusg50leds.sh

maybe also (but probably not, since the adding didn't work in the first place)
# update-rc.d asusg50leds.sh remove

Cheers,

.costin

---

### Post by noahTHEpurdy on 2009-01-05
I did remove the script from /etc/init.d with gksu nautilus before I ran it again.

I'll try those.

---

### Post by noahTHEpurdy on 2009-01-05
I removed the script from /etc/rc.local and ran both:

```
rm /etc/init.d/asusg50leds.sh
update-rc.d asusg50leds.sh remove
```

And then re-ran the installation script. It looked like it ran/installed fine, however on reboot It did not start.

---

### Post by costing on 2009-01-05
Could you please post the output of utils/install.sh?

If you run manually now
/etc/init.d/asusg50leds.sh start
does it start correctly ?

---

### Post by noahTHEpurdy on 2009-01-05
Running /etc/init.d/asusg50leds.sh start works.

Here is the output when I run install.sh:

```
Found acpid as /etc/init.d/acpid, installing event handlers in /etc/acpi
 * Reloading ACPI services...                                            [ OK ] 
Installing Ubuntu/Debian startup script
 Adding system startup for /etc/init.d/asusg50leds.sh ...
   /etc/rc0.d/K20asusg50leds.sh -> ../init.d/asusg50leds.sh
   /etc/rc1.d/K20asusg50leds.sh -> ../init.d/asusg50leds.sh
   /etc/rc6.d/K20asusg50leds.sh -> ../init.d/asusg50leds.sh
   /etc/rc2.d/S20asusg50leds.sh -> ../init.d/asusg50leds.sh
   /etc/rc3.d/S20asusg50leds.sh -> ../init.d/asusg50leds.sh
   /etc/rc4.d/S20asusg50leds.sh -> ../init.d/asusg50leds.sh
   /etc/rc5.d/S20asusg50leds.sh -> ../init.d/asusg50leds.sh

```

---

### Post by costing on 2009-01-05
That's weird...

Could you do the following please? Remove leds.log from the app folder, reboot and, without trying to start it again, post the contents of the fresh leds.log. Then the contents of the same file after you manage to start it.

Thanks a lot,

Cheers,

.costin

---

### Post by noahTHEpurdy on 2009-01-05
Upon reboot I do not have a fresh leds.log file.

After running /etc/init.d/asusg50leds.sh start to start the LCD this is what was contained in the leds.log:

```
ASUS G1 forced in the configuration file
Didn't find 'dcop' command line tool in $PATH, disabling DCOP support
Getting the battery info from /sys/class/power_supply/BAT0/{energy_full,energy_now}
Reading CPU temperature from /sys/class/thermal/thermal_zone0/temp
```

---

### Post by costing on 2009-01-05
So the script is actually never called at boot. What is the output of "runlevel"? If it's "N 2" then everything is just as it should and I'm running out of ideas :)

---

### Post by noahTHEpurdy on 2009-01-05
```
root@Mjlonir:/etc/init.d# runlevel asusg50leds.sh
unknown

```

That could be it. Suggestions?

---

### Post by costing on 2009-01-05
no, just simply "runlevel"

---

### Post by noahTHEpurdy on 2009-01-05
Oh. Yep, that's just N 2.

---

### Post by costing on 2009-01-05
Then just leave the call in /etc/rc.local, I cannot tell why it doesn't get called at boot as it should, when the setup seems ok :(

---

### Post by kyllikki on 2009-07-21
The daemon used to work perfectly for me on Intrepid 64 bit.  However, since upgrading to Jaunty I've failed to get it to work.

I can verify that the driver itself (from BerliOS) is working, but when I run start.sh manually there is no change.

The output in the leds.log is as follows:

```
Found an ASUS OLED device under '/sys/class/asus_oled/oled_1/picture'
Sorry, cannot find the asus_oled entry in /sys/class/asus_oled/. Please make sure you did all the following:
- grabbed the latest version of asus_oled from SVN
- executed make and make install for asus_oled
- rmmod usbhid; modprobe asus_oled; modprobe usbhid.
```

I made sure to grab the latest versions and having successfully set it up before I don't think I'm doing anything wrong :-)

---

### Post by costing on 2009-07-21
What happens when you go the where the module sources are and do a 
$ cat tux.txt > /sys/class/asus_oled/oled*/picture
?

Normally you should see the tux on the oled screen, but I've heard that in some cases the above command ends with an error. If this is the case you should contact the kernel module developer and provide as much information as possible about this issue (uname -a, modinfo asus_oled, dmesg ...).

---

### Post by mcurran on 2009-07-23
BUMP!

I get exactly the same message in the log file and mine isn't working either.  I'm currently running Jaunty x64 (2.6.28-14-generic).  I used to have to recreate the startup script and symlinks, but I did that and still no go for me...

---

### Post by kyllikki on 2009-07-24
The error I get is:

```
cat: write error: Bad address asus oled
```

---

### Post by LexMortis on 2009-07-24
It seems I have the exact same issues as [noahTHEpurdy]("http://ubuntuforums.org/member.php?u=566208").
I can run the start script manually, I can run the install script without any issues at all. It looks mighty fine on my G2k (so kudos on that).
But no matter what I try or do, it simply will never start automatically on booting.

I've read this entire thread and did pretty much everything that costing+noah tried/said.
It really does seem like the exact same issue as noah has. Although I run 9.04 32 bit..

costing.. any ideas?
If you need more details, please let me know.

---

### Post by costing on 2009-07-24
Can you please try downloading again the archive, clean the previous installation including removing the startup scripts:
```

# rm /etc/init.d/asusg50leds.sh
# update-rc.d asusg50leds.sh remove
```
then unpack the new version and execute utils/install.sh?

---

### Post by LexMortis on 2009-07-25
Ive just installed Ubuntu so I guess I already had the latest, however, I removed and installed everything again. Still nothing automatically. :(

---

### Post by costing on 2009-07-25
I've uploaded a new version yesterday so please do download [http://asusg50oled.sourceforge.net/download/asusg50oled.tgz](http://asusg50oled.sourceforge.net/download/asusg50oled.tgz) again. To make sure you have the latest version please check if the CHANGELOG has the latest change from 2009-07-24.

Now, if you do have the latest and it still doesn't work even after the commands in the previous post... Does "/etc/init.d/asusg50leds.sh start" work? What is the output of "ls -l /etc/*.d/*asusg50leds*"? And of "head -n1 /etc/init.d/asusg50leds.sh"?

---

### Post by LexMortis on 2009-07-25
It works! Yay!

One thing though, the mousepad on my G2K laptop has a red led. Before, the led was switched off, which meant the touchpad was switched off. Which is good as I have a USB mouse plugged in. Before I got the OLED working the led was off, but now that the OLED is working the led+touchpad is on. I dont really care for the touchpad itself, but I'd like to have the bright (and for me useless) led off. Can you help with that?
Can I, and if so, how can I turn the led off?

Also, slightly related.
In the install guide, there is the command "rmmod usbhid".
Now, I'm a *nix noob. With a USB keyboard... see where I'm going?
You might wanna give people a heads up on that.

Perhaps make em c/p and execute this:
rmmod usbhid
modprobe asus_oled
modprobe usbhid

In a _single_ go?

You might not care for this.. but I bet *nix noobs with an Asus Laptop do. ;)
Do whatever you want with it.

Thanks for your assistance. You've been a great help!

---

### Post by costing on 2009-07-26
Good!

The led is used as a notification mechanism, for example if you set Thunderbird to call notify.sh as described in the documentation the message will be displayed on the screen and the led around the touchpad will blink a few times.

To control the initial state of the led you can:
echo 1 > "/sys/class/leds/asus::touchpad/brightness"
to turn it on, or
echo 0 > "/sys/class/leds/asus::touchpad/brightness"
to turn it off.

You will find the first command in /etc/init.d/asusg50leds.sh so you can either remove it or turn it off by default.

If you want to have notifications but only on screen and not using the led you can also edit application's config.properties and set this value to nothing:
flicker_on_new_message=

As for the usbhid, you are right, in your case it has to be done in one go. The commands are there just to test if everything is working, the script does this anyway for you at startup. However in your case the kernel was new enough so that it didn't require this trick :) I'll change the documentation a bit to make this part clearer, thanks!

---

### Post by LexMortis on 2009-07-26
Thanks again, it all works perfectly now!

---

### Post by sysghost on 2012-10-03
Just wanted to add in:
It looks like the asus_oled module has been abandoned. I tried to contact the developer about a few problems, but no response, and the modules hasn't been updated in years.
In ubuntu 12.04 the module loads fine, but whenever I try to show a picture it gives me an error.

```
cat tux.txt > /sys/class/asus_oled/oled_1/picture
```

Error message:
> cat: write error: Bad address
Current kernel version: 3.2.0-31

If I use an older kernel from the 2.6 branch (2.6.31), it works just fine.


I guess it's time to wave goodbye to this oled display.

---

