---
title: "Keymapping"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by napsilan on 2007-06-20
I have a gyration MCE remote.  Out of the box, the arrows, numbers, mouse, and enter/esc buttons worked.  In xev, the basic multimedia functions were recognized (play, pause, volume, skip, previous, stop), and even the volume keys worked in kde. _ However, there are other keys on the remote that don't even generate anything in xev when I hit them_.  Some of these are the input key, channel up/down keys, and menu key.  Is there a way to map these keys if xev doesn't catch them?  I assume right now the remote is just using the build-in USB keyboard and mouse drivers (usb_hid).  Do I need to set up LIRC, even though the remote is RF and not IR?

---

### Post by napsilan on 2007-06-21
starting to answer my own question.  [http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys](http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys) says that I need to check dmesg and edit /etc/conf.d/local.start
[quote=gentoo wiki]
If pressing a key doesn't do anything at all (ie, xev produeces no output), run the following command in an X terminal:

 dmesg

You will probably see some lines like these:


[indent]Output of dmesg[/indent]
```

atkbd.c: Unknown key released (translated set 2, code 0x96 on isa0060/serio0).
atkbd.c: Use 'setkeycodes e016 <keycode>' to make it known.

```


This means that the kernel doesn't have keycodes mapped to your keyboard's scancodes.  You will have to add one line in /etc/conf.d/local.start for each missing key as follows:


[indent]/etc/conf.d/local.start[/indent]
```

setkeycodes e008 136
setkeycodes e016 150
... And so on ...

``` [noparse]
Where the first number (e008) is what you see in dmesg, and the second number (136) is an unused keycode in your kernel.  In general you can find a good keycode by taking the last 2 digits of this first number, converting it from hex (base-16) to decimal (base-10) and adding 128.[/noparse]
[/quote]

/etc/conf.d/local.start isn't used in ubuntu, I think it's /etc/rc.local instead

---

### Post by napsilan on 2007-06-21
looks like evrouter does the trick for most keys

[http://www.bedroomlan.org/~alexios/coding_evrouter.html](http://www.bedroomlan.org/~alexios/coding_evrouter.html)

I attached the evrouter dump codes for the remote.  I still can't get any output from the "TV home", "setup menu", "Last" and "Input" keys.

---

### Post by napsilan on 2007-06-22
it looks like evrouter doesn't work with openbox for some reason. 

```

xlib: connection to ":0.0" refused by server
xlib: no protocol specified

evrouter: could not open display ":0.0"

```

Anyone know how to get xlibs or whatnot working with openbox?

---

### Post by napsilan on 2007-06-22
needed to run

xhost +local:root

to fix that issue.  Still not getting it to correctly autostart though.  My /home/mythtv/.config/openbox/autostart.sh looks like

xhost +local:root &
sudo evrouter --config=...... /dev/input/......

I have the mythtv user set to sudo both autostart.sh and evrouter w/o a password.

---

### Post by napsilan on 2007-06-22
Got it working, although this is probably NOT the "proper" way to do it.  

I left /home/mythtv/.config/openbox/autostart.sh as it was
```

xhost +local:root
killall evrouter
sudo rm /tmp/.evrouter*   #removes a previous lock file
sudo evrouter --config=/home/mythtv/Evrouter_gyration.txt /dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-mouse /dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd &

```

Then I set it so that the mythtv user could sudo both evrouter and rm without a password. This was done with visudo.   Having a password-less rm is the thing that made me save this idea for last.  *If anyone has a better way to allow the mythtv user to delete the evrouter lock file, please say so.  *  
```

mythtv ALL=NOPASSWD: /usr/bin/evrouter
mythtv ALL=NOPASSWD: /bin/rm

```

Finally I added the autostart file to the end of the /usr/share/mythtv/startmythtv.sh file, right before "exec mythfrontend."  This is the script called by the mythtv-xsession.desktop file.  For some reason, the autostart script wasn't being run normally, so this was needed.  
```

sh /home/mythtv/.config/openbox/autostart.sh &
#start mythtv frontend software
exec mythfrontend

```

This finally automatically starts up evrouter correctly on login and lets it map the remote keys (except those 4 that it didn't recognize).  

I attached the evrouter deb and my current config file if anyone wants them.

---

### Post by napsilan on 2007-10-07
everytime mythtv updates, I have to re-edit the startmythtv file again.

---

### Post by modulok on 2007-10-09
wow, a whole thread talking to yourself...good stuff though!

I found the remote/keyboard combo on buy.com for cheap ($65) and was thinking about getting both. Right now I use the Logitech Dinovo Edge and trying to get the ATI Remote Wonder to work (without much success in mythtv).

Wondering how the remote works with mythtv (0.20.2)...and do you have the universal one? does it connect nicely to other components?

---

### Post by napsilan on 2007-10-09
> wow, a whole thread talking to yourself...good stuff though
Yah basically.  Started out as a request for help but I figured that others might find the info useful

I think my remote is slightly unique in that it registers as a keyboard and mouse, not as an actual remote.  Have you tried looking at the LIRC info?  That is the program/module that takes care of IR remotes, which I believe the ATI remote is.  

Can you get any input from your remote at all?  For example, if you are in a terminal and hit the numbers on your remote, will it enter those numbers into the terminal?  Or does it not work at all?  Mine was able to do that right when I plugged it in, so I just had to keymap the wierd keys, not get the whole thing working.  

LIRC page 
[http://mythtv.org/wiki/index.php/LIRC](http://mythtv.org/wiki/index.php/LIRC)

ATI remote wonder pages, depending on which model you have
[http://mythtv.org/wiki/index.php/ATI_Remote_Wonder](http://mythtv.org/wiki/index.php/ATI_Remote_Wonder)
[http://mythtv.org/wiki/index.php/ATI_Remote_Wonder_II](http://mythtv.org/wiki/index.php/ATI_Remote_Wonder_II)
[http://mythtv.org/wiki/index.php/ATI_Remote_Wonder_Plus](http://mythtv.org/wiki/index.php/ATI_Remote_Wonder_Plus)

---

### Post by modulok on 2007-10-10
yup, that first link is the remote I have....but I just ordered the gyration kb/universal remote combo.

IS that the remote you have, the gyration universal media center remote?
[http://www.gyration.com/c-3-remotes.aspx](http://www.gyration.com/c-3-remotes.aspx) - I got the combo coming, but remote is the same in both I think.

---

### Post by napsilan on 2007-10-10
I think mine is an older version of that one (windows buttons is rectangular, not round), but yes, same model line.

Also note that the Mythbuntu 7.10 will use xfce instead of openbox, so the autostart files will probably be different.  ([http://www.mythbuntu.org/node/67](http://www.mythbuntu.org/node/67))

---

### Post by pennstatebadboy on 2007-10-16
I'm so confused. Napsilan, do you think you could post a step-by-step on how you got your Gyration MC Remote to function properly in Ubuntu?

I've had this remote for nearly a month, and have tried to get it configured without success. Only a few of the buttons work (mouse, arrows, OK, and volume).

The evrouter seems to be the best solution, but I'm having a hard time following your posts.

If you could do a step-by-step, I think you'd help a lot of people who are trying to use this remote with Ubuntu.

Thanks in advance!

---

### Post by napsilan on 2007-10-16
What are you using it for?  Because I use it for mythtv (feisty), the autostart file information only applies to openbox (and will be different for kde, gnome, xfce, etc.).

Out of the box, the numbers, arrows, and mouse should work with no problem.  What other buttons are you trying to get working, and for which application and Desktop?

---

### Post by pennstatebadboy on 2007-10-16
I'm trying to get them all to work for mythtv. Is it possible to program the buttons to mimic a keyboard stroke? Say, for instance, I want to make the record button seem as if it's the letter R on my keyboard. Or channel up = pageup. That way, the remote will work (although not perfectly) between various applications.

In other words, I'd like to mimic the keyboard keys that perform various function for mythtv.

Does that make sense?

Thanks.

---

### Post by napsilan on 2007-10-17
Step 1--Download the evrouter.deb and evrouter_gyration.txt files from post #6

Step 2--install evrouter (sudo dpkg -i evrouter.deb)

step 3--edit /home/mythtv/.config/openbox/autostart.sh (assuming mythtv is your user, and that evrouter_gyration.txt is in mythtv's home directory, and that the remote ID in /dev hasn't changed) and add

```

xhost +local:root
killall evrouter
sudo rm /tmp/.evrouter*   #removes a previous lock file
sudo evrouter --config=/home/mythtv/Evrouter_gyration.txt /dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-mouse /dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd &

```

step 4--Use visudo to edit sudo permissions, and add these lines to the file (again, assuming mythtv is your user)
```

mythtv ALL=NOPASSWD: /usr/bin/evrouter
mythtv ALL=NOPASSWD: /bin/rm

```

step 5--Edit /usr/share/mythtv/startmythtv.sh (sudo gedit), and right before the line that says #start mythtv frontend software, add (again assuming mythtv is the user)
```

sh /home/mythtv/.config/openbox/autostart.sh &

```

step 6--if you want to edit the keybindings, edit the evrouter_gyration.txt file. (man evrouter should help with special commands)

---

### Post by pennstatebadboy on 2007-10-17
Thanks, Napsilan! You are most excellent! You get popcorn, because it's delicious.

:popcorn:

---

### Post by arbrandes on 2007-11-19
napsilan, thanks for the info!  Very useful.  But have you gotten the final 4 keys to work?  That'll probably take some kernel hacking, huh?

---

### Post by arbrandes on 2007-11-20
I also found that the power button on this remote will endlessly repeat.

---

### Post by arbrandes on 2008-01-18
Update:

I talked to Gyration (their online support is pretty neat), and the "SETUP MENU", "LAST", and "INPUT" keys are actually not meant to send USB signals, only IR ones.  So 3 of the 5 keys are not actually broken on Linux; they just weren't designed to work as expected.

The other two keys, namely POWER and TV, still need fixing though.  I got the attention of one of the USB kernel developers through the Linux Kernel Mailing List (Jiri Kosina, he's being very helpful), and there just might be a kernel patch for the offending keys in the coming days or weeks.  This is the thread in question:

[http://lkml.org/lkml/2007/12/28/84](http://lkml.org/lkml/2007/12/28/84)

As I noted there, the folks at Gyration pointed me in the direction of fiire.com, where they sell the same remote but supposedly with firmware that makes it work out of the box in Linux.  It's a nice alternative, especially if we can't get the Windows version to work, or if one doesn't want to patch his/her kernel.

---

### Post by DemonBob on 2008-02-04
Can anyone update this for the new Mythbuntu based on Xfce? I'm on 7.10. 

Thanks.

---

### Post by volkswagner on 2008-02-08
Ditto, I would love to get more function from this remote with mytbuntu 7.10

Only numbers, navigation and mouse are working here

---

### Post by volkswagner on 2008-02-15
Bump.....  Does anyone know how to apply this to XFCE?

---

### Post by arbrandes on 2008-02-15
Using evrouter under XFCE shouldn't be any different from Gnome.  What kind of problem are you having?

---

### Post by volkswagner on 2008-02-15
This is the line which has stopped me from even attempting an install.  My experience level is newbie.  When I jump into stuff I often find myself with  system worse than prior to applying a fix.  The following is in post #13 of this thread.

> What are you using it for? Because I use it for mythtv (feisty), the autostart file information only applies to openbox (and will be different for kde, gnome, xfce, etc.).

Do you feel I can just install evrouter running mythbuntu 7.10 all latest updates?

Will evrouter place my autostart file correctly?  Will I need to do something else to get it to autostart?

---

### Post by arbrandes on 2008-02-16
Just try to run it manually and see if it works for you.  When it's working properly (i.e. .evrouterrc is configured to your liking), then figure out how to autostart in XFCE.  Don't get me wrong, it's a good question (to which I don't know the answer), but only indirectly related to whether evrouter can do the job.

---

### Post by arbrandes on 2008-02-16
By the way, Jiri Kosina has produced a kernel patch on the LKML that'll fix the power button on this remote.  It also tries to fix the TV button, but this part doesn't work (at least not for me):

[http://lkml.org/lkml/2008/2/11/386](http://lkml.org/lkml/2008/2/11/386)

I had to fix a few typos on the patch to make it work, so I'm attaching it here.

---

### Post by volkswagner on 2008-02-16
Thanks for the response.

The Good:  Installed EvRouter on my slave machine.  I have a lot more function from the remote.  Need to do some tweaking to get the following buttons to work (back,live tv,music,pictures,video)

Most important to me is get the back button to work, i can use the "clear", but it is small and in a difficult location.

I had to change the file name Evrouter_gyration.txt to .evrouterrc

I am not sure what to do so I can get it to load on start up with mythfrontend.

The bad:  No AMD64 version so I can't use it for my Master BE/FE in my family room entertainment center.  :(

I emailed the author to see if he will be willing to make and AMD64 version.

---

### Post by volkswagner on 2008-02-17
Update:  I have the remote working with most of the important buttons.  I have not tackled the shortcut buttons.

I had to add the evrouter to the autostart folder.  I had to create an udev rule to change the permissions to allow users access so in fact it would autostart.  As mentioned earlier I had to change the name of the .txt file to what evrouter wanted.

What joy  :)

Thanks again!

---

### Post by hpladds on 2008-02-20
volkswagner:

> I had to create an udev rule to change the permissions to allow users access so in fact it would autostart.

Would elaborate on your udev permissions changes? 

I need to change the permissions of the Gyration keyboard and mouse devices -- /dev/input/event 0 and 1 (respectively).

Currently only root has access to these devices at boot time and running evrouter as non-root returns a "permission denied" error message. Changing the permissions to allow non-root access to the device files solves the problem.

I suspect this is the very reason you wrote your udev rule.

thanks,
hpladds

---

### Post by hpladds on 2008-02-21
Well that wasn't so tough.

I created the file:
 > /etc/udev/rules.d/10-local.rules

and placed this text into it

> KERNEL=="event[0,1]",  OWNER="*nameofuser*"

Thanks for the reference to:

[http://reactivated.net/writing_udev_rules.html]("http://reactivated.net/writing_udev_rules.html")

---

### Post by DemonBob on 2008-02-21
How did you get it to autostart? I don't know where to put the files.

---

### Post by 4dognight on 2008-03-04
> **DemonBob said:**
> How did you get it to autostart? I don't know where to put the files.

I put the evrouter_gyration.txt file in my home directory as .evrouterrc
I then modified his 'start' script he had and put it in /usr/local/bin/evrouter_start.sh
change permissions on the file

sudo chmod 4755 /usr/local/bin/evrouter_start.sh

The contents of /usr/local/bin/evrouter_start.sh

xhost +local:root
killall evrouter
 rm /tmp/.evrouter*   #removes a previous lock file
/usr/local/bin/evrouter  /dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-mouse /dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd &



Then I created an autostart from the Applications->settings->autostarted applications menu and pointed it to the start script i created in /usr/local/bin/evrouter_start.sh

---

### Post by 4dognight on 2008-03-04
> **arbrandes said:**
> By the way, Jiri Kosina has produced a kernel patch on the LKML that'll fix the power button on this remote.  It also tries to fix the TV button, but this part doesn't work (at least not for me):

[http://lkml.org/lkml/2008/2/11/386](http://lkml.org/lkml/2008/2/11/386)

I had to fix a few typos on the patch to make it work, so I'm attaching it here.

How did you apply the patch?  I dont see a file called hid-input.c , and it asks me which file to apply the patch to.

---

### Post by arbrandes on 2008-03-04
hid-input.c lives in drivers/hid/.  Sorry about that, the patch should have been more explicit.

---

### Post by 4dognight on 2008-03-04
> **arbrandes said:**
> hid-input.c lives in drivers/hid/.  Sorry about that, the patch should have been more explicit.

Im a newbie when it comes to patching drivers. When I tried to apply the patch it failed. It appears I need a newer version. mine is a 2.6.22.

I dont suppose you could give me a few pointers on what steps I would need to get this patch applied?

---

### Post by arbrandes on 2008-03-05
Okay, lemme try to help.  This patch was made against 2.6.24-rc6, vanilla from kernel.org, which is what I'm running now.  It'll probably work with 2.6.24.3, the latest stable vanilla kernel as of now, but I believe you'll be better off trying to make it work with your own 2.6.22.  I'm attaching a version of the patch that *should* work with 2.6.22, although it is untested.

I'm going to assume you're running Ubuntu Gutsy with the default kernel, and this is what I would do, as root:

```

# aptitude install linux-source
# cd /usr/src
# tar xjf linux-source-2.6.22.tar.bz2
# cd linux-source-2.6.22/drivers/hid
# patch -p0 < hid-input-2.6.22-gyration.patch
# make -C /lib/modules/`uname -r`/build M=`pwd` modules
# find . -name '*ko' -exec cp {} /lib/modules/`uname -r`/kernel/drivers/hid/{} \;

```

Then reboot and see if it works!

---

### Post by 4dognight on 2008-03-05
ok, I got that to compile.

When I tried it, it didnt seem any different. 
when I run 

lsmod|grep hid, i get

usbhid                 29536  0 
hid                    28928  1 usbhid
usbcore               138632  6 lirc_imon,usbhid,ohci_hcd,ehci_hcd

So  I did ,
sudo  rmmod hid 
sudo rmmod usbhid

 Then did 
 sudo modprobe -a hid 
sudo modprobe -a usbhid

Then I rerun

lsmod|grep hid

usbhid                 29792  0 
hid                    29312  1 usbhid
usbcore               138632  6 usbhid,lirc_imon,ohci_hcd,ehci_hcd

So, it is using the newer driver, I am assuming by the different sizes.

Problem is when I reboot, it reverts back to the old ones. What am I doing wrong.


Also, is the center green button suppsed to be the same function as the power button after the patch?

---

### Post by arbrandes on 2008-03-06
Hmm, you could probably do an update-initramfs to fix the reboot issue.  But it is pointless if the patched driver isn't working the way it should.

The patch shouldn't do anything to the green button.  The only thing it does is fix the power button, which otherwise would repeat endlessly.  You can check that with xev.

---

### Post by DemonBob on 2008-03-23
I wrote a script to make the Green MCE button to start and stop mythfrontend

1. Download the attachement

2. copy the file to /usr/local/bin/

3. Change the premissions of the file to executable.

```
sudo chmod 4755 /usr/local/bin/mce.start.sh
```

4. Edit your .evrouterrc for key event 102 and make it look like so. (Notice the change at the end)
```

"Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-mouse" none key/102 "Shell/mce.start.sh &"
```

---

