---
title: "problems with wireless Netgear card wg511"
date: 2006-01-07
forum: Hardware &amp; Laptops
---

### Post by amitab09 on 2006-01-07
Hi,

I have been having problems installing my Netgear wireless card WG511.  (Netgear WG511 v1, made in china) I am a newbie with Linux and chose the Ubuntu dist because of its community support. I have tried many ways of getting this card to work but have got nowhere. I have read that I need to use ndiswrapper to get the card working because netgear only provide exe files and no ini files.

When following the instructions from ndiswrappers installation page (link [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)) i cant seem to get any further than the make part of the compile and install part. This is what i get when i try:

root@kuks:~/Desktop/ndiswrapper-1.7# make
make -C driver
make[1]: Entering directory `/root/Desktop/ndiswrapper-1.7/driver'
Can't find kernel sources in /lib/modules/2.6.12-9-386/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/root/Desktop/ndiswrapper-1.7/driver'
make: *** [all] Error 2

root@kuks:~/Desktop/ndiswrapper-1.7# make install
make -C driver install
make[1]: Entering directory `/root/Desktop/ndiswrapper-1.7/driver'
Can't find kernel sources in /lib/modules/2.6.12-9-386/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/root/Desktop/ndiswrapper-1.7/driver'
make: *** [install] Error 2

Could someone help me to get this card working. I am completely lost and need someone to walk me through this one. Many thanks in advance. 

Amit

---

### Post by Titus A Duxass on 2006-01-08
As it says in the report, it can't find the kernel sources.

You probably don't have them installed.

Use Synaptic and search for kernel Sources then select the appropriate kernel sources and Kernel Header.

Install these and then run ndiswrapper.

---

### Post by mabster on 2006-01-08
I have just (as of last night) gone through this process myself so I might be able to help.  In the ndiswrapper sourceforge wiki instructions it talks about installing from source, but you don't really need to do this under Ubuntu.

In the bit where it talks about downloading and installing ndiswrapper, you can just do this (the versions found in the packages below appear to be sufficient to get the device to work):

```
apt-get install wireless-tools
apt-get install ndiswrapper-utils
```

From there you should be able to follow on from the 'Install Windows Driver'.  You might find like I did that the driver the eventually link to had a broken link, but you'll be able to find it easily enough.

Note that the instructions from the ndiswrapper wiki are just enough to get the device working for the single session.

For more sources of information:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu) and
[https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto) and
[https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)

The bottom-most link will go through how to get the device to enable as your system boots up (which appears to slow down the boot quite considerably but that's another issue).

Hope I actually helped there ;)

---

### Post by amitab09 on 2006-01-08
Thanks for your replies guys. I managed to get the ini and sys files for the official driver (that worked on my windows xp system) from the exe installation file from netgear and get them wrapped by ndiswrapper. I checked by looking into the /etc/mdiswrapper folder and I also ran the command:

ndiswrapper -l 

Installed ndis drivers:
netwg511        driver present, hardware present

I also typed in the iwconfig command and got the following:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      NOT READY!  ESSID:"belkin"
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Tx-Power=31 dBm   Sensitivity=0/200
          Retry min limit:0   RTS thr=0 B   Fragment thr=0 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Im not sure what to do now. Could someone please assist me. Thanks

---

### Post by mabster on 2006-01-09
I notice that your driver name is different to mine.  I grabbed the mrv8000c driver that the intructions told me to grab.

Was your lspci identifier value (or whatever it's called ; ) 11ab:1faa?  Did you install the mrv8000c driver and rename or grab it off the CD?

---

