---
title: "NEWBIE: How to get online with a Lucent WinModem?"
date: 2004-11-06
forum: Hardware &amp; Laptops
---

### Post by AndyGates on 2004-11-06
Gods, I hate being a noob sometimes!

Right: I've installed Ubuntu as the only OS on a PC.  Install was easy and painless, but now I discover that the machine's modem is a WinModem, and these are apparently a problem.

According to ScanModem, I have a Lucent LT WinModem (rev 02) with the Lucent/Agere DSP chipset.  Class 0780: 11c1:044c, if that means anything.  And I'm running the Warthog release of Ubuntu Linux, kernel version 2.6.8.1-3-386.  

I had a go at downloading and installing what I thought were suitable drivers, and I now have a ttyLT0 device... but being a noob, I've no idea how to test if it's working.  Running wvdialconf fails to detect it.

Help!  The modem's this machine's only connection to the net and I'm suffering withdrawal!  Pretty please?

---

### Post by az on 2004-11-06
1- Either try making a symlink from /dev/ttySL0 to /dev/modem.  Then try to see if you can automatically detect your modem.

2-  Look here:
[http://phep2.technion.ac.il/goldberg/post-install.html](http://phep2.technion.ac.il/goldberg/post-install.html)
or here:
[http://users.ox.ac.uk/~mert1313/ltmodem.html](http://users.ox.ac.uk/~mert1313/ltmodem.html)

Good Luck!

While connecting, in another terminal do
sudo tail -f /var/log/messages

to see what is going on...

---

### Post by AndyGates on 2004-11-06
Erk, after a reboot I have no ttyLT0 nor ttySL0 and certainly no modem.  Trying the other links for inspiration...

... okay, the post-install stuff isn't relevvant yet as I don't seem to have it installed at all.  The other link starts off good but when I follow it through to the Debian site (Ubuntu's a Debian variant, right?) they's got vaguely impenetrable navigation and their site search is offline.  The other suggestion on Goldber's site is to compile the sourse.  I could probably handle the utter scariness of that if there were details for the 2.6 kernel... but there ain't.

Stuck again!

---

### Post by jdong on 2004-11-06
For now, this seems like a hardware problem -- configuring the LT Winmodem.

After you get the devices to show up, start a new topic in General Support if you need help setting up PPP.

---

### Post by az on 2004-11-06
And after that amazingly helpful bit from the moderator....

I did a forty second serach on google 
ltmodem kenel 2.6 

and found

[http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/)

Here is also a snip from someone who installed an ltmodem on his/her laptop.

Now if these do not work, maybe your chipset is not supported.  Not with a 2.6 kernel anyway.  In that case, maybe try installing a debian 2.4 kernel and using one of the drivers mentioned on the pages in the earlier post.






Install LT modem drivers for Linux 2.6
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
$ cd /usr/src ; wget [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ltmodem-2.6-alk-v00.tar.gz](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ltmodem-2.6-alk-v00.tar.gz) ; tar zxvf ./ltmodem-2.6-alk-v00.tar.gz
$ cd ltmodem-2.6-alk
$ vi Makefile   # and edit KERNEL_DIR to be /usr/src/linux-2.6.0
$ make
$ sudo mkdir /lib/modules/2.6.0/ltmodem-alk
$ sudo cp -a ltmodem.ko ltserial.ko /lib/modules/2.6.0/ltmodem-alk
$ sudo depmod -a

$ sudo cat > /etc/modprobe.d/ltmodem <<EOF
alias char-major-62  ltserial
alias /dev/tts/LT0   ltserial
alias /dev/LT-modem  ltserial
EOF
$ sudo update-modules

---

### Post by AndyGates on 2004-11-07
Feels like I'm getting somewhere now - thanks!  I've got the ltmodem-2.6-alk tarball unpacked in /usr/src/ltmodem-2.6-alk.  Next thing to do is edit the Makefile - but these instructions don't quite match up.  There's no /usr/src/linux-2.6.0 folder present.  In fact in /usr, there's just my modem folder and /RPM.  So... how do I work out what my kernel folder is?

(I'll have to write this up as an utternoob howto when I'm done!)

---

### Post by az on 2004-11-07
You need the kernel source to build kernel modules.  You can, howver just use the headers from your kernel source.
sudo apt-get install build essential
sudo apt-get install linux-headers-2.6-386 kernel-kbuild-2.6-3

Then, when asked where your source directory is, use:
/usr/src/linux-headers-2.6.8.1-3-386


That is assuming that you are using the default 386 kernel...  Change the names accordingly.
Yes, you can use synaptic to get all these packages...

---

### Post by AndyGates on 2004-11-08
"You need the kernel source to build kernel modules. "

Thanks.  I fired up Synaptic and found the linux-kernels, which seem to be what was needed.  

Of course, to make the drivers you also need to install gcc, otherwise you've not got a compiler at all.  That was a bit of a curveball.  Gcc installes fine via synaptic too, and hey presto! I have some drivers that sometimes nearly work.

Sometimes: the driver package I was pointed to includes an autorun script which loads up the software drivers.  They're supposed to load up only when needed, but they don't: if I reboot, there's no modem.  If I dial, it is supposed to appear, but it doesn't until I re-run that autorun script manually.  If I do that...

... it dials!  Only from the GUI dialler, as wvdial says it has no valid config (even though as far as I can tell it does, /etc/wvdial.conf created with wvdialconf and edited for phone number, etc).  

Unfortunately, all it does is dial, negotiate, and hang up.

At this stage I'm losing the will to live.  If I rip this thing out and buy a proper modem, what can I expect to have to do to make it work?  Are there going to be drivers on the Ubuntu install CD?  And is there any form of auto-detect?

---

### Post by az on 2004-11-08
Had you installed build-essential, as I had suggested, you would have gotten gcc and everything necessary to compile.

Gnome-PPP and wvdial use different config files, I think.  Also, you probably do not have all of your permissions set up.

Add the name of the module you built to /etc/modules so that it is loaded at boot every time.

Then, try adding a network connection in then Ubuntu network setup.  Also, check your logs to find out why it dies using wvdial (or whatever you are using)

sudo tail -f /var/log/messages.

Myself, I find pppconfig useful.  Pon and poff are already there in the  applet "Modem Lights"

sudo pppconfig
Be sure to add your user to the dip group in the advanced menu.
Be sure to save your settings.
sudo pon provider
tail -f /var/log/messages

---

### Post by AndyGates on 2004-11-10
Right, this is a long one 'cos I've captured loads of error messages.  As usual, please forgive the utter shuddering newbiness of it all: without knowing what to know, I've erred on the side of the verbose.

Okay, I've installed build-essential and rebuilt the drivers using the three-stage scripts build_module, ltinst2 and autoload which are provided in the driver tarball.

There was a little iffy output from build_module, but it claimed to have finished OK:

|grep: /etc/modprobe.conf: No such file or directory
|grep: /etc/modprobe.conf: No such file or directory
|
|utils/scanmodem: line 3010: exit0: command not found
|utils/scanmodem: line 3161: syntax error near unexpected token `fi'
|utils/scanmodem: line 3161: `fi'

Here's what has been built:

|Checking for driver products:
|-rw-r--r--    1 root     root       561828 2004-11-10 18:48 lt_modem.ko
|-rw-r--r--    1 root     root        23861 2004-11-10 18:48 lt_serial.ko

>Add the name of the module you built to /etc/modules so that it is loaded at boot every time.

Hmm, you don't mean add the driver filenames, lt_modem.ko and lt_serial.ko, to the list of other bits and bobs (psmouse, mousedev, ide-cd etc), do you?  That don't work.  Which is probably not surprising ;)  

>Myself, I find pppconfig useful. Pon and poff are already there in the applet "Modem Lights"

Okay set up in pppconfig.  (How do I run modemlights?)

Here's the log I get from using "sudo pon myprovider":

Nov 10 20:05:15 localhost kernel: CSLIP: code copyright 1989 Regents of the University of California
Nov 10 20:05:15 localhost kernel: PPP generic driver version 2.4.2
Nov 10 20:05:20 localhost pppd[4733]: pppd 2.4.2 started by root, uid 0
Nov 10 20:05:20 localhost kernel: lt_modem: module license 'Proprietary' taints kernel.
Nov 10 20:05:20 localhost kernel: Loading Agere/Lucent WinModem Controller driver version 8.31
Nov 10 20:05:20 localhost kernel: lt_serial: no version for "ltmodemDependency" found: kernel tainted.
Nov 10 20:05:20 localhost kernel: Detected Parameters Irq=10 BaseAddress=0xe800 ComAddress=0xecd8
Nov 10 20:05:20 localhost kernel: ttLTM0 at I/O 0xe800 (irq = 10) is a AgereModem
Nov 10 20:05:20 localhost kernel: Loading module Agere/Lucent WinModem Interface driver version 8.31 (2004-03-31)
Nov 10 20:05:22 localhost chat[4748]: abort on (BUSY)
Nov 10 20:05:22 localhost chat[4748]: abort on (NO CARRIER)
Nov 10 20:05:22 localhost chat[4748]: abort on (VOICE)
Nov 10 20:05:22 localhost chat[4748]: abort on (NO DIALTONE)
Nov 10 20:05:22 localhost chat[4748]: abort on (NO DIAL TONE)
Nov 10 20:05:22 localhost chat[4748]: abort on (NO ANSWER)
Nov 10 20:05:22 localhost chat[4748]: abort on (DELAYED)
Nov 10 20:05:22 localhost chat[4748]: send (ATZ^M)
Nov 10 20:05:22 localhost chat[4748]: expect (OK)
Nov 10 20:05:22 localhost chat[4748]: ATZ^M^M
Nov 10 20:05:22 localhost chat[4748]: OK
Nov 10 20:05:22 localhost chat[4748]:  -- got it
Nov 10 20:05:22 localhost chat[4748]: send (ATDT08089916106^M)
Nov 10 20:05:22 localhost chat[4748]: expect (CONNECT)
Nov 10 20:05:22 localhost chat[4748]: ^M
Nov 10 20:05:53 localhost kernel: APIC error on CPU0: 00(40)
Nov 10 20:06:07 localhost chat[4748]: alarm
Nov 10 20:06:07 localhost chat[4748]: Failed
Nov 10 20:06:09 localhost pppd[4733]: Exit.

----------------------------------------------------------------------
When I try to activate the network connection using the
Network Settings dialog, this is what I see in the tail messages:

Nov 10 19:00:27 localhost pppd[7199]: pppd 2.4.2 started by root, uid 0
Nov 10 19:01:48 localhost pppd[7199]: Serial connection established.
Nov 10 19:01:48 localhost pppd[7199]: Using interface ppp0
Nov 10 19:01:48 localhost pppd[7199]: Connect: ppp0 <--> /dev/modem
Nov 10 19:01:55 localhost pppd[7199]: Hangup (SIGHUP)
Nov 10 19:01:55 localhost pppd[7199]: Modem hangup
Nov 10 19:01:55 localhost pppd[7199]: Connection terminated.
Nov 10 19:01:56 localhost pppd[7199]: Terminating on signal 15.
Nov 10 19:01:56 localhost pppd[7199]: Exit.

Exit code 15 is: The  link  was  terminated because the peer is not
responding to echo requests.
-----------------------------------------------------------------------
After a reboot, nothing, no response to the GUI dialler or Network 
Settings requests to fire up the modem connection unless the autodial
script from the driver package is run.

If I run "sudo ./autodial" and *then* try to activate the network 
connection, I get the following:

Nov 10 19:42:37 localhost kernel: CSLIP: code copyright 1989 Regents of the University of California
Nov 10 19:42:37 localhost kernel: PPP generic driver version 2.4.2
Nov 10 19:42:42 localhost pppd[4375]: pppd 2.4.2 started by root, uid 0
Nov 10 19:42:42 localhost kernel: lt_modem: module license 'Proprietary' taints kernel.
Nov 10 19:42:42 localhost kernel: Loading Agere/Lucent WinModem Controller driver version 8.31
Nov 10 19:42:42 localhost kernel: lt_serial: no version for "ltmodemDependency" found: kernel tainted.
Nov 10 19:42:42 localhost kernel: Detected Parameters Irq=10 BaseAddress=0xe800 ComAddress=0xecd8
Nov 10 19:42:42 localhost kernel: ttLTM0 at I/O 0xe800 (irq = 10) is a AgereModem
Nov 10 19:42:42 localhost kernel: Loading module Agere/Lucent WinModem Interface driver version 8.31 (2004-03-31)
Nov 10 19:43:54 localhost kernel: APIC error on CPU0: 00(40)
Nov 10 19:44:02 localhost pppd[4375]: Serial connection established.
Nov 10 19:44:02 localhost pppd[4375]: Using interface ppp0
Nov 10 19:44:02 localhost pppd[4375]: Connect: ppp0 <--> /dev/modem
Nov 10 19:44:10 localhost pppd[4375]: Hangup (SIGHUP)
Nov 10 19:44:10 localhost pppd[4375]: Modem hangup
Nov 10 19:44:10 localhost pppd[4375]: Connection terminated.
Nov 10 19:44:11 localhost pppd[4375]: Terminating on signal 15.
Nov 10 19:44:11 localhost pppd[4375]: Exit.

---

### Post by AndyGates on 2004-11-12
Okay, I've found Modem Lights and popped that on the panel (right-click the panel, Add, pick it from the list); and I've Googled around and realised that "kernel tainted" is an ideological error message and not the sort of horror show that such a message might mean to a Windows user ;).  Still no idea how to correctly load the drivers or to get it to stay connected...

---

### Post by az on 2004-11-12
Adding the name of the module and not the filename of the module to /etc/modules is the thing to do.

Tainting the kernel means adding non-free (GPL) modules to it.

If I had the hardware, I could probably help you further...

---

### Post by ex0ja on 2005-01-24
I've got the same modem and I'm also getting problems.  It really sucks because I can't go on the net for help whilst linux is booted, I have to restart my computer and boot into windows every 2 minutes!  On top of that, because I only have dial-up (obviously) I have to keep paying for dial-up call costs everytime I reboot!

[QUOTE=AndyGates]|grep: /etc/modprobe.conf: No such file or directory
|grep: /etc/modprobe.conf: No such file or directory[/QUOTE]

I also get that error, what's it mean?

---

### Post by ex0ja on 2005-03-28
Still havn't got this working?  Anyone help?

---

### Post by Prudentissimus on 2005-07-01
[QUOTE=ex0ja]Still havn't got this working?  Anyone help?[/QUOTE]
 I cannot connect to internet either using Lucent modem... NO DIAL TONE.

---

