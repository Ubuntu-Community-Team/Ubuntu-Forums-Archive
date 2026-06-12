---
title: "iPhone USB pass-through to VMware broken?"
date: 2007-07-01
forum: Hardware &amp; Laptops
---

### Post by milli on 2007-07-01
Help?  Hints?

Ok, I've been Googling for a couple days now, chasing down any possible lead and I've come up short.

Setup:  Thinkpad T60p laptop, Ubuntu Feisty (7.04), kernel 2.6.20-16-generic (latest).  VMware workstation 6.0.0 build-45731installed with Window XP SP2 guest.  (obstensibly to run Quicken and QuickBooks, but now also to run iTunes...)

Problem:  iPhone cannot connect via USB 2.0 to Windows XP and be recognized, hence, can't sync, activate, etc..  :(

Sypmtoms:

The ehci_hcd driver seems to pick up on the iPhone okay, and HAL does recognize it as a camera device (and thus causes a popup asking what to do with it).  I didn't want HAL to do that so I told HAL to ignore the device (created /etc/hal/fdi/preprobe/10-iphone.fdi in which I put instructions to "info.ignore" the device).  Good on that front.

Jul  1 17:28:42 host kernel: [150548.956000] usb 5-2: new high speed USB device using ehci_hcd and address 24
Jul  1 17:28:42 host kernel: [150549.088000] usb 5-2: configuration #1 chosen from 3 choices

When I go into VMware to connect it to Windows, by selecting VM->Removable Devices->USB Devices->Apple iPhone, which should enable it, it does a quick connect and disconnect in the VM...

Jul 01 17:26:27.405: vmx| USB: Connecting device 0xe005001605ac1290
Jul 01 17:26:27.405: vmx| USB: Found device [name:Genesys\ Logic\ USB\ Reader vid:05e3 pid:0710 path:5/3 speed:high family:storage]
Jul 01 17:26:27.405: vmx| USB: Found device [name:SGS\ Thomson\ Biometric\ Coprocessor vid:0483 pid:2016 path:4/1 speed:full family:vendor]
Jul 01 17:26:27.405: vmx| USB: Found device [name:Apple\ iPhone vid:05ac pid:1290 path:5/4 speed:high family:vendor,hid,imaging autoclean:1]
Jul 01 17:26:27.405: vmx| USBG: CONNREQ: Dequeued head request after 0 ms for [name:Apple\ iPhone vid:05ac pid:1290 path:5/4 speed:high family:vendor,hid,imaging autoclean:1]
Jul 01 17:26:27.466: vmx| USBGL: Connect failed for e005001605ac1290
Jul 01 17:26:27.715: vmx| USB: Autoconnecting e005001705ac1290
Jul 01 17:26:27.715: vmx| USBGL: Connect failed for e005001705ac1290
Jul 01 17:26:27.715: vmx| USBGL: Autoconnect failed for e005001705ac1290

There were some hints on the VMware forums and elsewhere that this is caused by the USB driver in the kernel, some posts referencing problems with the 2.6.21 kernel on other distros, and that going back to 2.6.20 fixed it.  Well, that's what I'm running of course and I have the problem attributed to 2.6.21...  perhaps some of the kernel git commits from 2.6.21 have been applied to 2.6.20-16-generic in Ubuntu and re-introduce the problem?

I'll keep looking, but could use some help / hints / more clues...

---

### Post by fheinsen on 2007-07-01
Similar problem here.  Running XP SP2 under vmware player 2.0.  Win XP actually *does* recognize the iPhone -- but then it never shows up on iTunes.

Any help would be appreciated of course.

---

### Post by jtatum on 2007-07-03
Running VMware server on my laptop which is running Dapper.  Kernel version is 2.6.17 and the guest is XP Pro SP2.  Same problems as above - the device shows in the guest OS but does not appear in iTunes.  It looks good in the log:

Jul 03 13:40:51: vmx| USB: Found device [name:Apple\ Inc.\ iPhone vid:05ac pid:1
290 path:5/4]
Jul 03 13:40:51: vmx| USB: Autoconnecting device "Apple Inc. iPhone" matching pa
ttern [path:5/4 autoclean:1]
Jul 03 13:40:51: vmx| USB: Connecting device 0xe005000505ac1290

Edit: Looks like an issue that VMware is already working on...
[http://www.vmware.com/community/thread.jspa?messageID=686593](http://www.vmware.com/community/thread.jspa?messageID=686593)

---

### Post by fheinsen on 2007-07-03
> **jtatum said:**
> Looks like an issue that VMware is already working on...
[http://www.vmware.com/community/thread.jspa?messageID=686593](http://www.vmware.com/community/thread.jspa?messageID=686593)

Jtatum - thanks, this is helpful -- it means we will need to wait for the VMware patch.  In the meantime, I was able to get the phone activated by creating a new hard drive partition, installing and booting Win XP in it, and then running the new version of iTunes.  (Like many others in these forums, I have a handful of unused CDs of Win XP from past PC purchases.)  I hope this is helpful to others seeking to activate their iPhones.

---

### Post by gadgetgirl on 2007-07-11
> **milli said:**
> The ehci_hcd driver seems to pick up on the iPhone okay, and HAL does recognize it as a camera device (and thus causes a popup asking what to do with it).  I didn't want HAL to do that so I told HAL to ignore the device (created /etc/hal/fdi/preprobe/10-iphone.fdi in which I put instructions to "info.ignore" the device).  Good on that front.

Could someone post the fdi to ignore the iPhone in HAL here? I plugged in my iPhone today to charge it on my ubuntu laptop, and it's freaking out. The iPhone goes into charge mode, the photo import dialog comes up in gnome, and the iPhone drops out of charge mode. I'm hoping that configuring HAL to ignore it will fix this.

Edit:
I think the fdi to handle it is:
```

<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
    <match key="info.product" string="iPhone">
      <merge key="info.ignore" type="bool">true</merge>
    </match>
  </device>
</deviceinfo>

```

However, that didn't fix anything for me. I'll make a new post for my question.

---

### Post by milli on 2007-07-12
Here's mine...

/etc/hal/fdi/preprobe/10-iphone.fdi:

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device> 
    <match key="usb.vendor_id" int="1452">
      <match key="usb.product_id" int="4752">
        <merge key="info.ignore" type="bool">true</merge>
      </match>
    </match>
  </device>
</deviceinfo>

```

Don't forget to "/etc/init.d/dbus restart", which will restart HAL so this change is picked up.

---

### Post by haldor64 on 2007-07-26
Same here (T60p, Feisty, VMware Server...)

But it looks like its not an VMware issue, try lsusb.
As soon as you do lsusb, the iPhone goes into charging mode.
Then after a second or two comes back to normal, but you don't see it with lsusb...
The Windows XP VMware guest was able to connect the iPhone USB port when I did a
$ while true; do lsusb; sleep 1; done
first.

But then XP just recognized a "Apple Mobile Device USB Driver".

Then I stopped the Apple Mobile Device service (just run services.msc), and the Found New Hardware Wizard popped up, wants to install a driver for iPhone.

When I want to install the driver automatically, says cant find it.
Under C:/Program files/common Files/Apple/Mobile Device Support/Drivers
there is only a driver for the USB part.

Starting the Apple Mobile Device service again freezes... I have to disconnect the iPhone to recover.

Any ideas, could this be a workaround?

Or is patching the USB kernel modules the only way?

---

### Post by niclane on 2007-09-05
Hey anyone find a solution to this????

Nic

---

### Post by Xlorep DarkHelm on 2007-09-19
I also am quite interested. It definitely appears to be a problem with the kernel driver from what I can tell. My iPhone won't charge for more than a half second then immediately drops out from charging mode. There are times it appears to connect, disconnect, connect, etc. multiple times in a series over a few seconds, usually if I try to do anything with the phone, like see pictures on it. This does not appear to be a problem exclusive to vmware or virtualbox or any other virtualization software, but rather something wrong in the module that os used by the Kernel itself.

This is frustrating, because I have to currently borrow my roommate's computer to sync my iPhone, since I do not have a Windows partition on my system, nor want one.

---

### Post by wireless on 2007-10-03
Hey All.
Any progress with this issue?
running gutsy beta, thinkpad x60, and VW 6.0.1  and having the same issue exactly.

---

### Post by niclane on 2007-11-24
hey folks, anyone out there seen a solution to this problem?

nic

---

### Post by jgnavarro on 2008-04-29
Solution: Install VMWare 6.0.3.x workstation and the iphone is right

---

### Post by bobdobbs on 2008-07-15
> **jgnavarro said:**
> Solution: Install VMWare 6.0.3.x workstation and the iphone is right

Alas, this is not the case.

I understood that up-to-date versions of VMware workstation don't have this problem.

I'm using vmware workstation 6.04 on both my laptop and my deskktop.

In both, vmware sees that an iphone is connected.
But, the XP guest cant see the iphone.

This is quiet frustrating.

---

### Post by man on 2008-07-23
It works for me here.
Try running vmware as root.

---

