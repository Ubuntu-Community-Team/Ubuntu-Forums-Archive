---
title: "Internet wireless problem"
date: 2009-08-03
forum: Hardware
---

### Post by MartinoM on 2009-08-03
I have a big problem with internet wireless connection. If i left my pc inactive for only 5 minutes or i close the lid for the same time, internet connection doesn't work on! I must reconnect to wi-fi. Can someone hel me?

Command lspci:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
07:00.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:00.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:00.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:00.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:00.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

martino@martino-laptop:~$ sudo /etc/init.d/networking restart
[sudo] password for martino:
 * Reconfiguring network interfaces...                                         
 Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]



iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Casa" 
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0C:F6:35:B6:4F   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=42/100  Signal level:-84 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by am256 on 2009-08-03
What kind of PC are you running? Dell, HP, etc..

---

### Post by nothingspecial on 2009-08-05
I`ve tried everything and more to get this thing running properly.

There has been a bug filed but there seems to be some disagreement as to where the bug lies. Apparently the intel devs say it`s a gnome network manager bug but their devs say its not.

Installing wicd does not help me (so it`s definately a driver issue), but it may help you.

It used to be possible to install the old ipw3945 driver which works perfectly well thankyou very much but as it has not been developed for a couple of years this is a security risk.

Hell, I`ve even tried using the 2.6.31-3.19 kernel with jaunty (I don`t recommend you trying that) without success.

Luckily this wireless card is not in my main system, just a spare laptop but it is incredibly frustrating. The only way to make it useable is by limiting your speed to less than 110kbs.

Rest assured I`ll post a solution if I find one.

---

### Post by slakkie on 2009-08-05
I'm running a similar wireless card as you, but in combination with wpa_supplicant..

```

0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

lsmod | grep iwl
iwl3945                97912  0
mac80211              217592  1 iwl3945
led_class              12036  1 iwl3945
cfg80211               38288  2 iwl3945,mac80211

```

I made the following page in Dutch on how to create a wireless connection without a network manager, google translate is pretty good, quickly scanned through it, maybe it helps:

[http://translate.google.com/translate?js=y&prev=_t&hl=en&ie=UTF-8&u=http%3A%2F%2Fwiki.fok.nl%2Findex.php%3Ftitle%3DDig%2Flinux%2Fwireless&sl=nl&tl=en&history_state0=](http://translate.google.com/translate?js=y&prev=_t&hl=en&ie=UTF-8&u=http%3A%2F%2Fwiki.fok.nl%2Findex.php%3Ftitle%3DDig%2Flinux%2Fwireless&sl=nl&tl=en&history_state0=)

Only thing I had to change compared to the howto are two things (assuming you go for the advanced configuration):

/etc/default/ifplugd:

```

INTERFACES="eth0 wlan0"
HOTPLUG_INTERFACES=""
ARGS="-F -u0 -d10 -w -I"
SUSPEND_ACTION="stop"

```

And my wpa.sh has been updated:

```

#!/bin/bash

SELF=`basename $0`
WPA=wpa_supplicant
PROGRAM=/sbin/${WPA}
CONF=/etc/${WPA}.conf
INTERFACE=wlan0
DRIVER=iwl3945 # Intel Interfaces
DRIVER=wext     # default linux driver
DAEMONMODE="-B"

function start() {
    local ver=$(lsb_release -sr | sed -e 's/\.//g');
    OPTIONS="-W -c $CONF -i $INTERFACE -D $DRIVER $DAEMONMODE"
    OPTIONS="-c $CONF -i $INTERFACE -D $DRIVER $DAEMONMODE"

    # Ubuntu 8.10 and up doesn't need the -w anymore..
    [ $ver -lt 810 ] && OPTIONS="$OPTIONS -w"

    eval $PROGRAM $OPTIONS
}

function stop() {
    pkill $WPA
}

function debug() {
    stop
    DAEMONMODE="-ddd"
    start
}

function status() {
    pgrep -lf $WPA
}

case $1 in
    start|stop|debug|status)
        $1
        exit $?
    ;;
  *)
   echo "Usage: $SELF <start|stop>"
   exit 2
  ;;
esac

```

Best of luck!

---

### Post by nothingspecial on 2009-08-05
Thankyou ever so much I shall try this later today when I get home and report on the outcome.

At the moment I cannot stream music or video, download or transfer files at any useable speed.

---

### Post by slakkie on 2009-08-05
Yw. You might want to have a tab open on the original page, since google translate adds spaces and stuff not needed for all the stuff which is in [code] tags on the wiki.

---

### Post by nothingspecial on 2009-08-05
Unfortunately wpasupplicant has not solved my issue.

Thanks for the help anyway.

I have given up and am now using an old usb wireless thingy kindly donated by my brother.

This is satisfactory but not perfect. I only have 3 usb ports. 1 for the mouse (my family need it), one for the music hard drive (we were intending to use this as the family computer to manage all 4 mp3 players), and one for the speakers (we like tunes).

So as it is we have to disconnect something to update the mp3 players - no problem on my part, I`m a shortcut kind of guy but it doesn`t help the wife & kids.

To the OP, if you decide to go down this route, there is a little bit of command line tweaking that needs to be done - ie you have to make sure your internal wireless card doesn`t claim the networking at boot. Feel free to pm me and I`ll let you know how to do it.

Why can`t people leave well alone?

---

### Post by slakkie on 2009-08-05
You could switch the channel you are on, experienced this myself. Had really slow downloads, switched to another channel (less busy), speed went up..

---

### Post by nothingspecial on 2009-08-05
Thanks for that but i have tried.

Honestly, it`s not such an issue for me.

--- but if this were my only system,I`d be p*****d ---

The way I have it now is fine but I pity users who only have this wireless card.

---

### Post by slakkie on 2009-08-05
This is my laptop from work, works like a dream:

```

wlan0     unknown bit-rate information.
          Current Bit Rate=54 Mb/s


```

---

### Post by nothingspecial on 2009-08-05
Are you using hardy, like your sig says?

---

### Post by slakkie on 2009-08-05
I just upgraded a couple of days ago to jaunty. Can restore a backup once my downloads are done (need to backup Jaunty first) and check again.

---

### Post by nothingspecial on 2009-08-05
Please do.

Maybe I`ve not followed your how to right.

---

### Post by slakkie on 2009-08-05
> **nothingspecial said:**
> Please do.

Maybe I`ve not followed your how to right.

I will let you know later this evening or tomorrow k?

---

### Post by nothingspecial on 2009-08-05
Thanks  :D

---

### Post by slakkie on 2009-08-05
```

sudo iwlist wlan0 rate
[sudo] password for wesleys:
wlan0     unknown bit-rate information.
          Current Bit Rate=54 Mb/s

Distributor ID: Ubuntu
Description:    Ubuntu 8.04.3 LTS
Release:        8.04
Codename:       hardy

lspci| grep -i network
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

lsmod | grep iwl
iwl3945                96244  0
lbm_iwl_mac80211      242292  1 iwl3945
rfkill                  8596  2 iwl3945
led_class               6020  1 iwl3945
lbm_iwl_cfg80211       33248  2 iwl3945,lbm_iwl_mac80211


```

Here you go.

That is funny, Hardy tells me something different from Jaunty in respect to lsbpci and the network component..

-edit-
Be very grateful, my backup of 9.04 was corrupted, had to switch back to hardy and redo my upgrades :( Now at 8.10.. 
Minor set back

lspci @ 8.10
```

0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

---

