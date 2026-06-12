---
title: "HOW-TO: Sixaxis/DualShock3 in bluetooth mode - Intrepid"
date: 2008-11-06
forum: Hardware
---

### Post by falkTX on 2008-11-06
If you're looking for a way to connect your Sixaxis to PC (through USB or bluetooth mode), you've come to the right place. I'm writing an app that makes that just as easy as press some buttons. The only things you need are a Sixaxis (1 or more), and a bluetooth pen/stick (if you want to connect through bluetooth).

This app is (obviously) for Linux only. At least Ubuntu Intrepid (8.10) is required (or any other distro based on this Ubuntu, or later)



NOTE:
This tread was moved. Please go here for the updated program:
```
http://ubuntuforums.org/showthread.php?p=7472939
```

---

### Post by falkTX on 2008-11-06
I made a video proving this is possible

[http://rapidshare.com/files/161235313/TheProve.ogv.html](http://rapidshare.com/files/161235313/TheProve.ogv.html)

Only 10 downloads available.


Upload it somewhere else if you want

---

### Post by Holmen on 2008-11-08
And if I'm not running 64-bit?

---

### Post by falkTX on 2008-11-10
Intrepid 64-bit doesn't handle joysticks well, so it has priority.

If you want 32-bit, I can do it as well. Do you want it?

---

### Post by Holmen on 2008-11-10
Yes, please! I'm actually creating a application just for SixAxis. But unfortunately I haven't got that far. One of the reasons why is that I haven't got my gamepad working since Hardy. Ive been using Intrepid since alpha 3.

Read more - [http://www.danielholm.se/sixaxis](http://www.danielholm.se/sixaxis)

---

### Post by Holmen on 2008-11-11
I would really appreciate it. Thank you so much.

---

### Post by falkTX on 2008-11-13
Ok, I'll try 32-bit as well. But be patient as I have to download a new ISO and my net connection is low

---

### Post by Npl on 2008-11-13
A bit offtopic, but as I thought buying a DS3 solely for using on PC (no PS3 yet)... does it "just work" when attached via USB (minus rumble of course)?

---

### Post by Holmen on 2008-11-13
> **Npl said:**
> A bit offtopic, but as I thought buying a DS3 solely for using on PC (no PS3 yet)... does it "just work" when attached via USB (minus rumble of course)?

Yes, Ubuntu sees it as a joystick - which it is. So, yes it does "just work".

---

### Post by falkTX on 2008-11-13
Hey Holmen, I noticed that you're programing software, so I think it's okay to ask you this;

Can you check:
[https://help.ubuntu.com/community/Sixaxis](https://help.ubuntu.com/community/Sixaxis)

And make all those steps on a 32-bit hardy installation (use VirtualBox if you don't have any PC left for tests).

Then you could upload the 'sixpair' 32-bit binary and the bluez3.26 with the patched hidd. You would save me a lot of time...

---

### Post by Holmen on 2008-11-13
Yeah, sure thing!

But doesn't Hardy come with the version of Bluez that replaced hidd with luetoothd-service-input?

Then you will have to use sixpair2, which I still have from my previous Hardy install.

---

### Post by Leno. on 2008-11-15
I got my PS3-controller connected now using the normall hidd-method (i386), but it doesn´t seem to react when I pust the buttons ("cat" only gives me some output, it confirms that it is connected, but nothing else happens)

---

### Post by umesh.hansla on 2008-11-16
I'm presuming that the amd64bit patch will not work for powerpc64? :)

---

### Post by Holmen on 2008-11-16
> I'm presuming that the amd64bit patch will not work for powerpc64? 
I'm afraid so. 

But couldn't you attach the patch and tell us how to apply and compile it so that you won&#7831; have to to that, falkTX?

---

### Post by falkTX on 2008-11-17
> **Holmen said:**
> I'm afraid so. 

But couldn't you attach the patch and tell us how to apply and compile it so that you won&#7831; have to to that, falkTX?


The patch is actually from Hardy along with almost all the files in the deb file.
The thing is that bluez4.12 doesn't use "hidd" anymore but "bluetoothd" (hidd was replaced).
What this deb file does is installing old things without messing with the new ones.
For example, the "/etc/init.d/bluetooth" was renamed to "bluetooth-six".

I don't think there's any other way to make this work (for now).
I'll try to make an i386 deb file soon, but if you could post the patched Hardy deb file, it will save lots of time.

For the powerpc64 users, I can also make a deb for that, but you'll have to upload the bluez3.26 with the hidd patch and also the sixpair (build on powerpc64)

---

### Post by falkTX on 2008-11-17
I just found this:

[https://launchpad.net/ubuntu/intrepid/i386/bluez-compat](https://launchpad.net/ubuntu/intrepid/i386/bluez-compat)
(other platforms are supported as well)

Please check if it works, I'll check too once I get home

---

### Post by Holmen on 2008-11-17
> I just found this:

[https://launchpad.net/ubuntu/intrepid/i386/bluez-compat](https://launchpad.net/ubuntu/intrepid/i386/bluez-compat)
(other platforms are supported as well)

Please check if it works, I'll check too once I get home

Yeah, I where to ask you about the bluez-compat package. Do you think that would work?

How do we i386- and sparc64-users give it a try?

You seem to know more about BlueZ the I do. I'm just a simple GUI builder. Perhaps you would like to join be with the creation of SixA? [https://launchpad.net/gsixaxis](https://launchpad.net/gsixaxis)

---

### Post by falkTX on 2008-11-20
I'm no developer, but I can help

about the bluez-compat, I think it will work (and if it did it would be so much better, since it was support till Jaunty).

So I'll focus on this

see ya soon

---

### Post by Holmen on 2008-11-21
Sounds great! Looking forward to it.

---

### Post by falkTX on 2008-11-24
It's done!

I've sucefully completed the amd64 and i386 packages and I'll do for other versions as well.
It doesn't need the patched hidd, cause the bluez-compat provides it (yes, with the hidd patch included!)

I didn't have the chance to try if the i386 is working correctly, but I assume it will (they are both based on bluez-compat)

I also made 4 scripts to make our life easier:
 1. connect
when sixaxis has been setup and you restart, just run this and then press the PS button. Simple, ha?
 2. bt-normal
after connecting or setup sixaxis run this script to make bluetooth back to normal again
 3. setup
to setup a connection between you pc and sixaxis (only needed to run once, unless you have various joysticks). It is divided in 5 small steps and uses zenity to display messages about what the user needs to do. It's very very easy to setup
 4. turn-off
turns off the sixaxis by killing the hidd connection (useful to save battery).


I'm not using my laptop now, so I can't upload the packages, but I'll do it soon.



But I need you to test one thing (It's very important!):
install bluez-compat, and run "sudo hidd --nocheck --server -n" (you may have to turn off bluetooth - "sudo /etc/init.d/bluetooth stop"
Does the terminal log something when you press the PS button on sixaxis?
In my 64-bit Ubuntu it does, even without installing bluez-sixaxis deb.
If it works with 32-bit, or any other version, then the sixaxis will just work (in any version!), if not... it will be useless to try

Please test

---

### Post by ravay on 2008-11-24
> **falkTX said:**
> It's done!

But I need you to test one thing (It's very important!):
install bluez-compat, and run "sudo hidd --nocheck --server -n" (you may have to turn off bluetooth - "sudo /etc/init.d/bluetooth stop"
Does the terminal log something when you press the PS button on sixaxis?


Please test


First of all thank for your work.

I just tested on my PC (i386) and after entering "sudo hidd --nocheck --server -n" I don't see any message on the terminal after pressing the PS button on a paired joypad.

Hope somebody else can test it in order to know if is just a problem with my configuration or a common problem.

Regards,

Ravay

---

### Post by Holmen on 2008-11-24
That is so F awesome! You rule, falkTX. I think I love yoU ;)
I waited so long to get my PS3 gamepad working under Ubuntu.
I will definitly use your .deb in SixA -with your permission, of course.

I actually do get something from running "sudo hidd --nocheck --server -n", Bluetooth off.

---

### Post by ravay on 2008-11-25
That's a good news holmen. I gonna check again if something if wrong with my configuration...

---

### Post by falkTX on 2008-11-25
Here it is!
the 1st version of bluez-sixaxis for 32 and 64 bit.

Please check the first post for info and the above post for the files

---

### Post by falkTX on 2008-11-25
Here are the files.

sixaxis-x86 for 32-bit and sixaxis-x64 for 64-bit


If you want for any other version please say so

---

### Post by Holmen on 2008-11-25
I'm very sorry to tell you that your awseome package did not work..

I follow the sixaxis_setup steps but after reboot and trying the sixaxis_connect-script, my gamepad doesn't show up in /dev/input.

But during the setup process it is recognized in the list of connectable devices in BlueZ.

I'm sorry to tell you this. Your package is truly awseome and the Zenity-windows is almost like cutting-edge for theese kind of ways to get fun hardware working in Linux.

I would really like to help you some more. Like writing a description of the package, and perhaps creating some binarys so you wouldn't have to cd into the /usr/share dir.

This really gives me so much inspiration to work more with my GUI for the SixAxis/DualShock 3 gamepads. 

I really don't mean to be destructive with is, rather the opposite.

---

### Post by falkTX on 2008-11-26
> **Holmen said:**
> I'm very sorry to tell you that your awseome package did not work..


Can you post the results of the sixaxis_setup script?
(I mean, run the script on terminal, and send me all the terminal outpus)
Thank you

---

### Post by Holmen on 2008-11-26
Of course! Here it is.

```
daniel@daniel-laptop:/usr/share/bluez-sixaxis$ ./sixaxis_setup > ~/sixaxis-setup.txt
hidd: no process stoppedbluetooth-applet-six: no process stoppedhidd[14900]: Bluetooth HID daemonhidd[14900]: New HID device 00:19:C1:E5:48:0D (Sony Computer Entertainment Wireless Controller)
mkdir: unable to create dir "/usr/local/bin"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""": File exists
eate dir "/usr/local/bin""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""hidd[14900]: Exit
```

---

### Post by falkTX on 2008-11-26
Seems like everything is ok...
Did you test if the joystick was working fine after the 'sixaxis_setup'?
(jstest /dev/input/js0)

This is a little weird...

---

### Post by Holmen on 2008-11-26
Yeah, I know. And I do get the gamepas listed in BlueZ during the setup. But there is quite hard to set it to trusted in the 4 step. It's blinking. But I do get it trusted and if I run the setup again, it is set to trusted.

Could it be something with the pairing?

```
daniel@daniel-laptop:~$ ls /dev/input/ | grep js
js0
daniel@daniel-laptop:~$ jstest /dev/input/js0 
jstest: No such device

```

---

### Post by falkTX on 2008-11-26
Did you clicked on "Turn Off"?
cause it automatically turns off sixaxis after few seconds

---

### Post by Holmen on 2008-11-26
Yes I did. Tried to follow the instructions the best I could.

---

### Post by falkTX on 2008-11-27
I think I know what's wrong
Can you run the 'sixaxis_setup' again, and on step 3, when it asks to set as untrusted, click on the 2nd separator (services, I think), and see if the 'Input service' is running?
That was the 1st problem I faced with the 64-bit deb, but I though it was fixed already.

---

### Post by Holmen on 2008-11-27
No, it is not running and I can't seem to start it ither.

---

### Post by falkTX on 2008-11-28
I'm downloading the original Ubuntu 32-bit iso and I'll install on a real PC (not VM).
Give me 3 days and It will be fixed

---

### Post by Holmen on 2008-11-29
Sounds lovely! Thank you soo much!

---

### Post by falkTX on 2008-12-03
Here it is again!

I actually fix it in just one day, so I started making new stuff on the time I had left.

There are now 6 scripts, one of them is a "GUI" to the other 5.
There's also a *.desktop file for it!
And I made a build for powerpc and sparc!

Just download, install, and go to Apps -> Acessories -> Sixaxis-Gui
It couldn't get easier, really.

Feel free to use the scripts and modify them;
Just send me the final result (my e-mail is inside the scripts)

If you find any problem or just want another version please say so.

For more information check the first post.

---

### Post by Holmen on 2008-12-03
IT WORKS! And Neverball is alive again, at last ;D

Thank you soo much! And the GUI is awesome. I Will definitely use it with my app.

---

### Post by falkTX on 2008-12-03
I'm glad I could help.

I also started making configuration files for some apps/games (smc, torcs, trigger, pcsx2, epsxe...)

But I know you'll be playing games for some time...
So I don't think I need to work on this for a while.

Tell me anything once when you get... bored.
LOL

---

### Post by Holmen on 2008-12-03
Dude, you have to help me mith SixA! What you are doing the exact same thing that I'm trying to figure out. Could you please help me with it on Launchpad?

I have more ideas. Like figuring out the tilt function, batterystatus and more. It will also be a GUI for maping the buttons and axis to keys using xserver-xorg-input-joystick.

[https://www.launchpad.net/gsixaxis](https://www.launchpad.net/gsixaxis)
[http://&www.danielholm.se/sixaxis](http://&www.danielholm.se/sixaxis)

---

### Post by falkTX on 2008-12-03
Sure I can help.

I still don't understand much of Launchpad, so I'll just keep posting news here.
But, as I said before, I am no developer (yet). I don't know anything about C++ or python or whatever.

So my work will just be (for now) creating configuration files.
I'm thinking on controlling Compiz (the cube) with Sixaxis.

What do you think?

---

### Post by falkTX on 2008-12-03
I just downloaded your source-code.
I'm a total newbie in this, but I'll try to integrate my scripts there (by doing a single one that combines everything and has support for 'switches').

Do you accept me as a member of SixA?

---

### Post by Holmen on 2008-12-03
That is awesome! I will defeintly grant you a member.

I have also send you a PM with my mail.

You don't have to use my code. We could start a new branch instead. I would maybe be more easy for both of us?

---

### Post by falkTX on 2008-12-03
Yes, that would be really nice.
I also send you a mail, so you can know mine

I don't have net acess at home yet, so I think we should do different tasks now, then combine them.

I'll try to make an ALL-in-One script and some patch files for configure apps for sixaxis (ex. Trigger = ~/.trigger/trigger.config).
Then we could use the GUI to setup these apps for Sixaxis just by running the patch

---

### Post by Holmen on 2008-12-03
Great idea!

Maybe we shouldn't spam this post with more of SixA talk? This is your .deb ;)

I've send you a response mail. And also added some more blueprints one the project site.

---

### Post by thiefness on 2008-12-05
Ok, I am running
Linux ubuntu 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux
and have installed your sixaxis-x64.deb package, have tried following the steps many times. Some time in the middle of the set up new connection, it will recognize the controller. so i finish the steps and restart, run connect sixaxis to pc, but it is not recognized, there is no longer any bluetooth icon, and jscalibrator does not recognize any joysticks connected. I added the lines to xorg.conf that you posted were needed for 64-bit users but still no luck. Any help would be greatly appreciated.

---

### Post by falkTX on 2008-12-05
You should check if other joysticks work, and if yes, check if sixaxis is running ok after setup.
The bluetooth icon disappears on "Connect Sixaxis to PC", you can restore it by running "Restore Normal Bluetooth"

Main causes of the problem are:
 1. Did you installed the deb on page 4, or an older one?
 2. When you run "Setup New Connection", on step 3, click on the BT applet and the on the "Services" tab. Is the Input Service running?

If everything seems ok, please post your terminal output (by running "sixaxis-gui" in a terminal)



Note: I've tested it with Ubuntu, Kubuntu and Xubuntu. It doesn't seem to work on Xubuntu (weird thing)

---

### Post by falkTX on 2008-12-09
I noticed that were 5 downloads for the powerpc version. Can you tell me if it's working?

And has anyone tried to play with 2 sixaxis at the same time?
(Cause I'm going to buy a new one, with hope that it will work)

---

### Post by ravay on 2008-12-11
HI FalkTx,

first of all thank you very much for your work...

I tried the 386 and PowerPC version.

For the 386 version I wasn't able to make it working, I don't receive any message from the HIDD server, but I believe is a problem with my USB bluetooth stick.

The PowerPC version (tried on PSUbuntu) worked just perfectly.


Regards,

Ravaz

---

### Post by falkTX on 2008-12-11
Thank you ravay,
I'm very glad it worked on powerpc, cause I didn't have any way of testing it.

I had to reinstall Ubuntu and I noticed something - The setup connection doesn't work at first time. I had to run "Connect Sixaxis to PC" two times in order to get "PlayStation(3) Controller" at the bluetooth-applet (It presented "00-19-XX-XX-XX" instead of PS-controller the first time).

So, if you're reading this - don't quit at first time
(Just at the second, LOL...)

---

### Post by ravay on 2008-12-11
hehe, I didn't give up at the first and neither the second time but at the 100th time. But the problem is always the same, no information coming from the hidd server. I even tried to reinstall bluez without succes. I'm looking for some friend able to borrow me another BT adapter and see if I can have better result. I will let you know.

I'm also looking forward to see the tool you and Holmen are trying to make for the sixaxis....

---

### Post by falkTX on 2008-12-12
Do you want a preview? Here it is (mock-up)

About your problem - Can you check if the input service is running on step 3? (on the bluetooth-applet). This was a problem Holmen was having, but with the new package it was fixed (I think).
But maybe it's just the BT device that is broken

---

### Post by ravay on 2008-12-13
The preview seems very good, nice work...

Regarding my problem. Yes the input service is running with the last version you made.

---

### Post by falkTX on 2008-12-15
If you checked that your BT device was not broken, then you can use a patched hidd from Hardy.
I'll see if I can find it

---

### Post by ravay on 2008-12-17
I don't think the bluetooth device is broken. I can see one device on the applet, but the weird thing is that I just see the address with my PC, where in the PS3 a see the name of the device (Sony Bluetooth...).

---

### Post by falkTX on 2008-12-17
You can try this:
(1)
 - install bluez-sixaxis (beta2)
 - run:
/etc/init.d/bluetooth stop
/etc/init.d/bluetooth-six start
/etc/init.d/bluetooth-six stop
sudo hidd --nocheck --server -n
 - see if hidd reported anything
(2)
 - navigate to '/var/lib/bluetooth'
 - see if there is any folder there (if yes, continue)
 - edit the 'trusts' file for something like this:
00:19:C1:62:9D:5F [all]


I've found a way to set sixaxis as trusted without using bluetooth-applet, but sometimes it doesn't work. I'll need more time

---

### Post by jaime77 on 2008-12-20
hi,
its almost 1 year since i start looking modding the sixaxis in ubuntu.
always crashing in a wall lol

here is my original scream for help
[http://ubuntuforums.org/showthread.php?t=665130](http://ubuntuforums.org/showthread.php?t=665130)

with intrepid many things improved but one thing i never could made was the keyboard thing, what i wanted was not mapping keys to one button, but a combination of buttons to one key.

since you have some experience with scripts and configurations, you think maybe is plausible?

thx for any help or idea

PD..
by the way, the only response i got at the time was from Holmen your partner in SixA, i installed the package and read the man he told me, but cant do the keyboard thing, if both are seeking ideas for SixA i like to see that feature in SixA

---

### Post by Holmen on 2008-12-21
Hello again!

Sorry that my previous post did not help. But SixA will! ;)

falkTX has made a beautiful prototype and I will try to get some coding going so that you could use your gamepad properly ;)

---

### Post by jaime77 on 2008-12-21
if i can help you in anything holmen let me know.
i have some free time that can spend coding, testing, trying(lol), etc

i truly apreciate the SixA effort, good luck

---

### Post by Holmen on 2008-12-22
If you know anything about coding you are more then welcome to join us. As I said before, falkTX has made and awesome prototype of the app, and I've been quite busy until now. And neither of us are so familiar with coding - yet. I know PHP, but learning Python.

If you are interested, send me a PM here or at the projects page on Launchpad.
[https://launchpad.net/gsixaxis](https://launchpad.net/gsixaxis)

---

### Post by falkTX on 2008-12-22
If what you want is to have sixaxis as keyboard/mouse, then I'm glad to tell you that I've already done it. The SixA app I'm (trying) to build with Holmen will let you configure it with a nice GUI.
I'm a little busy with one other project, KMStar, but after christmas I should have lots of time again.
So, be patient, and wait just a couple of days, since I'm working on some new scripts...

PS: I still can't get some key combinations to work (like Ctrl+Alt+Left, to rotate compiz-cube). I don't know if I'm doing something wrong or if it's just a bug; but I'll keep trying (I don't give up easily).

See ya soon!

---

### Post by pilotv on 2008-12-29
> **falkTX said:**
> EDIT:
----- [COLOR="Blue"]This is the updated version - #2![/COLOR] -----
Now supporting 32-bit, 64-bit, sparc and powerpc versions of Ubuntu Intrepid

Just download the attached deb (**_on page 4!_**) and install
(It requires bluez-compat, bluez, gksu and zenity)
quick-link: [http://ubuntuforums.org/showthread.php?p=6299657#post6299657](http://ubuntuforums.org/showthread.php?p=6299657#post6299657)

Then click on "Applications" -> "Accessories" -> "Sixaxis-Gui"

----------------------------------------------------------------------

It now as a simple GUI that lets you choose 5 things:

  1. "Setup New Connection"
To setup a connection between you pc and sixaxis;
(only needed to run once, even if you have many joysticks, but they ALL needed to be configured at the same time).
It is divided in 5 small steps and uses zenity to display messages about what the user needs to do. It's very very easy to setup, and bluetooth is automatically back to normal when finished
  2. "Connect Sixaxis to PC"
When sixaxis has been setup and you restart or you turn it off, just run this and then press the PS button. Simple, ha?
  3. "Check HIDD Connections"
This display all connected joysticks to your PC [experimental]
  4. "Restore Normal Bluetooth"
After connecting sixaxis run this script to make bluetooth back to normal again
  5. "Turn Off Sixaxis"
Turns off the sixaxis by killing the hidd connection (useful to save battery).


For users with the **64-bit** version they also need to do a little thing, or any joystick won't work at all. Run:
*sudo gedit /etc/X11/xorg.conf* [replace 'gedit' for 'kate' if you're using kubuntu]
Add the following lines to the beginning:

Section "ServerFlags"
    Option         "AutoAddDevices"  "False"
EndSection

You may have to reconfigure your keyboard after doing this
(go to System -> Preferences -> Keyboard Layout (or something similar)


Hello,
I`m working with Ubuntu PowerPC in a PS3.

First I`ve connected the Dualshock3 by usb, using "hal" and it runs ok.

Then I disconnected the DS3 from usb port, connected a wireless mouse and I`ve installed the Sixaxis-gui with the correct file following the instructions provided by Falk, and reached to connect by bluetooth the Dualshock3 to Ubuntu, it blinks all 4 led`s, but I can`t do nothing with it.

I`ve tested it with the jstest command but when I press the buttons it don`t give any signal to jstest.

Can you help me?
Regards
Pilotv

---

### Post by Holmen on 2008-12-29
That is unfortunate. Try 'dmesg' after that you finished the "connect-to-pc" with SixAxis-gui, and post the output.

---

### Post by pilotv on 2008-12-30
Hi Holmen,

Here is the output from "dmesg" command in a attached file txt.

As you can see the Sixaxis is connected by Bluetooth.
Waiting your reply.
regards

---

### Post by Holmen on 2008-12-30
Try to run:
```
ls /dev/input | grep js
```

---

### Post by Leafer on 2009-01-01
In order for me to get this to work I had to follow the "USB Pairing" section from:
[https://help.ubuntu.com/community/Sixaxis/](https://help.ubuntu.com/community/Sixaxis/)

After that I could use sixaxis-gui.

Now if only motion sensing would work I could die happy having played Freespace2 and Vegastrike by waving my arms through the air like an idiot.

---

### Post by ravay on 2009-01-04
I finally got a new usb bluetooth adapter and as expected I made my sixaxis working with the PC. The problem was on the previous hw/driver. Now I'm just impatient to see SixA in action... ;-)

I'm trying to connect two sixaxis to the PC without succes, did somebody manage to make more then one joypad working together?

---

### Post by falkTX on 2009-01-06
Good news!
After some time working on another project, now I'm back to bluez-sixaxis again.

The next version I'll upload will be RC1, so many things will be fixed. (I started learning a few more C...)
There will be a script to check if the PC supports linking to Sixaxis in bluetooth mode (if this fails, you can just quit).

I also talked to some guys in a computer store and they will let me test many Sixaxis at once (I think they have 2; +1 that I own).


Some guys are actually making gyro and motion sensors of Sixaxis working under Linux, trough a 'hidraw' kernel patch. This is a very hard to get and "normal" Ubuntu doesn't support it (needs a kernel patch).


For now, I'll just focus on getting RC1 done and upload it.

See ya soon

---

### Post by falkTX on 2009-01-06
> **Leafer said:**
> In order for me to get this to work I had to follow the "USB Pairing" section from:
[https://help.ubuntu.com/community/Sixaxis/](https://help.ubuntu.com/community/Sixaxis/)

After that I could use sixaxis-gui.

I've tested my package many times.
USB Pairing is not needed

---

### Post by Holmen on 2009-01-06
Same here. I also got more time to work on the project again after some hard work with four websites. Or was it five...

Ither way, I'm also exited for the final release. Hope you will like it.

falkTX, keep up the awesome work!

---

### Post by ddryden on 2009-01-11
I really like the look of this good work so far. What else did you want to add that needs a coder? The bash scripts seem to do the job as it is :)

---

### Post by falkTX on 2009-01-12
RC1.1 is here!

Check first post for more info.

---

### Post by falkTX on 2009-01-12
--Advanced--
If you're using KDE 4.1 or just need BT to Sixaxis you can replace the sixaxis init-bluetooth with the normal one.
*sudo cp /etc/init.d/bluetooth-six /etc/init.d/bluetooth*
(This will make sixaxis always work, so you don't need to launch Sixaxis-GUI to connect)
Don't forget to reinstall bluez when you don't want it anymore.



If you want to help, you can:
 - Create more fdi files (check those on /usr/share/bluez-sixaxis). I'll also make files for Totem, SMPlayer and KDE. Note that the Firefox one is not finished.
 - Add "--setup" to 'sixaxis' in terminal
 - Create new cool scripts (Anything that is cool, I'll accept)
 - Check how the 'hidraw'* thing can be done easily in Ubuntu
 - Test the program and report how it works


***
"The 'hidraw' thing" - is a kernel patch that, after done, you can use Sixaxis' gyro and motion sensors. It would be great to see this feature included soon (maybe trough a fdi file?)

---

### Post by ravay on 2009-01-12
FORGET ABOUT THIS POST I SHOULD READ BETTER THE INSTRUCTIONS ;-) I DID NOT SEE THERE ARE TWO PACKAGES...




Hi FalkTx,

I just installed the new version on a 386 but is not working.
I can't find the sixaxis-gui and /usr/share/bluez-sixaxis doesn't exist.


Any idea?

PS: did you test the new version with more then one sixaxis together?

---

### Post by falkTX on 2009-01-12
I splited in 2 packages cause it would be lot easier for me to update them.

So, for all people reading this:
 - READ FIRST PAGE -

Then you should know that you must instal 'bluez-sixaxis-bin' that matches your Ubuntu version (i386, amd64, powerpc or sparc) [i386 is the default one]; then you install the new 'bluez-sixaxis' RC1.1
(If you installed previous beta1-2, please remove them first:
*sudo dpkg -r bluez-sixaxis*)

It's not complicated...

---

### Post by falkTX on 2009-01-12
I just realised that Jaunty has the new 'hidraw' patch, in kernel 2.28.
This will not happen on Intrepid.

I'll focus on getting RC2 done, and then I'll be working on getting gyro/motion sensors working.


See ya soon!

---

### Post by darfe on 2009-01-12
Nice work! Im using it now!..

---

### Post by falkTX on 2009-01-14
> **darfe said:**
> Nice work! Im using it now!..

You're fist post and you're already thanking me...


Well, welcome to the forums

---

### Post by vulcanfk on 2009-01-14
downloaded bluez-sixaxis-bin_i386.deb and bluez-sixaxis_rc1.1_all.deb from page 8.  installed the *-bin first, then the *-rc1

when i run the compatibility check, it says "Your device not compatible... Please check your BT device and controller."  i've tried multiple times, so its not just a first time failure.

i know my BT device is working.  its an "IOGear GBU421 Bluetooth 2.0 USB Micro Adapter" that's about a week old.  i can connect my wiimote via this adapter.

my setup:
EeeBox PC B201
EeeBuntu built on 8.10 (Intrepid)
Kernel 2.6.27-8-eeepc

is there a command line process i can go through to get more feedback?  i.e. what is not working.  thanks

---

### Post by falkTX on 2009-01-15
> **vulcanfk said:**
> 
i know my BT device is working.  its an "IOGear GBU421 Bluetooth 2.0 USB Micro Adapter" that's about a week old.  i can connect my wiimote via this adapter.

my setup:
EeeBox PC B201
EeeBuntu built on 8.10 (Intrepid)
Kernel 2.6.27-8-eeepc

is there a command line process i can go through to get more feedback?  i.e. what is not working.  thanks

You can do the "compatibility check" manually (by look at sixaxis-gui script on gedit), but I don't think it's necessary since it only depends on hidd terminal output.
But, you can force the connection. You just need to know the MAC of your Sixaxis. I'll explain:
When you run "Setup First Connection", it simply turns on old hcid (that has support for hidd) and then launches hidd (the 'hidd --nocheck ...' thing). Then the output of hidd is writen to '/var/lib/bluetooth/X1:XX:XX:XX:XX/trusts' in this way:

X2:XX:XX:XX:XX [all]
--------------------
X1:XX... is the MAC of your bluetooth device
(this folder should already exist)
X2:XX... is the MAC of your Xixaxis
So, if you know your Sixaxis' MAC, just add a line to the trusts file, and you can skip the setup part.

Then, run "Connect Sixaxis to PC".
(or 'sixaxis -c' in terminal)

This might work, so please try and tell me the result.

---

### Post by vulcanfk on 2009-01-15
> **falkTX said:**
> You can do the "compatibility check" manually (by look at sixaxis-gui script on gedit), but I don't think it's necessary since it only depends on hidd terminal output.
But, you can force the connection. You just need to know the MAC of your Sixaxis. I'll explain:
When you run "Setup First Connection", it simply turns on old hcid (that has support for hidd) and then launches hidd (the 'hidd --nocheck ...' thing). Then the output of hidd is writen to '/var/lib/bluetooth/X1:XX:XX:XX:XX/trusts' in this way:

X2:XX:XX:XX:XX [all]
--------------------
X1:XX... is the MAC of your bluetooth device
(this folder should already exist)
X2:XX... is the MAC of your Xixaxis
So, if you know your Sixaxis' MAC, just add a line to the trusts file, and you can skip the setup part.

Then, run "Connect Sixaxis to PC".
(or 'sixaxis -c' in terminal)

This might work, so please try and tell me the result.

Thanks falkTX.  I won't get a chance to try this out until Friday night, but I'll let you know how it goes.

---

### Post by vulcanfk on 2009-01-16
Stupid question...how do I get the MAC of my sixaxis?

---

### Post by falkTX on 2009-01-20
> **vulcanfk said:**
> Stupid question...how do I get the MAC of my sixaxis?

Honestly, I don't know.
Usually hidd reports it, so the app manage to write it to the trusts file.

But you can try:
 1. Do the 'sixpair' stuff (don't know the webpage, but it's easy to find), then try the compatibility check again
 2. Connect it to U. Hardy? (not sure if it will work) (Then hidd reports the MAC)
 3. Trough a PS3 console settings?? (Never touched one)

But, more important - can you connect it trough USB, and upload the "lsusb" output command? I'm guessing there are 2 types of Sixaxis and one doesn't work...

---

### Post by falkTX on 2009-01-26
I recently changed to Ubuntu Jaunty (Alpha 3).
Since I don't have net acess at home it's going to take some time to set it up to my tastes...
But it will give me the chance to try it on the new bluez4.25

RC2 is coming soon...

---

### Post by jikki on 2009-01-28
Hi, I got my ps3 controller to work via bluetooth in mouse/keyboard mode. However, when I click "disable mouse/keyboard" so that I could play it as a gamepad in sldmame, my joystick is no longer functioning.

I want my controller to be a "controller" and not a "fake gamepad," so how can I fix this? Thanks!

---

### Post by Holmen on 2009-01-28
What do you mean?

The Gamepad is recognized as a joystick natively in Ubuntu and for the "fake" it doesnt really matter, does it?

---

### Post by jikki on 2009-01-28
Well, that's the problem.. With mouse/keyboard option enabled, my joystick is registered fine. But if I disable that option so I can use the analog sticks, my gamepad is no longer registered. 

With mouse/keyboard option, the left analog is assigned to the mouse movement, so when I try to bind the keys in the emulator, it thinks I'm moving the mouse, instead of the analog stick..

---

### Post by Cobaltikus on 2009-01-31
First off thank you for this thread and all the hard work put in here!  I was so glad to find that I didn't have to manually patch or recompile anything to get this to work.

I was having trouble getting this to work for the LONGEST TIME. And then I had a big "duh I'm an idiot moment" due to a misunderstanding in the first connection prompts. I thought I should share this in case others were having trouble too.

I have a 60 GB PS3, latest firmware as of 2009-01-30, Ubuntu 8.10 Intrepid clean install, haven't upgraded anything, and have done nothing but try to get this to work so I can use my sixaxis using bluetooth for emulators.

I was confused during the Setup First Connection. At the point where the prompts are telling you to connect the bluetooth device I thought it was refering to the sixaxis controller!!! (after all it is a bluetooth device)  And it confused me when it said "If it's internal turn it on".  I thought What does that mean? internal? It is in my hands...  So I just shrugged and connected the USB cable because it said to connect the bluetooth device and I thought well maybe it needs to pair that way like it does on the PS3 Game OS.  The 4 red lights flashed for a minute. As instructed I waited until the lights stopped and then I clicked OK.  I pressed the PS button when it prompted me to and the setup complete message was displayed saying to run Connect sixaxis to PC so I clicked OK, Chose Tasks Menu, Chose Connect Sixaxis to PC, Pressed the PS button when instructed and then clicked OK.

This obviously did not work so after trying again and again and going back and forth between jstest and Sixaxis-Gui for a while I started writing this post to ask for help.  When I finished I re-read it and then it hit me.

The bluetooth device it was refering to is the PS3! Not the sixaxis!:o

I repeated the steps with this new found knowledge and vwah-lah!!  All is now well.

In the end I think it would help the instructions if it included the fact that the sixaxis controller should not be connected with the USB cable at any time during the setup, even though this may seem like an obvious common sense fact, I missed it and others may also.

Thanks again.  This app works great now. You guys are awesome!

---

### Post by falkTX on 2009-02-01
> **jikki said:**
> Well, that's the problem.. With mouse/keyboard option enabled, my joystick is registered fine. But if I disable that option so I can use the analog sticks, my gamepad is no longer registered. 

With mouse/keyboard option, the left analog is assigned to the mouse movement, so when I try to bind the keys in the emulator, it thinks I'm moving the mouse, instead of the analog stick..

This will be fixed in RC2.
Also a picture showing what buttons-2-keys do is present when you choose a input profile for sixaxis.
Please wait just a few more days for it.

---

### Post by falkTX on 2009-02-02
RC2 is... well... is ready, but the forums doesn't allow a file to exceed 900Kb.
You have to wait a little until I create my PPA repo and upload it there.

---

### Post by Cobaltikus on 2009-02-03
This really doesn't have anything to do with Ubuntu, but has everything to do with this sixaxis program.

Could someone make a version of this AWESOME software for Pocket PC/Windows Mobile 6? (Or maybe Android)

Didn't think so but thought it couldn't hurt to ask.

---

### Post by NTolerance on 2009-02-03
Rather than use the Sixaxis as a mouse/keyboard, I'd just like to use it in ZSNES.  Am I in the right place?  I have installed RC 1.1 and my Sixaxis just blinks at me, nothing seems to work.  I'm using a Broadcom USB Bluetooth adapter.  Do I need to somehow un-pair my Sixaxis from my PS3 before I start this process?  Is it true that a USB cable is not used in this process at all?  Anyone get this working in ZSNES?

---

### Post by falkTX on 2009-02-04
I've never tried ZNES before. But, just because you asked I'm going to install it and see if it works there.
And USB cables are not needed, just the bluetooth stick. But some bluetooth sticks don't support connect to sixaxis, so I created the "Check Compatibility" just to see if it will work or not. If not, it's the bluetooth stick/pen problem, not the sixaxis controller/joystick.

---

### Post by falkTX on 2009-02-04
> **Cobaltikus said:**
> This really doesn't have anything to do with Ubuntu, but has everything to do with this sixaxis program.

Could someone make a version of this AWESOME software for Pocket PC/Windows Mobile 6? (Or maybe Android)

Didn't think so but thought it couldn't hurt to ask.

This is Linux only, It will never work on Windows, just because it's not open-source (the bluetooth drivers need a patch, that is already included in Ubuntu).

---

### Post by NTolerance on 2009-02-04
> **falkTX said:**
> I've never tried ZNES before. But, just because you asked I'm going to install it and see if it works there.
And USB cables are not needed, just the bluetooth stick. But some bluetooth sticks don't support connect to sixaxis, so I created the "Check Compatibility" just to see if it will work or not. If not, it's the bluetooth stick/pen problem, not the sixaxis controller/joystick.

The compatibility check fails on my adapter.  :(

---

### Post by falkTX on 2009-02-04
> **NTolerance said:**
> The compatibility check fails on my adapter.  :(

What ubuntu version do you use? Does your bluetooth stick work for anything else (like connecting to cellphones?).
Please run 'lsusb' on a terminal and post the results.

The RC2 will include in the compatibility-check adapters that *may* support Sixaxis. I've already mailed Holmen asking for upload the RC2 (my network is with problems).


Also, about the ZSNES - I've installed it and it seems to work "out-of-the-box". I mean, I can assign any ZSNES key to a sixaxis button or even the axis. What is the real problem with ZSNES?

---

### Post by Holmen on 2009-02-04
I think that some of the users has issues with the SixAxis as a Keyboard/mouse - the just want to connect the SixAxis to their PC over bluetooth and use it as a joystisk.

And for thoose of you who want this - just connect the sixaxis to your pc without the keyboard/mouse-mode and you are done. Now map your keys in your favorte emulator.

---

### Post by falkTX on 2009-02-05
Good News!
I went to a computer store to test my app there, cause they have a PS3...


This is what I've learned:

1 - Connecting a Sixaxis to PC while is connected/paired to a PS3 is not possible
2 - You have to unpair your Sixaxis before using it on PC:
      Go to Setting/Acessories (and somewhere else I can't remember, but it's obvious) and hold the PS button
      The Sixaxis may unpair itself. You know when you click PS (on Sixaxis), if it turns on "1", then it's still paired.
(I never work with a PS3 before but the unpairing process was easy and fast, so I don't remember what I really did)
3 - Connecting 2 Sixaxis to PC is possible (but they have to be setup one by one)
4 - It's possible to have 2 Sixaxis with different input profiles:
      Disconnect All
      Select a profile for one Sixaxis and connect it
      Select another profile and connect other Sixaxis
(This way one Sixaxis could be set to Gnome, while the other to Wormux, for example)


About the RC2 (at this time is actually RC2.3), I'm having problems uploading it to my PPA repository; I'll probably had to upload it somewhere else. But that will be soon, I promise

---

### Post by falkTX on 2009-02-06
-  New Version - 1.0test  -

This is actually the final version, but I think it requires more testing before saying "hey, it's final and stable!"; so, 1.0test.


Sorry guys for taking so long on uploading the files, it's just that my usual network connection (the library) was not working fine. But now it works again.


So, you ask, what changed in this version?

Here is a full list:
1. Added KDE, Totem and SMPlayer profiles
2. After choose an input profile you can view a picture showing the buttons-key configuration
3. The Compatibility check, reports if your devices might be (but not fully) supported
4. Translations now possible (I've already made portuguese)
5. Setup stuff was completely rewrite (You'll have to try it...)
6. You can disconnect 1 Sixaxis while leaving the other connected
7. Fixed Select/L3/R3 sometimes not working correctly
8. Manual page for 'sixaxis' (the Sixaxis-Gui version in terminal)
9. New icon


I also tested with Jaunty, and it's compatible. This way you don't have to stick to Intrepid just because of this app (LOL)

For those interested in the development of SixA, it hasn't been started yet, but the ideas are there (an applet...); It will not take much time to have a real app replacing this crappy zenity dialogs...

---

### Post by ravay on 2009-02-06
Hi FlakTx,

I'm not able to download the file from upload.com. Could you please put somewhere else (i.e. [http://www.mediafire.com](http://www.mediafire.com) ). 

Thanks

Ravaz

---

### Post by falkTX on 2009-02-07
> **ravay said:**
> Hi FlakTx,

I'm not able to download the file from upload.com. Could you please put somewhere else (i.e. [http://www.mediafire.com](http://www.mediafire.com) ). 

Thanks

Ravaz

Sure. I'm searching for a good spot to put the files there (in order to make a full repository). Until I don't find it, I'll just have to upload files one by one. If you know a good place to put the files (FTP?) tell me, okay?

---

### Post by ravay on 2009-02-07
FTP I don't know, but for simple file hosting [www.mediafire.com](www.mediafire.com) works good. If I find an FTP I will tell you...

---

### Post by ravay on 2009-02-08
Hi FalkTx,

I tried to install on Jaunty Alpa3 but he has a problem with a dependency (xserver-xorg-input-joystick). You said the package is working with it, how did you test it?

---

### Post by Holmen on 2009-02-08
> **ravay said:**
> Hi FalkTx,

I tried to install on Jaunty Alpa3 but he has a problem with a dependency (xserver-xorg-input-joystick). You said the package is working with it, how did you test it?

Hi, I also got this bug and have reported it on Launchpad - [https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-input-joystick/+bug/326965](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-input-joystick/+bug/326965)

---

### Post by falkTX on 2009-02-09
Although I said it works on Jaunty, I needed to do a little trick to get it work. I explain how:

1. Download the xserver-xorg-input-joystick here:
[http://packages.ubuntu.com/jaunty/xserver-xorg-input-joystick](http://packages.ubuntu.com/jaunty/xserver-xorg-input-joystick)

2. copy it to your home folder

3. open a terminal and type:
  a) dpkg -x xserver-xorg-input-joystick*deb input-joy-hack
  b) dpkg -e xserver-xorg-input-joystick*deb input-joy-hack/DEBIAN

4. Now navigate to the input-joy-hack folder, then DEBIAN, and open the control file. There's a section containing:
Replaces: xserver-xorg (<< 6.8.2-35)
Provides: xserver-xorg-input-2.1
(delete them, save, and delete the back-up file created by the editor)

5. Now on terminal type:
a) dpkg -b input-joy-hack
b) sudo dpkg -i input-joy-hack.deb
c) sudo apt-get install -f


You can now install the bluez-sixaxis[-bin] packages.

Note: Keyboard/Mouse feature is not yet supported in Jaunty, just because it still uses old xorg-joystick driver. Once it gets updated, it will be supported

---

### Post by falkTX on 2009-02-09
wow...
my app is already used at other forums:
[http://tutorials.dcemu.co.uk/how-to-install-ubuntu-on-your-ps3-for-vintage-gaming-emulation-182288.html](http://tutorials.dcemu.co.uk/how-to-install-ubuntu-on-your-ps3-for-vintage-gaming-emulation-182288.html)

---

### Post by Morten M on 2009-02-23
Being a total noob in linux, I've been trying to setup the PS3 controller as a mouse in Kubuntu 8.10.

Managed to do it with some success - but remapping the buttoms on the pad is making my patience growing thin...

Been reading a bit about the work you're doing here - and I wonder if:

a) Will I be able to set up /change setups without bluetooth - running it from USB?

b) Would it require much work to "snip" some of the coding's you've done - and make a small prog just for changing the setup/mapping of the controls on the sixaxis?

c) Could you post a "print" of the x11/joystick.fdi with a few buttom setups, i.e. "dpad up" mapped to "up"... Would love to set it up so the kids can use it to play some games with it instead of using the keyboard...


Thanks in advance

Morten

---

### Post by Holmen on 2009-02-25
Hi, 

A) Just plug the gamepad in and you have yourself a joystick. The Linux kernel sees the gamepad as a joystick and you can map the keys inside your favorite emulator.

B) SixA will support this and you will be able to use it for both wireless and threw wired connection.

C) attached.

---

### Post by Morten M on 2009-02-26
Thanks, Holmen - that file was exactly what I was looking for. Couldn't figure out the syntax when reading some other .fdi file :)

---

### Post by Holmen on 2009-02-26
Glad to be of service.

---

### Post by falkTX on 2009-03-01
For those that want to use Sixaxis from boot/login time, I explain how:

1. create a back-up of the normal bt file:
*sudo cp /etc/init.d/bluetooth /etc/init.d/bluetooth-new*

2. replace the original bt file so it loads sixaxis' bluetooth instead of the normal one:
*sudo cp /etc/init.d/bluetooth-six /etc/init.d/bluetooth*


This will make "Connect Sixaxis to PC" active during boot (you can press the PS button right after the Ubuntu usplash logo appears, and seconds later its connected).

If you want to revert what you done earlier, do:
*sudo cp /etc/init.d/bluetooth-new /etc/init.d/bluetooth*
This will make things back to normal

NOTE:
Normal bluetooth will became unusable in this mode

---

### Post by sucher22 on 2009-03-01
nice tool, thanks

maybe you should link that sixpair thing in your start post or even make a note if compability check fails - it was necessary for my eee-901

---

### Post by falkTX on 2009-03-02
I just need to say that I might not update this app soon.
I don't have a job for almost a year and I really need to focus on that. Also my usual network connection (at the library) is not working again and it shouldn't work soon.

So, give me 1 month or 2 till I can find a job, then (with network at home) I'll be able to make my own repo, so this app can be updated easily.
Sorry for this

---

### Post by halfsoul on 2009-03-05
Hi,
I can't figure out why this seems to work for everyone except for me.

First things first:
> **falkTX said:**
> It doesn't seem to work on Xubuntu (weird thing)
Is this still true?  If so, that could be my problem since I'm using Xubuntu.  I tend to think this comment is outdated, can someone confirm if this works on Xubuntu?

Here's my situation:
- The sixaxis works via usb (nothing special, just confirming)
- sixaxis paired successfully with sixpair method
- sixaxis-gui says it's compatible
- sixaxis-gui successfully connects to sixaxis
   * dev/input/js0 appears
   * sixaxis lights continue to blink indefinitely until I turn off via sixaxis-gui = connection confirmed
- jstest registers no change while pushing buttons, does not seem to recognize buttons
- jscalibrator does not recognize pushing buttons or moving joystick, but seems to pull & populate info correctly (name, axes, etc)

I have tried keyboard & mouse off, k&m on (fake joystick), k&m on (gnome).  Nothing seems to work.

Here is my dmesg:
```
[  207.744260] usb 2-2.3: new full speed USB device using ps3-ehci-driver and address 6
[  207.768261] usb 2-2.3: configuration #1 chosen from 1 choice
[  183.404051] input: Sony PLAYSTATION(R)3 Controller as /class/input/input3
[  207.854512] input,hiddev97,hidraw2: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-sb_05-2.3
[  191.740735] ioctl32(xfce4-terminal:5171): Unknown cmd fd(12) cmd(0000530b){t:'S';sz:0} arg(0fe79588) on /dev/pts/1
[  191.743518] ioctl32(xfce4-terminal:5171): Unknown cmd fd(12) cmd(0000530b){t:'S';sz:0} arg(0fe79590) on /dev/pts/1
[  191.746207] ioctl32(xfce4-terminal:5171): Unknown cmd fd(12) cmd(0000530b){t:'S';sz:0} arg(0fe79598) on /dev/pts/1
[  243.164353] usb 2-2.3: USB disconnect, address 6
[  222.593556] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[  226.765484] input: Sony Computer Entertainment Wireless Controller as /class/input/input4
[  266.972383] input: Sony Computer Entertainment Wireless Controller as /class/input/input5
[  325.478134] input: Sony Computer Entertainment Wireless Controller as /class/input/input6
[  342.366678] input: Sony Computer Entertainment Wireless Controller as /class/input/input7
[  412.192657] input: Sony Computer Entertainment Wireless Controller as /class/input/input8
[  459.348754] input: Sony Computer Entertainment Wireless Controller as /class/input/input9
[  477.056782] input: Sony Computer Entertainment Wireless Controller as /class/input/input10
[  719.798203] input: Sony Computer Entertainment Wireless Controller as /class/input/input11
[  746.340043] input: Sony Computer Entertainment Wireless Controller as /class/input/input12
[  830.925574] input: Sony Computer Entertainment Wireless Controller as /class/input/input13
[  947.465801] input: Sony Computer Entertainment Wireless Controller as /class/input/input14
[ 1011.874419] usb 2-2.3: new full speed USB device using ps3-ehci-driver and address 7
[ 1011.897986] usb 2-2.3: configuration #1 chosen from 1 choice
[ 1011.964996] input: Sony PLAYSTATION(R)3 Controller as /class/input/input15
[ 1012.003341] input,hiddev97,hidraw2: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-sb_05-2.3
[ 1034.346033] usb 2-2.3: USB disconnect, address 7
[ 1034.818033] input: Sony Computer Entertainment Wireless Controller as /class/input/input16
```
You can see here that I connected with USB to perform sixpair, then tried 11 times in sixaxis-gui, double-checked proper operation via usb, then two more attempts via sixaxis-gui.  No luck.

I notice that via usb there is an extra line of recognition that is absent via bluetooth:
```
[ 1012.003341] input,hiddev97,hidraw2: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-sb_05-2.3
```
I don't know enough to understand if this is just extra usb stuff or if perhaps the bluetooth interface doesn't recognize it as an HID.  So, will someone please post dmesg of a successful bluetooth connection?

Thanks!

---

### Post by falkTX on 2009-03-09
> **halfsoul said:**
> Hi,
I can't figure out why this seems to work for everyone except for me.

First things first:

Is this still true?  If so, that could be my problem since I'm using Xubuntu.  I tend to think this comment is outdated, can someone confirm if this works on Xubuntu?

Here's my situation:
- The sixaxis works via usb (nothing special, just confirming)
- sixaxis paired successfully with sixpair method
- sixaxis-gui says it's compatible
- sixaxis-gui successfully connects to sixaxis
   * dev/input/js0 appears
   * sixaxis lights continue to blink indefinitely until I turn off via sixaxis-gui = connection confirmed
- jstest registers no change while pushing buttons, does not seem to recognize buttons
- jscalibrator does not recognize pushing buttons or moving joystick, but seems to pull & populate info correctly (name, axes, etc)

I have tried keyboard & mouse off, k&m on (fake joystick), k&m on (gnome).  Nothing seems to work.

Here is my dmesg:
```
[  207.744260] usb 2-2.3: new full speed USB device using ps3-ehci-driver and address 6
[  207.768261] usb 2-2.3: configuration #1 chosen from 1 choice
[  183.404051] input: Sony PLAYSTATION(R)3 Controller as /class/input/input3
[  207.854512] input,hiddev97,hidraw2: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-sb_05-2.3
[  191.740735] ioctl32(xfce4-terminal:5171): Unknown cmd fd(12) cmd(0000530b){t:'S';sz:0} arg(0fe79588) on /dev/pts/1
[  191.743518] ioctl32(xfce4-terminal:5171): Unknown cmd fd(12) cmd(0000530b){t:'S';sz:0} arg(0fe79590) on /dev/pts/1
[  191.746207] ioctl32(xfce4-terminal:5171): Unknown cmd fd(12) cmd(0000530b){t:'S';sz:0} arg(0fe79598) on /dev/pts/1
[  243.164353] usb 2-2.3: USB disconnect, address 6
[  222.593556] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[  226.765484] input: Sony Computer Entertainment Wireless Controller as /class/input/input4
[  266.972383] input: Sony Computer Entertainment Wireless Controller as /class/input/input5
[  325.478134] input: Sony Computer Entertainment Wireless Controller as /class/input/input6
[  342.366678] input: Sony Computer Entertainment Wireless Controller as /class/input/input7
[  412.192657] input: Sony Computer Entertainment Wireless Controller as /class/input/input8
[  459.348754] input: Sony Computer Entertainment Wireless Controller as /class/input/input9
[  477.056782] input: Sony Computer Entertainment Wireless Controller as /class/input/input10
[  719.798203] input: Sony Computer Entertainment Wireless Controller as /class/input/input11
[  746.340043] input: Sony Computer Entertainment Wireless Controller as /class/input/input12
[  830.925574] input: Sony Computer Entertainment Wireless Controller as /class/input/input13
[  947.465801] input: Sony Computer Entertainment Wireless Controller as /class/input/input14
[ 1011.874419] usb 2-2.3: new full speed USB device using ps3-ehci-driver and address 7
[ 1011.897986] usb 2-2.3: configuration #1 chosen from 1 choice
[ 1011.964996] input: Sony PLAYSTATION(R)3 Controller as /class/input/input15
[ 1012.003341] input,hiddev97,hidraw2: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-sb_05-2.3
[ 1034.346033] usb 2-2.3: USB disconnect, address 7
[ 1034.818033] input: Sony Computer Entertainment Wireless Controller as /class/input/input16
```
You can see here that I connected with USB to perform sixpair, then tried 11 times in sixaxis-gui, double-checked proper operation via usb, then two more attempts via sixaxis-gui.  No luck.

I notice that via usb there is an extra line of recognition that is absent via bluetooth:
```
[ 1012.003341] input,hiddev97,hidraw2: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-sb_05-2.3
```
I don't know enough to understand if this is just extra usb stuff or if perhaps the bluetooth interface doesn't recognize it as an HID.  So, will someone please post dmesg of a successful bluetooth connection?

Thanks!

hm...
It's weird that It wasn't working on Xubuntu, but I was using it in VirtualBox, so things are different.

This:
```
[ 1012.003341] input,hiddev97,hidraw2: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-sb_05-2.3
```
is the 'hidraw' driver for Sixaxis (all HID componenets should have). This is what (will) make work Sixaxis' Gyro & Sensors. On Intrepid the hidraw is only available in USB mode; On Jaunty Bluetooth mode also supports 'hidraw'.

You can try this: (commands in Sixaxis-Gui)
1. Config/Clear All HIDD Data
2. Setup new connection
3. Connect Sixais to PC
4. Disconnect All
5. Reboot
6. Connect Sixais to PC (again)

The problem is that Xubuntu loads the wrong driver:
*input: Sony Computer Entertainment Wireless Controller as /de...*
instead of 
*input: PLAYSTATION(R)3 Controller as /devices/pci0000:00/0000:..*
and this shouldn't happen after Sixaxis is configured properly (although it happens once, as it says on the last part of setup).
Once you got '_PLAYSTATION(R)3 Controller_' instead of 'S_ony Computer Entertainment Wireless Controller_', then you're good to go.

Maybe there's a way to blacklist this driver, I'll look for it once I have time

---

### Post by falkTX on 2009-03-19
Hello guys!

Getting a job is not easy, and I realise that it doesn't have to take all my time. I'll do what I can, and if I can't get a job it's not really my fault.
This means I have enough time for updating 'bluez-sixaxis'. I've been rewriting every piece of it, so by the end of the month it should be ready for real use (the CLI part).
I haven't got much news for the SixA project and guys, so maybe I'll create the GUI by myself. I'm starting to learn a little C, but I'm also interested on Qt4.
Resuming, the rewritten 'bluez-sixaxis' will be ready by the end of the month, and the GUI will start to be worked on once the CLI part is ready.
There's some things that I still don't know how to do, so I'll need your help on this.

See ya soon

---

### Post by falkTX on 2009-03-23
Good News!

On Jaunty, the xserver-xorg-input-joystick has been updated, this means that mouse/keyboard stuff works again.

And, if you're interested, I got a job.. I'll still try to make the rewrite by the end of the month.
For the curious ones, I uploaded the code as it is right now, and also the gui-test1.ui for the GUI (Qt4). Note that only amd64 and the basic things work right now

---

### Post by Holmen on 2009-03-23
Awesome. Thanks for everthing, but I guess that I will keep up with my work anyway.

---

### Post by falkTX on 2009-03-24
> **Holmen said:**
> Awesome. Thanks for everthing, but I guess that I will keep up with my work anyway.

What have you done so far? Qt4 is far away from my knowledges, and now with my job I don't have much time to learn stuff

---

### Post by roger.ubu on 2009-03-24
hey falkTx
where i can dowmload the last version.
i think is 1.0test
thx

---

### Post by falkTX on 2009-03-25
> **roger.ubu said:**
> hey falkTx
where i can dowmload the last version.
i think is 1.0test
thx

1st page

---

### Post by falkTX on 2009-03-27
Good News!
I've talking to Holmen and we put a deadline for the first alpha/beta - 15th April. This version wil have a real GUI!

The command-line part will be ready sooner than that, so I'll release it here around next week.

See ya soon

---

### Post by SparkyFlary on 2009-03-28
I just tried it with my sixaxis controller. I installed both apps and now it's working great with Mupen64Plus! Mupen64Plus seems to accept the ps3 controller if it's connected to usb. This forum should be placed in place of [https://help.ubuntu.com/community/Sixaxis](https://help.ubuntu.com/community/Sixaxis) or something because your app is a lot simpler and better.

---

### Post by falkTX on 2009-03-30
> **SparkyFlary said:**
> This forum should be placed in place of [https://help.ubuntu.com/community/Sixaxis](https://help.ubuntu.com/community/Sixaxis) or something because your app is a lot simpler and better.

Once I finish the rewrite, I'll look into it. I also have plans for creating a webpage (maybe on sourceforge.net). It shouldn't take long

---

### Post by falkTX on 2009-04-01
Here's first (alpha) rewrite.

To install:

```
cd /dir/to/extrated/source
make YOUR-ARCHITECTURE
sudo make install
```

replace YOUR-ARCHITECTURE by i386/amd64/powerpc/sparc (choose yours).


As this is a rewrite, some stuff don't work now. But the most important (setup new connection, load, disconnect & restore) is working.
This release don't have a GUI (waiting for Holmen), but it has a new option 'sixaxis bluetooth on boot', that fully works.
The GUI should be ready near 15 April

---

### Post by falkTX on 2009-04-03
I just found out something that I used to dream about...

Check:
[http://www.evosmartconsole.com/index.html](http://www.evosmartconsole.com/index.html)


It's an open-source console! It will be release this month (April 2009), and it's based on Linux Fedora.

Guess what?
I'll work on getting the Sixaxis connecting it by bluetooth. Since it is Linux based, that shoudn't be too hard.

And, Wow, that will be so cool!! A gaming-console that allows to run virtualized OSes, Linux games (this also means emulators!), and use any normal Linux application!! Maybe Wine will be supported as well, in time...

Downloading Fedora now...

---

### Post by Holmen on 2009-04-03
That is awesome. I think that Fedora also uses BlueZ, so that shouldn't be to hard. And Fedora is also a big desktop OS and probably Ubuntus closest relative in ease of users.

---

### Post by falkTX on 2009-04-04
> **Holmen said:**
> That is awesome. I think that Fedora also uses BlueZ, so that shouldn't be to hard. And Fedora is also a big desktop OS and probably Ubuntus closest relative in ease of users.

Indeed, Fedora is very easy to use. But it works trough RPMs not DEBs...
This means I still don't even know how to install things (the 'apt-get' doesn't exist for RPM distros).
I also mailed the EVO devs telling of my intention.

How is the GUI going, Holmen?

---

### Post by Holmen on 2009-04-04
> I also mailed the EVO devs telling of my intention. Yeah! That is great.

Fedora uses 'yum' instead om 'apt-get'. I'm sure you can google after some instructions. And for the compiling and installation from source its the same. We can use Checkinstall for building a temporary .rpm package.

The GUI is turning out wine. I have one week away from school which should be enough for the GUI to be finished. I alse integraded Jauntys new awesome notification to SixA. The hardest thing would be the applet.

---

### Post by falkTX on 2009-04-04
> **Holmen said:**
> I also integraded Jauntys new awesome notification to SixA.

What??? WOW!!! Man, that is really great! Good job!

I found a way to get more things to work on 'sixaxis' script, so in a few days it will be able to "check compatibility", "force compatibility" (through sixpair), and a new function:
Disconnect a sixaxis based on his number:
Let's say we have 2 sixaxis plugged, but we only wanted to disconnect the 1st one. We do:
```
sixaxis disconnect 1
```
replacing "*1*" by any other number will disconnect that sixaxis, or, if it doesn't exist, tell that to the user.

Also I'm making a list with the full commands that can be used in your GUI, so you don't have to search it. They will detect the DE (Gnome, KDE or none) and launch appropriate sudo app (gksu, kdesudo or sudo) when needed.

---

### Post by Holmen on 2009-04-04
That is really cool. That is feature that we need very much!

---

### Post by __Ryan__ on 2009-04-04
FalkTX,

First of my hat goes off to you for the work that you've done! I've been working on getting the PS3 controller working over bluetooth for some time.

On that note I have have come up with a solution that is slightly different from your own. Instead of using the deprecated version of bluez-utils I have instead applied that patch successfully to the default 4.12 version of bluez and gotten it to work that way. 

In the end it seems much easier as you can simply replace the default 4.12 version of the hidd daemon and replace it with the patched one. This seems to be much more of a straight-forward approach which eliminates possible compatibility issues and unneeded configuration. I have not looked into powerpc support but it supports 32/64bit versions of Ubuntu just fine.

I have posted the guide here:
[http://www.wiredrevolution.com/ubuntu/setup-ps3-controller-over-bluetooth-on-ubuntu]("http://www.wiredrevolution.com/ubuntu/setup-ps3-controller-over-bluetooth-on-ubuntu")

It may work to serve as a better foundation to build your GUI upon than the current solution.

Let me know what you think.

Ryan

---

### Post by Holmen on 2009-04-04
Thanks for the guide. Im walking it trough just as we speak. I recognise it all and this is how I first got my gamepad working. But I don't know if this is really what we need for SixA. Even if this is more straight forward it mixes with the users bluetooth stack and after an possible upgrade or update of it, they wont have the possibility to get it working again without recompiling the source, or wait for us to do it.

falkTX's way is the most friendly one, except the part where the "usual" bluetooth is stopped to make room for sixaxis. But this absolutely could be interesting for SixA 0.2. SixA 0.1 will be released on the 15th of April.

But I think that you would be welcome to our team, if you would be interested?

---

### Post by falkTX on 2009-04-06
I'm not sure I understand what your patch does. The 'hidd' on the bluez-compat package already includes the ps3/sixaxis patch.

Let us finish the 1st version, then we reconsiderate that.
And Holmen, I know I told I'll make a list of actions that the GUI will use, but now I feel It's better if you do that. You should use commands like this:

sixaxis sixa d
sixaxis sixa l
sixaxis sixa r
sixaxis sixa setup_1
sixaxis sixa setup_2
sixaxis sixa setup_cancel
sixaxis sixa check_comp
sixaxis sixa ..etc..

---

### Post by __Ryan__ on 2009-04-07
> I'm not sure I understand what your patch does. The 'hidd' on the bluez-compat package already includes the ps3/sixaxis patch.

The source code for the hidd daemon "hidd.c" does contain the "enable_sixaxis" function which would lead a person to believe that the patch already exists. However if you look closer you will see that the 4.12 version is still missing the patch. 

It's very misleading because if you launch the unpatched hidd daemon and try to connect the controller you will see the normal bluetooth traffic signals from hcitool and it would appear that it has successfully connected. jstest will show otherwise as it does not recognize any button presses from the controller. This has really tripped up some people. The patched hidd daemon ensures correct registration.

Ryan

---

### Post by Holmen on 2009-04-07
> **__Ryan__ said:**
> The source code for the hidd daemon "hidd.c" does contain the "enable_sixaxis" function which would lead a person to believe that the patch already exists. However if you look closer you will see that the 4.12 version is still missing the patch. 

It's very misleading because if you launch the unpatched hidd daemon and try to connect the controller you will see the normal bluetooth traffic signals from hcitool and it would appear that it has successfully connected. jstest will show otherwise as it does not recognize any button presses from the controller. This has really tripped up some people. The patched hidd daemon ensures correct registration.

Ryan

Perhaps in SixA 0.2 we could have a patchet bluez in our PPA.

---

### Post by Holmen on 2009-04-07
> **falkTX said:**
> I'm not sure I understand what your patch does. The 'hidd' on the bluez-compat package already includes the ps3/sixaxis patch.

Let us finish the 1st version, then we reconsiderate that.
And Holmen, I know I told I'll make a list of actions that the GUI will use, but now I feel It's better if you do that. You should use commands like this:

sixaxis sixa d
sixaxis sixa l
sixaxis sixa r
sixaxis sixa setup_1
sixaxis sixa setup_2
sixaxis sixa setup_cancel
sixaxis sixa check_comp
sixaxis sixa ..etc..

Okay, I will look into it ;)

---

### Post by falkTX on 2009-04-07
> **__Ryan__ said:**
> The source code for the hidd daemon "hidd.c" does contain the "enable_sixaxis" function which would lead a person to believe that the patch already exists. However if you look closer you will see that the 4.12 version is still missing the patch. 

It's very misleading because if you launch the unpatched hidd daemon and try to connect the controller you will see the normal bluetooth traffic signals from hcitool and it would appear that it has successfully connected. jstest will show otherwise as it does not recognize any button presses from the controller. This has really tripped up some people. The patched hidd daemon ensures correct registration.

Ryan

Thanks for sharing this. That is why the usual PS3 driver (Sony Computer Wireless Controller) doesn't work, and we have to do a trick to pull the new one (Playstation3 Controller). That should make things easier (and faster).
Thank you

---

### Post by Holmen on 2009-04-13
Removed, due to that I read from the first page and taught that it was new.

---

### Post by Holmen on 2009-04-13
Hey everybody!

We have some wonderful news. Not only is there two days untill release, but we also need your help - looking for bugs and just give us a quick saying regarding how our work looks.

Run this do get the latest code: ```
bzr branch lp:gsixaxis
```
And then just run sudo make install to install it without having to compile sixpair and other stuff. This only installes the desktopfiles, CLI and GUI SixA, icons and some other stuff. Then you should be able to run ```
sixa-gui
``` and there it is. Tray icon and GUI.

If you dont want the tray run: ```
sixa --no-tray
``` or no GUI: ```
sixa --no-gui
```
By just running ```
sixa
``` you have the cli-based app.

And nothing really functional is set yet not to mess with the upcoming settings. When handling a signal it just gives a printed output.

Please report all bugs, ask questions and create blueprints on our project-page: [http://www.launchpad.net/gsixaxis](http://www.launchpad.net/gsixaxis)

---

### Post by falkTX on 2009-04-14
You should write commands into code mode, like this:
```
bzr branch lp:gsixaxis
```

Its just a little better

---

### Post by Holmen on 2009-04-14
Done ;)

---

### Post by Holmen on 2009-04-15
Hi everybody. So SixA 0.1 is released as planned. But, yes there is a but.
We have got some issues with how to run sudo to change the bluetooth mode and other root needed privileges.

Because of this, SixA will not always show Jauntys new awesome notifications. But this is only when the command that is run is a (gk)sudo command. Otherwise the new notifications will be shown. But if you're not running Jaunty then you wont notice the difference.

And because of all of this SixA will be updated quite often. Hopefully a few times a day. But As of branch 23, SixA should run as it should. Se a video and more info on my homepage: [http://www.danielholm.se/video-sixa-action](http://www.danielholm.se/video-sixa-action)

Please report bugs and come up with ideas on our project page: [http://www.launchpad.net/gsixaxis](http://www.launchpad.net/gsixaxis)

Download 0.1: [http://www.danielholm.se/dropbox/SixA-0.1.tar.bz2](http://www.danielholm.se/dropbox/SixA-0.1.tar.bz2)
Latest branch:```
bzr branch lp:gsixaxis
```

Cheers!

---

### Post by falkTX on 2009-04-16
For those who don't care about GUI, I have made a deb package for the Command-Line 'sixa' (renamed 'sixaxis' to 'sixa').
This one fully works, but doesn't have GUI/Interface.

I'm learning python(-qt4) to help improving the GUI.
The new SixA version (0.2) will be available in less then 2 months

---

### Post by nagual on 2009-04-20
I have been trying to get this to work on ubuntu 8.10 and seem to be stuck.  Under /dev/input js0 shows up, the lights keep flashing until I click the turn off sixaxis controller, and dmesg shows the following.

```
[  751.798789] input: Sony Computer Entertainment Wireless Controller as /devices/pci0000:00/0000:00:02.0/usb1/1-4/1-4.1/1-4.1:1.0/bluetooth/hci0/hci0:7/input11
[  773.211363] input: PLAYSTATION(R)3 Controller as /devices/pci0000:00/0000:00:02.0/usb1/1-4/1-4.1/1-4.1:1.0/bluetooth/hci0/hci0:6/input12
[  915.746055] input: PLAYSTATION(R)3 Controller as /devices/pci0000:00/0000:00:02.0/usb1/1-4/1-4.1/1-4.1:1.0/bluetooth/hci0/hci0:7/input13

```

However when running jstest or jscalibrator, or an emulator nothing responds to buttons being pressed.  I have also tried rebooting and doesn't help.  

Thanks for any suggestions in advance.

---

### Post by Holmen on 2009-04-20
Yeah, that is some kind of bug. But the fix is quite easy, its just another step in the process. Download the latest branch and read the README file, its under 'Use SixA GUI'.

---

### Post by nagual on 2009-04-20
I tried your suggestion, however it still doesn't work.  js0 shows up, and the lights are flashing, just doesn't respond to any input from the controller.  I am going to try and upgrade to jaunty with a clean install to see if it helps at all.

---

### Post by Holmen on 2009-04-20
Try theese steps after the guide:
1. Reset bluetooth: File > Reset.
2. Press the connect button in the maintab.
3. Press the PS button on the gamepad. 

Or you could do it trough the terminal:
1. sixa -r
2. sixa -l
3. Press the PS button in the gamepad.

It this wont work, press the PS button on the gamepad until it stops twinkling instead or reseting the Bluetooth and then do the next steps.

---

### Post by Psyphre on 2009-04-21
Hi, i just want to say that this is a great project and looks very promising.

I tried to download the bzr sourc code but seem to fail trying to compile it.

When typing in 'make 1386' (i use 32bit) it get errors :(

```
cp ./bins/bluetoothd-service-input_i386 bluetoothd-service-input
cp ./bins/hcid_i386 hcid
gcc -o sixpair sixpair.c -lusb
sixpair.c:9:17: error: usb.h: No such file or directory
sixpair.c: In function ‘fatal’:
sixpair.c:17: warning: incompatible implicit declaration of built-in function ‘exit’
sixpair.c: At top level:
sixpair.c:19: error: expected ‘)’ before ‘*’ token
sixpair.c:30: error: expected ‘)’ before ‘*’ token
sixpair.c:44: warning: ‘struct usb_config_descriptor’ declared inside parameter list
sixpair.c:44: warning: its scope is only this definition or declaration, which is probably not what you want
sixpair.c:44: warning: ‘struct usb_device’ declared inside parameter list
sixpair.c: In function ‘process_device’:
sixpair.c:47: error: ‘usb_dev_handle’ undeclared (first use in this function)
sixpair.c:47: error: (Each undeclared identifier is reported only once
sixpair.c:47: error: for each function it appears in.)
sixpair.c:47: error: ‘devh’ undeclared (first use in this function)
sixpair.c:62: warning: incompatible implicit declaration of built-in function ‘exit’
sixpair.c:71: warning: incompatible implicit declaration of built-in function ‘exit’
sixpair.c: In function ‘main’:
sixpair.c:86: warning: initialization makes pointer from integer without a cast
sixpair.c:92: error: dereferencing pointer to incomplete type
sixpair.c:94: error: dereferencing pointer to incomplete type
sixpair.c:94: error: dereferencing pointer to incomplete type
sixpair.c:96: error: dereferencing pointer to incomplete type
sixpair.c:97: error: dereferencing pointer to incomplete type
sixpair.c:97: error: dereferencing pointer to incomplete type
sixpair.c:98: error: increment of pointer to unknown structure
sixpair.c:98: error: arithmetic on pointer to an incomplete type
sixpair.c:100: error: dereferencing pointer to incomplete type
sixpair.c:101: error: dereferencing pointer to incomplete type
sixpair.c:103: error: dereferencing pointer to incomplete type
sixpair.c:104: error: dereferencing pointer to incomplete type
sixpair.c:104: error: dereferencing pointer to incomplete type
sixpair.c:105: error: increment of pointer to unknown structure
sixpair.c:105: error: arithmetic on pointer to an incomplete type
sixpair.c:106: error: dereferencing pointer to incomplete type
sixpair.c:107: error: dereferencing pointer to incomplete type
sixpair.c:108: error: dereferencing pointer to incomplete type
sixpair.c:109: warning: passing argument 3 of ‘process_device’ from incompatible pointer type
sixpair.c:109: warning: passing argument 4 of ‘process_device’ from incompatible pointer type
make: *** [i386] Error 1

```

---

### Post by Holmen on 2009-04-22
Hi,

Thank you for your kind words!

Well first of all I hope that you meant 'make i386' and not 'make 1386'.
Secondly, do you have all nedded packages for building and compile?

I think that you need to install two main packages:
```
sudo apt-get install build-essential libusb-dev
```

You should then be ready to go ;)

---

### Post by Psyphre on 2009-04-22
> **Holmen said:**
> Hi,

Thank you for your kind words!

Well first of all I hope that you meant 'make i386' and not 'make 1386'.
Secondly, do you have all nedded packages for building and compile?

I think that you need to install two main packages:
```
sudo apt-get install build-essential libusb-dev
```

You should then be ready to go ;)

Yeh sorry i meant to type i386. It appears I didn't have libusb-dev so its installed now, thanks for the quick reply!

Unfortunately now I cant seem to pair the gamepad to my bluetooth :(
In step 2 of adding a gamepad it says to press the ps3 button and then ctrl+c when terminal logs it. Nothing happens though :(

---

### Post by Holmen on 2009-04-22
Yeah, I am aware of the bug regarding the pairing of the gamepad. I've written about it in the README file. Just let the gamepad try to connect a while and you should be good to go. Just wait a minute or so. The Gamepad will keep upp the twinkling.

---

### Post by Psyphre on 2009-04-22
> **Holmen said:**
> Yeah, I am aware of the bug regarding the pairing of the gamepad. I've written about it in the README file. Just let the gamepad try to connect a while and you should be good to go. Just wait a minute or so. The Gamepad will keep upp the twinkling.

Hi, thanks for the reply again.
Ive tried waiting a while (until the gamepad stops completely and turns it's lights off).

Ive tried pressing it 3 times, but still nothing happens :(

Just to outline exactly what I've done incase ive got something wrong:
1 - downloaded the bzr source code
2 - compiled and installed it (thanks to your help)
3 - Started sixaxis gui and clicked on 'add'
4 - Unplugged the ps3 so it doesnt turn on when i press the PS button.
5 - Pressed the PS button  on the game pad and waited.
6 - Repeated step 5 a few times  but still nothing happens.

---

### Post by falkTX on 2009-04-23
> **Psyphre said:**
> Hi, thanks for the reply again.
Ive tried waiting a while (until the gamepad stops completely and turns it's lights off).

Ive tried pressing it 3 times, but still nothing happens :(

Just to outline exactly what I've done incase ive got something wrong:
1 - downloaded the bzr source code
2 - compiled and installed it (thanks to your help)
3 - Started sixaxis gui and clicked on 'add'
4 - Unplugged the ps3 so it doesnt turn on when i press the PS button.
5 - Pressed the PS button  on the game pad and waited.
6 - Repeated step 5 a few times  but still nothing happens.

try the command-line version

---

### Post by Psyphre on 2009-04-23
Hi FalkTX.

I just tried it and I get this at step 2:

```
Please press the PS button (in your Sixaxis controller) now and then press Ctrl+C after the terminal logs Sixaxis information
sudo: hidd: command not found
hidd: no process killed
ed@ed-desktop:~$ 
```

It looks like thats not meant to happen?

---

### Post by falkTX on 2009-04-24
> **Psyphre said:**
> Hi FalkTX.

I just tried it and I get this at step 2:

```
Please press the PS button (in your Sixaxis controller) now and then press Ctrl+C after the terminal logs Sixaxis information
sudo: hidd: command not found
hidd: no process killed
ed@ed-desktop:~$ 
```

It looks like thats not meant to happen?

No, you didn't.
My bluez-sixa requires 'bluez-compat' that happens to have hidd. So, please install the package correctly

---

### Post by Psyphre on 2009-04-24
**falktx**: thanks, I installed bluez-compat but unfortunately stilll no go. I don't get that error anymore,  but (just like with the GUI) I keep waiting and pressing the ps button and nothing happens.

---

### Post by ravay on 2009-04-25
nagual said:
> I tried your suggestion, however it still doesn't work. js0 shows up, and the lights are flashing, just doesn't respond to any input from the controller. I am going to try and upgrade to jaunty with a clean install to see if it helps at all.

I'm facing the same problem. I'm running a fresh compiled version of sixa on Jaunty.

---

### Post by sephirothff on 2009-04-26
hello
i have a problem

i need to remove bluez-sixa , but after type command "apt-get remove bluez-sixa , i have error

> sub-process /usr/bin/dpkg returned an error code (1)

help me please

ps: sorry for my english , i am french

---

### Post by azquelt on 2009-04-26
> **sephirothff said:**
> hello
i have a problem

i need to remove bluez-sixa , but after type command "apt-get remove bluez-sixa , i have error

When reporting an error, it's better if you can include anything else in the output which might be related to the error. In this case I get:

```
Removing bluez-sixa ...
rm: cannot remove `/usr/lib/bluetooth/bluetoothd-service-input': No such file or directory
rm: cannot remove `/usr/sbin/hcid': No such file or directory
dpkg: error processing bluez-sixa (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 bluez-sixa
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

In this case, the problem is with the package, the post-removal script it trying to remove files which don't exist. You can get it to remove by doing
```
sudo touch /usr/lib/bluetooth/bluetoothd-service-input
sudo touch /usr/sbin/hcid
```
and then trying to remove bluex-sixa again.

---

### Post by falkTX on 2009-04-29
I'm going to be fully honest here:
I started a new rewrite, cause I just want to have the basic stuff implemented and I'm done. I'm a little busy taking care of other things, but I never forget you guys here.
The FINAL product should be SixA-NG, something that will really works without any problems. But, as I'm new to programing stuff, I/we need your help!

Making the CLI is easy to me, but the GUI is giving me some trouble. So, to get this project moving we need:
1 - PPA Repo (anyone familiar on making debs will be really nice)
2 - powerpc/sparc users (to pre-compile new/patched 'hidd')
3 - python-QT4 experts (I need some tips so I can finish the GUI)
4 - sourceforge (or any opensource code/web hosting) website [this one is not really hard, so don't bother about it]


I think that bluez4 should support josticks, as v3 did. Maybe we should help there instead of creating a specific app?
Please tell me what you guys think

---

### Post by Holmen on 2009-04-29
A rewrite is needed to compress the code. And as you previous said Filipe, it should just work.

1. The only thing we need is how to make .asc and orginal.tar.bz2 files
2. If we would go for a patched bluez-utils, we should provide this from our PPA.
3. I'm still a GTK+ freak - but sure, go ahead ;)
4. I'm working on a homepage.

But I do not think that there should be a SixA-NG. SixA 0.2 is good enough.
The codename is after the author of Mario - Miyamoto.

And I also thin that we should support BlueZ in this matter and make SixA into a clean GUI for handling gamepad/joysticks-profiles and settings. Then the PS3 gamepad could have a plugin to enable batterystatus, tilt-function and stuff.

By the way - if you use Blueman instead of Bluez-Gnome, you can use the gamepad and other Bluetooth devices as usual.

---

### Post by Psyphre on 2009-04-29
Well I think its a great idea, and I'm thankful theres someone like you writing a great app like this. Unfortunately the current Six-A doesnt work for me, but hopefully the re-write will.

I wish I was able to help but I know nothing about coding :(

---

### Post by Holmen on 2009-04-29
Haha, neither do (did) we. You could start with reporting bugs, creating Blueprints and translate SixA into your native language. All this on our project page: [https://edge.launchpad.net/gsixaxis](https://edge.launchpad.net/gsixaxis)

And thank you for your kind words.

---

### Post by falkTX on 2009-04-30
Trying to keep things simple I created a very small script for connecting Sixaxis - Please test it!

Instead of a complicated & long script, this one only has 'start', 'disconnect', and 'restore'.
Just open a terminal and do
```
sixa start
```
It will start hidd server and tells you to press the PS button; once you did, just press the Enter key.
It may not work fine (that's why I need you to test).

This uses (when available) pacthed hidd (so far, only compiled to amd64), but once I get pre-compiled 'hidd's, it may just work out of the box for all architectures.
If you have an Ubuntu-PC other than 32 or 64bit, PLEASE tell me!

To test, please remove all other DEBs related to sixa/sixaxis (not necessary if files were installed manually).

---

### Post by Psyphre on 2009-05-02
> **Holmen said:**
> Haha, neither do (did) we. You could start with reporting bugs, creating Blueprints and translate SixA into your native language. All this on our project page: [https://edge.launchpad.net/gsixaxis](https://edge.launchpad.net/gsixaxis)

And thank you for your kind words.

Whats blueprints? 
I can try translating.


> **falkTX said:**
> Trying to keep things simple I created a very small script for connecting Sixaxis - Please test it!

Instead of a complicated & long script, this one only has 'start', 'disconnect', and 'restore'.
Just open a terminal and do
```
sixa start
```
It will start hidd server and tells you to press the PS button; once you did, just press the Enter key.
It may not work fine (that's why I need you to test).

This uses (when available) pacthed hidd (so far, only compiled to amd64), but once I get pre-compiled 'hidd's, it may just work out of the box for all architectures.
If you have an Ubuntu-PC other than 32 or 64bit, PLEASE tell me!

To test, please remove all other DEBs related to sixa/sixaxis (not necessary if files were installed manually).

Are these debs ok for jaunty (64 bit)? I just installed jaunty yesterday.

---

### Post by Holmen on 2009-05-03
Blueprints are features that the user might want us to implant into the application. It could also be ideas of new things or improvements.

But I think that you could skip the translation for the moment. Wait until SixA 0.2, which will have a better way to change translation depending on the users settings.

---

### Post by Psyphre on 2009-05-03
ah right so you mean like brainstorming ideas?

---

### Post by Holmen on 2009-05-03
Yeah, I suppose you could say that ;)

---

### Post by falkTX on 2009-05-04
> **Psyphre said:**
> 
Are these debs ok for jaunty (64 bit)? I just installed jaunty yesterday.

Yes, Jaunty and Intrepid

---

### Post by vapor0 on 2009-05-04
The only way I was able to get this working on AMD64 Jaunty was to follow this tutorial first:
[http://www.wiredrevolution.com/ubuntu/setup-ps3-controller-over-bluetooth-on-ubuntu](http://www.wiredrevolution.com/ubuntu/setup-ps3-controller-over-bluetooth-on-ubuntu)
Including the part where you compile and install your own patched bluez-compat. 
Then I was able to use this package, and it worked flawlessly. 
Thanks!

---

### Post by falkTX on 2009-05-05
> **vapor0 said:**
> The only way I was able to get this working on AMD64 Jaunty was to follow this tutorial first:
[http://www.wiredrevolution.com/ubuntu/setup-ps3-controller-over-bluetooth-on-ubuntu](http://www.wiredrevolution.com/ubuntu/setup-ps3-controller-over-bluetooth-on-ubuntu)
Including the part where you compile and install your own patched bluez-compat. 
Then I was able to use this package, and it worked flawlessly. 
Thanks!

That's what I used for my little package. I think we should start using pre-compiled & patched 'hidd'.
On my package it just starts this hidd (if detected), ask user to press PS button then OK/Enter and then it restores bluetooth. It still done on terminal, but for a very simple thing as this, a GUI doesn't make much sense

---

### Post by Holmen on 2009-05-05
I agree that it would be easier if the user just would do that part in a terminal, but they should have a choice if they rather would like a GUI.

By the way, SixA 0.2 is under development.

---

### Post by falkTX on 2009-05-05
> **Holmen said:**
> I agree that it would be easier if the user just would do that part in a terminal, but they should have a choice if they rather would like a GUI.
Of course, I agree.
It's just... 'sixa start' is not that complicated.

Good to see your still working on the GUI. My QT port is stuck; I have no idea how to do some things, so I have o let all the GUI stuff to you (sorry!).

The next thing we need is pre-compiled 'hidd's for different ARCHs. I have my amd64, can you compile the patched hidd for i386? And we'll we do for other archs?

---

### Post by Holmen on 2009-05-05
> **falkTX said:**
> Of course, I agree.
It's just... 'sixa start' is not that complicated.

Good to see your still working on the GUI. My QT port is stuck; I have no idea how to do some things, so I have o let all the GUI stuff to you (sorry!).

The next thing we need is pre-compiled 'hidd's for different ARCHs. I have my amd64, can you compile the patched hidd for i386? And we'll we do for other archs?

Exactly.

It's ok. I will do a GTK+ version first, and then perhaps create a QT version. I just have to read a lot about it and I just did that regarding GTK and like to use it for a while. (QT developers are welcome to join).

Sure I can build a package for i386, but we have to start using our PPA. Then we wont have to build our packages anymore. The only thing we need is learn how to create .dsc-files.

By the way: You all out there, we need your help. Now when SixA 0.2 is under active development - we need translators. Come with ideas for new features and ideas. Help develop the application. Look for bugs and report them. You can to all this on our project page on Launchpad: [http://www.launchpad.net/gsixaxis](http://www.launchpad.net/gsixaxis)

Also, we might need a new icon. Come on guys and send one to us. Create one with the resolution of 192x192 in a PNG format.
It has to resolve to the category to the app. Perhaps a retro gamepad/joystick.

Cheers!

---

### Post by vapor0 on 2009-05-07
The "Gnome" controller setting works pretty good for games such as Nexuiz and Sauerbraten - only the two axis are reversed. You have to stop using the d-pad and use the left stick with your left hand to look around.

Is there an easy way to change the configuration settings so that I could have the Gnome setup but with the two sticks "switched"? Or even a "PS3-style" layout? It must be possible, I just don't know how.:guitar:

---

### Post by Holmen on 2009-05-07
It is indeed possible. The profile files is under /usr/share/bluez-sixa/profiles/
The thing is that you have to manually add some lines to the basic sixa binary to add new profiles, but you can still use thoose that is from the start.

This will one of the main features in SixA 0.2 and it will also support to create some good-looking profiles graphicly.

We would really eppricitate if you would create profiles for your favorite games and apps to distribute them with SixA from start.

SixA Profile Example:
[http://dl.getdropbox.com/u/284076/sixa-profile-example.fdi](http://dl.getdropbox.com/u/284076/sixa-profile-example.fdi)

PS. Homepage on its way!

---

### Post by vapor0 on 2009-05-07
Sorry, I am using the GUI version of the program. I have cannibalised the different "use as mouse/keyboard" configurations to make my own .fdi, and have managed to get so far as to make the sticks work correctly in Nexuiz, so that one can move with the left and look with the right.

But, in doing so, I have lost the ability to switch weapons. This used to be the right stick in the Gnome configuration, which scrolled. I am trying to find a way to make either the top buttons or the D-Pad work as up/down scroll, so that at least I will have basic functionality in Nexuiz.

I just wish there was a layout I could use that mapped the buttons for the sixaxis to the default PS3 controls. I have a lot of games and emulators I would like to use this on. There must be some kind of standard config that could be made, and I'm willing to help if someone can point me in the right direction.

Thanks.

---

### Post by Psyphre on 2009-05-08
> **falkTX said:**
> Trying to keep things simple I created a very small script for connecting Sixaxis - Please test it!

Instead of a complicated & long script, this one only has 'start', 'disconnect', and 'restore'.
Just open a terminal and do
```
sixa start
```
It will start hidd server and tells you to press the PS button; once you did, just press the Enter key.
It may not work fine (that's why I need you to test).

This uses (when available) pacthed hidd (so far, only compiled to amd64), but once I get pre-compiled 'hidd's, it may just work out of the box for all architectures.
If you have an Ubuntu-PC other than 32 or 64bit, PLEASE tell me!

To test, please remove all other DEBs related to sixa/sixaxis (not necessary if files were installed manually).

Hi, tested the deb 10 mins ago. No luck im afraid, just like the GUI version it sits there and cant detect the ps3 controller.

Ive noticed it also cuts out my wifi temporarily shortly after I press the PS button. Wierd.


Using jaunty 64bit.
Everything says 'ok' at start.

---

### Post by vapor0 on 2009-05-08
Psyphre

Follow the link that I posted at the top of this page, and follow the instructions. Sixaxis-gui should then work.

I'm pretty sure I followed every tutorial on the Internets, but that's the only thing that worked for me.

---

### Post by Holmen on 2009-05-09
> **vapor0 said:**
> Sorry, I am using the GUI version of the program. I have cannibalised the different "use as mouse/keyboard" configurations to make my own .fdi, and have managed to get so far as to make the sticks work correctly in Nexuiz, so that one can move with the left and look with the right.

But, in doing so, I have lost the ability to switch weapons. This used to be the right stick in the Gnome configuration, which scrolled. I am trying to find a way to make either the top buttons or the D-Pad work as up/down scroll, so that at least I will have basic functionality in Nexuiz.

I just wish there was a layout I could use that mapped the buttons for the sixaxis to the default PS3 controls. I have a lot of games and emulators I would like to use this on. There must be some kind of standard config that could be made, and I'm willing to help if someone can point me in the right direction.

Thanks.

If you do not load a profile, you can use the gamepad as a regular joystick in emulators to map keys and so on. But we should perhaps create a general FPS-profile?

Psyphre, does your Bluetooth work with other Bluetooth-devices?

---

### Post by Psyphre on 2009-05-09
> **vapor0 said:**
> Psyphre

Follow the link that I posted at the top of this page, and follow the instructions. Sixaxis-gui should then work.

I'm pretty sure I followed every tutorial on the Internets, but that's the only thing that worked for me.


Will give it a go as a last resort cos Im afraid i might change things that make bugs/testing harder to narrow down. Correct me if I'm wrong please. thanks.


> **Holmen said:**
> If you do not load a profile, you can use the gamepad as a regular joystick in emulators to map keys and so on. But we should perhaps create a general FPS-profile?

Psyphre, does your Bluetooth work with other Bluetooth-devices?


Yes it does, I use it with my mobile phone.
Do I have to unpair my ps3 controller or something first? Ive turned off the ps3 (unplugged) so it doesnt turn on when I press the PS button. I thought that would  be enough but I could be wrong.

---

### Post by halfsoul on 2009-05-09
> **Psyphre said:**
> Do I have to unpair my ps3 controller or something first? Ive turned off the ps3 (unplugged) so it doesnt turn on when I press the PS button. I thought that would  be enough but I could be wrong.

I'll leave it to the developers to say for sure, but supposedly the sixaxis has a different pairing scheme than standard bluetooth (notice you never have to type a PIN or anything).  It's all done over USB (which, in my opinion, is more secure than a PIN anyway since it has to be physically connected).  Anyway, follow the USB Pairing section on this page:
[https://help.ubuntu.com/community/Sixaxis](https://help.ubuntu.com/community/Sixaxis)

---

### Post by Psyphre on 2009-05-12
Thanks for the tip, I actually never tried it over USB! I thought it was all done wirelessly thru bluetooth. MAybe thats where I was going wrong.

I wish I could try it out but my motherboard decided to die last night. So I'll have to get it repaired/replaced which will take a while :(

---

### Post by Holmen on 2009-05-12
> **Psyphre said:**
> Thanks for the tip, I actually never tried it over USB! I thought it was all done wirelessly thru bluetooth. MAybe thats where I was going wrong.

I wish I could try it out but my motherboard decided to die last night. So I'll have to get it repaired/replaced which will take a while :(

Bummer! Hopefully SixA 0.2 will be release untill then!

---

### Post by jordan420 on 2009-05-14
hey guys sorry to post.  but i cant seem to get it to appear as a joystick in /dev...  it shows up in the sixa cli though. is there something im missing?

---

### Post by Holmen on 2009-05-16
Have you followed the install-steps? The new site is under construction, but I added the instructions to it: [http://sixa.danielholm.se/help](http://sixa.danielholm.se/help)

---

### Post by vapor0 on 2009-05-26
So does anyone know how to make it so that the D-pad switches weapons?

---

### Post by Holmen on 2009-05-27
If you change weapons by scrolling, you can set a button on the gamepad to act as the scroll. Otherwise if you can set (in them game) that you want to change weapons forward and backward by one set of buttons, you can set thoose buttons in the profile.

Stay with us, SixA 0.2 will soon be released.

---

### Post by vapor0 on 2009-05-30
If anybody is like me, and are still using the old sixaxis-gui program, and would like a mouse/keyboard setup for KXmame with SDLmame, I made a controller configuration with buttons and joysticks setup for MAME (1 player/2 player), that also works as a mouse in Gnome, with no conflicts.

Overwrite /var/games/sdlmame/cfg/default.cfg,  /usr/share/bluez-sixaxis/sixaxis_wormux.fdi and /usr/share/bluez-sixaxis/sixaxis-wormux.png with the attached files, and you're done! You just have to switch to "wormux" in the "Connect as keyboard/mouse" dialogue.

---

### Post by Holmen on 2009-05-30
Hi,

That is lovely! Thank you for your contribution - Your profile will be in SixA 0.2.

---

### Post by zack77 on 2009-06-01
Good work guys, works like a charm in Ubuntu/Kubuntu 9.04 after I found out that xserver-xorg-input-joystick was needed to get things working.

I've made an custom fdi for XBMC, see attached file.

One question thought, how can I map plus (+) and minus (-) signs in the fdi ? 

This is the default keys for volume up and down in XBMC, I managed to make an own map with 9 and 0 for volume in XBMC Keymap.xml.
But I rather send + and - from the sixaxis instead so others do not need to change Keymap.xml. 
Did not figure out how to map backslash either, which toggles full-screen mode in XBMC.

Tried several combinations for -/+ without luck, does anyone have successful maps for those keys ?

NB! You have to overwrite this file with one of the other .fdi files in /usr/share/bluez-sixaxis/, since the code don't include custom .fdi's

Thanks

---

### Post by Holmen on 2009-06-02
Thank you! Another profile to add to SixA 0.2.

Run this command and look for the keys you need and use ither one of thoose keysums:
```
xmodmap -pke
```

---

### Post by zack77 on 2009-06-02
Thanks, much easier now instead of guessing :)
Of course I did try to use Minus and Plus with capital letters like BackSpace. But it just had to be all lowercase (minus & plus)

Se attached fdi file for standard XBMC keys now instead of custom.

Thank you very much

---

### Post by Holmen on 2009-06-02
Awesome! Your profile is now in SixA 0.2 (Im coding on it just as we speak).

---

### Post by falkTX on 2009-06-02
I hope you guys haven't forgot about me...

Anyway, as I just started learning python (pyQt), I made a quick GUI.
It's very basic but works. 

The bluez-sixa packages comes bundles with patched 'hidd's for both 32 and 64-bit Ubuntu. sparc and powerpc will not work with these.
This means no pairing is needed, just click on "Start".

To launch the GUI, run 'sixa-gui'

See ya soon

*Edit: XMBC profile is already there.*
*Edit2: I confused XMBC with XBMC, so that profile won't work with my GUI yet*

---

### Post by blakemcclaren on 2009-06-06
Anyone know how to make this work on the PS3 itself?  I need a ppc version, and would it still require a bluetooth device separate from the one built into the Ps3?
v 9.04

-thanks

---

### Post by halfsoul on 2009-06-08
> **blakemcclaren said:**
> Anyone know how to make this work on the PS3 itself?  I need a ppc version, and would it still require a bluetooth device separate from the one built into the Ps3?
v 9.04

-thanks
I'm not sure about the current development versions, but the original version should work with the built-in bluetooth module as long as you're not using Xubuntu (although that may be fixed in 9.04).  The only other "trick" is to pair it with the USB cable.

---

### Post by falkTX on 2009-06-08
> **blakemcclaren said:**
> Anyone know how to make this work on the PS3 itself?  I need a ppc version, and would it still require a bluetooth device separate from the one built into the Ps3?
v 9.04

-thanks

Do you have a PS3-ubuntu?
If yes, then you can help us making it work on ppc. Please PM me if interested.

Edit: It doesn't require an extra bluetooth device/stick/usb thing. But you'll still have to unpair the Sixaxis first

---

### Post by halfsoul on 2009-06-08
> **falkTX said:**
> It doesn't require an extra bluetooth device/stick/usb thing. But you'll still have to unpair the Sixaxis first

falk, it is not possible to simply "unpair" the sixaxis with the PS3.  It HAS to be done by creating a new pair via USB.

---

### Post by falkTX on 2009-06-09
> **halfsoul said:**
> falk, it is not possible to simply "unpair" the sixaxis with the PS3.  It HAS to be done by creating a new pair via USB.

I only used a PS3 once (for testing), and all I can say is - when you press the PS button on a Sixaxis, if it turns on "1", "2", "3" or "4" led, that means it's still paired with the PS3. Once it just blinks (no 1,2,3,4 led always on), that means it's ready for use in a PC.

Anyway, I'm reading the PPA creation stuff right now, so maybe we'll got a powerpc compatible package soon

---

### Post by falkTX on 2009-06-09
The repo is coming!

[http://falktx.xtreemhost.com/](http://falktx.xtreemhost.com/)

---

### Post by falkTX on 2009-06-12
The Repository is ready for testing!

```
deb http://falktx.xtreemhost.com/repo/ubuntu jaunty main
```

It contains the packages *bluez-sixa* and *sixa*.
I included a pre-compiled powerpc hidd that I got from the psubuntu forums (not sure if it will work).
The XBMC profile is fixed and I've added a new one - Super Maryo chronicles.


Note: The repo is treated as untrusted, I'll try to fix that soon

---

### Post by falkTX on 2009-06-12
There's seem to be a problem downloading the *bluez-sixa* package. In any case, I upload that here (attachments)

---

### Post by falkTX on 2009-06-14
I've updated the repository

It now will install all packages without problems (I think), and there are some new stuff you will like. Just update and see.

The repo it's still untrusted. Someone who knows a solution please tell me.

---

### Post by falkTX on 2009-06-15
I know this is working for me.

But PLEASE report how it's working for you guys.
Thank you

---

### Post by marganis on 2009-06-15
hey mate, im sorry youve probably got this question a million times but  I can get the first bin file installed but when I try to install the rc11 I get this 

Error: Dependency is not satisfiable: xserrver-xorg-input-joystick
how do i get it to work??

when i installed ubuntu, my establishing a link with my wireless router didnt work. is it because of this it couldnt be working? if so how do i re config my internet settings for it. i have my ip and all the other details, just cant seem to figure out how to do it. sorry i very new to linux.

---

### Post by falkTX on 2009-06-15
> **marganis said:**
> hey mate, im sorry youve probably got this question a million times but  I can get the first bin file installed but when I try to install the rc11 I get this 

Error: Dependency is not satisfiable: xserrver-xorg-input-joystick
how do i get it to work??

when i installed ubuntu, my establishing a link with my wireless router didnt work. is it because of this it couldnt be working? if so how do i re config my internet settings for it. i have my ip and all the other details, just cant seem to figure out how to do it. sorry i very new to linux.

First of all, it seems you're using an old version of my app... (I should probably create a new thread for this...)

Because you're new to Linux, please go to the "Newbie Help" on the main page of the Ubuntu Forums. My app is "only" installable if you have net access (that is why it asks on a xserver...joystick thing that you don't have access to 'cause there's no network to get it)

---

### Post by marganis on 2009-06-17
hey, i know its not directly related to this topic, but im having trouble syncing my controller to the snes9x program which i guess heaps of you use on the ps3. i have my controller working on ubuntu and have changed the output to /dev/input/js0, i also changed the code in the snes9x.conf  file but when i use my controller to load up a game that requires start such as mario, but instead of working, the start button affects bg# , X button affects frame effects and so forth, what should i do? have i edited the file wrong if so could you post up the full code and i can just cut and paste it. im really sorry about all the questions im just so close to having all my linux stuff done on my ps3 this is the last thing and it doing my head in lol.

---

### Post by falkTX on 2009-06-17
> **marganis said:**
> hey, i know its not directly related to this topic, but im having trouble syncing my controller to the snes9x program which i guess heaps of you use on the ps3. i have my controller working on ubuntu and have changed the output to /dev/input/js0, i also changed the code in the snes9x.conf  file but when i use my controller to load up a game that requires start such as mario, but instead of working, the start button affects bg# , X button affects frame effects and so forth, what should i do? have i edited the file wrong if so could you post up the full code and i can just cut and paste it. im really sorry about all the questions im just so close to having all my linux stuff done on my ps3 this is the last thing and it doing my head in lol.

Try using my repo. Install the package 'sixa'; then on the GUI, unselect the option "Use sixaxis as mouse/keyboard" and click apply.
I'm guessing that your joystick is also working as keyboard when you press some buttons (like if you press X, it will simulate "F4").

---

### Post by falkTX on 2009-06-17
Some users seems to have installed the previous version of my app...
And I guess that uploading different versions of a program in the same thread can be confusing.

So, new thread:
[http://ubuntuforums.org/showthread.php?p=7472939](http://ubuntuforums.org/showthread.php?p=7472939)

_Please continue the conversation there_

---

### Post by fummo on 2010-01-19
This is great FalkTX, thank you very much.

---

