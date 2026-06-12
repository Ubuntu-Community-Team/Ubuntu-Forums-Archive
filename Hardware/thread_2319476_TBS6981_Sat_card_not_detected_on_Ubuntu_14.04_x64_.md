---
title: "TBS6981 Sat card not detected on Ubuntu 14.04 x64 (kernel 4.2)"
date: 2016-04-04
forum: Hardware
---

### Post by originaldavz on 2016-04-04
Hi.
After a clean reinstall of my Ubuntu the other week I am having trouble installing the TBS6981 drivers.
I have run through the instructions many times in the past (usually after upgrading the kernel) without any issue but this time it doesn't work. The strange thing is that it worked last week and there have been no changes to the kernel since then.
These are the instructions I followed:
```

cd /usr/src/TBS6981
rm -r linux-tbs-drivers
# Have also used older version of the drivers, previously worked with v160219
unzip -q tbs-linux-drivers_v160331.zip
tar -xjf linux-tbs-drivers.tar.bz2


# This patch from http://www.vanbest.org/drupal7/sites/www.vanbest.org/files/linux-3.7.1-dvb-mutex.patch, have tried installing both with and without this line...
patch -p1 <  linux-3.7.1-dvb-mutex.patch


cd linux-tbs-drivers
find -type d -exec chmod 755 \{\} \;
find -type f -exec chmod 644 \{\} \;
find -name '*.sh' -exec chmod 755 \{\} \;
find -name '*.pl' -exec chmod 755 \{\} \;


# Some tutorials mention this line, when it worked previously I needed this line
rm -r -f /lib/modules/$(uname -r)/kernel/drivers/media


./v4l/tbs-x86_64.sh
make
make install
# One tip somewhere also mentioned to try copying the dvb-fe-cx24116.fw in the zip file to /lib/firmware. Was not necessary for the once it did work
cp ../dvb-fe-cx24116.fw /lib/firmware
reboot

```


The code runs fine with no errors. On reboot the output of dmesg | grep -i dvb shows nothing.


I also once installed an older kernel (3.19) and tried, it worked (only after deleting the /lib/modules/$(uname -r)/kernel/drivers/media folder) so I tried again booting into the 4.2 kernel, that also worked. Now it has disappeared and trying to make and make install seem to work, but shows nothing in bootup.


Please help me install this, and I'm happy to provide any additional details or outputs, I'm just not sure what I'm looking for in logs or where to get the details of this stuff.


Thanks very much

---

### Post by originaldavz on 2016-04-06
Here is an output of my dmesg if that will help anybody with more info
[http://pastebin.com/f1HKJeqp](http://pastebin.com/f1HKJeqp)

And my output of `lspci -v`
[http://pastebin.com/aXKP5zpZ](http://pastebin.com/aXKP5zpZ)

Really am stuck with this one, any suggestions welcome as I am going crazy just constantly reinstalling it
Thanks

---

### Post by listless2 on 2016-04-10
I had this exact same problem. Solved it using:
[http://ubuntuforums.org/showthread.php?t=2240131](http://ubuntuforums.org/showthread.php?t=2240131) which recommends:

```
sudo rm -R /lib/modules/3.13.0-24-generic/kernel/drivers/media/
cd tbs-linux-drivers_v140323/linux-tbs-drivers/
make distclean
./v4l/tbs-x86_64.sh
make -j5
sudo make install
```



that rm -R bit at the top was what solved it for me. I was a bit nervous  running it because kernel/drivers/media contains a bunch of different  things that arent really related to the tv tuner card. But it worked,  so... *shrug*.  If anyone reading this could explain why killing that  entire directory isn't as destructive as one might expect then I'd  certainly feel safer for knowing.

---

