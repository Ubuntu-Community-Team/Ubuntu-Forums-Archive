---
title: "Any solve to the SR9700 problem"
date: 2024-08-21
forum: Hardware
---

### Post by 123nbom on 2024-08-21
So I have this SR9700, it does not support Linux.
After installing Linux, I found that this device is not compatible. I tried various methods, such as running it in bottles and entering commands in the terminal, but none of them worked.
The problem is that Linux only recognizes this device as a CD drive. I don't want that-I just want the device to work with Linux.
Could you help me with this?
I contacted the company that manufactured this device, but they didn't provide a helpful response. They simply mentioned that the driver was added in Linux 3.12. I messaged them again about it; they informed me that the device is too  old and only support windows, hence it does not support the  Linux apps.
Here source;
[https://www.kernelconfig.io/config_usb_net_sr9700](https://www.kernelconfig.io/config_usb_net_sr9700)
[https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux.git/tree/drivers/net/usb/sr9700.c?h=v6.10.6](https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux.git/tree/drivers/net/usb/sr9700.c?h=v6.10.6)
Question: how to install this kernel code?

---

### Post by Doug S on 2024-08-24
That kernel code is included in the kernel by default. The driver is a module, which is normal. The crc stuff is built in.

```
doug@s19:~/kernel/linux$ grep CONFIG_USB_NET_SR9700 /boot/config-6.8.0-35-generic
CONFIG_USB_NET_SR9700=m
doug@s19:~/kernel/linux$ grep CONFIG_CRC32= /boot/config-6.8.0-35-generic
CONFIG_CRC32=y
```

I wonder if the module is getting loaded when required. You could check after trying your device and/or force load it:

```

doug@s19:~/kernel/linux$ lsmod | grep sr97
doug@s19:~/kernel/linux$ sudo modprobe sr9700
[sudo] password for doug:
doug@s19:~/kernel/linux$ lsmod | grep sr97
sr9700                 20480  0
usbnet                 61440  1 sr9700
mii                    20480  2 sr9700,usbnet

```

---

### Post by 123nbom on 2024-08-24
Must i try the second code in terminal or the first one? I've unplug the device and plug it again-But it didnt work (Ubuntu detected it as a CD drive). What do i do now?
1-EDIT: is there a way to load the driver from the kernel itself?  Maybe install the driver from the kernel.

---

### Post by Doug S on 2024-08-25
> **123nbom said:**
> is there a way to load the driver from the kernel itself?

Yes, you can force load the driver module via the command I posted before:

```

doug@s19:~/kernel/linux$ [COLOR="#FF0000"]sudo modprobe sr9700[/COLOR]

```

And then you can check that it is a loaded module via the subsequent command I posted earlier:

```

doug@s19:~/kernel/linux$ [COLOR="#FF0000"]lsmod | grep sr97[/COLOR]
sr9700                 20480  0
usbnet                 61440  1 sr9700
mii                    20480  2 sr9700,usbnet

```

---

### Post by 123nbom on 2024-08-25
The device didnt work

---

### Post by snowcrash1 on 2024-08-26
bump

---

### Post by 123nbom on 2024-08-30
Can anyone make the driver for me.
I have the .c file, its done - its need just need the other things that i dont know
Ubuntu 20.04.4 LTS 
[https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux.git/tree/drivers/net/usb/sr9700.c?h=v6.10.6](https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux.git/tree/drivers/net/usb/sr9700.c?h=v6.10.6)

---

### Post by Doug S on 2024-08-30
As explained in my previous posts on this thread, you have the driver. As far as I know, there is nothing for us to do to help you further.

What kernel version are you using now?

EDIT 3: If I understand correctly, you think you need the latest version of the driver that include this commit from July 25th and that has been back-ported to kernel 6.10.6:
```

doug@s19:~/kernel/linux$ git show 08f3a5c38087
commit 08f3a5c38087d1569e982a121aad1e6acbf145ce
Author: Ma Ke <make24@iscas.ac.cn>
Date:   Thu Jul 25 10:29:42 2024 +0800

    net: usb: sr9700: fix uninitialized variable use in sr_mdio_read

    It could lead to error happen because the variable res is not updated if
    the call to sr_share_read_word returns an error. In this particular case
    error code was returned and res stayed uninitialized. Same issue also
    applies to sr_read_reg.

    This can be avoided by checking the return value of sr_share_read_word
    and sr_read_reg, and propagating the error if the read operation failed.

    Found by code review.

    Cc: stable@vger.kernel.org
    Fixes: c9b37458e956 ("USB2NET : SR9700 : One chip USB 1.1 USB2NET SR9700Device Driver Support")
    Signed-off-by: Ma Ke <make24@iscas.ac.cn>
    Reviewed-by: Shigeru Yoshida <syoshida@redhat.com>
    Reviewed-by: Hariprasad Kelam <hkelam@marvell.com>
    Signed-off-by: David S. Miller <davem@davemloft.net>

diff --git a/drivers/net/usb/sr9700.c b/drivers/net/usb/sr9700.c
index 0a662e42ed96..cb7d2f798fb4 100644
--- a/drivers/net/usb/sr9700.c
+++ b/drivers/net/usb/sr9700.c
@@ -179,6 +179,7 @@ static int sr_mdio_read(struct net_device *netdev, int phy_id, int loc)
        struct usbnet *dev = netdev_priv(netdev);
        __le16 res;
        int rc = 0;
+       int err;

        if (phy_id) {
                netdev_dbg(netdev, "Only internal phy supported\n");
@@ -189,11 +190,17 @@ static int sr_mdio_read(struct net_device *netdev, int phy_id, int loc)
        if (loc == MII_BMSR) {
                u8 value;

-               sr_read_reg(dev, SR_NSR, &value);
+               err = sr_read_reg(dev, SR_NSR, &value);
+               if (err < 0)
+                       return err;
+
                if (value & NSR_LINKST)
                        rc = 1;
        }
-       sr_share_read_word(dev, 1, loc, &res);
+       err = sr_share_read_word(dev, 1, loc, &res);
+       if (err < 0)
+               return err;
+
        if (rc == 1)
                res = le16_to_cpu(res) | BMSR_LSTATUS;
        else
doug@s19:~/kernel/linux$

```
EDIT: If you need some of the most recent driver edits, you will have to use a mainline kernel.

```
doug@s19:~/kernel/linux$ git log --oneline drivers/net/usb/sr9700.c
08f3a5c38087 net: usb: sr9700: fix uninitialized variable use in sr_mdio_read
05417aa9c0c0 net: usb: sr9700: stop lying about skb->truesize
ecf7cf8efb59 net: usb: sr9700: Handle negative len
e9da0b56fe27 sr9700: sanity check for packet length
2674e7ea22ba net: usb: don't write directly to netdev->dev_addr
766607570bec ethernet: constify references to netdev->dev_addr in drivers
49ed8dde3715 net: usb: use eth_hw_addr_set() for dev->addr_len cases
a76053707dbf dev_ioctl: split out ndo_eth_ioctl
77651900cede usbnet: add _mii suffix to usbnet_set/get_link_ksettings
323955a0498c net: usb: switch to dev_get_tstats64 and remove usbnet_get_stats64 alias
f819cd926ca7 drivers: net: Remove unnecessary semicolon
ba23dc642dff net: usb: sr9700: Replace mdelay() with msleep() in sr9700_bind()
fb796707d7a6 Merge git://git.kernel.org/pub/scm/linux/kernel/git/davem/net
d532c1082f68 sr9700: use skb_cow_head() to deal with cloned skbs
c8b5d129ee29 net: usbnet: support 64bit stats
39f49eadc3e5 net: usb: sr9700: use new api ethtool_{get|set}_link_ksettings
06b19b1b1785 net: usb: sr9700: Use 'SR_' prefix for the common register macros
a81ab36bf52d drivers/net: delete non-required instances of include <linux/init.h>
c9b37458e956 USB2NET : SR9700 : One chip USB 1.1 USB2NET SR9700Device Driver Support
doug@s19:~/kernel/linux$ git tag --contains 08f3a5c38087
v6.11-rc2
doug@s19:~/kernel/linux$ git tag --contains 05417aa9c0c0
v6.10
v6.10-rc1
v6.10-rc2
v6.10-rc3
v6.10-rc4
v6.10-rc5
v6.10-rc6
v6.10-rc7
v6.11-rc1
v6.11-rc2

```Note that at this time of writing mainline is up to [6.11-rc5]("https://kernel.ubuntu.com/mainline/v6.11-rc5/"), I am just behind a few weeks.

EDIT 2: after catching up:
```
doug@s19:~/kernel/linux$ git tag --contains 08f3a5c38087
v6.11-rc2
v6.11-rc3
v6.11-rc4
v6.11-rc5
doug@s19:~/kernel/linux$
```

---

### Post by 123nbom on 2024-08-30
I will be using Ubuntu 20.04.4 LTS based on Linux kernel versions 5.4  and 5.8. Will the updated drivers make my device work as intended? I think that i need the latest driver to ensure my device  functions properly. Initially, my priority was to simply make the device  work, regardless of whether it functions perfectly or not. At the very  least, I want it to work.
Is there a way to update or install the driver online? For example, can I use a command like 'sudo update sr9700' to do this?

---

### Post by Doug S on 2024-08-31
> **123nbom said:**
> Is there a way to update or install the driver online? For example, can I use a command like 'sudo update sr9700' to do this?No.

---

### Post by 123nbom on 2024-08-31
What do i do now. if there any way to make this device work, tell me

---

### Post by Yellow Pasque on 2024-08-31
> **123nbom said:**
> The problem is that Linux only recognizes this device as a CD drive.

[https://manpages.ubuntu.com/manpages/noble/man1/usb_modeswitch.1.html](https://manpages.ubuntu.com/manpages/noble/man1/usb_modeswitch.1.html)

I think 0fe6:9700 is the USB ID, but check output of lsusb to be sure.
```

sudo apt install usb-modeswitch
sudo usb_modeswitch -v 0fe6 -p 9700 -K

```

And before you give up and throw the device away, you can try hacking the hardware like this person:
[https://blog.brixit.nl/making-a-usb-ethernet-adapter-work-sr9700/](https://blog.brixit.nl/making-a-usb-ethernet-adapter-work-sr9700/)

---

### Post by 123nbom on 2024-08-31
Are you sure this code can make my device work?

---

### Post by Yellow Pasque on 2024-08-31
No, I'm not sure. But I am sure you need to get it out of CD mode if you want it to be more useful than a paperweight.

---

### Post by 123nbom on 2024-09-01
Nice joke xD

---

### Post by Yellow Pasque on 2024-09-01
> **123nbom said:**
> Nice joke xD

Thanks, but please tell me - are you going to take 5 seconds to run the commands or can I unsubscribe from this thread because I've already wasted enough time/effort?

---

### Post by 123nbom on 2024-09-01
I need to install ubuntu again. I will message you if i used these codes. But can you tell me the last thing, how can i make driver for it? I got the .c driver but i dont know how to use it. You can unsubscribe in any time you like, it wont be problem. i will keep search for fix

---

### Post by Yellow Pasque on 2024-09-01
> But can you tell me the last thing, how can i make driver for it? I got the .c driver but i dont know how to use it.

The driver module is already built into the kernel. Have been there some minor fixes since the days of Ubuntu 20.04? Yes. Do you actually need any of those fixes for the device to function? Probably not. And you shouldn't worry about the driver until you can get the device out of storage/CD mode.

---

### Post by 123nbom on 2024-09-02
I don't have a soldering iron to shorten the pins. Can I just cut or scratch it (using a knife)

---

### Post by Yellow Pasque on 2024-09-02
So you tried usb-modeswitch and it didn't work?

---

### Post by 123nbom on 2024-09-02
No, I'll try it when I get free time

---

### Post by 123nbom on 2024-09-06
Nothing..............
It didnt work, Seems this device wont work on linux forever. I will not try the hacking method

---

### Post by 123nbom on 2024-09-13
Hello. If i tried the hacking method (Cut the pins) Using a (knife) will it destroy my device?
And are you 100% sure that if i cut those pins will the device at Least (work) even if it didnt work on linux will it work on windows?

---

### Post by Yellow Pasque on 2024-09-13
> **123nbom said:**
> Hello. If i tried the hacking method (Cut the pins) Using a (knife) will it destroy my device?

I don't own the device and don't know anything more than what the page says. I don't even know if you have the exact same device. You're on your own there.

> And are you 100% sure that if i cut those pins will the device at Least (work) even if it didnt work on linux will it work on windows?

If you still want to use the device on Windows, don't even try to break it open. I just threw it out there as a "last ditch" idea before you sent it to the trash/recycling.

---

