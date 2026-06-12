---
title: "iwlwifi_mac80211/iwl3945 install packet injection driver"
date: 2008-11-13
forum: Hardware
---

### Post by 325i08 on 2008-11-13
Hi Iam trying to get my intel wifi card setup for packet injection...

What I do Know about my system:
Compal el81-LAPTOP
Ubuntu Hardy 2.6.24-16-generic
Intel/Proset Wireless 802.11abg 
  -DRIVER: iwl3945 
  -STACK : mac80211

*note that aircrack-ng.org confirms that this wifi device allows packet   injection.

TERMINAL COMMAND 
    dmesg (Confirmed that my wifi eth1 was working properly)
    lsmod (Stated that My device is using the IWL3945 Driver)

I searched aircrack-ng.org for IWL3945
I was directed to this Link: 

[http://aircrack-ng.org/doku.php?id=iwl3945&s=iwl3945]("http://aircrack-ng.org/doku.php?id=iwl3945&s=iwl3945")

> Installing and patching compat-wireless

   1.
      Install your kernel headers and sources, as well as all packages required for building kernel modules.
   2.
      Download compat-wireless from here. For 2.6.26 and older, use compat-wireless-old, for newer versions (currently 2.6.27-rcX), use compat-wireless-2.6.
   3.
      Untar the archive to your home directory. This will create a dated directory ~/compat-wireless-DATE, where DATE is the build date of the package.
   4.
      Download the fragmentation patch, and apply it to the compat-wireless package. This is needed to make attacks -5 and -7 work.
   5.
      Cd to the compat-wireless directory, and run &#8220;make&#8221; to build the package.
   6.
      Install the package with &#8220;make install&#8221;, then load it with &#8220;make load&#8221;.
   7.
      If you get errors during &#8220;make load&#8221;, reboot and all should work.



I am really Confused here and need help on proceeding with compat-wireless driver and furthering my setup for AIRCRACK-NG

*I UNDERSTAND THAT THIS IS A NETWORK SECURITY TOOL AND PLAN TO USE IT ETHICALLY.

---

