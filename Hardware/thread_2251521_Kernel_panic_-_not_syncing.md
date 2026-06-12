---
title: "Kernel panic - not syncing"
date: 2014-11-04
forum: Hardware
---

### Post by laurietruluck on 2014-11-04
Hello,

Relatively new to Ubuntu - can someone please help me with this problem?
I get the following (see picture) after turning on computer. Don't know what caused it or how to fix it.

[ATTACH=CONFIG]257752[/ATTACH]

Thanks very much,
Laurie

---

### Post by laurietruluck on 2014-11-06
Can somebody help me with this please? I can't use my computer at the moment and I need to!

Thanks

---

### Post by MIJ-VI on 2014-11-07
Does this happen on AC or battery power?
How old is the main battery?
How old is the CMOS battery?
Does the above panic occur when booting from a LIVE DVD?
How much RAM does your notebook have?
Was it running fine up until now or did you just install a fresh OS?
Does it run OK under other operating systems?

VPCEB1Z0E/VAIO, BIOS R0270Y8 05/05/2010

Support for VPCEB1Z0E | Sony
[http://www.sony.co.uk/support/en/product/vpceb1z0e](http://www.sony.co.uk/support/en/product/vpceb1z0e)

---

### Post by laurietruluck on 2014-11-08
Thanks for your reply!

It happens on both AC and battery power.
The main battery is about 4 years old. It lasts for about an hour or so of usage.
I don't know what the CMOS battery is...
I haven't tried booting from a DVD.
4GB RAM I believe.
I've been running Ubuntu fine for about 5 months, always updating.
Used to run fine on Windows as well.

I hope that helps you diagnose the problem a bit more.
Thanks

---

### Post by MIJ-VI on 2014-11-09
Re the *CMOS battery: It's a little battery mounted somewhere on the motherboard which is responsible for powering the small potion of RAM that preserves the time, date and BIOS' setup configuration when the AC supply and battery are both disconnected. When the *CMOS battery gets old and weak it can sometimes corrupt that small amount of RAM thus preventing the OS from properly interacting with the hardware via the BIOS. Accessing the *CMOS battery on a notebook computer usually involves dismantling the notebook to some degree.

However, one can test the *CMOS battery by disconnecting the AC adaptor and removing the main battery for a few minutes. After reinstalling the main battery and reconnecting the AC adaptor and booting the notebook, if the date and time are wrong then the CMOS battery has to be replaced.

But before bothering with the *CMOS battery, try booting from a DVD as part of a process of elimination. Also try booting from other OS install DVDs if you have them.

BTW:

- Are you using the original AC adaptor which came with the notebook?
- Can you boot into the BIOS?
- Have you downloaded and browsed through the manuals from the link I posted?
- Have you unplugged all unnecessary USB peripherals?

EDIT: You should download this too in case you or a computer tech has to replace that *CMOS battery:

M970 Service Manual20101012.pdf - 985287306_sm.pdf
[https://docs.sony.com/release/MDSM/985287306_sm.pdf](https://docs.sony.com/release/MDSM/985287306_sm.pdf)

*EDIT #2: I just had a look at the above Service Manual. The correct name for the "CMOS battery" I described above is: RTC Battery.

EDIT # 3:

CMOS battery also know as RTC battery | Laptop Parts 101
[http://www.laptopparts101.com/cmos-rtc-battery/](http://www.laptopparts101.com/cmos-rtc-battery/)

---

### Post by laurietruluck on 2014-11-10
I don't think I have a DVD I can boot from. What DVD could I use?

-I am using the original AC adapter
-Yes I can boot into the BIOS
-Yes I've downloaded and had a look at the manuals. I don't know what to look for though and it doesn't seem to be relevant to using my Vaio with ubuntu
-Yes I've unplugged all peripherals

Thanks for your help

---

### Post by MIJ-VI on 2014-11-10
> **laurietruluck said:**
> I don't think I have a DVD I can boot from. What DVD could I use?

-I am using the original AC adapter
-Yes I can boot into the BIOS
-Yes I've downloaded and had a look at the manuals. I don't know what to look for though and it doesn't seem to be relevant to using my Vaio with ubuntu
-Yes I've unplugged all peripherals

Thanks for your help

The purpose of booting from the following live DVD is to find out if it too exhibits a kernel panic (or any other problem). If not then that would narrow the problem down to the Ubuntu install which currently resides on your notebook's hard drive or possibly to the hard drive itself.

Please download **ubuntu-14.04.1-desktop-amd64.iso**,
- change its permissions to read-only (Right-click-->Properties-->Permissions)
- *check its sha256sum,
- burn it to a DVD-R / DVD+R,
- boot with said DVD, verify the DVD's integrity (tap the <Spacebar> when the keyboard icon appears at the bottom of the screen and additional options will appear) and then
- re-boot into the DVD's desktop to see how well your machine runs it. If all goes well then do a clean install (not an upgrade) and we'll take it from there. 
 
Ubuntu 14.04.1 LTS (Trusty Tahr)
[http://releases.ubuntu.com/trusty/](http://releases.ubuntu.com/trusty/)

HowToSHA256SUM - Community Help Wiki
[https://help.ubuntu.com/community/HowToSHA256SUM](https://help.ubuntu.com/community/HowToSHA256SUM)

*All I do is to:

1) Launch Terminal and type in *sha256sum* , tap the <Spacebar> once, then drag the downloaded **ubuntu-14.04.1-desktop-amd64.iso** into the Terminal window, un-highlight the **ubuntu-14.04.1-desktop-amd64.iso** (so that it won't mount when I tap the <Enter> key) and then tap the <Enter> key.

2) Highlight and copy the resulting sha256sum and paste it underneath the one below (which I copied from the 'Ubuntu 14.04.1 LTS (Trusty Tahr)' link) to see if they match (they should if the **ubuntu-14.04.1-desktop-amd64.iso** you downloaded is intact).

sha256sum
347232658fb14a7ff473ae8854b588da3df70e36b97e4f70e00f18c7b64e4b31 *ubuntu-14.04.1-desktop-amd64.iso

--

Downloading and studying manuals is something I always do to familiarize myself with the gear I'm using. While much of the info in PC manuals is the same from one to the next, every now and again there's a machine-specific quirk, the knowledge of which can be helpful.

---

