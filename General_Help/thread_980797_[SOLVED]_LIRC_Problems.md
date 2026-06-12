---
title: "[SOLVED] LIRC Problems"
date: 2008-11-13
forum: General Help
---

### Post by eleniontolto on 2008-11-13
Sorry if this isn't the right forum to be posting this in, but I wasn't really sure of the correct place so I'm putting it in general.  I recently did a clean install of intrepid and have been having trouble getting it to work.  I'm somewhat of a linux noob, but I had everything working perfectly on hardy, and the same things don't seem to work on intrepid.  I spent the better part of a day searching the internet for solutions and nothing yet has worked.  I should also note that I had this problem earlier on with intrepid, then i REinstalled intrepid today, and the problem still exists.

To get lirc up and running, I do sudo apt-get install lirc.  It runs me through the setup process where I choose the type of remote and transmitter and such.  I chose the "Windows Media Center Remotes (old version Microsoft USB ID)" which worked perfectly on Hardy, and chose "none" for the transmitter.  It then shows the following:

* Reloading kernel event manager...        [OK]
* Loading LIRC modules                     [OK]
* Starting remote control daemon(s): LIRC  [fail]


I have tried running sudo dpkg-reconfigure lirc several times to make sure, and it still comes back with a fail.  Typing in irw in the terminal behaves normally, except pressing buttons on the remote while in irw doesn't result in any remote codes displaying in terminal, though I can tell the receiver itself is receiving the codes from the remote because its light blinks every time i press a button.

Any ideas?  I would really appreciate any suggestions or even links or whatever that could be helpful.  Let me know if I need to provide any more info as well!

---

### Post by geirha on 2008-11-13
The logfiles might provide some clues. Try ```
grep lirc /var/log/{daemon.log,kern.log}
```

---

### Post by josephmc on 2008-11-13
I've had a similar problem but if I start lirc after boot it works fine. It just won't start at boot for some reason. It is in the rc folders. 

```
sudo /etc/init.d/lirc start
```

It gets it working but I would like it to start at boot. 

Log files show lirc starting fine. I'm wondering if it's taking a little bit to initialize the lirc driver (lirc_i2c for hauppage) and it doesn't finish before lirc starts. Perhaps I should just raise the boot priority on lirc.

---

### Post by eleniontolto on 2008-11-13
Here's the log geirha.  Thanks for taking a look.

[http://pastebin.ca/1255494](http://pastebin.ca/1255494)

And that command doesn't work for me, josephmc.  I get the same thing as before.  Loading LIRC modules OK, loading daemon FAIL

---

### Post by geirha on 2008-11-13
No obvious reasons for why it doesn't work in the logs, it looks rather correct there. Try running lircd manually and see if it gives some more information. 

```

lsmod | grep lirc    # Make sure the two lirc_-modules are loaded
sudo killall lircd   # Kill lircd in case it is running
sudo lircd -n        # Run it without going to the background

```
Once it's started, try connecting to it with irw in another terminal. Does lircd print anything?

---

### Post by eleniontolto on 2008-11-13
lsmod gave:

lirc_mceusb            16992  0 
lirc_dev               20020  1 lirc_mceusb
usbcore               148848  5 lirc_mceusb,usbhid,ehci_hcd,ohci_hcd

lircd -n gave:

lircd-0.8.3[5960]: lircd(userspace) ready

When I tried running irw in a new terminal, the original terminal gave:

lircd-0.8.3[5960]: accepted new client on /dev/lircd
lircd-0.8.3[5960]: could not get file information for /dev/lirc
lircd-0.8.3[5960]: default_init(): No such file or directory
lircd-0.8.3[5960]: caught signal
Terminated


And irw didn't work at all in that other window.  It kept saying connect: Connection refused

---

### Post by lovinglinux on 2008-11-13
Could you post the content of "/etc/lirc/hardware.conf"?

I had similar problems and I was able to make my remote work after manually editing some options in that file.

---

### Post by eleniontolto on 2008-11-14
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Remotes (old version MicroSoft USB ID)"
REMOTE_MODULES="lirc_dev lirc_mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```

---

### Post by lovinglinux on 2008-11-14
> **eleniontolto said:**
> ```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Remotes (old version MicroSoft USB ID)"
REMOTE_MODULES="lirc_dev lirc_mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```

Try editing these settings:

```
REMOTE_MODULES="false"
```

```
LOAD_MODULES="lirc_dev lirc_mceusb"
```

Then restart lirc

```
sudo /etc/init.d/lirc restart
```

If it works, you should get something like this:

```
 * Stopping remote control daemon(s): LIRC                               [ OK ] 
 * Starting remote control daemon(s) : LIRC                              [ OK ] 
```

Then test the remote input running the following command and pressing a few buttons in the remote:

```
irw
```

You should get something like this:

```
~$ irw
0000000000fec63e 00 Chan-Stop PinnacleSysPCTVRemote
0000000000fec63e 00 Chan-Stop PinnacleSysPCTVRemote
0000000000fec63e 01 Chan-Stop PinnacleSysPCTVRemote
0000000000fec63e 00 Chan-Stop PinnacleSysPCTVRemote
```

If you get these kind of output when running irw test then you are good to go.

---

### Post by eleniontolto on 2008-11-14
That seems to have gotten it working.  Thanks!

---

### Post by lovinglinux on 2008-11-14
Nice. Please don't forget to mark the thread as [SOLVED] using the Thread Tools menu. This helps other people find the solution to similar problems.

---

### Post by usererror on 2009-04-27
This post helped me solve my problems too!

I found that my hardware.conf had a line that stated:

```
REMOTE_MODULES="lirc_dev lirc_mceusb2"
```

I don't know why the above line got changed to "REMOTE_MODULES" from "LOAD_MODULES" but heck everything works now!

must have been an upgrade and a change in the way lirc was written to read its configs, who knows!

Thanks, lovinglinux!!

---

### Post by lovinglinux on 2009-04-27
> **usererror said:**
> This post helped me solve my problems too!

I found that my hardware.conf had a line that stated:

```
REMOTE_MODULES="lirc_dev lirc_mceusb2"
```

I don't know why the above line got changed to "REMOTE_MODULES" from "LOAD_MODULES" but heck everything works now!

must have been an upgrade and a change in the way lirc was written to read its configs, who knows!

Thanks, lovinglinux!!

You are welcome.

Since I installed Jaunty I can't get my remote to work. Ironic, isn't it?  :mrgreen:

---

### Post by pokogr on 2009-04-27
> **lovinglinux said:**
> You are welcome.

Since I installed Jaunty I can't get my remote to work. Ironic, isn't it?  :mrgreen:

me too :) 
ggrrrrrrrrr

---

### Post by lovinglinux on 2009-04-27
> **pokogr said:**
> me too :) 
ggrrrrrrrrr

What is weird is that I'm using the same settings and config files. Lirc actually load successfully, but the irw test reveals no input from the remote.

---

### Post by pokogr on 2009-04-27
> **lovinglinux said:**
> What is weird is that I'm using the same settings and config files. Lirc actually load successfully, but the irw test reveals no input from the remote.

After installing Jaunty I hadn't tested the remote at all. So, one night I tried that out and I saw it was working!!! The day after, it wasn't... My embedded  ir receiver (hp hdx16) seems to not be starting on each boot. I was able to use the control even on the grub menu so I don't think that it is a lirc properties problem...

---

### Post by lovinglinux on 2009-04-27
Edit: Ooops. Wrong thread. I will post in the new thread about Jaunty.

---

