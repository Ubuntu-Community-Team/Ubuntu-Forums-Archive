---
title: "I buy Dell laptop with Ubuntu and the hardware is not supported"
date: 2021-11-24
forum: Hardware
---

### Post by juanjf on 2021-11-24
It's very difficult to get that all the components of a laptop work in linux, so I made an economic effort and I bought a Dell Inspiron with Ubuntu 20.04.3 LTS. Dell has sold me a computer with Ubuntu 20.04 and certain features, including the fingerprint reader, and ... Surprise! Fingerprint reader doesn't work. Technical support solution that costs me about 10€/month is that I've to install Windows, they say that Ubuntu is free and they don't offer support for this operating system beacuse is free of charge. I'm outraged, I want to use linux. I bought this computer (and not another) because of the operating system, I wanted everything to work without problems. I'm using the operating system that comes with the factory computer, it should work.
I leave my comment here for the community to know, in case someone else is looking for a laptop for linux, let him/her know about this problem. I feel cheated.

I have tried several solutions, including:
```
sudo sh -c 'cat > /etc/apt/sources.list.d/focal-dell.list << EOF
deb http://dell.archive.canonical.com/updates/ focal-dell public
# deb-src http://dell.archive.canonical.com/updates/ focal-dell public

deb http://dell.archive.canonical.com/updates/ focal-oem public
# deb-src http://dell.archive.canonical.com/updates/ focal-oem public

deb http://dell.archive.canonical.com/updates/ focal-somerville public
# deb-src http://dell.archive.canonical.com/updates/ focal-somerville public

deb http://dell.archive.canonical.com/updates/ focal-somerville-melisa public
# deb-src http://dell.archive.canonical.com/updates focal-somerville-melisa public
EOF'

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9FDA6BED73CDC22
sudo apt update -qq

sudo apt install oem-somerville-melisa-meta libfprint-2-tod1-goodix oem-somerville-meta tlp-config -y

sudo add-apt-repository ppa:boltgolt/howdy -y
sudo apt update -qq
sudo apt install howdy -y

sudo usermod -aG input <user>
```

On this website it's reported that is not compatible: [https://linux-hardware.org/?id=usb:27c6-639c](https://linux-hardware.org/?id=usb:27c6-639c)
```
$ lsusb
Bus 003 Device 003: ID 27c6:639c Shenzhen Goodix Technology Co.,Ltd. Goodix USB2.0 MISC
```
```
$ fprintd-verify
Impossible to verify: GDBus.Error:net.reactivated.Fprint.Error.NoSuchDevice: No devices available
```
```
$ uname -r
5.11.0-40-generic
```

---

### Post by Frogs Hair on 2021-11-24
You may get help with Howdy on the developers page. I see no need to add the key server on that page.

[https://github.com/boltgolt/howdy](https://github.com/boltgolt/howdy)

---

### Post by oldfred on 2021-11-24
See also:
[https://www.reddit.com/r/pop_os/comments/hl3jxg/fingerprint_login_working_on_dell_with_goodix/](https://www.reddit.com/r/pop_os/comments/hl3jxg/fingerprint_login_working_on_dell_with_goodix/)
&
[https://www.dell.com/community/XPS/XPS-13-9300-Does-fingerprint-reader-work-on-linux/td-p/7514958](https://www.dell.com/community/XPS/XPS-13-9300-Does-fingerprint-reader-work-on-linux/td-p/7514958)

Some mention of newer versions of Ubuntu with newer kernel also work.
I might create a 30 or 40GB / partition for a test install and see if then it does work.

---

### Post by Shibblet on 2021-11-25
> **juanjf said:**
> It's very difficult to get that all the components of a laptop work in linux, so I made an economic effort and I bought a Dell Inspiron with Ubuntu 20.04.3 LTS. Dell has sold me a computer with Ubuntu 20.04 and certain features, including the fingerprint reader, and ... Surprise! Fingerprint reader doesn't work. Technical support solution that costs me about 10€/month is that I've to install Windows, they say that Ubuntu is free and they don't offer support for this operating system beacuse is free of charge. I'm outraged, I want to use linux. I bought this computer (and not another) because of the operating system, I wanted everything to work without problems. I'm using the operating system that comes with the factory computer, it should work.
I leave my comment here for the community to know, in case someone else is looking for a laptop for linux, let him/her know about this problem. I feel cheated.

I agree with you.  I would feel cheated as well.

If you purchased the computer with Ubuntu as the OS, and there is nothing on their web-site (or at the place of purchase) that states that some of the functionality does not work...

If they are not willing to help, I'd return the computer in a nano-second.

Purchased "As Advertised," but does not function "As Advertised."

---

