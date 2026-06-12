---
title: "Lenovo Yoga 2 11 (not Pro) - wifi issues solved"
date: 2015-05-31
forum: Hardware
---

### Post by mercuzio2 on 2015-05-31
I recently bought a Lenovo Yoga 2 11 (not Pro) and wifi was not recognized by Ubuntu.
It took me a couple of hours to sort things out so I thought I could share the pain.

First of all, laptop does not come with any other networking adapters but wifi. So wifi had to be fixed offline.
Here's the wifi adapter details

```
*-network                description: Network controller
                product: BCM43142 802.11b/g/n
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=bcma-pci-bridge latency=0
                resources: irq:16 memory:d0400000-d0407fff 
```

And of course here's my Ubuntu version

```
mercuzio@mercuzio-Lenovo-Yoga-2-11:~$ uname -aLinux mercuzio-Lenovo-Yoga-2-11 3.16.0-38-generic #52~14.04.1-Ubuntu SMP Fri May 8 09:43:57 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
mercuzio@mercuzio-Lenovo-Yoga-2-11:~$ 

```

I was side-tracked big time by the discussions around 'rfkill' and the necessity of blackisting the 'ideapad_laptop' module. 
In reality the issue with Broadcom and Lenovo Yoga 2 11 has to do with the driver, not with the HW block on the adapter. In fact if you run an 'rfkill list all' you will not see anything blocked.

The solution was found by upgrading the driver: bcmwl-kernel-source.
You need to make sure that the correct version is used. The correct version is -> bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb
It can be found here -> [http://packages.ubuntu.com/utopic/amd64/bcmwl-kernel-source/download](http://packages.ubuntu.com/utopic/amd64/bcmwl-kernel-source/download)

* please check and re-check the version number. The one in the default dist for 14.04.1 is x.xx.xxx.141, while the correct one is x.xx.xxx.248 as you can see above.

Given I had no wifi connection, I downloaded all the required packages (and their dependencies) on another laptop and transferred them with an USB stick.

Good luck!

---

### Post by dino99 on 2015-05-31
as often, with recent hardware, you also need a recent ubuntu flavour for handling the chipsets.

---

### Post by jeremy31 on 2015-05-31
Actually, a year ago the problem was the hard block and ideapad_laptop but the ideapad module was fixed eventually.  See [http://git.kernel.org/cgit/linux/kernel/git/next/linux-next.git/commit/drivers/platform/x86/ideapad-laptop.c?id=85093f79f586176f8bbf90e56e22a3dfa526e334](http://git.kernel.org/cgit/linux/kernel/git/next/linux-next.git/commit/drivers/platform/x86/ideapad-laptop.c?id=85093f79f586176f8bbf90e56e22a3dfa526e334)

Now the problem is that the Ubuntu download still has the old version of bcmwl-kernel-source with the 3.16 kernel and bcmwl-kernel-source needs a patch file to compile in the 3.16 kernel.  This bug was reported in March and still isn't fixed  [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1432444](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1432444)

---

