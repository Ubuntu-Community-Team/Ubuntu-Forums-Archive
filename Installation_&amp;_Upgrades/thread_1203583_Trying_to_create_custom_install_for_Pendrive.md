---
title: "Trying to create custom install for Pendrive"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by daniel.pool on 2009-07-03
Hi,

I'm trying to put together a custom ubuntu install for my HTPC. I'm looking to set up an [XBMCbuntu]("http://xbmc.org/wiki/?title=XBMCbuntu") build which will run off a USB stick, but also run some extra services such as VDR. From what I understand this is the base server install of Ubuntu, the Open SSH Server and then the addition of VDR and any other packages I want/need.

From what I understand the instructions in the link provided above aren't really applicable as they would install on an HDD, or knacker a USB stick due to the IO of a normal install. I've therefore been looking to follow instructions for creating a [LiveCD from stratch]("https://help.ubuntu.com/community/LiveCDCustomizationFromScratch"). My plan is instead of installing the standard ubuntu, I'll go for the base server etc.

My problem is that when I get to the line where I run the update of apt, I'm unable to resolve any URL. For example:

```
Err http://security.ubuntu.com jaunty-security Release.gpg
  Could not resolve 'security.ubuntu.com'

```This is where I announce that I'm a bit of a linux noob and am still learning the ropes. So perhaps this is an easy one to fix?

Also, am I on the right track to achieve what I want, or will I not be able to put together the install I'm after this way?

Cheers in advance,
~Dan

---

### Post by pytheas22 on 2009-07-03
I've never installed XMBC, but I looked over their installation instructions that you link to, and I would think that you could follow them exactly as written.  The only exception would be that at the partitioning step, you should select Expert Mode and tell it to install to your USB stick rather than the internal hard drive.  It should be obvious which device is the USB based on the disk size.

And if by "knacker a USB stick" you mean destroy it by reading and writing to it too many times, don't worry about this.  I've installed Ubuntu desktop edition (which involves a lot more I/O than the much smaller server edition) from scratch at least four times on my $20 thumb drive, as well as used the device for lots of other I/O-intensive stuff, and it's still going strong.  If you installed XMBC to the device a hundred times, you might start to damage it, but one installation is no worse than copying a 30-minute video to the drive.

So I think that installing directly to a USB stick following the XMBC instructions would be your best approach.  But to answer your real question, the error message that you posted would most likely result from not being connected to the Internet, so make sure you're online and able to resolve domain names, and try again.

---

### Post by daniel.pool on 2009-07-03
Pytheas,

Thanks your reply, I was actually just about to post that I managed to fix the apt-get issue. I was connected to the internet, but hadn't copied the resolv.conf across (must have been a typo I missed the first time around). This was stopping it resolving the DNS mappings, so all good now.

To your first point though, I'd thought that a pen drive install needed something like casper in order to persist any changes, and the install described there wouldn't put casper on?

Thanks,

---

### Post by pytheas22 on 2009-07-03
While I'm not an expert on these things, I believe that casper is used for live systems, not ones where you want changes to be persistent throughout reboots.  If you install Ubuntu to the USB stick using the normal installation method, changes should persist through reboots--as far as Ubuntu is concerned, your USB stick is just another hard drive, so the system should act just as it would if it were installed to an internal disk.

Anyway, glad you fixed the DNS issue.

---

