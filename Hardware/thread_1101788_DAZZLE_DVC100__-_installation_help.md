---
title: "DAZZLE DVC100  - installation help"
date: 2009-03-20
forum: Hardware
---

### Post by gladnicke3 on 2009-03-20
[B][U]Hello!
[/U][/B]
I would install an DAZZLE DVC 100 - adapter, an adapter who can transferring from an old VHS and older analog things to my computer, im using the Instant recorder - prgoram, but i cant install the adapter in Ubuntu 8.10. Anyone who knows how todo?

In the swedish Ubuntu forum, a guy told me to check in this link: [http://translate.google.com/translate?u=http%3A%2F%2Fwww.equinoxefr.org%2Fpost%2F2008%2F09%2F05%2Fdazzle-dvc-100-sous-ubuntu-804%2F&hl=nl&ie=UTF-8&sl=fr&tl=en](http://translate.google.com/translate?u=http%3A%2F%2Fwww.equinoxefr.org%2Fpost%2F2008%2F09%2F05%2Fdazzle-dvc-100-sous-ubuntu-804%2F&hl=nl&ie=UTF-8&sl=fr&tl=en)

There was a lot of codes there, and i have not used Linux before, so everything is quite new for me, so i did not understand anything.

Anyone who can help where to find the right things so i can use the adapter? 

//Gladnicke3 :D

---

### Post by cariboo on 2009-03-20
Here are the commands needed to install your device in a condensed version:

[list=1]
[*] Open an Applications-->Accessories-->Terminal and type:

```
lsusb
```

with your device plugged in the result should look something like this:

```
Bus 005 Device 003: ID 2304:021 a Pinnacle Systems, Inc.
```

[*] You will need to install a few programs to help compile the driver. In the same terminal type:

```
sudo apt-get install mercurial build-essential
```

[*] You need to use mecurial you installed in the previous step to retrieve the source module:

First you deed to create a directory to download the module source to:

```
mkdir ~/src
```

This command creates a directory called src in you home directory. Next change directory to src:

```
cd ~/src
```

[*] This next command:

```
hg clone http://linuxtv.org/hg/v4l-dvb
```

downloads the module source to the directory you just created, go get a cup of your favorite beverage as this step may take a while.

```
cd v4l-dvb
```

The above command changes directory to the directory that was created when the module source was retrieved

[*] the next step is to compile the source:

```
make
```

You will see some errors, but it is safe ignore them

[*] The final step is to install the modules:

```
sudo make install
```

once this step is done the driver for your device should load automagically when the device is plugged in.

[/list]

Note: I just had a look and the driver for your device is available in kernel 2.6.28-11 which is part of Jaunty, the next version of Ubuntu due out at the end of April

Jim

---

