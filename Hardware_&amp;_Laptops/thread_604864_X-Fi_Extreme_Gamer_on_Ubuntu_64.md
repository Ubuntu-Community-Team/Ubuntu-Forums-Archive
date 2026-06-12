---
title: "X-Fi Extreme Gamer on Ubuntu 64"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by Dawoodmm on 2007-11-06
Hi there.
I've got a slight problem with my sound on my 64-bit installation.I currently own a Dell inspiron 531, which has an integrated sound card and an Creative X-Fi Extreme Gamer.
I decided to use 64bit ubuntu, because i thought that since the X-Fi sound card drivers were out for linux, i would be able to use it.

I somehow managed to get the onboard sound working after installing a quiete a few random ALSA packages / drivers (the read me file said i needd a complete kernel and ALSA installation)

However, i'm having some trouble setting the X-Fi up and running. i downloaded the driver files for 64 bit linux and tried to run the install file. However, it says that it will only run on a 64-bit system. and i know i have a 64bit installation. So how do i go about doing this, and making it work.
Thanks

---

### Post by Onurzaim on 2007-11-07
In those installation there is usually a "force" option. 

Also you can try another terminal viewer if you try using command prompt.

---

### Post by Jenguran on 2008-02-03
If you open the "installer" file in a text editor, the first lines look like:

```
platform=$(uname -i)

if [ "$platform" != "x86_64" ]
then
	echo "This product only support 64-bit Operating Systems"
	echo "Setup will now exit"
	exit 1
fi
```

When I do uname -i on Ubuntu 7,10 I get "unknown" so just change the if to read like:
```
if [ "$platform" != "unknown" ]
```

That's as far as I got. Most of creative's driver packs can't even detect my (onboard) X-Fi, even on Windows.

---

