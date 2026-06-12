---
title: "Atheros: ath9k: disconnections"
date: 2010-01-08
forum: Hardware
---

### Post by isterios on 2010-01-08
I am running ubuntu 2.6.31-17 (64 bits), from an acer laptop with Atheros AR928X wireless device. 

I am running Wicd for the network connections. I am using wpa2 personal protocol.

The problem is I have regularly disconnections (the connection often starts normally after reboot), and here is what I can read in logs:
$ dmesg:

ath9k: timeout (10000 us) on reg 0x806c
ath9k: RX failed to go idle in 10 ms RSXM=0xf02401
wlan0: deauthenticated from (my router mac address)
wlan0: direct probe to AP (my router mac address)
wlan0: direct probe responded
wlan0: authenticated with AP (my router mac address)
wlan0: authenticated
wlan0: associate with AP (my router max address)
wlan0: RX ReassocResp from (my router mac address)
wlan0: asscoiated

After this, if I try:
sudo dhclient wlan0:

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval x (this line appears many times)
receive_packet failed on wlan0: Network is down
No DHCPOFFERS received
No working leases in persistent database - sleeping.

So once I am disconnected, I cannot connect again, until I reboot.

My router works perfectly with two other laptops using others wifi devices (no Atheros).

I uninstalled network-manager and installed Wicd a couple of days ago, but the problem was similar with network-manager.

I tried to comment "blacklist ath_pci" in the blacklist-ath_pci.conf file,  but no difference.

Do you have ideas I could try?

Thank you.

---

### Post by drpjkurian on 2010-01-09
> **isterios said:**
> I am running ubuntu 2.6.31-17 (64 bits), from an acer laptop with Atheros AR928X wireless device. 

I am running Wicd for the network connections. I am using wpa2 personal protocol.

The problem is I have regularly disconnections (the connection often starts normally after reboot), and here is what I can read in logs:
$ dmesg:

ath9k: timeout (10000 us) on reg 0x806c
ath9k: RX failed to go idle in 10 ms RSXM=0xf02401
wlan0: deauthenticated from (my router mac address)
wlan0: direct probe to AP (my router mac address)
wlan0: direct probe responded
wlan0: authenticated with AP (my router mac address)
wlan0: authenticated
wlan0: associate with AP (my router max address)
wlan0: RX ReassocResp from (my router mac address)
wlan0: asscoiated

After this, if I try:
sudo dhclient wlan0:

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval x (this line appears many times)
receive_packet failed on wlan0: Network is down
No DHCPOFFERS received
No working leases in persistent database - sleeping.

So once I am disconnected, I cannot connect again, until I reboot.

My router works perfectly with two other laptops using others wifi devices (no Atheros).

I uninstalled network-manager and installed Wicd a couple of days ago, but the problem was similar with network-manager.

I tried to comment "blacklist ath_pci" in the blacklist-ath_pci.conf file,  but no difference.

Do you have ideas I could try?

Thank you.

Hi
Please install the following packages by synaptic package manager
They are linux-backports-modules-karmic-generic and linux-backports-modules-wireless-karmic-generic.

This might help you. This solution was given by coffeecat

Dr Kurian

---

### Post by isterios on 2010-01-09
Thanks drpjkurian but I already installed them.

Here is the result of dmesg when the connection is ok (before disconnection):

.
[   28.467633] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.597828] ppdev: user-space parallel port driver
[   34.369907]   alloc irq_desc for 29 on node 0
[   34.369915]   alloc kstat_irqs on node 0
[   34.369937] atl1c 0000:08:00.0: irq 29 for MSI/MSI-X
[   34.370760] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   37.921012] atl1c 0000:08:00.0: irq 29 for MSI/MSI-X
[   37.921827] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.291432] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.862071] wlan0: direct probe to AP "myrouteraddress" (try 1)
[   40.060048] wlan0: direct probe to AP "myrouteraddress" (try 2)
[   40.064652] wlan0: direct probe responded
[   40.064661] wlan0: authenticate with AP "myrouteraddress" (try 1)
[   40.066553] wlan0: authenticated
[   40.066584] wlan0: associate with AP "myrouteraddress" (try 1)
[   40.070307] wlan0: RX AssocResp from "myrouteraddress" (capab=0x431 status=0 aid=1)
[   40.070315] wlan0: associated
[   40.082257] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   40.102517] Intel AES-NI instructions are not detected.
[   40.131883] padlock: VIA PadLock not detected.
[   50.192534] wlan0: no IPv6 routers present

---

### Post by drpjkurian on 2010-01-09
Hi
Please discuss this issue with pytheas...the wizard in wireless

Dr Kurian

---

