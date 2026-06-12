---
title: "Cannot see different drives"
date: 2012-08-01
forum: Hardware
---

### Post by tapasray on 2012-08-01
I am running Ubuntu 12.04 on a Dell Vostro laptop. I am unable to see the hard drive, the optical drive, or any USB stick that I insert in one of the USB drives. My guess is that these should be visible in the "root" folder, but when I double-clock on it, I receive a message that I do not have permission - although I have "administrator" status. Would really appreciate some help here. Thanks!

---

### Post by steeldriver on 2012-08-01
removable drives should appear under /media

/root is the private home directory for the actual root user and is not really used in Ubuntu (since administrator privileges are granted via sudo)

---

### Post by tapasray on 2012-08-01
Thanks, @steeldriver! I was able to see the contents of a thumb drive in 'media'. But when I inserted a DVD and selected 'Movie Player', it refused to play. Says "may be because the DVD is encrypted and a DVD decryption library is not installed." So how do I install the library - assuming that indeed is the problem?

Thanks again!

---

### Post by ahallubuntu on 2012-08-02
To play DVDs, install libdvdcss:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs/](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs/)

You may or may not need to do this first (may not be needed):

```
sudo apt-get install libdvdread4
```

but you almost certainly have to do this:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

After that, you should be able to play DVDs.

---

### Post by tapasray on 2012-08-02
Thanks, @ahallubuntu! I'll do this as soon as I can go online. That's the other issue I am getting help about, on the 'Networking & Wireless' forum.

---

