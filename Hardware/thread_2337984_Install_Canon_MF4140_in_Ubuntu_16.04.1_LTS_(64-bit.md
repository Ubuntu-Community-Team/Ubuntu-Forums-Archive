---
title: "Install Canon MF4140 in Ubuntu 16.04.1 LTS (64-bit)"
date: 2016-09-23
forum: Hardware
---

### Post by Iurie on 2016-09-23
This is an update of my [old instructions]("https://ubuntuforums.org/showthread.php?t=1723101&page=10&p=12387276#post12387276") about how to install the Canon i-SENSYS MF4140 all-in-one laser printer in Ubuntu 16.04.1 LTS (64-bit). Because the used driver is for the MF4150 printer, I suppose these instructions will work also for it.

1. Install dependencies (not sure if all of them are needed):
```
sudo apt install libc6-i386 lib32ncurses5 lib32z1
sudo apt install libxml2:i386 libjpeg62:i386 libstdc++6:i386
```

2. Create a symbolic link '*/usr/lib64*' to '*/usr/lib*' (not sure if this is really needed):
```
sudo ln -s /usr/lib /usr/lib64
```

3. Download the *[Linux_UFRII_PrinterDriver_V320_us_EN.tar.gz]("http://gdlp01.c-wss.com/gds/8/0100002708/14/Linux_UFRII_PrinterDriver_V320_uk_EN.tar.gz")* from [Canon USA]("https://www.usa.canon.com/internet/portal/us/home/support/details/printers/support-laser-printers-imageclass/imageclass-mf4150").

4. Extract files from archive.

5. If you extracted files in the *Downloads* folder, open the *~/Downloads/Linux_UFRII_PrinterDriver_V320_us_EN/64-bit_Driver/Debian/* folder in terminal and run:
```
sudo dpkg -i cndrvcups-common_3.60-1_amd64.deb
```

* If you received some errors about unmet dependencies, run:
```
sudo apt install -f
```

6. If the *cndrvcups-common_3.60-1_amd64.deb* package was installed without errors, run:
```
sudo dpkg -i cndrvcups-ufr2-us_3.20-1_amd64.deb
```

7. Plug the printer and enjoy!

**P.S.** To use the scanner, just install the *xsane* (my preferred). At the first run, if the *xsane* displays two options, select as in the below picture.

[IMG]http://66.media.tumblr.com/e7f5ba3cd6c1c3772b1b7b276f168767/tumblr_oe067jTLfe1rxg1n8o1_1280.png[/IMG]

---

