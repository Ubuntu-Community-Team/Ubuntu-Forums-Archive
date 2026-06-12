---
title: "Acer Aspire One AOA110-AGw fan control - acerhdf stopped working"
date: 2010-03-07
forum: Hardware
---

### Post by Oropher8598 on 2010-03-07
I've been using the acerhdf fan control utility on my AOA110-AGw. Short story is that acerhdf stopped working when I the update manager switched from kernel 2.6.31-19 to 2.6.3-20. None of the 'solutions' I've found searching here or the web in general have helped.

Some background:
[LIST]
[*]Acerhdf didn't work on the inital install (kernel 2.6.31-17). I tried the instructions [here](http://blog.brightbox.co.uk/posts/ubuntu-netbook-remix-on-an-acer-aspire-one-a110) and in the [acerhdf readme](http://piie.net/files/acerhdf_README.txt) without success.
[*]The fan control magically worked after the update to kernel 2.6.31-19. (At least, it obeyed the fanon/fanoff settings I had for acerhdf.)
[*]After the update to 2.6.31-20, the fan control immediately reverted to its' original behaviour.
[*]Having hunted around, I've found the same advice in several places: edit /etc/modprobe.d/acerhdf.conf and add the line "options acerhdf kernelmode=1", then reboot. No success with this, with or without fanon/fanoff settings included.
[*]An alternative suggestion was to try the above settings in /etc/modprobe.conf; again, no success.
[*]Also found this: To enable for the running session: "sudo echo -n "enabled" > /sys/class/thermal/thermal_zone0/mode". That returns a 'permission denied' message. I've also tried adding this command to /etc/rc.local manually; again, no good.
[/LIST]

I'm out of ideas at this point. The fan's still going, even though "dmesg|grep acerhdf" reports temp as low as 34C... :(

---

### Post by jaycott on 2010-03-08
I can confirm that this is an issue for the Acer Aspire One AOA150 as well.  All the suggested fixes I've found online have failed.  dmesg|grep acerhdf reports that it's there. I've rolled back to using 2.6.31-19 in the meantime.

Could this be a bios version issue?  I've read that acerhdf needed to be patched for bios v.3310, which is what I'm running.  Not sure what happened between kernels -19 and -20.

---

### Post by Oropher8598 on 2010-03-08
> **jaycott said:**
> I can confirm that this is an issue for the Acer Aspire One AOA150 as well.  All the suggested fixes I've found online have failed.  dmesg|grep acerhdf reports that it's there. I've rolled back to using 2.6.31-19 in the meantime.Yeah, 2.6.31-19 seems to work still for me too. 

> Could this be a bios version issue? I've read that acerhdf needed to be patched for bios v.3310, which is what I'm running.  Not sure what happened between kernels -19 and -20.I don't know about a bios issue - I'm running v3309 here.

Which version of acerhdf are you using? I'm still on v0.5.22 as I haven't had time to compile v0.5.23 yet. Can't find a changelog, unfortunately, so I've no idea if that will help. Will post back when I've had a chance to try it, anyway.

---

### Post by bailout on 2010-03-08
I have just run into this problem since upgrading to 2.6.31-20. I used to use the acerhdf.conf line

```
options acerhdf interval=5 fanon=60 fanoff=55 kernelmode=1
```

Following a post on the aspire one forum I changed it to

```
options acerhdf interval=5 fanon=60000 fanoff=55000 kernelmode=1
```

This seems to work as before.

btw I think without fan control the bios turns on the fan at about 30C

---

### Post by Oropher8598 on 2010-03-08
I've updated to acerhdf v0.5.23 and tried it with the temps formatted as '65000' or just '65'. Still not working in kernel 2.6.31-20.

Kernel 2.6.31-19 still works whichever way the temps are formatted...

The way temps are reported seems to be one difference between the kernel versions: doing "cat /sys/class/thermal/thermal_zone0/temp" or "dmesg|grep acerhdf" returns the temp as eg '65' in -19, but as '65000' in -20.

One strange thing is that acerhdf seems to believe it's still controlling the fan in 2.6.31-20. If I set kernelmode=0, "dmesg|grep acerhdf" shows a message saying fan control is off and suggesting I enable it by "echo -n "enabled" > /sys/class/thermal/thermal_zone0/mode". With kernelmode=1, however, this message is absent, so presumably acerhdf *thinks* it's controlling the fan even though it isn't.

Colour me confused.

**bailout**, do you have a link for the thread that helped you?

---

### Post by bailout on 2010-03-09
Thde thread is here but it doesn't give any more info

[http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=20095](http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=20095)

From what I understand acerhdf is now a module built into the kernel. All you have to do is add the acerhdf.conf file to enable it. You don't need to compile it from source and add it yourself as in the link you posted. Mine works with the default and just needed the 000 added to the temps in the config file. I would check that you haven't made an error in the config file or its name and if that doesn't work try to undo the update you tried.

---

### Post by Oropher8598 on 2010-03-09
In the end the solution was really simple. At some point (probably back when I was trying to get acerhdf to work under 2.6.31-17, because I really don't remember doing it), I'd put a line in /etc/modules that called acerhdf and specified the fanon/fanoff settings... and this was overriding anything I put in /etc/modprobe.d/acerhdf.conf! Commented out that line and everything seems to work now. :)

Thanks, **bailout** - if you hadn't pointed out that acerhdf is now baked into the kernel I'd never have gone looking to see how to remove the module I'd installed manually!

---

### Post by Jose Catre-Vandis on 2010-03-12
Thanks for this tip, very handy and all quiet on the western front now :)

---

### Post by grahamst on 2010-03-16
Thanks to all concerned for this thread - well-specified problem, knowledgeable and useful answers. Adding the 000s to the fanon/fanoff settings worked a treat for me.

The only question left is why the settings were changed at all. Is there any need to be more specific than one degree? Never mind. As long as it works.

Graham

---

### Post by Jarige on 2010-04-13
Thank you guys, you've solved my problem either. I use Lucid, and some kernel update turned off acerhdf. Now it's on again.

I noticed that acerhdf is no longer a package, which is a shame. There should be a package that will create the default acerhdf.conf file. Shouldn't be much work, right?

---

### Post by NetTechGuy on 2010-05-10
Well I have an Acer aspire one ZG5 AAO150 running 2.6.31-21 kernel,
Had some issues getting the acerhdf module working properly and making this a permanent fix, but I eventually got it working after editing 
/etc/modprobe.d/acerhdf.conf 
and adding the specific options controlling the thermal events. 
The values need to be added into the conf file as following:
 
options acerhdf interval=5 fanon=60000 fanoff=55000 kernelmode=1

this worked quite well for me, no more noisy fan.

Thanks for all the help everyone!

---

### Post by sisyphus1978 on 2010-05-11
Thanks. That helped no end. :)

---

### Post by kesman on 2010-06-12
So acerhdf should be in the newest kernel?
How do I enable it, I tried creating the file
```
/etc/modprobe.d/acerhdf.conf
```
with parameters
```
options acerhdf interval=5 fanon=60000 fanoff=55000 kernelmode=1
```
but when trying
```
sudo modprobe acerhdf
```
all I got was
```
FATAL: Error inserting acerhdf (/lib/modules/2.6.32-22-generic/kernel/drivers/platform/x86/acerhdf.ko): No such device
```
what to do? I have bios version 1.3310, should I manually compile the module to enable support for this bios version?

---

### Post by MountainX on 2010-06-24
I'm running Lucid on the Acer Aspire One 532h (Gateway LT2115u). [s]The fan runs all the time. (It never turns off). [/s] Any suggestions?

UPDATE: I found out that the fan is actually turning on and off. It turns on at 40 degrees C, which is way too low. That's why I thought is ran all the time. So now that I know it turns on and off, I just need to reset the levels.

Actually, Lucid is running amazingly well on this netbook!

--------------------------

Here's some stuff I found. It has not solved the problem for me.

See [http://ubuntuforums.org/showthread.php?p=9507369](http://ubuntuforums.org/showthread.php?p=9507369)

Acer Aspire One AOA110-AGw fan control - acerhdf stopped working

The thread is here but it doesn't give any more info

[http://www.aspireoneuser.com/forum/v...p?f=28&t=20095](http://www.aspireoneuser.com/forum/v...p?f=28&t=20095)

From what I understand acerhdf is now a module built into the kernel. All you have to do is add the acerhdf.conf file to enable it. You don't need to compile it from source and add it yourself as in the link you posted. Mine works with the default and just needed the 000 added to the temps in the config file. I would check that you haven't made an error in the config file or its name and if that doesn't work try to undo the update you tried.

----------

In the end the solution was really simple. At some point (probably back when I was trying to get acerhdf to work under 2.6.31-17, because I really don't remember doing it), I'd put a line in /etc/modules that called acerhdf and specified the fanon/fanoff settings... and this was overriding anything I put in /etc/modprobe.d/acerhdf.conf! Commented out that line and everything seems to work now. 

Thanks, bailout - if you hadn't pointed out that acerhdf is now baked into the kernel I'd never have gone looking to see how to remove the module I'd installed manually!

-----------------

[http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=20095](http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=20095)

[http://swiss.ubuntuforums.org/showthread.php?p=9276907](http://swiss.ubuntuforums.org/showthread.php?p=9276907)

[http://www.piie.net/index.php?section=acerhdf](http://www.piie.net/index.php?section=acerhdf)

---

### Post by marcisim on 2010-10-07
> **kesman said:**
> So acerhdf should be in the newest kernel?
How do I enable it, I tried creating the file
```
/etc/modprobe.d/acerhdf.conf
```with parameters
```
options acerhdf interval=5 fanon=60000 fanoff=55000 kernelmode=1
```but when trying
```
sudo modprobe acerhdf
```all I got was
```
FATAL: Error inserting acerhdf (/lib/modules/2.6.32-22-generic/kernel/drivers/platform/x86/acerhdf.ko): No such device
```what to do? I have bios version 1.3310, should I manually compile the module to enable support for this bios version?


I've got the same kernel and the same problem on Acer Aspire 5738zg

---

### Post by ianmillington on 2010-10-11
I would be interested to know the status of this in 10.10.

I installed the rc on an aspire one 110L (16gb SSD version with /home on the SDHC card in the left hand slot). )on friday night. I was a bit disappointed to see that I still needed to edit grub to enable detection of the SD card in the right SD slot. On that basis I have assumed that if it is suspended or hibernated the filesystem on the SD card will continue to be corrupted. Is anyone able to say whether this is fixed please?

However, I'm really confused by the Fan. After install the fan would bang away at full speed all the time. However, since an update it now seems to operate at low speed (at a whisper) at least on boot-up. It hasn't been run for any length of time. Does anyone know the current status of this and what if anything I need to do to have the fan switch on and off according to temperature please?

Thanks in advance

---

### Post by ianmillington on 2010-10-22
Bump

Anyone able to help on this?

Clean install of 10.10 on an AAO110 and the fan is banging away all the time. A search for acerhdf reveals nothing.

I assume I've got to set this up from scratch and would appreciate guidance as the official help seems to stop at 9.04. 

Thanks

---

### Post by kamereon on 2010-11-02
Just create a file **/etc/modprobe.d/acerhdf.conf**
containing: *options acerhdf interval=5 fanon=68000 fanoff=55000 kernelmode=1*
then open a terminal and type *sudo modprobe acerhdf*
Works like a charm with kernel 2.6.35-22 Ubuntu 10.10

---

### Post by ianmillington on 2010-11-02
Thanks very much, will try later

Edit:

Thanks it works! I did in fact do that when I installed lucid on the machine and had forgotten. Specifically I was looking for the file and had forgotten I had to create it first. Grateful for the help.

---

### Post by marcisim on 2010-11-22
> **kamereon said:**
> Just create a file **/etc/modprobe.d/acerhdf.conf**
containing: *options acerhdf interval=5 fanon=68000 fanoff=55000 kernelmode=1*
then open a terminal and type *sudo modprobe acerhdf*
Works like a charm with kernel 2.6.35-22 Ubuntu 10.10

thanks but it doesn't work, it still gives:

[COLOR=Red]/etc/modprobe.d
22:19:39 marcisim@tnagia$sudo modprobe acerhdf
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
FATAL: Error inserting acerhdf (/lib/modules/2.6.32-25-generic/kernel/drivers/platform/x86/acerhdf.ko): No such device[/COLOR]

---

### Post by qazatqazah on 2010-12-21
At first I had some trouble installing acerhdf in Maverick (Ubuntu 10.10), but **I got it working**.
The problem turned out to be that my laptop (an Acer Aspire 7730G) was simply not in the list of recognized pc's, but it was easy to add it to the list. 
This solution will probably work for any Acer, Gateway or Packard Bell suffering from erratic fan behavior.
Of course tampering with the code (which is what I did) is at your own risk.
[INDENT]**Please note** that if you use Ubuntu's automatic update system, and you have manually installed kernel modules (like this one), **every time that Ubuntu installs a new kernel, you will have to reinstall all manually installed kernel modules as well**. (In my case, that also includes a NVidia video driver.) 
If you leave the sources where they are after installing, it will suffice to perform steps 7, 9 and 10. (Please take care to use the right parameters when inserting the module.)[/INDENT]

Here's the **[SIZE="3"]recipe[/SIZE] to install acerhdf**:

_Step 1_
Open a terminal. You normally automatically start in your home directory, i.e.  [FONT="Courier New"]/home/yourname/[/FONT]

_Step 2_ 
Determine which linux kernel version you are using:
```
uname -r
```
In my case, that was [FONT="Courier New"]2.6.35-23-generic[/FONT]

_Step 3_
Get everything you need to build a kernel module:
```
sudo apt-get install build-essentials linux-kernel-headers
```

_Step 4_
In a web browser, download the appropriate sources of acerhdf from [FONT="Courier New"][http://www.piie.net/index.php?section=acerhdf](http://www.piie.net/index.php?section=acerhdf)[/FONT]
For my kernel, which is linux-2.6.30+, that is [FONT="Courier New"][http://www.piie.net/files/acerhdf_kmod-0.5.25.tar.gz](http://www.piie.net/files/acerhdf_kmod-0.5.25.tar.gz)[/FONT]
Move the downloaded file to your home directory if it is not already there.
You can either use a filemanager to do that, or you can do it in the terminal.
E.g.: if your download is on your desktop, you could type:
```
mv /home/yourname/Desktop/acerhdf_kmod-0.5.25.tar.gz /home/yourname/
```

_Step 5_
In the terminal create an automatic startup settings file with conservative (low) temperature settings:
```
sudo echo options acerhdf interval=10 fanon=60000 fanoff=55000 kernelmode=1 > /etc/modprobe.d/acerhdf.conf
```

_Step 6_
Unpack the tarball:
```
gunzip -c acerhdf_kmod-0.5.25.tar.gz | tar -xvf -
```
This creates a directory [FONT="Courier New"]/home/yourname/acerhdf_kmod[/FONT]

_Step 7_
Change to the newly created directory:
```
cd acerhdf_kmod
```

_Step 8_
**RTFM!** 
```
gedit README.txt &
```

_Step 9_
Build the kernel module:
```
make && sudo make install
```

_Step 10_
Try and insert the module into the kernel:
```
sudo modprobe acerhdf interval=10 fanon=60000 fanoff=55000 kernelmode=1
```

_Step 11_
Check for error messages:
```
dmesg|grep acerhdf
```
In my case, it read:
[FONT="Courier New"][COLOR="Red"][  477.322743] acerhdf: Acer Aspire One Fan driver, v.0.5.25
[  477.322779] acerhdf: unknown (unsupported) BIOS version [/COLOR]Acer[COLOR="Red"], inc./[/COLOR]Aspire 7730G[COLOR="Red"]     /[/COLOR]v0.3636[COLOR="Red"], please report, aborting![/COLOR][/FONT]
[LIST]
[*]If you get a similar error message, and you're convinced your laptop is compatible with acerhdf, you're lucky, because these instructions should work for you. :)
[*]If you only get the first line, you're even luckier, because the module seems to have loaded correctly, and you can skip the next steps, and go straight to _step 15_. :D
[*]If you got another error message, something else is wrong. :(
[/LIST]

_Step 12_
Open the C source of the module:
```
gedit acerhdf.c
```
Scroll down to the line that says [FONT="Courier New"]/* Register addresses and values for different BIOS versions */[/FONT]
Below that, you will find a table of laptops and BIOSes that are known to work with acerhdf.
Copy the line that best resembles your machine, and adapt it with the data from the error message in step 11.
In my case, I copied the line:
[FONT="Courier New"]{"Acer", "Aspire 1810T",  "v1.3314", 0x55, 0x58, {0x9e, 0x00} },[/FONT]
And I changed it to:
[FONT="Courier New"]{"[COLOR="Red"]Acer[/COLOR]", "[COLOR="Red"]Aspire 7730G[/COLOR]",  "[COLOR="Red"]v0.3636[/COLOR]", 0x55, 0x58, {0x9e, 0x00} },[/FONT]

_Step 13_
Scroll all the way down to the end of the program. Again, copy the line that best resembles your machine, and adapt it.
In my case, I copied the line:
[FONT="Courier New"]MODULE_ALIAS("dmi:*:*Acer*:pnAspire 1825PTZ:");[/FONT]
And I changed it to:
[FONT="Courier New"]MODULE_ALIAS("dmi:*:*[COLOR="Red"]Acer[/COLOR]*:pn[COLOR="Red"]Aspire 7730G[/COLOR]:");[/FONT]

_Step 14_
Save the file (Ctrl-S) and close the editor (Alt-F4). Now go back to _step 9_.

_Step 15_
Determine if the fan is properly enabled:
```
cat /sys/class/thermal/thermal_zone0/mode
```
If you get the answer [FONT="Courier New"]enabled[/FONT], then go on to _step 16_
If you get another answer, enable the fan:
```
sudo echo enabled > /sys/class/thermal/thermal_zone0/mode
```

_Step 16_
**Your fan should behave normally by now.**
You can easily check the current temperature by typing:
```
cat /sys/class/thermal/thermal_zone0/temp
```

_Step 17_
Instruct the system to load the module automatically on system start. To do that, edit the modules file:
```
sudo gedit /etc/modules
```
And add a new line with the word [FONT="Courier New"]acerhdf[/FONT]
Save the file and close the editor.

_Step 18_
Reboot to check if autoload really works. Use the check in step 11.

_Step 19_
If all works well, it is time to find the maximum operating temperature for your cpu (on the internet), and change the temperature values (fanon, fanoff) in [FONT="Courier New"]/etc/modprobe.d/acerhdf.conf[/FONT] accordingly.
```
sudo gedit /etc/modprobe.d/acerhdf.conf
```
In my case (an Intel Centrino Core2 Duo T6600), the values fanon=67000 fanoff=62000 work well. 
You can find your machine's exact cpu type in the BIOS.

_Step 20_
20. If for any reason you should want to unload the kernel module, you can do so by typing:
```
sudo modprobe -r acerhdf
```

**Ready!** :D

---

### Post by marcisim on 2010-12-24
i'm trying to follow your instructions. How can I get the register addresse and values for my machine?

thanks!

---

### Post by qazatqazah on 2010-12-25
> **marcisim said:**
> i'm trying to follow your instructions. How can I get the register addresse and values for my machine?

thanks!

There's some intelligent guessing and a little bit of luck involved here. I didn't know the correct the values for my machine either, but here is what I did.

The first three values in the table are obviously used by the program to identify your machine and BIOS version, and for those you can use the values in the error message of step 11. The last four values are more tricky.

Closely examining the table, I noticed that all newer Acer Aspire models/BIOSes use the same values. So, it was easy for me to use those same values as well. This is exactly the reason why I wrote "Copy the line that best resembles your machine".

Please note that the very last step describes how to unload the module. This gives you the possibility to use trial and error to determine the correct values for your machine. 
Also, if you install your new module using the trial-and-error method, take care to closely monitor the temperature of your machine. If you see that the temperature rises above the temperature value that you specified when loading the module, and the fan should not turn on, immediately unload the module to prevent damage to your cpu! In that case, the addresses in the table are obviously not correct, and you could try other values.

Sadly, I do not know of any general way to determine the correct values for your machine. :( What machine/BIOS are you using? (I might be able to help you with the guess...)

Good luck!

---

### Post by marcisim on 2010-12-26
> **qazatqazah said:**
> There's some intelligent guessing and a little bit of luck involved here. I didn't know the correct the values for my machine either, but here is what I did.

The first three values in the table are obviously used by the program to identify your machine and BIOS version, and for those you can use the values in the error message of step 11. The last four values are more tricky.

Closely examining the table, I noticed that all newer Acer Aspire models/BIOSes use the same values. So, it was easy for me to use those same values as well. This is exactly the reason why I wrote "Copy the line that best resembles your machine".

Please note that the very last step describes how to unload the module. This gives you the possibility to use trial and error to determine the correct values for your machine. 
Also, if you install your new module using the trial-and-error method, take care to closely monitor the temperature of your machine. If you see that the temperature rises above the temperature value that you specified when loading the module, and the fan should not turn on, immediately unload the module to prevent damage to your cpu! In that case, the addresses in the table are obviously not correct, and you could try other values.

Sadly, I do not know of any general way to determine the correct values for your machine. :( What machine/BIOS are you using? (I might be able to help you with the guess...)

Good luck!

thank you very much for you answer!

I'm using an ACER ASPIRE  5738ZG and the problem is that, whan I use either UBUNTU or SLACKWARE, fans are always on, except few minutes after the startup. Instead, when I work on winzoz everything is ok.

i'll try to execute your instruction, even if the only conseguence of my problem is that it becomes hard working on battery.

thanks

---

### Post by qazatqazah on 2010-12-26
> **marcisim said:**
> thank you very much for you answer!

I'm using an ACER ASPIRE  5738ZG and the problem is that, whan I use either UBUNTU or SLACKWARE, fans are always on, except few minutes after the startup. Instead, when I work on winzoz everything is ok.

i'll try to execute your instruction, even if the only conseguence of my problem is that it becomes hard working on battery.

thanks

I would exspect your machine to use the same values, i.e.
0x55, 0x58, {0x9e, 0x00} },

---

