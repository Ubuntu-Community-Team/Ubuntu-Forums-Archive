---
title: "emachine e520 wireless card"
date: 2009-02-06
forum: Hardware
---

### Post by Bendds on 2009-02-06
I have an emachines or acer e520 and have not been able to enable the Atheros wireless card, Ubuntu recognizes the hardware and driver as working properly but the card is not enabled. Wireless does work from a usb plug in device. The wireless switch on the machine seems to be software controlled and not by ubuntu.  Does anyone have any fixes for this issue?

---

### Post by squidx on 2009-02-06
Same problem here! Considering madwifi but wanted to check with others before wasting time/messing things up, etc.

---

### Post by squidx on 2009-02-06
:p

Ok, I did some checking around, and decided that because of all of the broken links on the madwifi page, and because they moved away from sourceforge, etc, that I wanted a more reliable solution. I mean, even their FAQ didn't work, or at least have some kind of FAQ/explanation on it.

I finally found a reference to some drivers which seemed reliable, in the sense that they were in default repositiories accessible through apt-get.

The site is here and contains instructions. 
[http://unsharptech.com/2008/10/31/atheros-wireless-in-ubuntu-810-intrepid-ibex/](http://unsharptech.com/2008/10/31/atheros-wireless-in-ubuntu-810-intrepid-ibex/)

The process is very easy, and I can sum it up here. It takes 2 reboots, which is odd, and a slight PIA, but since it worked immediately (sending via wifi right now), I would say it is a good solution:

0) I guess you should confirm your situation in terms of hardware -- go to System->Administration->Hardware Drivers and see if it shows "Support for Atheros 802.11 wireless LAN cards" and that it is "activated and in currently in use" (sure it is, that's why we need new drivers??)

1) In a terminal window, run apt-get by entering the following line (copy-paste is fine). Apt-get will download and install the drivers.

sudo apt-get install linux-backports-modules-intrepid-generic  

In case you're not familiar with sudo, sudo will ask you for your password and then perform as if you were root, but then log out of root when the task is finished. 

Apt-get will ask you a couple of things, like is it ok to download this, which is xx, y/n. Answer y. 

2) When apt-get is finished, close the terminal and reboot.

3) When the installation is finished, reboot, then check the Hardware Drivers. Now you'll see the new driver in there, "Support for 5XXX series of Atheros 802.11 wireless LAN cards". That's the one you want. Select the old one (doesn't say 5XXX) and click on Deactivate.

4) Reboot again :( 

5) When ubuntu comes up again, the network manager will be trying to do wireless things and probably ask you for your password, with a choice of Just Once or whenever it wants it. Being lazy, I told it to keep the password. If you left-click on the network icon to the left of the speaker icon in the upper menubar (assuming you haven't changed things around on your desktop too much), you'll see a list of the wireless networks around you. Wireless should be working!

Now it's up to you to connect to them.

I'm very happy it was this easy for me. Let me know if you have the same experience. 

BTW: woot?

---

### Post by Bendds on 2009-02-06
That was great, it works now, bless you,

However I have to tweak every time it reboots and set it up again in hardware drivers, this is not a major issue but wanted to report it

---

### Post by jmartinb on 2009-02-06
Squid-
I followed your steps but get no wireless.  Under System->Administration->Hardware Drivers it shows "Support for 5xxx series of Atheros 802.11 wireless LAN cards." with a green indicator.  No other drivers are present.  It states at the bottom of this window, "This driver is activated and currently in use.".

I too have an eMachine E520 courtesy of Woot!

I am posting this via my Ethernet (eth0) connection.

When I click on the Network Manager icon (the one next to the speaker), I only get two(2) entries:  eth0 and lo.  I would imagine this wireless connection would show up here.

When I run the iwconfig command, here are the results:

jmartinb@jmartinb-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


It feels like I've missed a step somewhere.  Any help is greatly appreciated.
Thanks,
Jeff

---

### Post by Bendds on 2009-02-06
Try disabling the driver and then enabling it again.  This is what worked for me.  It was very strange and I have to do it at every boot up but it does work.

---

### Post by squidx on 2009-02-06
Jeff,

I'm kind of new at this stuff, so you've got me stumped...

Here are some thoughts I'm having:

a) Did you reboot *two* times?

b) My iwconfig looks almost exactly like yours, except that it shows the connection I have. But it kind of looks like yours is on -- try right-clicking on the Network Manager and making sure Enable Wireless is checked.

I actually had pre-setup a connection under Preferences->Network Configuration/wireless tab to see if that was my problem in the first place -- when the network came on, this connection became enabled. Maybe you should make one of those, too.

c) Jimro at another Ubuntu Forum said that the backport had only worked until a kernel update, and swears by the madwifi. Here's a link to that: [http://ubuntuforums.org/showthread.php?p=6690143#post6690143](http://ubuntuforums.org/showthread.php?p=6690143#post6690143) although I note that the Ubuntu 8.10 release notes do mention the backport [http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default) and I wouldn't give it up just yet. Did you update the kernel like Jimro?

Good luck!

---

### Post by jmartinb on 2009-02-06
Squidx-
That's why I think I missed a step.  Unless I am doing something really stupid...when I right-click the Network Manager icon, the "Enable Wireless" option doesn't exist.

Under Network Connections, I setup a wireless entry for our guest network which is wide open, no security.  It doesn't see it.

I'll read Jimro's entries about the kernel update....any other ideas are appreciated.

Did you get your wireless toggle switch, left of the Tab key, to light up?  Mine doesn't which means I am trying every twice since I dont know if its on or off. 

Appreciate the feedback.

---

### Post by Bendds on 2009-02-06
Squid, any thoughts on why it needs to be set up at each boot?  The connection is excellent, Thanks again

---

### Post by jmartinb on 2009-02-06
Just some more info:

I performed a lsmod | grep "ath"
Here's the output:

jmartinb@jmartinb-laptop:~$ lsmod | grep "ath"
ath5k                 116612  0 
lbm_cw_mac80211       215856  1 ath5k
lbm_cw_cfg80211        46744  2 ath5k,lbm_cw_mac80211
led_class              12164  1 ath5k
jmartinb@jmartinb-laptop:~$ 


No sign of ath_pci (which is the expected outcome).

Here are the results of doing an "iwlist wlan0 scanning, grepping on ESSID.  It's finding valid wireless networks but I still can't connect to anyone of them.
root@jmartinb-laptop:/home/jmartinb# iwlist wlan0 scanning | grep ESSID
                    ESSID:""
                    ESSID:""
                    ESSID:""
                    ESSID:"Erickson"
                    ESSID:"Guest"
                    ESSID:"Guest"
                    ESSID:"Erickson"
                    ESSID:"Guest"
                    ESSID:"Erickson"
                    ESSID:"Guest"
                    ESSID:"Erickson"
                    ESSID:"UMBC Visitor"
                    ESSID:"Guest"
                    ESSID:"Guest"
                    ESSID:"N89I4"
                    ESSID:""
                    ESSID:""
                    ESSID:"ascguest"
                    ESSID:"Erickson"
                    ESSID:""
                    ESSID:"Erickson"
                    ESSID:"Erickson"
                    ESSID:"Guest"


Can I connect to a wireless network via the command line if there is something wrong with the GUI?

---

### Post by jmartinb on 2009-02-07
Guys-
I got it to work.  The last thing I did was run System -> Administration -> Update Manager.  I had a ton of updates.  Installed them all and rebooted.  The wireless LAN came up.

So, in retrospect Squidx, doing your process (with 2 reboots) plus running Update Manager against my fresh 8.10 installation probably did the trick.

---

### Post by Bendds on 2009-02-07
Hi Jeff,

Do you have to force it each time you reboot?  Mine works but I have to "turn it on" each time.  Could the "switch" on the machine be an issue?

Ben

---

### Post by sgfish on 2009-02-08
SquidX - I was having the exact same problem with my e520, and it fixed it right up. Thank you!

---

### Post by squidx on 2009-02-12
I'm glad I was able to share my research with everyone. I didn't invent the solution, just publicize what worked for me. That's what's great about the linux community.

Bendds -- I don't know why your configuration changes and needs resetting every time. Obviously a preference/config file isn't being written persistently even though the change works at the time. Often, this will be a permissions thing, I think. You could try setting up to directly login as root, although I think that's frowned upon.

If anyone knows what files get modified when this control panel gets used, please let us know -- then we can check permissions, diff it, etc.

Also, if anyone knows how to make the specific configuration changes from the command line (ie, under su) rather than via the control panel, that would be a good start. 

I'd even settle for knowing how to call the control panel from the terminal under su, thus ensuring powerful permissions magic!

ps: the "switch" on the machine, which I assume is the button on the left of the keyboard with the cryptic symbol and a little LED, seems to have no effect for me whatsoever. However, using the keylogger (I'll try to remember/search for how to invoke that) will allow us to determine how it appears to the OS, and then it will be a simple matter to assign (or remove!) a function to it...

---

### Post by pal8 on 2009-02-24
Sorry for jumping in with a parallel question that regards the laptop e520. Are you talking about Acer e520? And it works with Ubuntu 8.10?

---

### Post by msheppard on 2009-04-03
squid's technique worked most of the way for me - but I had to go to system->admin->hardware and disable the "support for Atheros 802.11" entry in the driver list.

M@

---

### Post by andrewbond007 on 2009-04-04
HI!!
Thanks to Bend because I tried the way "deactivate-active" for the 5xxx support and it works!!, but I'm looking for an answer to the issue that this has to be done in every system start!
If anyone find the answer or a clue please let as know.

Best Regards!!

UBUNTU LINUX FOR EVER AND EVER!!

---

