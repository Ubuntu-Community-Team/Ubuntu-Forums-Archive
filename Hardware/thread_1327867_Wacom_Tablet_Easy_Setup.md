---
title: "Wacom Tablet Easy Setup"
date: 2009-11-15
forum: Hardware
---

### Post by junalmeida on 2009-11-15
I've made a script to setup wacom-based tablet pc's like mine.
This script may work on laptops that have wacom usb based devices.

I've tested it on karmic 9.10. Please fell free to report bugs on other versions and distros.

Steps:
Download the attachment, extract and run.

Requirements: 
A debian based distro; zenity package.

**Karmic users, please do the following before:**
> 
wget [http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/hid-ids.h](http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/hid-ids.h)
sudo cp ./hid-ids.h /lib/modules/`uname -r`/build/drivers/hid/hid-ids.h


Known to work:
HP TX2000 running Ubuntu 9.10 64-bit.
HP TX2000 running Ubuntu 9.10 32-bit (thanks @correaa & @goldenroad08 )

Please try it and tell me if it works. Fell free to report bugs.
:D

---

### Post by correaa on 2009-11-29
thank you very much, it works almost perfectly in my hp tx2000, ubuntu 9.10, 2.6.31-15-generic. I had to copy 10-linuxwacom.fdi manually to /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi and reboot.

---

### Post by junalmeida on 2009-11-29
Do you know if the script shows any error about coping this file? 
This step is done at the end of the window "Installing driver".

---

### Post by goldenroad08 on 2009-11-30
worked for me just fine! 

tx2000 running 9.10 32 bit with the 14 kernel i think. had to manually install the fdi logged in  a root and reboot as well.

but in any case much thanks!

---

### Post by Dosundo on 2009-12-15
Thank You!!! :P:P:P
The script works fine.
tx2000/ubuntu 9.10 32 bit

---

### Post by Robbie Huffman on 2009-12-23
The driver build phase fails for me.

```
make[2]: Entering directory `/home/robbie/Downloads/linuxwacom-0.8.4-4/src/2.6.31'
cp -f ../2.6.27/wacom.h .
cp -f ../2.6.28/wacom_wac.h .
cp -f ../2.6.28/wacom_sys.c .
cp -f ../2.6.28/wacom_wac.c .
cp /lib/modules/2.6.31-16-generic/build/drivers/hid/hid-ids.h .
cp: cannot stat `/lib/modules/2.6.31-16-generic/build/drivers/hid/hid-ids.h': No such file or directory
make[2]: *** [all] Error 1
make[2]: Leaving directory `/home/robbie/Downloads/linuxwacom-0.8.4-4/src/2.6.31'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/robbie/Downloads/linuxwacom-0.8.4-4/src'
make: *** [all-recursive] Error 1
DONE

```There isn't much in that directory, but hid-ids.h is certainly not there:
```

[[COLOR=SeaGreen]robbie@Vermouth:/lib/modules/2.6.31-16-generic/build/drivers/hid[/COLOR]]
[0]=> ls -l
total 20
-rw-r--r-- 1 root root 9344 2009-09-09 18:13 Kconfig
-rw-r--r-- 1 root root 1555 2009-09-09 18:13 Makefile
drwxr-xr-x 2 root root 4096 2009-12-22 19:13 [COLOR=MediumTurquoise]usbhid[/COLOR]
```There must be some source dependency missing, but I have not figure it out yet.

---

### Post by Favux on 2009-12-24
Hi Robbie Huffman,

Welcome to Ubuntu forums!

Please see "3) For Karmic only" in Section 1 of this linuxwacom compile and install [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

Hope this is helpful.

---

### Post by junalmeida on 2009-12-24
Hi, Favux, you are right!

But since its a Karmic file, I can, but I don't know if I should include this file on the easy setup. 

I'm including this instruction on the main thread now.

Thanks for all feedback :D

---

### Post by Favux on 2009-12-24
Hi junalmeida,

You are welcome.  By the way nice work with the script.  :)

Yes, not an easy call on the hid-ids.h.  You can always add it later if you think it improves the script.

I think you'll be interested in gali98's python script at the [LWP's HOWTO]("http://linuxwacom.sourceforge.net/index.php/howto/install").  Great minds think alike.  :)

---

### Post by Gorlist on 2010-01-16
Good job! works in 9.10 64bit :)

---

### Post by originalsurfmex on 2010-01-22
is there a way to undo the changes this script made?

---

### Post by junalmeida on 2010-01-22
Hi, originalsurfmex
You can sudo make uninstall on the download folder and delete the file at /lib/modules/$KernelVersion/kernel/drivers/input/tablet/wacom.ko


But, why do you need to undo? 

Regards.

---

### Post by texaswriter on 2010-01-22
junalmedia> In regards to the Wacom tablets, I have a CTH-460. I understand there are specific instructions for patching the open source drivers to work for this [and supposedly even that works], the only problem is those instructions are for an older version of the drivers than what I have installed. 

My question is whether your script works for CTH-460 or just the older Bamboo tablets. Additionally, does your script take into consideration that the newer [not beta] version of open source wacom drivers. 

Thanks

---

### Post by junalmeida on 2010-01-23
Hi texaswriter,

This script was tested on Tablet PC's HP Laptops. 

The Wacom USB and Serial devices may work with this script, but i can't even test 'cause I don't have such devices. So, you can give a try and tell me if it works.

---

### Post by dhjohn on 2010-01-28
Hello. I am installing this script for my hp tx2000 tablet now.
I was wandering if the script configures the tablet to fit the screen, or if not, if there is an easy way to configure it.

Thank you,
dhjohn

---

### Post by Gorlist on 2010-01-31
Config program in the repo, "wacom-tools", and type "wacomcpl" into the terminal.

---

### Post by Fredrik Andersson on 2010-02-09
Thanks!

The script worked really smooth for me, and tablet is working really great now, including touch functionality.

The only thing that didn't work was the eraser tip. I know the script should support it (the eraser is defined in the .fdi file). Any ideas on why it doesn't work.

I installed the latest driver, my system is a HP TX2020 with Ubuntu 9.10.

/Fredrik Andersson

---

### Post by junalmeida on 2010-02-09
> **Fredrik Andersson said:**
> The only thing that didn't work was the eraser tip. 

Hi Fredrik,

Please, check if the fdi file was correctly copied to the destination.

/usr/share/hal/fdi/policy/20thirdparty/

---

### Post by nossifer on 2010-02-10
Thank you for doing the script.  Unfortunately, it doesnt work for me on KDE 4.3.5.  It runs perfect, and says that it should work.  Yes, I copied over the file, and followed the instructions.  I don't have gnome installed, but this is my problem:

driver = none when i run: more /proc/bus/usb/devices

and it does not appear when I run: xinput --list

and, wacomcpl does not show a device

So, maybe this is just a KDE thing, not sure.  Any help is appreciated.
Computer is a DELL XPS M1730



S:  Manufacturer=Wacom Co.,Ltd.                                  
S:  Product=CTH-460                                              
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr= 98mA                           
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=   9 Ivl=4ms                         
I:* If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=(none)
E:  Ad=82(I) Atr=03(Int.) MxPS=  64 Ivl=4ms


actually.... when I redid it, I looked back through the log even though it said "DONE", and what I found was this:  "***Note: Drivers not enabled as modules in your kernel config but requested through configure are NOT built"
... not sure if this matters or not.

---

### Post by Favux on 2010-02-10
Hi nossifer,

The reason it doesn't work is that support for the Bamboo Pen & Touch hasn't been added to linuxwacom yet.  The patches developed on this forum have been submitted to the LWP and hopefully support will be included in 0.8.5-10, which is due out in a few days (hopefully).

If you want to get it working now, you can apply the patches.  See [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384").  In the 'Note:' near the bottom it links you to the patch sets and HOW TO's.

---

### Post by nossifer on 2010-02-11
> **Favux said:**
> Hi nossifer,

The reason it doesn't work is that support for the Bamboo Pen & Touch hasn't been added to linuxwacom yet.  The patches developed on this forum have been submitted to the LWP and hopefully support will be included in 0.8.5-10, which is due out in a few days (hopefully).

If you want to get it working now, you can apply the patches.  See [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384").  In the 'Note:' near the bottom it links you to the patch sets and HOW TO's.

Wow.  you are all over this stuff eh?  Thank you so much.  I did look through that thread at some point, but the 40+ pages is a little tough on an amature.  I will try the patches and report back.  Thanks again.

---

### Post by nossifer on 2010-02-11
> **Favux said:**
> Hi nossifer,

The reason it doesn't work is that support for the Bamboo Pen & Touch hasn't been added to linuxwacom yet.  The patches developed on this forum have been submitted to the LWP and hopefully support will be included in 0.8.5-10, which is due out in a few days (hopefully).

If you want to get it working now, you can apply the patches.  See [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384").  In the 'Note:' near the bottom it links you to the patch sets and HOW TO's.

I cant believe it.  It works.

I walked throug the steps on my netbook and tested it maybe twice during the steps.  It wasnt working.  I figured to reboot, and while it was shutting down, I grabbed the pen just for kicks and tested.... it worked.  I went over to my normal computer, redid the steps (2 minutes) and bang.  Works.

I am not sure what does and doesnt on a complete level as I have never used one before ;)    All I know is that I am trying to fight off Carpal and this is hopefully a way.  

THANK YOU SO MUCH.

KDE 4.4 came out last nite (updated) and working under that with QT 4,6
Kubuntu Karmic 9.10
wacom bamboo touch pen

---

### Post by Apetrunk on 2010-02-11
Hey there.

I extracted that file and try to run it, but I get an error window that says it can't find the 10-linuxwacom.fdi file. In your script, where does it look for it at?

EDIT: I forgot I could look at that and I see where you mapped it to. That file is indeed there, but it doesn't work. Also, I tried to map it to the extracted 10-linuxwacom.fdi and that didn't work either.

---

### Post by kchings on 2010-02-12
This works for me! thanks!
oh, but the eraser doesn't seem to work... is there some parameter that I have to set to get it to work?
I have a Gateway E-155.

---

### Post by nossifer on 2010-02-12
The pen works great.  'Touch' works in that I can use my finger instead of the pen.  Gestures are not working, and I am a moron who doesn't really understand how the calibration feature works for Touch in wacomcpl.  I get a box in the top left which turns black after doing a gesture in it, but the box on the bottom right doesnt do anything for me, thus I assume, I cannot complete the calibration?  Not sure if this affects gestures or not.  (CTH-661)

---

### Post by nossifer on 2010-02-12
> **kchings said:**
> This works for me! thanks!
oh, but the eraser doesn't seem to work... is there some parameter that I have to set to get it to work?
I have a Gateway E-155.

I don't have an eraser either for what its worth.

---

### Post by nossifer on 2010-02-12
> **Apetrunk said:**
> Hey there.

I extracted that file and try to run it, but I get an error window that says it can't find the 10-linuxwacom.fdi file. In your script, where does it look for it at?

EDIT: I forgot I could look at that and I see where you mapped it to. That file is indeed there, but it doesn't work. Also, I tried to map it to the extracted 10-linuxwacom.fdi and that didn't work either.

Did you download and extract the zip?  It should be in there if memory serves, And then you copy it to here:  /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi 
You will need to be root to do that.

---

### Post by Favux on 2010-02-12
Hi nossifer and kchings,

Eraser doesn't work everywhere, the program has to support it.  To configure extended input devices in Gimp and Inkscape see near the bottom of the [Wacom wiki]("https://help.ubuntu.com/community/Wacom").


Hi nossifer,

They really hadn't added any changes to wacomcpl to support the P & T.  I pointed that out to them and ob1kenobi added some.  Ping just committed the P & T #357 patchset to the linuxwacom CVS within the last hour.  So hopefully 0.8.5-10 will be out today.  And hopefully it will support the P & T and have those wacomcpl changes.

---

### Post by Favux on 2010-02-12
Hi nossifer,

Linuxwacom 0.8.5-10 was just released:  [https://sourceforge.net/projects/linuxwacom/files/](https://sourceforge.net/projects/linuxwacom/files/)  It has the new P & T patch set and hopefully you'll now be able to get support without patching!  And with luck wacomcpl will have more P & T support.

---

### Post by nossifer on 2010-02-12
> **Favux said:**
> Hi nossifer,

Linuxwacom 0.8.5-10 was just released:  [https://sourceforge.net/projects/linuxwacom/files/](https://sourceforge.net/projects/linuxwacom/files/)  It has the new P & T patch set and hopefully you'll now be able to get support without patching!  And with luck wacomcpl will have more P & T support.

haha,  I went to install on the netbook and saw that the old link to wget was 404.  That led me to find that your 5-10 was up.  Congrats.  I am sure it was a lot of hard work to get it there.

It installed on the netbook and seemed to recognize itself differently in wacomcpl.  My CTH661 is displayed in wacomcpl as a Wacom_BambooFun_2FG_6x8 (single config option).  This differs from before where it was recognised as a Pen device and a Touch device, both were independently configurable.  

Pen is working and configurable, but touch is not recognised or configurable.  

Which .fdi file should be used?  Is that a contributor to this?

---

### Post by Favux on 2010-02-12
Hi nossifer,

Well it sounds like there are some changes to wacomcpl, which we were expecting.

Yes it could be the .fdi.  Which one do you have currently, if you know?

---

### Post by nossifer on 2010-02-12
> **Favux said:**
> Hi nossifer,

Well it sounds like there are some changes to wacomcpl, which we were expecting.

Yes it could be the .fdi.  Which one do you have currently, if you know?

The change was noticed using simply a recompile/reboot.  I just tried with the RC2 .fdi and it created two entries for "stylus", neither was touch.  I recompliled and again have my "Fun" entry in wacomcpl as in the last post.  I am not aware of how any .fdi is included in 5-10, but I guess whatever is default in there...

---

### Post by Favux on 2010-02-12
Hi nossifer,

With the new-generic rc2 was anything working?  Like stylus?  What does wacomcpl call your tablet with it?  We need to see what the .fdi that gives you Wacom_BambooFun_2FG_6x8 (single config option) in wacomcpl looks like.

Anyway there should be just one 10-linuxwacom.fdi on your system located at /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi.  In the 0.8.5-10 tar the .fdi is located in /src/util.  Is it the one that gives you the new wacomcpl entry?

Doesn't sound like you need to keep recompiling.

PS:  Just want to point out you should probably now be posting on the P & T thread:  [http://ubuntuforums.org/showthread.php?t=1321238](http://ubuntuforums.org/showthread.php?t=1321238)

---

### Post by nossifer on 2010-02-12
> **Favux said:**
> Hi nossifer,

With the new-generic rc2 was anything working?  Like stylus?  What does wacomcpl call your tablet with it?  We need to see what the .fdi that gives you Wacom_BambooFun_2FG_6x8 (single config option) in wacomcpl looks like.

Anyway there should be just one 10-linuxwacom.fdi on your system located at /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi.  In the 0.8.5-10 tar the .fdi is located in /src/util.  Is it the one that gives you the new wacomcpl entry?

Doesn't sound like you need to keep recompiling.

PS:  Just want to point out you should probably now be posting on the P & T thread:  [http://ubuntuforums.org/showthread.php?t=1321238](http://ubuntuforums.org/showthread.php?t=1321238)

Hi.
With the generic RC2, yes, the stylus was working (no touch) and there were two entries listed simply as "stylus"

I went into /src/util and made copied it over to the proper directory just to make sure that it was the one currently being used, and it is.  wacomcpl registers my devide as the 6x8.

I will end my contribution (or subtraction) ;) from this thread now and use the one you listed.  Thanks again for all your help.

EDIT:  I followed the updated instructions (5-10) from that thread and there are more entries in the wacomcpl now.  There is still no touch, but I think that thread is aware of that, and will better suit us P&T guys.  Thanks once again!!

---

### Post by dedhandi on 2010-05-02
Hmm, maybe I shouldn't be giving this a go on 10.04 but installation fails for me:

```
alex@ubuntu:~/Documents/wacom$ sudo '/home/alex/Documents/wacom/setup-wacom.sh' 
You're running this from the terminal. I like you.
--2010-05-02 20:59:05--  http://sourceforge.net/api/file/index/project-id/69596/rss
Resolving sourceforge.net... 216.34.181.60
Connecting to sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/rss+xml]
Saving to: `/var/tmp/driver-wacom.rss'

    [      <=>                                                     ] 122,899     84.7K/s   in 1.4s    

2010-05-02 20:59:08 (84.7 KB/s) - `/var/tmp/driver-wacom.rss' saved [122899]

Selected: 0.8.6-1
E: Package wacom-tools has no installation candidate
/home/alex/Documents/wacom/setup-wacom.sh: line 191: cd: linuxwacom-0.8.4-4: No such file or directory
```

And then I get a dialog saying "Something went wrong. Remove downloaded files and try again."

I'd really like it to work though!!

---

### Post by junalmeida on 2010-05-02
> **dedhandi said:**
> Hmm, maybe I shouldn't be giving this a go on 10.04 but installation fails for me:
Hi, my script was not updated to work on Lucid yet.

But, for my machine, lucid detected the wacom out-of-the-box. So, i guess that my script is not necessary anymore.

---

### Post by dedhandi on 2010-05-03
I'm using a basic Wacom Bamboo Pen but it doesn't seem to have been recognised sadly...

---

### Post by junalmeida on 2010-05-03
> **dedhandi said:**
> I'm using a basic Wacom Bamboo Pen but it doesn't seem to have been recognised sadly...

Try to compile from source of linuxwacom project. 

This script was made for HP Tablet PC's.

---

### Post by dedhandi on 2010-05-03
Thanks for the tip, I reckon it's more hassle than it's worth though (in my humble opinion).

---

