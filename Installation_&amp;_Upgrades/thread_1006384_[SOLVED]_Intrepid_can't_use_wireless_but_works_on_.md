---
title: "[SOLVED] Intrepid can't use wireless but works on older kernel, how to copy to new ke"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by ubunny on 2008-12-09
> Final Update: Read the last post (#13) to get this solved quickly.  I ended up abandoning ath5k and using madwifi for greatest wireless success in Ubuntu Ibex 8.10.  Cheers

The new install doesn't recognize ath0 or atheros although is shows pcmcia in dmesg.  So I'm booting into the previous kernel in ibex and that works with the card. (proxim gold 8470-wd)

uname -a
2.6.24-21-386

instead of
2.6.25-2-386

inside the /lib/modules/2.6.24-21-386 are all the madwifi files also under ubuntu/wireless are more.  Should I cp over these files to the newer kernel directory or is it different?  Am I asking for trouble? ;)

has madwifi
/lib/modules/2.6.24-21-386$ ls
initrd         modules.ccwmap       modules.isapnpmap  modules.symbols
kernel         modules.dep          modules.ofmap      modules.usbmap
madwifi        modules.ieee1394map  modules.pcimap     ubuntu
modules.alias  modules.inputmap     modules.seriomap   volatile

does not have madwifi
:/lib/modules/2.6.25-2-386$ ls
build   modules.alias   modules.ieee1394map  modules.ofmap   modules.seriomap
initrd  modules.ccwmap  modules.inputmap     modules.order   modules.symbols
kernel  modules.dep     modules.isapnpmap    modules.pcimap  modules.usbmap

Thanks

---

### Post by Pumalite on 2008-12-09
Did you recently try to upgrade?
This is Intrepid Ibex:
pumalite@pumalite-desktop:~$ uname -a
Linux pumalite-desktop 2.6.27-10-generic #1 SMP Fri Nov 21 19:19:18 UTC 2008 x86_64 GNU/Linux
pumalite@pumalite-desktop:~$

---

### Post by ubunny on 2008-12-10
copy paste module files, 
depmod -a, 
init 6 
...didn't work.

I'm running Intrepid with the previous kernel (as per the third grub menu option) so that the wireless card still works (and I can still work too).  I thought that the ath5k (madwifi replacement) was supposed to be in the new kernel?  I tried modinfo below with no result.  When I'm in the new kernel 2.6.25-2-386, modinfo -k `uname -r` ath_pci is there but it won't detect the card.  lshw -C network just reports the card as unclaimed or something like that.

Currently;

$ uname -r
2.6.24-21-386

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid

$ modinfo -k 2.6.25-2-386 ath5k
modinfo: could not find module ath5k (obviously)

all this was a recent dist-upgrade from hardy.  I don't fear a lesser kernel since I'm using an old PIII laptop.

If you have a working internet connection with your Intrepid, run these commands and reply.  I'd like to compare.  Or better yet I'd like a solution ;)

lsb_release -a
lshw -C network
modinfo -k `uname -r` ath5k

---

### Post by ubunny on 2008-12-22
no luck.  tried making a new kernel but still the pcmcia pccard wireless is "unclaimed" when you type lshw -C network.  

-why is my pccard unclaimed
-how can I check ath5k for my proxim card if the modinfo -k `uname -r` ath5k does not exist in ibex???

---

### Post by ubunny on 2008-12-22
looking at the release note again I get this gem

[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

"""Atheros ath5k wireless driver not enabled by default

The version of the ath5k driver for Atheros wireless devices included in Linux 2.6.27 interferes with the use of the madwifi driver for some wireless devices and as a result has been disabled by default. Many Atheros chipsets will work correctly with the madwifi driver, but some newer chipsets may not, and the madwifi driver may not work with WPA authentication. If you have an Atheros device that does not work with madwifi, you will want to install the linux-backports-modules-intrepid-generic package, which includes an updated version of the ath5k driver. While not installed by default, this linux-backports-modules-intrepid-generic package is included on the Ubuntu 8.10 CD and DVD images for ease of installation. """ 

I need to install this linux-backports-modules-intrepid-generic and see if that works

---

### Post by Pumalite on 2008-12-22
You are running Hardy; not Intrepid.
Open up all your repos and do:
sudo apt-get update
sudo apt-get dist-upgrade
Reboot
Post:
sudo lshw -C network

---

### Post by ubunny on 2008-12-22
for petes' sake and the third time, no, I'm not running Hardy.  I'm running Intrepid.  Intrepid is the collection of packages that work with a kernel, but it's not a kernel.  I'm not at my linux machine right now but from my previous posts you can read:

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 8.10
Release: 8.10
Codename: intrepid

Thus I'm running Intrepid and decided to run on the prior kernel 24 not 25 as per the 3rd grub menu so that I have wireless working.  I even made my own kernel with 2.6.27 but it didn't have ath5k loaded either.  I'll probably just try a custom kernel again with madwifi/ath5k.  It would still be Intrepid after that unless I change the packages.

I'll load the backports as per the release notes regarding this issue and update this thread after a Merry Christmas.  

edit:
this link seems particularly cogent : [http://people.uleth.ca/~daniel.odonnell/Blog/installing-ubuntu-810-intrepid-ibex-on-acer-aspire-one-netbook#wireless](http://people.uleth.ca/~daniel.odonnell/Blog/installing-ubuntu-810-intrepid-ibex-on-acer-aspire-one-netbook#wireless)

It appears this should keep my drivers for Atheros 5xxx series.

> sudo apt-get install linux-backports-modules-intrepid-generic

I'll run this when I have the chance.

Cheers

---

### Post by ubunny on 2008-12-31
ok, ran command as stated above.  It downloaded kernel modules for 2.6.27-9 along with generic intrepid modules and updated grub.  I had to manually edit /boot/grub/menu.1st as I had it customized to run the 2.6.24-21 first (last working kernel with wireless)

rebooted and computer hung on selecting new 2.6.27-9-generic kernel.  Screen blanked out.

rebooted and this time selected 2.6.27-9-generic (recovery mode) and then selected resume to get gui loaded.  Light to pccard only had power lit but no activity.

ran terminal and iwconfig reported no ath0.  not good.

ran System > Administration > Hardware Drivers and the Atheros driver was listed as installed but not active?  I hit the Deactive button, then Active again

ran terminal and iwconfig reported ath0 there.  yay

ran iwconfig script and browser and got connected.

Cool. On a newer kernel as well.  dmesg shows ath5k_pci with the Atheros driver.  Only issue is that the pccard activity light is not active?

Any thoughts?

---

### Post by ubunny on 2008-12-31
del

---

### Post by ubunny on 2008-12-31
furthermore to this post, I was able to correct the 2.6.27-9-generic kernel boot freeze by redoing the grub menu in /boot/grub/menu.1st .  I copied it to mv menu.1st menu.1st_dec31 then ran sudo update-grub .  Now can boot to any kernel as desired.

another forum post that has two options, the backports or a compat bz2 file install noted here:

[http://ubuntuforums.org/showthread.php?t=964836]("http://ubuntuforums.org/showthread.php?t=964836")

it was correct in that for me to use the internet I have to load the driver each boot, so I'm opting for the second option and will see how that goes.

it would appear to take the approach to compile the wireless drivers into the kernel as opposed to just the ath5k loader.  If I do this with the other kernels on my machine perhaps they can all have wireless.

I'll check.

---

### Post by ubunny on 2008-12-31
the compat-wireless approach I feel works better, so I got rid of the initial steps with the 2.6.27-9 backports and kernel, and just updated my logged into 2.6.27.8-p3 kernel, and ran the compat-wireless install again.  The compat-wireless install gives me a "sudo athload ath5k" command which I add to my wireless scripts, and that works fine without all so much overhead.

note to self: LED activity lights not active.  read about sysctl -w dev.wifi0.ledpin=3 but wifi0 is no longer in ifconfig (its wmaster0), nor is the ledpin command available.  

Cheers

---

### Post by ubunny on 2008-12-31
Loaded and ran compat wireless kernel package from above link and it did work for a while on kernel 2.6.27.8-p3 custom kernel and 2.6.27-9-generic, however eventually after 1 day cannot get connectivity again, or it kicks out in a few minutes.

So I went back to kernel 2.6.24-21 on my grub menu and all is well in wireless land.

until "they" can get ath5k to work as well as madwifi I can't see why (or how) I can update the kernel level and keep the madwifi drivers for my computer.  They're supposed to be the same but clearly they fail on these points:

ath5k is UNCLAIMED and basically useless without installing the compat driver package
ath5k did not resurrect on backports
ath5k has no led network lights working
ath5k initially reports a lot of noise 
ath5k when it did work is not stable enough to use (one day in my case)

I'm now full circle.  Technically the solution worked, but not long enough or stable enough.  A nice experience but I was hoping for a different outcome :(

---

### Post by ubunny on 2009-01-01
I got this to finally work to my satisfaction by replacing the wonky ath5k module with madwifi instead.  Details below:

here's some information on my card:
```

$ lspci -nn | grep -i atheros
0b:00.0 Ethernet controller [0200]: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter [168c:0013] (rev 01)

```

lsmod at the time reported ath5k and various dependencies using ath5k
run it to see where you are in your troubleshooting case:
```

lsmod | grep -e ath

```

While I could connect with ath5k it was slow and unreliable.  Google to the rescue..

"ath5k slow as molassus" post referred to slackware but easy to adjust for ubuntu here:
[http://www.linuxquestions.org/questions/linux-networking-3/slackware-12.2-ath5k-is-slow-as-molassus-693170/]("http://www.linuxquestions.org/questions/linux-networking-3/slackware-12.2-ath5k-is-slow-as-molassus-693170/")

Here's another link from 2006.  It's actually outdated but it made me suddenly realize to myself that I ALREADY had madwifi installed!!! Duh..
[http://hamzakc.wordpress.com/2006/12/11/atheros-wireless-setup-ubuntu/]("http://hamzakc.wordpress.com/2006/12/11/atheros-wireless-setup-ubuntu/")

So if I already have the software installed while running in different kernels, then it's only THIS kernel that won't have the right modules loaded in its modules list.  

I had installed madwifi previously in Hardy, so sure enough I had the madwifi.sh script already in a personal ~/bin directory....when I looked! D'oh  

While I was still connected slightly with ath5k then, I ran this madwifi.sh script.  It updated the svn of itself from madwifi-project site then installed modules ath_pci, ath_hal and detected my wireless card.

If you otherwise do not have madwifi installed go get the download here: [http://madwifi-project.org/]("http://madwifi-project.org/").  It will then update itself with the latest version everytime you run the madwifi.sh script.

1) run your previous madwifi.sh script whereever you put it..
```

~/bin$ sudo madwifi.sh
...

```

(this takes a while)

2) I go verify the loaded modules and I have ath_pci etc loaded at last
```
lsmod | grep -e ath
```


3) However at this point I had ath_pci AND ath5k shown here, so lets reset this from scratch to prevent conflicts.  Any error msgs here I'm ignoring since it would just meant it isn't there.  Remove modules:
```
 sudo modprobe -r ath_pci ath5k ath9k 
```

4) Go and reload ath_pci again, then verify it loaded.
```

sudo modprobe ath_pci

```

only last few lines interesting

```

dmesg | grep -e ath

[   13.588107] md: multipath personality registered for level -4
[  751.803871] ath5k 0000:0b:00.0: enabling device (0000 -> 0002)
[  751.807372] ath5k 0000:0b:00.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[  751.809104] ath5k 0000:0b:00.0: registered as 'phy0'
[  752.198058] ath5k phy0: Atheros AR5213A chip found (MAC: 0x59, PHY: 0x43)
[  752.198076] ath5k phy0: RF2112B 2GHz radio found (0x46)
[  752.206582] udev: renamed network interface wlan0 to ath0
[  754.611374] ath0: direct probe to AP 00:1b:11:61:ac:95 try 1
[  754.808058] ath0: direct probe to AP 00:1b:11:61:ac:95 try 2
[  755.008045] ath0: direct probe to AP 00:1b:11:61:ac:95 try 3
[  755.208040] ath0: direct probe to AP 00:1b:11:61:ac:95 timed out
[  790.125680] ath5k phy0: noise floor calibration timeout (2437MHz)
[  846.950510] ath0: direct probe to AP 00:0f:3d:51:3f:b4 try 1
[  846.956226] ath0 direct probe responded
[  846.956263] ath0: authenticate with AP 00:0f:3d:51:3f:b4
[  846.961151] ath0: authenticated
[  846.961180] ath0: associate with AP 00:0f:3d:51:3f:b4
[  846.968138] ath0: RX AssocResp from 00:0f:3d:51:3f:b4 (capab=0x431 status=0 aid=2)
[  846.968164] ath0: associated
[  897.331559] ath5k phy0: noise floor calibration timeout (2437MHz)
[  968.331048] ath5k phy0: noise floor calibration timeout (2437MHz)
[  979.331047] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1041.331082] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1052.330979] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1083.331064] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1156.330980] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1177.331015] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1228.331672] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1269.330882] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1351.330865] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1373.330880] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1395.331663] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1456.331012] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1477.331013] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1488.331161] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1499.331161] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1510.331195] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1521.331095] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1542.331047] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1563.332051] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1574.330898] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1595.330899] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1606.331458] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1617.332975] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1638.331210] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1649.331212] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1660.331639] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1671.331016] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1682.331264] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1724.330951] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1890.866487] ath0: deauthenticated (Reason: 7)
[ 1891.864074] ath0: direct probe to AP 00:0f:3d:51:3f:b4 try 1
[ 1891.866402] ath0 direct probe responded
[ 1891.866424] ath0: authenticate with AP 00:0f:3d:51:3f:b4
[ 1891.868497] ath0: authenticated
[ 1891.868514] ath0: associate with AP 00:0f:3d:51:3f:b4
[ 1891.871235] ath0: RX ReassocResp from 00:0f:3d:51:3f:b4 (capab=0x431 status=0 aid=3)
[ 1891.871247] ath0: associated
[ 1895.331211] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 1979.033526] ath0: deauthenticated (Reason: 7)
[ 1980.032054] ath0: direct probe to AP 00:0f:3d:51:3f:b4 try 1
[ 1980.232056] ath0: direct probe to AP 00:0f:3d:51:3f:b4 try 2
[ 1980.250237] ath0 direct probe responded
[ 1980.250251] ath0: authenticate with AP 00:0f:3d:51:3f:b4
[ 1980.264591] ath0: authenticated
[ 1980.264602] ath0: associate with AP 00:0f:3d:51:3f:b4
[ 1980.277867] ath0: RX ReassocResp from 00:0f:3d:51:3f:b4 (capab=0x431 status=0 aid=4)
[ 1980.277877] ath0: associated
[ 2055.833089] ath0: deauthenticated (Reason: 7)
[ 2056.832101] ath0: direct probe to AP 00:0f:3d:51:3f:b4 try 1
[ 2056.844839] ath0 direct probe responded
[ 2056.844852] ath0: authenticate with AP 00:0f:3d:51:3f:b4
[ 2056.862841] ath0: authenticated
[ 2056.862854] ath0: associate with AP 00:0f:3d:51:3f:b4
[ 2056.868228] ath0: RX ReassocResp from 00:0f:3d:51:3f:b4 (capab=0x431 status=0 aid=4)
[ 2056.868240] ath0: associated
[ 2138.627194] ath0: deauthenticated (Reason: 7)
[ 2139.624059] ath0: direct probe to AP 00:0f:3d:51:3f:b4 try 1
[ 2139.824084] ath0: direct probe to AP 00:0f:3d:51:3f:b4 try 2
[ 2139.845105] ath0 direct probe responded
[ 2139.845118] ath0: authenticate with AP 00:0f:3d:51:3f:b4
[ 2139.846821] ath0: authenticated
[ 2139.846833] ath0: associate with AP 00:0f:3d:51:3f:b4
[ 2139.849106] ath0: RX ReassocResp from 00:0f:3d:51:3f:b4 (capab=0x431 status=0 aid=4)
[ 2139.849116] ath0: associated
[ 2229.185933] ath0: deauthenticated (Reason: 7)
[ 2230.184058] ath0: direct probe to AP 00:0f:3d:51:3f:b4 try 1
[ 2230.384040] ath0: direct probe to AP 00:0f:3d:51:3f:b4 try 2
[ 2230.389129] ath0 direct probe responded
[ 2230.389142] ath0: authenticate with AP 00:0f:3d:51:3f:b4
[ 2230.392901] ath0: authenticated
[ 2230.392913] ath0: associate with AP 00:0f:3d:51:3f:b4
[ 2230.395286] ath0: RX ReassocResp from 00:0f:3d:51:3f:b4 (capab=0x431 status=0 aid=4)
[ 2230.395297] ath0: associated
[ 2308.824427] ath0: deauthenticated (Reason: 7)
[ 2309.824054] ath0: direct probe to AP 00:0f:3d:51:3f:b4 try 1
[ 2309.827027] ath0 direct probe responded
[ 2309.827041] ath0: authenticate with AP 00:0f:3d:51:3f:b4
[ 2309.829396] ath0: authenticated
[ 2309.829408] ath0: associate with AP 00:0f:3d:51:3f:b4
[ 2309.831642] ath0: RX ReassocResp from 00:0f:3d:51:3f:b4 (capab=0x431 status=0 aid=3)
[ 2309.831652] ath0: associated
[ 2395.375956] ath0: deauthenticated (Reason: 7)
[ 2396.372079] ath0: direct probe to AP 00:0f:3d:51:3f:b4 try 1
[ 2396.376419] ath0 direct probe responded
[ 2396.376438] ath0: authenticate with AP 00:0f:3d:51:3f:b4
[ 2396.387083] ath0: authenticated
[ 2396.387096] ath0: associate with AP 00:0f:3d:51:3f:b4
[ 2396.389404] ath0: RX ReassocResp from 00:0f:3d:51:3f:b4 (capab=0x431 status=0 aid=4)
[ 2396.389414] ath0: associated
[ 2479.028387] ath0: deauthenticated (Reason: 7)
[ 2480.028055] ath0: direct probe to AP 00:0f:3d:51:3f:b4 try 1
[ 2480.032902] ath0 direct probe responded
[ 2480.032917] ath0: authenticate with AP 00:0f:3d:51:3f:b4
[ 2480.034657] ath0: authenticated
[ 2480.034669] ath0: associate with AP 00:0f:3d:51:3f:b4
[ 2480.038970] ath0: RX ReassocResp from 00:0f:3d:51:3f:b4 (capab=0x431 status=0 aid=4)
[ 2480.038981] ath0: associated
[ 2556.104057] ath0: No ProbeResp from current AP 00:0f:3d:51:3f:b4 - assume out of range
[ 2646.331688] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 2677.330668] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 2768.330669] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 2810.330668] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 2841.330668] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 2886.705153] ath0: direct probe to AP 00:0f:3d:51:3f:b4 try 1
[ 2886.904085] ath0: direct probe to AP 00:0f:3d:51:3f:b4 try 2
[ 2887.104057] ath0: direct probe to AP 00:0f:3d:51:3f:b4 try 3
[ 2887.304040] ath0: direct probe to AP 00:0f:3d:51:3f:b4 timed out
[ 2977.330667] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 2988.330767] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 2999.330833] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 3031.330718] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 3042.330667] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 3047.852318] ath0: direct probe to AP 00:0f:3d:51:3f:b4 try 1
[ 3047.855570] ath0 direct probe responded
[ 3047.855592] ath0: authenticate with AP 00:0f:3d:51:3f:b4
[ 3047.937048] ath0: authenticated
[ 3047.937074] ath0: associate with AP 00:0f:3d:51:3f:b4
[ 3047.979982] ath0: RX AssocResp from 00:0f:3d:51:3f:b4 (capab=0x431 status=0 aid=4)
[ 3047.979997] ath0: associated
[ 3138.331111] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 3245.757351] ath0: deauthenticated (Reason: 7)
[ 3246.756056] ath0: direct probe to AP 00:0f:3d:51:3f:b4 try 1
[ 3246.767376] ath0 direct probe responded
[ 3246.767390] ath0: authenticate with AP 00:0f:3d:51:3f:b4
[ 3246.769598] ath0: authenticated
[ 3246.769610] ath0: associate with AP 00:0f:3d:51:3f:b4
[ 3246.778710] ath0: RX ReassocResp from 00:0f:3d:51:3f:b4 (capab=0x431 status=0 aid=4)
[ 3246.778720] ath0: associated
[ 3279.333089] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 3328.017192] ath0: deauthenticated (Reason: 7)
[ 3329.016054] ath0: direct probe to AP 00:0f:3d:51:3f:b4 try 1
[ 3329.019449] ath0 direct probe responded
[ 3329.019462] ath0: authenticate with AP 00:0f:3d:51:3f:b4
[ 3329.021102] ath0: authenticated
[ 3329.021114] ath0: associate with AP 00:0f:3d:51:3f:b4
[ 3329.023411] ath0: RX ReassocResp from 00:0f:3d:51:3f:b4 (capab=0x431 status=0 aid=4)
[ 3329.023420] ath0: associated
[ 3402.821697] ath0: deauthenticated (Reason: 7)
[ 3403.820059] ath0: direct probe to AP 00:0f:3d:51:3f:b4 try 1
[ 3403.827452] ath0 direct probe responded
[ 3403.827473] ath0: authenticate with AP 00:0f:3d:51:3f:b4
[ 3403.855317] ath0: authenticated
[ 3403.855338] ath0: associate with AP 00:0f:3d:51:3f:b4
[ 3403.858226] ath0: RX ReassocResp from 00:0f:3d:51:3f:b4 (capab=0x431 status=0 aid=4)
[ 3403.858241] ath0: associated
[ 3500.331687] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 3511.333916] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 3522.332710] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 3544.332678] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 3555.331790] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 3566.333417] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 3578.666806] ath0: deauthenticating by local choice (reason=3)
[ 3916.166131] ath_hal: module license 'Proprietary' taints kernel.
[ 3978.183866] ath5k 0000:0b:00.0: PCI INT A disabled
[ 4108.627562] ath_pci 0000:0b:00.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[ 4108.820795] MadWifi: ath_attach: Switching rfkill capability off.
[ 4109.277779] ath_pci: wifi0: Atheros 5212: mem=0x38000000, irq=11


```

verify I'm only on ath_pci not ath5k.  If I see any ath5k I just run sudo modprobe -r ath5k or rmmod ath5k again etc.

```
$ lsmod | grep -e ath
ath_rate_sample        13952  1 
ath_pci               225464  0 
wlan                  230000  5 wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               250592  3 ath_rate_sample,ath_pci
multipath               6912  0 
md_mod                 81428  6 raid10,raid456,raid1,raid0,multipath,linear

```

Looks good.  No more ath5k.  Running iwconfig reports wifi0 not wmaster0 so again looks like madwifi not ath5k.

re-run my normal connection script
or
```

sudo ifconfig ath0 down
sudo iwconfig ath0 essid "Somthing" key NNN
sudo ifconfig ath0 up
sudo dhclient ath0

```

Connects.

Now online at last with madwifi on Ubuntu 8.10 and custom kernel 2.6.27.8-p3 (would work with any kernel thanks to madwifi.sh script installer)

As for wifi issues, 
-The card now has happy blinky network lights working as per normal operation under previous kernels.
-Connection speed is noticeably faster without disconnects.
-I had left it on all night before going to a New Years' bash and it was still working when I got back *much* later.
-I now have an update method here in case of further upgrade wireless harassment.

Happy New Year, this puppy is done.
:D

---

