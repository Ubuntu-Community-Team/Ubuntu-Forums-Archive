---
title: "ati driver manual install problem"
date: 2012-03-09
forum: Hardware
---

### Post by realpsygnosis on 2012-03-09
hi!
I have graphical glitch and I have the idea to install the official ati driver (ati mobility radeon hd 3450) and I've downloaded the .run from the amd website..

then I've followed the istruction on the [ubuntu wiki]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

but the strange thing is that everytime I give the command 

```
sudo sh amd-driver-installer-12-1-x86.x86_64.run --buildpkg Ubuntu/oneiric
```

I first have an error that the ati installer can't install dpkg-dev so I've installed it from apt-get
then it couldn't install debhelper and i've installed it from apt-get;
then the same thing with dh-modaliases, execstack..

After I've installed all this the installer works, but if I give:

```
fglrxinfo
```

I have this error:

> X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  139 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13


and now ubuntu works so bad slow and with bad graphic..how can I solve this and install the driver well?
thanks a lot in advance I'd like to learn what I've do wrong

---

