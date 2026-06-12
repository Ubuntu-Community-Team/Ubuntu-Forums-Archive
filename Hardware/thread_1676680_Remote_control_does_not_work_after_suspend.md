---
title: "Remote control does not work after suspend"
date: 2011-01-27
forum: Hardware
---

### Post by stee on 2011-01-27
Hi,
I recently bought an EEEbox 1501P. It came with a remote control with an internal IR receiver (European/Asian version of the 1501P). 
It's located at /sys/devices/pnp0/00:0a, and through googling and following the guides I have found, like [this]("http://wiki.xbmc.org/index.php?title=HOW-TO_perform_a_miminal_Ubuntu_and_XBMC_install_on_a_Asus_EeeBox_PC_EB1501"), I have been able to make it work flawlessly with LIRC and Ubuntu 10.04 (including XBMC). (Ubuntu 10.10 does not work due to a [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/659449") in the kernel.)

That is, until I suspend the machine. After waking up from suspend, the remote control simply does not work. The file /sys/devices/pnp0/00:0a/resources still says "active", and it seems that what works for everyone else doesn't work for me. Many guides and forum posts suggest making a script either in /etc/pm/sleep.d or in init.d, where I am supposed to stop the lirc program and remove the lirc_it87 and lirc_dev modules before going to suspend, and then add the modules back and restart the lirc daemon during wake-up. This simply has no effect on my remote.

Normally I can get output from both "sudo irw /dev/lircd" and "sudo mode2 -d /dev/lircd", but after wake-up, I get nothing at all. No error messages either. 

I'm really frustrated here. Any idea about where I can start looking for clues?

---

### Post by polc on 2011-04-15
Dear see.

I can see the same problem with My 10.10.
Remote works after startup, even in XBMC.
After sleep, and wake, nothing in XBMC, and irw cannot detect input.
I am using serial ttyS0 serial port with a home built adapter.
I checked: serial port is active, 8V output is switched on.

Have you got any news/solution already?

Regards

---

### Post by stee on 2011-04-15
Nope, no resolution yet. 
I've given up.

---

### Post by polc on 2011-04-16
Dear Stee,

Yesterday, I was able solve the problem on my computer.
If You (or somebody else) still interested, here is the solution:

I found some hints on:
 [http://wiki.xbmc.org/index.php?title=Ubuntu_Suspend_/_Wake](http://wiki.xbmc.org/index.php?title=Ubuntu_Suspend_/_Wake)

As I am using 10.10 some names, and files are different. (however HAL was installed)
As it is more speaking about USB device rights, and enable, and I am using a home built serial adapter, I did not take care about these parts, but at the end of the page, I have found that:

- - - - - - - - - - -- - -  - - - - - - - - - - - -
** Fix the Lirc Device Increment Bug**

 If your IR remote does not work after waking from sleep, you most  likely have this bug.  The IR software for Linux, Lirc, will create a  new device **/dev/lirc1** because it presumes the old device **/dev/lirc0** is in use by another process.  This confuses XBMC  and you end up with a non-working remote.  The solution is to shutdown  Lirc before suspension and then start it back up after wake.  This is  done by creating a script at **/etc/pm/sleep.d/90_lirc** : 
 [LEFT][FONT=monospace]# Script to disable lirc before suspend and restart after wake.
 
case "${1}" in
       suspend[COLOR=Black][/COLOR]|hibernate)
		if [ "$(pidof xbmc.bin)" ] ; then
			wget -q -b -O /dev/null -o /dev/null "http://127.0.0.1:8080/xbmcCmds/xbmcHttp?command=ExecBuilt&Inparameter=LIRC.Stop"
		fi
                /etc/init.d/lirc stop
                ;;
        resume|thaw)
 # If remote still does not work after suspend, uncomment the lines below. 
 # Note you may need to change "lirc_mceusb". See output from 'sudo lsmod | grep lirc' for module name.
                [B]#rmmod lirc_mceusb
                #modprobe lirc_mceusb[/B]
                /etc/init.d/lirc start
		if [ "$(pidof xbmc.bin)" ] ; then
			wget -q -b -O /dev/null -o /dev/null "http://127.0.0.1:8080/xbmcCmds/xbmcHttp?command=ExecBuiltIn&parameter=LIRC.Start"
		fi
                ;;
esac[/FONT]
[/LEFT]
 Make sure the script is executable: 
 [LEFT][FONT=monospace]chmod 755 /etc/pm/sleep.d/90_lirc

- - - - - - - - -- - - - -- 
I have created the file 90_lirc in the directory.
Of course was not working....
I have deleted #s from the two lines, mentioned above, and changed the mce_usb name to serial_idonnow 
(the name found with sudo lsmod | grep lirc).
:-) And working. Remote works after wakeup!

Hi.
[/FONT]
[/LEFT]

---

### Post by ariel on 2011-06-08
> **polc said:**
> Dear Stee,

Yesterday, I was able solve the problem on my computer.
If You (or somebody else) still interested, here is the solution:

I found some hints on:
 [http://wiki.xbmc.org/index.php?title=Ubuntu_Suspend_/_Wake](http://wiki.xbmc.org/index.php?title=Ubuntu_Suspend_/_Wake)

As I am using 10.10 some names, and files are different. (however HAL was installed)
As it is more speaking about USB device rights, and enable, and I am using a home built serial adapter, I did not take care about these parts, but at the end of the page, I have found that:

- - - - - - - - - - -- - -  - - - - - - - - - - - -
** Fix the Lirc Device Increment Bug**

 If your IR remote does not work after waking from sleep, you most  likely have this bug.  The IR software for Linux, Lirc, will create a  new device **/dev/lirc1** because it presumes the old device **/dev/lirc0** is in use by another process.  This confuses XBMC  and you end up with a non-working remote.  The solution is to shutdown  Lirc before suspension and then start it back up after wake.  This is  done by creating a script at **/etc/pm/sleep.d/90_lirc** : 
 [LEFT][FONT=monospace]# Script to disable lirc before suspend and restart after wake.
 
case "${1}" in
       suspend|hibernate)
        if [ "$(pidof xbmc.bin)" ] ; then
            wget -q -b -O /dev/null -o /dev/null "http://127.0.0.1:8080/xbmcCmds/xbmcHttp?command=ExecBuilt&Inparameter=LIRC.Stop"
        fi
                /etc/init.d/lirc stop
                ;;
        resume|thaw)
 # If remote still does not work after suspend, uncomment the lines below. 
 # Note you may need to change "lirc_mceusb". See output from 'sudo lsmod | grep lirc' for module name.
                [B]#rmmod lirc_mceusb
                #modprobe lirc_mceusb[/B]
                /etc/init.d/lirc start
        if [ "$(pidof xbmc.bin)" ] ; then
            wget -q -b -O /dev/null -o /dev/null "http://127.0.0.1:8080/xbmcCmds/xbmcHttp?command=ExecBuiltIn&parameter=LIRC.Start"
        fi
                ;;
esac[/FONT]
[/LEFT]
 Make sure the script is executable: 
 [LEFT][FONT=monospace]chmod 755 /etc/pm/sleep.d/90_lirc

- - - - - - - - -- - - - -- 
I have created the file 90_lirc in the directory.
Of course was not working....
I have deleted #s from the two lines, mentioned above, and changed the mce_usb name to serial_idonnow 
(the name found with sudo lsmod | grep lirc).
:-) And working. Remote works after wakeup!

Hi.
[/FONT]
[/LEFT]


Thanks for posting back polc. I am having the same issue (also with xbmc) on ubuntu 11.04 but this solution doesn't seem to work. Apparently LIRC changed a lot in the last ubuntu release.

Did you run into this issue in natty? could you solve it?

---

### Post by lupick on 2011-06-09
> **ariel said:**
> Thanks for posting back polc. I am having the same issue (also with xbmc) on ubuntu 11.04 but this solution doesn't seem to work. Apparently LIRC changed a lot in the last ubuntu release.

Did you run into this issue in natty? could you solve it?


I was able to have lirc working in Ubuntu 10.10 but in 11.04 lirc hang after the resume!!

I'va also opended a bug:

[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/789819](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/789819)

please subscribe it!

thx

L.

---

