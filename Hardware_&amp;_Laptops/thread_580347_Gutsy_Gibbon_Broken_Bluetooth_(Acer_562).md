---
title: "Gutsy Gibbon Broken Bluetooth (Acer 562)"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by shrinkpad on 2007-10-18
EDIT: Acer 5620 travelmate.

Everything was looking good after the upgrade, but just noted bluetooth is not working;

$ sudo /etc/init.d/bluetooth start
 * Starting Bluetooth services                                           [ OK ] 

$ dmesg | grep Bluetooth
[   51.404000] Bluetooth: Core ver 2.11
[   51.404000] Bluetooth: HCI device and connection manager initialized
[   51.404000] Bluetooth: HCI socket layer initialized
[   51.572000] Bluetooth: L2CAP ver 2.8
[   51.572000] Bluetooth: L2CAP socket layer initialized
[   51.728000] Bluetooth: RFCOMM socket layer initialized
[   51.728000] Bluetooth: RFCOMM TTY layer initialized
[   51.728000] Bluetooth: RFCOMM ver 1.8
[  356.992000] Bluetooth: BNEP (Ethernet Emulation) ver 1.2
[  356.992000] Bluetooth: BNEP filters: protocol multicast
[  615.812000] Bluetooth: HIDP (Human Interface Emulation) ver 1.2

$ hcitool dev
Devices:

$ hcitool scan
Device is not available: No such device

---

### Post by cogitordi on 2007-10-21
Following your steps on my T40 Thinkpad, I have success but cannot browse devices or transfer files. 

The Browse action reports:
"obex://[00:20:e0:4a:19:53]" is not a valid location.

Yet I can see the other BT devices in my office.

I don't care about browsing, but I do care about transferring files. This worked in Feisty Fawn.

---

### Post by teh'p3nsi0n3r on 2007-10-21
> **cogitordi said:**
> Following your steps on my T40 Thinkpad, I have success but cannot browse devices or transfer files. 

The Browse action reports:
"obex://[00:20:e0:4a:19:53]" is not a valid location.

Yet I can see the other BT devices in my office.

I don't care about browsing, but I do care about transferring files. This worked in Feisty Fawn.

yep im having this same issue. :(

---

### Post by toMeloos on 2007-10-21
Me too on an IBM ThinkPad T43. I can browse devices and see my phone, but get the same obex is not a valid location error. I cannot get the phone to see the computer.

Guess this is not a hardware-related problem, but a gutsy configuration problem. I'm running a clean Gutsy installation (=not a Feisty upgrade). Maybe I've got to install additional packages?

---

### Post by teh'p3nsi0n3r on 2007-10-21
i was able to now recieve files by installing "bluetooth file sharing" program from the respos / add/remove, but i still cannot browse my phone.

---

### Post by talent03 on 2007-10-23
I am having the same issue here. I have not been able to solve it. Browse finds my devices but I get the same obex is not a valid location. I hope they fix this.

---

### Post by tassoman on 2007-10-24
You must register the obex:// protocol to be opened with some kind of progr. But i dunno how/what

---

### Post by cogitordi on 2007-10-25
> **tassoman said:**
> You must register the obex:// protocol to be opened with some kind of progr. But i dunno how/what

I don't understand what the default Bluetooth utility is supposed to do. Why is it incomplete?

I installed the Gnome-Bluetooth package (as I've done before) and can do what I need to do by activating Bluetooth Filesharing from Applications>Accessories.

---

### Post by ouellettesr on 2007-10-25
Install: 

sudo apt-get install gnome-vfs-obexftp

Im not on an acer 562, so I think this applies to everyone. Hope this helps. Let me know.

---

### Post by tassoman on 2007-10-25
:guitar: Rock 'n roll !

---

### Post by varkey on 2007-10-28
> **ouellettesr said:**
> Install: 

sudo apt-get install gnome-vfs-obexftp

Im not on an acer 562, so I think this applies to everyone. Hope this helps. Let me know.


Thank you so much!!!!! :):):):):):)

---

### Post by toMeloos on 2007-10-29
> nstall:

sudo apt-get install gnome-vfs-obexftp

Im not on an acer 562, so I think this applies to everyone. Hope this helps. Let me know.

Doesn't seem to solve it for me.

---

### Post by camini on 2007-10-30
Great - works for me too.

---

### Post by cogitordi on 2007-11-02
Not only does it work, but it works better than the Bluetooth functionality in MS Windows and OS X. I can browse my Nokia mobile telephone with no problems. 

I am liking Gutsy Gibbon more and more.

---

### Post by gillis on 2007-11-04
> **ouellettesr said:**
> Install: 

sudo apt-get install gnome-vfs-obexftp

Im not on an acer 562, so I think this applies to everyone. Hope this helps. Let me know.


well instead of having 'is not a valid connection'  i get ' could display obex .............. check if the service is available"

---

### Post by tombott on 2007-11-06
> **ouellettesr said:**
> Install: 

sudo apt-get install gnome-vfs-obexftp

Im not on an acer 562, so I think this applies to everyone. Hope this helps. Let me know.

Cheers mate.

This fixed the issue on my Acer Aspire 9500, am now able to browse my phone without any isuees.

---

### Post by shrinkpad on 2007-11-08
Am I missing something still?

luke@luke-laptop:~/boxes$ sudo apt-get install gnome-vfs-obexftp
[sudo] password for luke:
Sorry, try again.
[sudo] password for luke:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libopenobex1
The following NEW packages will be installed
  gnome-vfs-obexftp libopenobex1
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 70.1kB of archives.
After unpacking 250kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main libopenobex1 1.3-3ubuntu1 [21.3kB]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe gnome-vfs-obexftp 0.4-1 [48.8kB]
Fetched 70.1kB in 0s (269kB/s)          
Selecting previously deselected package libopenobex1.
(Reading database ... 144058 files and directories currently installed.)
Unpacking libopenobex1 (from .../libopenobex1_1.3-3ubuntu1_i386.deb) ...
Selecting previously deselected package gnome-vfs-obexftp.
Unpacking gnome-vfs-obexftp (from .../gnome-vfs-obexftp_0.4-1_i386.deb) ...
Setting up libopenobex1 (1.3-3ubuntu1) ...

Setting up gnome-vfs-obexftp (0.4-1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
luke@luke-laptop:~/boxes$ sudo /etc/init.d/bluetooth restart
 * Restarting Bluetooth services  

luke@luke-laptop:~/boxes$ hcitool dev
Devices:
luke@luke-laptop:~/boxes$ hcitool scan
Device is not available: No such device

---

### Post by jasnils on 2007-11-14
> **ouellettesr said:**
> Install: 

sudo apt-get install gnome-vfs-obexftp

Im not on an acer 562, so I think this applies to everyone. Hope this helps. Let me know.

You're the Man, this works on my Dell Latitude X1 with gutsy gibbon.

THX.

---

### Post by 4leite on 2007-11-21
cheers, this fixed it for me too

---

### Post by tungsai on 2007-11-30
Hi All! Here's MY situation:

I have an IBM Thinkpad X60s, Nokia 6126, Bluetooth-enabled Cell, and a Logitech Bluetooth Mouse, model M-RBB93.

The mouse has never connected up properly. :( I gave up on it for a while. Then I tried the Phone OBEX stuff; and encountered the error mentioned here. I ran the apt-get install fix; and it WORKED! However, like the previous person, when now trying to sync up the mouse, I get the "Couldn't display OBEX://[xx:xx:xx:xx:xx:xx]". Check if the service is available." 

Maybe I'm not doing it right?

Tung Sai

[www.tungsai.com](www.tungsai.com)

---

### Post by nilgiri on 2007-12-02
I had the same problem and according to a [Fedora post]("http://forum.fedoraforum.org/showthread.php?p=908776") I found, it is just bug that particular UI. For now, > Right-click on the bluetooth applet and select "Preferences", go to the "Services" tab, left-click on "Input service", click the "Add" button, select your input device & connect.

Now, if I could just get my brand new HP 6715b laptop to stop black-screen-freezing up when I use bluetooth or my USB 2.0 HUB, I'd be all set.  But that is off topic here. =)

---

### Post by awnishUpadhyay on 2007-12-07
[QUOTE=nilgiri;3880926]I had the same problem and according to a [Fedora post]("http://forum.fedoraforum.org/showthread.php?p=908776") I found, it is just bug that particular UI. For now, 

....

hello i can connect to bluettoth phones using my portable by all the setups and connections mentioned in this thread...but my problem is that the bluettoth connection gets lost after almost every 20 sec of connection...plz if some one can help..i m new to linux ubuntu and m really enjoying using linux..and this is my 1st task....if some body can plz help mee.....will appreciate ur help guys...
[email]awnishupadhyay@gmail.com[/email]....

---

### Post by nyroshan on 2007-12-27
I've tried all of these solutions and I still get the couldn't display location obex:/// etc.
Has anyone found any other solution for this?

---

### Post by FRuMMaGe on 2008-01-02
This is incredibly annoying.

I was fully able to access my phone through gnome-vfs-obexftp. Then 5 minutes later, it stopped working.

I done nothing and it stopped working.

WTF is going on!

---

### Post by seesoe on 2008-01-02
i've gone through the whole thread with all the suggested fix but i still get the same
obex:/// error for some reason

---

### Post by thetictacaddict on 2008-01-03
Also getting the error here.  It changed to 
```
Couldn't display "obex://[...]".
Check if the service is available.
```
after I installed gnome-vfs-obexftp, but I still can't connect.  I've had this problem on two different computers.  On one I was trying to connect to a mouse, now I'm trying to connect to a phone but the error is the same.

---

### Post by nickthecook on 2008-01-04
I have the same problem trying to pair a bluetooth headset/headphones.

Just for fun I tried adding it as an input device in the preferences for the bluetooth app, and it worked, but it is not an input device, so that won't allow me to use it.

```
Couldn't display "obex://[00:XX:XX:XX:XX:XX]".
Check if the service is available.
```

I do have gnome-vfs-obexftp installed, and it works well with my phone.

I would like to say that overall I'm very impressed with how well bluetooth has worked for me in Gutsy (especially coming from gentoo :) ). This is the first thing that hasn't worked out-of-the-box, and I've thrown phones, other headsets, and wiimotes at it.

---

### Post by nickthecook on 2008-01-05
Turns out that, for myself at least, the device connected in spite of the error message. It seems as if attempting to browse the device in nautilus is just a default action when a new device is connected, but of course by device (headphones/headset) probably does not support obexftp.

I followed the instructions on this page:

[http://wiki.bluez.org/wiki/HOWTO/AudioDevices](http://wiki.bluez.org/wiki/HOWTO/AudioDevices)

...and now I can switch between my internal speakers and my bluetooth headphones with a command. Naturally, I wrote a script to toggle the audio output device in gnome, and bound a laptop button to it. :)

So as for the 'Couldn't display "obex://[00:XX:XX:XX:XX:XX]".' message, if you're trying to browse a device's filesystem through bluetooth, it's a problem, but otherwise, try ignoring it.

---

### Post by Yogiz on 2008-01-06
The same problem seems to be bugging me. I installed Ubuntu Gutsy just yesterday (being a Slackware user) and bluetooth worked just fine. I also installed opensync 0.35 with a bunch of plugins and everything still worked. Now it doesn't. I get the aformentioned 'Couldn't display "obex://[MAC]... check if the service is running' error with bluetooth applet but what bothers me most is that obex is not working, even after I reinstalled all the packages. Opensync gives errors but even the simplest things don't work.

Obexftp:
```
sander@gabriel:~$ obexftp -b $MAC -l /
Browsing $MAC ...
Channel: 6
Connecting...failed: connect
Still trying to connect
Connecting...failed: connect
Still trying to connect
Connecting...failed: connect
Still trying to connect
```

I haven't been able to fix it yet and I have no idea what's frong as it worked just fine before. If I can get my cell to sync fine here I might just stick to gutsy for now.

(I have to say though, synaptic makes you lazy : ).)

---

### Post by dm1024 on 2008-01-06
Well, I got success in browsing my wife's samsung e530 using obextool. On any folder listing it requires confirmation, but anyway...
But I still get ugly "Couldn't display" message using Bluetooth Manager's Browse Device.

---

### Post by glittalogik on 2008-01-07
I got the same error until I added my phone (Sony Ericsson k750i) to the 'bonded devices' list in my bluetooth preferences. Now it's all cool =)

---

### Post by Yogiz on 2008-01-08
Here's the thing, now it works again, everything- obexftp, opensync, the gnome applet. The thing is, I didn't change anything in between. It is a mystery.

---

### Post by johnnypy on 2008-01-10
I am getting exactly the same problem, with a bluetooth keyboard. Same obex error change etc. I can connect to the keyboard using hidd but the connection can't be sustained after reboot even using the edit to the bluetooth configuration file. i am using GG 7.10 - just loaded today. Im new to linux and to ubuntu

Can anyone help? I am using a logitech mediaboard pro

---

### Post by DenverDamon on 2008-01-10
Hello...first time Ubuntu user here so please forgive ignorance....

I've tried the:sudo apt-get install gnome-vfs-obexftp commend and I get the following...

damon@damon-laptop:~$ sudo apt-get install gnome-vfs-obexftp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnome-vfs-obexftp
damon@damon-laptop:~$ 

Any idea why it's not working??
I have an internet connection that's functioning properly...

Thanks
Damon

---

### Post by ls8 on 2008-01-14
> **nilgiri said:**
> Right-click on the bluetooth applet and select "Preferences", go to the "Services" tab, left-click on "Input service", click the "Add" button, select your input device & connect.

Thanks, it works on Lenovo 3000 V100 laptop with Logitech v270 bluetooth mouse :)

---

### Post by ups on 2008-01-20
> **DenverDamon said:**
> Hello...first time Ubuntu user here so please forgive ignorance....

I've tried the:sudo apt-get install gnome-vfs-obexftp commend and I get the following...

damon@damon-laptop:~$ sudo apt-get install gnome-vfs-obexftp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnome-vfs-obexftp
damon@damon-laptop:~$ 

Any idea why it's not working??
I have an internet connection that's functioning properly...

Thanks
DamonYou need to enable Universe (System > Admin > Software Sources - make sure universe component is checked here).

---

### Post by geoffatmk on 2008-01-26
Hi

Lots of problems connecting my treo 650.

Tried to add it as an input device, it makes a connection to the treo but then the bluetooth manager closes and the device is not added.  I have added other devices (BT mouse) and I can browse my Nokia e61 so I know the PC is setup correctly.

Any suggestions?

---

### Post by astx813 on 2008-02-08
> **geoffatmk said:**
> 
Lots of problems connecting my treo 650.

Tried to add it as an input device, it makes a connection to the treo but then the bluetooth manager closes and the device is not added.  I have added other devices (BT mouse) and I can browse my Nokia e61 so I know the PC is setup correctly.

Still working on the big picture, but I did manage to get past this particular glitch by initiating the connection from my Palm Centro.  Open Bluetooth Preferences and make your computer visible (I did Limited discoverable... and put a time limit on it).  Then open the Bluetooth app on your Palm, click the Setup Devices button, Trusted Devices, Add Device.  It should pick up your computer after a short scan.  The Palm will ask for a passkey first, you can make one up.  Then Ubuntu will announce a connection request and ask for a passkey, use the one you just made.  Now your phone shows up in the Bluetooth Prefs bonded devices list.

---

### Post by geoffatmk on 2008-02-11
Thanks astx813 but this is not the problem. 

My Treo 650 is already paired with my computer but I cannot browse it.  Every time I try I get;

Couldn't display "obex://[00:07:e0:06:91:38]".
Check if the service is available.

I read that I need to add the Treo to my "Input Services" list in preferences but every time I try to do so the preference window closes (crashes?) and the Treo is not added.  I still cannot browse my Treo.

I am still looking for a soluiton.  Is this a Palm treo 650 issue rather than a bluetooth one? I can connect and browse my Nokia E61.

Geoff

---

### Post by dcstar on 2008-02-12
> **geoffatmk said:**
> Thanks astx813 but this is not the problem. 

My Treo 650 is already paired with my computer but I cannot browse it.  Every time I try I get;

Couldn't display "obex://[00:07:e0:06:91:38]".
Check if the service is available.
........

I have similar issues with my LG mobile, I can pair it in Linux but cannot do anything with it.

When I start my XP (in VMware Server, inside Ubuntu), I can communicate with the same device no problems with the little Bluetooth dongle I am using!

Oh well, at least I can transfer files and manage the device sort of still using Linux.......

---

### Post by Jason.TJ.Johnson on 2008-02-14
Well, I'm having the same issue but I think I know why.

I originally had the Obex blah blah blah is not a valid location.
After installing "gnome-vfs-obexftp" the error changed to "check if service is running."

I tried it with a different phone, and now I'm able to browse, read, and write data to the phone easily.

The phone that isn't working is the Kyrocera E2000. The phone that is working is the Nokia 6265i.

Maybe that error message is referring to the service on the phone, and not on the computer?

---

### Post by 4leite on 2008-02-14
Hi,

I also had a similar problem like Couldn't display "obex://[00:07:e0:06:91:38]" with my nokia 3250. After banging my head against the wall I tried it on a mates XP with the proprietry software and got the same message. A quick trip back to the supplier and a replacement cell and everything is working fine...

---

### Post by outferno on 2008-02-15
I'm having trouble with this too.  I'm trying to connect a Samsung Blackjack to my computer.

I can get it to send files using nautilus if I right click the file and then click send.  I can also receive.  However, I can never browse my phone like a mass storage device.

I used to be able to bond my phone and it would show up on the Bonded Devices, but now it won't even bond with my phone anymore.  Anybody got a fix for this to rebond the phone?

---

### Post by ok67 on 2008-02-28
I also have some problems with bluetooth and my Sony Ericsson W910i.
I am able to send files from the phone to my PC, and also the other way. 

However if I select the blue icon and choose Browse Device and selects my phone and Connect it connects to my phone and my phone asks for a password/Code, but I dont know what code to use. I don't know what code to use, and if I enter anything (like my phne PIN code) I get an error message telling me that the code dos not confirm with the code in the other end (that means the code on my PC).


Added:

I solved the problem. I used the phone to add a new device. It searched up the computer and I could add it as a new device. I was then asked for a password on the phone, next I was asked for a password from the blue tooth manager on my PC. Then everything is OK, I am now able to browse my phone as well.

---

### Post by phaggood on 2008-03-09
I have the Palm Centro and Gutsy - I can bond to the phone (shows up on bonded devices with 'trusted' star in Bluetooth Preferences), but if I click 'Browse Device' - 'Select Device to Browse' and hit 'Connect' I get the obex://[00:07:e0:06:91:38]" 'check if service available' error.  What's supposed to happen when I hit browse? Is a file browser window supposed to open up?   The Centro is an awesome device and once I get mp3 file transfers over bluetooth working it'll truly rock (using the SD card for transfers is completely out due to the asinine placement of the card under the battery door)

---

### Post by Youresorock on 2008-03-11
I have a C2D Macbook running Ubuntu 7.10.  Fully updated as of this post.  I have gone thru this an other forum posts looking for a solution.  I'm trying to sync a Samsung phone.  I can pair, but that's it.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=62329&d=1205278646[/IMG]

---

### Post by madmaxo on 2008-03-31
I had the same problem. After reinstalling gnome-vfs-obexftp, I fixed the problem by doing the following:

1. Right-click the bluetooth icon in the notification area, choose Preferences
2. Delete any bonded devices
3. Under the 'Services' tab, enable all services
4. Right-click the bluetooth icon in the notification area, choose Browse Device again. You'll be prompted for a passkey on your phone, which you're then prompted to enter in Ubuntu too. Then a window opens and you can browse your phone.

---

### Post by Lex Luthor on 2008-07-02
UPDATE:
Got it to work now !

I entered the phone, removed my notebook from its history and asked to connect again. it asked for the passwork again. I typed, but in ubuntu, the window asking for it is hidden, it should be very very clear asking for that password.

After I type the passwd, it gave the same error, but I tried to connect again and it worked !

---------------------------------------------------
I also have problem with BT and Ubuntu.
Now I have hardy, but in gutsy it also happens.

I cannot connect through nautilus with the obex://[MAC] address
I was able to make it work doing nothing on Feisty, but when I upgraded to gutsy it stopped to work. Now on fresh hardy it also does not work.

I have a Motorola PEBL U6 phone, I can send my photos using BT to my laptop and from laptop I can send files to it, all using BT. But if I try to connect to it using nautilus, then apeears on my phone a message asking to bond to the machine but it instantantly goes away.

My obexftp show this (the problem persists):
obexftp -b 00:19:2C:81:7A:0F -l /
Browsing 00:19:2C:81:7A:0F ...
Channel: 9
Connecting...failed: connect
Still trying to connect
Connecting...failed: connect
Still trying to connect
Connecting...failed: connect
Still trying to connect

anyone have a clue ?


---------------------------------

---

