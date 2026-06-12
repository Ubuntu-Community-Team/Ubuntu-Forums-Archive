---
title: "Lenovo laptops / Intel GMA 4500 brightness"
date: 2010-08-28
forum: Hardware
---

### Post by Chimes on 2010-08-28
For the record (as a reference to those with the same problem searching for the answer)

If you are using the Intel GMA4500 (/ GMA 4500 whatever) or a Lenovo laptop, and the brightness keys don't seem to work, try going to /proc/acpi/video/GFX0/ and then reading the "brightness" file in each of the subfolders. Some of them will say 'not supported' but another will give a list of available brightness levels and the current level. Just rewrite the entire file with the number you want and it'll change the screen to that brightness.

If this isn't working, try using [this guide]("http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx") to update to the latest kernel and video drivers (which have better support for intel chips than than already in 10.04.

I'm just posting this here because the answer isn't anywhere else on the web, and the thread which asked the question originally has somehow vanished (see ), so having the same problem, I figured out the solution myself and want to put it on record for google search.

example:
```

cd /proc/acpi/video/GFX0
cat DD3/brightness #this prints the contents of the file
echo "30" > DD3/brightness

```

---

