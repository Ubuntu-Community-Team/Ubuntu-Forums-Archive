---
title: "1/0 Error &amp; no visible partitions"
date: 2008-12-26
forum: Installation &amp; Upgrades
---

### Post by jesuisbenjamin on 2008-12-26
Hello Forum

I managed to convert my father to switch to Ubuntu. However when i tried to run from disk and install i got the following issues:

[LIST]
[*]First arriving at step 4 of 7, there were no partitions at all listed and couldnt select any as root for install.
[*]With another download i tried again but couldn't even run from live CD. I would read the followin error:
[/LIST]

```
[127119323] en request: 1/0 error, dev sr1, sector 1431184
[127119381] buffer 1/0 error on device sr1, logical block 35779697
```

This several times.

I can't figure out why it would boot and load from Live CD the first time and not the second. 
Then i can' figure out why the installation process couldn't identify any partitions while the demo session saw the various partitions of the disk at the time.
Finally i have no idee as to what the 1/0 error etc. is.

If someone can help us with this it would be great.

---

### Post by albinootje on 2008-12-26
> **jesuisbenjamin said:**
> 
[*]With another download i tried again but couldn't even run from live CD. I would read the followin error:
[/LIST]

```
[127119323] en request: 1/0 error, dev sr1, sector 1431184
[127119381] buffer 1/0 error on device sr1, logical block 35779697
```



Make sure you verify the md5sum of the downloaded iso image.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto)

And burn the cdrom at lower burning-speed than you would normally do.

You can also install Ubuntu from a usb-stick.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

